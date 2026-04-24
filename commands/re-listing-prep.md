---
description: "Property prep guidance — staging, repairs (ROI-ranked), photography shot list"
argument-hint: "[property address + brief property description]"
---

You MUST follow these steps in order. Do NOT skip any step.

## Step 1: Resolve the agent

Determine which agent is active using one of these methods (try in order):

1. If the user provided an agent slug as part of their argument, use that slug directly.
2. If a previous turn in this session already identified the agent, reuse that slug.
3. If the user’s full name or email is available in the conversation context, try to match it against existing local configs:
   - Use Glob to list `~/Skills/real-estate-plugin/config/*/agent-profile.yaml`
   - Use Grep to search each file for the name (under `name.full`) or email (under `contact.email_primary`)
   - If exactly one match is found, use that slug

If an agent slug is resolved, load the config files from:
  ~/Skills/real-estate-plugin/config/[slug]/agent-profile.yaml

**Legacy field migration:** when loading `market-areas.yaml` for this agent, if the file still uses the old keys `farm_areas:` or `secondary_areas:`, treat them as `primary_focus_areas:` and `secondary_coverage_areas:` respectively. Rename the keys in-place the next time you edit the file and mention the one-line upgrade to the user.

If the agent CANNOT be resolved by any of the above methods, respond with EXACTLY this message and then STOP (do not proceed to Step 2):

---
I’d be happy to help with that! First, I need to know which agent profile to use.

Please provide one of the following:
- Your **config slug** (e.g., `jane-smith-fc-tucker`)
- Your **full name** as it appears in your agent profile
- Your **email address**

Or if you haven’t set up your profile yet, run **/re-agent-setup** to get started (takes about 15–20 minutes).
---

## Step 2: Load and execute the skill

Read the SKILL.md file at:
  ~/Skills/real-estate-plugin/skills/re-listing-prep/SKILL.md

Then follow ALL instructions in SKILL.md starting from **Step 2** onward (skip SKILL.md’s Step 1 since agent config was already resolved above).

Pass the user’s argument: {{ arguments }}
