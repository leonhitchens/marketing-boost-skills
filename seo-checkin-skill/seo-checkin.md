---
name: seo-checkin
description: >
  Use this skill for bi-weekly SEO account check-ins (roughly twice a month). Triggers include: "seo check-in", "seo checkin", "do the seo check-in for", "seo review for", "check seo for", "how are rankings for", "seo performance for [client]", or any request to review organic search performance, ranking movement, or technical SEO health for a client. Uses Ahrefs Rank Tracker, Site Audit, GSC, GA4, and Basecamp. For Google Ads PPC check-ins use the account-checkin-weekly skill instead.
---

# SEO Bi-Weekly Check-In

From Ruskin Consulting SEO operations.

The bi-weekly SEO check-in tracks ranking movement, organic traffic trends, technical health, and competitor activity. Unlike PPC which reacts daily, SEO moves in weeks and months. The goal each check-in is not to find a silver bullet but to confirm the work done is moving the needle and to identify the next highest-leverage action.

**This check-in runs every two weeks, roughly twice a month.**

---

## Before Starting: Client Lookup

Look up the client by domain or name. Both formats are valid.

**Step 1: Find the client's spreadsheet ID**

Search the master tracker: `https://docs.google.com/spreadsheets/d/1RPSn8V2cP4p5KXh4Nu4nQdIe11lTjAGzesNh8rcDphg`

Use `Google Drive:search_files` to locate the master tracker or use `Google Drive:read_file_content` on that spreadsheet ID to pull the client list. Find the row matching the client by domain (e.g., `hoyack.com`) or name (e.g., `Hoyack`). Pull their individual spreadsheet ID from the Spreadsheet ID column.

**Step 2: Pull client KPI data**

The KPI hub is at: `https://docs.google.com/spreadsheets/d/1QHQzY8razWXJHSdj2TE5EpayidyLBCi94QjFLQBN6OI`

Pull the relevant tabs for this client: GSC, GA4, and Ahrefs tabs. These contain historical baselines to compare current check-in data against.

**Step 3: Find the client's Basecamp project**

Use `Basecamp Railway:search_projects` with the client's name and domain as two separate queries to maximize the chance of finding the right project. Pull completed tasks for the past two weeks using `Basecamp Railway:get_project_tasks` with `status: completed` and the relevant date range.

---

## The 7 Steps of the SEO Check-In

Run all steps every check-in. Some pull data simultaneously — those are noted.

---

### Step 1: Domain Authority and Overall Organic Health

Use `Ahrefs:site-explorer-metrics` to get a snapshot of the client's current organic health. Compare to the previous check-in baseline from the KPI hub.

```
target: [client domain]
date: [today YYYY-MM-DD]
mode: subdomains
```

**Key fields returned:**

| Field | What It Measures | Direction You Want |
|---|---|---|
| `org_keywords` | Total keywords ranking in top 100 | Up |
| `org_keywords_1_3` | Keywords ranking in positions 1-3 | Up |
| `org_traffic` | Estimated monthly organic visitors | Up |
| `org_cost` | Estimated traffic value in USD cents | Up |

Pull `Ahrefs:site-explorer-domain-rating` alongside this to track Domain Rating over time. DR is a lagging indicator but consistent growth signals a healthy link profile.

```
target: [client domain]
date: [today YYYY-MM-DD]
mode: subdomains
select: domain_rating,ahrefs_rank
```

Flag any significant drops in `org_keywords`, `org_traffic`, or DR since the last check-in. A sudden drop often signals a Google algorithm update, a technical issue, or a penalty.

---

### Step 2: Rank Tracker — Keyword Position Movement

This is the core of the bi-weekly check-in. Pull position data from Ahrefs Rank Tracker with a comparison date set to the previous check-in (14 days ago).

Use `Ahrefs:rank-tracker-overview` with the client's Rank Tracker `project_id`:

```
project_id: [client rank tracker project ID]
date: [today YYYY-MM-DD]
date_compared: [14 days ago YYYY-MM-DD]
device: desktop
select: keyword,position,position_prev,position_diff,volume,traffic,traffic_diff,url,serp_features,best_position_kind
order_by: traffic_diff:desc
limit: 100
```

**Categorize results into four buckets:**

