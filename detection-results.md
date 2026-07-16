Detection / Provenance Check

Check 1: Deepware Scanner (beta)


Tool: Deepware Scanner — https://scanner.deepware.ai (beta)
File scanned: video_persona2_SYNTHETIC.mp4 (originally A_friendly_young_professional.mp4)
File size: 2.4 MB
Timestamp: 2026-07-15, 21:05:53 UTC
Result: Gauge needle landed in the yellow/middle zone — not a confident "real" (green) or "fake" (red) classification.


What the tool actually gave me

A single visual gauge with no numeric confidence score and no explanation of
why it landed where it did. There was no frame-by-frame breakdown, no
flagged region of the video, and no stated reasoning — just the needle
position. Deepware's own disclaimer notes the scanner is in beta and results
"should not be treated as an absolute truth or evidence."

My assessment of the tool's performance

This is a real finding, not a null result: the detector was not able to
confidently classify a video I know for certain is 100% AI-generated
(Google Gemini/Veo output, dialogue and visuals both synthetic from the
prompt stage). An inconclusive reading on a clear-cut synthetic video
suggests either:


Deepware's detection models aren't well-tuned to the visual signatures
Veo produces (a newer generation model than what many detectors are
trained against), or
The short clip length (10 seconds) gave the detector less temporal
signal to work with than it would have on a longer clip.


Either way, this supports the broader pattern noted in the assignment's
research questions: detection tools are lagging behind current
generation quality, and a beta tool handing back an unexplained score
with no reasoning is not something I would rely on for a real
provenance decision.


Check 2: Deepware Scanner (beta) — second video


Tool: Deepware Scanner — https://scanner.deepware.ai (beta)
File scanned: video_persona1_SYNTHETIC.mp4 (originally A_professional_woman_in_her_.mp4)
File size: 2.4 MB
Timestamp: 2026-07-15, 21:07:48 UTC
Result: Gauge needle again landed in the yellow/middle zone — same
inconclusive read as Persona 2.


Why this second result matters

Getting the same "yellow/inconclusive" result on both videos rules out the
possibility that Check 1 was a one-off fluke tied to a specific persona,
prompt, or lighting setup. Two independently generated Veo clips, different
personas, different settings and backgrounds, same detector, same
inconclusive outcome. That consistency is itself the finding: Deepware's
current detection model does not reliably distinguish this generation of
Gemini/Veo output from real footage — at least not confidently enough to
land the needle in clearly green or red territory either time.

As with Check 1, no numeric score, no frame-level explanation, no stated
reasoning was given for either result — just the gauge position.

Follow-up worth trying (not yet done)


Scan the audio-only files (if the tool supports audio) to see if
detection differs by content type.
Check whether the Gemini/Veo output embeds C2PA content credentials
natively, and whether they survive the download.