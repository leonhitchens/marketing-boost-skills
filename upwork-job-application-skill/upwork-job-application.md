---
name: upwork-job-application
description: Use this skill any time Joshua Ruskin or Leon Hitchens is deciding whether to apply to an Upwork job, drafting an Upwork proposal or cover letter, or vetting an Upwork posting against Ruskin Consulting's wheelhouse. Triggers include "should I apply to this Upwork job", "write an Upwork proposal", "draft an Upwork cover letter", "is this Upwork job a fit", "bid on this Upwork posting", "Upwork job for Joshua", "Upwork job for Leon", or any pasted Upwork URL or job description that looks like a freelance brief. Use this skill even if the user just pastes a job posting without explicit instructions, since the implied request is almost always "screen this and write me a proposal."
---

# Upwork Job Application

This skill helps Joshua Ruskin and Leon Hitchens of Ruskin Consulting screen Upwork jobs and write proposals that actually get replies.

There are three jobs to do, in order:

1. Screen the job. Is it a fit for Ruskin Consulting? Which of the two should bid?
2. Draft the cover letter in the right length band and the right voice.
3. Hand back 1 to 3 short clarifying questions the bidder can send with the proposal or in the first reply.

Read the reference files when you need the detail. The top of this file is the playbook. The references are the long version.

## Inputs you can expect

The user will give you one of:

- A pasted Upwork job description
- An Upwork job URL (fetch it with the web fetch tool, then proceed)
- A loose description of the job in their own words

If you only have a vague description, ask one tight question to nail down the work type before going further. Do not invent details.

## Step 1: Screen the job

Run the job through the wheelhouse filter and the client filter. Detailed checklist lives in `references/job-screening.md`. The short version:

**Wheelhouse fit.** The job must be a service Ruskin Consulting actually delivers. If it is ecommerce, the budget floor is $100+ and the work must be PPC, SEO, or web (not store-building, product photography, fulfillment, etc.). If the post says "no agencies," skip unless the pay is unusually high. Same with "consultation only."

**Client filter.** Prefer payment verified clients with at least a 30% hire rate. Prefer US, UK, Canada, Australia, New Zealand, Singapore, Portugal. Other geographies are not disqualifying but the rate they will pay usually is.

**Counter-intuitive client read.** Whales (over $500k lifetime spend, 4.8+ stars) reply at roughly half the rate of the middle market. The sweet spot is $1k to $50k lifetime spend with 4.0 to 4.7 star feedback. Note this in your fit verdict if you can see it in the posting.

Output a verdict in this exact shape:

```
FIT: yes / no / maybe
BIDDER: Joshua / Leon / either (ask)
WHY: one or two sentences
```

If the verdict is "no," stop and explain. Do not write a cover letter for a job that should be skipped.

## Step 2: Route to Joshua or Leon

Detailed profiles live in `references/joshua-profile.md` and `references/leon-profile.md`. The fast routing rules:

- **Heavy Google Ads (Search, Display, Shopping, YouTube), pure PPC, paid media strategy**: Joshua.
- **SEO, technical SEO, AI search visibility, content/blog work, website builds, WordPress (Elementor / Kadence), Rank Math, landing pages, conversion copy**: Leon.
- **LinkedIn Ads, Meta Ads, paid social outside Google**: Leon (with Joshua as backup if it is heavy budget management).
- **GA4, reporting, analytics setup**: either, default to Leon for SEO contexts and Joshua for PPC contexts.

If the job clearly fits both (e.g., "we need a marketing partner across PPC and SEO"), the verdict should say BIDDER: either (ask) and you should ask the user which name to write the proposal under before drafting.

Hard nos:

- Joshua does not market ecommerce, Figma work, or full-time roles.
- Leon does not do Divi or Avada websites.
- Neither does pure copy/text/email work as a primary offer.

## Step 3: Draft the cover letter

This is where most agencies lose. The middle of the bell curve, 100 to 149 words, is the worst performing length in a 134,000 proposal dataset (6.7% reply rate). Reply rate is a U-curve. Both tails win.

**Pick a length band on purpose, never in the middle.**

