---
name: google-ads-ad-writing
description: >
  Use this skill whenever the user needs to write, review, critique, or improve Google Ads copy - including responsive search ads (RSAs), headlines, descriptions, or full ad sets. Triggers include: "write ads for", "write Google Ads", "create ad copy", "write headlines and descriptions", "review my ads", "are these ads good?", "write RSA copy", "ad copy for [client/campaign/keyword]", "write ads for this search term", or any request to generate or audit ad copy for a Google Ads campaign. Also use when the user provides a list of keywords or search terms and needs ads written for them. Use this skill even if the request is phrased casually, like "can you write some ads for this" or "draft some headlines".
---

# Google Ads Ad Writing Skill

This skill encodes Ruskin Consulting's internal standards for writing high-performing Google Search Ads. Follow these rules precisely every time ad copy is written or reviewed.

---

## Ad Structure (Responsive Search Ads)

Every RSA requires exactly **15 headlines** (30 characters max each) and **4 descriptions** (90 characters max each). Google uses machine learning to test combinations, so more variety across headlines and descriptions leads to better performance. Always write the full set - never fewer.

| Field | Quantity | Character Limit |
|---|---|---|
| Headlines | 15 | 30 each |
| Descriptions | 4 | 90 each |

Always display character counts next to each field when outputting ad copy.

---

## The 3 Components of a Good Ad

Every ad must answer these three questions in order:

### 1. Match the Search Term (Headline 1)
The user needs to know immediately that you have what they are searching for. Headline 1 should mirror or closely reflect the search term, plus optionally layer in a small qualifier ("Best", "Top-Rated", "#1", "Local").

- Search term: "dentist in manhattan" → Headline 1: `#1 Dentist in Manhattan` (25 chars)
- Search term: "home water damage" → Headline 1: `Do You Have Home Water Damage?` (30 chars)
- Search term: "wedding announcement cards" → Headline 1: `Wedding Announcement Cards` (26 chars)

### 2. Unique Value Propositions (Headlines 2–3 + Descriptions)
After matching the search term, the ad must answer: "Why should I choose you over everyone else?"

**Good UVPs are specific and business-specific.** Ask: could McDonald's, Apple, or any other company in a different industry say the same thing? If yes, it is NOT a unique value proposition.

Good examples:
- "40% Off Sitewide"
- "24/7 Emergency Response Line"
- "Family Owned and Operated for 25 Years"
- "Fastest Emergency Plumbing Response in San Antonio"
- "Hand Picked. Free Same-Day Delivery."
- "Author of 'Tooth Colored Restoratives'"

Bad examples (reject these):
- "Quality and Professional Services for All Your Needs"
- "Best of the Best"
- "We Care About Our Customers"
- "Innovative Solutions for Everyone"
- "Leading Provider in Our Industry"
- "Best Prices in Town"

**Never invent value propositions.** Only use what is confirmed to be true about the business or what appears on their website. False advertising wastes budget and violates policy.

### 3. Call to Action (End of Description)
The final sentence of the last description tells the user what to do next. Match the CTA to the business's primary conversion action.

Good CTAs:
- "Call Today for a Free Consultation!"
- "Order Online Today!"
- "Schedule an Appointment Today!"
- "Get a Free Quote - Call Now!"
- "Request a Demo Today!"

The CTA should end with a single exclamation mark (`!`). Only one `!` per description.

---

## The Modus Ponens Framework

Use this logical structure to ensure every ad flows correctly:

- **p** (Headline 1) = Status quo / what the user is searching for
- **p → q** (Headline 2, Description) = Why you are the best choice (UVPs)
- **∴ q** (End of Description) = What the user should do (CTA)

---

## Ad Writing Do's

1. **Title Case:** Capitalize the first letter of all major words and all words 4+ letters long. Example: `Award Winning Dentist in Manhattan`
2. **Use numbers and symbols appropriately:** `#1`, `?` in headlines, `!` at the end of descriptions only
3. **Maximize character count:** Use as much of the 30/90 character limits as possible. Don't leave empty space.
4. **Use natural American English:** The copy should sound native, not translated or robotic.
5. **Only advertise what is on the website:** Do not invent discounts, claims, or offers.

