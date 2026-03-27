---
name: score-report
description: Output format template for the voice drift score report
---

# Voice Drift Report Format

Use this exact format for the drift score output. Score first, details second.

## Score Display (Show This First)

```
═══════════════════════════════════════
  VOICE DRIFT SCORE
═══════════════════════════════════════

                 {score}/10

  Score confidence: {confidence} ({post_count} posts, ~{word_count} words)

═══════════════════════════════════════
```

**Pause here.** Let the score sit before continuing.

## Voice Profiles

```
YOUR WEBSITE VOICE
  Authority:    {w_auth}/5 — {w_auth_desc}
  Formality:    {w_form}/5 — {w_form_desc}
  Temperature:  {w_temp}/5 — {w_temp_desc}
  Vocabulary:   {w_vocab}
  Positioning:  {w_positioning}

YOUR SOCIAL VOICE
  Authority:    {s_auth}/5 — {s_auth_desc}
  Formality:    {s_form}/5 — {s_form_desc}
  Temperature:  {s_temp}/5 — {s_temp_desc}
  Vocabulary:   {s_vocab}
  Positioning:  {s_positioning}
```

## Drift Examples

Show 2-3 examples, each with this format:

```
  Website: "{exact quote from website}"
  Social:  "{exact quote from social post}"
  Gap:     {dimension} shifted {direction}. {One sentence explaining why this matters.}
```

**Rules:**
- Exact quotes only. Never paraphrase.
- Pick the most dramatic contrasts.
- Maximum 3 examples. Quality over quantity.

## Recommendation

One paragraph. Based on the direction finding:
- If website stronger: tell them to bring social up to match.
- If social stronger: tell them their website needs to catch up.
- If both weak: tell them they need a system, not a tune-up.

Be specific about WHAT is drifting (authority, formality, vocabulary, etc.) and in WHAT direction.