| Bucket | Definition | Action |
|---|---|---|
| Movers Up | `position_diff` is negative (lower number = higher rank) | Document, connect to work done if applicable |
| Movers Down | `position_diff` is positive (higher number = lower rank) | Investigate cause, prioritize recovery |
| New Rankings | `position_prev` is null, `position` is not null | New keyword captured — note what content or change drove it |
| Lost Rankings | `position` is null, `position_prev` is not null | Page may have dropped out of top 100 — check in Site Explorer |

**Positions to highlight specifically:**

- Keywords that moved into top 3 (positions 1-3) — highest traffic impact
- Keywords in positions 4-10 — close to page 1 dominance, worth targeting for quick wins
- Keywords that dropped from top 10 to 11+ — these lose significant traffic and need attention

Also pull `Ahrefs:gsc-performance-by-position` to see how GSC-reported click distribution aligns with rank tracker data:

```
project_id: [client project ID in Ahrefs GSC integration]
date_from: [14 days ago YYYY-MM-DD]
date_to: [today YYYY-MM-DD]
```

---

### Step 3: GSC Performance — Clicks, Impressions, and CTR

Pull Google Search Console performance data using the dedicated GSC MCP connector. Use the client's verified site URL (e.g., `https://hoyack.com/` or `sc-domain:hoyack.com` depending on how the property is verified in GSC).

Use `GSC MCP:gsc_performance_overview` for the overall performance summary:

```
siteUrl: [client site URL as verified in GSC]
startDate: [14 days ago YYYY-MM-DD]
endDate: [today YYYY-MM-DD]
```

Use `GSC MCP:gsc_performance_queries` to pull the top performing queries:

```
siteUrl: [client site URL]
startDate: [14 days ago YYYY-MM-DD]
endDate: [today YYYY-MM-DD]
limit: 25
```

Use `GSC MCP:gsc_performance_pages` to see which pages are driving the most organic clicks:

```
siteUrl: [client site URL]
startDate: [14 days ago YYYY-MM-DD]
endDate: [today YYYY-MM-DD]
limit: 25
```

Also use `Ahrefs:gsc-performance-history` for the 28-day trend with weekly grouping (requires Ahrefs GSC integration project ID):

```
project_id: [client Ahrefs project ID]
date_from: [28 days ago YYYY-MM-DD]
date_to: [today YYYY-MM-DD]
history_grouping: weekly
```

**What to look for:**

| Metric | Flag If |
|---|---|
| Clicks | Down more than 10% vs prior period |
| Impressions | Down significantly (may signal indexing issue) |
| CTR | Below 2% on keywords ranking in positions 1-5 (title tag or meta description may need work) |
| Avg. Position | Rising number = rankings slipping across the board |

Low CTR on high-impression keywords is an immediate action item. The page is visible but not compelling. Update the title tag and meta description.

---

### Step 4: GA4 — Organic Traffic and Engagement

Use `Google Analytics MCP:ga4_overview` for the 14-day window:

```
propertyId: [client GA4 property ID]
startDate: [14 days ago YYYY-MM-DD]
endDate: [today YYYY-MM-DD]
```

Use `Google Analytics MCP:ga4_sources` to isolate organic search specifically:

```
propertyId: [client GA4 property ID]
startDate: [14 days ago YYYY-MM-DD]
endDate: [today YYYY-MM-DD]
```

**Metrics to compare bi-weekly:**

| Metric | What to Watch For |
|---|---|
| Organic sessions | Overall trend up or down |
| Organic users | New vs returning ratio |
| Bounce rate (organic) | Above 70% signals content-intent mismatch |
| Pages per session (organic) | Below 1.5 suggests visitors are not finding what they want |
| Avg. session duration | Sharp drops may signal slow pages or poor UX |
| Conversions from organic | The ultimate measure — is SEO traffic converting? |

Compare organic channel specifically against the previous 14-day period and flag any channel shift (e.g., organic declining while direct is rising could signal brand search changing, not content issues).

---

### Step 5: Site Audit — Technical SEO Health

Use `Ahrefs:site-audit-issues` with the client's Site Audit `project_id`. Run without a date to get the most recent crawl:

```
project_id: [client site audit project ID]
```

**Triage issues by importance:**

| Importance | Action |
|---|---|
| Error | Fix immediately. These actively hurt rankings or user experience. |
| Warning | Fix within the current check-in cycle. These suppress performance. |
| Notice | Log and address in a future cycle unless volume is high. |

