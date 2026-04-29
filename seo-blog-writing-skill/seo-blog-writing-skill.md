---
name: seo-blog-writing
description: >
  Use this skill whenever the user needs to research, outline, or write an SEO blog post. Triggers include: "write a blog post", "write a blog for", "create a blog", "blog about", "write an article", "SEO blog", "blog post for [client]", or any request to produce written content intended to rank in search. The skill runs in four sequential steps: gather context, keyword research, outline, write. Always complete all four steps in order.
---

# SEO Blog Writing

From Ruskin Consulting Blog Writing SOP.

The goal is a blog post that reads like a real expert wrote it, ranks well in search, and moves the reader toward a specific action. It should not read like AI generated it. It will be run through Grammarly for AI detection after writing, so every draft must pass the human writing standard.

No em dashes. No AI-isms. Write with a point of view.

---

## Before Starting: What to Ask

If the user has not already provided the following, ask before doing anything else:

1. **Topic** - What is the blog post about? (If not provided, offer 5 to 10 topic ideas based on the client's niche and website before proceeding.)
2. **Focus keyword** - What keyword should this post rank for? (If not provided, pull it from Ahrefs keyword research and confirm with the user.)
3. **Client website URL** - Needed for internal link research and to check what they already rank for.
4. **Target audience** - Who is reading this? (Industry, role, pain point, or demographic.)
5. **CTA** - What do you want the reader to do at the end? (Call, contact form, download, book a demo, etc.)
6. **Tone** - Conversational, professional, direct, educational? Default to conversational and direct if not specified.

Do not ask all six in a list. Ask in a natural way and proceed as soon as you have enough to start. Topic, keyword, and website URL are the minimum required.

---

## Step 1: Keyword Research with Ahrefs

Run keyword research before writing a single word of the outline. The keyword data determines the primary keyword, secondary keywords, and ideal word count.

### 1a. Extract the Client's Brand Colors

Before any keyword research, fetch the client's website and extract the color palette. This is used to style the final HTML output.

Use `web_fetch` on the client's homepage and inspect the CSS or inline styles for:
- **Primary color** — the dominant brand color (usually the main CTA button, header background, or logo color)
- **Secondary color** — an accent or supporting color
- **Text color** — the primary body text color (usually near-black)
- **Background color** — the main page background (usually white or off-white)
- **Font family** — the primary font used in headings and body text

If the colors cannot be extracted from the homepage fetch, note generic fallbacks (white background, dark text, a professional accent color) and flag to the user that brand colors should be confirmed before publishing.

Store these values. They will be used in Step 4 when generating the HTML output.

### 1b. Check What the Client Already Ranks For

Use `Ahrefs:site-explorer-organic-keywords` to pull the client's existing organic rankings. Look for:
- Keywords related to the blog topic that already have some ranking (positions 5-30 are candidates to push into the top 3 with a strong post)
- Gaps where competitors rank but the client does not

```
target: [client domain]
date: [today YYYY-MM-DD]
mode: subdomains
country: us
select: keyword,volume,best_position,sum_traffic,keyword_difficulty
order_by: volume:desc
limit: 50
where: {"field":"best_position","is":["lte",30]}
```

**Efficiency note:** Run 1c, 1d, and 1e simultaneously where possible. Pulling keyword overview, matching terms, search suggestions, related terms (both modes), and SERP overview in parallel produces faster, more complete data than running them sequentially. Each call is independent.

### 1c. Primary Keyword Research

Use `Ahrefs:keywords-explorer-overview` to get core metrics for the focus keyword:

```
country: us
keywords: [focus keyword]
select: keyword,volume,difficulty,cpc,traffic_potential,global_volume,intents
```

### 1d. Secondary Keyword Expansion

Use `Ahrefs:keywords-explorer-matching-terms` to find related and long-tail variations:

```
country: us
keywords: [focus keyword]
select: keyword,volume,difficulty,cpc,traffic_potential
order_by: volume:desc
limit: 50
```

Use `Ahrefs:keywords-explorer-search-suggestions` for question-based and long-tail terms (these become H2 and H3 candidates):

```
country: us
keywords: [focus keyword]
select: keyword,volume,difficulty,cpc
limit: 30
```

Use `Ahrefs:keywords-explorer-related-terms` twice — once for each mode:

**also_rank_for** — keywords that pages ranking for your topic also rank for. These are the terms Google expects to see in a topically authoritative post:
```
country: us
keywords: [focus keyword]
select: keyword,volume,difficulty,traffic_potential,global_volume
terms: also_rank_for
order_by: volume:desc
limit: 30
```

**also_talk_about** — semantic keywords and concepts Google associates with the topic. Use these to fill out sections and avoid thin content:
```
country: us
keywords: [focus keyword]
select: keyword,volume,difficulty,traffic_potential,global_volume
terms: also_talk_about
order_by: volume:desc
limit: 30
```

### 1e. Competitor Content Research

Use `Ahrefs:serp-overview` to pull the top ranking pages for the primary keyword. This is faster and more reliable than a manual Google search and returns domain rating, backlinks, and traffic per result — all useful for assessing how hard the SERP is to crack:

```
country: us
keyword: [primary keyword]
select: url,position,domain_rating,backlinks,traffic,title
top_positions: 10
```

If Ahrefs returns no SERP data for a keyword, that signals a genuinely new or low-indexed term rather than a data error. Flag it as a first-mover opportunity and note the lack of established competition as an advantage.

For each competitor post note:
- Approximate word count
- Number of H2 sections
- Main angle or argument
- Gaps or angles they do not cover

**Determine target word count:** Match or slightly exceed the average word count of the top 3 ranking posts. The range is 800 to 2,000 words. Ask the user if their preference differs from what the data suggests. Do not write shorter than what is ranking unless the data clearly supports it.

### 1f. Keyword Research Summary

Before moving to the outline, present:

| Keyword | US Volume | Global Volume | Difficulty | Role |
|---|---|---|---|---|
| [primary keyword] | X | X | X | Primary |
| [secondary 1] | X | X | X | Secondary |
| [secondary 2] | X | X | X | Secondary |
| [long-tail 1] | X | X | X | H2 or H3 candidate |
| [question keyword] | X | X | X | FAQ or H3 candidate |

Include `global_volume` alongside US volume. For topics with international audiences (crypto, SaaS, e-commerce, travel) global volume is often the more relevant planning metric. For local service businesses, US volume is sufficient.

Confirm the primary keyword with the user before proceeding. If the focus keyword has very low volume or very high difficulty, recommend a better alternative from the research.

---

## Step 2: Deep Research

Before writing the outline, gather the source material. This is what separates a good SEO blog from a generic one.

### What to research:

**External sources (3 to 5 minimum):**

Prioritize sources in this order:
1. **.gov sources** — government agencies, regulatory bodies, official statistics (e.g., bls.gov, census.gov, cdc.gov, ftc.gov). These carry the highest trust signal.
2. **.edu sources** — university research, academic studies, institutional publications. Strong authority and trusted by Google.
3. **Trusted industry publications** — well-known non-competitor sources: Forbes, Harvard Business Review, Gartner, McKinsey, Statista, industry-specific publications with established authority.

**Never link to a competitor.** If a stat or study is only cited on a competitor's site, find the original source and link to that instead. Do not send readers to a business that competes with the client.

**Do not repeat links.** Each external source should appear only once in the article. Do not link to the same domain twice.

**Verify every URL before including it.** Fetch each link and confirm it returns a live page. A 404 in the published article signals low quality to both readers and Google. If a source returns a 404, find an alternative source for the same data point. Do not include a link you have not confirmed is live.

**Internal links (3 to 5 minimum):**
- Fetch `[client domain]/sitemap.xml` using `web_fetch` to get the full list of indexed pages. This is faster and more complete than a web search because it returns every page the client has submitted to Google, not just ones that happen to rank.
- Scan the sitemap for pages relevant to the blog topic: service pages, case studies, related blog posts, landing pages, resource pages.
- If the sitemap is an index file pointing to multiple sitemaps (common on larger sites), fetch each sub-sitemap to get the full page list.
- Each internal link should go to a page that is genuinely relevant to the section it sits in, not just any page on the site.
- **Verify every internal URL before including it.** Fetch each candidate page and confirm it loads and returns a live page. Do not link to pages that return 404, redirect chains, or are noindexed. If a page is gone, find an alternative or use a placeholder noting it needs a live destination.

**People Also Ask / Related Questions:**
- Pull from the keyword research in Step 1 (search suggestions tool)
- These often become H2 or H3 headings and FAQ sections
- Including PAA questions improves the chance of capturing featured snippets

---

## Step 3: The Outline

Write the full outline before writing the post. Do not skip this step.

### Outline format:

```
BLOG OUTLINE

Primary keyword: [keyword]
Secondary keywords: [list]
Content type: [Informational / Commercial / Transactional]
Target word count: [X words based on competitor research]
Audience: [who is reading this]
Tone: [tone]

META
Title tag: [under 60 characters, includes primary keyword]
Meta description: [under 160 characters, compelling and clickable]
URL slug: [short, keyword-rich, no stop words]

OUTLINE
H1: [Full title, includes primary keyword, written to attract clicks]

Introduction (approx X words)
[Hook that connects to the reader's pain point or question. Reference a stat or data point from external research. Do not start with "In today's world" or any generic opener.]

H2: [Section title] (approx X words)
[One sentence on what this section covers and why it matters]
[Note: Place [EXTERNAL LINK: source] here if applicable]

  H3: [Sub-section if needed]
  [One sentence on what this covers]

H2: [Section title] (approx X words)
[One sentence on what this section covers]
[Note: Place [INTERNAL LINK: page name] here]

[Continue for all H2s...]

H2: Frequently Asked Questions (optional, include if PAA data supports it)
  H3: [Question 1]
  H3: [Question 2]
  H3: [Question 3]

Conclusion (approx X words)
[Summarize the key takeaway. Do not restate every section. End with a transition into the CTA.]

CTA
[Specific call-to-action matching what the client wants the reader to do]

LINKS
External links to include:
- [Source name] - [URL] - [Which section it supports]

Internal links to include:
- [Page name] - [URL] - [Which section it supports]
```

### Outline rules:
- 4 to 7 H2 sections for a 1,000 to 1,500 word post. Not 20. Not 10.
- H3s only when a section genuinely needs sub-division. Do not create H3s just to add structure.
- Every H2 should be able to stand alone as a clear question or statement a reader would care about
- The introduction does not get an H2
- The conclusion does not get an H2

---

## Step 4: Write the Article

Write from the outline. Do not deviate from the structure unless there is a clear reason.

### Writing rules (apply to every post, every time):

**Voice and readability:**
- Write like an expert with a point of view, not a content generator producing generic information
- Use the second person ("you") to speak directly to the reader
- Vary sentence length. Mix short punchy sentences with longer explanatory ones.
- Paragraphs are 2 to 4 sentences. No single-sentence paragraphs. No five-line walls of text.
- **Use bullet points to break up lists, steps, and grouped information.** If a sentence contains three or more items in a row, convert it to a bulleted list. A wall of prose is harder to scan and more likely to be abandoned.
- **Use tables wherever comparison or structured data appears.** If the content involves comparing options, listing attributes, showing pricing tiers, or presenting data with two or more dimensions, a table communicates it better than paragraphs. Tables also improve time-on-page and are frequently pulled into Google featured snippets.
- No em dashes. Replace with a comma, period, or rewrite the sentence.
- No AI-isms. No "leverage", "delve", "seamless", "game-changer", "holistic", "transformative", "innovative solution", "in today's fast-paced world", or any phrase that sounds like it was generated by a chatbot. Refer to the grammar-writing skill for the full list.
- Do not start the introduction with a question. Do not start any sentence with "Additionally" or "Furthermore."
- Write contractions where natural. "You'll" not "you will." "It's" not "it is." This improves readability and sounds less robotic.

**Keyword usage:**
- Primary keyword in the H1, the first 100 words of the introduction, at least one H2, and naturally throughout the body
- Secondary keywords woven in naturally. Never forced. Never repeated awkwardly.
- Do not keyword-stuff. If a keyword appears more than once every 200 words it is probably too much.

**Content type adjustments:**
- **Informational posts:** Lead with education, not promotion. FAQ section is required. Neutral tone. Primary keyword is usually a question or "what is / how to" format. Avoid pushing the client's services too hard — the value comes from being the most helpful answer on the page.
- **Commercial posts:** Comparison tables and pros/cons lists are expected. The reader is evaluating options. Include the client's services as a natural recommendation, not a sales pitch. CTA can be more prominent. Primary keyword usually contains "best", "vs", "top", or "alternatives."
- **Transactional posts:** Short and conversion-focused. Get to the point fast. CTA is prominent and repeated. Body copy is leaner. Primary keyword usually contains "hire", "buy", "get", "services", or a location modifier.

**FAQs:**
- Include a FAQ section for any post that is primarily informational or targets question-based search terms.
- Pull FAQ questions directly from the People Also Ask data in the keyword research (search suggestions tool). These are the exact questions Google is already surfacing for this topic.
- Aim for 3 to 5 FAQ questions. Each answer should be 2 to 4 sentences — long enough to be useful, short enough to be scannable.
- FAQ sections improve the chance of capturing featured snippets and People Also Ask placements in Google.
- For commercial or transactional posts (e.g., "best [product] for X"), FAQs are optional but still worth including if PAA data supports them.
- Format as H3 questions under an H2 "Frequently Asked Questions" heading.

**Links:**
- Minimum 3 external links to credible, relevant sources. Hyperlink anchor text naturally (not "click here").
- Minimum 3 internal links to relevant pages on the client's site. Use placeholder format if exact URLs are not confirmed: [INTERNAL LINK: page name or topic]
- External links should open in a new tab (note this for the CMS editor)

**Structure:**
- Introduction: hook, context, and what the reader will get from reading. No more than 150 words.
- Each H2 section delivers on its heading. Do not pad sections with filler.
- Conclusion: one to two short paragraphs. Summarize the main takeaway and transition directly into the CTA. Do not rehash every section.
- CTA: specific and direct. Matches the conversion goal the client cares about.

**Images:**
- Note image placement opportunities in the draft using [IMAGE: suggested alt text and what the image should show]
- At minimum, suggest a featured image and one in-body image

### Images

Every blog post requires a minimum of 3 images. Source them before writing or note placement for the client to fill in.

**Image 1: Featured image**
The hero image shown at the top of the post and in social previews. Should visually represent the topic. Source from Unsplash (unsplash.com), Adobe Stock, or the client's own photography. Note the suggested subject matter in the draft.

**Image 2: In-body image (mid-article)**
Place roughly halfway through the article, ideally at the start of a new H2 section. Should break up the text and add visual context to the section it sits in.

**Image 3: In-body image or infographic (near end)**
A supporting visual, comparison table screenshot, data visualization, or process diagram relevant to the topic. For how-to or process content, a step-by-step visual works well here.

**For each image in the draft, include a placeholder note:**
```
[IMAGE: Featured image — suggest showing X. Alt text: "primary keyword + descriptive phrase"]
[IMAGE: Mid-article — suggest showing X. Alt text: "secondary keyword + descriptive phrase"]
[IMAGE: End-article — suggest showing X. Alt text: "descriptive phrase"]
```

Alt text rules:
- Describe what is in the image
- Include the primary or a secondary keyword naturally where it fits
- Never stuff keywords into alt text
- Keep it under 125 characters

### Output format

Deliver the final blog post as a styled .docx file using the docx skill. The document should be formatted using the client's brand colors extracted in Step 1a so it is ready to copy and paste directly into WordPress or any CMS with minimal reformatting needed.

**Docx styling requirements:**

Apply the extracted brand colors throughout the document:
- **H1 heading:** Client's primary color, bold, large (28-32pt)
- **H2 headings:** Client's primary color, bold, medium (18-22pt)
- **H3 headings:** Client's secondary color or a darker shade of primary, bold, small (14-16pt)
- **Body text:** Standard dark text (near-black), 11-12pt, readable font matching the client's site (or Arial/Georgia as fallback)
- **Highlight boxes / stat callouts:** Light background tint of the primary color with a left border in the primary color. Use these for key stats, quotes, or important callouts pulled from the research.
- **Tables:** Header row uses the primary color as background with white text. Alternating row shading uses a light tint of the primary color.
- **CTA block at the end:** Shaded box using the secondary color or primary color tint, with the CTA text bolded and centered.
- **Hyperlinks:** Standard blue underline is fine — WordPress will preserve these on paste.

**Document structure (in order):**
1. H1 title
2. Featured image placeholder: `[IMAGE 1: Featured image — suggest showing X. Alt text: "..."]`
3. Introduction
4. Body sections (H2/H3, paragraphs, bullets, tables)
5. Mid-article image placeholder: `[IMAGE 2: suggest showing X. Alt text: "..."]`
6. Remaining body sections
7. End-article image placeholder: `[IMAGE 3: suggest showing X. Alt text: "..."]`
8. FAQ section (if applicable)
9. Conclusion
10. CTA block
11. Meta section (separate page or clearly separated section at the end):
    - Meta title (under 60 characters)
    - Meta description (under 160 characters)
    - URL slug
    - Primary keyword and secondary keywords used
    - External links list with anchor text and URLs
    - Internal links list with anchor text and URLs or placeholders

**WordPress copy-paste note:**
The docx format pastes cleanly into WordPress's classic editor and mostly into the block editor. Heading styles, bold, bullets, and tables transfer. Images need to be uploaded separately using the placeholders as a guide. Hyperlinks transfer intact.

### What to deliver at the end of the article:

```
META
Title tag: [under 60 characters]
Meta description: [under 160 characters]
URL slug: [short, lowercase, hyphenated]

KEYWORDS USED
Primary: [keyword, approximate uses]
Secondary: [keyword, approximate uses]
[Continue for all]

LINKS
External:
- [Anchor text] linked to [URL]

Internal:
- [Anchor text or placeholder] linked to [page]
```

---

## Quality Check Before Delivering

Before handing off the final draft, check every item:

- [ ] No em dashes anywhere in the post
- [ ] No AI-isms (run mentally against the grammar-writing skill list)
- [ ] Primary keyword in H1, first 100 words, and at least one H2
- [ ] Secondary keywords placed naturally throughout
- [ ] 4 to 7 H2 sections (not too many, not too few)
- [ ] H3s only where genuinely needed
- [ ] Paragraphs are 2 to 4 sentences
- [ ] Introduction is under 150 words and does not start with a question
- [ ] At least 3 external links to real, working, non-404 URLs (each one verified by fetching)
- [ ] External links are .gov, .edu, or trusted non-competitor sources only
- [ ] No competitor links anywhere in the post
- [ ] No repeated external domains
- [ ] At least 3 internal links sourced from the client's sitemap.xml — confirmed live pages only, no 404s
- [ ] Content type confirmed and post structure matches (informational = FAQ required, commercial = comparison table, transactional = short and CTA-forward)
- [ ] Conclusion transitions directly into the CTA
- [ ] CTA is specific and matches the client's conversion goal
- [ ] Bullet points used wherever three or more items appear in sequence
- [ ] Tables used wherever comparison, structured data, or multi-attribute content appears
- [ ] FAQ section included for informational posts (3 to 5 questions pulled from PAA data)
- [ ] All 3 image placeholders present with alt text suggestions
- [ ] Meta title under 60 characters and includes primary keyword
- [ ] Meta description under 160 characters and is compelling
- [ ] URL slug is short and keyword-rich
- [ ] Word count is within the target range determined by competitor research
- [ ] Docx uses client brand colors for H1, H2, H3, tables, and CTA block
- [ ] Highlight boxes used for key stats or callouts
- [ ] Image placeholders clearly labeled with suggested subject and alt text
- [ ] Meta section included at the end of the document (meta title, description, slug, links)
- [ ] Image placements noted

---

## Common Mistakes to Avoid

These are the patterns that produce low-quality output. Avoid all of them.

| Mistake | Why It Fails |
|---|---|
| Too many H2s (15-20 for a 1,200 word post) | Makes the post feel like a listicle with no depth. Google rewards depth. |
| Short paragraphs throughout (1-2 sentences) | Feels thin and generated. Does not demonstrate expertise. |
| No external links | Reduces credibility and misses a key on-page SEO signal |
| Generic opener ("In today's digital landscape...") | Immediately signals AI content. Loses the reader in the first sentence. |
| Keyword in every other sentence | Reads as spam, hurts rankings |
| CTA buried or missing | Wastes the traffic the post generates |
| Internal links to the homepage only | Misses the SEO opportunity of linking to specific relevant pages |
| Writing from memory without research | Produces thin, generic content that will not outrank competitors who did the work |
| Including unverified external or internal links | 404s in the published post signal low quality to Google and break trust with readers |
| No bullet points or tables | Walls of text increase bounce rate. Structured content is easier to scan and more likely to earn featured snippets. |
| No FAQ section on informational posts | Misses People Also Ask placements and featured snippet opportunities |
| No images or missing alt text | Images break up text, improve engagement, and are an additional keyword placement opportunity |
| Linking to competitors | Sends the reader to a competing business and signals poor editorial judgment |
| Repeating external links | Using the same domain twice dilutes the trust signal and looks lazy |
| Using web search instead of sitemap for internal links | The sitemap returns every indexed page. Web search returns a partial, ranking-biased view. Always use the sitemap. |
| Ignoring content type | An informational post written like a sales page will not rank. A transactional post written like an essay will not convert. Match the structure to the intent. |
| Generic or unstyled docx output | A blog that matches the client's brand colors looks professional and pastes cleanly into WordPress. An unstyled document requires reformatting before publishing. |
| No meta section at end of document | The editor needs meta title, description, slug, and links in one place to publish correctly. Missing this creates extra back-and-forth. |