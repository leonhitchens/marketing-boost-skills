---
name: keyword-match-types
description: >
  Use this skill whenever the user needs to understand, apply, or make decisions about Google Ads keyword match types or negative keyword match types. Triggers include: "what match type should I use", "broad vs exact", "phrase match", "negative keyword match type", "why is my ad showing for wrong searches", "keyword match types explained", "should I use broad match", "exact match not working", "close variants", or any question about how keywords trigger ads in Google Ads. 
---

# Keyword and Negative Keyword Match Types

From Ruskin Consulting Training Module 7.

---

## How It All Fits Together

Search Term → Keyword → Ad

A keyword is what bridges a user's search to your ad. When someone types something into Google, Google looks at the keywords in your account and decides whether the search term is a close enough match to enter your ad into the auction. The match type you assign to a keyword controls how loosely or strictly that matching happens.

---

## The 3 Keyword Match Types

| Match Type | Symbol | Reach | Control |
|---|---|---|---|
| Broad Match | keyword | Highest | Lowest |
| Phrase Match | "keyword" | Medium | Medium |
| Exact Match | [keyword] | Lowest | Highest |

---

### Broad Match

Your ad can show for searches that **relate to the meaning** of your keyword. Google uses signals like the user's search history, landing page content, other keywords in the ad group, and intent to decide what qualifies. The search does not need to contain your keyword at all.

**Syntax:** just the keyword, no symbols

**Example keyword:** red shoes
- Will match: "women's red sandals", "discount red boots", "buy red heels"
- May also match: "red shoes worn by actor", "red shoe store near me"

**Important 2025 update:** Broad match became the default match type for new Search campaigns using Smart Bidding in mid-2024. If you create a new campaign with a Smart Bidding strategy and do not manually set match types, all your keywords will be broad match. Watch for this every time you set up or inherit a campaign.

**When Ruskin uses broad match:**
- The account is generating at least 30 conversions per month (Google needs conversion data to bid intelligently)
- There are robust negative keyword lists already built out
- The campaign has plateaued on phrase and exact and you need to scale
- There is enough budget to absorb wasted spend while gathering data
- Smart Bidding is active (broad match without Smart Bidding is almost always a waste)

**For most small and medium business clients, broad match should not be the starting point.** The risk of burning budget on irrelevant searches is too high without strong negative keyword coverage and conversion data.

---

### Phrase Match

Your ad can show for searches that **include the meaning of your keyword**. The user does not need to type your exact phrase, but the core meaning must be present. Phrase match expanded significantly in 2021 and now matches on intent and synonyms, not just word order.

**Syntax:** "keyword in quotes"

**Example keyword:** "pet supplies"
- Will match: "discount pet supplies", "supplies for pets", "online pet supply store"
- Will not match: "pet training", "best pets", "art supplies"

**Example keyword:** "car engine"
- Will match: "car motor", "1995 mazda rx7 engine", "toyota engine"
- Will not match: "motorcycle engine", "generator engine", "boat motor"

Phrase match is a solid default for most campaigns. It gives you meaningful reach while keeping the matching reasonably relevant to what you are selling.

---

### Exact Match

Your ad can show for searches that **have the same meaning or intent** as your keyword. This is the most controlled match type but it is no longer truly "exact." Since 2021, exact match includes close variants and same-intent searches, not just the identical phrase.

**Syntax:** [keyword in square brackets]

**Example keyword:** [golf shoes]
- Will match: "golf shoes", "golf shoe", "golph shoes" (misspelling), "shoes for golf"
- Will not match: "cheap golf shoes", "buy golfing shoes", "golf shoes sale"

**Example keyword:** [black cocktail dress]
- Will match: "black cocktail dress", "black cocktail dresses", "cocktail dress black"
- Will not match: "cocktail dress", "black dress", "expensive black cocktail dress"

Exact match is best for high-intent, proven keywords where you want maximum control over what triggers your ads and are willing to accept lower volume in exchange for higher relevance.

---

## Close Variants

All three match types allow close variants. This means your keywords can match searches that are similar but not identical. Close variants include:

- Misspellings: "plannign" matches "planning"
- Singular/plural: "shoe" matches "shoes"
- Stemming: "floor" matches "flooring"
- Abbreviations: "ATM" matches "automatic teller machine"
- Accents: "á" matches "a"
- Same meaning: "car engine" matches "automotive engine"

