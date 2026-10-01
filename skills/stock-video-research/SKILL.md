---
name: stock-video-research
description: Watch and analyze a video to extract research value — competitor launches, ad creative, viral hooks, tutorial structure, or a screen-recorded bug — by downloading, sampling frames, and transcribing audio. Use when someone shares a video URL or local file and asks what happens, how the hook works, what tools are shown, or when a bug appears. Trigger on "watch this video", "analyze this video", "video research", "bedah video", "riset video", or a pasted YouTube/TikTok/Loom/Instagram link. Not for producing video (/motionforge) or writing metadata (/stock-metadata-qa).
---

# Stock Video Research

Give the agent eyes and ears on a video: download, sample frames, transcribe,
then answer grounded in what is actually on screen and in the audio.

## When to use

- Analyze a competitor's promo, ad, or launch video and extract the structure.
- Reverse-engineer a viral hook from the first three seconds.
- Summarize a long video without watching it at 2x.
- Diagnose a bug from a screen recording.

## Inputs

- A URL (`yt-dlp`-supported: YouTube, Loom, TikTok, X, Instagram, Vimeo…) or a
  local path (`.mp4`, `.mov`, `.mkv`, `.webm`).
- The question to answer.
- Optional time window (`--start` / `--end`) when a moment is named.

## Prerequisites

- `ffmpeg` and `yt-dlp` on PATH.
- A Whisper backend (Groq `whisper-large-v3` preferred, or OpenAI `whisper-1`)
  only when the video has no caption track.
- No private platforms: this skill does not log in anywhere.

## Method

1. **Preflight.** Confirm `ffmpeg`/`yt-dlp` exist; if not, print the exact
   install command for the OS and stop.
2. **Acquire.** URL → download to a temp working dir; local file → probe in place.
3. **Sample frames** with a duration-aware budget (token cost is dominated by
   frames):
   - ≤30 s → ~30 frames; 30–60 s → ~40; 1–3 min → ~60; 3–10 min → ~80;
     >10 min → 100 and print a "sparse scan" warning.
   - Hard caps: 2 fps, 100 frames. Default 512 px wide; use 1024 px when
     on-screen text must be read.
   - If the user names a moment, use focused mode — denser per-second budget.
4. **Transcribe.** Prefer native captions; fall back to Whisper on a mono
   16 kHz extract. Keep timestamps.
5. **Read the frames** (as images) and the transcript together.
6. **Answer** with timestamps, citing what was seen and heard. Separate
   observation from inference.
7. **Clean up** the temp working dir unless follow-ups are coming.

## Output

- Direct answer with `t=MM:SS` citations.
- For structural analysis: a beat sheet of the video (what happens when).
- For hook analysis: the first 3 seconds described frame by frame.
- The working dir path if the user wants to keep frames.

## Quality checklist

- The answer cites timestamps, not vague descriptions.
- No claim is made about a moment that was not sampled.
- Frame budget respected; long videos warn instead of silently scanning.
- Local-file workflows leave the source untouched.
- Temp files removed when no follow-up is expected.
