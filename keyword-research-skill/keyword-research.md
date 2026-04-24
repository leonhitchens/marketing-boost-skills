---
name: keyword-research
description: >
  Use this skill whenever the user needs to do keyword research for a Google Ads or SEO campaign. Triggers include: "do keyword research for", "find keywords for", "what keywords should I target", "competitor keyword research", "keyword ideas for", "research keywords for this client", "what are people searching for", "find me keywords", or any request to build a keyword list for a client or campaign. Also use when the user provides a website URL or competitor domain and wants to know what keywords to go after. Always use the Ahrefs MCP connector when doing keyword research.
---

# Keyword Research

From Ruskin Consulting Training Module 12.

---

## The Goal

Find the keywords clients should be buying on Google Ads and ranking for organically. The goal is not to reinvent the wheel. Competitors have already spent money figuring out what works. Use the tools below to find what they are bidding on and ranking for, then build a smarter list.

---

## Step 1: Start with the Client's Website

Before opening any tool, go through the client's website. Every service page, product category, and landing page is a keyword idea. Write down every product, service, and location the client offers. This becomes your seed list.

**Example (Dr. Manhattan DDS):**
Reading the website surfaces: teeth cleaning, cosmetic dentistry, tooth restoration, dental implants, emergency dentist, family dentist, oral checkup, restorative dentistry, cracked tooth repair.

Those become seed keywords: "dentist near me", "dentist in manhattan", "cosmetic dentist", "emergency dentist", "affordable dental implants", etc.

---

## Step 2: Keyword Research with Ahrefs

Ahrefs is the primary tool for keyword research at Ruskin. Use the MCP connector to pull data directly in the conversation.

### Key field names (verified against Ahrefs API)

| Field | Description |
|---|---|
| `keyword` | The keyword |
| `volume` | Average monthly searches (last 12 months) |
| `difficulty` | Keyword difficulty 0-100 |
| `cpc` | Cost per click in USD cents (divide by 100 for dollars) |
| `clicks` | Average monthly clicks on search results |
| `traffic_potential` | Total organic traffic the #1 ranking page gets from all its keywords |
| `intents` | Object with boolean fields: `informational`, `navigational`, `commercial`, `transactional`, `branded`, `local` |
| `parent_topic` | The broader topic this keyword falls under |

### 2a. Keyword Overview

Use `keywords-explorer-overview` to get core metrics for your seed keywords.

**Required parameters:**
- `country`: Two-letter country code (`us`, `au`, `gb`, etc.)
- `keywords`: Comma-separated seed keywords
- `select`: `keyword,volume,difficulty,cpc,clicks,traffic_potential,intents`
- `order_by`: `volume:desc`

### 2b. Matching Terms (Keyword Expansion)

Use `keywords-explorer-matching-terms` to expand your seed list and surface long-tail variations. Note: this tool does NOT return a `clicks` field — do not request it.

**Required parameters:**
- `country`: Two-letter country code
- `keywords`: Your seed keywords
- `select`: `keyword,volume,difficulty,cpc,traffic_potential`
- `order_by`: `volume:desc`
- `limit`: 50-100
- `match_mode`: `terms` (any order) or `phrase` (exact order) — defaults to `terms`

### 2c. Search Suggestions

Use `keywords-explorer-search-suggestions` to find autocomplete-style long-tail terms. Note: this tool does NOT return `clicks` or `traffic_potential` — do not request them.

**Required parameters:**
- `country`: Two-letter country code
- `keywords`: Your seed keywords
- `select`: `keyword,volume,difficulty,cpc`
- `limit`: 25-50

### 2d. Related Terms

Use `keywords-explorer-related-terms` to find "also rank for" and "also talk about" keywords. Note: this tool does NOT return `clicks` — do not request it.

**Required parameters:**
- `country`: Two-letter country code
- `keywords`: Your seed keywords
- `select`: `keyword,volume,difficulty,cpc,traffic_potential`
- `order_by`: `volume:desc`
- `limit`: 50

---

## Step 3: Competitor Research with Ahrefs

Competitors have already validated what works. Use Ahrefs to find what they rank for organically and what they are bidding on in paid search.

### 3a. Find Organic Competitors

Use `site-explorer-organic-competitors` to identify who the client competes against in search.

**Required parameters:**
- `target`: Client's domain (e.g., `drmanhattan.com`)
- `country`: Two-letter country code
- `date`: Today's date in YYYY-MM-DD format
- `mode`: `subdomains` (always use this for domains — using `domain` can exclude www and subdomains)
- `select`: `competitor,common_keywords,competitor_organic_traffic`
- `limit`: 10

### 3b. Pull Competitor Organic Keywords

