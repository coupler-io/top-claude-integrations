---
title: Connect Facebook Ads to Claude with Coupler.io
slug: connect-facebook-ads-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md
source: Facebook Ads (Meta Ads)
destination: Claude
meta_title: Connect Facebook Ads to Claude with Coupler.io
meta_description: Send Facebook Ads insights, sponsored leads, creatives, and invoices to Claude and ask about spend and billing in plain language.
---

![Facebook Ads](https://static.coupler.io/importers/facebook.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Facebook Ads to Claude with Coupler.io

Ads Manager is comfortable when you are pausing a campaign or checking a single date range. It gets clumsy as soon as the question needs performance, lead forms, and invoices in the same breath, because those live in different corners of the product. A long comparison turns into another download. Coupler.io connects your Facebook Ads (Meta Ads) account and refreshes the one kind of data you choose. From there you can ask Claude the way you would ask a colleague: how spend and results moved last month, which leads came in through your lead forms, what your ads actually looked like, who changed a budget and when, or what Meta billed the business. You set the flow up once, and the schedule keeps Claude's next answer in step with the account.

## How to export Facebook Ads data to Claude

The wizard covers nine categories: Reports and Insights, List of Sponsored Leads, List of Ad creatives, List of Ad sets, List of Campaigns, List of Ads, List of Ads with ad creatives, List of Activities, and List of Business invoices. Sponsored leads use Pages and optional Lead generation forms. Business invoices use Businesses plus the billing and issue dates instead of the report period.

### Step 1. Basic settings

- **Report type** — The category this flow refreshes. Choose one of the nine. Later steps change to match that choice.
- **Ad accounts** — Every ad account the question should cover. Several accounts can share one flow, so an agency roll-up does not mean a separate setup per client.
- **Pages** — Used by List of Sponsored Leads. Pick the Pages whose form submissions Claude should be able to discuss.
- **Businesses** — Used by List of Business invoices. Pick the businesses whose bills belong in the answer.

### Step 2. Report period

Performance and structure categories use this window. List of Business invoices does not; it uses the date filters in the next step.

- **Start date** — Where the Facebook Ads window opens. You can pick *last year* or *this year*, *last month* or *this month*, or *days ago*. Those choices move forward on later runs, so you are not editing the flow every Monday. For windows the presets do not cover, use a macro instead. `{{2monthsago.startof(month)}}` starts on the first day of the month before last, and the window still moves forward on every run. See [Macros in data flows](https://docs.coupler.io/functionality/macros-in-data-flows) for the full list.
- **End date** — Where the window closes. Leave it on a relative choice and each refresh still reaches the latest days.
- **Split data by period** — Daily, Weekly, Monthly, or Totals only. Daily is the grain to pick when you will ask Claude what changed from one day to the next. Totals only is enough when you want one figure for the whole window.

### Step 3. Date filters

List of Business invoices uses these four fields in place of the report period.

- **Billing start date** — First day of the billed window for the Businesses you selected. A relative value such as *last month* or *this year* keeps the following run current.
- **Billing end date** — Last day of that billed window.
- **Issue start date** — First day of the window based on when the invoice was issued. Use this pair when the question is about issue dates.
- **Issue end date** — Last day of the issue window.

### Step 4. Metrics and dimensions

- **Metrics and dimensions** — The measures and cuts on Reports and Insights. Keep spend, impressions, clicks, CTR, CPC, and CPM when those are the questions you actually ask, and leave the rest of the long list unticked so Claude is not sorting through columns you will never name.
- **Breakdowns** — The breakdown control inside this step. Split the result by placement, device, age, geography, and the rest of the breakdown list when the answer needs to say which slice moved.

### Step 5. Advanced settings

- **Attribution settings** — Use ad group settings when each ad set should keep its own rule, or Specify manually when every selected ad account should share one rule before you ask Claude to compare them.
- **Action attribution windows** — How long an action still counts toward the ad. Fix this before a comparison, or Claude will faithfully mix different credit rules.
- **Filters** — Leave out campaigns and other rows you do not want in the answer.
- **Lead generation forms** — Optional for List of Sponsored Leads. Name the forms you care about, or leave the field unset and every form on the selected Pages is included.
- **Ad creative columns** — Which creative attributes travel with the ads. Set it on List of Ads with ad creatives so Claude sees the attributes you intend to ask about.
- **Updated since** — Only records touched after this date. On List of Activities, a boundary such as *last month* keeps the question on recent edits.

### Step 6. Blend and transform data

- **Column management** — Hide Facebook Ads fields you will not ask about, rename the ones Ads Manager leaves cryptic, and put spend beside the breakdown you care about.
- **Join** — Coupler.io's Join stitches Facebook Ads categories such as Reports and Insights and List of Campaigns together before Claude sees a combined result. The other path is one flow per category, then a question that asks Claude to relate them.
- **Append** — Coupler.io's Append stacks another paid source under the Facebook Ads columns before Claude answers a cross-channel question.
- **Aggregate** — Coupler.io's Aggregate rolls a Daily Facebook Ads split up to a week or a month before Claude summarizes that stretch.
- **Custom SQL** — Write a query when Facebook Ads needs a figure the other transformations do not produce, and ask Claude about the query output.

### Step 7. Claude destination

The product step is **Setup Claude integration**. It has two tabs and no extra fields to name. Complete one tab and Claude can take questions against the Facebook Ads category this flow refreshes.

- **Chat and Cowork** — The person asking about Facebook Ads needs a Claude account, so register one first. Open the Coupler.io connector and click Connect (https://l.rw.rw/couplerio-claude-connector). A Team or Enterprise plan allows that click only for an admin. After the connector is listed, use the Connectors menu to click Connect and log in to Coupler.io, which is what makes this flow visible in chat.
- **Claude Code** — Open a session you have not used for this yet. Paste the command below into that session. Restart after the paste is saved, finish the browser sign-in, and click Authorize:

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 8. Schedule

New form fills justify a short interval: every 15 minutes, or hourly, so a question about List of Sponsored Leads is not waiting on a manual download. Reports and Insights and List of Business invoices are usually enough on a daily, weekly, or monthly cadence. Every run brings the Facebook Ads category up to date for the next question you put to Claude.

### Bonus: or just ask the AI Agent to build it for you

A Facebook Ads flow can start from one sentence in the Coupler.io app. The AI Agent is the panel along the right sidebar, and it only drafts the importer. Treat it as separate from Claude, from ChatGPT, and from Cursor.

> For *last month*, refresh Reports and Insights split Daily, break the rows down by placement, and send the result to Claude.

The sign-in steps stay in your hands:

1. Connect Facebook Ads. You complete the Meta login yourself.
2. Choose which **Ad accounts** are in scope. For leads, also choose **Pages**. For invoices, also choose **Businesses**.
3. Connect Claude on the Chat and Cowork tab, or authorize it from Claude Code.

Report type, the dates, and the schedule can come from the prompt. You do not retype them.

## What data can you export from Facebook Ads to Claude with Coupler.io?

Nine categories are available. Each flow carries one of them. When a question needs two, Coupler.io's Join combines those Facebook Ads categories before Claude sees the result. Leaving them as separate flows and asking Claude to relate the answers works as well.

- **Reports and Insights** — The performance category. Spend, impressions, clicks, CTR, CPC, and CPM, cut by the Breakdowns you kept (placement, device, age, geography), are what Claude uses when you ask what the ads did.
- **List of Sponsored Leads** — People who submitted a form on the Pages you selected, optionally narrowed with Lead generation forms. Ask which page and which form the submission came from.
- **List of Ad creatives** — The creative assets held by the ad accounts, separate from the ads that reference them. Ask what is in the library before you ask what ran.
- **List of Ad sets** — The ad sets inside the selected Ad accounts. Ask how they sit under the campaigns you are about to judge.
- **List of Campaigns** — The campaign roster behind a performance answer. Refresh it beside Reports and Insights when the question needs both a name and a result.
- **List of Ads** — The ads themselves, without the creative detail. Ask which ads belong to a campaign when the asset library is a separate question.
- **List of Ads with ad creatives** — Ads with creative detail already attached, shaped by Ad creative columns. Ask which creative ran on the ad without assembling that link yourself.
- **List of Activities** — The account's change history, optionally bounded with Updated since. Ask what was edited in the window, then how Reports and Insights moved in the same dates.
- **List of Business invoices** — What was billed for the Businesses you selected, using Billing start date, Billing end date, Issue start date, and Issue end date. Ask how those bills compare with spend in Reports and Insights.

## Why export Facebook Ads to Claude — real life cases

These are the Facebook Ads questions that stop needing another download once a flow is refreshing for Claude.

- **Ask what moved since the previous day**

  Set Report type to Reports and Insights and Split data by period to Daily. Under Metrics and dimensions, keep spend, impressions, clicks, CTR, CPC, and CPM, and add Breakdowns for placement, device, age, or geography. Claude can say which slice changed, and the next run keeps that answer current.

- **Find the creative that rode on the ad**

  List of Ads with ad creatives already attaches creative detail to each ad, and Ad creative columns decides which attributes come along. When the question is the library itself, refresh List of Ad creatives on its own flow. Coupler.io's Join can stitch that library to List of Ads before Claude has to guess which asset ran.

- **Read new sponsored leads in the same conversation**

  List of Sponsored Leads depends on the Pages you select, and Lead generation forms is optional when only some forms matter. Ask Claude which page the submission came from and which form collected it. An interval of every 15 minutes means the answer is not waiting on someone to download the lead file.

- **Set the invoice next to reported spend**

  List of Business invoices uses Businesses plus the date filters, not the report period. Set Billing start date and Billing end date, or Issue start date and Issue end date when finance means the issue window. Ask Claude how those amounts sit against Reports and Insights for the same Ad accounts.

- **See what changed in the account**

  List of Activities is the change history. Updated since keeps it to edits after a boundary such as *last month*. Ask Claude what changed in that window, and whether Reports and Insights moved with the edit.

- **Make attribution agree before you compare accounts**

  Attribution settings offers Use ad group settings, which follows each ad set, or Specify manually, which puts one rule on every Ad account in the flow. Action attribution windows then decides how long an action still counts. Ask Claude to compare accounts only after those two fields agree.

- **Ask across a year without rebuilding the file**

  Start date accepts *this year*, *last year*, *this month*, *last month*, *days ago*, or `{{365daysago}}` for a trailing year. End date stays relative so the window moves on by itself. Ask Claude how Reports and Insights for *this year* compare with *last year* on the same Breakdowns.

- **Ask about setup and results together**

  List of Campaigns and List of Ad sets describe how the account is put together, and Reports and Insights describes what those campaigns did. Coupler.io's Join stitches a structure list to the insights before Claude sees them. Filters can drop campaigns you do not want included in that question.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

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
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

