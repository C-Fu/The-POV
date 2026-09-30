# GSD — Workflow Quickstart

English | [Bahasa Melayu](GSD.ms-MY.md) · Back to [README](README.md)

**GSD (Get Shit Done)** is a spec-driven development workflow that runs inside [OpenCode](INSTALL.md). You describe the outcome; GSD researches, plans, builds, and verifies — with you approving at the right moments.

---

## How It Works

The full journey from "I have an idea" to "it's shipped" — six steps:

### 1. Create the project

```text
/gsd-new-project
```

One guided flow: Questions → Research (parallel agents) → Requirements (v1 / v2 / out of scope) → Roadmap (phases). It creates `PROJECT.md`, `REQUIREMENTS.md`, `ROADMAP.md`, `STATE.md`, and `.planning/research/`.

Already have code? Run `/gsd-map-codebase` first so GSD understands what exists.

### 2. Discuss the phase

```text
/gsd-discuss-phase 1
```

Captures your implementation preferences **before** planning. GSD identifies the gray areas for your phase type — visual (layout, density, interactions), APIs (response format, flags), content (structure, tone), or organizational (grouping, naming) — and asks about them. Creates `{phase}-CONTEXT.md`.

### 3. Plan the phase

```text
/gsd-plan-phase 1
```

Researches your codebase and ecosystem (guided by `CONTEXT.md`), then creates 2–3 atomic task plans as structured XML, verifying each plan against the requirements in a loop. Creates `{phase}-RESEARCH.md` and `{phase}-{N}-PLAN.md`. Every plan is small enough to execute in a fresh context window.

### 4. Execute the phase

```text
/gsd-execute-phase 1
```

Runs the plans in dependency-ordered waves — independent plans run in parallel, dependent ones sequentially. Each plan runs in fresh context, each task gets an atomic Git commit, and results are verified against the plan's goals. Creates `{phase_num}-{N}-SUMMARY.md` and `{phase_num}-VERIFICATION.md`.

### 5. Verify the work

```text
/gsd-verify-work 1
```

User acceptance testing: GSD extracts the testable deliverables and walks you through them one by one, auto-diagnoses anything that fails, and creates fix plans. Creates `{phase}-UAT.md`.

### 6. Repeat and complete

```text
/gsd-complete-milestone
```

Repeat discuss → plan → execute → verify for each phase. When the milestone is done, `/gsd-complete-milestone` archives the work and tags the release; use `/gsd-new-milestone` to start the next version.

---

## Quick mode

```text
/gsd-quick
```

For ad-hoc tasks that don't need a whole phase — with the same planner + executor quality, but skipping research/checker/verifier steps. Quick tasks are tracked in `.planning/quick/`, not in phases.

Use it for: bug fixes, small features, config changes, one-off tasks.

---

## Why It Works

### Context Engineering

GSD keeps quality high by giving OpenCode exactly the context it needs — and nothing more:

- `PROJECT.md` — the vision, always loaded.
- `research/` — ecosystem knowledge gathered up front.
- `REQUIREMENTS.md` — scoped v1/v2, so scope creep is visible.
- `ROADMAP.md` — where you're going and what's done.
- `STATE.md` — decisions, blockers, and memory across sessions.
- `PLAN.md` — one atomic task with verification.
- `SUMMARY.md` — what happened, for the next agent.
- `todos/` — captured ideas waiting for a slot.

Every file has a size limit, based on where OpenCode's quality measurably degrades.

### XML Prompt Formatting

Every plan is structured XML with `name`, `files`, `action`, `verify`, and `done` fields. That means precise instructions instead of vibes, no guessing, and verification built into every task.

### Multi-Agent Orchestration

A thin orchestrator spawns specialized subagents: 4 parallel researchers, a planner + checker loop, parallel executors each with a fresh 200k context, then a verifier and debuggers. Because the real work happens in fresh subagent contexts, your main context stays at 30–40% full.

### Atomic Git Commits

Every task is committed immediately with its own commit. `git bisect` finds the exact failing task, any task can be reverted independently, and the history reads clearly.

### Modular by Design

Add phases when you need them, insert urgent work between phases, complete milestones, and adjust plans — without rebuilding anything.

---

## What's next

Install the toolchain first? Follow [INSTALL.md](INSTALL.md) — then come back and run `/gsd-new-project`. More context in [START.md](START.md) (free AI chat + writing your spec) and the [README](README.md).
