---
title: Connect Instagram Insights to Claude with Coupler.io
slug: connect-instagram-insights-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-insights-to-claude.md
source: Instagram Insights
destination: Claude
meta_title: Connect Instagram Insights to Claude with Coupler.io
meta_description: "Connect Profile: daily reach and Story: navigation by action type (last 24 hours) so Claude can answer while those stories are still fresh."
---

![Instagram Insights](https://static.coupler.io/importers/instagram-ads.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Instagram Insights to Claude with Coupler.io

Instagram's professional dashboard keeps a profile's overview, its posts, and its stories in separate places, and several story figures only cover the last 24 hours. Coupler.io schedules the report type you choose for the profiles you choose, so the same question can be asked again after the next refresh. Claude is where you ask it: which city a reached audience sits in, which contact button collected link taps, how story navigation broke down. Demographic metrics stay tied to age, gender, city, or country. Promoted posts can list ad ids on their own rows. One carousel report type is deprecated; the other fifteen categories are the ones to build on.

## How to export Instagram Insights data to Claude

Sixteen categories cover profiles, posts, and stories. They include a 30-day follower breakdown, three story reports limited to the last 24 hours, reach and follow-type cuts, link taps, and Post insights: carousel (deprecated).

### Step 1. Basic settings

- **Profiles** — the Instagram profiles in this flow. Claude answers for those profiles.
- **Report type** — one category per flow. The full sixteen are listed below.

### Step 2. Report period

- **Start date** — where Instagram profile history should open. Use a relative value such as *days ago*, *this month*, *last month*, *this year*, or *last year*. `{{365daysago}}` is the macro for a trailing year of profile history.
- **End date** — the closing bound, using those same relative choices so a scheduled run does not stay stuck on an old end.
- **Timeframe** — the window control for report types that use it, alongside the start and end dates.
- **Published after** — the earliest publish time for items you want included. The relative picker works here too.
- **Published before** — the latest publish time. Pair it with Published after when the question is a campaign's posts, not the whole profile history.
- **Split by** — Totals only, or Daily. Totals only collapses the window; Daily keeps a row per day.

### Step 3. Metrics and dimensions

- **Metrics** — Engaged audience demographics and Reached audience demographics, on the report types that ask for them.
- **Dimension** — Age, Gender, City, or Country. This is the cut Claude will be able to talk about for those demographic metrics.

### Step 4. Advanced settings

- **Show promoted posts ad ids in separate rows** — turn this on when a post report should list each promoted ad id on its own row.
- **Data behavior** — for a profile, post, or story report, choose Latest data or Track changes over time. Latest data is the current Instagram rows. Track changes over time keeps the path those rows took.

### Step 5. Blend and transform data

- **Column management** — hide Instagram Insights columns that do not belong in the question, rename what remains, and keep the profile identifier easy to find.
- **Join** — Coupler.io's Join lines Profile: daily reach up with Post: performance totals before Claude is in the conversation. Hold the profile flow apart from the post flow and let the question you put to Claude make the connection.
- **Append** — Coupler.io's Append stacks the Profiles you selected when they share one report type, so the combination exists before you ask Claude which profile stands out.
- **Aggregate** — Coupler.io's Aggregate rolls a Daily Split by into a single total before Claude is asked for that total.
- **Custom SQL** — a query covers combinations, such as a demographic Dimension beside a reach report, that the other transformations cannot make. Ask Claude about the query result.

### Step 6. Claude destination

This step has no destination form. Its product name is **Setup Claude integration**, and you finish it on two tabs.

- **Chat and Cowork** — This tab starts by registering a Claude account for the person who will ask about these profiles. Next, open the Coupler.io connector for Instagram Insights and click Connect (https://l.rw.rw/couplerio-claude-connector) before any story report is scheduled. You must be an admin if the workspace is on a Team or Enterprise plan. Return to the Connectors menu after the profile list is saved, click Connect again there, and log in to Coupler.io before any story question.
- **Claude Code** — Start a new session for these Instagram profiles rather than reusing an old one. Paste this command, restart the session, complete the browser sign-in when it opens, and click Authorize.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Story categories that only cover the last 24 hours benefit from a short cadence: every 15 minutes, or hourly. Daily, weekly, and monthly remain available for profile reports that can wait. That run refreshes the dataset Claude answers from, which is what a story question later the same day is reading.

### Bonus: or just ask the AI Agent to build it for you

Building the flow can start from one sentence. The Coupler.io AI Agent is in the Coupler.io app, in the right sidebar. Claude is the destination you ask later; ChatGPT and Cursor are not part of building the flow.

> Load Profile: followers demography insights with Dimension set to City, plus Story: performance totals (last 24 hours), and send the result to Claude.

Three steps remain manual:

1. Connect Instagram Insights. You still sign in to the profiles.
2. Choose the **Profiles** that belong in the flow.
3. Connect Claude for those profiles from the Chat and Cowork connector, or through Claude Code authorization.

Profiles and the Claude connection stay in your hands.

## What data can you export from Instagram Insights to Claude with Coupler.io?

Instagram Insights lists sixteen categories. A single flow carries one of them. Coupler.io's Join can stitch a profile category to a post or story category before Claude sees the combination.

- **Post: performance totals** — ask Claude how posts performed inside the publish window you set with Published after and Published before.
- **Profile: account overview** — the profile-level starting point for the Profiles you selected. Ask what the overview contains before you open a narrower report.
- **Profile: followers daily breakdown (last 30 days)** — a follower series whose name already limits it to the last 30 days. Ask how the daily line moved inside that window.
- **Profile: followers demography insights** — ask who the followers are. Pair Metrics (Engaged audience demographics or Reached audience demographics) with a Dimension of Age, Gender, City, or Country.
- **Post: comment details review** — ask which posts drew comments, and what those comment rows contain, for the profiles on the flow.
- **Post: profile interactions breakdown** — ask how interactions on posts break down, separate from the lifetime-style totals in Post: performance totals.
- **Story: performance totals (last 24 hours)** — ask about story totals while they still fall inside the last 24 hours. A slow cadence will outlive the window.
- **Story: navigation by action type (last 24 hours)** — ask how people moved through stories, by action type, in that same 24-hour window.
- **Story: profile interactions breakdown (last 24 hours)** — ask which profile interactions stories collected in the last 24 hours.
- **Profile: daily reach** — ask how reach moved day by day. Split by can stay Daily here, or Totals only if you want the window collapsed.
- **Profile: performance by media type** — ask whether the profile's result differs by media type. This is the current place for a media-type question.
- **Profile: performance by follow type** — ask how performance splits by follow type for the profiles you included.
- **Profile: links taps by contact button type** — ask which contact button type collected the link taps inside the Timeframe you set.
- **Profile: reach by media product type and follow type** — ask whether reach differs by follow type inside a media product type.
- **Profile: new audience demography insights** — ask about the new audience, with the same Metrics and Dimension choices as the follower demography report.
- **Post insights: carousel (deprecated)** — this category is deprecated. Prefer Post: performance totals for current post questions, and use the carousel report only when you are checking a flow that already depends on it.

## Why export Instagram Insights to Claude — real life cases

These are the Instagram questions that outgrow a single profile screen and belong in Claude.

- **Ask about the account before the posts**

  Profile: account overview is the starting point for the Profiles you selected. Ask Claude what that overview contains for a relative window such as *this month*. Add Profile: daily reach on another flow when the question is reach by day, with Split by set to Daily.

- **Use the 30-day follower line and the demographic cuts**

  Profile: followers daily breakdown (last 30 days) is a short window by name. Profile: followers demography insights and Profile: new audience demography insights take Metrics of Engaged audience demographics or Reached audience demographics and a Dimension of Age, Gender, City, or Country. Ask Claude which city or age band the reached audience sits in.

- **Read post totals, comments, and interactions together**

  Post: performance totals, Post: comment details review, and Post: profile interactions breakdown are three report types. Ask Claude which posts drew comments and which interactions sit on the profile. Bound the posts with Published after and Published before when a publish window matters more than all-time totals.

- **Catch stories before the day moves on**

  Story: performance totals (last 24 hours), Story: navigation by action type (last 24 hours), and Story: profile interactions breakdown (last 24 hours) only describe that recent day. Ask Claude how navigation by action type compares with the story totals. Refresh every 15 minutes or hourly so the window has not expired before you ask.

- **Split the profile by media type and follow type**

  Profile: performance by media type, Profile: performance by follow type, and Profile: reach by media product type and follow type are different cuts of the same profile. Ask Claude whether reach differs by follow type inside a media product type. Split by can be Totals only or Daily, depending on whether you want a series.

- **See which contact button collected the taps**

  Profile: links taps by contact button type is the report for link taps by button. Ask Claude which contact button type accounts for the taps in the Timeframe you set. Keep that report type on its own flow, and use Start date and End date when the report also shows those fields.

- **Put promoted ad ids on their own rows**

  Turn on Show promoted posts ad ids in separate rows when a post report should list ad ids separately. Ask Claude which promoted rows belong to which post. Data behavior of Track changes over time is the choice when you want the path of the numbers, and Latest data is the choice when you want the current rows only.

- **Leave the deprecated carousel report behind**

  Post insights: carousel (deprecated) is still listed, and it is deprecated. Prefer Post: performance totals for a current post question, and ask Claude about the carousel report only to check a flow that already uses it. Profile: performance by media type is the non-deprecated place to talk about media type.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
- [Connect Google Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md)
- [Connect Google Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-analytics-to-claude.md)
- [Connect Google Search Console to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-search-console-to-claude.md)
- [Connect Instagram Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-ads-to-claude.md)
- [Connect LinkedIn Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-ads-to-claude.md)
- [Connect LinkedIn Public Data to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-public-data-to-claude.md)
- [Connect Microsoft Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-microsoft-ads-to-claude.md)
- [Connect QuickBooks to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-quickbooks-to-claude.md)
- [Connect Shopify to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md)
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

