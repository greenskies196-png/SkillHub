---
name: session-learning-tracker
description: Captures errors, corrections, and discoveries during a session and writes them to a structured LEARNINGS.md file so future sessions can load and apply this knowledge. Use when a command fails unexpectedly, when the user corrects the agent, when a better approach is discovered, or when the user says "remember this for next time."
---

## Overview

This skill solves the problem of agents starting every session cold with no memory of what went wrong last time, what the user prefers, or what approaches have already been tried and failed. It maintains a LEARNINGS.md file in the project root that grows over time into a project-specific knowledge base the agent reads at the start of each session.

## Instructions

**When to write a learning:** Write to LEARNINGS.md any time one of these events occurs during a session. A command or operation fails unexpectedly and the cause is identified. The user corrects the agent with a phrase like "no, that's wrong" or "actually" or "that's not how we do it here." A better approach to a recurring task is discovered. An external tool or API behaves differently from how documentation suggests. A project-specific convention is established or clarified.

**How to write a learning:** Open LEARNINGS.md (create it if it does not exist) and append the new learning in this exact structure:
