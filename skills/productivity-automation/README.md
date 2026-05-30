# Productivity Automation Skills

This category contains skills that automate the repetitive, low-creativity tasks that eat into a developer's day — the things that need to happen consistently but should not require active thought every time.

## What Belongs Here

A skill belongs in this category if its primary value is eliminating a recurring manual task from a developer's workflow. This includes skills for automating release processes, generating changelogs from commit history, setting up project scaffolding, running pre-flight checks before deployment, generating boilerplate configuration files, managing dependencies, and orchestrating multi-step workflows that combine several smaller tasks into one reliable sequence.

If the skill is primarily about writing or reviewing code itself, it belongs in Coding and Development. If it is about working with a specific document format, it belongs in Document Processing. The question to ask: is the core value of this skill that it removes something tedious and repetitive from the developer's plate? If yes, it belongs here.

## Why This Category Matters

Developer productivity is compounding. A skill that saves five minutes per day saves over twenty hours per year — and that is before accounting for the cognitive load reduction that comes from not having to think about routine tasks. The skills in this category target the highest-frequency, most predictable tasks in a typical development workflow because those are the ones where automation has the greatest return on investment.

## Quality Bar For This Category

Productivity automation skills must be reliable enough to run without supervision. A skill that works 80% of the time is worse than no skill at all for automation purposes, because the 20% failure rate creates unpredictable interruptions. Reviewers test automation skills for edge cases specifically — what happens when the input is empty, when a dependency is missing, when the environment is slightly different from what was expected. Skills that do not handle these cases gracefully will not pass review.

## Skills In This Category

| Skill | Description | Compatible With |
|---|---|---|
| `changelog-generator` | Generates a structured CHANGELOG.md from Git commit history using conventional commit format | Claude Code, Codex, OpenClaw, Cursor |
| `project-scaffolder` | Creates a complete project scaffold for common project types with correct folder structure, config files, and a working initial setup | Claude Code, Codex, OpenClaw, Cursor |
| `dependency-auditor` | Audits project dependencies for outdated packages, known vulnerabilities, and licence conflicts | Claude Code, Codex, OpenClaw, Cursor |

## Installing a Skill From This Category

Copy the skill folder into your agent's skills directory. For Claude Code and OpenClaw, use `.claude/skills/` or `.openclaw/skills/` inside your project, or `~/.claude/skills/` for global personal use.

## Submitting a Skill To This Category

Read the main [CONTRIBUTING.md](../../CONTRIBUTING.md) before submitting. Automation skills must include clear documentation of what the skill does when something goes wrong — failed commands, missing files, unexpected states. A skill with no error handling strategy will not pass review regardless of how well it works in the happy path.
