---
name: video-content-production
description: >
  Use this skill whenever the user needs to produce content around a recorded video episode. Triggers include: "write the YouTube description for", "generate social posts for this episode", "create content for this video", "write the title and description", "repurpose this transcript", "social media posts for this episode", or any request to turn a video transcript into YouTube metadata, social media posts, show notes, or other content assets. Always ask which show it is before starting.
---

# Video Content Production

From Ruskin Consulting / The Boost Network.

This skill takes a raw video transcript and produces every content asset needed to publish and promote the episode across YouTube, X, Facebook, and LinkedIn.

No em dashes. No AI-isms. Write like a person who watched the whole thing and found it genuinely interesting.

---

## Step 1: Identify the Show

Always ask which show this episode belongs to before doing anything else. Each show has a distinct tone, audience, and format.

**The three shows:**

| Show | Format | Tone | Audience | Host(s) | Sponsor |
|---|---|---|---|---|---|
| The Social Ledger | News-cast style, topical, no guest | Fast, sharp, opinionated | Crypto and DeFi natives, finance-curious investors | Leon Hitchens and JRB (Jesus Rafael Burgoa) | MintLocke |
| The Marketing Boost | Long-form interview, 20-45 min | Conversational, practical, founder-focused | Founders, marketers, entrepreneurs | Leon Hitchens | Ruskin Consulting |
| Beyond Giving | Long-form interview, 20-45 min | Warm, mission-driven, storytelling | Nonprofit leaders, donors, community builders | Zac Brown | Givekit |

If the user has not stated the show, ask before proceeding.

Also ask for the guest name (for The Marketing Boost and Beyond Giving) and the episode topic or focus if it is not clear from the transcript.

---

## Step 2: Read the Transcript

Before writing anything, read the full transcript carefully. Pull out:

- The 3-5 most interesting moments, stories, or insights
- Any strong quotes worth using verbatim in social posts
- The guest's main accomplishment, mission, or company being promoted
- The central theme or tension of the episode
- Any specific numbers, stats, or facts mentioned
- The timestamp of each topic shift (for chapters)

---

## Step 3: Generate All Content Assets

Produce all assets in one complete output, organized by section. Use the deliverable structure below.

---

## Output Format

Every completed video content package is delivered as a single .docx file using the docx skill. The document should be clean and easy to hand off to whoever handles scheduling and uploading.

**Document structure:**
- Show name and episode title as the H1
- Each section (YouTube Metadata, Chapters, Thumbnail Concept, Show Notes, Social Posts, Email Blurb, Key Quotes) as H2 headings
- Platform names within the social posts section as H3 headings
- All checklist items and post sequences clearly labeled
- Publishing schedule in a table at the top of the social section
- Font: Arial, 11pt body, black text throughout

The .docx file should be named: `[ShowName] - [GuestNameOrEpisodeTopic] - Content Package.docx`

---

## Deliverable Structure

### 1. YouTube Title (3 options)

Write three title options. Titles should:
- Be under 70 characters
- Lead with the most compelling hook, not the guest name
- Make a non-subscriber want to click
- Not use clickbait that misleads -- the title must reflect what the episode actually delivers
- Avoid starting with the show name (YouTube already shows the channel name)

**The Social Ledger titles** should feel like a financial news headline. Sharp, opinionated, timely.
**The Marketing Boost titles** should lead with the marketing or business insight, not just the guest.
**Beyond Giving titles** should lead with the mission or the story, not just the nonprofit name.

---

### 2. YouTube Description

**Structure for The Marketing Boost and Beyond Giving (interview format):**

```
[2-3 sentence hook. What is this episode about and why does it matter to the audience?
Do not start with "In this episode." Lead with the idea, the story, or the problem.]

[1 paragraph about the guest: who they are, what they built or lead, why they're worth listening to.]

[Bullet list of what the audience will learn or hear in this episode. 3-5 bullets.]

[Guest's links: website, social, product -- ask the user for these if not in the transcript]

[Sponsor line -- see show-specific defaults below]

[Show subscribe/follow line]

[Standard channel description -- see show-specific defaults below]

[Timestamps / Chapters -- generated from transcript in Step 4]

[Hashtags -- see show-specific defaults below]
```

