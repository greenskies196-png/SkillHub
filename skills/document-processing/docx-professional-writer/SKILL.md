---
name: docx-professional-writer
description: Creates professionally formatted Word documents (.docx) with correct heading styles, tables, and page layout using python-docx. Use when the user asks to create a Word document, generate a .docx file, write a report, or produce any document that needs to open correctly in Microsoft Word.
---

## Overview

This skill produces Word documents that open correctly in Microsoft Word, Google Docs, and LibreOffice — with proper heading hierarchy, consistent paragraph styles, and correctly structured tables. It uses python-docx exclusively. It does not use pandoc or markdown conversion, because those approaches produce inconsistent styling across environments.

## Instructions

When this skill activates, gather the document content and structure from the user's request before writing any code.

Always apply Word's built-in named styles rather than manual formatting. Use `Heading 1`, `Heading 2`, `Heading 3` for structure, `Normal` for body text, `List Bullet` and `List Number` for lists, and `Table Grid` or `Light Shading` for table styles. Never apply bold, font size, or colour directly to paragraphs — this creates visual formatting that breaks when the document theme changes.

For tables, always set the column widths explicitly using `Inches()` values. A table without explicit column widths will render inconsistently across different versions of Word. Use `table.style = 'Table Grid'` for bordered tables and `table.style = 'Light Shading Accent 1'` for header-row tables.

For page layout, set margins using `sections[0].left_margin` and related properties. Standard professional margins are 1 inch (914400 EMUs) on all sides unless the user specifies otherwise.

Always add a document title using the `Title` paragraph style as the first element. Never use `Heading 1` for the document title — reserve `Heading 1` for major sections within the document body.

Save the file to the path specified by the user. If no path is specified, save to the current working directory with a descriptive filename derived from the document title.

## Example
