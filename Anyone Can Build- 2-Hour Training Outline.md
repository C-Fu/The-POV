# Anyone Can Build: From Problem to App — 2-Hour Training Outline

**Duration:** 120 minutes
**Format:** Short talks + one live build + hands-on exercises
**Audience:** Non-developers / beginners who want to build working apps with AI

---

## Agenda at a Glance

| # | Clock | Min | Segment |
|---|-------|-----|---------|
| 1 | 00:00 | 8 | Welcome + hook: show the finished result first |
| 2 | 00:08 | 8 | Why anyone can build now (AI vs traditional org, FDE) |
| 3 | 00:16 | 18 | **Topic 1:** Everyday problems → app ideas (exercise) |
| 4 | 00:34 | 14 | **Topic 2:** Fact-finding & research — asking relevant questions |
| 5 | 00:48 | 15 | **Topic 3:** Plan the app — features, user flow, requirements |
| 6 | 01:03 | 5 | Break |
| 7 | 01:08 | 25 | **Topic 4:** Build with free AI tools — LIVE build |
| 8 | 01:33 | 12 | **Topic 5:** Test, troubleshoot, improve (live) |
| 9 | 01:45 | 8 | **Topic 6:** Prototype → practical working solution |
| 10 | 01:53 | 7 | **Topic 7:** Apply it everywhere + recap + Q&A |

**Total: 120 min.** Questions are taken throughout; a "parking lot" list is kept for the final 7 minutes.

---

## Segment Details

### 1. Welcome + Hook (8 min)
- Show a **finished example app first** — the payoff before the process.
- One-sentence promise: "By the end, you'll know the exact path from a problem you have to an app that works."
- Ground rules: no coding experience needed; ask questions any time.

### 2. Why Anyone Can Build Now (8 min)
- **AI vs Traditional organization** (use the mermaid diagram: CEO → Engineering/Design/PM/Research vs CEO → Prototypers/Builders/Sweepers/Growers/Maintainers).
- Key message: the team of one is now a team of many — AI collapses roles.
- **Forward Deployed Engineer** as the real-world version of this: someone who goes to the problem and ships the solution.
- Transition: "So what does that workflow actually look like? Let's do it."

### 3. Topic 1 — Everyday Problems → App Ideas (18 min)
- Method: notice friction → name the problem → picture the smallest app that removes it.
- Red flags: ideas that need a big team, network effects, or months of work. Reject them today.
- **Exercise (8 min):** each person writes ONE everyday problem + a one-line "the app would ___" statement. Pair-share.
- Recap 2–3 audience examples aloud.

### 4. Topic 2 — Fact-Finding & Research (14 min)
- Who has the problem? What do they do today? What would "solved" look like?
- **Asking relevant questions** — the core skill. Teach the pattern:
  - Ask the AI to interview *you* about the problem before it builds anything.
  - Good prompt: "Ask me the questions you need answered before designing a solution."
  - Feed answers from real users / coworkers / records — not guesses.
- Output of this stage: a short problem brief (user, pain, current workaround, success criteria).

### 5. Topic 3 — Plan the App (15 min)
- **Features:** must-have vs nice-to-have. Cut to 3–5 for v1.
- **User flow:** sketch the path — open → do the one core thing → done. (Simple arrow diagram, like the mermaid style.)
- **Requirements:** plain-language list the AI can build from ("must work on phone", "data must survive refresh", etc.).
- **Exercise (7 min):** write the 3 must-have features + a 4-step user flow for their idea.
- This plan is what gets handed to the AI in the next segment.

### 6. Break (5 min)

### 7. Topic 4 — Build With Free AI Tools — LIVE (25 min)
- **The stack:** OpenCode (AI coding agent), GSD (structured workflow), OpenChamber, Tailscale (access anywhere).
- **MCP = giving the AI hands.** Show 1–2 wow moments:
  - Playwright MCP: browser does a Google image search and drops results into Excel.
  - Blender MCP: AI drives a desktop app directly.
  - Point: tools aren't chatbots — they *do things*.
- **Live build:** take the planning output from Segment 5 and build it in front of the audience.
- **CARA JIMAT TOKEN (token-saving tips):** scope small, reuse the plan, avoid re-explaining context, break work into steps.
- Audience tracks along on their own machine if set up; otherwise watches.

### 8. Topic 5 — Test, Troubleshoot, Improve (12 min)
- Test against the plan: does each must-have feature actually work?
- Loop: run it → spot the break → describe it plainly to the AI → re-test.
- Show a real (or staged) failure and fix it live — troubleshooting is the skill, not avoiding errors.
- Quick win: one round of audience-requested improvement on the spot.

### 9. Topic 6 — Prototype → Practical Solution (8 min)
- Prototype proves the idea; a working solution needs: real data, a way for others to open it, and a habit of fixing what breaks.
- Path: deploy/share (Tailscale for private access), hand it to one real user, keep a short fix list.
- Expect v1 to be ugly and useful — that's success.

### 10. Topic 7 — Apply It Everywhere + Recap + Q&A (7 min)
- Same loop for: **personal** (household/admin tasks), **workplace** (reports, trackers, internal tools), **business** (customer-facing small tools).
- Recap the loop in one line: **Problem → Research → Plan → Build → Test → Ship → Repeat.**
- Q&A from the parking lot; point to resources and next session.

---

## Pre-Session Checklist

- [ ] Fix the 3 broken image paths in the source deck (currently point to `C:/Users/C-Fu/AppData/Roaming/marktext/images/` — copy images into this repo).
- [ ] Re-export the HTML deck after fixing (current export also has encoding damage).
- [ ] Verify live-build environment: OpenCode installed, MCP servers connected (Playwright MCP, Blender MCP), demo project ready.
- [ ] Prepare a pre-built fallback version of the demo app in case live build fails.
- [ ] Dry-run the MCP wow-demo (image search → Excel) so it's reliable.
- [ ] Print/prepare exercise sheets for Segments 3 and 5.

## Appendix / Backup Material

- **Design Language vs Design System vs Brand Ecosystem** — hold for Q&A; too deep for the main 2 hours unless the audience asks.
- Extra MCP examples if time opens up.
- Alternate org-chart examples if the mermaid diagram stalls.
