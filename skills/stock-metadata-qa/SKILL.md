---
name: stock-metadata-qa
description: Validate and repair stock metadata before upload — titles, descriptions, keywords, and category — against each platform's rules. Use to catch title/description limits, keyword spam and duplicates, irrelevant or banned terms, missing categories, CSV format errors, and Adobe/Shutterstock/iStock/Freepik/Vecteezy submission mismatches. Trigger on "metadata QA", "check metadata", "keyword spam", "validate CSV", "cek metadata", or before a bulk upload. Not for generating metadata from scratch (/stock-metadata-qa complements the StockStudio AI nodes) and not for choosing what to shoot (/stock-keyword-research).
---

# Stock Metadata QA

Be the last gate before upload: catch what gets files rejected, de-ranked, or
banned — automatically and with evidence.

## When to use

- After any AI metadata generation pass, before exporting the CSV.
- Before a bulk upload to a new platform.
- When a batch was rejected or de-ranked and you need the cause.

## Inputs

- The metadata set: CSV, sidecar, or the StockStudio `metadataEditor` output.
- Target platform(s).
- Optional: the asset files, to verify the metadata actually matches the image.

## Platform rules (defaults — confirm against current platform docs)

| Platform | Title | Keywords | Notes |
|---|---|---|---|
| Adobe Stock | ≤ 200 chars, no special symbols | ≤ 49 | Title must be a natural phrase, not keyword stuffing |
| Shutterstock | ≤ 200 chars | ≤ 50 | Categories required; editorial flag matters |
| iStock/Getty | ≤ 200 chars | ≤ 50 | Stricter relevance scoring |
| Freepik | ≤ 150 chars | ≤ 50 | — |
| Vecteezy | ≤ 150 chars | ≤ 50 | — |
| Pond5 (video) | descriptive | ≤ 50 | Clip length & codec rules apply |

Treat the numbers above as defaults; re-verify if the platform has changed them.

## Method

1. **Structural checks.** Required columns present, correct platform template,
   no empty title/keyword fields, correct delimiter and quoting, UTF-8.
2. **Length checks.** Title and description within limits per platform; flag
   every overflow with the exact count.
3. **Keyword hygiene.** Remove duplicates (case-insensitive, singular/plural
   and close variants), remove generic filler (`image`, `photo`, `stock`,
   `background` alone), and remove terms not present or implied by the asset.
4. **Relevance check.** If assets are available, confirm keywords describe the
   actual content — mismatched keywords cause rejection and de-ranking.
5. **Compliance check.** Flag trademarks, brand names, celebrity names, news
   events, sensitive/medical/legal claims, and anything requiring a model or
   property release that is not declared.
6. **Category check.** Each asset has a valid category for the platform;
   editorial assets are flagged editorial.
7. **Repair, do not just report.** Emit a corrected row for every failure, and
   keep the original next to it so the change is auditable.
8. **Re-run until clean.** Loop QA → fix → re-QA on the corrected set.

## Output

```text
file,field,platform,issue,severity,original,fixed
```

Severity: `blocker` (upload will fail / policy risk), `warn` (de-rank risk),
`info` (style suggestion). Plus a final "ready to upload" count.

## Quality checklist

- Every blocker has a concrete fix applied, not just a description.
- Duplicate detection is case- and variant-insensitive.
- No keyword survives that the asset cannot justify.
- Limits are cited per platform, and re-checked rather than assumed.
- The corrected CSV round-trips: it parses and passes a second QA pass.
