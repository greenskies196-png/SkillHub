---
name: test-suite-generator
description: Generates comprehensive unit and integration tests for a given function or module. Use when the user asks to write tests, generate a test suite, add unit tests, test this function, or improve test coverage.
---

## Overview

This skill generates a complete test suite for a given function or module by systematically identifying and covering the happy path, edge cases, error conditions, and boundary values. The output follows the testing conventions of the language and framework in use.

## Instructions

When this skill activates, first identify the testing framework already in use in the project. Check for jest.config, vitest.config, pytest.ini, or equivalent configuration files. Use the existing framework — never introduce a new one without asking.

Identify the function or module to test from what the user has provided. Read its signature, return type, and body to understand its full behaviour surface.

Generate tests in this order. First, the happy path — the standard case with valid inputs that produces the expected output. Second, boundary values — the minimum and maximum valid inputs, empty strings, zero values, single-element arrays. Third, edge cases — null or undefined inputs, inputs of the wrong type, empty collections, very large inputs. Fourth, error conditions — inputs that should trigger exceptions, async failures, invalid state. Fifth, for async functions specifically — test both the resolved and rejected paths.

For each test, write a name that reads as a plain English sentence describing exactly what is being asserted. "should return null when user is not found" is a good test name. "test1" is not. Use the Arrange-Act-Assert pattern explicitly and leave a blank line between each section.

When mocking is required, mock at the boundary — the network call, the database query, the file system read. Do not mock internal helper functions unless there is a specific reason stated.

## Example

**Input:** A `getUserById(id: string): Promise<User | null>` function that queries a database.

**Output (Jest/TypeScript):**
