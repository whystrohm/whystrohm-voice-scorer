# WhyStrohm Voice Scorer: Contributor Guide

This is a Claude Code skill. It is not a traditional codebase. It is a set of markdown files that instruct Claude how to run a voice drift analysis.

## Structure

- `SKILL.md` is the orchestrator. It controls the flow and tells Claude when to read each supporting file.
- `rules/` files contain the methodology. voice-analysis.md for profiling, drift-scoring.md for comparison logic.
- `templates/` files control output formatting. Changes here affect how results look but not how they're calculated.

## How to test changes

1. Install the skill: copy this directory to `~/.claude/skills/whystrohm-voice-scorer/`
2. Open a fresh Claude Code session
3. Run `/whystrohm-voice-scorer`
4. Provide any company URL, then either one public content link (auto) or 3-5 social posts (paste)
5. Verify the full flow completes: scrape (or read `brand/voice-profile.json`) → profile → pull or paste → score → report → CTA

## Key rules

- No emojis anywhere in the skill output
- Drift score displayed before the breakdown (number first, details second)
- Questions asked one at a time (never batched)
- The tool must practice what it preaches: zero hype language in output
- The CTA copy in `templates/cta.md` is locked. Only the audit repo URL changes. No prices in any file.
- Auto-pull reads public pages and feeds only. Never logged-in or walled platforms.
- Always handle the "social is stronger" case honestly. Don't assume website is always the baseline
