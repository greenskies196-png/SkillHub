---
name: typescript-jsdoc-generator
description: Generates complete JSDoc comments for TypeScript functions, classes, and interfaces. Use when the user asks to document code, add JSDoc, generate comments for TypeScript, or asks "document this function."
---

## Overview

This skill generates accurate, complete JSDoc comments for TypeScript code by reading the type signatures, parameter names, return types, and function body to infer correct documentation. The output integrates cleanly with TypeScript's type system and works with documentation generators like TypeDoc and JSDoc.

## Instructions

When this skill activates, read the TypeScript code the user has provided or pointed to. For each function, class, or interface that needs documentation, generate a JSDoc block placed immediately above the definition.

For functions and methods, always include: a one-sentence summary in the first line describing what the function does (not how it does it), a `@param` tag for every parameter with its type and a description of its purpose, a `@returns` tag describing what is returned and under what conditions, a `@throws` tag for every exception the function can throw, and an `@example` block showing a concrete, runnable usage example.

For classes, include a summary of the class's purpose and responsibility, `@param` tags for constructor parameters, and an `@example` showing instantiation and a typical method call.

For interfaces and type aliases, include a summary of what the type represents and a `@property` description for each field.

Write descriptions from the user's perspective — describe what the function accomplishes, not the internal implementation details. "Fetches user data from the database by ID" is a good description. "Calls db.query with a SELECT statement" is not — that is the implementation, not the behaviour.

When a parameter has a complex type, add a sentence explaining the expected shape even if TypeScript already captures it — the JSDoc is also documentation for humans reading the code in a browser or generated documentation site.

## Example

**Input:**
