---
name: git-commit-formatter
description: Generates structured conventional commit messages by analysing staged diffs. Use when the user asks for help writing a commit message, asks to commit staged changes, mentions they want to commit, or has staged files ready to commit.
---

## Overview

This skill produces Git commit messages that follow the Conventional Commits specification (conventionalcommits.org). A conventional commit message has a type, an optional scope, and a short imperative summary — for example `feat(auth): add OAuth2 login flow`. This format makes commit history readable, enables automated changelog generation, and is the standard expected in professional open source and team projects.

## Instructions

When this skill activates, follow these steps in order.

**Step 1 — Read the staged diff.** Run `git diff --staged` to see exactly what has changed. If nothing is staged, inform the user and suggest they stage their changes with `git add` before proceeding.

**Step 2 — Identify the commit type.** Select the single most accurate type from this list:

- `feat` — a new feature or capability visible to users
- `fix` — a bug fix that corrects incorrect behaviour
- `docs` — changes to documentation only, no code changes
- `style` — formatting, whitespace, or code style changes with no logic impact
- `refactor` — code restructuring with no behaviour change and no bug fix
- `test` — adding or updating tests
- `chore` — maintenance tasks, dependency updates, build configuration
- `perf` — a change that improves performance
- `ci` — changes to CI/CD configuration or scripts

When in doubt between `feat` and `fix`, ask yourself: was the previous behaviour intentional? If yes, it is a `fix`. If no, it is a `feat`.

**Step 3 — Identify the scope (optional but recommended).** The scope is the area of the codebase most affected, written in parentheses after the type. Use the module name, component name, or layer (e.g. `auth`, `api`, `ui`, `db`). Omit the scope only if the change spans many unrelated areas with no clear primary scope.

**Step 4 — Write the subject line.** The subject line must be imperative mood, lowercase (except proper nouns), under 72 characters, and must not end with a period. Imperative mood means you write the verb as a command: "add login form" not "added login form" and not "adds login form". Think of it as completing the sentence "this commit will...".

**Step 5 — Write the body (when needed).** Add a body paragraph if the subject line alone does not explain the why behind the change. The body goes after a blank line following the subject. Explain the motivation and what changed conceptually — the diff already shows what changed technically, so do not repeat it.

**Step 6 — Add breaking change footer (when applicable).** If this commit introduces a breaking change, add a footer line: `BREAKING CHANGE: description of what breaks and how to migrate`.

**Step 7 — Present the commit message** inside a code block so the user can copy it directly. Then briefly explain your type and scope choice in one sentence so the user can correct you if you misread the diff.

## Examples

**Input:** A diff showing a new `sendPasswordResetEmail` function added to `src/services/auth.js`.

**Output:**
