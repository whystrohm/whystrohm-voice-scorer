# WhyStrohm Voice Drift Scorer

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code Skill](https://img.shields.io/badge/Claude%20Code-Skill-7C3AED)](https://claude.ai/code)
[![whystrohm.com](https://img.shields.io/badge/WhyStrohm-whystrohm.com-00D4FF)](https://whystrohm.com)

**A free Claude Code skill that scores how well your social content matches your website voice.**

Does your LinkedIn sound like your website? Your X posts match your brand? Paste your social content, get a drift score out of 10, and see exactly where your voice breaks down across platforms.

<p align="center">
  <img src="demo.gif" alt="WhyStrohm Voice Scorer Demo" width="720">
</p>

---

## How It Works

| Step | What Happens |
|------|-------------|
| **1. Scrape** | Pulls your website to build a voice profile |
| **2. Paste** | You paste 3-5 recent social posts (LinkedIn, X, any platform) |
| **3. Compare** | Scores your social voice against your website voice |
| **4. Report** | Shows drift score, per-dimension breakdown, and exact drift examples |
| **5. Recommend** | Tells you which voice is stronger and what to fix |

## What It Scores

Your voice is analyzed across 5 dimensions:

| Dimension | What It Measures |
|-----------|-----------------|
| **Authority** | Are you direct or hedging? Expert or tentative? |
| **Formality** | Conversational or corporate? Contractions or full words? |
| **Temperature** | Engaging or clinical? Personality or spec sheet? |
| **Vocabulary** | Technical, conversational, hype, or mixed? |
| **Positioning** | "I build" or "We help"? Builder or vendor? |

Drift between your website and social content = lost trust. Readers who follow you on LinkedIn and then visit your site should recognize the same person.

---

## Install

**One command:**

```bash
git clone https://github.com/whystrohm/whystrohm-voice-scorer.git ~/.claude/skills/whystrohm-voice-scorer
```

### Requirements

- [Claude Code](https://claude.ai/code) (CLI, desktop app, or IDE extension)
- No API keys. No external tools. No configuration.

---

## Run

```
> /whystrohm-voice-scorer
```

You'll be asked for your website URL, then asked to paste 3-5 social posts. Takes about 60 seconds.

---

## What You Get

1. **A drift score out of 10** — how well your social matches your website voice
2. **Two voice profiles** — your website voice vs your social voice, scored per dimension
3. **Exact drift examples** — specific quotes from both sources showing where they diverge
4. **A clear recommendation** — which voice is stronger and what needs to change

---

## Want the Full Picture?

This scores **1 of 5 layers** — voice consistency.

The full [WhyStrohm Content Infrastructure Audit](https://github.com/whystrohm/whystrohm-audit) scores all 5 layers: vocabulary, structure, proof density, voice consistency, and buyer alignment. Total score out of 50. Plus a live rewrite of your lowest-scoring content.

```bash
git clone https://github.com/whystrohm/whystrohm-audit.git ~/.claude/skills/whystrohm-audit
```

```
> /whystrohm-audit
```

---

## The System Behind This

This tool uses the same voice analysis framework from WhyStrohm's content infrastructure system — the methodology behind building content engines for founder-led companies.

**What the full system includes:**
- Brand voice encoded as 40-60 enforceable rules (not a PDF)
- Content guardrails that reject hype and require proof before publish
- Video production pipeline that renders branded content from code
- Multi-platform posting automation
- Templates, calendars, and a content engine your team owns completely

**Starting at $3,000/month. One operator. Full stack. 30 minutes of your time per week. You own everything I build.**

Score your content first — 10 seconds, no email, no pitch:

[whystrohm.com/scan](https://whystrohm.com/scan)

---

## Other WhyStrohm Skills

| Skill | What It Does | Install |
|-------|-------------|---------|
| [Digital Twin](https://github.com/whystrohm/digital-twin-of-yourself) | Reverse-engineer how you think and talk. Stress-tested AI System Prompt of yourself. | `git clone https://github.com/whystrohm/digital-twin-of-yourself.git ~/.claude/skills/digital-twin` |
| [Content Audit](https://github.com/whystrohm/whystrohm-audit) | Score your content against a 5-layer framework, get a live rewrite. | `git clone https://github.com/whystrohm/whystrohm-audit.git ~/.claude/skills/whystrohm-audit` |

## Brand Infrastructure Consulting

This skill is one piece of the brand infrastructure I build for founder-led brands. Voice extraction, programmatic video, automated publishing. One operator, full stack. You own everything.

→ [whystrohm.com/pricing](https://whystrohm.com/pricing?utm_source=github&utm_medium=repo-cta&utm_campaign=2026-04-10-closed-loop)

## License

MIT
