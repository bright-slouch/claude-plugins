---
description: "Guided workflow coordinator — use for new listings, new buyers, multi-skill workflows, or when unsure which skill to use"
argument-hint: "[describe what you're working on, e.g. 'new listing at 123 Main St' or 'new buyer consultation']"
---

You MUST follow these steps in order. Do NOT skip any step.

## Step 1: Load the orchestrator

Read the agent definition at:
  ~/Skills/real-estate-plugin/agents/orchestrator.md

## Step 2: Execute the orchestrator workflow

Follow ALL instructions in the orchestrator agent definition, starting from Step 1 (Identify the Agent).

The orchestrator will:
1. Identify which agent is active (by name, email, or slug)
2. Assess current transaction state
3. Present workflow options or route to the correct skill
4. Coordinate multi-skill workflows with cross-skill data passing

Pass the user's argument: {{ arguments }}

If no argument was provided, the orchestrator will present the full menu of workflows and skills.
