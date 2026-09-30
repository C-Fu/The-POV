<!-- refreshed: 2026-09-30 -->
# Architecture

**Analysis Date:** 2026-09-30

> **No executable architecture.** This repository has no application code, no modules,
> no layers, and no runtime flow. It is a training-material repository containing one
> Markdown source document and its HTML export. What follows documents the actual
> (content) structure rather than a software architecture.

## System Overview

```text
┌─────────────────────────────────────────────────────────────┐
│                   AUTHORING (external)                      │
│   MarkText editor (not part of the repo)                    │
└────────────────────────────┬────────────────────────────────┘
                             │ manual export
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                    CONTENT SOURCE                           │
│  "Anyone Can Build- From Problem to App.md"   (114 lines)   │
│  Training outline + notes + 1 mermaid diagram               │
└────────────────────────────┬────────────────────────────────┘
                             │ export
                             ▼
┌─────────────────────────────────────────────────────────────┐
│                   RENDERED ARTIFACT                         │
│  "Anyone Can Build- From Problem to App.html" (1,798 lines) │
│  Self-contained, inline CSS, opens in any browser           │
└─────────────────────────────────────────────────────────────┘
```

## Component Responsibilities

| Component | Responsibility | File |
|-----------|----------------|------|
| Training source notes | Canonical content: topic list, presenter reminders, mermaid org-chart diagram, design-concept explainer | `Anyone Can Build- From Problem to App.md` |
| HTML export | Distributable/read-only rendering of the source, for viewing without a Markdown renderer | `Anyone Can Build- From Problem to App.html` |
| Planning output | GSD analysis documents (generated, not source) | `.planning/codebase/` |

## Pattern Overview

**Overall:** Single-document content pipeline (source → export). Not a software pattern.

**Key Characteristics:**
- One-way flow: the `.md` is the source of truth; the `.html` is a derived artifact.
- No automated build — the export is performed manually in MarkText.
- No code, no interfaces, no abstractions.

## Layers

**Content (only layer):**
- Purpose: Hold the training material for the 2-hour "Anyone Can Build: From Problem to App" session.
- Location: repository root.
- Contains: Markdown prose, one mermaid fenced block, three absolute-path image references.
- Depends on: Nothing (images are external and optional).
- Used by: A presenter/attendee, or a Markdown/HTML viewer.

## Data Flow

### Primary Content Path

1. Authoring in MarkText (external, not in repo).
2. Source written to `Anyone Can Build- From Problem to App.md` (lines 1-114).
3. Manual HTML export produces `Anyone Can Build- From Problem to App.html` (1,798 lines, inline `markdown-body` CSS).
4. Consumption: open the `.html` in a browser, or read the `.md` in any viewer.

### Diagram Rendering (secondary)

1. Mermaid `flowchart LR` block at `Anyone Can Build- From Problem to App.md`, lines 43-74.
2. Rendered by a mermaid-capable Markdown viewer at read time. The HTML export carries the block as-is; no mermaid runtime script is embedded.

**State Management:**
- None. Static files.

## Key Abstractions

**None.** There are no classes, interfaces, modules, or shared types in this repository.

## Entry Points

**Human entry point:**
- Location: `Anyone Can Build- From Problem to App.md`
- Triggers: Opened by a person in a Markdown editor/viewer.
- Responsibilities: Present the 7-topic training agenda (lines 5-11), the presenter checklist under `# YANG PERLU TAHU` (lines 13-41), and the design-language/design-system/brand-ecosystem explainer (lines 76-114).

**Browser entry point:**
- Location: `Anyone Can Build- From Problem to App.html`
- Triggers: Opened in a web browser.
- Responsibilities: Render the same content with self-contained styling.

## Architectural Constraints

- **Threading:** Not applicable — no code executes.
- **Global state:** Not applicable.
- **Circular imports:** Not applicable — there are no imports.
- **Content constraint:** The Markdown references images via absolute local paths under `C:/Users/C-Fu/AppData/Roaming/marktext/images/`, so those images are unrecoverable from this repository alone.
- **Encoding:** The HTML export contains mojibake in place of emoji/smart quotes (e.g. `dY`%`, `�?Ts`, `�+'`), indicating a charset mismatch (file is declared `UTF-8` but was written with different byte handling) — see `CONCERNS` notes below.

## Anti-Patterns

### Derivative artifact committed alongside its source

**What happens:** `Anyone Can Build- From Problem to App.html` sits next to `Anyone Can Build- From Problem to App.md` with no indication of which is authoritative.
**Why it's wrong:** Edits applied to the HTML are silently lost on the next export, and the two files can drift (they already differ: the HTML carries mojibake the Markdown does not).
**Do this instead:** Treat `Anyone Can Build- From Problem to App.md` as the single source of truth and re-export the HTML whenever it changes — or drop the HTML from the repo entirely.

### Absolute local paths in shared content

**What happens:** Image references point at `C:/Users/C-Fu/AppData/Roaming/marktext/images/...` (`Anyone Can Build- From Problem to App.md`, lines 23, 29, 33-37).
**Why it's wrong:** The images break for every other machine and every other user.
**Do this instead:** Copy images into an `assets/` folder inside the repository and reference them relatively.

## Error Handling

**Strategy:** Not applicable — no code, no failure modes.

## Cross-Cutting Concerns

**Logging:** Not applicable.
**Validation:** Not applicable.
**Authentication:** Not applicable.

---

*Architecture analysis: 2026-09-30*
