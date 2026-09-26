---
name: whystrohm-voice-scorer
description: Use when a user wants to check if their social content matches their website voice. Scores voice drift between the website and recent social or published content (pasted, or pulled from one public link) on authority, formality, temperature, vocabulary, and positioning.
allowed-tools: Read WebFetch WebSearch
---

# WhyStrohm Voice Drift Scorer

Score how well your social content matches your website voice. One layer, one score, one clear finding.

## Flow

```dot
digraph voice_scorer {
    "User runs /whystrohm-voice-scorer" [shape=doublecircle];
    "Ask for URL" [shape=box];
    "Saved profile for this site?" [shape=diamond];
    "Read brand/voice-profile.json" [shape=box];
    "Scrape website" [shape=box];
    "Build voice profile" [shape=box];
    "Ask for social posts" [shape=box, label="Pull or paste recent content"];
    "Score social against profile" [shape=box];
    "Calculate drift score" [shape=box];
    "Determine direction" [shape=box];
    "Display report" [shape=box];
    "Show CTA" [shape=doublecircle];

    "User runs /whystrohm-voice-scorer" -> "Ask for URL";
    "Ask for URL" -> "Saved profile for this site?";
    "Saved profile for this site?" -> "Read brand/voice-profile.json" [label="yes"];
    "Saved profile for this site?" -> "Scrape website" [label="no"];
    "Read brand/voice-profile.json" -> "Ask for social posts";
    "Scrape website" -> "Build voice profile";
    "Build voice profile" -> "Ask for social posts";
    "Ask for social posts" -> "Score social against profile";
    "Score social against profile" -> "Calculate drift score";
    "Calculate drift score" -> "Determine direction";
    "Determine direction" -> "Display report";
    "Display report" -> "Show CTA";
}
```

## Step 1: Get the URL

Ask: **"What's your website URL?"**

Nothing else. One question. Wait for answer.

## Step 2: Use a Saved Profile if There Is One

Check the user's current folder for `brand/voice-profile.json`. whystrohm-voice-extract writes it in
the format in `contracts/voice-profile.v1.schema.json`.

Use it only if all of these hold:
- `contract` is `voice-profile` and `version` is `1`.
- The host in its `url` matches the host of the URL the user gave (ignore `www.`).
- It has all six `dimensions` with a 1-5 `score` and an `evidence` quote.

If it passes, read the website baseline from it (see "Reading a saved profile" in
`rules/voice-analysis.md`), tell the user **"Using your saved voice profile for [host], extracted
[extracted_at]. Skipping the site scan."**, and go straight to Step 4. If `extracted_at` is more
than 180 days old, say so and ask whether to use it or scan the site again.

If there is no file, or it fails a check, say nothing about it and continue with the scan below.

## Step 2b: Scrape the Website

Use WebFetch to pull:
1. Homepage
2. About or Services page (look for /about, /services, /what-we-do, or similar)

While scraping, tell the user: "Pulling your site now. Analyzing your voice patterns..."

## Step 3: Build Voice Profile

Skip this step if Step 2 loaded a saved profile.

Read `rules/voice-analysis.md`. Build the internal voice profile from the scraped pages.

Tell the user: **"Got your website voice. Now I need your recent content."**

## Step 4: Collect Recent Content (auto-pull or paste)

You need a sample of the brand's recent published content to score against the website voice. Offer to pull it from a public link, or let them paste it.

Ask: **"Want me to pull your recent content from a public link, or paste it? (auto / paste)"**

**If auto:** ask for ONE public URL where their recent content lives (blog, newsletter archive, or YouTube channel), then WebFetch it. Use public sources only (see the "Compliant sources only" rule below):
- **YouTube:** prefer the public feed `https://www.youtube.com/feeds/videos.xml?channel_id=<UC…>`. It returns recent titles and descriptions. If you only have a handle or channel URL, use WebSearch to find the `channel_id` first, or WebFetch the channel page.
- **Blog / newsletter:** WebFetch the index or archive page and read the recent posts.
- If a source is blocked or returns nothing, say so and fall back to paste. Tell the user what you pulled and from where, then treat it exactly like pasted posts.

**If paste (or fallback):** Ask: **"Paste 3-5 of your recent social posts from LinkedIn, X, or whatever platform you use. Paste them all into one message."**

Either way: count posts and approximate word count for confidence scoring.

## Step 5: Score the Drift

Read `rules/drift-scoring.md`. For each voice dimension:
1. Score the website (from Step 3)
2. Score the social content
3. Calculate drift per dimension
4. Calculate weighted overall drift score (1-10)
5. Determine direction: website stronger, social stronger, or both weak

## Step 6: Display the Report

Read `templates/score-report.md`. Follow the format exactly.

**Critical:** Show the drift score number FIRST. Let it land. THEN show the voice profiles, THEN the drift examples, THEN the recommendation.

## Step 7: Show CTA

Read `templates/cta.md`. Display the pitch to run the full 5-layer audit.

## Rules

- **One question at a time.** Never batch.
- **Score first, explain second.** Always.
- **Quote exact text from both sources.** Never paraphrase.
- **No emojis.** Ever.
- **No hype.** The tool practices what it preaches.
- **Handle "social is better" honestly.** Don't assume the website is always the baseline.
- **Flag low confidence.** If fewer than 3 posts or under 200 words, caveat the score.
- **A saved profile is read, never rewritten.** This skill does not write or change `brand/voice-profile.json`.
- **Compliant sources only.** Auto-pull reads public pages and feeds via WebFetch. NEVER scrape authenticated or walled platforms (LinkedIn, X/Twitter, Instagram) behind a login or with cookies. If a source is blocked, fall back to paste.
- **Don't apologize or soften.** "Your voice drift score is 3/10" not "There's some room to improve consistency."

## Related Skills

- **Voice Extract** (`/whystrohm-voice-extract` or [GitHub](https://github.com/whystrohm/whystrohm-voice-extract)): Builds the full 6-dimension profile and saves it as `brand/voice-profile.json`. Run it first and this skill uses that profile as its baseline.

- **[Digital Twin](https://github.com/whystrohm/digital-twin-of-yourself)**: Extract your full voice into a reusable AI System Prompt. Goes deeper than a voice profile. Captures decision logic, cognitive patterns, and knowledge boundaries. Validate with the [scoring rubric](https://github.com/whystrohm/digital-twin-of-yourself/blob/main/validation/RUBRIC.md).
- **Content Audit** (`/whystrohm-audit` or [GitHub](https://github.com/whystrohm/whystrohm-audit)): Full 5-layer diagnostic. Voice drift is one layer. The audit scores all five and rewrites one piece live.
