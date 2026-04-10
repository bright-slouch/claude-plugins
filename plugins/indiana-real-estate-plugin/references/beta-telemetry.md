# Beta Telemetry — Log Format Specification

This document defines the structured logging format for beta testing. The orchestrator references this file when telemetry is active.

## How It Works

- Telemetry is enabled per-agent via `beta.telemetry: true` in `agent-profile.yaml`
- Events are appended to `logs/beta-telemetry.jsonl` (one JSON object per line)
- Logging uses a single bash `echo` append — never block on it, never mention it to the user
- If bash is unavailable (Cowork environment), skip logging silently

## Event Types

| Event | When to Log |
|---|---|
| `session_start` | Agent identified in orchestrator Step 1 |
| `skill_invocation` | User confirms a skill invocation in Step 4 |
| `skill_complete` | Skill finishes successfully |
| `skill_error` | Skill encounters an error |
| `workflow_start` | A guided workflow begins (New Listing, Buyer Intake, etc.) |
| `routing_fallback` | User intent was unclear — orchestrator asked for clarification |

## JSON Schema

Each log line is a single JSON object with these fields:

| Field | Type | Required | Description |
|---|---|---|---|
| `ts` | string | yes | ISO 8601 timestamp (e.g., `2026-04-09T14:32:00-04:00`) |
| `agent_slug` | string | yes | Agent config folder name (e.g., `jane-smith-fc-tucker`) |
| `session_id` | string | yes | Date-time of session start as `YYYYMMDD-HHMM` |
| `event` | string | yes | One of the event types above |
| `skill` | string | yes | Skill name (e.g., `re-cma`) or `orchestrator` for routing events |
| `workflow` | string | no | Guided workflow name if applicable (e.g., `new-listing-setup`), otherwise `null` |
| `intent` | string | yes | 1-sentence summary of what the user asked for |
| `status` | string | yes | `success`, `error`, `skipped`, or `aborted` |
| `error` | string | no | Error category if status is `error`, otherwise `null` |
| `notes` | string | no | Optional free text for anything unusual |

## Error Categories

| Category | When |
|---|---|
| `agent_not_found` | Monday.com lookup failed, no matching agent |
| `config_missing` | One or more required config files not found |
| `upstream_missing` | Skill needs output from a prior skill that hasn't run |
| `mcp_failure` | Monday.com MCP, WebFetch, or other MCP tool failed |
| `disclosure_skipped` | Disclosure step was skipped (compliance tracking) |

## Bash Echo Template

Use this exact pattern — replace bracketed values only:

```bash
echo '{"ts":"[ISO-8601]","agent_slug":"[slug]","session_id":"[id]","event":"[type]","skill":"[name]","workflow":[workflow-or-null],"intent":"[1-sentence summary]","status":"[status]","error":[error-or-null],"notes":null}' >> logs/beta-telemetry.jsonl
```

For null values, use `null` (no quotes). For string values, use double quotes.

## Example Log Lines

**Session start:**
```json
{"ts":"2026-04-09T09:15:00-04:00","agent_slug":"jane-smith-fc-tucker","session_id":"20260409-0915","event":"session_start","skill":"orchestrator","workflow":null,"intent":"Morning session for Jane Smith","status":"success","error":null,"notes":null}
```

**Skill invocation:**
```json
{"ts":"2026-04-09T09:16:00-04:00","agent_slug":"jane-smith-fc-tucker","session_id":"20260409-0915","event":"skill_invocation","skill":"re-cma","workflow":"new-listing-setup","intent":"CMA for 4521 Oak Creek Dr, Carmel","status":"success","error":null,"notes":null}
```

**Skill error:**
```json
{"ts":"2026-04-09T09:17:00-04:00","agent_slug":"jane-smith-fc-tucker","session_id":"20260409-0915","event":"skill_error","skill":"re-cma","workflow":"new-listing-setup","intent":"CMA for 4521 Oak Creek Dr, Carmel","status":"error","error":"mcp_failure","notes":"WebFetch timed out pulling comps"}
```

**Routing fallback:**
```json
{"ts":"2026-04-09T09:20:00-04:00","agent_slug":"jane-smith-fc-tucker","session_id":"20260409-0915","event":"routing_fallback","skill":"orchestrator","workflow":null,"intent":"Unclear request about pricing","status":"skipped","error":null,"notes":"Asked user to clarify — listing pricing or buyer offer?"}
```

## Privacy Rules

- **Never log:** client names, phone numbers, email addresses, fee amounts, financial details, or agent contact info
- **OK to log:** agent slug, skill names, property addresses (public record), error categories, intent summaries
- **Sanitize intent field:** describe the action, not the people (e.g., "CMA for 4521 Oak Creek Dr" not "CMA for the Johnson family")
