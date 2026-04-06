# re-agent-setup: Example Prompts

---

## Scenario 1: New Solo Agent at F.C. Tucker

**Context:** Sarah Chen just got her Indiana real estate license and is joining F.C. Tucker's Carmel office. She's starting from scratch and needs a complete profile.

**Prompt:**
```
Set up a new agent profile for me. I just got licensed in Indiana and I'm joining F.C. Tucker's Carmel office. My name is Sarah Chen.
```

**What happens:**
The skill welcomes Sarah, generates her slug (`sarah-chen-fc-tucker`), and begins gathering identity info. It asks for her license number, managing broker, contact info, and then moves through each config section. Because she's new, she may not have a vendor list yet — the skill accepts "I'll add that later" and uses TODO comments. It drafts a bio for her based on her background and asks for refinement. At the end, it creates all 7 config files and adds her row to Monday.com with Config Status = "Partial" (since vendor network is incomplete).

---

## Scenario 2: Experienced Team Lead at Keller Williams

**Context:** Marcus Williams is a 12-year REALTOR® at Keller Williams Indy Metro North, leading a team of 4 agents plus a TC. He has a full vendor network, strong brand, and multiple farm areas in Hamilton County.

**Prompt:**
```
Set up the plugin for Marcus Williams at KW Indy Metro North. He's a team leader with 4 agents and a TC. His focus areas are Carmel, Fishers, and Noblesville.
```

**What happens:**
The skill generates slug (`marcus-williams-kw-indy-metro-n`) and immediately asks if this is team leader Marcus or if a team member is setting this up on his behalf. It gathers his extensive credential and experience data efficiently (using numbered prompts for things like designations and farm areas). The team-structure section gets full attention — it captures all 4 agents' names, roles, and responsibilities, plus the TC's contact info. Fee structure section includes team splits. Config Status = "Setup Complete" because all sections are filled.

---

## Scenario 3: Brand New Agent Who Needs Everything

**Context:** Tyler Okonkwo just passed his Indiana exam and starts Monday at RE/MAX Advanced Realty. He has no vendor relationships, no bio, no brand, and doesn't know what half of the questions mean.

**Prompt:**
```
I just got my real estate license and I'm starting at RE/MAX Advanced Realty next week. Help me set up my profile. I'm a complete beginner and I'm not sure what I'll need.
```

**What happens:**
The skill adopts a more educational tone. It explains each section briefly before asking questions ("The next thing we'll set up is your vendor network — these are the service providers you refer to clients..."). It recognizes when Tyler doesn't know something and handles it gracefully: "No problem — we'll mark that as a TODO for now. Your managing broker can help you identify preferred vendors." It drafts Tyler's bio from scratch using his background information. All vendor sections are marked TODO. Fee structure uses brokerage standard language (which the skill explains he'll get from his managing broker). Config Status = "Partial."

---

## Scenario 4: Agent Updating Their Vendor List

**Context:** Jennifer Hartley has been in the plugin for 6 months. Her preferred inspector retired and she's adding two new lenders to her network.

**Prompt:**
```
Update the vendor network for jennifer-hartley-c21-scheetz. I need to add two new lenders and replace my inspector.
```

**What happens:**
The skill loads the existing `vendor-network.yaml` for Jennifer's config and displays the current vendor list. It asks specifically about the retiring inspector (confirm removal or archive?) and then gathers the two new lenders' details — name, company, phone, email, NMLS number, specialty. It also asks whether either new lender should be marked as the primary recommendation. It updates only `vendor-network.yaml`, leaving all other config files unchanged. No new Monday.com row is created (Jennifer is already in the registry).

---

## Scenario 5: Agent Switching Brokerages

**Context:** David Park is moving from Compass to CENTURY 21 Scheetz. His slug will change and his brokerage disclaimer text needs to update across all config files.

**Prompt:**
```
David Park is switching to CENTURY 21 Scheetz from Compass. We need to update his profile. His old slug was david-park-compass.
```

**What happens:**
The skill loads David's existing config and flags that a brokerage change requires updates across multiple files (agent-profile.yaml, brand-kit.yaml, email-templates.yaml signature block). It asks for the new brokerage office details, managing broker name, and new contact email. It generates a new slug (`david-park-c21-scheetz`) and asks: "Should I create a new config at the new slug, or update in place at the old slug?" (New slug is recommended.) It updates Monday.com to reflect the new brokerage and new slug, archiving the old entry or updating it. Fee structure section is flagged for review since commissions often change with brokerage. Config Status reset to "Partial" until fee structure is confirmed.

---

## Scenario 6: Agent Adding a Team Member

**Context:** Lisa Morales is an established solo agent who just hired a showing assistant and is considering bringing on a buyer's agent. She wants to add both to her team config.

**Prompt:**
```
I need to add a showing assistant to my team structure. Her name is Brooke Tanner and she just got licensed. I might also be adding a buyer's agent next month.
```

**What happens:**
The skill loads Lisa's existing `team-structure.yaml`. It confirms the current `enabled: false` setting and asks if Lisa wants to formally set up as a team now. If yes, it captures:
- Team name (optional)
- Brooke Tanner's full details: license number (required for showing licensed properties), phone, email, what she handles
- Whether Lisa wants to note the future buyer's agent as a TODO placeholder

The skill updates only `team-structure.yaml` and sets `enabled: true`. It reminds Lisa that her managing broker should be looped in on the team structure for brokerage policy compliance. Config Status updated to reflect the new team section is complete.
