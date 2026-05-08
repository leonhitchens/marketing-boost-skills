---
name: monthly-reporting
description: >
  Use this skill whenever the user needs to write, draft, or produce a monthly report for a Google Ads client. Triggers include: "write the monthly report for", "draft the report for", "monthly report for [client]", "write up the results for", "what should I put in the report", "summarize this month's performance", or any request to produce a client-facing performance update. Uses Basecamp to pull completed work, MCP Master Server for Google Ads and GA4 data, and connects work done to metric improvements to tell a coherent story.
---

# Monthly Reporting

From Ruskin Consulting Training Module 19.

---

## The Purpose of a Monthly Report

A monthly report is how Ruskin communicates to clients that we are professionals who are extremely good at our jobs and that we care about their results. The report should make the client feel confident they are in expert hands.

Write every report from the position of the expert. You are the captain of the ship. Tell the client what happened, why it matters, and what comes next. Do not just dump numbers. Tell a story.

The report has two jobs:
1. Show the results of the work done this month
2. Explain what comes next and why

---

## The 14 Core Metrics

Know these by heart. They are the foundation of every report and every optimization decision.

**Performance metrics:**

| Metric | Definition | Formula |
|---|---|---|
| Clicks | Times someone clicked the ad | Raw count |
| Impressions | Times the ad was displayed | Raw count |
| Impr. (Top) % | % of impressions shown above organic results | Impressions above organic / Total impressions |
| Impr. (Abs. Top) % | % of impressions shown as the very first ad | Abs. top impressions / Total impressions |
| CTR | Click-through rate | Clicks / Impressions x 100% |
| Avg. CPC | Average cost per click | Cost / Clicks |
| Cost | Total spend | Raw count |

**Conversion metrics (most important to clients):**

| Metric | Definition | Priority |
|---|---|---|
| Cost/Conversion (CPA) | Cost divided by conversions | #1 most important |
| Conversions | Form fills, calls, purchases | #2 most important |
| Conversion Rate | Conversions divided by clicks | #3 most important |

**Competitive metrics:**

| Metric | Definition |
|---|---|
| Search Impression Share | Impressions received / Eligible impressions |
| Search Exact Match Impression Share | Exact match impressions received / Eligible exact match impressions |
| Search Lost IS (Rank) | How often ads did not show due to poor Ad Rank |
| Search Lost IS (Budget) | How often ads did not show due to low budget |

**Landing page / engagement metrics (from GA4):**

| Metric | Definition |
|---|---|
| Bounce Rate | % of sessions where users left from the landing page without interacting |
| Pages per Session | Average pages viewed per visit |
| Avg. Session Duration | Total session time / Number of sessions |
| % New Sessions | % of visits from first-time users |

---

## Step 1: Pull Completed Work from Basecamp

Before pulling any data, get the list of work completed this month for the client. This is what the report is built around. Work done connects directly to metric changes.

Use `Basecamp Railway:search_projects` to find the client's project, then `Basecamp Railway:get_project_tasks` with `status: completed` and date filters for the reporting month to pull all completed tasks.

**Task-to-metric connections:**

| Type of Work Completed | Metric It Should Improve |
|---|---|
| Ad rewriting / new RSAs | CTR, Ad Relevance, Quality Score |
| New landing pages | Conversion Rate, Landing Page Experience, Bounce Rate |
| Negative keyword additions | Cost, Avg. CPC, Conversion Rate (removing wasted spend) |
| Search term review and cleanup | CTR, CPA, Conversion Rate |
| Bid adjustments | Impr. (Top) %, Impr. (Abs. Top) %, Avg. CPC |
| Account restructure / new ad groups | CTR, Ad Relevance, Quality Score |
| Budget reallocation | Cost efficiency, Impression Share |
| Keyword additions | Impressions, Clicks, Conversions |
| Ad extensions / assets added | CTR, Impr. (Top) % |
| Conversion tracking setup or fixes | Conversions, CPA accuracy |

Every major task completed should connect to at least one metric improvement in the report narrative.

---

## Step 2: Pull Google Ads Performance Data

Use `Google Ads MCP:search` to pull the current month's performance and the prior month for comparison.

**Campaign-level overview query:**

```
resource: campaign
fields: [
  campaign.name,
  metrics.clicks,
  metrics.impressions,
  metrics.ctr,
  metrics.average_cpc,
  metrics.cost_micros,
  metrics.conversions,
  metrics.cost_per_conversion,
  metrics.conversions_from_interactions_rate,
  metrics.search_impression_share,
  metrics.search_rank_lost_impression_share,
  metrics.search_budget_lost_impression_share,
  metrics.search_top_impression_share,
  metrics.search_absolute_top_impression_share
]
conditions: [
  "segments.date DURING LAST_MONTH"
]
```

Note: `metrics.cost_micros` is in micros (divide by 1,000,000 for dollars). `metrics.average_cpc` is also in micros.

Run the same query with `DURING THIS_MONTH` for current period if reporting mid-month, or compare LAST_MONTH to the month before by using date range conditions.

**Always compare month over month.** Every metric should be shown as: this month vs. last month, with the delta and whether it improved or declined.

---

## Step 3: Pull GA4 Data for Website Performance

Use `Google Analytics MCP:ga4_overview` for overall site traffic and engagement metrics. Set `startDate` and `endDate` to the reporting month.

Use `Google Analytics MCP:ga4_sources` to isolate paid search traffic specifically, so you can attribute website behavior to Google Ads visitors rather than all traffic sources combined.

Key metrics to pull:
- Sessions
- Users
- Bounce rate
- Pages per session
- Average session duration
- % New sessions

Compare to the prior month to show trajectory.

---

## Step 4: Write the Report

### Report Structure

**1. Summary (2-3 sentences)**
One paragraph that captures the overall story of the month. Did performance improve, hold steady, or decline? What was the most significant thing that happened?

**2. Work Completed This Month**
List the tasks completed from Basecamp. For each major task, connect it to the metric it was designed to improve.

Example: "This month we rewrote all ads in the Implants campaign with new headlines targeting high-intent search terms. This was designed to improve CTR and Ad Relevance for that campaign."

**3. Performance Results**
Present the 14 core metrics with month-over-month comparison. Group them:
- Paid Search Performance (Clicks, Impressions, CTR, Avg. CPC, Cost)
- Conversions (Conversions, CPA, Conversion Rate)
- Competitive Position (Impression Share, Lost IS Rank, Lost IS Budget)
- Website Engagement (Bounce Rate, Pages/Session, Session Duration)

For each metric, state whether it improved or declined and by how much. Connect improvements back to the work done where possible.

Example: "CTR in the Implants campaign increased from 4.2% to 6.8% month over month. This aligns with the ad rewrite completed in the first week of the month."

**4. What We Are Working on Next**
Tell the client what is coming next and why. Be specific. This shows you have a plan and are managing their account proactively.

Example: "Next month we will focus on expanding the Cleaning campaign with 3 new ad groups targeting teeth whitening search terms. We will also review search terms to remove any non-converting traffic that has accumulated over the past 60 days."

---

## Writing Guidelines

These rules apply to every report, every time.

**Tell a story, not a spreadsheet.** Numbers without context mean nothing to most clients. Every metric needs a sentence explaining what it means and whether it is good or bad.

**Lead with what matters to the client.** Clients care about conversions and CPA first. Traffic and clicks second. Lead with conversion results, not impressions.

**Own good results and bad results.** If something improved because of work you did, say so. If something declined, explain why and what you are doing about it. Do not hide behind passive language.

**Be the expert.** The client hired you because they do not understand this. Write like the person who knows what is happening and has a plan. Do not hedge everything.

**Month-over-month always.** Never present metrics in isolation. Every number needs a comparison. A 5% CTR means nothing without knowing if it was 3% or 8% last month.

**No em dashes. No AI-isms.** Write clearly and directly. Avoid filler words and phrases that sound generic or robotic. Refer to the grammar-writing skill for the full list.

---

## Metric Benchmarks (General Reference)

Use these as rough guides when explaining to a client whether a number is good or bad. Every industry and account differs, but these are reasonable starting points.

| Metric | Below Average | Average | Strong |
|---|---|---|---|
| CTR (Search) | Below 2% | 2-5% | Above 5% |
| Conversion Rate | Below 2% | 2-5% | Above 5% |
| Search Impression Share | Below 40% | 40-70% | Above 70% |
| Quality Score | 1-4 | 5-7 | 8-10 |
| Bounce Rate | Above 70% | 50-70% | Below 50% |

---

## Quick Tool Reference

| Task | Tool | Notes |
|---|---|---|
| Find client Basecamp project | `Basecamp Railway:search_projects` | Search by name and domain |
| Pull completed tasks | `Basecamp Railway:get_project_tasks` | status: completed, date range |
| Pull Google Ads metrics | `Google Ads MCP:search` | Requires `customer_id`. Use `orderings` not `order_by` |
| Pull GA4 overview | `Google Analytics MCP:ga4_overview` | Requires `propertyId` |
| Pull GA4 traffic by channel | `Google Analytics MCP:ga4_sources` | Requires `propertyId` |
