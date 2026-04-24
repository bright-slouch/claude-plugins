# Orchestrator — Quick Start Guide

## What the Orchestrator Does

The orchestrator is your primary entry point for the Central Indiana Real Estate Agent Plugin. Rather than picking a specific skill yourself, describe what you're working on and the orchestrator routes you to the right skill or walks you through a guided workflow.

**It handles:**
- Identifying which agent config to load (matches name/email against `config/*/agent-profile.yaml` files)
- Assessing where active transactions stand and what's needed next
- Running multi-step workflows where skills hand off data to each other
- Remembering session context so you don't repeat yourself

---

## Getting Started in 3 Steps

### Step 1: Identify yourself

Say your name, email, or config slug:

```
I'm working as Jane Smith
```
```
Working as jane-smith-fc-tucker
```
```
Set up for jsmith@fctucker.com
```

The orchestrator will load your config locally and confirm your identity, brokerage, and primary markets.

**First time? Don't have a config yet?**
```
I need to set up a new agent profile
```
The orchestrator will route you to `re-agent-setup`.

---

### Step 2: Describe what you're working on

You don't need to know which skill to use. Just describe the situation:

```
I have a listing appointment tomorrow at 8812 Maple Ridge Lane, Fishers
```
```
New buyer client — the Johnsons, looking in Hamilton County, budget $475K
```
```
We just got an offer on our Carmel listing — help me review it
```
```
Inspection came back with $18K of issues on the Westfield property — seller's side
```
```
We went under contract yesterday — April 30 close date
```

The orchestrator maps your description to the right skill or workflow.

---

### Step 3: Follow the prompts

The orchestrator confirms before running each skill:

```
I'm ready to run re-seller-consultation for 8812 Maple Ridge Lane.

This will:
- Generate a listing appointment prep package
- Create seller discovery questions
- Build a pricing conversation framework

Proceed? → Yes / Tell me more first / Actually I need something else
```

Say yes, and the skill runs with your agent config pre-loaded.

---

## Supported Workflows

### New Listing Setup (8 stages)
Takes a new listing from first appointment to active on MLS.

```
Start a new listing setup for [address]
```

Stages: Seller consultation → CMA → Listing prep → Disclosure review → MLS content → Marketing → Showings → Open house

### New Buyer Intake (7 stages)
From first buyer contact through offer accepted and into transaction management.

```
I have a new buyer client — [describe buyer]
```

Stages: Buyer consultation → Neighborhood research → Showing coordination → Offer writing → Negotiation → Transaction setup → Closing

### Offer Management
Write or review offers and prepare for negotiation.

```
[Buyer side] Write an offer for [buyer names] on [address]
[Seller side] Got an offer on [address] — help me review it
```

### Contract to Close
Set up and track a transaction from accepted offer through closing.

```
We went under contract on [address] — close date [date]
```

### Morning Briefing
Indiana real estate news + optional market snapshot.

```
Morning briefing for [agent name]
```

---

## Checking Session Status

At any point, ask:

```
What are we working on?
```

The orchestrator returns a summary of active transactions, skills run this session, and recommended next steps.

---

## Switching Between Tasks

You can move between transactions mid-session without losing context:

```
Let's switch to the Johnson buyer for a moment — they want to make an offer
```

The orchestrator keeps all active transaction contexts in memory and switches cleanly.

---

## Tips

**Be specific about the property and client.** The more context you give upfront, the less the orchestrator needs to ask:
- Good: "Listing appointment tomorrow at 8812 Maple Ridge, Fishers — seller expects $525K"
- Less good: "I need to prep for an appointment"

**Skip stages you've already done.** Every workflow stage has a "Skip (already done)" option. If you've already done the seller consultation, start at the CMA stage.

**Trust the data flow.** When skills share context, you won't be asked for information you already provided. The CMA will use your seller consultation data; the listing description will use the CMA price.

**Use plain language.** You don't need to know skill names. "Help me get ready for a buyer consultation" and "run re-buyer-consultation" both work.

---

## Common Quick Commands

| What you want | What to say |
|---|---|
| Start a new listing | "New listing at [address]" |
| New buyer client | "New buyer — [describe them]" |
| Picking up a transaction | "We're under contract on [address] — close date [date]" |
| Inspection issues | "Inspection came back with issues — [buyer/seller side]" |
| Market data | "Market update for [area/zip]" |
| Draft an email | "Draft [email type] for [client/situation]" |
| News | "Morning briefing" or "What's in the Indiana real estate news?" |
| Status check | "What are we working on?" |
| Switch agents | "Switch to working as [other agent name]" |