**Priority issue categories to flag first:**

- **Indexability:** Noindexed pages that should be indexed, pages blocked by robots.txt
- **Links:** Broken internal links (4xx), redirect chains, orphaned pages
- **Content:** Duplicate title tags, missing meta descriptions, duplicate content, thin pages (under 300 words)
- **Usability and Performance:** Slow pages, non-mobile-friendly pages, Core Web Vitals failures
- **Redirects:** Redirect chains, redirect loops

For any issue with `change` > 0 (new issues added since last crawl), flag these specifically. New issues that appeared since the last check-in mean something changed on the site.

Use `Ahrefs:site-audit-page-explorer` to drill into specific pages with errors if needed.

---

### Step 6: Competitor Tracking

**Step 6a: Rank Tracker competitor overview**

If competitors are set up in the client's Rank Tracker project, use `Ahrefs:rank-tracker-competitors-overview` to pull their keyword overlap and position data:

```
project_id: [client rank tracker project ID]
date: [today YYYY-MM-DD]
date_compared: [14 days ago YYYY-MM-DD]
device: desktop
select: keyword,volume,serp_features
```

This returns `competitors_list` per keyword showing each competitor's URL, position, position change, and traffic estimate.

**Step 6b: Site Explorer competitor analysis**

Use `Ahrefs:site-explorer-organic-competitors` to pull the top organic competitors:

```
target: [client domain]
date: [today YYYY-MM-DD]
country: us
mode: subdomains
select: competitor,common_keywords,competitor_organic_traffic,competitor_domain_rating
order_by: common_keywords:desc
limit: 10
```

**For each competitor movement, ask:**

- Did a competitor gain rankings on keywords where the client dropped? If yes, look at what they changed (new content, backlinks, page updates).
- Did a competitor lose rankings the client could now capture? Look for their weakening pages as targets.
- Are there keywords competitors rank for top 5 that the client has no content for at all?

**Step 6c: Gap analysis and recommended actions**

For the top 2-3 competitors, use `Ahrefs:site-explorer-organic-keywords` to find keywords they rank in positions 1-10 where the client ranks 11+ or not at all:

```
target: [competitor domain]
date: [today YYYY-MM-DD]
mode: subdomains
country: us
select: keyword,volume,best_position,keyword_difficulty,sum_traffic
order_by: volume:desc
limit: 50
where: {"field":"best_position","is":["lte",10]}
```

Cross-reference against the client's rankings to find gaps. These become blog or landing page recommendations.

**For each meaningful competitor move, provide a specific recommendation:**

| Competitor Action | What It Means | Recommended Response |
|---|---|---|
| Competitor published new blog on X | They are targeting a keyword gap | Write a competing post targeting the same keyword with more depth |
| Competitor gained backlinks to a page | Their authority on that topic increased | Build backlinks to the client's competing page |
| Competitor improved position on a key term | Client may see traffic drop on that term | Update and strengthen the client's page targeting the same term |
| Competitor dropped significantly | Opportunity to capture their traffic | Optimize the client's page for that keyword and consider outreach |

---

### Step 7: Work Done and What Comes Next

**Step 7a: Connect work done to ranking changes**

Pull completed Basecamp tasks for the past two weeks using `Basecamp Railway:get_project_tasks` with `status: completed` and the date range.

Connect each major task to the metric it was designed to move:

| Work Completed | Metric to Check |
|---|---|
| Published new blog post | New keyword rankings, impressions |
| Updated existing page | Position movement on target keyword |
| Built backlinks | Domain Rating, rankings for linked page |
| Fixed technical issues from Site Audit | Crawl errors resolved, indexability restored |
| Updated title tags / meta descriptions | CTR improvement in GSC |
| Added internal links | Traffic to linked pages, ranking improvements |
| Improved page speed | Bounce rate, session duration, Core Web Vitals |

**Step 7b: Identify next actions**

Based on all seven steps, determine the top 3 priorities for the next two weeks. Frame each as a specific action with a measurable expected outcome.

**Priority framework:**

1. **Fix first** — any Error-level site audit issues and any page that dropped significantly in rankings
2. **Optimize second** — pages in positions 4-15 that are close to a ranking jump with a small improvement
3. **Create third** — new content targeting competitor keyword gaps identified in Step 6

