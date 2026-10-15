---
title: Connect TikTok Organic to Claude with Coupler.io
slug: connect-tiktok-organic-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md
source: TikTok Organic
destination: Claude
meta_title: Connect TikTok Organic to Claude with Coupler.io
meta_description: Ask Claude about TikTok Organic profile audiences, profile insights, and video list insights on a refresh schedule you set.
---

![TikTok Organic](https://static.coupler.io/importers/tiktok.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect TikTok Organic to Claude with Coupler.io

TikTok's own analytics splits gender, country, hourly activity, profile totals, and video lists into separate views. A question that needs both who watches and which videos travel is hard to finish there. Coupler.io carries TikTok Organic to Claude, with one report type in each flow. You set that report type and a start and end date, and a rolling window lets the next refresh move on its own. Claude can then answer from Profile insights or from Video list insights without a fresh download before the morning read.

## How to export TikTok Organic data to Claude

The wizard asks for one report type. Audience reports cover gender, country, and hourly activity. A separate profile report and two video-list reports cover the rest. Each name is listed in the data section below.

### Step 1. Basic settings

- **Report type** — Pick the single category this flow will refresh. Profile audience genders, Profile audience countries, and Profile audience hourly activity describe who shows up and when. Profile insights summarizes the profile. Video list top countries and Video list insights describe the videos.

### Step 2. Report period

- **Start date** — Where the pull begins. *this year* covers the calendar year, *last month* is a finished recent month, and *days ago* is the short lookback. The choice is relative, so the window keeps its length as time moves.
- **End date** — Where the pull stops. *this month* includes the month underway, and *last year* is available when Claude should hold the prior year in view. Keep the end relative and scheduled runs stay current.

### Step 3. Blend and transform data

- **Column management** — Keep the gender, country, or hour columns that the chosen TikTok Organic report type actually uses, and hide the rest so Claude is reading the fields you meant.
- **Join** — Coupler.io's Join lines Profile audience countries up with Video list top countries on country before Claude compares the two mixes.
- **Append** — Coupler.io's Append stacks separate TikTok Organic flows that share a date column before Claude reads them as one series.
- **Aggregate** — Coupler.io's Aggregate totals Profile audience hourly activity into broader dayparts before Claude names the quiet hours.
- **Custom SQL** — Write a query that keeps the leading countries from Video list top countries, and pass that shorter list to Claude.

### Step 4. Claude destination

TikTok Organic becomes something you can ask about during **Setup Claude integration**. That step is two tabs and nothing else to fill in.

- **Chat and Cowork** — Register a Claude account before any profile question goes to chat. The Coupler.io connector is at https://l.rw.rw/couplerio-claude-connector, and the button is Connect. Team and Enterprise plans allow that button for an admin. A further Connect, inside the Connectors menu, is the Coupler.io sign-in.
- **Claude Code** — Open a fresh Claude Code session and paste the command that follows. Restart comes after the paste. The browser then asks you to sign in, and Authorize finishes it.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 5. Schedule

Profile and video reports can refresh every 15 minutes. Hourly, daily, weekly, and monthly are the other cadences. After a run finishes, Claude answers from the TikTok Organic window that just updated.

### Bonus: or just ask the AI Agent to build it for you

Sketch the profile or video flow with the Coupler.io AI Agent. It is the assistant along the right edge of the Coupler.io app. Questions still go to Claude afterward. ChatGPT and Cursor do not build this importer.

> "Take Profile audience hourly activity and Video list insights for this month and load the result to Claude."

Three steps stay in your hands:

1. Connect TikTok Organic yourself. Sign-in cannot be delegated.
2. Choose the **Report type**, which is the scope decision this wizard actually offers.
3. Sign Claude in yourself on Chat and Cowork, or authorize Claude Code next.

## What data can you export from TikTok Organic to Claude with Coupler.io?

Six categories are available. A flow is dedicated to a single report type. Coupler.io's Join can combine a profile report type with a video report type ahead of any question to Claude.

- **Profile audience genders** — Lets Claude describe how the profile audience splits by gender for the dates you set.
- **Profile audience countries** — Lets Claude say which countries the profile audience comes from, which is the geographic cut on the account itself.
- **Profile audience hourly activity** — Lets Claude point at the hours the audience is active, so a posting question can follow the clock rather than a hunch.
- **Profile insights** — The profile summary Claude can quote when you want the account's own totals for the chosen window.
- **Video list top countries** — The country ranking for the video list, so Claude can talk about where videos travel, separate from where the profile audience lives.
- **Video list insights** — The video-level read. Ask Claude what the list shows for the start and end dates on the flow.

## Why export TikTok Organic to Claude — real life cases

Once those profile and video categories are flowing, Claude can answer the audience questions the TikTok app keeps in separate screens.

- **Ask how the audience splits by gender**

  Profile audience genders is the whole category. Set Start date and End date to *last month* if you want a closed month, then ask Claude how the split looks. A weekly refresh keeps the next answer on a new window without rebuilding the flow.

- **Ask which countries watch the profile**

  Profile audience countries answers "where is the profile audience?" Ask Claude for the countries that dominate, and for any country that showed up only after you moved Start date to *this year*. The report type is the scope; there is no second geography field to set.

- **Find the hours the audience is actually on**

  Profile audience hourly activity is the clock. Ask Claude which hours carry activity and which stay quiet. Coupler.io's Aggregate can fold those hours into dayparts before Claude names a posting window.

- **Get a profile summary for the dates that matter**

  Profile insights is the account-level category. Ask Claude for the profile picture over *this month*, or compare it with *last year* by running the same report type on two date windows and appending them. The sign-in still happens in your TikTok account.

- **See where the videos travel**

  Video list top countries is about the videos, not the profile audience. Ask Claude which countries lead the video list for *days ago* versus *this year*. That shorter lookback is useful when a single clip is still spreading.

- **Read the video list itself**

  Video list insights gives Claude the video list for the saved dates. Ask which videos belong in the current window and what the list implies for the next posting week. Keep this report type in its own flow.

- **Relate profile countries to video countries**

  Profile audience countries and Video list top countries answer different questions. Coupler.io's Join can match them on country before Claude says whether the videos are finding the same places as the profile audience. Ask that only after both flows have run.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
- [Connect Google Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md)
- [Connect Google Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-analytics-to-claude.md)
- [Connect Google Search Console to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-search-console-to-claude.md)
- [Connect Instagram Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-ads-to-claude.md)
- [Connect Instagram Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-insights-to-claude.md)
- [Connect LinkedIn Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-ads-to-claude.md)
- [Connect LinkedIn Public Data to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-public-data-to-claude.md)
- [Connect Microsoft Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-microsoft-ads-to-claude.md)
- [Connect QuickBooks to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-quickbooks-to-claude.md)
- [Connect Shopify to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md)
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

