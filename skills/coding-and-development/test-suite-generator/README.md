# test-suite-generator

Generates a complete, methodical test suite for any function or module — covering the happy path, boundary values, edge cases, and error conditions in one pass.

## What It Does

When you ask your agent to write tests for a function, this skill activates. It detects your existing test framework (Jest, Vitest, pytest, etc.), reads the function signature and body, and generates tests that cover every meaningful behaviour the function can exhibit. Each test follows the Arrange-Act-Assert pattern with a descriptive name that reads as a plain English sentence.

## Compatible Agents

Verified working on Claude Code, OpenClaw, Codex CLI, Cursor, and Gemini CLI.

## Installation

Copy the `test-suite-generator` folder into your agent's skills directory.

For Claude Code (project scope): `.claude/skills/test-suite-generator/`
For Claude Code (global): `~/.claude/skills/test-suite-generator/`
For OpenClaw: `.openclaw/skills/test-suite-generator/`
For Cursor: `.cursor/skills/test-suite-generator/`

## Dependencies

None beyond whatever test framework is already installed in your project.

## Example

**You say:** "Write tests for this function"

**Agent produces:**