---

## Report Structure

The bi-weekly check-in produces a written summary deliverable as a .docx using the docx skill, following the same story-first approach as the monthly PPC report.

**Report sections:**

1. **Summary (2-3 sentences)** — what happened this period, one sentence on the overall trend
2. **Work Completed** — tasks from Basecamp with metric connections
3. **Ranking Movement** — top movers up, top movers down, new and lost rankings
4. **GSC Performance** — clicks, impressions, CTR, average position vs prior period
5. **Organic Traffic (GA4)** — sessions, users, engagement, conversions from organic
6. **Technical Health** — new errors or warnings from Site Audit, issues resolved
7. **Competitor Movements** — what competitors did and what we recommend in response
8. **Next Two Weeks** — top 3 priority actions with expected outcomes

**Writing guidelines:**

- No em dashes. No AI-isms. Refer to the grammar-writing skill.
- Lead with what moved and why. Do not just list metrics.
- Connect every significant metric change to a cause if possible.
- Frame competitor movements as opportunities, not threats.
- Be specific in next actions. "Optimize the dental implants page for 'affordable dental implants manhattan'" is useful. "Improve SEO content" is not.
- Month-over-month and bi-weekly comparisons always. Never present a number without context.

---

## Quick Reference: Tools and Parameters

| Step | Tool | Key Parameters |
|---|---|---|
| Client lookup | `Google Drive:read_file_content` | Master tracker spreadsheet ID |
| Basecamp tasks | `Basecamp Railway:get_project_tasks` | status: completed, 14-day date range |
| Domain health | `Ahrefs:site-explorer-metrics` | target, date, mode: subdomains |
| Domain Rating | `Ahrefs:site-explorer-domain-rating` | target, date, mode: subdomains |
| Rank movement | `Ahrefs:rank-tracker-overview` | project_id, date, date_compared (14 days ago), device: desktop |
| GSC overview | `GSC MCP:gsc_performance_overview` | siteUrl, startDate, endDate |
| GSC top queries | `GSC MCP:gsc_performance_queries` | siteUrl, startDate, endDate, limit |
| GSC top pages | `GSC MCP:gsc_performance_pages` | siteUrl, startDate, endDate, limit |
| GSC 28-day trend | `Ahrefs:gsc-performance-history` | project_id, date_from, date_to, history_grouping: weekly |
| GSC by position | `Ahrefs:gsc-performance-by-position` | project_id, date_from, date_to |
| GA4 overview | `Google Analytics MCP:ga4_overview` | propertyId, startDate, endDate |
| GA4 sources | `Google Analytics MCP:ga4_sources` | propertyId, startDate, endDate |
| Site audit | `Ahrefs:site-audit-issues` | project_id |
| Competitor overview | `Ahrefs:rank-tracker-competitors-overview` | project_id, date, date_compared, device |
| Competitor keywords | `Ahrefs:site-explorer-organic-competitors` | target, date, country, mode: subdomains |
| Competitor gap | `Ahrefs:site-explorer-organic-keywords` | competitor domain, date, mode: subdomains, where: best_position lte 10 |

---

## Bi-Weekly SEO Check-In Checklist

- [ ] Client found in master tracker by domain or name
- [ ] Client spreadsheet ID located and KPI hub tabs reviewed for baseline
- [ ] Basecamp completed tasks pulled for the past 14 days
- [ ] Domain metrics pulled and compared to last check-in (org_keywords, org_traffic, DR)
- [ ] Rank Tracker positions pulled with 14-day comparison
- [ ] Top movers up and down identified and categorized
- [ ] Keywords entering or exiting top 10 flagged
- [ ] GSC performance pulled (clicks, impressions, CTR, avg position)
- [ ] Low CTR keywords on positions 1-5 identified for title/meta update
- [ ] GA4 organic traffic and engagement pulled and compared
- [ ] Organic conversion data reviewed
- [ ] Site Audit issues reviewed — Errors and new issues flagged
- [ ] Competitor rank movements reviewed
- [ ] Competitor keyword gaps identified with specific recommendations
- [ ] Work done connected to metric changes
- [ ] Top 3 priority actions for next two weeks defined with expected outcomes
- [ ] .docx report written following the 8-section structure
