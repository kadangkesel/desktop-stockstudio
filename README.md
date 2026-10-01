# ✨ StockStudio – Your Microstock Assistant

![License: GPL](https://img.shields.io/badge/License-GPL--3.0-yellow.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-blueviolet)
![Status](https://img.shields.io/badge/status-Active-brightgreen)
![Version](https://img.shields.io/badge/version-4.4.0-blue)

**StockStudio** is a desktop app for microstock creators — a single place to
generate metadata, build automation pipelines, research keywords, and prep your
files for upload across every major stock platform.

Whether you're shipping AI artwork, clearing a photo shoot, or scaling a content
library, StockStudio handles the busywork so you can keep producing.

---

## 🚀 Features

### 🤖 AI Metadata Generation
Drop in your images or clips and let AI write titles, descriptions, and
keywords. Bring your own API key from any of the supported providers:

> **Gemini · OpenAI · Anthropic · Mistral · Groq · OpenRouter**

### 🧩 Automation Workflows (node-based)
Build visual, node-based pipelines — no coding required. Chain **40+ nodes** to
automate your entire process end to end:

- **Input** — file import, file picker, download file, webhook, manual start
- **AI** — analyze image/video, generate image/video, chat, text-to-speech, AI Agent
- **Metadata** — metadata editor, JSON parser, set, aggregate, split
- **Image tools** — background remover, upscale (Upscayl), vector convert,
  retrace (raster→vector), image compress
- **Flow control** — loop, if/condition, wait, code (custom JS)
- **Export** — save files, export CSV, HTTP request

Ready-made workflows live in [`workflows/`](workflows/) — import a `.json`
straight into the app and run it.

### 📝 Smart Metadata Management
Edit titles, descriptions, and keywords in bulk. Apply filters, truncation
rules, and negative-keyword presets across hundreds of files at once.

### 📤 Multi-Platform CSV Export
Export upload-ready CSVs tailored to each platform's format:

> **Adobe Stock · Shutterstock · Freepik · Vecteezy · Canva · Envato · Alamy**

### 🔍 Keyword Research & Presets
Pull real keyword suggestions from the biggest stock sites, with thumbnail
previews. Save your best keyword sets as presets and reuse them anywhere.

### 🎨 Prompt Generator
Craft better prompts for AI image tools, with templates and suggestions built in.

### 🪄 Image Utilities
One-click background removal, upscaling, vector conversion, and compression —
built right into the workflow engine or as standalone tools.

---

## 🧠 Skills

The [`skills/`](skills/) folder contains **Agent Skills** — reusable instructions
for AI coding agents (Claude Code, Codex, and anything that reads `SKILL.md`)
that cover the research and QA work *around* the app, before and after metadata
generation.

> ⚠️ **Note:** Skills are **not** an in-app feature. They run inside your AI
> agent, not the StockStudio workflow engine. They complement the app — the app
> produces metadata; the skills help you decide what to make and verify it
> before upload.

| Skill | Job | When it runs |
|---|---|---|
| [`stock-keyword-research`](skills/stock-keyword-research/SKILL.md) | Seed/niche → ranked, deduplicated, platform-ready keyword sets | Before deciding what to produce |
| [`stock-competitor-niche-research`](skills/stock-competitor-niche-research/SKILL.md) | Competitor portfolio analysis & underserved-niche gaps | When choosing the next batch |
| [`stock-prompt-generator`](skills/stock-prompt-generator/SKILL.md) | Keyword cluster → consistent, commercially-safe prompts | Between research and production |
| [`stock-metadata-qa`](skills/stock-metadata-qa/SKILL.md) | Validate & auto-repair titles/keywords/categories | After AI metadata, before upload |
| [`stock-video-research`](skills/stock-video-research/SKILL.md) | Watch a video (frames + transcript) and answer grounded in it | Analyzing reference/competitor video |
| [`stock-batch-planner`](skills/stock-batch-planner/SKILL.md) | Research → capacity-aware production plan with cost & QA gates | Scheduling a week/month of production |
| [`stock-upload-checklist`](skills/stock-upload-checklist/SKILL.md) | Final pre/post-upload gate: integrity, releases, CSV match | Right before and after uploading |

**Install** (copy any skill folder into your agent's skills directory):

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