---

## Ad Writing Don'ts

These will cause ad disapprovals and reflect poorly on the account manager:

- ALL CAPS text (e.g., `FREE CONSULTATION NOW`)
- RaNdOm CaPiTaLiZaTiOn
- More than one `!` in a single description
- Exclamation marks in any headline
- Repeated symbols: `()()()` or `!!!`
- Inappropriate abbreviations: `@` instead of "at"
- Extra spaces or irregular spacing
- Phone numbers in ad copy (use call extensions instead)
- Multiple domains in the same ad group

---

## Output Format

Always output the full RSA. Never write a partial set. Format every ad like this:

```
Search Term: [search term]

HEADLINES
Headline 1:  [copy] (X chars)
Headline 2:  [copy] (X chars)
Headline 3:  [copy] (X chars)
Headline 4:  [copy] (X chars)
Headline 5:  [copy] (X chars)
Headline 6:  [copy] (X chars)
Headline 7:  [copy] (X chars)
Headline 8:  [copy] (X chars)
Headline 9:  [copy] (X chars)
Headline 10: [copy] (X chars)
Headline 11: [copy] (X chars)
Headline 12: [copy] (X chars)
Headline 13: [copy] (X chars)
Headline 14: [copy] (X chars)
Headline 15: [copy] (X chars)

DESCRIPTIONS
Description 1: [copy] (X chars)
Description 2: [copy] (X chars)
Description 3: [copy] (X chars)
Description 4: [copy] (X chars)

[Optional: Brief note explaining UVP and CTA choices if the user would benefit]
```

**Headline variety guidelines:**
- Headlines 1-3: Match the search term directly, with slight variations
- Headlines 4-8: Lead with the strongest unique value propositions
- Headlines 9-12: Secondary UVPs, location signals, trust indicators, offers
- Headlines 13-15: CTAs formatted for headline length (e.g., "Call Us Today", "Get a Free Quote", "Schedule Online Now")
- Vary phrasing across all 15 so Google has meaningful combinations to test

---

## Review / Critique Mode

When asked to review or critique existing ad copy, evaluate against each of the following and flag issues:

1. Does Headline 1 match the search term?
2. Are the UVPs specific and unique, or generic/interchangeable?
3. Is there a clear CTA at the end of the description?
4. Are character limits respected?
5. Are any disapproval triggers present (ALL CAPS, multiple `!`, etc.)?
6. Are value propositions verifiable (not invented)?

Output a structured review: what works, what should change, and a revised version.

---

## Quick Reference Examples

**Example 1**
Search term: `dentist for whitening`
- Headline 1: `#1 Teeth Whitening Dentist` (26 chars)
- Headline 2: `Local Office in Manhattan` (25 chars)
- Description: `Award Winning Dentist and Author of "Tooth Colored Restoratives". Schedule an Appointment.` (90 chars)

**Example 2**
Search term: `home water damage`
- Headline 1: `Do You Have Home Water Damage?` (30 chars)
- Headline 2: `24/7 Emergency Response Line` (28 chars)
- Description: `Family Owned and Operated for 25 Years. We Specialize in Home Water Damage. Call Now.` (85 chars)

**Example 3**
Search term: `wedding announcement cards`
- Headline 1: `Wedding Announcement Cards` (26 chars)
- Headline 2: `40% Off Sitewide` (16 chars)
- Description: `Customizable Wedding Announcements. Free and Fast Delivery. Order Online Today!` (79 chars)

**Example 4**
Search term: `red roses delivered`
- Headline 1: `Want Roses Delivered Now?` (25 chars)
- Headline 2: `Free Delivery To Your Door` (26 chars)
- Description: `Beautiful Hand Picked Roses. Free Same-Day Delivery. Call Now to Make an Order!` (79 chars)
