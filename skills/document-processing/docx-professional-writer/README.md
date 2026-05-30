# docx-professional-writer

Creates Word documents (.docx) that open correctly in Microsoft Word, Google Docs, and LibreOffice — with proper heading hierarchy, consistent paragraph styles, and correctly structured tables.

## What It Does

When you ask your agent to create a Word document or .docx file, this skill activates. It uses python-docx with Word's built-in named styles rather than raw formatting, so documents look professional and remain fully editable. Tables get explicit column widths so they render consistently across Word versions. Page margins are set correctly. The distinction between a document title and section headings is handled properly — a detail that trips up most agents without this skill.

## Compatible Agents

Verified working on Claude Code, OpenClaw, Codex CLI, Cursor, and Gemini CLI.

## Installation

Copy the `docx-professional-writer` folder into your agent's skills directory.

For Claude Code (project scope): `.claude/skills/docx-professional-writer/`
For Claude Code (global): `~/.claude/skills/docx-professional-writer/`
For OpenClaw: `.openclaw/skills/docx-professional-writer/`
For Cursor: `.cursor/skills/docx-professional-writer/`

## Dependencies

Install python-docx with `pip install python-docx`.

## Example

**You say:** "Create a Word document with a title, an executive summary section, and a table showing regional sales figures"

**Agent produces a .docx file with:**

- A title rendered in Word's built-in Title style
- An Executive Summary heading in Heading 1 style
- A three-column table with explicit column widths and Light Shading Accent 1 styling
- All content correctly linked to named styles so the document updates cleanly when the theme changes

## Notes

This skill intentionally avoids pandoc and markdown-to-docx conversion pipelines because they produce inconsistent heading styles across environments. The skill generates python-docx code directly, giving you full structural control over the output. If you need to convert an existing markdown document to Word, this skill will rewrite it using proper python-docx calls rather than piping it through a converter.
