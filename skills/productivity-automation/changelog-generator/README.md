# changelog-generator

Generates a complete, properly formatted CHANGELOG.md from your Git commit history — categorising changes automatically from Conventional Commits types and rewriting developer shorthand into plain English for a user-facing document.

## What It Does

When you ask your agent to generate or update a changelog, this skill activates. It reads your Git log, categorises commits into the standard Keep a Changelog sections (Added, Fixed, Changed, Security, Removed, Deprecated), ignores internal-only changes like test and CI commits, and rewrites terse commit messages into plain English that non-developers can read. It always shows you the output for review before writing the file to disk.

## Compatible Agents

Verified working on Claude Code, OpenClaw, Codex CLI, Cursor, and Gemini CLI.

## Installation

Copy the `changelog-generator` folder into your agent's skills directory.

For Claude Code (project scope): `.claude/skills/changelog-generator/`
For Claude Code (global): `~/.claude/skills/changelog-generator/`
For OpenClaw: `.openclaw/skills/changelog-generator/`
For Cursor: `.cursor/skills/changelog-generator/`

## Dependencies

None beyond Git. Must be run inside a Git repository.

## Example

**You say:** "Generate a changelog for the v2.0 release"

**Agent produces** a fully formatted CHANGELOG.md with an Unreleased section at the top, a v2.0 section below it grouping commits into Added, Fixed, and Changed, and all commit messages rewritten from developer shorthand into plain sentences a product manager or end user can read. It presents the output for your review before writing the file.

## Notes

Works best with Conventional Commits-formatted history but also handles less structured commit messages by inferring category from content. You can ask for a specific version range or the full history going back to the first commit.
