# session-learning-tracker

Automatically captures errors, corrections, and discoveries during a session and writes them to a LEARNINGS.md file — so the next session starts informed rather than cold.

## What It Does

Every time something goes wrong, the user corrects the agent, or a better approach is discovered, this skill writes a structured entry to LEARNINGS.md in the project root. At the start of subsequent sessions, the agent reads this file and applies the accumulated knowledge proactively — without the user having to re-explain the same things.

Think of it as a project-specific memory layer that grows more useful over time. After a week of development on a project, LEARNINGS.md becomes a precise record of everything the agent has learned about that specific codebase, team preferences, and environment quirks.

## Compatible Agents

Verified working on Claude Code, OpenClaw, Codex CLI, Cursor, and Gemini CLI.

## Installation

Copy the `session-learning-tracker` folder into your agent's skills directory.

For Claude Code (project scope): `.claude/skills/session-learning-tracker/`
For Claude Code (global): `~/.claude/skills/session-learning-tracker/`
For OpenClaw: `.openclaw/skills/session-learning-tracker/`
For Cursor: `.cursor/skills/session-learning-tracker/`

## Dependencies

None. The skill writes plain markdown to the filesystem.

## Notes

Install this skill at the project scope rather than globally — each project's LEARNINGS.md is specific to that project. You can commit LEARNINGS.md to version control to share accumulated knowledge with teammates across the entire team.
