---
description: "Set up your agent profile (alias for /re-agent-setup)"
argument-hint: "[agent-name or 'new']"
---

This is an alias for /re-agent-setup.

You MUST follow these steps in order. Do NOT skip any step.

## Step 1: Load the skill

Read the SKILL.md file at:
  ~/Skills/real-estate-plugin/skills/re-agent-setup/SKILL.md

## Step 2: Execute the skill

Follow ALL instructions in SKILL.md from the beginning.
This skill does NOT require an existing agent config — it creates one.

Pass the user’s argument: {{ arguments }}

If no argument was provided, ask the user for the agent’s name to get started.