**Structure for The Social Ledger (news format):**

```
[1-2 sentence summary of what topics are covered this episode]

[Bullet list of topics covered with brief descriptions. 3-6 bullets.]

[Subscribe/follow line]

[Standard channel description]

[Timestamps / Chapters]

[Hashtags]
```

**Show-specific defaults:**

*The Social Ledger:*
- Sponsor line: "This episode is brought to you by MintLocke -- automate your crypto strategy. Learn more at mintlocke.com"
- Subscribe line: "Subscribe for weekly crypto and market commentary from The Boost Network."
- Hashtags: #SocialLedger #Crypto #DeFi #Bitcoin #Markets #Web3 #BoostNetwork #MintLocke

*The Marketing Boost:*
- Sponsor line: "This episode is presented by Ruskin Consulting -- the digital marketing agency behind real business growth. Learn more at ruskinconsulting.com"
- Subscribe line: "Subscribe to The Marketing Boost for founder stories and marketing insights that actually move the needle."
- Hashtags: #MarketingBoost #Marketing #Entrepreneurship #Founder #BusinessGrowth #BoostNetwork #RuskinConsulting

*Beyond Giving:*
- Sponsor line: "This episode is sponsored by Givekit -- the giving platform built for nonprofits that want to grow. Learn more at givekit.com"
- Subscribe line: "Subscribe to Beyond Giving for stories from the people building a better world."
- Hashtags: #BeyondGiving #Nonprofit #SocialImpact #Philanthropy #MissionDriven #BoostNetwork #Givekit

---

### 3. YouTube Chapters

Generate chapters from the transcript. Format:

```
00:00 Intro
02:14 [Topic from transcript]
08:45 [Next topic]
...
```

Rules:
- Every chapter title should tell the viewer what they will learn or hear in that section, not just label it (e.g., "How Leon built his first $1M client" not "Business growth")
- Minimum 5 chapters for a full episode
- First chapter is always "Intro" at 00:00
- Last chapter can be "Final Thoughts" or "Where to Find [Guest]" if applicable
- If the transcript has no timestamps, note the approximate topic breaks and flag that timestamps need to be added manually

---

### 4. Thumbnail Concept

Generate one thumbnail concept. Include:
- **Main visual:** What should the main image show? (Guest headshot + host, a key visual metaphor, a bold stat)
- **Headline text:** The 3-7 word text overlay that goes on the thumbnail
- **Color/energy direction:** Describe the feel (e.g., dark and bold for crypto content, warm and human for Beyond Giving, clean and professional for marketing content)

Note that the final design will be done in the Boost Network template. This is a creative brief for the designer, not a final product.

---

### 5. Show Notes (Blog-Style)

Write a 400-600 word show notes post. This is the written companion to the episode -- it lives on the website or in a newsletter. Structure:

```
[Episode title as H1]

[2-3 paragraph summary of the episode. Highlight the most interesting moments and insights.
Write this like a journalist recapping a conversation, not a press release about a guest.]

[Key Takeaways section -- 3-5 bullet points of the most actionable or memorable insights]

[Notable Quote -- one strong verbatim quote from the transcript, formatted as a blockquote]

[Where to Find [Guest] -- links to their website, social, product]

[Listen/Watch section with YouTube embed placeholder]
```

No AI-isms. No em dashes. Write like a human who found the conversation genuinely worth recapping.

---

### 6. Social Media Posts

Generate platform-specific posts for every platform. Each post should feel native to that platform -- not just the same copy resized.

**Upload note:** Raw video uploads go to YouTube, X, and Facebook. LinkedIn gets a link post (not a native upload). Factor this into how each post is written.

---

#### YouTube Community Post

A short teaser posted to the YouTube Community tab to drive views on launch day.

- 2-4 sentences
- Casual, like you're talking to subscribers directly
- End with a question to drive comments
- No hashtags needed here

---

#### X (Twitter) -- 3 posts

