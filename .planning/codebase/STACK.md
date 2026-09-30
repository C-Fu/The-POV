# Technology Stack

**Analysis Date:** 2026-09-30

> **Repository type: documentation / training-material repo. There is no software stack.**
> The project root `C:\Users\C-Fu\Documents\yayasan_peneraju` contains exactly two content
> files (plus the `.planning/` analysis directory). No application code, no dependencies,
> no build system, no runtime exist.

## Languages

**Primary:**
- Markdown - `Anyone Can Build- From Problem to App.md` (114 lines, 4,604 bytes). Source notes for a 2-hour training session.

**Secondary:**
- HTML + inline CSS - `Anyone Can Build- From Problem to App.html` (1,798 lines, 75,609 bytes). Self-contained export of the Markdown document.

**Embedded (content, not code):**
- One `mermaid` fenced code block inside the Markdown (`Anyone Can Build- From Problem to App.md`, lines 43-74) — a `flowchart LR` comparing "Traditional Org" vs "AI Age Org". Rendered by a Markdown viewer, not executed by any build step.

## Runtime

**Environment:**
- Not applicable — no runtime, interpreter, or engine is required to use this repository.

**Package Manager:**
- Not applicable — no package manager.
- Lockfile: missing (no `package.json`, `requirements.txt`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `pnpm-lock.yaml`, `yarn.lock`, `package-lock.json`).

## Frameworks

**Core:**
- Not applicable — no framework.

**Testing:**
- Not applicable — no test framework (no `jest.config.*`, `vitest.config.*`, `pytest.ini`, `*.test.*`, `*.spec.*`).

**Build/Dev:**
- Not applicable — no build tooling. The HTML file is an **export artifact**, not a build output: it was produced by a Markdown editor (MarkText — evidenced by the embedded GitHub-style `.markdown-body` CSS and by image paths under `C:/Users/C-Fu/AppData/Roaming/marktext/images/` referenced in the Markdown).

## Key Dependencies

**Critical:**
- None.

**Infrastructure:**
- None.

**Authoring toolchain (external to the repo, inferred, not declared):**
- MarkText (Markdown editor) — used to author the `.md` and produce the HTML export.

## Configuration

**Environment:**
- No configuration. No `.env*` files, no config files of any kind (`*.config.*`, `tsconfig.json`, `.nvmrc`, `.python-version`, `.editorconfig`, `.prettierrc`, `eslint.config.*`) are present.

**Build:**
- No build config files.

## Platform Requirements

**Development:**
- Any text or Markdown editor. Nothing to install, compile, or run.

**Production:**
- Any browser or Markdown viewer. The HTML export is fully self-contained (inline CSS, no external scripts or stylesheets), so `Anyone Can Build- From Problem to App.html` opens offline by double-click.

## Observed Tooling References (content topics, not dependencies)

The training notes *mention* the following as discussion topics; these are **not** installed,
declared, or used by this repository:
- OpenCode, GSD, OpenChamber, Tailscale (install walkthroughs — `Anyone Can Build- From Problem to App.md`, line 19)
- MCP / Playwright MCP / Blender MCP (`Anyone Can Build- From Problem to App.md`, lines 21-29)

---

*Stack analysis: 2026-09-30*
