---
name: search-terms
description: >
  Use this skill whenever the user needs to evaluate, categorize, or act on Google Ads search terms. Triggers include: "review these search terms", "are these search terms good or bad?", "should I add or block this keyword?", "what do I do with this search term?", "add negative keywords", "clean up search terms", "search term analysis", "keyword decisions", or any time a list of search terms needs to be reviewed and actioned. Also use when the user is deciding whether to add a keyword, add a negative keyword, move a search term to another ad group, or do nothing. This skill applies to any Google Ads account, not just Ruskin Consulting clients.
---

# Search Terms Skill

This skill is built on the search term evaluation standards developed by Ruskin Consulting in Training Modules 5 and 8. The framework applies to any Google Ads account. Search terms must be done flawlessly every single time.

---

## Core Concept

Google Ads is fundamentally about buying search terms. A search term is a word or group of words a person types into Google. Every time someone searches, Google runs an auction and shows ads. Your job is to decide which search terms should trigger your ads and which ones should not.

The only thing that matters to business owners is getting more customers (conversions) at a lower cost per conversion. Every search term decision feeds directly into that goal.

---

## Good vs. Bad Search Terms

**A good search term** shows high intent to buy and become a paying customer.
- "buy jeans online"
- "dentist in santa rosa"
- "store that sells treadmills"