For exact match specifically, close variants also include:
- Reordered words with the same meaning: [mens shoes] matches "shoes mens"
- Added or removed function words: [shoes for men] matches "men shoes" (function word "for" removed)

---

## The 3 Negative Keyword Match Types

Negative keywords prevent your ads from showing when a search contains a term you want to block. Negative keywords are more powerful than regular keywords. If you have a keyword "red bag" but add "bag" as a negative keyword, your ad will not show for any search containing "bag," including the keyword you are trying to target. Be precise.

| Match Type | Symbol | What It Blocks |
|---|---|---|
| Negative Broad Match | keyword | Any search containing all your negative keyword terms, in any order |
| Negative Phrase Match | "keyword" | Searches containing your exact keyword terms in the same order |
| Negative Exact Match | [keyword] | Only the exact search query, no extra words |

---

### Negative Broad Match

Blocks any search that contains all the words in your negative keyword, regardless of order.

| Negative Keyword | Blocked | Not Blocked |
|---|---|---|
| golf shoes | "golf shoes", "golf red shoes", "golf shoes for sale" | "golf shoe", "golfing shoes" |
| black dress | "black cocktail dress", "cocktail dress black", "black sun dress" | "cocktail dress", "red dress" |

---

### Negative Phrase Match

Blocks searches that contain your exact keyword terms in the same order. Additional words around the phrase are fine, it still gets blocked. But if word order changes or characters are added to a word, it may not block.

| Negative Keyword | Blocked | Not Blocked |
|---|---|---|
| "golf shoes" | "golf shoes", "buy golf shoes online", "golf shoes for sale" | "golf shoe", "golf red shoes", "buy golfing shoes" |
| "black dress" | "black dress cocktail", "black dress for prom" | "dress black", "black cocktail dress" |

---

### Negative Exact Match

Blocks only the precise search query with no extra words. If someone searches with anything added before or after, the ad may still show.

| Negative Keyword | Blocked | Not Blocked |
|---|---|---|
| [golf shoes] | "golf shoes" | "golf shoes for sale", "buy golf shoes", "golf shoe" |
| [black dress] | "black dress" | "black dress for sale", "dress black" |

---

## Important: Negative Keywords and Close Variants

Unlike regular keywords, **negative keywords do not match to close variants.** If you add a negative keyword, it only blocks that specific spelling and form. You must manually add variations you want to block.

**Exception as of June 2024:** Negative keywords now block misspellings. So if you add "youtube" as a negative, it will also block "yuotube" and similar typos. This is new behavior and is a meaningful improvement for controlling irrelevant traffic.

| Negative Keyword | Search Term | Blocked? |
|---|---|---|
| dental clinic | dentist clinic | No |
| car engine | car engines | No |
| lipsticks | lipstick | No |
| floor | flooring | No |
| youtube | yuotube | Yes (misspelling, blocked as of June 2024) |

This means if you want to block plural forms, synonyms, or close variants of a negative keyword, you need to add them separately.

---

## Match Type Strategy for Ruskin Clients

Most clients Ruskin manages are small to medium businesses with limited budgets. The default approach:

1. **Start with exact match** on your most important, highest-intent keywords. This keeps spend controlled while you gather conversion data.
2. **Use phrase match** for broader service/category terms where you want some reach but still need relevance.
3. **Avoid broad match** until the account has at least 30 conversions per month, a solid negative keyword list, and Smart Bidding is confirmed to be working.
4. **Check campaign-level broad match setting** on every account you touch. If the "broad match setting" is enabled at the campaign level, all keywords in that campaign are treated as broad regardless of what match type you assigned. This is a common trap in newly created Smart Bidding campaigns.
5. **Layer in negatives aggressively** regardless of match type. The search terms report is your audit tool. Review it regularly.

---

## Quick Reference

| Situation | Use This |
|---|---|
| New campaign, limited budget | Exact match to start |
| Scaling a performing campaign | Add phrase match on proven terms |
| High conversion volume, Smart Bidding active | Test broad match with careful negative coverage |
| Blocking a competitor name | Negative broad match |
| Blocking a specific phrase while keeping individual words usable | Negative phrase match |
| Blocking only one precise search query | Negative exact match |
| Blocking a misspelling in negatives | Handled automatically as of June 2024 |
| Blocking plural/synonym in negatives | Must add manually, no auto-expansion |
