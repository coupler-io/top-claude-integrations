---
title: Connect Instagram Ads to Claude with Coupler.io
slug: connect-instagram-ads-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-ads-to-claude.md
source: Instagram Ads
destination: Claude
meta_title: Connect Instagram Ads to Claude with Coupler.io
meta_description: Send Instagram Ads Reports and Insights, campaigns, ad sets, and ads to Claude and ask about spend, clicks, and CTR.
---

![Instagram Ads](https://static.coupler.io/importers/instagram-ads.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Instagram Ads to Claude with Coupler.io

Meta's ads screens will show an Instagram campaign total, then leave you exporting when you want that total beside the ad set and the ad that produced it. The interface is built for changing delivery, not for a follow-up question. Coupler.io connects Instagram Ads and refreshes one category per flow: Reports and Insights, List of Campaigns, List of Ad sets, or List of Ads. Claude can answer about spend, impressions, clicks, CTR, CPC, and CPM, and about how those three structure lists are organized. You set the dates and the schedule once, and the next question does not need a fresh download.

## How to export Instagram Ads data to Claude

Four categories fit in this wizard, and the steps below are the whole path for each of them. Reports and Insights is the performance pull. List of Ad sets, List of Campaigns, and List of Ads are the structure pulls. A single flow never carries more than one of those four.

### Step 1. Basic settings

- **Ad accounts** — The ad accounts whose Instagram ads belong in this flow. Include every account the question will mention so Claude is not answering from a partial set.
- **Report type** — Reports and Insights, List of Ad sets, List of Campaigns, or List of Ads. The rest of the wizard follows that choice.

### Step 2. Report period

- **Start date** — First day of Instagram delivery to include. Choose *days ago* for a short lookback, or *last month*, *this month*, *last year*, or *this year* for a calendar stretch. Those values advance on their own. `{{365daysago}}` covers a trailing year.
- **End date** — Closing day of the window. Keep it relative and later refreshes still include the newest days.
- **Split data by period** — Set the grain Claude should answer in. The options are Daily, Weekly, Monthly, and Totals only. Daily or Weekly suits a question about what changed. Totals only fits when one figure for the whole window is the point.

### Step 3. Metrics and dimensions

- **Metrics and dimensions** — You choose from a long list of metrics and breakdowns. Stick to measures Instagram Ads insights actually expose and that you will name in a question: spend, impressions, clicks, CTR, CPC, and CPM. Leave the rest unticked. Structure report types do not need this picker.

### Step 4. Advanced settings

- **Attribution settings** — How Instagram Ads assigns credit. Use the same choice on every flow you plan to compare, or Claude will repeat a mismatch you created here.
- **Action attribution windows** — How long an action still counts. Lock the window before you ask which campaign looks stronger.
- **Filters** — Remove campaigns and other rows that should not enter the answer. Apply the same idea on Reports and Insights and on List of Campaigns when both flows will be discussed together.

### Step 5. Blend and transform data

- **Column management** — Remove Instagram Ads metrics you did not mean to ask about, and rename the ones you kept so spend, impressions, and clicks are obvious in the question.
- **Join** — Coupler.io's Join stitches Instagram Ads categories, for example Reports and Insights with List of Ad sets, together before Claude is asked anything. Two separate flows, and a question that asks Claude to connect them, is the other path.
- **Append** — Coupler.io's Append stacks a Facebook Ads pull beneath the Instagram Ads columns before Claude compares the two Meta surfaces.
- **Aggregate** — Coupler.io's Aggregate lifts Daily Instagram Ads insights to a Weekly or Monthly grain before Claude gives you the longer view.
- **Custom SQL** — Write a query when the Instagram Ads combination you want is not one of the metrics you selected, then ask Claude about that query output.

### Step 6. Claude destination

The destination step is labeled **Setup Claude integration**. Two tabs, and no further fields. Choose the tab for the place you already ask questions.

- **Chat and Cowork** — Register a Claude account first. In Claude, open the Coupler.io connector and click Connect (https://l.rw.rw/couplerio-claude-connector). On a Team or Enterprise plan, only an admin can finish that connection. Then, still in the Connectors menu, click Connect again and log in to Coupler.io.
- **Claude Code** — Begin a new session, paste the command that follows, restart the session, finish browser sign-in, and click Authorize:

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

During a launch, refresh Reports and Insights every 15 minutes, or hourly, so Claude's figures stay close to the ads screen. A quieter List of Campaigns flow can run daily, weekly, or monthly. That run is what updates the Instagram Ads dataset behind the next reply.

### Bonus: or just ask the AI Agent to build it for you

Describing an Instagram Ads pull beats filling the wizard by hand. In the Coupler.io app, open the right sidebar and use the AI Agent there to assemble the flow. That agent is not Claude, and it is not ChatGPT or Cursor.

> For *last month*, set Reports and Insights to spend, impressions, clicks, CTR, CPC, and CPM, split Weekly, and send the result to Claude.

What you still do yourself:

1. Connect Instagram Ads. Meta sign-in stays with you.
2. Choose the **Ad accounts** whose Instagram ads belong in the flow.
3. Hook up Claude on your own, using Chat and Cowork or an authorization inside Claude Code.

The prompt can carry Metrics and dimensions and the report period. You review them, and you do not rebuild the flow by hand.

## What data can you export from Instagram Ads to Claude with Coupler.io?

Four categories exist, and each flow is dedicated to one. Coupler.io's Join can stitch Reports and Insights to a structure list before Claude sees both. You can also keep the four flows separate and ask Claude to relate a result to the campaign, ad set, or ad behind it.

- **Reports and Insights** — The only performance category. With spend, impressions, clicks, CTR, CPC, and CPM selected under Metrics and dimensions, this is the set Claude uses when you ask what the Instagram ads returned. Split data by period decides whether that answer is a trend or one total.
- **List of Ad sets** — The ad sets in the Ad accounts you ticked. Ask how those ad sets are organized before you ask what they spent, and join this list to Reports and Insights when the question needs both.
- **List of Campaigns** — The campaigns those accounts contain. Ask for the campaign roster, then which of those campaigns show up in the insights once Coupler.io's Join has paired the two categories.
- **List of Ads** — The ads inside those campaigns and ad sets. Ask which ads exist, and which of them carried the clicks, after this list is refreshed next to Reports and Insights.

## Why export Instagram Ads to Claude — real life cases

Instagram Ads supports four categories, and these are the questions that list can actually answer.

- **Ask what the ads returned**

  Reports and Insights is the performance category. In Metrics and dimensions, tick CTR, CPC, and CPM together with spend, impressions, and clicks, and ignore the rest of that long list. Ask Claude which Ad accounts rose on CTR and which only rose on spend.

- **Put campaigns next to the ads inside them**

  List of Campaigns and List of Ads are separate flows. Coupler.io's Join stitches them before Claude sees the pair, which is how you ask which ads sit in the campaign that spent. Keeping both flows and asking Claude to relate them works when you want each list left intact.

- **Ask what the ad sets look like before you judge the result**

  List of Ad sets is the configuration category for the Ad accounts in the flow. Ask Claude how those ad sets differ across accounts. Pair the list with Reports and Insights only after Coupler.io's Join has run, so the question can mention setup and results together.

- **Lock credit before the comparison**

  Attribution settings and Action attribution windows decide how an action is credited. Set both the same way on every Instagram Ads flow you intend to compare, then ask Claude which campaign looks better. If the windows differ, the answer will differ for a reason that has nothing to do with the ads.

- **Keep stray campaigns out of the answer**

  Filters, on the advanced step, drops rows you do not want Claude to reason over. Use the same standard on Reports and Insights and on List of Campaigns so both answers ignore the same campaigns. Then ask what the remaining ads did on spend, impressions, and clicks.

- **Ask for a trend, or for one number**

  Split data by period offers Daily, Weekly, Monthly, or Totals only. Start date and End date take *this month*, *last month*, *this year*, *last year*, or *days ago*, and `{{365daysago}}` when the lookback is a full year. Ask Claude what changed week to week, or ask for the single total when the grain would only add noise.

- **Have a current figure by the time you ask**

  Schedule Reports and Insights every 15 minutes while a flight is live, or hourly, daily, weekly, or monthly when the questions are calmer. Each refresh updates the Instagram Ads dataset Claude answers from. You ask in plain language instead of downloading the date range again.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
- [Connect Google Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md)
- [Connect Google Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-analytics-to-claude.md)
- [Connect Google Search Console to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-search-console-to-claude.md)
- [Connect Instagram Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-insights-to-claude.md)
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

