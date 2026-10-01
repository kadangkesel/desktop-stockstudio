---
name: stock-keyword-research
description: Research, score, and expand keywords for microstock images, vectors, and video before producing or uploading. Use for seed keyword discovery, long-tail expansion, demand-vs-competition scoring, buyer-intent grouping, and building platform-ready keyword sets for Adobe Stock, Shutterstock, iStock, Freepik, Vecteezy, and Pond5. Trigger on "keyword research", "what should I make", "trending keywords", "riset keyword", "keyword microstock", or when planning a new batch. Not for writing titles/keywords from an existing file (/stock-metadata-qa) or competitor portfolio gaps (/stock-competitor-niche-research).
---

# Stock Keyword Research

Turn a rough idea or niche into a ranked, deduplicated, platform-ready keyword
plan — so you produce what buyers search for instead of what you feel like
making.

## When to use

- "What should I upload this week?" / "Is this niche saturated?"
- Expanding one seed keyword into long-tail buyer phrases.
- Building a keyword preset to reuse across a batch.
- Deciding between two topic ideas with limited render/production time.

## Inputs

Ask for, or infer:

- **Seed** — a niche, subject, or single keyword ("sustainable packaging").
- **Asset type** — photo / vector / video / 3D (defaults: photo).
- **Platforms** — default Adobe Stock + Shutterstock.
- **Constraints** — must-avoid topics (brands, people, trademarks), season window.

## Method

1. **Seed expansion.** Generate 6–10 angles per seed across these axes, so you
   are not just re-wording one idea:
   - subject, action, concept, emotion, setting, demographic, season/holiday,
     style (flat, isometric, 3D, watercolor), composition (copy space, isolated,
     top view), use-case (banner, background, icon, infographic).
2. **Long-tail expansion.** For each angle, write 3–5 buyer phrases of 2–4
   words. Buyers search phrases, not single words. Example from `finance`:
   `personal finance app`, `budget planning icon`, `saving money concept`,
   `investment growth chart`.
3. **Demand signal.** Estimate relative demand with whatever evidence is
   available (platform autocomplete, "trending" pages, seasonality, search
   volume tools). Record the *source* next to every number. Never invent a
   volume figure — if there is no source, mark `demand: unverified`.
4. **Competition signal.** Search each phrase on the target platform and note
   result count. Few results + plausible demand = opportunity. Huge result
   counts = saturated unless the angle is clearly differentiated.
5. **Score.** Rank with a transparent heuristic:
   `score = demand_weight − competition_weight + differentiation_bonus`.
   Show the three components; do not hide the arithmetic.
6. **Group by buyer intent.** Cluster the surviving phrases into themes so one
   production run can serve a whole cluster (one shoot → 20 keywords).
7. **Output the keyword set.** For the winning cluster, produce the final
   keyword list for the asset(s): 25–45 keywords for Adobe/Shutterstock, ordered
   most-relevant-first, no duplicates, no competitor brand names, no spammy
   repeats of the same word.

## Output

A markdown report plus a CSV:

```text
keyword,cluster,demand,demand_source,competition_count,platform,score,notes
```

Followed by, per winning concept, the ready keyword list in a copy-paste block.

## Quality checklist

- Every demand number has a source, or is explicitly `unverified`.
- No keyword appears twice in a final set; no platform gets the same list blindly
  (Adobe allows ~49, Shutterstock ~50, iStock lower — respect each cap).
- No trademarks, celebrity names, or brand logos suggested.
- Every cluster maps to something you can actually produce with your pipeline.
- The report names the 2–3 concepts with the best score-to-effort ratio.
