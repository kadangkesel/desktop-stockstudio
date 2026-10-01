# StockStudio Skills

Agent skills that work alongside the StockStudio app — the research and QA work
that happens *before* and *after* metadata generation. Each skill is a folder
with a `SKILL.md` following the open [Agent Skills](https://agentskills.io)
convention, so it also works in Claude Code, Codex, and any other agent that
reads `SKILL.md`.

| Skill | Job | When it runs |
|---|---|---|
| [`stock-keyword-research`](stock-keyword-research/SKILL.md) | Seed/niche → ranked, deduplicated, platform-ready keyword sets | Before deciding what to produce |
| [`stock-competitor-niche-research`](stock-competitor-niche-research/SKILL.md) | Competitor portfolio analysis and underserved-niche gaps | When choosing the next batch |
| [`stock-prompt-generator`](stock-prompt-generator/SKILL.md) | Keyword cluster → consistent, commercially-safe generation prompts | Between research and production |
| [`stock-metadata-qa`](stock-metadata-qa/SKILL.md) | Validate and auto-repair titles/keywords/categories | After AI metadata, before upload |
| [`stock-video-research`](stock-video-research/SKILL.md) | Watch a video (frames + transcript) and answer grounded in it | Analyzing competitor or reference video |
| [`stock-batch-planner`](stock-batch-planner/SKILL.md) | Research → capacity-aware production plan with cost, schedule, QA gates | Scheduling a week/month of production |
| [`stock-upload-checklist`](stock-upload-checklist/SKILL.md) | Final pre/post-upload gate: integrity, releases, CSV match, log | Right before and after uploading |

## Install

Copy any skill folder into your agent's skills directory:

```bash
# Claude Code (per-user)
cp -r skills/stock-* ~/.claude/skills/

# Claude Code (per-project)
cp -r skills/stock-* .claude/skills/
```

## Design notes

- **Evidence over vibes.** Every demand claim carries a source or is marked
  `unverified`. No invented volume numbers.
- **Repair, not just report.** The QA skill emits a corrected row for every
  failure, so it can be re-run until clean.
- **Commercial safety first.** Prompts and keywords avoid brands, celebrities,
  trademarks, and text artifacts that cause rejection.
- **Capability-aware.** Research skills filter recommendations down to what the
  stated pipeline can actually produce.
