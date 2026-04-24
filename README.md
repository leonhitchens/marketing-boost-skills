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
| Account Organization | `account-organization-skill/` | Structures, organizes, and audits Google Ads accounts — campaign and ad group layout, keyword segmentation, and preventing ad groups from competing against each other. |
| Google Ads Ad Writing | `google-ads-ad-writing-skill/` | Writes and reviews Google Search Ads (RSAs) following Ruskin Consulting's internal copy standards — 15 headlines, 4 descriptions, UVP framework, and disapproval rules. |
| Grammar | `grammar-skill/` | Checks, corrects, and improves written content against Ruskin Consulting's grammar standards — applies to ad copy, client emails, reports, proposals, and any other written deliverable. |
| Keyword Match Types | `keyword-match-types-skill/` | Explains and applies Google Ads keyword match types and negative match types — broad, phrase, exact, close variants, and guidance on which match type to use in a given situation. |
| Keyword Research | `keyword-research-skill/` | Builds keyword lists for Google Ads and SEO campaigns using competitor research and intent analysis — uses the Ahrefs MCP connector when available. |
| Search Terms | `search-terms-skill/` | Evaluates and categorizes Google Ads search terms — deciding whether to add a keyword, add a negative, move to another ad group, or take no action. |

---

## How Skills Work

Each skill file is a Markdown document with a `name`, `description`, and body. Claude Code reads the `description` field to decide when to invoke the skill automatically. The body contains the rules, frameworks, and output formats Claude follows when the skill is active.

To add a new skill, create a new folder and `.md` file following the same structure as the existing skills.
