---
name: code-reviewer
description: Reviews code for bugs, security vulnerabilities, and style violations, organising findings by severity. Use when the user asks to review code, check a file for issues, audit a function, inspect a pull request diff, or asks "what's wrong with this code."
---

## Overview

This skill performs a structured code review that organises findings into three severity tiers — Critical, Warning, and Suggestion — so the developer can prioritise fixes efficiently. The review covers correctness bugs, security vulnerabilities, performance problems, and code style issues in a single pass.

## Instructions

When this skill activates, follow these steps in order.

**Step 1 — Establish scope.** Identify what code is being reviewed. If the user has pointed to a specific file or function, review that. If they have pasted code directly, review the pasted content. If they have asked for a review without specifying what, ask: "Which file or function would you like me to review?"

**Step 2 — Perform the review across four dimensions:**

*Correctness* — Look for logic errors, off-by-one errors, null or undefined access without guards, incorrect type assumptions, unreachable code, and missing return values in code paths that require them.

*Security* — Look for SQL injection, command injection, cross-site scripting (XSS), insecure direct object references, hardcoded credentials, missing input validation, use of cryptographically weak algorithms (MD5, SHA1 for passwords), and improper error handling that leaks stack traces or sensitive data.

*Performance* — Look for N+1 query patterns, unnecessary loops inside loops, synchronous blocking calls in async contexts, unbounded data loading, and missing indexes implied by the query patterns.

*Style and maintainability* — Look for functions that are doing too many things (over 30 lines is a signal, not a rule), unclear variable names, missing error handling for operations that can fail, and code that is harder to read than it needs to be.

**Step 3 — Organise findings by severity.** Use exactly this structure:

### 🔴 Critical
Issues that could cause data loss, security breaches, or application crashes.

### 🟡 Warning
Issues that will likely cause bugs or performance problems under real conditions.

### 🔵 Suggestion
Improvements to readability, maintainability, or style that do not affect correctness.

### ✅ What Works Well
One to three things the code does well. Always include this section.

**Step 4 — For each Critical finding, provide a corrected code snippet** showing exactly how to fix the issue. For Warnings, provide a corrected snippet when the fix is non-obvious. For Suggestions, a brief description of the improvement is sufficient.

**Step 5 — Provide a one-paragraph summary** of the overall code quality and the single most important thing to fix first.

## Example

**Input:** A JavaScript function that queries a database using string concatenation with user input.

**Critical finding output:**

### 🔴 Critical
- Line 12: SQL injection vulnerability. User input is concatenated directly into the query string without sanitisation. An attacker can manipulate the query to access or destroy arbitrary data.

Fix:
