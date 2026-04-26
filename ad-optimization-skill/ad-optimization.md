---
name: ad-optimization
description: >
  Use this skill whenever the user needs to optimize, evaluate, pause, or improve Google Ads. Triggers include: "which ads should I pause", "optimize my ads", "ad optimization", "A/B test ads", "which ad is performing better", "should I pause this ad", "ad CTR analysis", "quality score improvement", "ad rank", "why is my CPC so high", "how do I improve quality score", or any request involving evaluating ad performance and deciding what to keep or cut. Also use when writing RSA copy that needs to account for pinning, description strategy, or position-aware CTAs.
---

# Ad Optimization

From Ruskin Consulting Training Modules 16 and 17.

---

## The Two Goals

1. Write ads that earn high Quality Scores so Ad Rank goes up and CPC goes down
2. Identify and pause underperforming ads so only the best ads run

You will spend more time optimizing existing ads than creating new ones. Learn this process well.

---

## Part 1: Ad Rank and Quality Score

### Ad Rank Formula

**Ad Rank = CPC Bid x Quality Score**

Ad Rank determines position on the search results page. Position 1 goes to the highest Ad Rank, not the highest bid. A lower bid with a high Quality Score can outrank a higher bid with a poor Quality Score.

### Actual CPC Formula

Your bid is not what you pay. Actual CPC is determined by the advertiser below you:

**Actual CPC = (Ad Rank of advertiser below you / Your Quality Score) + $0.01**

Example:

| Advertiser | Max Bid | Quality Score | Ad Rank | Actual CPC |
|---|---|---|---|---|
| Advertiser I | $2.00 | 10 | 20 | (16/10) + $0.01 = $1.61 |
| Advertiser II | $4.00 | 4 | 16 | (12/4) + $0.01 = $3.01 |
| Advertiser III | $6.00 | 2 | 12 | (8/2) + $0.01 = $4.01 |
| Advertiser IV | $8.00 | 1 | 8 | N/A (bottom) |

Advertiser I has the lowest bid and the best position and pays the least. Quality Score is the lever that makes this happen.

---

### Quality Score (1-10)

Quality Score has three components. Expected CTR is the most important.

#### 1. Expected CTR
How likely your ad is to be clicked. Google only makes money when people click. An ad that nobody clicks is worthless to Google regardless of bid. Write ads that people actually want to click.

#### 2. Ad Relevance
How closely your ad matches the intent behind the user's search. To maximize Ad Relevance:
- Build specific ad groups with tightly themed keywords
- Maintain a strong negative keyword list
- Include the user's search term in your ad copy
- Send users to a landing page that is SEO optimized for that search term

The goal: the user's exact search term appears in a specific ad group, the ads contain that search term, and the landing page is all about that search term.

#### 3. Landing Page Experience
How relevant and easy to navigate your landing page is. Google tracks bounce rate, pages per session, and session duration. A bad landing page hurts Quality Score. Always send users to the most specific, relevant page for their search term, not just the homepage.

---

## Part 2: Responsive Search Ads (RSAs)

### Format
- Up to **15 headlines** (30 characters max each)
- Up to **4 descriptions** (90 characters max each)
- Google's AI tests combinations and shows the best performing ones more often

### Ruskin RSA Writing Practices

**Headlines:**
- Write all 15. More variety gives Google's AI more to test with.
- Do not use all 30 characters on every headline. Mix long and short. Long headlines in positions 1 and 2 can prevent the 3rd headline from showing.
- Include headlines that match the keyword/ad group theme
- Include headlines with CTAs (e.g., "Call Us Today", "Get a Free Quote")
- Include headlines with value propositions

**Descriptions:**
- Write all 4
- Description 1: Match the search term/search query. Add a CTA at the end if space allows
- Description 2: Lead with a value proposition
- Description 3: About the company or brand being advertised
- Description 4: Additional value proposition or offer

**CTAs and Position 3:**
Since the 3rd headline often does not show when headlines 1 and 2 are long, include a CTA at the end of at least one description. This ensures the CTA still gets seen.

### Pinning

Pinning locks a headline or description to a specific position so Google's AI cannot move it. Use pinning when you want guaranteed control over which message appears first.

Best practice: pin the search term match headline to Position 1. This ensures Ad Relevance is always high regardless of which other headlines Google picks.

**Warning:** Pinning reduces the number of combinations Google can test. Only pin when there is a specific reason.

### URL Path Fields

- **Final URL:** Send users to the most specific landing page for the search term. Never just the homepage.
- **Path fields:** Match the search term in the path to reinforce relevance. Format: `www.domain.com/Path1/Path2`. The path does not have to be the actual URL structure, just relevant text. Example: if the final URL is `example.com/dental-services/teeth-cleaning`, the path could be `Teeth/Cleaning`.

