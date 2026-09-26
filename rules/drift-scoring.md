---
name: drift-scoring
description: How to compare website voice profile against social content and score the drift
---

# Voice Drift Scoring

After building the website voice profile (from voice-analysis.md) and collecting the user's recent content (pasted, or pulled from one public link in Step 4), score the drift between the two.

## Step 1: Profile the Social Content

Apply the same voice-analysis.md framework to the collected posts:
- Authority level (1-5)
- Formality (1-5)
- Emotional temperature (1-5)
- Vocabulary pattern (technical/conversational/hype/mixed)
- Proof style (data/stories/mechanisms/none)
- Positioning signal (what they call themselves, who they serve)

**Important:** Social posts are short-form, often 50-200 words each. Pulled items (feed titles and descriptions, blog posts) vary in length. Score based on patterns across ALL collected posts, not individual posts. Look for the dominant voice, not outliers. Each pasted post or pulled item counts as one post for confidence.

## Step 2: Calculate Per-Dimension Drift

For each scored dimension (authority, formality, temperature):
- Drift = abs(website score - social score)
- Max drift per dimension = 4 (on the 1-5 scale)

For vocabulary and positioning (categorical, not numeric):
- Match = 0 drift
- Partial match = 1 drift
- Mismatch = 2 drift
- Opposite = 3 drift
- Max drift per categorical dimension = 3

## Step 3: Calculate Overall Drift Score

Weighted formula (higher weight = more noticeable to readers):

| Dimension | Weight |
|-----------|--------|
| Authority drift | 30% |
| Formality drift | 25% |
| Emotional temperature drift | 20% |
| Vocabulary pattern match | 15% |
| Positioning signal match | 10% |

**Calculation:**
1. Normalize each dimension's drift to 0-1 scale (divide by max possible drift: 4 for authority, formality, and temperature; 3 for vocabulary and positioning)
2. Multiply by weight
3. Sum all weighted drifts to get total drift (0-1)
4. Convert to score: Score = 10 - (total drift * 9), rounded to nearest integer
5. Clamp to 1-10 range

**Interpretation:**
| Score | Meaning |
|-------|---------|
| 9-10 | Identical voice. Rare without a system. |
| 7-8 | Minor drift. A few patches where social goes off-brand. |
| 5-6 | Noticeable drift. Social sounds like a different person in spots. |
| 3-4 | Significant drift. Website and social could be different companies. |
| 1-2 | Complete disconnect. No recognizable voice relationship. |

## Step 4: Determine Direction

Compare the quality of each voice source independently. Assess which voice is more:
- Specific (vs. vague)
- Direct (vs. hedging)
- Proof-dense (vs. claim-heavy)
- Distinctive (vs. generic)

Three possible findings:

**Website voice is stronger:**
> "Your website voice is stronger than your social content. Your social is drifting toward [generic B2B / corporate / tentative / hype] language. The fix: apply the same rules that govern your website copy to every social post."

**Social voice is stronger:**
> "Your social voice is actually stronger than your website. You sound more [authentic / direct / specific] on [LinkedIn/X] than on your own site. Your website needs to catch up. It's more corporate than your real voice."

**Both are weak:**
> "Neither your website nor your social content has a clear, distinctive voice. Both drift toward generic [B2B / corporate / template] language. You don't need a tune-up. You need a system that defines your voice from scratch."

## Step 5: Pull Drift Examples

Find 2-3 specific examples where website and social voice diverge. For each:
- Quote the website text
- Quote the social text
- Name the specific gap (authority shift, formality change, vocabulary drift, etc.)

**Rules for examples:**
- Use exact quotes. Never paraphrase.
- Pick the most dramatic contrasts.
- Name the dimension that drifted and the direction.
- Keep each example to 3 lines: Website / Social / Gap.

## Confidence Levels

Based on the amount of content collected. Count posts (each pasted post or pulled item is one) and total approximate words across all of them. Find the one row that matches both counts:

| Posts | Total words | Confidence | Action |
|-------|-------------|------------|--------|
| 5 or more | 500 or more | High | No flag needed |
| 5 or more | 200-499 | Moderate | Flag: "Score confidence: moderate (N posts, ~X words)" |
| 3-4 | 200 or more | Moderate | Flag: "Score confidence: moderate (N posts, ~X words)" |
| 3 or more | Under 200 | Low | Flag prominently: "Score confidence: low. Add more posts for a more accurate reading." |
| 1-2 | Any | Low | Flag prominently: "Score confidence: low. Add more posts for a more accurate reading." |

Every combination lands in exactly one row. For example, 5 posts with 400 words is Moderate, and 2 posts with 250 words is Low.

Always proceed with scoring regardless of confidence. A low-confidence score is still useful. Just caveat it.
