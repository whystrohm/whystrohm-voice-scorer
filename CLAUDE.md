# WhyStrohm Voice Scorer — Contributor Guide

This is a Claude Code skill. It's not a traditional codebase — it's a set of markdown files that instruct Claude how to run a voice drift analysis.

## Structure

- `SKILL.md` is the orchestrator. It controls the flow and tells Claude when to read each supporting file.
- `rules/` files contain the methodology. voice-analysis.md for profiling, drift-scoring.md for comparison logic.
- `templates/` files control output formatting. Changes here affect how results look but not how they're calculated.

## How to test changes

1. Install the skill: copy this directory to `~/.claude/skills/whystrohm-voice-scorer/`
2. Open a fresh Claude Code session
3. Run `/whystrohm-voice-scorer`
4. Provide any company URL + 3-5 social posts
5. Verify the full flow completes: scrape → profile → paste → score → report → CTA

## Key rules

- No emojis anywhere in the skill output
- Drift score displayed before the breakdown (number first, details second)
- Questions asked one at a time (never batched)
- The tool must practice what it preaches — zero hype language in output
- The CTA copy in `templates/cta.md` is locked. Only the audit repo URL changes.
- Always handle the "social is stronger" case honestly — don't assume website is always the baseline