| Band | Word count | When to use |
|---|---|---|
| Short tail | Under 50 words | Default for Web/design/quick-turnaround jobs. One credible sentence plus an opening question and a CTA. |
| Long tail | 200 to 400+ words | Use when the job clearly wants a real pitch: strategy roles, monthly retainers, "tell us about your approach," requests for deliverables or samples. Include a brief plan, two or three specifics, and a sign-off. |

Never land in 100 to 149 words. If a draft comes in at 130, cut to 49 or expand past 200.

**Format rules (apply to every cover letter):**

- Salutation: `Howdy,` (with the comma). Not "Hi," not "Hello," not the wave emoji.
- No em dashes. Anywhere. Use commas, periods, or new lines.
- No "I am a [role] with X years of experience" opener. Eyes skip it.
- Open with a question that proves you read the post. Specific, not generic. Example: "Is the Stripe migration in your last post the same scope as this one, or has it grown?" Not "Do you need a developer?"
- Optional closer to try: "Any questions you may have?" This is the highest-lift closer in the dataset. It probably has confounds, but it is worth testing.
- Empathetic tone. Less lecturing. We are joining a conversation, not delivering a TED talk.
- Do not parrot the client's exact post wording back at them. Experienced clients flag that.
- Do not write "I want to absorb your vision," "delve into," "leverage," "unlock," "robust," "comprehensive," "seamlessly," "streamline," "actionable insights," "holistic approach," "game-changer," "cutting-edge," "in today's digital age."
- Short to medium sentences. Fragments are fine.
- Sign off with the bidder's name on its own line.

**Structure of the short version (under 50 words):**

1. Question opener tied to a specific detail in the post.
2. One sentence of credibility, with one concrete proof point (a metric, a relevant client type, or a certification).
3. CTA. "Want me to send a 10 minute Loom on this?" works. "Worth a quick call?" works.

**Structure of the long version (200 to 400+ words):**

1. Question opener tied to a specific detail in the post.
2. One short paragraph naming what you read in the brief and the read you have on it. Show you understood the problem.
3. A short plan, 3 to 5 lines or a tight numbered list, on how you would approach the work in the first 30 days.
4. One paragraph of credibility with two or three specifics (relevant client, metric, cert, or named platform you have used).
5. One paragraph on logistics: how you work, what you would need from them, response time, rate posture if relevant.
6. Optional closer: "Any questions you may have?"
7. Sign off with name.

**Voice. Joshua vs. Leon.**

- Joshua leans PPC, performance, CPA and ROAS. Use the framing he uses: "revenue is vanity and profit is sanity." Lean into measurement.
- Leon leans SEO, web, and brand. Use the framing of long-term compounding traffic, technical health, and content that ranks. He covers some LinkedIn / Meta / paid social too.

Worked examples in both voices and at all three length bands live in `assets/examples.md`. Read them before drafting if you have not seen them before in this conversation.

## Step 4: Suggest clarifying questions

Right after the cover letter, give the bidder 1 to 3 short questions they can send the client. These should be questions that:

- Reveal scope creep risk
- Reveal timeline or urgency
- Reveal who the real decision maker is
- Reveal what success looks like (so you can price properly)

These are not for the cover letter body. They are for the chat the cover letter is trying to start.

## Output format

Always return in this order:

```
SCREEN
FIT: yes / no / maybe
BIDDER: Joshua / Leon / either (ask)
WHY: one or two sentences

COVER LETTER (target X words)
[the cover letter, in the bidder's voice, with Howdy salutation, no em dashes, signed off with the bidder's name]

CLARIFYING QUESTIONS
1. ...
2. ...
3. ...
```

If the verdict is "no," stop after SCREEN.

## Reference files

- `references/joshua-profile.md`: what Joshua does and does not do, certs, voice
- `references/leon-profile.md`: what Leon does and does not do, certs, voice
- `references/cover-letter-playbook.md`: the data behind the U-curve, opener/closer regression, what kills replies
- `references/job-screening.md`: the full filter checklist
- `assets/examples.md`: worked example cover letters at each length band, in both voices
