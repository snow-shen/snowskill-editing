# SnowSkill Editing

A shareable talking-head editing workflow for AI coding assistants. 中文口播 / 英文讲解均可；首次检查环境，所有选项由使用者选择。

## What it does

Assess available tools → ask about format, style, voice and transcription → plan the script and style preview → edit and animate using available tools → check and package the result.

**No defaults:** no preselected style, voice, transcription provider, platform or aspect ratio. Fish Audio and ElevenLabs are optional. Existing subtitles, local Whisper and authorized cloud transcription are alternative routes. Voice cloning is not required for transcription.

Read [STYLE-SHEET.md](STYLE-SHEET.md) for optional visual directions, including Snow’s paper-and-doodle look. None is automatically applied.

## Install

Copy this entire folder into your assistant’s supported skills directory, using the folder name `snowskill-editing`. For Claude Code, a user-level example is `~/.claude/skills/snowskill-editing/`; for Codex, `~/.codex/skills/snowskill-editing/`. Refresh the client and check that it discovers the skill. Other clients should follow their own installation instructions.

Example request:

> Use snowskill-editing. Check my environment first, then ask me to choose the style, format, voice and transcription route. Explain any downloads, uploads or costs before proceeding.

## Included

- `SKILL.md`: provider-neutral workflow and onboarding instructions.
- `STYLE-SHEET.md`: optional styles and a record of selected choices.
- `README.md`: installation and scope.

This is an instruction package, not a standalone video editor. It does not include rendering scripts, model weights, fonts, media, personal voice samples, credentials or private project logs. The assistant must use or implement tools available in the creator’s environment.
