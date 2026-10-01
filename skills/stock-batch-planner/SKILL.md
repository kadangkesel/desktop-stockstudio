---
name: stock-batch-planner
description: Plan a production batch end-to-end — turn research into a scheduled, resource-aware plan with concepts, asset counts, model/cost estimates, naming, folder structure, and a QA gate before upload. Use to schedule a week or month of microstock production, size a batch to a budget, split work across image/video/vector pipelines, or recover a stalled backlog. Trigger on "batch plan", "production plan", "rencana batch", "jadwal produksi", "how many assets", or "plan my uploads". Not for choosing topics (/stock-keyword-research, /stock-competitor-niche-research) or validating finished metadata (/stock-metadata-qa).
---

# Stock Batch Planner

Turn research output into a plan you can execute: what to make, how many, in
what order, at what cost, and when it ships.

## When to use

- You have keyword/niche research and need to convert it into actual work.
- You must fit production to a budget, a GPU quota, or limited free hours.
- A backlog is growing and you need to decide what to finish vs. drop.
- Coordinating multiple pipelines (photo, vector, AI image, AI video).

## Inputs

- **Research output** — keyword clusters and/or niche gaps.
- **Capacity** — hours per week, GPU/API budget, storage, upload cadence.
- **Platforms** — where this batch is going.
- **Publish window** — season or launch date the batch must hit.

## Method

1. **Rank concepts** by expected return per unit effort, not raw demand. Use the
   score already produced by research skills; do not re-invent it.
2. **Size the batch** from capacity, not ambition. Compute:
   `assets = min(concept_count × target_per_concept, capacity_limit)`.
3. **Estimate cost** per asset (API/generation, retries, render time) and total;
   flag any concept whose cost exceeds its expected return.
4. **Sequence by dependency and season.** Seasonal work must be uploaded well
   before the season (typically 4–8 weeks). Start the longest-lead pipeline
   first.
5. **Split across pipelines** so a blocked pipeline does not stall the batch:
   image / vector / video / editorial each get their own track.
6. **Define the naming and folder contract** up front:
   `batch-YYYYMM/<concept>/<concept>_<variant>_<n>.<ext>`, so exports, CSVs, and
   metadata stay traceable to the concept.
7. **Insert QA gates.** One gate after generation (defects, IP, composition),
   one after metadata (`/stock-metadata-qa`), one before upload
   (`/stock-upload-checklist`).
8. **Schedule with buffers.** Plan ~20% slack for retries and rejected assets.
9. **Define done.** A batch is done when assets pass QA, metadata is clean, the
   CSV is exported, and the upload is logged.

## Output

```text
concept,pipeline,assets,unit_cost,total_cost,start,qa_gate,upload_window,owner
```

Plus:

- A week-by-week schedule.
- The folder/naming contract.
- The explicit cut line: what is deferred if time runs short.

## Quality checklist

- Asset counts are derived from capacity, and the arithmetic is shown.
- Seasonal uploads land 4–8 weeks before the season.
- Every concept has an owner (or is explicitly unassigned) and a QA gate.
- Buffers exist; the plan is not 100% utilisation.
- The deferral list is explicit, so a shortfall degrades gracefully.
