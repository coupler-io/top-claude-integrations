---
title: Connect Microsoft Ads to Claude with Coupler.io
slug: connect-microsoft-ads-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-microsoft-ads-to-claude.md
source: Microsoft Ads (Bing Ads)
destination: Claude
meta_title: Connect Microsoft Ads to Claude with Coupler.io
meta_description: Connect Campaign performance report, Keyword performance report, and Share of voice report from Microsoft Ads so Claude can answer on a schedule.
---

![Microsoft Ads](https://static.coupler.io/importers/microsoft.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Microsoft Ads to Claude with Coupler.io

Microsoft Ads still asks you to open one report at a time, then keep the comparison in a download or in your head. Campaign, keyword, hotel, shopping, and share reports sit in different corners of that interface. Coupler.io runs the **Report type** you select for the **Ad accounts** you select, and it refreshes that choice on a schedule. You ask Claude, in ordinary language, which keyword conflicts with a negative, which hotel group moved, or which extension sat beside a call. Metrics and dimensions are fixed in the wizard, so the question lands on the rows you meant to include.

## How to export Microsoft Ads data to Claude

The wizard covers forty-four report types: campaign and keyword performance, extensions and calls, budget and change history, dynamic search, hotels, shopping, audiences, and **Custom report**. Every label is named further down. One flow carries one report type.

### Step 1. Basic settings

- **Ad accounts** — tick the Microsoft Ads accounts this flow should cover. Claude can be asked about only those accounts.
- **Report type** — the single report Claude will answer from. All forty-four human-readable labels are listed in the data section below.

### Step 2. Report period

- **Report period** — the range the report is calculated for, read together with the start and end bounds.
- **Start date** — where the window opens. The relative picker offers *days ago*, *this month*, *last month*, *this year*, and *last year*, and it rolls forward on later runs. A trailing year is the macro `{{365daysago}}`.
- **End date** — where the window closes. The same relative picker keeps every refresh aligned with the schedule.
- **Split data by period** — the grain of the rows. Choose Summary, Hourly, Daily, Weekly from Sunday, Weekly from Monday, Monthly, or Yearly.

### Step 3. Metrics and dimensions

- **Metrics** — the measures this report type should include. Leave off anything you will not ask Claude about.
- **Dimensions** — the breakdowns that sit with those metrics on this screen.

### Step 4. Dimensions

- **Dimensions** — the same field title on the following screen. Add the breakdowns the report type still needs. It is not a second, invented label.

### Step 5. Advanced settings

- **Advanced filters** — conditions that drop rows before Claude sees them. What you can filter depends on the report type you picked.

### Step 6. Blend and transform data

- **Column management** — hide Microsoft Ads columns you will not mention, rename the cryptic leftovers, and lead with the campaign or keyword identifiers you expect to cite.
- **Join** — Coupler.io's Join stitches a Keyword performance report to a Search campaign change history report before Claude sees the combined rows. A separate flow per report type also works, and the question you put to Claude is what relates the keyword rows to the edit history.
- **Append** — Coupler.io's Append stacks several Ad accounts that share one report type, and Claude can then be asked which of those accounts diverges.
- **Aggregate** — Coupler.io's Aggregate rolls Hourly or Daily Microsoft Ads rows up to Weekly from Monday or Monthly before Claude is asked about that coarser grain.
- **Custom SQL** — write a query when the named transformations cannot shape the Microsoft Ads result, then ask Claude about the query result.

### Step 7. Claude destination

This step has two tabs and no fields of its own. The product step is **Setup Claude integration**.

- **Chat and Cowork** — Register a Claude account before you leave this Microsoft Ads tab. Open the Coupler.io connector for these ad accounts and click Connect (https://l.rw.rw/couplerio-claude-connector) while the report type is still the one you saved. A Team or Enterprise plan means you must be an admin to finish that link. Afterward, stay in the Connectors menu, click Connect again beside the Microsoft Ads flow, and log in to Coupler.io.
- **Claude Code** — Begin by starting a new session for these Microsoft Ads reports. Put the command below into that session, restart it so the command is picked up, finish the browser sign-in, and click Authorize.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 8. Schedule

Refresh can run every 15 minutes. Hourly, daily, weekly, and monthly are the slower cadences. Each run refreshes the dataset Claude answers from, so a Thursday question about a keyword report uses Thursday's run.

### Bonus: or just ask the AI Agent to build it for you

Microsoft Ads can be described in one sentence instead of clicking every field. Inside the Coupler.io app, the Coupler.io AI Agent occupies the sidebar on the right and only assembles the wizard. Claude is where you ask afterward. ChatGPT and Cursor are not that agent.

> Pull Keyword performance report and Negative keyword conflict report for the ad accounts I select, split Daily from last month through this month, and send the result to Claude.

The agent sets the report type, dates, metrics, dimensions, and filters when it can. Three choices stay with you:

1. Connect Microsoft Ads. You complete the Microsoft sign-in.
2. Choose the **Ad accounts** this flow is allowed to read.
3. Connect Claude for these reports, using the Chat and Cowork connector or a Claude Code authorization.

Those three Microsoft Ads choices stay manual.

## What data can you export from Microsoft Ads to Claude with Coupler.io?

Microsoft Ads contributes forty-four report types. A flow carries only one of them. Stitching two report types is Coupler.io's Join, and that stitch happens before Claude sees the rows. Related labels are grouped below; each name is the wizard label.

- **Campaign performance report**, **Ad group performance report**, **Ad performance report**, **Keyword performance report**, and **Account performance report** — ask Claude which campaign, ad group, ad, keyword, or account is carrying the ad accounts in the flow.
- **Campaign performance report with share performance statistics**, **Ad group performance report with share performance statistics**, **Account performance report with share performance statistics**, and **Share of voice report** — ask how share statistics sit beside delivery. The first three bake share into campaign, ad group, or account rows; Share of voice report is the dedicated voice view.
- **Ad extension by ad report**, **Ad extension by keyword report**, **Ad extension detail report**, and **Call detail report** — ask which extension, on an ad or a keyword, lines up with the calls in Call detail report.
- **Budget summary report** and **Search campaign change history report** — ask whether the budget summary agrees with the edits recorded between your start and end dates.
- **DSA auto target performance report**, **DSA category performance report**, **DSA search query performance report**, **Search query performance report**, and **Destination URL performance report** — ask which dynamic-search target or category sits behind a query, and whether the destination URL is the page you expect. Search query performance report is the query report outside DSA.
- **Hotel dimension performance report**, **Hotel dimension performance report with share performance statistics**, **Hotel group performance report**, and **Hotel group performance report with share performance statistics** — ask how a hotel group compares with its dimension rows, with or without share performance statistics.
- **Product dimension performance report**, **Product dimension performance report with share performance statistics**, **Product match count report**, **Product partition performance report**, **Product partition performance report with share performance statistics**, **Product partition unit performance report**, and **Product search query performance report** — ask which partition, unit, dimension, or product search query looks thin, and use Product match count report when the question is how many products matched.
- **Ad dynamic text performance report**, **Asset performance report**, **Asset group performance report**, **Audience performance report**, **Conversion performance report**, **Goals and funnels report**, and **Publisher usage performance report** — ask about dynamic text, assets, asset groups, audiences, conversions, goals and funnels, or where publisher usage concentrates. Each label is its own report type.
- **Age gender audience report**, **Professional demographics audience report**, **Geographic performance report**, **User location performance report**, and **Negative keyword conflict report** — ask how age and gender, professional demographics, geography, and user location differ, and which negatives conflict.
- **Custom report** — the report type for a combination you define with Metrics and Dimensions. Ask Claude about that combination on its own flow.

## Why export Microsoft Ads to Claude — real life cases

Once a report type is refreshing, these are the Microsoft Ads questions worth putting to Claude.

- **See which campaign is actually carrying the account**

  Point Claude at a Campaign performance report for the Ad accounts in the flow and ask which campaigns deserve the next budget conversation. Add an Ad group performance report or an Ad performance report as a second flow when the answer has to go below the campaign. Coupler.io's Join can put two of those report types together before you ask.

- **Catch keywords that fight their own negatives**

  A Keyword performance report beside a Negative keyword conflict report is how you ask which queries a negative is blocking and which keywords still spend in the same ad groups. Bring in Search query performance report when the question is the query people typed, not the keyword you bought. Set Split data by period to Daily if you want the conflict dated.

- **Read share without opening a second export**

  Share of voice report, Campaign performance report with share performance statistics, and Account performance report with share performance statistics answer different share questions. Ask Claude how share moves for one account when Split data by period is Weekly from Monday. Leave each report type on its own flow unless Coupler.io's Join has already stitched them.

- **Inspect shopping partitions and product queries**

  Product partition performance report, Product partition unit performance report, and Product search query performance report answer different shopping questions. Ask Claude which partition looks thin and which product search query keeps showing under it. Product match count report and Product dimension performance report belong on their own flows when the question turns to match counts or product dimensions.

- **Treat hotel campaigns as their own conversation**

  Hotel dimension performance report and Hotel group performance report are separate from a standard campaign report. Ask Claude how a hotel group compares with its dimension rows. Switch to Hotel dimension performance report with share performance statistics or Hotel group performance report with share performance statistics when share is the point of the question.

- **Follow dynamic search from target to landing page**

  DSA auto target performance report, DSA category performance report, and DSA search query performance report cover dynamic search from three sides. Ask Claude which auto target or category sits behind the queries you care about. Destination URL performance report is the follow-up when the landing page is what you distrust.

- **Line edits up with the budget**

  Search campaign change history report is the audit of what changed. Ask Claude what changed between Start date and End date, then set a Budget summary report flow if the question is whether the budget moved with the edit. Coupler.io's Join can line that history up with a performance report before Claude sees it.

- **Ask about people, places, calls, and extensions**

  Age gender audience report, Professional demographics audience report, Geographic performance report, and User location performance report are the people-and-place report types. Call detail report and Ad extension detail report cover calls and extensions. Ask Claude which place or age-gender slice, and which extension, belongs with the accounts you selected under Ad accounts.

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
- [Connect QuickBooks to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-quickbooks-to-claude.md)
- [Connect Shopify to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md)
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

