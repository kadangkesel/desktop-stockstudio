---
name: stock-upload-checklist
description: Final pre-upload and post-upload checklist for microstock submissions — file integrity, model/property releases, editorial flags, CSV/platform match, thumbnail and preview sanity, and a logged submission record. Use right before pressing upload and again after, to confirm acceptance and catch rejections early. Trigger on "upload checklist", "before upload", "submission checklist", "cek sebelum upload", "rejected", or "review status". Not for validating metadata content (/stock-metadata-qa) and not for planning what to produce (/stock-batch-planner).
---

# Stock Upload Checklist

The last gate. Everything here is cheap to check and expensive to skip.

## When to use

- Immediately before submitting a batch to any platform.
- After uploading, to confirm acceptance and catch early rejections.
- When files were rejected and you need to find which gate failed.

## Pre-upload

1. **Files**
   - No corrupted or zero-byte files; every file opens.
   - Correct format and codec per platform (JPEG/PNG, MP4/MOV with expected codec).
   - Resolution and aspect ratio meet the platform minimum.
   - No visible watermarks, logos, signatures, or AI-tool artifacts left in frame.
   - Filenames follow the batch naming contract and are unique.
2. **Legal**
   - Model releases present and attached for every recognisable person.
   - Property releases present for recognisable private property/trademarks.
   - Editorial content flagged editorial; no editorial content submitted as
     commercial.
   - No third-party copyrighted elements (art, screens, characters, logos).
3. **Metadata** — run `/stock-metadata-qa` and confirm zero blockers.
4. **CSV / platform match**
   - Correct template for this platform, correct delimiter and encoding.
   - Title/keyword limits within the platform's caps.
   - Category filled; language consistent with the platform.
   - Every CSV row maps to an existing file, and every file has a row.
5. **Preview sanity**
   - Generate a contact sheet and look at it: subjects visible, no accidental
     crops, consistent series look.
   - Spot-check 5 random files at full size.

## Upload

6. **Batch size** — submit in chunks that let you react to a rejection before
   uploading everything.
7. **Log it** — record platform, date, file count, CSV name, and batch ID.

## Post-upload

8. **Confirm receipt** — files appear in the contributor dashboard, count matches.
9. **Watch the review window** — check review status within the platform's
   normal turnaround.
10. **Triage rejections** by cause: technical / metadata / legal / duplicate.
    Fix the cause, not just the file, then re-submit.
11. **Record outcomes** — accepted, rejected, reason — so the next batch plan
    learns from it.

## Output

A checklist report:

```text
item,status,evidence,action_if_failed
```

Plus a submission log entry:

```text
batch_id,platform,date,files,csv,status,rejections,notes
```

## Quality checklist

- Every unchecked item names the exact action to fix it.
- Releases are verified against the actual people/property in the files.
- Editorial vs. commercial is decided per file, not per batch by default.
- The submission log is written even when everything passes.
- Rejections are triaged to a cause and fed back into the batch plan.
