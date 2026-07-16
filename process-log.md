# Process Log

This project compares two distinct pipelines built from the same source
script:
1. **Audio-only TTS** (Google AI Studio, Gemini 3.1 Flash TTS) — voice
   generated independently, no visual component.
2. **Full video with native voice + lip-sync** (Gemini video generation /
   Veo) — dialogue embedded directly in the prompt, so the tool generates
   its own voice and syncs lip movement to it.

Each pipeline was run twice, with a different persona/voice, as the two
required distinct approaches.

---

## Attempt 1: Audio generation — Gacrux voice

- **Timestamp:** 2026-07-14, ~19:47
- **Tool + version/tier:** Google AI Studio, Gemini 3.1 Flash TTS (Preview) — free tier, aistudio.google.com
- **Goal:** Generate a career-advisor-style narration of the script using a mature/mid-pitch voice
- **Exact prompt / settings used:**
  - Scene: "Read the following script in a professional, friendly career-advisor tone"
  - Sample Context: "Professional presentation style. Clear pacing. Confident and informative tone. Speaking to graduate students seeking career advice. Natural pauses between key points. Sound knowledgeable, supportive, and professional."
  - Speaker: Gacrux (mature, middle pitch)
  - Inline audio tag used: [enthusiastic] on opening line
  - Script: full narrative (graduate-student career-advisory text)
- **Output:** `Generated_Audio_July_14_2026_7_51PM.wav` — saved as `artifacts/audio_gacrux_SYNTHETIC.wav`
- **What happened:** Generation completed in a single pass with no errors or refusals. The tool produced a complete reading of the full script at once — no length cap encountered, unlike the video pipeline. Runtime shown in the AI Studio player was 0:26 for the sample line tested during setup; full-script runtime will be longer. [Confirm and note the actual full-script duration once played back.]
- **Verdict:** Pass — tool executed as expected with no technical failures. Qualitative delivery assessment is in `evaluation.md`.
- **Time spent:** ~10–15 minutes including prompt iteration and settings adjustment.

---

## Attempt 2: Audio generation — Zephyr voice

- **Timestamp:** 2026-07-14, ~20:02–20:05
- **Tool + version/tier:** Google AI Studio, Gemini 3.1 Flash TTS (Preview) — free tier
- **Goal:** Generate the same script with a brighter, higher-pitched voice as a direct comparison to Attempt 1
- **Exact prompt / settings used:**
  - Scene: "Read the following script as a professional career advisor speaking to graduate students. Maintain a confident, informative, and encouraging tone. Use natural pacing and clear pronunciation. Pause briefly between major ideas."
  - Sample Context: "Professional presentation. Career coaching session. Supportive and knowledgeable. Natural pacing. Suitable for a university audience."
  - Speaker: Zephyr (bright, higher pitch)
  - Script: identical to Attempt 1
- **Output:** `Generated_Audio_July_14_2026_8_05PM.wav` — saved as `artifacts/audio_zephyr_SYNTHETIC.wav`
- **What happened:** Generation completed without errors. Prompt wording was refined slightly from Attempt 1 (more explicit instruction to "pause briefly between major ideas") to test whether more directive phrasing changed pacing behavior. [Note whether pacing actually changed as a result, once compared by ear against Attempt 1.]
- **Verdict:** Pass — tool executed as expected. Qualitative comparison to Gacrux is in `evaluation.md`.
- **Time spent:** ~10 minutes, faster than Attempt 1 since the workflow was already familiar.

---

## Attempt 3: Video generation — Persona 1 ("professional woman, 40s")

- **Timestamp:** 2026-07-15
- **Tool + version/tier:** Gemini video generation (Veo, via gemini.google.com), Flash mode, Landscape 16:9 — free/student tier
- **Goal:** Generate a full talking-head video with native voice and lip-sync, using dialogue embedded directly in the prompt
- **Exact prompt used:**
  > A professional woman in her 40s with a warm, confident demeanor sits at a modern desk in a softly lit office, speaking directly to camera. She wears business-casual attire, gestures naturally and calmly while talking, maintains steady eye contact with the lens, and occasionally nods thoughtfully. Soft neutral background with blurred bookshelves. Static camera, medium shot, realistic lighting, professional presentation style. She says: "Hello and welcome. Navigating today's competitive job market as a graduate student can..." [continued with full script]
