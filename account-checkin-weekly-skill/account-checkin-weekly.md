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

**Diagnosing underpacing:** Before increasing bids, check Step 5 (Impression Share) first. A campaign that is underpacing AND losing IS to rank has a Quality Score problem, not a bid problem. A campaign underpacing AND losing IS to budget needs a higher budget. Treating the wrong cause wastes time.

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

Google silently re-enables auto-apply settings without warning. The navigation location has also moved over time — as of late 2025 it sits just above the regular recommendations section. Check every week regardless of where it has moved.

Only one setting should ever be ON:

- "Remove Conflicting Negative Keywords" — this automatically removes negative keywords that are blocking your own ads from showing, which is what you want.

Everything else must be OFF. This includes but is not limited to:
- Upgrade keywords to broad match
- Upgrade Smart Bidding strategy
- Set target CPA or target ROAS automatically
- Add new keywords
- Add responsive search ads
- Expand to Display Network
- Add callouts or sitelinks automatically
- Any audience or asset automation

Google uses auto-apply to optimize its own revenue, not yours. Bid strategy changes, keyword additions, and asset changes applied without review can undo weeks of optimization in a single day.

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

### Step 5b: Smart Bidding Health Check

After reviewing Impression Share, check the bid strategy on every campaign. Ruskin uses Smart Bidding on all campaigns. Manual CPC and Enhanced CPC are never used.

**The Smart Bidding progression:**

| Stage | Strategy | Status |
|---|---|---|
| 1 | Max Clicks | Starting point for new campaigns. Gets delivery going while Google learns. |
| 2 | Max Conversions | Move here once the campaign spends consistently and conversions are recording. Needs roughly 30 conversions per month to optimize well. |
| 3 | tCPA or tROAS | Move here once Max Conversions is stable with enough data to set a reliable target. tCPA for lead gen, tROAS for ecommerce. |

**Each week, ask these questions per campaign:**

- Is the campaign on the right strategy for where it is in the progression?
- Is a Max Clicks campaign spending well and recording conversions? If yes, consider moving to Max Conversions.
- Is a Max Conversions campaign hitting at least 30 conversions per month? If no, hold here longer before moving to tCPA/tROAS.
- Is a tCPA or tROAS campaign struggling to spend or losing conversion volume? If yes, step back to Max Conversions or Max Clicks and restart the progression.

**Use `MCP MASTER SERVER:gads_search` to check current bid strategies:**

```
resource: campaign
fields: [
  [campaign.name](http://campaign.name),
  campaign.bidding_strategy_type,
  [campaign.target](http://campaign.target)_[cpa.target](http://cpa.target)_cpa_micros,
  [campaign.target](http://campaign.target)_[roas.target](http://roas.target)_roas,
  metrics.conversions,
  metrics.cost_micros
]
conditions: ["[segments.date](http://segments.date) DURING LAST_30_DAYS"]
customer_id: [client ID]
```

Note: `campaign.bidding_strategy_type` returns values like `MAXIMIZE_CLICKS`, `MAXIMIZE_CONVERSIONS`, `TARGET_CPA`, `TARGET_ROAS`. Flag any campaign showing `MANUAL_CPC` or `ENHANCED_CPC` as misconfigured.

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

**Second:** Go through every ad group and evaluate ad performance using the ad-optimization skill. That skill contains the full three-factor framework: Enough Data check, Fair Comparison (position check), and the 2-Click Test. Run every ad through all three before deciding to pause it.

Prioritize ad groups where Expected CTR is Below Average from Step 6. For those ad groups:
- Rewrite the weakest ad using the google-ads-ad-writing skill for RSA standards
- Make sure the search term is matched in Headline 1
- Add more specific unique value propositions in Headlines 2 through 5
- Confirm the CTA is present in at least one description

**Ad Rotation note:** Campaigns using Smart Bidding (Max Clicks, Max Conversions, tCPA, tROAS) will have ad rotation automatically forced to "Optimize" by Google regardless of what you set. This is expected behavior. Set ad groups to "Do not optimize: Rotate indefinitely" only when you are running a deliberate A/B test and want equal exposure. For all evergreen ad groups, Optimize is fine since Smart Bidding is handling delivery.

**Third:** Check Account-Level Automated Assets every single week. Navigate to Campaigns > Assets > More > Account-level automated assets. Every toggle must be OFF. Google turns these back on without warning and they directly override your ad copy.

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

### Step 9: GA4, Conversion Tracking, and Website Check

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

**Conversion tracking check in Google Ads:**

Pull conversion data for the past 7 days using `MCP MASTER SERVER:gads_search`:

```
resource: campaign
fields: [[campaign.name](http://campaign.name), metrics.conversions, metrics.all_conversions, metrics.cost_per_conversion]
conditions: ["[segments.date](http://segments.date) DURING LAST_7_DAYS"]
customer_id: [client ID]
```

If conversions drop to zero or near zero for a campaign that normally converts, investigate immediately. Do not assume it is a slow period until you have ruled out a tracking break. Check the conversion actions in Google Ads, verify the tag is still firing in GA4, and test the form or phone number manually.

**Day-of-week and hour performance check (do this monthly or when diagnosing spend issues):**

Use `MCP MASTER SERVER:gads_search` with `[segments.day](http://segments.day)_of_week` or `segments.hour` to pull performance by time slot. Look for:
- Days or hours with high spend but zero conversions (consider excluding from the ad schedule)
- Days or hours with strong conversion rates that could benefit from a bid uplift
- Service businesses in particular often waste budget on weekends or after hours when nobody answers the phone

**What to check on the website:**
- No broken pages or 404 errors
- Forms are submitting correctly
- Phone numbers and emails are clickable
- Website formatting is not broken on mobile

If you find an issue with GA4, conversion tracking, or the website, flag it to the project manager immediately. Do not wait for the next check-in.

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
- [ ] Bid strategy checked per campaign (Max Clicks, Max Conversions, tCPA, or tROAS — no Manual CPC or Enhanced CPC)
- [ ] Campaigns on tCPA/tROAS confirmed to have 30+ conversions per month
- [ ] Any campaign struggling to spend stepped back to Max Clicks to restart progression
- [ ] Quality Scores reviewed (especially if Lost IS to Rank is high)
- [ ] All ads confirmed eligible with no disapprovals
- [ ] Ad performance evaluated using the 3-factor framework (see ad-optimization skill)
- [ ] Account-Level Automated Assets confirmed all OFF
- [ ] Competitor research done if CTR is Below Average
- [ ] GA4 checked for anomalies and conversion events still recording
- [ ] Conversion tracking verified in Google Ads (no unexplained drop to zero)
- [ ] Website checked for broken pages and form functionality
- [ ] Day-of-week performance reviewed if diagnosing spend issues or on monthly cadence
- [ ] Next week's deliverable written down with a measurable target
