# Changelog

All notable changes to the WhyStrohm Voice Drift Scorer skill.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). This project uses [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Reads `brand/voice-profile.json` from whystrohm-voice-extract when it exists for the same site, and skips the site scan. Format: `contracts/voice-profile.v1.schema.json`.
- CI checks the schema and that it matches the canonical copy in whystrohm/shotkit.
- Step 4 can pull recent content from one public link (blog, newsletter archive, or YouTube feed). Pasting still works and is the fallback. Public sources only.
- SECURITY.md listing every network call the skill makes.
- CONTRIBUTING.md and this CHANGELOG.

### Changed
- `rules/voice-analysis.md` describes the scorer's use of the profile, not the audit's.
- `rules/drift-scoring.md` states the max drift for categorical dimensions (3) and uses a confidence table that covers every case once.
- CTAs point straight at https://whystrohm.com/scan and https://whystrohm.com/system, with UTM tags in the README.
- Copy pass: no prices, no speed claims, no em dashes.

## [1.0.0] - 2026-03-27

### Added
- Voice drift flow: scrape the website, build a voice profile, collect social posts, score drift, report, CTA.
- Five scored dimensions: authority, formality, emotional temperature, vocabulary pattern, positioning signal.
- Weighted drift score out of 10, direction finding (website stronger, social stronger, or both weak), and exact-quote drift examples.
- Score-first report template and closing CTA to the full audit.
- Social preview image and demo GIF.
- README links to Digital Twin, Content Audit, and Ritual.
