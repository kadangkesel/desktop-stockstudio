# Generate Metadata — Strict QA

Generates metadata with a stricter prompt than the default workflow, aimed at surviving platform review on the first upload. It walks the same graph — import files, loop, analyze each image with Gemini, parse the JSON, build the metadata, save, export CSV for Adobe Stock — but the analysis prompt enforces hard limits and commercial-safety rules: a natural buyer-phrase title capped at 200 characters, no keyword stuffing or symbols, 25–49 unique lowercase keywords with no duplicates, singular/plural pairs, generic filler, brand names or celebrity names, and a category restricted to Adobe Stock's official list.

The result is a CSV that needs less manual cleanup before upload, which matters when a batch runs to hundreds of files.

## Tags

adobe stock, gemini, metadata, csv, qa, bulk upload

## Author

StockStudio Community
