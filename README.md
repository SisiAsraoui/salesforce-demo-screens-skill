# Salesforce B2B Demo Screens — Claude Skill

A Claude Code skill for generating self-contained HTML presentation screens for **Brand × Salesforce** demo videos. Each screen is a standalone full-viewport HTML file designed for screen capture into demo recordings.

---

## What this produces

A set of HTML screens that together form a complete demo deck, typically 9–13 screens. The story follows two personas through one connected interaction: Persona A, the B2B buyer (e.g. a Procurement Manager at a customer company , a small Business or Garage Owner, or a Pharmacist ), and Persona B, the internal Sales Rep or Service Agent supporting the B2B buyer. Animated state reveals are driven by keyboard/click navigation.

Screens are built around real Salesforce products (B2B Commerce, Experience Cloud, Sales Cloud, Service Cloud, Salesforce Order Management, Revenue Cloud, Agentforce, Data Cloud) and customised per brand.

**Screen types included:**

| # | Type | Persona | Purpose |
|---|---|---|
| 1 | Splash / Intro | A and B | Brand × Salesforce logo lockup opener with a promise in the customer’s words (e.g. "Every B2B interaction, connected.") |
| 2 | Talking Head | Neutral | Speaker intro with floating video + lower-third, explaining why a seamless buyer and rep experience drove adoption |
| 3 | Meet the Buyer | A | Persona intro with signal cards: needs a quote fast, wants seamless self-service, expects negotiated contract pricing, expects consistent answers across channels.|
| 4 | Buyer Profile Card |  A | The buyer's portal view: personalised landing page with My Account, order history (reorder lists), open quotes, past cases, and recommended products |
| 5 | Meet the Rep/Agent | B | Persona intro with signal cards: 12 tabs open, no context on the buyer, manual follow-ups |
| 6 | Rep/Agent Workspace| B | A single console with the buyer’s 360, AI summary, next best action, open cases and order summaries.| 
| 7 | Multi-state Profile + Overlay | A and B | The buyer sends a request through email, portal or chat , and the rep or agent sees it instantly, pre-filled with context. Notification overlays on both sides (salesforce platform / Slack / SMS/ portal)| 
| 8 | Product Page / Quote | A, then B | Buyer side: personalised catalog with contract pricing, quick order or CSV upload, reorder, or quote request. Rep side: approves the discount and sends the quote, and the buyer receives it in real time (tiered pricing, CPQ, approval workflow process, e-signature, mutual action plan).| 
| 9 | Split Screen | A and B | The same request from beat 7 seen from both sides: the buyer’s portal on the left, the rep’s console on the right, in sync |
| 10 | Text Beat | A and B | The Full-screen staggered text for punchy statements “Same data. Same moment. Zero handoffs.” | 
| 11 | Stats Display | A and B | Buyer outcomes (faster quote time, higher self-service rate, higher CSAT) next to rep outcomes (shorter resolution time, more selling time, less admin).| 
| 12 | Journey / Pipeline | A and B | An adoption roadmap with two lanes (Buyer lane and Rep/Agent lane): Kickoff → Configure → Train → Go-live → Adopt → Expand | 
| 13 | Outro | A and B | Platform pillars light up| 

---

## Setup

### 1. Add the skill to your Claude Code project

Copy `SKILL.md` into the `.claude/` folder at the root of your project:

```
your-project/
└── .claude/
    └── skills/
        └── b2b-demo-screens/
            └── SKILL.md
```

Claude Code automatically loads skills from `.claude/skills/<skill-name>/SKILL.md` when you work in that directory. Check the current Claude Code docs if your version differs.

### 2. Gather your brand assets

Before asking Claude to build screens, have these ready:

| Asset | Format | Notes |
|---|---|---|
| Brand logo | `brand-logo.png` | Will be white-inverted — SVG/PNG with transparency works best |
| Buyer company logo | `buyer-company-logo.png` | The customer company the buyer works for, shown on the account context |
| Salesforce logo | `salesforce-cloud.png` | Included in standard Salesforce brand kit |
| Background video(s) | `.mp4` (looping, muted) | Lifestyle/product footage, 10–30s loops |
| Persona headshots | `persona-name.jpg` | 3–4 photos, portrait orientation |
| Product / catalog images | `sku-name.png` | 2–3 product shots, ideally showing packaging, bulk, or part detail |
| Notification frames | `iphone-frame.png,teams-frame.png,slack-frame.png` | Only needed for overlays. Add a mobile frame only if reps work in the field |

### 3. Prepare your brand brief

