---
name: account-checkin-ash
description: >
  Use this skill when onboarding a new Google Ads client or performing a thorough top-to-bottom account review. Triggers include: "initial account check-in", "perform ash", "run ash", "do ash", "onboard this account", "new client setup", "audit this account from scratch", "first time reviewing this account", "full account audit", or any situation where a new account is being taken over or has not been reviewed in a long time (roughly a year or more). For recurring weekly check-ins use the account-checkin-weekly skill instead.
---

# Initial Account Check-In (ASH)

From Ruskin Consulting Training Module 24.

The initial check-in follows the ASH framework: Account Settings and History. Like a phoenix rising from the ashes, the goal is to fully understand what existed before and build something solid from it.

**After completing ASH, the account is entirely yours. You are responsible for its success or failure.**

---

## The 5 Things You Must Know Intimately

Before you touch anything in the account, you are trying to learn these five things about the client:

1. **Why** - Why are they paying for Google Ads? What is the business goal?
2. **Message** - What is the client trying to communicate to users?
3. **Measurements** - What does success look like? What conversions matter?
4. **Users** - Who are their customers? What are they searching for?
5. **Budget** - What is the monthly spend? How is it allocated?

Every step in ASH is feeding toward understanding these five things.

---

## The 10 Steps of ASH

### Step 1: Documentation and Change History

**What to do:**
Use `Basecamp Railway:search_projects` to find the client's Basecamp project. Pull all previous notes, proposals, and monthly reports. Use `Google Drive:search_files` with a query like `fullText contains '[client name]'` to find any stored documents in Drive.

Then log into Google Ads and review the Change History for the last 90 days. Change History shows every modification made to the account: who did it, when, where, and what changed. This is the account's story. Read it carefully.

**What you are looking for:**
- Why the client signed up and what their original goals were
- What strategies were tried previously and how they performed
- Any red flags in recent changes (budget cuts, paused campaigns, conversion tracking issues)
- The client's monthly budget

Write down every question you have after this step. You will answer them in Steps 4 and 5.

---

### Step 2: The Client's Website

**What to do:**
Go to every page of the client's website. Know every product, service, and location they offer. This directly informs which landing pages you send users to for each ad group.

Check:
- Page speed using Google PageSpeed Insights
- On-page SEO using SEOquake or a similar plugin
- Whether all necessary landing pages exist for the campaigns you plan to run
- Whether contact forms, phone numbers, and emails work correctly
- Whether there are clear calls to action on each page

**If the website has problems, you are responsible for flagging them.** Common issues and what to do:

| Problem | Action |
|---|---|
| Poor design | Show examples of better sites or provide your own mockup |
| Slow load speed | Use PageSpeed Insights to identify fixes and share with the client |
| Weak SEO / thin content | Tell the client which keywords each page should be targeting |
| Missing landing pages | Tell the client exactly which pages need to be created before campaigns launch |
| Weak CTAs | Tell the client what calls to action you want and where to place them |

You are responsible for the success of the landing pages unless the client refuses to act on your recommendations. Document every recommendation you make.

---

### Step 3: Google Analytics

**What to do:**
Use `MCP MASTER SERVER:ga4_overview` to pull site traffic data. Set `propertyId` to the client's GA4 property ID. Use a 90-day window for the initial review.

Use `MCP MASTER SERVER:ga4_sources` to see traffic by channel. Look at how much comes from paid search vs. organic vs. direct.

**What to verify:**
- Demographics and data collection are enabled
- The right conversion events are created (phone calls, form fills, purchases, downloads, subscriptions)
- GA4 is linked to Google Ads
- Conversion data is flowing correctly

Conversions and cost-per-conversion are the only two metrics that matter to business owners. If conversions are not set up correctly, every optimization decision after this will be based on bad data. Do not skip this step.

---

### Step 4 and 5: Talk to the Account Manager, Project Manager, and Previous Specialist

**What to do:**
Speak with the Account Manager and Project Manager about the client's objectives and account history. If accessible, speak with the previous account specialist.

Ask every question you need to manage the account well. Do not assume someone will volunteer information. It is your job to get what you need.

Bring the questions you wrote down in Step 1. Cover:
- What were the client's original goals?
- What has worked and what has not?
- Are there any client sensitivities or things to avoid?
- What is the client expecting in terms of deliverables?
- Are there any pending changes to the website, products, or services?

Quality people value their time. Be prepared, be thorough, and do not ask the same question twice.

---

### Step 6: Link All Accounts and Confirm Conversions

**What to verify in Google Ads Data Manager:**
- Google Analytics is linked
- Google Search Console is linked
- Google Merchant Center is linked (if running Shopping campaigns)
- YouTube is linked (if running video ads)

