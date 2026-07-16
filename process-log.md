# Process Log

Running log of every attempt, in chronological order.

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
- **Output:** `Generated_Audio_July_14_2026_7_51PM.wav` — saved in `artifacts/audio_gacrux_SYNTHETIC.wav`
- **What happened:** (fill in — pacing, any odd pauses, whether the [enthusiastic] tag was audible)
- **Verdict:**
- **Time spent:**

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
- **Output:** `Generated_Audio_July_14_2026_8_05PM.wav` — saved in `artifacts/audio_zephyr_SYNTHETIC.wav`
- **What happened:** (fill in — how did tone/pacing compare to Gacrux?)
- **Verdict:**
- **Time spent:**

---

## Attempt 3: Video generation — Persona 1 ("professional woman, 40s")

- **Timestamp:** 2026-07-15
- **Tool + version/tier:** Gemini video generation (Veo, via gemini.google.com), Flash mode, Landscape 16:9 — free/student tier
- **Goal:** Generate a full talking-head video with native voice and lip-sync, using dialogue embedded directly in the prompt
- **Exact prompt used:**
  > A professional woman in her 40s with a warm, confident demeanor sits at a modern desk in a softly lit office, speaking directly to camera. She wears business-casual attire, gestures naturally and calmly while talking, maintains steady eye contact with the lens, and occasionally nods thoughtfully. Soft neutral background with blurred bookshelves. Static camera, medium shot, realistic lighting, professional presentation style. She says: "Hello and welcome. Navigating today's competitive job market as a graduate student can..." [continued with full script]
- **Output:** `A_professional_woman_in_her_.mp4` — saved in `artifacts/video_persona1_SYNTHETIC.mp4`
- **What happened:** (fill in — how long was the generated clip vs. the full script length? did it cut off mid-script? how convincing was Veo's own voice and lip-sync? any visual artifacts — blinking, hand gestures, background stability?)
- **Verdict:**
- **Time spent:** (include generation wait time — Gemini showed "this could take a few minutes")

---

## Attempt 4: Video generation — Persona 2 ("young professional, late 20s")

- **Timestamp:** 2026-07-15
- **Tool + version/tier:** Gemini video generation (Veo, via gemini.google.com), Flash mode, Landscape 16:9 — free/student tier
- **Goal:** Second distinct persona/voice, using same pipeline as Attempt 3, to compare tone and visual style
- **Exact prompt used:**
  > A friendly young professional in their late 20s sits in a bright, modern coworking space, speaking energetically and directly to camera. Warm natural lighting, plants and soft-focus background, subtle hand gestures, engaged and enthusiastic facial expression, occasional smile. Static camera, medium shot, clean contemporary aesthetic. She says: "Hello and welcome. Navigating today's competitive job market as a graduate student can..." [continued with full script]
- **Output:** `A_friendly_young_professional.mp4` — saved in `artifacts/video_persona2_SYNTHETIC.mp4`
- **What happened:** (fill in — how did Veo's voice for this persona compare to Persona 1? did energetic tone come through in lip movement/expression? any glitches?)
- **Verdict:**
- **Time spent:**

---

## Notes on Tool Refusals / Content Filters

Did Gemini/Veo or AI Studio refuse or degrade on anything? What triggered it?

-

## Total Time Spent (rough cost-in-hours comparison)

| Tool / Pipeline | Time spent | Outcome |
|---|---|---|
| Gemini TTS (Gacrux) | | |
| Gemini TTS (Zephyr) | | |
| Gemini Video — Persona 1 | | |
| Gemini Video — Persona 2 | | |