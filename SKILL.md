---
name: snowskill-editing
description: Create speech-led explainer videos with a real-person hook and animated visual beats. Onboard the creator, assess available tools, and choose recorded voice, ordinary TTS or optional voice cloning; support existing subtitles, cloud transcription or local Whisper without requiring one provider.
---

# Portable talking-head explainer

This is a provider-neutral workflow skill, not a bundled video renderer. Do not assume scripts, templates, assets, other skills or accounts exist. Use the creator’s language. No particular model version is required; the original Opus name is not a dependency.

## No defaults

Do not assume a platform, aspect ratio, language, aesthetic, voice provider, transcription provider, background treatment or paid plan. Detection shows what is available, not what the user selected. Read STYLE-SHEET.md to present optional looks. Ask for a selection or a custom reference; no response means the choice remains unresolved. Continue only work independent of it.

## First use: assess, then ask

Start with read-only checks in the user-selected project. Check OS, available disk space and relevant commands (ffmpeg, ffprobe, node, python3, whisper-cli, whisper, hyperframes). Inspect installed packages or available tool descriptions when needed. Do not run npx to probe: it can download packages. Check whether named API environment variables are set as booleans only; never print values or read unrelated home-directory secrets. Command presence is not proof that a model, account, quota or GPU works.

Report a small capability table: capability / detected / still needed. Then ask one compact onboarding question covering only unresolved choices:
- Target language, platform and 16:9 or 9:16?
- Voice: keep the recording, ordinary synthetic voice for a preview, or optional authorized clone?
- Transcription: existing SRT/VTT, local Whisper for offline processing, or an available cloud service?
- May media leave this computer, and what is the spending limit? Unknown means no upload and no paid call yet.
- Visual preference: original background, cutout on paper, or another look?

Present viable routes and their tradeoffs based on actual capability; wait for the user to choose voice, transcription, style and output format before dependent work. Do not preselect any route; do not require the creator to register for every provider. Save choices and capability evidence in project-local HANDOFF.md. Recheck affected capabilities when an error occurs or the user changes environments, not on every invocation. Missing optional services must not block planning, script writing or a storyboard.

## Voice and transcription are separate

Transcription turns existing speech into text and timestamps. TTS creates speech from text. A voice clone is optional TTS and is never required for captions or editing.

Voice routes:
1. Recorded voice: preserve source recordings; cut a clean take and align captions to the final audio. No cloning account required.
2. Ordinary TTS: use an installed local engine, a user-configured service, or Edge TTS if available. Edge TTS requires network access and is not offline. Check the actual voice and language before generating the whole script.
3. Clone: Fish Audio or ElevenLabs only when selected and configured by this creator. Ask for their own voice ID and authorized voice material; never reuse another creator’s ID. Keep keys in environment variables or a local ignored config, never in the skill. Check current provider documentation, model availability and price; do not assume a historical free model remains free. Generate a short sample first.
4. No engine: write the script and recording directions; use supplied audio later. Do not silently replace the creator’s voice.

Transcription routes:
1. Existing SRT/VTT: inspect whether it matches the final cut. Segment captions do not provide word-level timing.
2. Local Whisper: use the installed implementation (whisper.cpp, faster-whisper or OpenAI Whisper). Check model files, language, CPU/GPU support and available resources. Explain model downloads and likely CPU load; obtain permission before installing or downloading. Test a short excerpt; choose model size based on the result. Syntax varies: inspect local help rather than inventing flags.
3. Cloud: Groq, ElevenLabs or another configured service. Verify file limits, timestamps and actual access with an authorized short sample. Require upload permission. Do not describe a service as free without checking.
4. Manual captions: acceptable for a short clip if no transcriber is available. Disclose that timing is manual.

On expired credentials or quota failure, explain the specific unavailable capability, offer local transcription / supplied subtitles / another authorized provider. Never silently upload to a fallback service or incur charges. Do not infer permission from the presence of a key.

## Production workflow

1. Identify the clip from its content and the chosen project; do not assume the newest download belongs to this task. Check for concurrent writes before editing.
2. Collect real notes, screenshots and source footage from the user-selected project. Missing facts remain unknown. Do not scan personal history, unrelated accounts or Downloads without a task reason.
3. Agree a concept, one understandable metaphor and a short outline. Humor, creator representation and pacing are preferences to ask about, not inherited personal rules. Do not invent experiences or results.
4. Write narration as scene data: one sentence per caption and visual beat. Keep facts and sources separate. Choose platform-specific wording with the creator; do not promise that euphemisms prevent moderation.
5. Show two or three actual style frames or a playable hook preview when the look is new. Include remaining work, estimated time and known costs. A script approval is not a style approval. Respect explicit permission to proceed without previews.
6. Lock the chosen voice, then build sentence timings against the actual audio. Timestamps must be recomputed after a cut, speed change or pause removal. Word-level animation requires verified word timestamps or a disclosed manual alignment.
7. Use the available renderer. If HyperFrames is installed and its skill is available, read its current instructions before writing compositions. Otherwise offer an available editor or storyboard-only output; do not pretend the renderer exists. Background removal, image generation and music are optional. Preserve the original background when removal is unavailable. Use user-supplied or licensed assets and record sources in CREDITS.md.
8. Animate from sentence start/end times; every spoken sentence gets a meaningful visual response. Keep state seek-safe. Use a real screen demo for concrete tutorials, readable captions and platform safe areas. Avoid mandatory personal fonts or references to another creator’s projects.
9. Preview before a full render. Check representative frames, transitions, cut continuity, caption accuracy, clipping, voice intelligibility and final audio loudness. Silence can cause Whisper hallucinations: compare suspicious repeats with the actual audio. Do not claim listening or visual review if not performed.
10. Deliver final video, a preview and selected cover/copy formats in final/. Write HANDOFF.md with decisions, tool choices, sources, unresolved issues and next steps. Never mark content published without evidence. Publishing, sending to others and deletion require the user’s instruction. Preserve source media and archive previous renders rather than overwriting them.

## Config and safety

Use project-local paths, no absolute personal paths. Separate reusable workflow from a creator-specific profile. Record language, platform, aesthetic, voice route, transcription route, upload permission and spending ceiling; never store tokens. An optional provider adapter must produce the same contract: audio file plus sentence timings, or transcript plus timestamps with their granularity. Validate that contract before passing it to the next stage.

Do not copy private project logs, voice samples, personal photos, account handles, API credentials or unverified-license assets into a distribution. This package intentionally includes no personal templates or assets. The agent writes or adapts project scripts to the tools actually available and states what is implemented versus proposed.