**Conversion setup checklist:**
- All conversion goals from Analytics are imported into Google Ads
- A "Call from Ads" conversion exists with these exact settings:
  - Conversion name: "Call from Ads" (capital A)
  - Count: One
  - Call length: 30 seconds
  - Attribution model: Position-based
- The Call from Ads conversion is connected to the call extension (not the default Google-created one)

You need two sets of conversions active: everything from Analytics, and Call from Ads. What gets measured gets managed.

---

### Step 7: Account Organization

Review or build the account structure using the noun/adjective framework. Campaigns are nouns (main services or products). Ad groups are adjectives (specific ways users search for those services).

Refer to the account-organization skill for the full framework including priority-based negative keyword setup.

A well-organized account saves time on every future check-in and makes bid adjustments far more effective.

---

### Step 8: Keywords and Negative Keywords

Review all keywords across every ad group, campaign, and the shared negative keyword library.

For each keyword ask:
- Is this the right keyword for the business?
- Is it in the correct match type?
- Is it in the correct ad group?

For negative keywords, ask these questions before accepting any existing list:
- Could any of these negatives block important search terms?
- Are the negative keyword lists too large to manage effectively?
- Could negatives be grouped or simplified?
- Are negatives placed at the right level (account, campaign, or ad group)?
- Are there duplicates that can be removed?

Bad negative keywords are more dangerous than bad keywords. A negative added for one bad search term can silently block dozens of good ones. Triple-check every negative.

---

### Step 9: Campaign Settings

Go through every campaign and verify these settings:

| Setting | Correct Value |
|---|---|
| Network | Search only OR Display only, never both |
| Campaign goal | None selected |
| Search partners | Disabled (unless budget is hard to spend) |
| Display expansion | Disabled |
| Bid strategy | Manual CPC with Enhanced CPC unchecked |
| Ad rotation | Do not optimize: Rotate ads indefinitely |
| Location options (targeted) | People in your targeted locations |
| Location options (excluded) | People in your excluded locations |
| Automatically created assets | Off |
| Language | Correct language(s) for the client's market |

---

### Step 10: Account, Campaign, and Ad Group Checklists

Run through each checklist before signing off on the initial check-in.

**Account Checklist**

Conversions:
- [ ] Appropriate conversions created and imported to Google Ads
- [ ] Conversions are being tracked and recording data
- [ ] All conversion actions set to count "One"
- [ ] "Call from Ads" conversion exists and is connected to call extension

Negative Keywords:
- [ ] Negative keyword lists exist
- [ ] Generic negative lists are added (irrelevant industries, job seekers, etc.)
- [ ] Negative keyword lists are applied to all appropriate campaigns

Linked Accounts:
- [ ] Google Analytics linked
- [ ] Google Search Console linked
- [ ] Google Merchant Center linked (if applicable)
- [ ] YouTube linked (if applicable)

**Campaign Checklist**

Budget:
- [ ] All campaign budgets are set
- [ ] Total daily budgets equal the desired daily spend
- [ ] Monthly budget math checks out (daily budget x 30.4 = monthly)

Conversions:
- [ ] Campaign has conversions assigned
- [ ] Conversions match the campaign's goals
- [ ] Conversion tracking is active

Locations:
- [ ] Correct locations are targeted
- [ ] Unwanted locations are excluded
- [ ] Location targeting options set correctly (people in, not interested in)

Bid Strategy:
- [ ] Manual CPC with Enhanced CPC disabled
- [ ] No automated bidding unless intentional and appropriate

Ad Settings:
- [ ] Ad rotation set to "Do not optimize: Rotate ads indefinitely"
- [ ] Ad schedule set to desired times
- [ ] Automatically created assets turned off

Network:
- [ ] Search Partners disabled
- [ ] Display Expansion disabled

**Ad Group Checklist**

Ads:
- [ ] All ads are eligible and running
- [ ] No typos in headlines or descriptions
- [ ] All ads in the same ad group share the same landing page
- [ ] Ads are going to the correct landing pages

Landing Pages:
- [ ] Conversions tracking correctly on each landing page
- [ ] Forms are working
- [ ] Phone numbers and emails are clickable

Keywords:
- [ ] Keywords are relevant to the ad group theme
- [ ] All keywords are approved and eligible
- [ ] No broad match keywords (pause any that exist)
- [ ] Keyword bids are set at reasonable levels

---

## Summary: What You Should Know After ASH

Once all 10 steps are complete, you should be able to answer all of the following without looking anything up:

- Why is this client running Google Ads?
- What does the client consider a conversion?
- What is the monthly budget and how is it split across campaigns?
- Who are the client's customers and what are they searching for?
- What has been tried before and what were the results?
- Is conversion tracking set up correctly?
- Is the account organized in a way that supports optimization?
- Are all campaign settings aligned with the client's goals?

If you cannot answer all of these, go back and complete the steps you skipped.
