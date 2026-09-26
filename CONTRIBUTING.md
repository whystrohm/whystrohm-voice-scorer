# Contributing to WhyStrohm Voice Scorer

Thanks for your interest in improving this skill.

## Reporting Issues

If the skill misscores content or breaks during the flow, open an [issue](https://github.com/whystrohm/whystrohm-voice-scorer/issues) and include:

- Your Claude Code version (`claude --version`)
- Which step broke (scrape, profile, pull or paste, scoring, report, CTA)
- What you expected and what happened
- The website URL and content you scored, or a sanitized version

## Pull Requests

1. Fork the repo
2. Create a branch (`git checkout -b improve-drift-scoring`)
3. Make your changes
4. Test by running `/whystrohm-voice-scorer` in a fresh Claude Code session, once with auto-pull and once with paste
5. Submit a PR with a clear description of what changed and why

## Rules for Changes

- No emojis in any file.
- No hype language in any template.
- No prices in any file.
- Auto-pull reads public pages and feeds only. Never add a step that logs in or uses cookies.
- Don't change the CTA copy without the maintainer's sign-off.

## Code of Conduct

See [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