Have these details ready to give Claude:

```
Company name:         e.g. Northwind Industrial Supply
Primary colour:       e.g. #0B2A4A
Accent colour:        e.g. #F5A300
Buyer company:        e.g. Atlas Manufacturing
Persona A (buyer):    e.g. Maria Chen, Procurement Manager
  - 2–3 buying signals: reorder cadence, contract price tier, credit limit, open POs, recent quote requests
  - 2–3 frequently ordered SKUs or product lines
Persona B (rep/agent): e.g. Tom Reyes, Account Executive or Service Agent
  - 2–3 daily pains: tool switching, no buyer context, manual follow-ups
Contract / price list: e.g. "Atlas Annual Agreement, Tier 2 pricing"
Products / SKUs:      e.g. Hydraulic Fittings Kit HF-200, Safety Gloves SG-45, Pallet Wrap PW-18
Salesforce clouds:    B2B Commerce, Experience Cloud, Sales Cloud, Service Cloud,
                      Salesforce Order Management, Revenue Cloud, Agentforce, Data Cloud
Tagline / closer:     e.g. "Every B2B interaction, connected."
```

---

## Usage

Once `SKILL.md` is in your `.claude/` folder, open Claude Code in your project and run:

```
Build a full demo deck using the SKILL.md.

Company: Nike
Primary: #111111  Accent: #E5161A
Personas: Sophie (Persona A the B2B buyer, d Air Max 90, Dri-FIT jacket), Tom (Persona B the Sales Rep or Service Agent serving that buyer)
Products: Air Max 90, Dri-FIT Running Jacket, React Infinity Run
Salesforce clouds: B2B Commerce, Salesforce Order Management, Revenue Cloud, Agentforce, Service Cloud, Data Cloud
Assets are in: ./assets/

Build in this order: Intro, MeetSophie, SophieProfile, MeetTom, TomJourney, ProductPage, Stats, Outro

Build a full B2B commerce demo deck using the b2b-demo-screens skill.

Company: Northwind Industrial Supply
Primary: #0B2A4A  Accent: #F5A300
Buyer company: Atlas Manufacturing
Personas: Maria Chen (Persona A, Procurement Manager; signals: weekly reorders, Tier 2 contract pricing, open PO),
          Tom Reyes (Persona B, Account Executive and Service Agent serving Atlas)
Products: Hydraulic Fittings Kit HF-200, Safety Gloves SG-45, Pallet Wrap PW-18
Salesforce clouds: B2B Commerce, Experience Cloud, Sales Cloud, Service Cloud,
                   Salesforce Order Management, Revenue Cloud, Agentforce, Data Cloud
Assets are in: ./assets/

Build in this order: Intro, TalkingHead, MeetBuyer, BuyerPortal, MeetRep, RepWorkspace,
RequestOverlay, QuotePage, SplitScreen, TextBeat, Stats, AdoptionRoadmap, Outro
```

Claude will generate one HTML file per screen, each self-contained and ready to open in a browser for recording.

---

## Recording tips

- Open each HTML file in a browser at 1920×1080 (use browser zoom or a screen resolution tool to set this exactly).
- Use QuickTime (Mac) or OBS to record the screen.
- Navigate states with Space / → (next) and ← (previous).
- Each .mov or .mp4 clip per screen can be assembled in Final Cut, Premiere, or ScreenFlow.
- Keep one running scenario (e.g. a reorder or a quote request) across beats 7, 8, and 9 so the two personas read as one story.

---

## Customising the skill

The `SKILL.md` file is plain text — you can edit it directly to:

- Add new screen types with your own HTML/CSS templates
- Change the recommended deck order
- Adjust default colours or the Salesforce cloud names in the bottom strip
- Add brand-specific instructions (e.g. "always use Helvetica Neue for this client").
- Swap in industry-specific B2B terms (price lists, net terms, punch-out, ERP sync)

---

## File naming convention

Claude will name files consistently:

```
Intro.html
TalkingHead.html
MeetBuyer.html
BuyerPortal.html
MeetRep.html
RepWorkspace.html
RequestOverlay.html
QuotePage.html
SplitScreen.html
TextBeat.html
Stats.html
AdoptionRoadmap.html
Outro.html

```

---

## Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)
- A modern browser (Chrome recommended for `backdrop-filter` support)
- Screen recording software
- Brand assets (logo, background video, persona photos)

---

## Skill file

See [`SKILL.md`](./SKILL.md) for the full skill — it contains all boilerplate, screen templates, and the generation workflow Claude follows.