**Post 1: Episode launch tweet**
- Lead with the most interesting insight or hook from the episode
- Tag the guest's X handle if known
- Include the YouTube link
- 1-2 relevant hashtags max
- Under 280 characters

**Post 2: Quote tweet**
- Pull a strong verbatim quote from the transcript
- Format as a quote (use quotation marks)
- Add 1 line of context beneath it
- Include the YouTube link

**Post 3: Thread opener (optional but recommended for Social Ledger)**
- Write the first tweet of a short thread (3-5 tweets)
- Each tweet in the thread covers one key point from the episode
- Last tweet links to the full video
- Label each tweet: Tweet 1/4, Tweet 2/4, etc.

---

#### Facebook -- 2 posts

**Post 1: Video launch post (native upload)**
- 3-5 sentences introducing the episode
- More conversational than YouTube, less formal than LinkedIn
- Ask a question at the end to drive engagement
- 3-5 relevant hashtags at the bottom

**Post 2: Quote graphic post**
- Short intro (1 sentence)
- The quote formatted clearly (use quotation marks)
- Credit the guest
- Note: "[Pair with quote graphic]" as a reminder for the designer
- 2-3 hashtags

---

#### LinkedIn -- 2 posts

**Post 1: Episode link post (link only, no native video)**
- LinkedIn rewards text-first posts so write 4-6 lines of substantive insight before the link
- Lead with a business or professional insight from the episode, not just "new episode out"
- Break into short paragraphs (LinkedIn line breaks matter)
- Add the YouTube or episode link at the bottom
- 3-5 relevant hashtags

**Post 2: Carousel or quote post teaser**
- Write copy for a text-based post pulling out 3 lessons or quotes from the episode
- Format each point on its own line with a number or label
- Note: "[Can be paired with carousel graphic -- 3 slides]" for the designer
- Close with the link and 2-3 hashtags

---

#### Instagram (if applicable)

- Caption: 3-5 sentences with the hook up top (Instagram cuts off after 2 lines so make the first line count)
- 10-15 hashtags at the bottom or in the first comment
- Note: "[Pair with clip or audiogram]" for repurposing as a Reel

---

### 7. Email Newsletter Blurb

Write a 3-4 sentence blurb for inclusion in The Boost Network email newsletter. Should:
- Summarize what the episode is about in a way that makes a busy person want to click
- Include the guest name and show name
- End with a direct link placeholder: [LINK]

---

### 8. Key Quotes for Graphics

Pull 3-5 of the strongest verbatim quotes from the transcript that would work well as standalone quote graphics. Format:

```
Quote 1:
"[Exact quote from transcript]"
-- [Speaker name], [Their title or company]

Quote 2:
...
```

These go to the designer for social graphics and thumbnail overlays.

---

## Quality Checklist

Before delivering, verify:

- [ ] Show is correctly identified and tone matches
- [ ] No em dashes anywhere in any asset
- [ ] No AI-isms (leverage, delve, seamless, transformative, etc.) -- refer to grammar-writing skill
- [ ] YouTube title is under 70 characters
- [ ] YouTube description leads with a hook, not "In this episode"
- [ ] Chapters are properly formatted with timestamps (or flagged as needing manual timestamps)
- [ ] Thumbnail concept includes visual, text, and direction
- [ ] Show notes are 400-600 words and written like journalism, not a press release
- [ ] All 6 social posts are written and platform-specific
- [ ] X posts are under 280 characters each
- [ ] LinkedIn post is text-first, link at the bottom
- [ ] Facebook posts include hashtags
- [ ] Guest links are included or flagged as needing input
- [ ] Key quotes are pulled verbatim from the transcript
- [ ] Deliverable header includes show, guest handles, publish times, and clip timestamp
- [ ] Pinned comment written for first 30 minutes after publish
- [ ] First 2 lines of YouTube description are the hook, not the guest bio
- [ ] End screen and card timestamps noted in the deliverable
- [ ] Keyword-optimized title variant included if topic has search potential
- [ ] Short-form clip identified with timestamp and caption hook
- [ ] All social posts include guest handle placeholders
- [ ] Three-post sequence written for each platform (launch, day 3, day 7)
- [ ] Posting times noted per platform

