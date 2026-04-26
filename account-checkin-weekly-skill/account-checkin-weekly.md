---
name: account-checkin-weekly
description: >
  Use this skill for recurring weekly Google Ads account check-ins. Triggers include: "weekly check-in", "weekly account review", "do the weekly check-in for", "ACE the account", "run ACE", "do ACE", "check in on this account", "weekly optimization", or any request to do a regular ongoing review of a Google Ads account. For a brand new account or one not reviewed in over a year, use the account-checkin-ash skill instead.
---

# Weekly Account Check-In (ACE)

From Ruskin Consulting Training Module 25.

The weekly check-in follows the ACE framework: Account, Competition, Edits and Expansion. The goal is to ACE the account every week. The heart of the account is always search terms and pairing a search term to an ad. Everything in ACE serves that core.

**Return to ASH steps 7 through 10 (Account Organization, Keywords, Campaign Settings, Checklists) once a year to make sure the account foundation is still solid.**

---

## The 10 Metrics to Track Over Time

Every week these metrics should be moving in the right direction. Use these as your north star across every step.

| Metric | Direction You Want |
|---|---|
| Clicks | Up or stable |
| Cost | Stable |
| Conversions | Up |
| Cost per Conversion | Down |
| CTR | Up or stable |
| Conversion Rate | Up or stable |
| Avg. CPC | Down |
| Impr. (Top %) | Up |
| Search Impression Share Lost to Rank | Down |
| Search Impression Share Lost to Budget | Down or stable |

---

## The 10 Steps of ACE

### Step 1: Billing, Notifications, and Account Overview

**Billing check:**

Use `MCP MASTER SERVER:gads_search` to pull this month's total spend:

```
resource: campaign
fields: [metrics.cost_micros]
conditions: ["[segments.date](http://segments.date) DURING THIS_MONTH"]
customer_id: [client ID]
```

Divide `cost_micros` by 1,000,000 for dollars. Then apply the pacing formula:

