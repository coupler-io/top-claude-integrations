---
title: Connect LinkedIn Ads to Claude with Coupler.io
slug: connect-linkedin-ads-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-ads-to-claude.md
source: LinkedIn Ads
destination: Claude
meta_title: Connect LinkedIn Ads to Claude with Coupler.io
meta_description: Send LinkedIn Ads analytics, Sponsored leads, Creatives, and Conversions to Claude and ask what each campaign achieved.
---

![LinkedIn Ads](https://static.coupler.io/importers/linkedin.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect LinkedIn Ads to Claude with Coupler.io

Campaign Manager shows LinkedIn Ads one breakdown at a time. A question that mixes companies, creatives, and sponsored leads means several exports, and member-level reporting does not share a screen with video inventory or conversion setup. Coupler.io connects LinkedIn Ads and refreshes the single category you chose, from Ad analytics by single dimension through Conversions. Claude answers in plain language from that category, or from categories Coupler.io has already joined. Ad accounts, the report period, and the schedule are set once, and the next question reuses them.

## How to export LinkedIn Ads data to Claude

The wizard covers eleven categories: Ad analytics by single dimension, Ad analytics by multiple dimensions, Campaign performance by member dimension, Sponsored leads, Ad account users, Campaign groups, Campaigns, Creatives, Video ads, Shares (creative sponsored content), and Conversions. Each flow is built for one of them. Analytics report types are the ones that use Metrics, Dimension, and Dimensions.

### Step 1. Basic settings

- **Ad accounts** — The LinkedIn ad accounts included in this flow. Select every account the question should see, or Claude will answer from a subset.
- **Report type** — The category to refresh. The eleven names above are the full set, and the later steps follow the one you pick.

### Step 2. Report period

- **Start date** — First day LinkedIn Ads should include. The relative picker can be *this month*, *last month*, *days ago*, *this year*, or *last year*, and it rolls forward at the next run. A trailing year is written `{{365daysago}}`.
- **End date** — Last day in the window. A relative end keeps later refreshes current without a manual change.
- **Split data by period** — Totals only, Daily, Monthly, or Yearly. There is no weekly grain. Daily is for a running question. Totals only is for one figure across the whole window. Yearly matches a question about *this year* against *last year*.

### Step 3. Metrics and dimensions

- **Metrics** — The measures for an analytics report type. Keep the ones you will actually name when you ask Claude, and skip the rest.
- **Dimension** — The single cut, for a report type that takes one dimension, such as Ad analytics by single dimension.
- **Dimensions** — One or more cuts when the report type takes several, such as Ad analytics by multiple dimensions. The values are Account, Campaign, Campaign group, Card index, Company, Campaign objective type, Conversion, Creative, Impression device type, Placement name, Serving location, and Shares (creative sponsored content).

### Step 4. Advanced settings

- **Advanced filters** — Narrow the LinkedIn Ads rows before Claude sees them, so a company or campaign you do not want in the answer never enters it.
- **Lead generation forms** — Which forms are included when Report type is Sponsored leads. Name the forms the question is about.

### Step 5. Blend and transform data

- **Column management** — Trim LinkedIn Ads fields down to the Metrics and Dimensions you intend to ask about, and give the survivors names you would actually say out loud.
- **Join** — Coupler.io's Join stitches LinkedIn Ads categories such as Campaigns and Campaign groups together before Claude gets the question. Separate flows also work: ask Claude to relate a campaign to its group.
- **Append** — Coupler.io's Append lines other paid sources up under the LinkedIn Ads columns before Claude answers across channels.
- **Aggregate** — Coupler.io's Aggregate rolls Daily LinkedIn Ads analytics up to Monthly or Yearly before Claude discusses the longer window.
- **Custom SQL** — Query the LinkedIn Ads pull when you need a company-level figure the Dimensions list does not finish on its own, and ask Claude about the query result.

### Step 6. Claude destination

You land on **Setup Claude integration**, which is two tabs and no extra form. Connect either tab and the LinkedIn Ads flow becomes something you can question.

- **Chat and Cowork** — Register a Claude account if the person reviewing LinkedIn Ads does not have one. Find the Coupler.io connector and click Connect (https://l.rw.rw/couplerio-claude-connector). Only an admin can do that on a Team or Enterprise plan. Still inside the Connectors menu, click Connect and finish the Coupler.io login before anyone asks about campaigns.
- **Claude Code** — Create a session, then place this command in it. Restart after the paste. When the browser asks you to sign in, finish that prompt, and click Authorize:

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Sponsored leads rewards a short interval, every 15 minutes or hourly, when someone will ask about new form fills the same day. Campaign groups, Creatives, and Conversions are fine on a daily, weekly, or monthly refresh. Whatever you ask Claude next about LinkedIn Ads should reflect the pull that just finished.

### Bonus: or just ask the AI Agent to build it for you

LinkedIn Ads setup can start from a sentence. In the Coupler.io app the AI Agent occupies the right sidebar and only assembles the flow. It is not Claude, and it is not ChatGPT or Cursor either.

> Build Ad analytics by multiple dimensions using Company and Campaign for *this year*, and load the result to Claude.

Your part is the three steps the agent cannot take:

1. Connect LinkedIn Ads. Signing in to LinkedIn stays with you.
2. Choose the **Ad accounts** that should be in scope.
3. Connect Claude through the Chat and Cowork connector, or through Claude Code authorization.

Dimension, Dimensions, and the report period can be taken from the prompt. You still confirm them before the first run.

## What data can you export from LinkedIn Ads to Claude with Coupler.io?

Eleven categories are on offer, and a flow is built around exactly one. Coupler.io's Join can stitch a performance category to a structure category before Claude sees them. You can also keep each category alone and ask Claude to relate the answers.

- **Ad analytics by single dimension** — Performance with one cut, chosen in Dimension. Ask a straight question, such as results by Campaign or by Company, without mixing a second cut into the same pull.
- **Ad analytics by multiple dimensions** — Performance with several cuts at once, chosen in Dimensions. Ask how Company and Campaign, or Impression device type and Placement name, moved together.
- **Campaign performance by member dimension** — The member-side performance category. Ask how members responded, and use Company or Campaign objective type from the Dimensions list when the analytics reports need those same cuts.
- **Sponsored leads** — Form submissions, limited by Lead generation forms when you name specific forms. Ask which form produced the lead for the Ad accounts in the flow.
- **Ad account users** — The people attached to the Ad accounts you selected. Ask who can act on the account when a result changes and you need the roster rather than another performance cut.
- **Campaign groups** — The groups that contain your campaigns. Ask for the group list, then join it to Campaigns when the question is whether a group or a single campaign did the work.
- **Campaigns** — The campaigns in those accounts. Ask for the campaign roster on its own, or next to Ad analytics by single dimension once Coupler.io's Join has paired them.
- **Creatives** — The creative inventory. Ask what is available to serve, separate from the performance of any one Creative dimension value.
- **Video ads** — The video ads in the account. Ask which videos are in market, then what the analytics say once that list sits beside an analytics category.
- **Shares (creative sponsored content)** — The sponsored shares themselves. Ask which share was served, and remember the same name is also a value under Dimensions when you need performance split by that share rather than the inventory list.
- **Conversions** — The conversion setup, which is a different category from the Conversion dimension on an analytics report. Ask what conversions exist, and keep that answer separate from performance split by Conversion.

## Why export LinkedIn Ads to Claude — real life cases

With one category refreshing, Claude can take the LinkedIn Ads questions Campaign Manager splits across screens.

- **Start with one dimension, then add another**

  Ad analytics by single dimension uses Dimension for one cut. Ad analytics by multiple dimensions uses Dimensions, so Account, Campaign, Campaign group, and Company can share a pull. Ask Claude the single-cut question first, then the cross-cut, without rebuilding the report in Campaign Manager.

- **Ask how companies and objectives responded**

  Campaign performance by member dimension is the category for member-side reporting. Company, Campaign objective type, and Conversion are available in Dimensions when an analytics report needs those cuts. Ask Claude which companies and which objectives the delivery reached.

- **Read sponsored leads without a manual download**

  Sponsored leads collects the form fills, and Lead generation forms limits that set to the forms you name. Ask Claude which form produced the lead and which Campaigns were in the Ad accounts you selected. A short schedule keeps that answer close to the moment the form was submitted.

- **Judge a campaign inside its group**

  Campaign groups and Campaigns are separate categories. Coupler.io's Join stitches a campaign to its group before Claude sees them, and Coupler.io's Aggregate can roll campaign rows up to the group when the question is the group total. Ask which group is carrying the result, and which campaign inside it is not.

- **Ask which creative, video, or sponsored share ran**

  Creatives, Video ads, and Shares (creative sponsored content) are three views of what was served. Card index and Creative are dimension values when you need performance by card or creative rather than the inventory list. Ask Claude which video or share was in market, then what Ad analytics by single dimension says it did.

- **Keep conversion setup apart from conversion results**

  Conversions is its own category, while the Conversion value inside Dimensions is how you split an analytics report. Pull the category when you want the setup, and use the dimension when you want performance cut by conversion. Ask Claude to keep those two answers apart so a setup list is not treated as a result.

- **See who can touch the ad account**

  Ad account users lists the people on the Ad accounts in the flow. Ask Claude who has access when performance moves and you need the roster. Advanced filters can keep that list to the accounts you are actually questioning.

- **Split delivery by device, placement, and where it served**

  On Ad analytics by multiple dimensions, Dimensions can include Impression device type, Placement name, and Serving location. Ask Claude whether those cuts carried the same Campaign objective type. Add Shares (creative sponsored content) as a dimension when the question is about the sponsored share, and use the Video ads category when the question is which video exists.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
- [Connect Google Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md)
- [Connect Google Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-analytics-to-claude.md)
- [Connect Google Search Console to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-search-console-to-claude.md)
- [Connect Instagram Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-ads-to-claude.md)
- [Connect Instagram Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-instagram-insights-to-claude.md)
- [Connect LinkedIn Public Data to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-public-data-to-claude.md)
- [Connect Microsoft Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-microsoft-ads-to-claude.md)
- [Connect QuickBooks to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-quickbooks-to-claude.md)
- [Connect Shopify to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md)
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