- **Output:** `A_professional_woman_in_her_.mp4` — saved as `artifacts/video_persona1_SYNTHETIC.mp4`
- **What happened:** Generation took several minutes (UI displayed "Generating your video... this could take a few minutes"). The resulting clip was confirmed via `ffprobe` to be exactly **10.005 seconds**, 1280×720, 24fps, H.264/AAC — far short of the full script, which runs to several hundred words. At natural speaking pace (~150 wpm), 10 seconds covers only about 20–25 words, meaning the video cuts off after roughly the first sentence rather than completing the monologue. This is a hard limitation of the free tier, not a setting that could be adjusted in the prompt. Visual inspection of frames at 0s, 4s, and 9.5s showed a stable background, coherent hand position, and consistent lighting throughout — no visible warping or flicker in the sampled frames.
- **Verdict:** Partial — visual generation succeeded with high fidelity, but the tool could not fulfill the "30 seconds to 2 minutes" target length from a single generation.
- **Time spent:** ~5 minutes generation wait + prompt-writing time (~10 minutes total).

---

## Attempt 4: Video generation — Persona 2 ("young professional, late 20s")

- **Timestamp:** 2026-07-15
- **Tool + version/tier:** Gemini video generation (Veo, via gemini.google.com), Flash mode, Landscape 16:9 — free/student tier
- **Goal:** Second distinct persona/voice, using the same pipeline as Attempt 3, to compare tone and visual style
- **Exact prompt used:**
  > A friendly young professional in their late 20s sits in a bright, modern coworking space, speaking energetically and directly to camera. Warm natural lighting, plants and soft-focus background, subtle hand gestures, engaged and enthusiastic facial expression, occasional smile. Static camera, medium shot, clean contemporary aesthetic. She says: "Hello and welcome. Navigating today's competitive job market as a graduate student can..." [continued with full script]
- **Output:** `A_friendly_young_professional.mp4` — saved as `artifacts/video_persona2_SYNTHETIC.mp4`
- **What happened:** Same generation behavior as Attempt 3 — confirmed via `ffprobe` to be exactly **10.005 seconds**, same resolution/frame rate/codec. Same early cutoff issue relative to the full script. Frame inspection at 0s, 4s, and 9.5s showed the persona's more animated, energetic demeanor came through visually (more visible hand movement and smiling than Persona 1), and the coworking-space background (glass partitions, plants) remained stable with no flicker or geometry drift across sampled frames.
- **Verdict:** Partial — same strengths and same length limitation as Attempt 3. Useful direct comparison point: the model responded to differing tonal cues ("calm/confident" vs. "energetic/friendly") with visibly different lighting, setting, and body language, not just a different face.
- **Time spent:** ~5 minutes generation wait + prompt-writing time (~10 minutes total).

---

## Attempt 5: Detection / provenance check

- **Timestamp:** 2026-07-15, 21:05–21:08 UTC
- **Tool + version/tier:** Deepware Scanner (beta), scanner.deepware.ai — free, no account required
- **Goal:** Test whether a public deepfake detector could confidently identify the Veo-generated videos as synthetic
- **What happened:** Both videos were scanned independently:
  - Persona 2 (`A_friendly_young_professional.mp4`, 2.4 MB): result landed in the **yellow/middle zone** of the gauge — inconclusive, not a confident "real" or "fake" read.
  - Persona 1 (`A_professional_woman_in_her_.mp4`, 2.4 MB): same **yellow/middle zone** result.
  - Neither scan returned a numeric confidence score or any stated reasoning — just the gauge position. Deepware's own disclaimer notes the scanner is in beta and results "should not be treated as an absolute truth or evidence."
- **Verdict:** Notable finding — both videos, despite being 100% AI-generated with certainty, produced an inconclusive rather than confidently-flagged result. Full write-up and interpretation in `detection-results.md`.
- **Time spent:** ~5 minutes (upload + wait for both scans).

---

## Notes on Tool Refusals / Content Filters

No refusals or content-filter triggers were encountered across any tool in
this project. All prompts used neutral, professional, non-sensitive
descriptive language (career-advisory script content, generic
professional personas, no real named individuals). This itself may be a
finding worth noting in `evaluation.md`: the tools were not stress-tested
against their actual safety boundaries, since the content never approached
them.

## Total Time Spent (rough cost-in-hours comparison)

| Tool / Pipeline | Time spent | Outcome |
|---|---|---|
| Gemini TTS (Gacrux) | ~10–15 min | Full-length audio, no length cap issue |
| Gemini TTS (Zephyr) | ~10 min | Full-length audio, no length cap issue |
| Gemini Video — Persona 1 | ~10–15 min (incl. wait) | High visual fidelity, capped at 10s |
| Gemini Video — Persona 2 | ~10–15 min (incl. wait) | High visual fidelity, capped at 10s |
| Deepware detection check (both videos) | ~5 min | Inconclusive result both times |

**Overall observation:** the audio pipeline was both faster to iterate on
and free of the length constraint that limited the video pipeline. The
video pipeline's per-attempt cost was similar in wall-clock time, but a
meaningful fraction of that was passive generation wait rather than active
prompt-engineering effort.