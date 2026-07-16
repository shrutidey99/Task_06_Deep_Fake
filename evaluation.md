# Critical Evaluation

Honest assessment of each artifact produced. Use precise language — avoid
vague terms like "looks fake" or "sounds real" in favor of specific failure
modes (prosody, lip-sync drift, blinking, temporal instability, etc.).

This project compares two pipelines: **audio-only TTS** (no visual) vs.
**full video with native voice + lip-sync** (Gemini video generation).
Because the video pipeline generates its own voice from the embedded
dialogue, the TTS audio tracks and the video artifacts are independent —
they were never combined.

---

## Artifact 1: Gacrux voice — Gemini 3.1 Flash TTS (audio only)

**Where does it hold up?**
(Was the pacing convincing? Did the tone match "career advisor" well? Did
the [enthusiastic] tag produce an audible shift in delivery?)

**Where does it fail?**
Be specific: unnatural pauses, robotic cadence, mispronunciations, flat
delivery on emotionally significant lines, breath sounds (or lack of them).

**Would this fool someone?**
Would you be fooled by this if you didn't know it was synthetic? Would
someone outside this field?

**What did the tool refuse or degrade on?**

---

## Artifact 2: Zephyr voice — Gemini 3.1 Flash TTS (audio only)

**Where does it hold up?**


**Where does it fail?**


**Would this fool someone?**


**What did the tool refuse or degrade on?**


---

## Artifact 3: Video — Persona 1 (professional woman, 40s), Gemini video generation

**Where does it hold up?**
(How convincing was Veo's own voice? Did lip movement match the spoken
words? Did gestures/expression look natural?)

**Where does it fail?**
Be specific:
- Lip-sync drift: any moments where mouth movement lagged or didn't match
  phonemes
- Did the generated clip cover the full script, or cut off partway
  (Veo free-tier clips are often short — note actual duration vs. script length)
- Visual: blinking rate, hand gesture repetition, background stability,
  any warping/flickering
- Voice: prosody, emotional register, any robotic quality despite the
  photorealistic visual

**Would this fool someone?**


**What did the tool refuse or degrade on?**

---

## Artifact 4: Video — Persona 2 (young professional, late 20s), Gemini video generation

**Where does it hold up?**


**Where does it fail?**


**Would this fool someone?**


**What did the tool refuse or degrade on?**

---

## Comparing the Two Pipelines

Key comparison for this task: **TTS-only audio (no visual, no lip-sync
concern) vs. full video with native voice + lip-sync (visual realism
attempted, but voice and face both AI-generated simultaneously)**.

- Which pipeline was more convincing overall, and why?
- Did generating voice and face together (video pipeline) produce a more
  or less natural-sounding voice than the dedicated TTS tool?
- Which persona (1 or 2) held up better, and what about the prompt made
  the difference — art direction, described demeanor, tone instructions?
- What would each artifact need to become genuinely convincing?

-

## Comparison to a Real Recording (if attempted)

If you compared your best synthetic output to a real recording of the same
script, what is still different?

-