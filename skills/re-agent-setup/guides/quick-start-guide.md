# Agent Setup: 5-Minute Quick Start Guide

## What You're Setting Up

Running `re-agent-setup` creates one thing:
- **Your personal config folder** at `config/[your-slug]/` — 7 YAML files that tell every skill who you are, how you communicate, where you work, and who you prefer to work with

Once set up, every other skill in the plugin automatically personalizes its output to your brand, voice, and market. There is no external registry — identity is entirely slug-based and lives locally under `config/`.

---

## Before You Start — Have These Ready

| Item | Why It's Needed |
|---|---|
| Indiana real estate license number | Appears in your bio, listing agreements, disclosures |
| MIBOR/BLC member ID | Used in MLS-related references |
| Brokerage name and office address | Used in all marketing and email signatures |
| Managing broker's name | Required in legal disclaimers |
| Your cell phone and email | Populates all client communication templates |
| 2-3 sentence professional bio | Or be ready to create one with the skill's help |

These are essential. Everything else can be added later.

---

## How the Conversation Works

The setup is a conversation, not a form. The skill asks one thing at a time. Here's the rough flow:

```
1. Identity and credentials          (~3 min)
   Name, license, brokerage, contact info, designations

2. Voice and tone                    (~2 min)
   How formal? How do you greet clients? Emoji or no emoji?

3. Your methodology                  (~3 min)
   How do you approach pricing? Buyer strategy? Communication cadence?

4. Market areas (~3 min)
   Counties, cities, school districts, primary focus areas, secondary coverage areas

5. Brand kit                         (~2 min)
   Colors, tagline, value proposition, hashtags

6. Vendor network                    (~5-10 min, or skip for later)
   Lenders (with NMLS), inspectors, photographers, stagers, contractors

7. Fee structure                     (~2 min, internal only)
   Commission rates for net sheet calculations — never shown to clients

8. Team structure                    (~2-5 min, or skip if solo)
   Team members, roles, TC contact

9. Review and save                   (~1 min)
   Confirm everything looks right, files are created
```

**Total time:** 20-30 minutes for a complete setup, 10-15 minutes if you skip vendor and team sections for now.

---

## What "TODO" Means

If you don't have something ready — a vendor's NMLS number, a specific brand color hex code, your exact commission rate — just say "I'll add that later" or "I don't know yet." The skill will put a `# TODO:` comment in the YAML file marking it as incomplete.

You can come back at any time and say:
```
Update my vendor network — I need to add a lender
```
or
```
I want to fill in my fee structure now
```

**Nothing breaks if sections are incomplete.** Skills will just ask you for that information when they need it.

---

## Your Config Slug

The skill generates a unique identifier called a **slug** from your name and brokerage:

- Sarah Chen at F.C. Tucker → `sarah-chen-fc-tucker`
- Marcus Williams at Keller Williams Indy Metro North → `marcus-williams-kw-indy-metro-n`

This slug is:
- Used as your folder name (`config/sarah-chen-fc-tucker/`)
- How you identify yourself to any skill (`"Working as sarah-chen-fc-tucker"`)

You can also just say your name — the skill will match it against the `name.full` field in each `config/*/agent-profile.yaml` and find your slug automatically.

---

## After Setup: What to Try First

Once your profile is created, these are great first runs:

**Get your daily briefing:**
```
/re-news-briefing
```
Fetches today's Indiana real estate news, personalized to your market areas.

**Get a market snapshot:**
```
/re-market-update — Hamilton County, current month
```

**Prepare for a listing appointment:**
```
/re-seller-consultation — 4521 Oak Creek Dr, Carmel, 4 bed/2.5 bath
```

**Draft an email to a client:**
```
/re-client-communication — email to my buyer Raj Patel confirming we go under contract tomorrow
```

---

## Updating Your Config Later

Everything is easy to update:

| Change | Command |
|---|---|
| New vendor | "Add [name] to my vendor network as a [type]" |
| New team member | "Add [name] to my team as [role]" |
| Changed brokerage | "I'm switching to [new brokerage] — update my profile" |
| New market area | "Add [city/neighborhood] to my market areas" |
| Revised bio | "Let's update my bio — I want to mention my GRI designation" |
| Updated fee structure | "Update my fee structure — I'm changing my commission to [X]%" |

The skill updates only the relevant YAML file and leaves everything else intact.

---

## Privacy Note

Your fee structure (`fee-structure.yaml`) is **never included in client-facing output**. It is used exclusively by the skills for internal calculations (net sheets, cost estimates). The file is stored locally in your config folder and is not shared externally.
