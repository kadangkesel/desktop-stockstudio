---
name: stock-competitor-niche-research
description: Analyze microstock competitor portfolios and find underserved niches before committing production time. Use to map a competitor's top sellers, measure demand-vs-supply gaps, spot style/format gaps (video, 3D, editorial, seasonal), and pick the next production topic with evidence. Trigger on "competitor research", "niche research", "is this saturated", "gap analysis", "riset kompetitor", or when choosing between several portfolio directions. Not for individual keyword expansion (/stock-keyword-research) or metadata writing (/stock-metadata-qa).
---

# Stock Competitor & Niche Research

Answer one question with evidence: **where is demand that other contributors
have not already flooded?**

## When to use

- Choosing the next batch topic and several options look similar.
- A portfolio sells but you do not know which direction to grow.
- Deciding whether to enter video/3D/editorial instead of more of the same.
- Auditing your own portfolio against the top contributors in a niche.

## Inputs

- **Target niche** or portfolio to analyze.
- **Platforms** — default Adobe Stock + Shutterstock; add Freepik/Pond5 for video.
- **Your capability** — what you can produce (photo / vector / AI image / AI
  video / 3D render), so gaps you cannot fill are filtered out.
- **Time budget** — how many assets this run should yield.

## Method

1. **Define the niche** in 1–2 sentences and list 5–10 adjacent sub-niches.
2. **Sample the leaders.** For 3–5 top contributors in the niche, record:
   portfolio size, dominant style, dominant format, upload recency, and the
   themes their top results cluster around.
3. **Measure supply.** For each sub-niche, record result counts per format.
   High count + same style everywhere = crowded; low count + relevant results
   = possible gap.
4. **Measure demand.** Use autocomplete, trending pages, and seasonality. Mark
   anything without a source as `unverified`.
5. **Find the gaps.** Classify each sub-niche:
   - **Style gap** — same topic, nobody offers your visual treatment.
   - **Format gap** — demand exists in video/3D/editorial but supply is photo-only.
   - **Angle gap** — the obvious angle is covered, the adjacent buyer need is not.
   - **Season gap** — content exists but is not refreshed for the coming season.
6. **Filter by capability.** Drop gaps you cannot produce; keep the ones that
   map to your pipeline.
7. **Rank and recommend.** Score each surviving gap on demand, supply weakness,
   production effort, and expected longevity (evergreen vs. one-season).
8. **Propose a batch plan.** For the top 2–3 gaps: concept list, asset count,
   format, keywords to target, and the season window to publish.

## Output

```text
sub_niche,format,competition_count,demand,demand_source,gap_type,effort,score,recommendation
```

Plus a short written recommendation naming the single best next batch and why.

## Quality checklist

- Competition counts are real platform numbers with a date.
- Demand claims carry a source or are marked `unverified`.
- No gap is recommended that the stated pipeline cannot produce.
- The batch plan fits the time budget and names a publish window.
- Nothing recommends copying a specific contributor's protected work; only
  patterns, topics, and formats are compared.
