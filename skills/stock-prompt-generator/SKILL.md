---
name: stock-prompt-generator
description: Build, version, and reuse image/video generation prompts tuned for microstock sellability. Use to turn a keyword cluster into batch prompts, enforce composition rules buyers need (copy space, isolated subject, no text, no logos), keep a consistent style across a batch, and adapt prompts per model (Midjourney, Flux, SDXL, Gemini, Veo, Kling, Seedance). Trigger on "prompt generator", "prompt batch", "prompt microstock", "buat prompt", or when turning a research plan into actual assets. Not for keyword/title writing (/stock-metadata-qa) or niche selection (/stock-competitor-niche-research).
---

# Stock Prompt Generator

Convert a keyword cluster into a batch of generation prompts that are
**commercially safe, compositionally sellable, and stylistically consistent**.

## When to use

- You finished keyword/niche research and need prompts to produce the assets.
- A batch must look like one coherent series, not random one-offs.
- Prompts keep producing text, logos, watermarks, or unusable framing.

## Inputs

- **Keyword cluster / concept list** from keyword or niche research.
- **Model** — Midjourney, Flux, SDXL, Gemini image, Veo, Kling, Seedance, other.
- **Asset type** — photo, vector-style, 3D render, or video clip.
- **Style lock** — palette, lighting, lens, rendering style, aspect ratios.

## Method

1. **Build a style lock block.** One reusable string with palette, lighting,
   render style, and camera/lens. Every prompt in the batch repeats it verbatim
   so the series matches.
2. **Compose each prompt** from ordered blocks:
   `[subject] + [action/context] + [composition] + [style lock] + [quality] + [negative]`.
3. **Enforce commercial rules** in every prompt:
   - include copy space / negative space when the concept sells for banners;
   - `no text, no watermark, no logo, no signature` in the negative;
   - avoid named brands, celebrities, and trademarked characters;
   - keep hands/faces out unless the concept needs them, to cut defect rates.
4. **Add composition variants** per concept so one keyword yields a set:
   isolated on white, top view, wide with copy space, close-up detail,
   vertical 9:16 for social, horizontal 16:9 for web.
5. **Adapt per model.** Keep one canonical prompt, then emit model-specific
   syntax (Midjourney `--ar --style --no`, Flux/SDXL weighted tokens, video
   models get a motion clause plus duration/fps intent).
6. **Plan the batch.** Group prompts so a single generation session covers a
   coherent series; number them `concept-01..N` and keep a manifest.
7. **Self-check before generation.** Flag prompts likely to fail review:
   recognizable IP, sensitive news context, real people, medical/legal claims.

## Output

- `prompts.csv` — `id,concept,asset_type,model,prompt,negative,aspect_ratio,variants`
- A copy-paste block per model with the style lock already applied.
- A short note listing prompts you deliberately excluded and why.

## Quality checklist

- The style lock string is byte-identical across the batch.
- Every prompt carries the no-text/no-logo negative.
- Aspect ratios match the target platforms, not a default.
- No prompt implies a real person, brand, or protected character.
- The manifest maps every prompt back to the keyword cluster it serves.
