---
name: account-organization
description: >
  Use this skill whenever the user needs to structure, organize, or audit a Google Ads account. Triggers include: "how should I organize this account", "set up campaigns and ad groups", "account structure", "campaign structure", "ad group structure", "keywords competing against each other", "duplicate keywords", "negative keywords for account organization", "how do I stop ad groups from competing", "build out a new account", or any request to plan or review the campaign and ad group layout of a Google Ads account.
---

# Account Organization

From Ruskin Consulting Training Module 13.

---

## The Goal

Organize a Google Ads account so that:
- It is easy to navigate and explain to a client
- Every search term goes to one and only one ad group
- No campaigns or ad groups compete against each other
- Ads shown to a user are as specific and relevant as possible

---

## Campaign vs. Ad Group Settings

Understanding what each level controls determines how you structure the account.

**Campaign level controls:**
- Budget
- Location targeting
- Ad schedule
- Language
- Networks (Search vs. Display)
- Bidding strategy

**Ad group level controls:**
- Keywords
- Ads
- Default max CPC
- Landing pages

If you need different budgets, locations, languages, or networks, those require separate campaigns. Ad groups within the same campaign share all campaign-level settings.

---

## The Noun/Adjective Strategy

The core account structure method at Ruskin. Every account is built this way unless the client's website structure dictates otherwise.

- **Campaigns = Nouns** (the main thing being advertised)
- **Ad Groups = Adjectives** (specific ways to describe or find that noun)

**Service business example (Dr. Manhattan DDS):**

| Campaign (Noun) | Ad Groups (Adjectives) |
|---|---|
| Dentist | Best Dentist, Cosmetic Dentist, Dentist Near Me, Emergency Dentist, Family Dentist, Local Dentist, Restorative Dentist, Manhattan Dentist |
| Implants | Affordable Dental Implants, Best Dental Implants, Dental Implant Specialist, Dental Implant Surgery, Endosteal Implants |
| Cleaning | Best Dental Cleaning, Calculus Cleaning, Deep Dental Cleaning, Oral Cleaning, Teeth Cleaning |

**Product business example (The Flooring Company):**

| Campaign (Noun) | Ad Groups (Adjectives) |
|---|---|
| Hardwood Floor | Hardwood Floor Installation, Hardwood Floor Refinish, Hardwood Floor Replacement |

Each ad group should map to a specific landing page on the client's website. If the website is well organized, use the website structure as a guide for how to build the account.

---

## Adding Keywords

Once the structure is set, add keywords to each ad group. Use a mix of phrase match and exact match per ad group. Some keywords may seem to belong in multiple ad groups. That is normal at this stage. The next step fixes it.

**Example (Dentist campaign):**

| Ad Group | Keywords |
|---|---|
| Best Dentist | "best dentist", [best dentist in manhattan] |
| Cosmetic Dentist | "cosmetic dentist", [affordable cosmetic dentist], [best cosmetic dentist], [cosmetic dentist near me] |
| Dentist Near Me | "dentist near me", [cosmetic dentist near me] |
| Emergency Dentist | "emergency dentist", [emergency need dentist now] |
| Manhattan Dentist | "manhattan dentist", [manhattan dentist office], [best dentist in manhattan] |

Notice that [best dentist in manhattan] appears in both Best Dentist and Manhattan Dentist. That is a duplicate and must be resolved.

---

## Duplicate Keywords

Never allow the same keyword to exist in more than one ad group. Duplicates cause three problems:

1. Your own keywords compete against each other, which drives up your cost
2. Performance data gets split across multiple ad groups, making optimization harder
3. The wrong ad may show for a search term instead of the most relevant one

---

## Resolving Duplicates: Priority System

To eliminate duplicates, assign a priority to each campaign and each ad group. More specific = higher priority. More generic = lower priority.

### Step 1: Set Campaign Priorities

Go from most specific to most generic. The most specific campaign gets Priority 1.

**Example (Dr. Manhattan):**

| Campaign | Priority |
|---|---|
| Implants | #1 |
| Cleaning | #2 |
| Dentist | #3 |

Implants is the most specific service. Dentist is the most generic.

### Step 2: Set Ad Group Priorities Within Each Campaign

Do the same thing inside each campaign.

**Example (Cleaning campaign):**

| Ad Group | Priority |
|---|---|
| Calculus Cleaning | #1 |
| Deep Dental Cleaning | #2 |
| Oral Cleaning | #3 |
| Teeth Cleaning | #4 |
| Best Dental Cleaning | #5 |

Calculus is the most specific. Best is the most generic.

---

## Adding Negative Keywords to Enforce Priority

Once priorities are set, use negative keywords to force each search term into the right campaign and ad group. The rule is:

**A campaign or ad group gets the keywords from all higher-priority campaigns/ad groups added as negatives.**

### Campaign Level Negatives

| Campaign | Priority | Negative Keywords Added |
|---|---|---|
| Implants | #1 | none |
| Cleaning | #2 | implants |
| Dentist | #3 | implants, cleaning |

This ensures a search containing "implants" never lands in the Cleaning or Dentist campaign.

### Ad Group Level Negatives

| Ad Group | Priority | Negative Keywords Added |
|---|---|---|
| Calculus Cleaning | #1 | none |
| Deep Dental Cleaning | #2 | calculus |
| Oral Cleaning | #3 | calculus, deep |
| Teeth Cleaning | #4 | calculus, deep, oral |
| Best Dental Cleaning | #5 | calculus, deep, oral, teeth |

---

## Full Example: Public Claims Adjuster Account

This shows a complete account with both campaign and ad group level negatives applied.

| Campaign | Ad Group | Ad Group Neg Keywords | Campaign Neg Keywords |
|---|---|---|---|
| Branding | ACMS | none | none |
| Catastrophe/Disaster | Flood and Water | none | "acms", "american claims management services" |
| | Fire and Smoke | flood, water | |
| | Hail Damage | flood, water, fire, smoke | |
| | Vandalism | flood, water, fire, smoke, hail | |
| | Catastrophe/Disaster | flood, water, fire, smoke, hail, vandalism | |
| Adjuster | Claims Management | none | "acms", "american claims management services", flood, water, fire, smoke, hail, vandalism, catastrophe, disaster |
| | Public Adjuster | "claims management" | |
| | Insurance Adjuster | "claims management", "public" | |
| | Commercial | "claims management", "public", "insurance" | |
| | Home/Residential | "claims management", "public", "insurance", "commercial" | |

---

## Step-by-Step Setup Checklist

Follow this order every time you build or reorganize an account:

- [ ] Map the client's website and identify landing pages
- [ ] Build campaigns as nouns based on main products or services
- [ ] Build ad groups as adjectives within each campaign
- [ ] Assign each ad group a specific landing page
- [ ] Add keywords to each ad group using phrase and exact match
- [ ] Identify duplicate keywords across ad groups
- [ ] Assign priority to campaigns (most specific = #1)
- [ ] Assign priority to ad groups within each campaign (most specific = #1)
- [ ] Delete duplicate keywords from lower-priority ad groups
- [ ] Add negative keywords at the campaign level to block higher-priority campaign terms
- [ ] Add negative keywords at the ad group level to block higher-priority ad group terms
- [ ] Verify every search term can only match one and only one ad group