---

## Show Context Reference

**The Social Ledger** -- Hosted by Leon Hitchens and JRB. Sponsored by MintLocke. Covers crypto markets, DeFi news, and financial commentary. News-cast style, no guest, fast-paced. Audience skews crypto-native and finance-curious. Posts should feel opinionated and sharp. Sponsor mention: "Brought to you by MintLocke -- automate your crypto strategy."

**The Marketing Boost** -- Hosted by Leon Hitchens. Sponsored by Ruskin Consulting. Long-form interviews with founders, marketers, and entrepreneurs about building businesses and marketing what they built. The audience wants practical insights, not inspiration fluff. Sponsor mention: "Presented by Ruskin Consulting -- the digital marketing agency behind real business growth."

**Beyond Giving** -- Hosted by Zac Brown. Sponsored by Givekit. Long-form interviews with nonprofit leaders, philanthropists, and mission-driven founders. Audience includes donors, community builders, and people working in or around the nonprofit world. Tone is warmer and more story-driven than the other two shows. Sponsor mention: "Sponsored by Givekit -- the giving platform built for nonprofits that want to grow."

---

## YouTube Best Practices

### First 24-48 Hours Are Everything

YouTube's algorithm judges a video primarily in the first 24-48 hours. Watch time, click-through rate, and comment velocity in that window determine whether the algorithm pushes the video further. Every publishing decision should be optimized for that window.

**Publish at the right time:**
- The Social Ledger: Recorded Saturday, target publish by Tuesday. Aim for Tuesday 8-10am CT to catch crypto and finance audiences early in the week.
- The Marketing Boost: Publishes Wednesday. Aim for Wednesday 9-11am CT.
- Beyond Giving: Publishes Thursday. Aim for Thursday 10am-12pm CT.

**Pin a comment immediately after publishing.** Within the first 30 minutes of going live, post a pinned comment from the channel asking the episode's central question. This seeds engagement before the algorithm decides the video's fate.

Example for The Marketing Boost: "What's the biggest marketing mistake you made in your first year of business? [Guest] talked about theirs at 14:22 - drop yours below."

Example for Beyond Giving: "What does 'impact' mean to you? [Guest] gave an answer at 18:30 that reframed how we think about it."

Example for The Social Ledger: "Do you think [topic covered] is being overblown or underreported? Drop your take."

---

### The Two-Line Rule

YouTube shows only the first 125 characters of a description before truncating with "Show More." Those two lines are the only thing most viewers read. They must be the hook, not the guest introduction, show name, or episode number.

**Wrong:**
"Welcome to The Marketing Boost. Today we sit down with [Guest Name], founder of [Company]..."

**Right:**
"Most founders waste their first $10k on ads that don't convert. [Guest] built to $2M without spending a dollar on paid traffic."

The full guest bio, links, and hashtags go after the chapters, not at the top.

---

### End Screens and Cards

Note these in the deliverable so whoever uploads the video adds them in YouTube Studio.

**End screen (last 20 seconds of video):**
- Subscribe button
- "Best for viewer" video recommendation or a manually selected related episode
- Channel link if applicable

**Cards (mid-video):**
- Add a card at the most relevant moment pointing to a related episode
- For The Marketing Boost and Beyond Giving, a good card placement is at the first major topic break (usually 8-12 minutes in)
- Cards should not be placed in the first 2 minutes or final 2 minutes

Include a note in the deliverable: **[ADD: End screen at [timestamp] and card at [timestamp] pointing to [related episode]]**

---

### Title and Description Keyword Optimization

For evergreen topics (marketing strategies, fundraising, nonprofit operations, crypto concepts, DeFi protocols) the title and description should include terms people actually search, not just what sounds compelling.

Before finalizing the title, consider what someone would type into YouTube to find this episode. A title like "How [Guest] Built a $5M Nonprofit From Scratch" may be compelling but if nobody searches that exact angle, it will only get algorithm-pushed views. Adding a searchable term like "nonprofit fundraising strategy" somewhere in the description captures search traffic too.

