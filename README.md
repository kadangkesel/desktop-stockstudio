# ✨ StockStudio – Your Microstock Assistant

![License: GPL](https://img.shields.io/badge/License-GPL--3.0-yellow.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blueviolet)
![Status](https://img.shields.io/badge/status-Active-brightgreen)
![Version](https://img.shields.io/badge/version-5.0.0-blue)

**StockStudio** is a desktop app for microstock creators — a single place to
generate metadata, research keywords, build automation pipelines, and now work
with an AI agent that handles the busywork for you, across every major stock
platform.

Whether you're shipping AI artwork, clearing a photo shoot, or scaling a content
library, StockStudio handles the busywork so you can keep producing.

**[⬇️ Download the latest release](https://github.com/kadangkesel/desktop-stockstudio/releases/latest)**

---

## 🆕 New in 5.0

- 🤖 **AI Agents** — chat with an agent that researches keywords, writes and
  applies metadata, creates images, and builds and runs workflows for you
- 🧠 **Skills, Memory & Notes** — teach the agent how you work, and keep the
  answers you want to reuse
- 🔌 **MCP servers** — give the agent tools from external services
- 🧩 **Workflow templates** and **60+ workflow nodes**
- 🔍 **Free Adobe Stock research** for everyone, with a daily allowance
- 📈 **Envato popular searches** and **StockStudio Users' Choice** on the dashboard
- 🌸 **Edelweis Bloom** — a new vectorize engine that keeps colours and clean edges

Full notes: [Release 5.0.0](https://github.com/kadangkesel/desktop-stockstudio/releases/tag/5.0.0-public)

---

## 🚀 Features

### 🤖 AI Agents
A chat assistant that does the work, not just talks about it. Ask it to research
a niche on Adobe Stock, write and apply metadata to your files, generate images,
search the web, or build, run and debug an Automation Workflow.

- Use the plan you already pay for: **ChatGPT (Codex)** · **Claude (Pro/Max)** ·
  **Antigravity** — or any **OpenAI-compatible** API (OpenRouter, LM Studio,
  Ollama, …)
- Understands images, PDF, Word, spreadsheets and video
- Shows a task list and a plan you can review, and asks before it changes your files
- Steer it while it works; it notifies you when a long job finishes
- Extend it with **Skills** (see below) and **MCP servers**

### 📝 AI Metadata Generation
Drop in your images or clips and let AI write titles, descriptions, and
keywords. Bring your own API key, or use a subscription you already have:

> **Gemini · OpenAI · OpenRouter · ChatGPT (Codex) · Claude Code · Antigravity · Custom (OpenAI-compatible)**

### 🧩 Automation Workflows (node-based)
Build visual, node-based pipelines — no coding required. Start from a
**template** or chain **60+ nodes** to automate your process end to end:

- **Triggers** — file import, manual start, webhook, schedule, agent input
- **Core** — metadata builder, file picker, Adobe Stock search, export CSV, save files
- **AI** — chat, analyze image/video, generate image/video, text-to-speech, with
  Gemini, OpenAI, Anthropic, Mistral, OpenRouter, ChatGPT (Codex), Claude Code,
  Antigravity and Custom nodes
- **Image tools** — background remover, upscale (Upscayl), vector convert,
  retrace, compress, crop, resize, sharpen, grain, strip metadata, QC, dedupe
- **Flow control** — loop, split, aggregate, if, wait
- **Utilities** — HTTP request, code (custom JS), JSON parser, set, base64,
  download file, read file, SFTP upload, video tools, append log

Any workflow with an *Agent input* trigger becomes a tool the agent can call.
Community workflows live in [`workflows/`](workflows/) — import a `.json`
straight into the app and run it.

### 🔍 Keyword Research & Presets
Search Adobe Stock for free (daily allowance in **Settings → Usage**), filter by
type, asset age and AI content, analyze any creator's portfolio, and export
creator reports to CSV. Save your best keyword sets as presets and reuse them
anywhere.

### 📈 Trends
Envato popular searches, StockStudio Users' Choice, a holiday calendar and a
daily **Top Pick** grid show you what buyers want before you produce.

### 🗂 Smart Metadata Management
Edit titles, descriptions, and keywords in bulk. Apply filters, truncation
rules, and negative-keyword presets across hundreds of files at once.

### 📤 Multi-Platform CSV Export
Export upload-ready CSVs tailored to each platform's format:

> **Adobe Stock · Shutterstock · Freepik · Vecteezy · Canva · Envato · Alamy**

### 🎨 Prompt Generator
Craft better prompts for AI image tools, with templates and suggestions built in.

### 🪄 Image Utilities
Background removal, vectorize (Potrace, Edelweis Zero and Bloom), upscaling and
compression — as standalone tools or inside the workflow engine.

---

## 🧠 Skills

Skills are reusable playbooks for an AI agent: a folder with a `SKILL.md` that
tells the agent how to do one job well. The agent sees each skill's name and
description, and loads the full playbook only when a request matches.

The [`skills/`](skills/) folder holds the research and QA skills — the work
*around* metadata generation: deciding what to make, and checking it before
upload.

| Skill | Job | When it runs | In the app |
|---|---|---|---|
| [`stock-keyword-research`](skills/stock-keyword-research/SKILL.md) | Seed/niche → ranked, deduplicated, platform-ready keyword sets | Before deciding what to produce | ✅ built in |
| [`stock-competitor-niche-research`](skills/stock-competitor-niche-research/SKILL.md) | Competitor portfolio analysis & underserved-niche gaps | When choosing the next batch | ✅ built in |
| [`stock-prompt-generator`](skills/stock-prompt-generator/SKILL.md) | Keyword cluster → consistent, commercially-safe prompts | Between research and production | ✅ built in |
| [`stock-metadata-qa`](skills/stock-metadata-qa/SKILL.md) | Validate & auto-repair titles/keywords/categories | After AI metadata, before upload | ✅ built in |
| [`stock-batch-planner`](skills/stock-batch-planner/SKILL.md) | Research → capacity-aware production plan with cost & QA gates | Scheduling a week/month of production | ✅ built in |
| [`stock-upload-checklist`](skills/stock-upload-checklist/SKILL.md) | Final pre/post-upload gate: integrity, releases, CSV match | Right before and after uploading | ✅ built in |
| [`stock-video-research`](skills/stock-video-research/SKILL.md) | Watch a video (frames + transcript) and answer grounded in it | Analyzing reference/competitor video | ➕ add it yourself |

StockStudio 5.0 also ships `stock-creative-brief`, `stock-upcoming-content-research`,
`workflow-builder`, `motion-video` and planning/debugging skills, for 16 built-in
skills in total.

### Use skills in StockStudio
Built-in skills work out of the box in **Agents**. To add one from this repo
(or your own):

1. In **Agents → Skills**, click **Open skills folder**
   (`~/.stockstudio/agents/skills/`, on Windows `%USERPROFILE%\.stockstudio\agents\skills\`).
2. Copy the skill folder in, e.g. `skills/stock-video-research/`.
3. Send your next message — the agent picks it up, no restart needed.

You can also write one in **Agents → Skills → New skill**, or ask the agent to
create it for you.

> A skill's folder name must match the `name` in its `SKILL.md` front-matter
> (lowercase letters, digits and `-`). Keep `name:` and `description:` on a
> single line each.

### Use skills in other agents
The skills follow the open `SKILL.md` convention, so they also work in Claude
Code, Codex, and any agent that reads `SKILL.md`:

```bash
# Claude Code – per user
cp -r skills/stock-* ~/.claude/skills/

# Claude Code – per project
cp -r skills/stock-* .claude/skills/
```

---

## 💼 Who's It For?

- 📸 Photographers & illustrators selling stock
- 🎨 Designers using AI to create visuals at scale
- 🧠 Agencies managing large content libraries
- 🚀 Creators who want better SEO and faster, automated workflows

---

## 📦 This Repository

This is the **public / community** repo for StockStudio. It hosts:

- [Releases](https://github.com/kadangkesel/desktop-stockstudio/releases) — installers and auto-updates
- [`workflows/`](workflows/) — shareable automation workflows (`.json` + `.md`)
- [`skills/`](skills/) — Agent Skills for research & QA
- Docs and the workflow submission guide

Want to contribute a workflow? See
[`workflows/WORKFLOW_SUBMISSION_GUIDE.MD`](workflows/WORKFLOW_SUBMISSION_GUIDE.MD).

---

## 🤝 Contributing & Feedback

Got a workflow, a skill, a bug, or an idea?
[Open an issue or suggestion here.](https://github.com/kadangkesel/desktop-stockstudio/issues)

---

**Let's make creating stock content fun and efficient again.**
✨ Built with care by creators, for creators — the KadangKesel Team.
