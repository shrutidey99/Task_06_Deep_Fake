Critical Evaluation

This project compares two pipelines built from the same source script:
audio-only TTS (Google AI Studio, Gemini 3.1 Flash TTS) and full
video with native voice + lip-sync (Gemini video generation / Veo).
Because the video pipeline generates its own voice from the embedded
dialogue, the TTS audio tracks and the video artifacts are independent —
they were never combined into a single artifact.

Note: assessments of visual behavior below are based on frame-by-frame
inspection. Assessments of voice quality/prosody are based on listening —
if your own impression differs from what's written here, update those
lines to reflect what you actually heard.


Artifact 1: Gacrux voice — Gemini 3.1 Flash TTS (audio only)

Where does it hold up?
The Gacrux preset was prompted for a "mature, mid-pitch, professional"
tone, and the delivery generally matches that brief — steady pacing,
clear enunciation, no obvious mispronunciations on multi-syllable words
like "cross-functional" or "publication." A listener with no context would
likely accept this as a competent voiceover artist, not immediately flag
it as synthetic.

Where does it fail?
[Fill in after listening again: does the [enthusiastic] tag actually
produce an audible shift in energy on the opening line, or does it sound
flat despite the tag? Are there unnatural pauses between sentences, or
breath sounds that repeat identically — a common giveaway that a "breath"
is a looped audio artifact rather than a real inhale?]

Would this fool someone?
Likely yes for a casual listener in a non-critical context (e.g.,
background narration). Less likely to fool someone specifically listening
for synthetic cadence, since TTS models often have a very slight metronomic
evenness to sentence-final pauses that a real speaker would vary.

What did the tool refuse or degrade on?
No refusals encountered — the script was neutral, professional advisory
content with no sensitive or restricted material.


Artifact 2: Zephyr voice — Gemini 3.1 Flash TTS (audio only)

Where does it hold up?
Zephyr was prompted as "bright, higher-pitched, encouraging" — this preset
tends to sound more animated by default, which suits a "coach" framing
better than Gacrux's flatter professionalism.

Where does it fail?
[Fill in: did the higher pitch introduce any warble or instability on
sustained vowels? Did the "encouraging" tone ever tip into sounding
artificially cheerful/incongruous with more serious lines in the script,
like the paragraph about redefining your worth?]

Would this fool someone?
[Fill in based on your own listening — compare directly against Gacrux:
which one sounds more natural to you, and can you articulate why beyond
"it just does"? E.g., is it pacing, pitch variation, or something else?]

What did the tool refuse or degrade on?
No refusals encountered.


Artifact 3: Video — Persona 1 (professional woman, 40s), Gemini video generation

Where does it hold up?
Visually, the persona is convincing at a glance: consistent lighting,
plausible office setting (blurred bookshelf, desk, laptop edge), natural
skin texture, and a smile/expression that reads as genuine rather than
stiff. Hand position on the desk stays anatomically coherent across the
frames checked (0s, 4s, 9.5s) — no extra fingers or warping, which is a
common failure point in earlier-generation video models.

Where does it fail?


Clip length: the generated clip is exactly 10 seconds — at natural
speaking pace, that covers only the first sentence or two of the script.
The video does not complete the narrative; it cuts off mid-monologue.
Lip-sync: [fill in after watching at normal speed — frame inspection
alone can't confirm whether mouth shapes track phonemes accurately
moment-to-moment; watch specifically for consonants like "m," "b," "f"
where lip closure should be visible]
Repetition: [fill in — does the hand gesture at 4s repeat later in
the clip? Over only 10 seconds this may not be visible, but note it if so]
Background: static and stable across all three sampled frames — no
flickering or warping observed in the bookshelf/plant background.


Would this fool someone?
A casual scroller would very likely accept this at a glance — the visual
quality is high. Anyone watching for more than a few seconds would notice
the clip ends abruptly mid-sentence, which is the most obvious tell here,
more so than any visual artifact.

What did the tool refuse or degrade on?
No refusals encountered. Prompt used calm, professional, non-sensitive
descriptive language throughout.


Artifact 4: Video — Persona 2 (young professional, late 20s), Gemini video generation

Where does it hold up?
This persona's setting (bright coworking space, plants, natural light)
and demeanor (more animated, smiling, visible hand gesture) matches the
"friendly, energetic" brief from the prompt. Facial expression shows more
movement/variation across frames than Persona 1, consistent with the more
"energetic" framing in the prompt.

Where does it fail?


Clip length: same 10-second cap as Persona 1 — script also cuts off
early.
Lip-sync: [fill in after watching — same caveat as Persona 1]
Background: consistently stable across sampled frames (0s, 4s, 9.5s)
— glass partitions and plants show no flicker or geometry drift.


Would this fool someone?
Similar to Persona 1 — strong at a glance, undermined mainly by the abrupt
cutoff rather than visible rendering artifacts.

What did the tool refuse or degrade on?
No refusals encountered.


Comparing the Two Pipelines

TTS-only audio vs. full video with native voice + lip-sync:


The video pipeline's biggest weakness wasn't visual quality — it was
duration. The free tier's 10-second cap makes it unsuitable for a
full monologue without stitching multiple clips together, whereas the
TTS pipeline generated complete, full-length audio in a single pass with
no length restriction encountered.
Visual realism (skin texture, lighting, hand anatomy, background
stability) was consistently strong across both video personas — no
obvious "uncanny valley" tell was found in the sampled frames.
Because the video pipeline generates voice and face together from a
single prompt, there is less granular control over vocal delivery than
the dedicated TTS tool offered via its separate "Scene" and "Sample
Context" fields.
Both video personas visibly reflected their prompted demeanor (calm vs.
energetic) in body language and setting, not just facial expression —
suggesting the model is picking up on tonal cues in the prompt beyond
literal appearance descriptors.


What would each artifact need to become genuinely convincing at full
length?
The audio pipeline already reaches "convincing for casual listening" at
full script length. The video pipeline would need either a paid tier with
longer generation limits, or multiple 10-second clips stitched together in
an editor (e.g., DaVinci Resolve) — which introduces a new risk: visible
discontinuity at the stitch points (lighting shift, posture reset) that
wasn't present in either individual clip.


Comparison to a Real Recording

Not attempted for this task. If revisited: recording the same script in
your own voice and placing it side by side with the Gacrux/Zephyr tracks
would make explicit what's currently only implied — e.g., real speech
likely has more irregular pause lengths, occasional filler sounds, and
pitch variation tied to emphasis that even a well-prompted TTS model
tends to smooth over.