---

## Part 3: Ad Optimization Process

The job is to pause underperforming ads so only the best ads run in each ad group. Always run more than one ad so you have something to compare against.

### The Key Metric

**CTR = (Clicks / Impressions) x 100%**

CTR is the #1 metric for Google. CTR is how Google makes money. Higher CTR = higher Ad Rank = lower CPC. Sort all ads by CTR first.

However, CTR alone is not enough to decide which ads to pause. You need two more checks first.

---

### The 3-Factor Ad Optimization Framework

Think of each ad as an NBA team and each impression as a game played. Before declaring a winner you need to ask:
1. Was enough data collected? (Did they play enough games?)
2. Was it a fair comparison? (Did both teams play on the same court?)
3. Who actually won? (Which ad had the higher CTR?)

---

#### Factor 1: Enough Data (Impressions Check)

An ad needs enough impressions before you can fairly judge its CTR. The minimum impressions threshold ensures each ad had the chance to earn at least 2 clicks.

**Formula:**
**Minimum Impressions = 2 / Ad Group Average CTR**

Example: If the ad group average CTR is 6.46%, minimum impressions = 2 / 0.0646 = **31 impressions**

If an ad has fewer impressions than the minimum, do not pause it. It has not had enough data yet.

---

#### Factor 2: Fair Comparison (Position Check)

An ad that showed mostly at the bottom of the page is not fairly comparable to one that showed mostly at the top. Position 1 gets far more clicks than position 5 regardless of ad quality. You need to make sure ads competed in roughly the same positions.

Use two metrics from Google Ads:
- **Impr. (Top) %** - How often the ad showed above organic results
- **Impr. (Abs. Top) %** - How often the ad showed in position 1

**Formula (20% Rule):**

Min. Impr. (Top) % = 0.80 x Ad Group Avg. Impr. (Top) %
Min. Impr. (Abs. Top) % = 0.80 x Ad Group Avg. Impr. (Abs. Top) %

If an ad's Impr. (Top) % or Impr. (Abs. Top) % is below either minimum, it did not have a fair comparison. Do not pause it yet.

Example:
- Ad group avg Impr. (Top) % = 84.67% → Minimum = 0.80 x 84.67% = **67.74%**
- Ad group avg Impr. (Abs. Top) % = 64.46% → Minimum = 0.80 x 64.46% = **51.57%**
- Ad 3 has Impr. (Abs. Top) % of 45.83% which is below 51.57% → Do not pause Ad 3

---

#### Factor 3: CTR (The 2-Click Test)

Once an ad passes both checks above, apply the 2-click test to determine if it should be paused.

**Formula:**
**If (Ad Clicks + 2) / Ad Impressions > Ad Group Average CTR → Keep the ad**
**If (Ad Clicks + 2) / Ad Impressions < Ad Group Average CTR → Pause the ad**

The +2 gives every ad a small buffer to account for variance. If an ad still cannot beat the group average even with 2 free clicks, it is underperforming.

Example:
- Ad Group Avg CTR = 6.46%
- Ad 2: (5+2) / 69 = 10.14% → 10.14% > 6.46% → **Keep**
- Ad 3: (1+2) / 59 = 5.08% → Already excluded by fair comparison check → **Do not pause**

---

### Decision Summary

Work through these three checks in order for every ad:

| Check | Formula | Result if Fails |
|---|---|---|
| Enough Data | Ad Impressions > 2 / Ad Group Avg CTR | Do not pause, needs more data |
| Fair Comparison | Ad Impr. (Top) % > 80% of Avg AND Ad Impr. (Abs. Top) % > 80% of Avg | Do not pause, position was unfair |
| 2-Click Test | (Clicks + 2) / Impressions > Ad Group Avg CTR | Pause the ad |

Only pause an ad if it passes the first two checks AND fails the third.

---

### What to Do After Pausing

Once an underperforming ad is paused, write a new ad to replace it. The new ad should try a different approach, different value propositions, or a different headline structure. Always keep at least two ads running per ad group so testing continues.

---

## Quick Reference: Metrics to Pull from Google Ads

For ad optimization you need these four columns per ad:

| Metric | What It Measures |
|---|---|
| Clicks | Total clicks the ad received |
| Impressions | Total times the ad was shown |
| Impr. (Top) % | How often ad showed above organic results |
| Impr. (Abs. Top) % | How often ad showed in absolute top position (position 1) |

CTR is calculated from Clicks and Impressions. All other formulas flow from these four inputs.
