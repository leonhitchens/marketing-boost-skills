# Marketing Boost Skills

A collection of Claude Code skills built for marketing and advertising work. These skills encode internal processes, copywriting standards, and workflows used across my consulting and media projects.

---

## About Leon Hitchens

I'm Leon Hitchens — a digital marketer, media producer, and entrepreneur. I run a small portfolio of businesses focused on marketing strategy, content, and web development.

- **[Ruskin Consulting](https://ruskinconsulting.com)** — My marketing consultancy. We help businesses grow through Google Ads, SEO, content strategy, and paid media management. These Claude Code skills are built around the internal standards and processes we use for client work.

- **[The Boost](https://theboost.fm)** — A podcast and media project covering marketing, business, and entrepreneurship. Focused on practical advice for small business owners and marketers.

- **[WP Creative House](https://wpcreativehouse.com)** — A WordPress design and development studio. We build fast, clean websites for small businesses and professionals.

- **[Leon Hitchens](https://leonhitchens.com)** — My personal site. Writing, thoughts, and updates on what I'm working on.

---

## About This Repository

This repo stores Claude Code skills that automate and standardize marketing work. Each skill lives in its own folder and is written as a Markdown file with a YAML frontmatter block that tells Claude when and how to use it.

### Skills

| Skill | Folder | Description |
|---|---|---|
| Account Check-In (ASH) | `account-checkin-ash-skill/` | Initial Google Ads account onboarding and top-to-bottom audit following the ASH framework (Account Settings and History) — use for new clients or accounts not reviewed in over a year. |
| Account Check-In (Weekly ACE) | `account-checkin-weekly-skill/` | Recurring weekly Google Ads check-in following the ACE framework (Account, Competition, Edits and Expansion) — covers billing pacing, search terms, impression share, quality scores, ads, competitors, and GA4. |
| Account Organization | `account-organization-skill/` | Structures, organizes, and audits Google Ads accounts — campaign and ad group layout, keyword segmentation, and preventing ad groups from competing against each other. |
| Ad Optimization | `ad-optimization-skill/` | Optimizes Google Ads by evaluating Quality Score, Ad Rank, and RSA copy strategy — uses the 3-factor framework (impressions, position, 2-click test) to decide which ads to pause and what to write next. |
| Google Ads Ad Writing | `google-ads-ad-writing-skill/` | Writes and reviews Google Search Ads (RSAs) following Ruskin Consulting's internal copy standards — 15 headlines, 4 descriptions, UVP framework, and disapproval rules. |
| Grammar | `grammar-skill/` | Checks, corrects, and improves written content against Ruskin Consulting's grammar standards — applies to ad copy, client emails, reports, proposals, and any other written deliverable. |
| Keyword Match Types | `keyword-match-types-skill/` | Explains and applies Google Ads keyword match types and negative match types — broad, phrase, exact, close variants, and guidance on which match type to use in a given situation. |
| Keyword Research | `keyword-research-skill/` | Builds keyword lists for Google Ads and SEO campaigns using competitor research and intent analysis — uses the Ahrefs MCP connector when available. |
| Search Terms | `search-terms-skill/` | Evaluates and categorizes Google Ads search terms — deciding whether to add a keyword, add a negative, move to another ad group, or take no action. |
| Landing Pages | `landing-pages-skill/` | Builds and audits standalone campaign landing pages — covers page types, the 15-second rule, headline formulas, CTA guidelines, social proof placement, message match, page speed, and thank-you page requirements. |
| Website Design | `website-design-skill/` | Evaluates and improves client websites against the 20 components of a high-converting site — covers color scheme, Core Web Vitals, mobile-first evaluation, schema markup, and a full audit checklist for technical, content, SEO, and ad campaign readiness. |

---

## MCP Servers

Several skills in this repo call external tools through MCP (Model Context Protocol) servers. Here is what each one is, whether it is publicly available, and what you need to do if you want to use these skills yourself.

### Ahrefs

The Ahrefs MCP is used in the keyword research and competitor research steps. Ahrefs provides an official MCP server that anyone with an Ahrefs subscription can connect. See the [Ahrefs MCP documentation](https://ahrefs.com/mcp) for setup instructions.

Skills that use Ahrefs: `keyword-research`, `account-checkin-weekly` (Step 8: Competitor Research).

### Google Ads and Google Analytics (MCP Master Server)

Skills reference a server called `MCP MASTER SERVER` for all Google Ads queries (via Google Ads API / GAQL) and Google Analytics 4 data. This is an internal server used at Ruskin Consulting and is not publicly available.

If you want to use these skills with your own setup, you will need to connect your own Google Ads and GA4 MCP servers and update the tool references in each skill file to match your server name and tool names.

**Community MCP servers to get you started:**

- [Google Ads MCP Server](https://github.com/cohnen/mcp-google-ads) — A community MCP server for querying Google Ads via GAQL. Covers campaigns, keywords, search terms, and performance metrics.
- [GA4 MCP Server](https://github.com/kilimanjaro2/google-analytics-mcp) — A community MCP server for querying Google Analytics 4 data including traffic, conversions, and sources.
- [MCP Servers (official directory)](https://github.com/modelcontextprotocol/servers) — The official Model Context Protocol repository listing available servers and the protocol specification.

Once you have your own servers running, find every instance of `MCP MASTER SERVER:gads_search`, `MCP MASTER SERVER:ga4_overview`, and `MCP MASTER SERVER:ga4_sources` in the skill files and replace them with the correct tool names from your own setup.

---

## How Skills Work

Each skill file is a Markdown document with a `name`, `description`, and body. Claude Code reads the `description` field to decide when to invoke the skill automatically. The body contains the rules, frameworks, and output formats Claude follows when the skill is active.

To add a new skill, create a new folder and `.md` file following the same structure as the existing skills.
