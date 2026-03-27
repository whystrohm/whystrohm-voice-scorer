---
name: voice-analysis
description: How to infer brand voice attributes from a website scrape. Used as the baseline for drift scoring against social content.
---

# Voice Analysis from URL Scrape

After scraping the prospect's website, build a voice profile before asking questions. This profile is used in Layer 4 (Voice Consistency) scoring.

## What to Extract

From the homepage, about page, and blog (if present), identify:

### 1. Authority Level (1-5)
- **1 — Tentative:** Hedging language ("we think," "we try to," "hopefully")
- **2 — Cautious:** Qualified claims ("we believe," "in our experience")
- **3 — Confident:** Direct statements without hedging ("the pattern is clear," "this is what works")
- **4 — Expert:** Commands respect ("the data shows," "after 200 implementations")
- **5 — Absolute:** Unqualified authority ("this is the only way," "everyone else is wrong")
- **How to detect:** Count hedge words vs. direct statements in first 3 paragraphs of each page.

### 2. Formality (1-5)
- **1 — Casual:** Slang, emojis, sentence fragments, first-name-basis
- **2 — Conversational:** Contractions, "you" heavy, approachable but not sloppy
- **3 — Professional:** Clean prose, contractions OK, no slang, industry terminology
- **4 — Formal:** Full words, structured paragraphs, third-person references
- **5 — Academic:** Dense, citation-heavy, passive voice, jargon-heavy
- **How to detect:** Check for contractions (casual signal), passive voice (formal signal), sentence length distribution.

### 3. Emotional Temperature (1-5)
- **1 — Cold/Clinical:** Data-only, no personality, reads like a spec sheet
- **2 — Warm-Professional:** Occasional human touch, mostly fact-driven
- **3 — Engaging:** Personality present, stories used, reader feels connection
- **4 — Passionate:** Strong opinions, exclamation points, emotional appeals
- **5 — Hype:** Urgency, FOMO, superlatives, emotional manipulation
- **How to detect:** Count exclamation marks, emotional adjectives, urgency words, personal stories.

### 4. Vocabulary Patterns
- **Technical density:** How much jargon per paragraph?
- **Proof style:** Do they cite numbers, stories, mechanisms, or nothing?
- **Sentence rhythm:** Short punchy lines? Long flowing paragraphs? Mixed?

### 5. Positioning Signal
- **What do they call themselves?** (agency, consultancy, studio, firm, partner)
- **What verbs do they use?** (build, help, transform, enable, create)
- **Who do they serve?** (stated on site vs. implied by language)

## Output Format

Build this internal profile (do NOT show to user — use it for scoring):

```
VOICE PROFILE (inferred from site):
- Authority: [1-5] — [one sentence evidence]
- Formality: [1-5] — [one sentence evidence]
- Emotional temp: [1-5] — [one sentence evidence]
- Vocab pattern: [technical/conversational/hype/mixed]
- Proof style: [data/stories/mechanisms/none]
- Positioning: [what they call themselves + who they serve]
- Key phrases: [3-5 distinctive phrases from their site]
```

## Using the Profile

Compare this profile against the content sample in Layer 4 scoring:
- Does the content match the authority level of the site?
- Does the content use the same vocabulary density?
- Does the content reference the same audience the site targets?
- Are the "key phrases" from the site present in the content?

Major drift between site voice and content voice = low Layer 4 score.
