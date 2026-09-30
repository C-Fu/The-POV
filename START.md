# START — From Idea to Spec with Free AI Chat

English | [Bahasa Melayu](START.ms-MY.md) · Back to [README](README.md)

Before you write any code, you need a clear problem and a written spec. Free AI chat tools are perfect for getting there — this guide shows you how.

---

## 1. Free AI chat tools

Any of these work well for hashing out ideas and writing specs:

| Tool | Link |
|------|------|
| Microsoft Copilot | <https://copilot.microsoft.com> |
| Google Gemini | <https://gemini.google.com> |
| DeepSeek Chat | <https://chat.deepseek.com> |

> Free tiers are fine — problem-hashing and spec writing don't need paid models.

---

## 2. The workflow

1. **Start with an everyday problem** — something that annoys you or someone you know.
2. **Hash it out with an AI chat** — use *interview mode*: let the AI ask *you* questions until the idea is sharp (see the magic phrase below).
3. **Write the spec** — save the outcome as a short Markdown document.
4. **Build it** — feed the spec to OpenCode + GSD and let the workflow take over (see [GSD.md](GSD.md)).

---

## 3. Token-saving basics

Five habits that keep your AI usage fast and cheap:

1. **Don't paste PDFs — convert to Markdown or plain text first.**
   Why: PDFs bloat the context with layout junk and cost more tokens.

2. **End your prompts with:** `ask me relevant questions`
   ```text
   ask me relevant questions
   ```
   Why: it makes the AI interview you to furnish details you forgot — instead of guessing and producing the wrong output.

3. **Paste only the relevant excerpt, not the whole document.**
   Why: context space is limited; every irrelevant line costs tokens and attention.

4. **One topic per conversation — start a new chat for a new problem.**
   Why: mixing topics pollutes the context and confuses the model.

5. **GIGO — Garbage In, Garbage Out.**
   Why: the AI can only be as good as your input. Vague shorthand like *"fix the login thing asap"* produces vague, wrong output. Use proper language and the correct terms, and write your questions and facts in full — a complete, precisely worded question gets a precise answer.

---

## 4. Spec-driven development

**Spec-driven development** means writing down *what* to build before building it — then giving that document to a coding agent as the source of truth:

**problem → requirements list (must-have vs nice-to-have) → user flow → simple spec doc → give to OpenCode + GSD**

Copy this skeleton into your chat with the AI (or a blank `.md` file) and fill it in:

```markdown
# [Project name]

## Problem
[One or two sentences: who has this problem and why it hurts.]

## Requirements

### Must-have
- [The app does not work without this]

### Nice-to-have
- [Can wait for version 2]

## User flow
1. [User opens the app and sees ...]
2. [User does ... and the app ...]
3. [User ends up with ...]

## Out of scope
- [Explicitly NOT building this, to keep v1 small]
```

Keep v1 small: 3–5 must-haves is a great first milestone.

---

**Next:** set up the toolchain with [INSTALL.md](INSTALL.md), then learn the build workflow in [GSD.md](GSD.md). Back to [README](README.md).
