# SPEC-DRIVEN-DEVELOPMENT — Why Specs Beat Prompts

English | [Bahasa Melayu](SPEC-DRIVEN-DEVELOPMENT.ms-MY.md) · Back to [README](README.md)

**Spec-driven development (SDD)** means writing down *what* to build — as structured Markdown documents — **before** building it, then treating those documents as the single source of truth that both you and the AI work from. [START.md](START.md) gets you to your first small spec; this guide explains why specs beat prompt-and-pray, and introduces the five spec files used in this toolkit.

---

## 1. Prompts evaporate. Specs persist.

Simple prompt engineering is a chat: describe what you want, iterate until it looks right, copy the result. It works — until the session ends. Then:

- the context is gone (new chat = explain everything again),
- nobody can review what was decided, or why,
- "done" means whatever looked right that day.

A spec is the same conversation, **written down and committed to git**. It is a prompt that never evaporates: every future session, agent, or teammate reads the same source of truth — and every change to it is a reviewable diff.

> Prompting doesn't disappear in SDD — it gets *smaller and sharper*, because the durable knowledge lives in the spec instead of the scrollback.

---

## 2. Why spec-driven wins

| | Simple prompt engineering | Spec-driven development |
|--|---------------------------|--------------------------|
| **Memory** | Lives in one chat; lost on a new session | Files in git — survive crashes, sessions, and handovers |
| **Reuse** | Re-paste and re-explain the context every time | Point the agent at the file once |
| **Consistency** | Same prompt, different output tomorrow | Fixed text; only deliberate edits change it |
| **"Done"** | Subjective — "looks right to me" | Acceptance criteria are checkable (GSD verifies against them) |
| **Scale** | One prompt can't hold a whole app | Specs split naturally into phases and milestones |
| **Review** | Decisions buried in scrollback | Decisions are diffable, commentable, revertable |
| **Fixing** | Another prompt gamble | Edit one section, commit, rebuild |

---

## 3. The five spec files

This toolkit splits the spec into five documents. Each answers one question:

| File | Answers | Feeds into |
|------|---------|------------|
| `BUSINESS-DESIGN-SPECIFICATION.md` | **Why** does this exist — and for whom? | Scope, the v1 cut, success metrics |
| `MARKETING-DESIGN-SPECIFICATION.md` | **How** will people find it — and care? | Landing page, launch, demo material |
| `DESIGN.md` | **What** will it look and feel like? | UI phases, visual consistency |
| `SOFTWARE-DESIGN-SPECIFICATION.md` | **What** must it do, exactly? | GSD requirements → phases → verification |
| `TECHNICAL-DESIGN-SPECIFICATION.md` | **How** will it be built? | Architecture, data model, deployment |

### BUSINESS-DESIGN-SPECIFICATION.md — the why

- Problem statement: who hurts, how much, how often
- Target users and segments
- Goals + success metrics (what "working" means for the business)
- Value proposition; pricing/revenue if any
- Constraints: budget, deadline, legal/compliance

*Decides what gets built at all — and what v1 is cut from.*

### MARKETING-DESIGN-SPECIFICATION.md — the reach

- Positioning: the one-liner and tagline
- Audience: where they are, what they respond to
- Channels + launch plan (social, WhatsApp, QR flyers…)
- Landing page copy outline; screenshots/demo assets

*Written before launch, it lets the AI build the landing page and store listing for you.*

### DESIGN.md — the look & feel

- Brand: name, logo, colours, fonts, tone of voice
- UX: user flows, screens, navigation map
- UI: components, layout rules, accessibility basics

*Keeps every GSD UI phase visually consistent — no re-deciding button styles each phase.*

### SOFTWARE-DESIGN-SPECIFICATION.md — the what

- Features as must-have / nice-to-have
- User stories with acceptance criteria
- Roles/permissions, edge cases, error states
- An explicit "out of scope" list

*The contract: GSD turns this into requirements → phases, and verifies the build against it.*

### TECHNICAL-DESIGN-SPECIFICATION.md — the how

- Architecture (a diagram or ASCII sketch is fine)
- Stack + why (framework, database, hosting)
- Data model, API endpoints, integrations
- Auth/security, environments, deployment, backups

*Answers the agent's implementation questions before they cost you tokens.*

---

## 4. Start with three

You don't need all five on day one. The minimum viable set for building:

1. **BUSINESS-DESIGN-SPECIFICATION.md** — so scope decisions have a why
2. **SOFTWARE-DESIGN-SPECIFICATION.md** — so GSD has something to build and verify
3. **TECHNICAL-DESIGN-SPECIFICATION.md** — so implementation choices aren't re-litigated

Add **DESIGN.md** before UI-heavy phases, and **MARKETING-DESIGN-SPECIFICATION.md** before launch. (Any three that match your next milestone are fine — the point is *written beats remembered*.)

---

## 5. Using them with OpenCode + GSD

1. **Draft them in a free AI chat** — interview mode (see [START.md](START.md)): let the AI ask you questions until each document is sharp.
2. **Save them at your project root** — the uppercase `.md` names above; they're plain files, versioned alongside your code.
3. **Feed them to GSD** — run `/gsd-new-project` in the project and point it at the specs; requirements become phases, phases become verified work.
4. **Keep them alive** — when reality teaches you something, edit the spec *first*, commit, then let GSD update the plan. The git history of your specs is your decision log.

---

**Next:** write your first spec with [START.md](START.md), set up the tools with [INSTALL.md](INSTALL.md), then build with [GSD.md](GSD.md). Back to [README](README.md).