When the topic has clear search volume potential, flag it in the deliverable and suggest a search-optimized title variant alongside the hook-driven options.

---

## Social Media Best Practices

### Clip Strategy (Short-Form Video)

For every long-form episode, identify the best 60-90 second clip from the transcript for short-form repurposing. This single clip becomes:
- A YouTube Short
- An Instagram Reel
- A TikTok (if the channel is active there)
- A native video on X and Facebook

**How to identify the best clip:**
Look for a moment in the transcript where the guest or host says something that is self-contained, surprising, or immediately useful without needing context. The best clips usually have one of these qualities:
- A counterintuitive statement ("Most people think X but actually Y")
- A short story with a clear point
- A specific number or result ("We went from 0 to 500 donors in 90 days")
- A strong opinion stated simply

Pull the clip as a quote block in the deliverable and note the timestamp:

```
RECOMMENDED SHORT-FORM CLIP
Timestamp: [00:00 - 00:00]
Quote: "[First line of clip]..."
Why: [One sentence on why this works as a standalone clip]
Hook for caption: [Suggested first line for the Reel/Short caption]
```

---

### Guest Handle Collection

Before writing any social post, collect the guest's handles on every platform they are active on. Tagging the guest is the single most effective way to expand reach on every post. When a guest shares or re-shares the episode, their entire audience sees it.

Ask for these upfront if they are not in the transcript or the user's notes:
- X (Twitter) handle
- LinkedIn profile URL
- Instagram handle
- Facebook page (if they have one)

Every platform-specific post should have a placeholder: **[@GuestHandle on [platform]]** if the handle is unknown, so whoever schedules the posts fills it in before publishing.

---

### Publishing Sequence (3-Post Launch Strategy)

One post on launch day wastes most of the content's value. Use a three-post sequence to extend the episode's lifespan across the first week.

**Day 1 (Launch Day):** Full episode announcement post. Link to the video. This is the primary launch post on every platform.

**Day 3:** Highlight post. Pull the best moment, quote, or insight from the episode. No link required on LinkedIn and Instagram -- the algorithm suppresses link posts. Frame it as a standalone insight, then mention the full episode is linked in bio or comments.

**Day 7:** Repurposing post. Use the short-form clip, a quote graphic, or a carousel pulling 3 lessons from the episode. This is the furthest from the launch so it should be the most self-contained -- someone who never heard of the episode should find it valuable on its own.

Generate all three posts for each platform in the deliverable, labeled clearly:

```
PLATFORM: LinkedIn
Post 1 (Launch Day): ...
Post 2 (Day 3 - Highlight): ...
Post 3 (Day 7 - Repurpose): ...
```

---

### Optimal Posting Times by Platform

Use these as defaults. Adjust based on actual analytics if the channel has data.

| Platform | Social Ledger | The Marketing Boost | Beyond Giving |
|---|---|---|---|
| YouTube | Tuesday by 10am CT | Wednesday 9-11am CT | Thursday 10am-12pm CT |
| LinkedIn | Tuesday 8-10am CT | Wednesday 8-10am CT | Thursday 9-11am CT |
| X (Twitter) | Tuesday 8-10am CT | Wednesday 8-10am CT | Thursday 8-10am CT |
| Facebook | Tuesday 10am-12pm CT | Wednesday 10am-12pm CT | Thursday 10am-12pm CT |
| Instagram | Tuesday 10am-12pm CT | Wednesday 10am-12pm CT | Thursday 10am-12pm CT |

Note the recommended publish time for each platform in the deliverable header so whoever schedules knows when to post.

---

### Updated Deliverable Header

Add this block at the top of every completed deliverable:

```
VIDEO CONTENT PACKAGE
Show: [Show name]
Episode: [Title or guest name]
Guest handles: X: [@] | LinkedIn: [URL] | Instagram: [@]
Guest website: [URL]
Recommended YouTube publish: [Day and time]
Recommended social schedule:
  - LinkedIn: [Date and time]
  - X: [Date and time]
  - Facebook: [Date and time]
  - Instagram: [Date and time]
Short-form clip: [Timestamp] - [Brief description]
```