**Expected Spend = (Monthly Budget x Today's Date) / Days in Month**

If actual spend is above expected: reduce budgets and bids.
If actual spend is below expected: increase bids.

If the credit card on file is not working, notify the manager and the client immediately and follow up daily until resolved.

**Notifications:**
Review all Google Ads notifications (the bell icon). Act on anything sensible. Dismiss everything else. There should be zero unread notifications when you finish the check-in.

**Account overview graphs:**

Use `MCP MASTER SERVER:gads_search` to pull 30-day and 90-day trend data. Review these five metric pairs and check that each is moving in the right direction:

| Graph Pair | What to Look For |
|---|---|
| Clicks and Cost | Both stable or rising together, spending evenly |
| Conversions and Cost per Conversion | Conversions up, CPA down |
| CTR and Conversion Rate | Both stable or rising |
| Avg. CPC and Impr. (Top %) | CPC down, Top % up |
| Lost IS (Rank) and Lost IS (Budget) | Both trending down |

---

### Step 2: Recommendations Tab

Review every recommendation in the Google Ads Recommendations tab. Apply ones that make sense. Dismiss everything else via the three-dot menu. The tab refreshes weekly.

**Critical: Check Auto-Apply settings every single week.**

Google has a tendency to silently re-enable auto-apply settings without warning. Only one setting should ever be enabled:

- "Remove Conflicting Negative Keywords" — keep ON
- Everything else — keep OFF

Auto-applied changes interfere with manual optimizations and bidding strategies. Unchecked, they can undo weeks of work.

---

### Step 3: Search Terms

This is the most important step. Do it every single week without exception.

Use `MCP MASTER SERVER:gads_search` to pull search terms from the past 7 days:

```
resource: search_term_view
fields: [
  search_term_[view.search](http://view.search)_term,
  search_term_[view.ad](http://view.ad)_group,
  metrics.clicks,
  metrics.impressions,
  metrics.ctr,
  metrics.conversions,
  metrics.cost_micros
]
conditions: ["[segments.date](http://segments.date) DURING LAST_7_DAYS"]
order_by: metrics.impressions DESC
customer_id: [client ID]
```

For every search term, make one of four decisions. Refer to the search-terms skill for the full decision framework.

| Decision | When |
|---|---|
| Add as exact match keyword | Good search term not yet in the account |
| Add negative keyword | Bad or irrelevant search term |
| Move to correct ad group | Good search term in the wrong ad group |
| Do nothing | Already a keyword or duplicate |

If you find no negative keywords to add from the search terms report, go to the master negatives list and upload additional negatives to the Shared Library. Clients should see negative keyword work happening every week.

---

### Step 4: Keywords and Negative Keywords

Review all keywords across every ad group and campaign. For each keyword ask:
- Is this the right keyword for the business?
- Is it in the correct match type?
- Is it in the correct ad group?

Use `MCP MASTER SERVER:gads_search` to pull all active keywords with performance data:

```
resource: keyword_view
fields: [
  ad_group_criterion.keyword.text,
  ad_group_criterion.keyword.match_type,
  ad_[group.name](http://group.name),
  [campaign.name](http://campaign.name),
  metrics.clicks,
  metrics.impressions,
  metrics.ctr,
  metrics.conversions,
  metrics.cost_micros
]
conditions: [
  "ad_group_criterion.status = ENABLED",
  "[segments.date](http://segments.date) DURING LAST_30_DAYS"
]
customer_id: [client ID]
```

For negative keywords, ask:
- Could any of these negatives block important search terms?
- Are the negative lists too large to manage?
- Could negatives be grouped or simplified?
- Are they placed at the right level (account, campaign, or ad group)?
- Are there duplicates that can be removed?

Bad negative keywords are more dangerous than bad keywords. Triple-check every one.

---

### Step 5: Search Impression Share

Review Impression Share across every campaign. Use `MCP MASTER SERVER:gads_search`:

```
resource: campaign
fields: [
  [campaign.name](http://campaign.name),
  [metrics.search](http://metrics.search)_impression_share,
  [metrics.search](http://metrics.search)_top_impression_share,
  [metrics.search](http://metrics.search)_absolute_top_impression_share,
  [metrics.search](http://metrics.search)_rank_lost_impression_share,
  [metrics.search](http://metrics.search)_budget_lost_impression_share
]
conditions: ["[segments.date](http://segments.date) DURING LAST_30_DAYS"]
customer_id: [client ID]
```

**How to interpret the results:**

| Metric | Target | Action if Off Target |
|---|---|---|
| Impr. (Top %) | Close to 100% — below 90% needs work | Improve Quality Scores, increase bids |
| Impr. (Abs. Top %) | Below 30% for non-branding campaigns | If too high, CPC is likely inflated |
| Lost IS (Rank) | As low as possible | Review Quality Scores in Step 6 |
| Lost IS (Budget) | Near zero | Reduce bids or request higher budget from client |

---

### Step 6: Quality Scores

If Step 5 showed significant Lost IS due to rank, go through every keyword's Quality Score. Use `MCP MASTER SERVER:gads_search`:

```
resource: keyword_view
fields: [
  ad_group_criterion.keyword.text,
  ad_[group.name](http://group.name),
  [campaign.name](http://campaign.name),
  ad_group_criterion.quality_info.quality_score,
  ad_group_criterion.quality_[info.search](http://info.search)_predicted_ctr,
  ad_group_criterion.quality_[info.ad](http://info.ad)_relevance,
  ad_group_criterion.quality_info.landing_page_experience
]
conditions: ["ad_group_criterion.status = ENABLED"]
customer_id: [client ID]
```

**What each component tells you and what to do:**

| Component | Below Average Fix |
|---|---|
| Expected CTR | Go to Step 7 and rewrite ads |
| Landing Page Experience | Find a better landing page, optimize the existing one, or propose a new one to the client |
| Ad Relevance | Change match type, add negative keywords, create a more specific ad group, write more relevant ads, or update landing page content to better match the search term |

---

### Step 7: Ads and Ad Assets

**First:** Check that all active ads are eligible. No disapprovals, no broken final URLs, no policy flags.

**Second:** Go through every ad group and review ad performance. Use the ad-optimization skill for the full three-factor framework (Enough Data, Fair Comparison, 2-Click Test).

Prioritize ad groups where Expected CTR is Below Average from Step 6. For those ad groups:
- Rewrite the weakest ad with a new approach
- Make sure the search term is matched in the headline
- Add more specific unique value propositions
- Confirm the CTA is clear

**Third:** Check Account-Level Automated Assets. Navigate to Campaigns > Assets > More > Account-level automated assets. Every single toggle must be OFF. Google turns these back on without warning and they will override your copy and strategy.

Refer to the ad-optimization skill for the full evaluation process and the google-ads-ad-writing skill for RSA writing standards.

---

### Step 8: Competitor Research

Do competitor research any week where:
- Expected CTR came back Below Average in Step 6
- You are struggling to write better ads
- You want to find new keyword ideas

**How to research:**

Use `Ahrefs:site-explorer-organic-competitors` to identify the top competitors for the client's domain. Then use `Ahrefs:site-explorer-organic-keywords` and `Ahrefs:site-explorer-paid-pages` to see what keywords competitors rank for and what pages they are bidding on.

Also Google the main search terms directly within the client's target location. Look at every ad that shows up. Read the headlines, value propositions, and CTAs. What are competitors saying that you are not? What angles have they found that you can test?

Use what you find to:
- Write better ads with sharper UVPs
- Identify keywords worth adding to the account
- Spot gaps in your current coverage

---

### Step 9: GA4 and Website Check

Every week, confirm both GA4 and the website are functioning correctly.

Use `MCP MASTER SERVER:ga4_overview` with the past 7 days to check for anything unusual:

```
propertyId: [client GA4 property ID]
startDate: [7 days ago]
endDate: [today]
```

Use `MCP MASTER SERVER:ga4_sources` to confirm paid search traffic is showing up and conversion events are firing.

**What to look for in GA4:**
- No abnormal traffic spikes or drops
- Key conversion events are still recording
- Traffic sources look normal

**What to check on the website:**
- No broken pages or 404 errors
- Forms are submitting correctly
- Phone numbers and emails are clickable
- Website formatting is not broken on mobile

If you find an issue with GA4 or the website, flag it to the project manager immediately. Do not wait for the next check-in.

---

### Step 10: Deliverables

Every check-in ends with a written deliverable for next week. This is your accountability item.

After going through all nine steps you should have identified at least one thing to improve. Decide what you will work on next week and define exactly how you will measure whether it succeeded.

**Deliverable-to-metric connections:**

| Work Planned | Metric to Measure |
|---|---|
| Ad rewriting | CTR |
| Keyword bid adjustments | Cost per Conversion |
| New landing page | Conversion Rate, Bounce Rate |
| Search term cleanup | CTR, CPA, wasted spend |
| New ad groups | CTR, Ad Relevance |
| Negative keyword expansion | CPA, Conversion Rate |
| Budget reallocation | Impression Share, Conversions |

Write the deliverable down. Set a target. Check it at the start of next week's check-in before doing anything else. If you hit your target, you ACEd it.

---

## ACE Weekly Checklist

Run through this at the end of every check-in before closing the account:

- [ ] Budget pacing checked and adjusted if needed
- [ ] Credit card confirmed working
- [ ] All notifications reviewed and cleared
- [ ] Account overview graphs reviewed across all 5 metric pairs
- [ ] Recommendations tab reviewed and irrelevant ones dismissed
- [ ] Auto-apply settings verified (only "Remove Conflicting Negative Keywords" is ON)
- [ ] Search terms reviewed for the past 7 days
- [ ] New exact match keywords added for good search terms
- [ ] Negative keywords added for bad search terms
- [ ] Keywords reviewed for match type and placement
- [ ] Negative keywords audited for dangerous blocks
- [ ] Impression Share reviewed across all campaigns
- [ ] Quality Scores reviewed (especially if Lost IS to Rank is high)
- [ ] All ads confirmed eligible with no disapprovals
- [ ] Ad performance evaluated using the 3-factor framework
- [ ] Account-Level Automated Assets confirmed all OFF
- [ ] Competitor research done if CTR is Below Average
- [ ] GA4 checked for anomalies and conversion tracking confirmed
- [ ] Website checked for broken pages and form functionality
- [ ] Next week's deliverable written down with a measurable target
