---
name: rest-api-integrator
description: Integrates REST APIs with automatic pagination handling, rate limit backoff, structured error recovery, and environment-variable-based credential management. Use when the user asks to call an API, fetch data from an external service, integrate a REST endpoint, or work with any HTTP-based data source.
---

## Overview

This skill produces REST API integration code that is production-grade by default — handling the failure modes that basic implementations miss: rate limiting, pagination, transient errors, and credential security. It works for any REST API regardless of provider.

## Instructions

When this skill activates, identify the API being integrated from the user's request. Ask for the API documentation link or relevant endpoint details if not provided. Never assume endpoint structure or authentication method — always confirm from documentation or user input.

**Authentication:** Always retrieve credentials from environment variables, never from hardcoded values. Use `os.getenv('API_KEY')` in Python or `process.env.API_KEY` in Node.js. At the start of the integration, check that the required environment variable is set and raise a clear error if it is not — do not fail silently at the first API call.

**Pagination:** Check the API documentation for the pagination style (cursor-based, page-number-based, or offset-based) and implement the full pagination loop. A function that returns only the first page of results without pagination is incomplete. Always include a `max_pages` safety limit defaulting to 100 to prevent infinite loops against APIs with unexpected pagination behaviour.

**Rate limiting:** Implement exponential backoff with jitter for 429 responses. Start at 1 second, double each retry, cap at 60 seconds, and add random jitter of plus or minus 20% to prevent thundering herd on concurrent requests. After 5 consecutive 429 responses, raise an exception rather than retrying indefinitely.

**Error handling:** Handle these HTTP status codes explicitly. For 400, log the request body and response for debugging. For 401, raise an authentication error pointing to the environment variable. For 403, raise a permissions error with the endpoint and required scope if available. For 404, return None or an empty result rather than an exception, unless the resource is expected to exist. For 429, apply rate limit backoff. For 500, 502, and 503, retry up to 3 times with backoff then raise.

**Logging:** Log every request at DEBUG level including method, URL, status code, and response time. Log retries at WARNING level. Log authentication failures at ERROR level. Never log the API key or any credentials at any log level.

## Example Structure