Use `site-explorer-organic-keywords` to see every keyword a competitor ranks for. Any keyword they rank for that the client does not have is an opportunity.

**Required parameters:**
- `target`: Competitor domain
- `date`: Today's date in YYYY-MM-DD format
- `mode`: `subdomains`
- `country`: Two-letter country code
- `select`: `keyword,volume,best_position,sum_traffic,cpc,keyword_difficulty`
- `order_by`: `volume:desc`
- `limit`: 100

Note: the position field is `best_position`, not `position`. To filter for top 10 rankings only, use:
`where`: `{"field":"best_position","is":["lte",10]}`

### 3c. Pull Competitor Paid Keywords

Use `site-explorer-paid-pages` to see what pages a competitor is running paid ads to and what keywords drive that traffic. This is a page-level view, not keyword-level.

**Required parameters:**
- `target`: Competitor domain
- `date`: Today's date in YYYY-MM-DD format
- `mode`: `subdomains`
- `select`: `url,sum_traffic,keywords,top_keyword,top_keyword_volume`
- `order_by`: `sum_traffic:desc`
- `limit`: 25

---

## Step 4: Evaluate Keywords Using the KPI Formula

Not every high-volume keyword is worth buying. Use the Ruskin KPI formula to score and prioritize:

**KPI = Search Volume / (Competition + 10)**

Where:
- `volume` = average monthly searches from Ahrefs
- `difficulty` = the keyword difficulty score (0-100)
- `+10` prevents division by zero on very low competition keywords

A higher KPI score means better opportunity relative to competition. Use this to rank the final list and cut keywords that score too low.

Note: Ahrefs `difficulty` is an SEO-focused score. For paid search, also factor in `cpc` — a high CPC means advertisers are willing to pay for that keyword, which is a signal that it converts.

---

## Step 5: Apply the Sales Funnel Filter

Run every keyword through the sales funnel before finalizing. Prioritize the bottom. Cut or deprioritize the top.

| Funnel Stage | Action |
|---|---|
| Transactional / Purchase intent | Include, bid aggressively |
| Commercial / Evaluation intent | Include |
| Informational / Interest | Include with caution, watch CPA |
| Awareness / Research | Exclude from paid, consider for SEO content only |
| N/A / Irrelevant | Cut entirely |

Ahrefs `intents` field returns intent signals per keyword (`transactional`, `commercial`, `informational`, `navigational`, `local`, `branded`). Use this to filter quickly at scale.

---

## Step 6: Location Settings

Always match the `country` parameter to where the client's customers are. Use `us` for US-based clients, `au` for Australia, etc.

For very local businesses, keyword data at city or zip code level is sparse in Ahrefs. Pull at the country level for volume estimates, then apply tighter geo-targeting inside the actual Google Ads campaigns.

---

## Keyword Research Output Format

When delivering keyword research, present results in this order:

1. **Summary** - How many keywords found, top themes, recommended focus areas
2. **Top Keywords Table** - Keyword, monthly volume, difficulty, CPC (in dollars), KPI score, intent, funnel stage
3. **Competitor Insights** - Key competitors found, top keywords they rank for that the client does not have
4. **Recommendations** - Which keywords to target first in paid, which to target in SEO, which to skip

---

## Quick Reference: Ahrefs Tools for Keyword Research

| Task | Tool | Key Select Fields |
|---|---|---|
| Seed keyword metrics | `keywords-explorer-overview` | `keyword,volume,difficulty,cpc,clicks,traffic_potential,intents` |
| Expand keyword list | `keywords-explorer-matching-terms` | `keyword,volume,difficulty,cpc,traffic_potential` |
| Autocomplete / long-tail | `keywords-explorer-search-suggestions` | `keyword,volume,difficulty,cpc` |
| Related / adjacent keywords | `keywords-explorer-related-terms` | `keyword,volume,difficulty,cpc,traffic_potential` |
| Find organic competitors | `site-explorer-organic-competitors` | `competitor,common_keywords,competitor_organic_traffic` |
| Competitor organic rankings | `site-explorer-organic-keywords` | `keyword,volume,best_position,sum_traffic,cpc,keyword_difficulty` |
| Competitor paid pages | `site-explorer-paid-pages` | `url,sum_traffic,keywords,top_keyword,top_keyword_volume` |

---

## Other Tools

- **Google Keyword Planner** (inside Google Ads) - Free. Best for confirming exact bid ranges before launching a campaign since it pulls directly from Google's own auction data. Requires access to the client's Google Ads account.
- **Google Trends** - Good for spotting seasonal patterns and trending blog topics. Not a primary research tool for paid search.
- **Google Auction Insights** - Shows which competitors are bidding in the same auctions. Does not reveal specific keywords but useful for identifying who to research in Ahrefs.