**A bad search term** shows little or no intent to buy, or is simply irrelevant to the business.
- "when were jeans invented"
- "dentist in new york" (wrong location)
- "nordictrack treadmill 1750 reviews" (researching a competitor's product)

---

## The Sales Funnel

Every search term sits somewhere in the sales funnel. Buy search terms at the bottom of the funnel. These indicate the user is ready to buy now.

| Funnel Stage | Description | Example (Treadmill Store) |
|---|---|---|
| N/A | Unrelated to the business or impossible to convert | "best gyms near me" |
| Lead Generation (Awareness) | Becoming aware of the product/service, very low purchase intent | "how to get fit at home" |
| Lead Nurture (Interest) | Interested but needs convincing, looking for results not products | "exercise equipment for homes" |
| Lead Nurture (Evaluation) | Comparing options, likely to buy but not yet decided | "best exercise equipment for homes" |
| Sales (Purchase) | Ready to buy the specific product/service | "buy stationary bike online" |

Target Lead Nurture (Evaluation) and Sales (Purchase) search terms. Be cautious with Awareness and Interest terms as they rarely convert and waste budget.

### Sales Funnel Examples by Business Type

**Nike (athletic wear)**
- N/A: "what Nike shoes did Kobe wear in the NBA"
- Awareness: "types of tennis shoes"
- Interest/Evaluation: "reviews for nike air zoom tennis shoes"
- Purchase: "buy Nike Air Zoom tennis shoes online"

**Dr. Manhattan DDS (dental clinic, Manhattan NY)**
- Awareness: "causes of tooth sensitivity"
- Consideration: "is teeth whitening worth it"
- Evaluation: "best dental clinics in manhattan"
- Purchase: "dr. manhattan appointment for tooth extraction"

**Mecca Beauty (salon, San Antonio TX)**
- Awareness: "types of hair coloring services"
- Consideration: "hair salons in san antonio"
- Evaluation: "best hair color salons open on Sunday"
- Purchase: "mecca beauty hair color appointment"

---

## The Decision Making Framework

When you see a search term, run it through this process in order:

### Step 1: Think Like the Customer
Put yourself in the shoes of the person who typed that search term. If you typed that into Google, would you be the exact customer the business wants? Use the client's website to verify what they actually offer. The website answers everything.

### Step 2: Test It on Google
If unsure about a search term, Google it. Look for:
- Do any ads show up? No ads = nobody wants to advertise on it = probably a bad search term.
- Are the ads that show up relevant to the business? If ads from unrelated industries appear, it is a bad match.
- If the search term includes a location, check that location on Google Maps. If it is far from the client's service area, it is a bad search term.

### Step 3: Make One of Four Decisions

---

## The 4 Decisions

### Decision 1: Add as Negative Keyword (Bad Search Term)

Block it. Find the smallest word or phrase that makes the search term bad, and negative keyword that component, not the entire search term.

**Match type guidance for negatives:**
- Use **broad match negative** when a single word is always bad (e.g., "sexual", "free", a competitor's name)
- Use **phrase match negative** when a specific phrase is bad but individual words in it are fine (e.g., "luxury dentistry", "insurance plans", "hail damage" at campaign level)
- Use **exact match negative** when only that precise search should be blocked and broader blocking is risky (e.g., [roofing companies hiring near me], [tombstone], [the floor store])

**Examples:**

| Search Term | Problem | What to Block | Match Type |
|---|---|---|---|
| "dentists near 12204" | Zip code 12204 is Albany NY, 148 miles from Manhattan | 12204 | Broad |
| "dentist laurie fleisher manhattan ny" | Searching for a different dentist not on the team | fleisher | Broad |
| "luxury dentistry california" | "Luxury Dentistry" is a competitor clinic | luxury dentistry | Phrase |
| "sexual massage parlor near me" | Unrelated service the business does not offer | sexual | Broad |
| "roofing companies hiring near me" | Ambiguous, could mean job seekers | roofing companies hiring near me | Exact |
| "tombstone" (for CNC parts company) | Too broad, could mean gravestones or the Arizona city | tombstone | Exact |
| "the floor store" | A competitor business with that exact name | the floor store | Exact |

Add negatives to the **Shared Negatives List** unless the block only applies to a specific campaign or ad group, in which case add it at the appropriate level.

---

### Decision 2: Move (Good Search Term, Wrong Location)

If a search term is good but it matched to the wrong campaign or ad group, move it by adding a negative keyword at the ad group or campaign level to force it to the correct location.

**Examples:**

| Search Term | Issue | Fix |
|---|---|---|
| "pediatric dentist near me" appearing in General Dentist ad group | Should be in Pediatric Dentist ad group | Add "pediatric" as negative keyword at the General Dentist ad group level |
| "acrylic nails near me" appearing in #General Nails ad group | Should be in Acrylic ad group | Add "acrylic" as negative keyword at the #General Nails ad group level |
| "repair service for hail damage on roof" appearing in Repair campaign | Should be in Extreme Weather campaign | Add "hail damage" as phrase match negative at the Repair campaign level |

---

### Decision 3: Do Nothing (Good Search Term, Already a Keyword)

If the search term is good, is in the right ad group, and is already added as a keyword or is a duplicate, do nothing. Adding it again just makes the account harder to manage.

Also do nothing in these situations:
- The search term is a misspelling of the keyword and the letters are adjacent on the keyboard (e.g., "azure" vs "axure" — Z and X are next to each other, likely a typo, so do not block)
- The search term is a general product type inquiry that is relevant but low volume — keep it to avoid accidentally blocking a good future term
- You cannot confirm whether the business carries that specific product/variant

**Examples:**

| Search Term | Keyword | Reason to Do Nothing |
|---|---|---|
| "azure cloud" | "axure cloud" | Close keyboard proximity, likely a typo, competitor campaign already handles it |
| "saltillo tile shop" | "ceramic tile shop" | General tile type, may or may not be in inventory, do not risk blocking |
| "machining angle plate" | "angle plate" | Low volume but highly relevant, do not risk blocking |

---

### Decision 4: Add as Exact Match Keyword (Good, New Search Term)

If the search term is good and is not already in the account as a keyword, add it as an exact match keyword. Exact match gives you the most control and allows you to bid higher specifically on that term to get more customers.

**Examples:**

| Search Term | Reason to Add |
|---|---|
| "toyota of gallatin" | Brand search, highly relevant, high traffic and conversions |
| "jim johnson nissan" | Competitor search, opportunity to capture customers comparing options |
| "motorworks engine center" | Drives conversions, confirmed by conversion data |
| "emergency dental services manhattan ny" | Specific service + location, high purchase intent |
| "dental cleaning and whitening" | More specific than existing keyword, worth capturing separately |

---

## Summary Decision Table

When you receive a search term, ask these questions in order:

1. Is it relevant to the business and the website? If no, negative keyword the bad component.
2. Is it good but in the wrong ad group or campaign? If yes, move it with an ad group or campaign level negative.
3. Is it good and already a keyword or duplicate? If yes, do nothing.
4. Is it good and new? If yes, add as exact match keyword.

| Situation | Decision |
|---|---|
| Bad search term | Negative keyword the smallest bad component |
| Good, wrong location | Move with ad group/campaign level negative |
| Good, already a keyword | Do nothing |
| Good, new search term | Add as exact match keyword |

---

## Quick Checklist

Before finalizing any search term decision:

- [ ] Did you look at the client's website to confirm relevance?
- [ ] Did you Google the search term to check what ads appear?
- [ ] If a location is involved, did you verify it is within the service area?
- [ ] Are you blocking the smallest possible bad component, not the entire search term?
- [ ] Is the negative match type appropriate (broad, phrase, or exact)?
- [ ] If moving, are you adding the negative at the right level (ad group vs. campaign)?
- [ ] If doing nothing, have you confirmed it is already in the account?
- [ ] If adding, are you using exact match?
