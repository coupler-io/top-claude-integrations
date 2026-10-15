---
title: Connect TikTok Ads to Claude with Coupler.io
slug: connect-tiktok-ads-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md
source: TikTok Ads
destination: Claude
meta_title: Connect TikTok Ads to Claude with Coupler.io
meta_description: Connect Basic campaign report, GMV Max campaign report, and Audience ad report from TikTok Ads so Claude can compare them for you.
---

![TikTok Ads](https://static.coupler.io/importers/tiktok.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect TikTok Ads to Claude with Coupler.io

TikTok Ads Manager is comfortable inside one advertiser and one tab. It gets clumsy when an Upgraded Smart+ creative, a GMV Max campaign, and an audience cut that includes the dimension Ac need to be asked about together. Coupler.io holds the report type, the ad accounts, and, for GMV Max, the stores, then refreshes them on a cadence you pick. Claude is where the question goes after that refresh. Audience, catalog, asset, and search breakdowns stay attached to the metrics you selected in the wizard.

## How to export TikTok Ads data to Claude

Eighteen categories sit in this wizard: basic campaign, ad group, ad, and advertiser reports, both Upgraded Smart+ ad reports, GMV Max, the object lists Campaigns and Ads, four audience reports, both playable reports, and four Dynamic Showcase Ads (DSA) reports. Each flow uses one of them.

### Step 1. Basic settings

- **Report type** — the category Claude will answer from. The eighteen names are in the data section, from Basic campaign report through Dynamic Showcase Ads (DSA) ad group report.
- **Ad accounts** — the advertisers included in this flow. Questions stay inside that set.
- **Stores** — required when the report is GMV Max. Pick the stores whose GMV Max campaign report you intend to ask about.

### Step 2. Report period

- **Start date** — where TikTok Ads history should begin. The relative picker offers *days ago* or *this month*, and also *last month*, *this year*, and *last year*. The macro `{{365daysago}}` is a year-long lookback that keeps moving.
- **End date** — the closing bound, using that same relative picker so the window does not freeze on the day you built the flow.
- **Split data by period** — whether Claude sees a total or a series. Set the grain that matches the question.

### Step 3. Metrics and dimensions

- **Metrics** — the measures for the report type you chose. Keep the list to what you will actually ask about.
- **Audience dimensions** — Gender, Age, Country code, Province, DMA region, Behavior, Device brand, Ac, Language, Platform, Interest category, Interest category second level, Interest category third level, Interest category fourth level, Placement, and Contextual tag. Leave the label Ac as printed.
- **DSA dimensions** — Catalog id, Product set id, Product id, and Sku id, for the Dynamic Showcase Ads report types.
- **Targeting dimension** — Country code and Ad type, on report types that offer this field.
- **Asset dimension** — Component name, Customer event type, Event source id, Image id, Minis id, Page id, Post id, Room id, and Video material id.
- **Search dimension** — Search terms.

### Step 4. Advanced settings

- **Advanced filters** — narrow the rows Claude will reason over. The conditions on offer follow the report type.

### Step 5. Blend and transform data

- **Column management** — hide TikTok Ads columns the question will never use, rename the opaque ones, and put advertiser and campaign identifiers where you will look first.
- **Join** — Coupler.io's Join stitches a Basic campaign report to an Audience campaign report before Claude is asked to compare them. A separate flow per report type is equally valid, and the wording of your question is what relates them.
- **Append** — Coupler.io's Append stacks rows from more than one Ad account when the report type matches, so Claude can be asked which account diverges.
- **Aggregate** — Coupler.io's Aggregate rolls a fine Split data by period into a coarser total before Claude sees that total.
- **Custom SQL** — a query can reshape metrics next to the dimension Ac when the named transformations stop short. Ask Claude about that result.

### Step 6. Claude destination

Claude does not ask you to fill a destination form. **Setup Claude integration** is the product step, and the work is on two tabs.

- **Chat and Cowork** — You register a Claude account on this TikTok Ads tab. Open the Coupler.io connector once the advertisers are chosen and click Connect (https://l.rw.rw/couplerio-claude-connector) before you schedule GMV Max. When the plan is Team or Enterprise, only an admin can complete the TikTok Ads connection. Back in the Connectors menu, after the report type is set, click Connect a second time and log in to Coupler.io so this advertiser flow is the one signed in.
- **Claude Code** — Use a fresh session for TikTok Ads. Paste the following command into that session, restart that session, complete the browser sign-in, and click Authorize before you ask about ad groups or GMV Max.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Choose every 15 minutes, or step down to hourly, daily, weekly, or monthly. Each run refreshes the dataset Claude answers from, which is what a later question about a GMV Max campaign report or an Audience ad report is reading.

### Bonus: or just ask the AI Agent to build it for you

Most of the wizard can start from a sentence. Inside the Coupler.io app, the right sidebar is the Coupler.io AI Agent, a different assistant from Claude, from ChatGPT, and from Cursor.

> Build an Audience ad report using Age, Country code, and Ac for my ad accounts over last month, and load the result to Claude.

You still handle the sign-in and the scope yourself:

1. Connect TikTok Ads yourself. The TikTok sign-in stays on your side.
2. Choose the **Ad accounts** to include, and the **Stores** to include when the report is GMV Max.
3. Connect Claude for those advertisers through the Chat and Cowork connector, or with a Claude Code authorization.

Those three TikTok Ads steps remain yours.

## What data can you export from TikTok Ads to Claude with Coupler.io?

TikTok Ads exposes eighteen categories. Each flow is built around a single category. When an answer needs two categories, Coupler.io's Join can stitch them before Claude sees the rows.

- **Basic campaign report** — ask Claude how campaigns compare for the ad accounts you included, at the grain you set with Split data by period.
- **Basic ad group report** — go one level down and ask which ad groups inside those campaigns are carrying the result.
- **Basic ad report (Upgraded Smart+ by ad)** — ask about Upgraded Smart+ performance with one row orientation per ad.
- **Basic ad report (Upgraded Smart+ by creative)** — ask the same family of questions with the row oriented by creative, so a creative can be separated from the ad that ran it.
- **GMV Max campaign report** — ask about GMV Max only after Stores and Ad accounts are both the ones you intend. A basic campaign report does not stand in for this category.
- **Campaigns** — the campaign objects themselves. Ask Claude about structure and status when the question is the object, not the performance report.
- **Ads** — the ad objects. Ask which ads exist in the accounts you selected, then relate them to a performance flow if you need numbers attached.
- **Basic advertiser report** — ask at advertiser level, across the Ad accounts on the flow, before you drill into campaigns.
- **Audience campaign report** — ask how a campaign splits on Audience dimensions, including Ac, Age, Gender, or Country code.
- **Audience advertiser report** — the same style of audience question rolled to the advertiser.
- **Audience ad report** — ask which ad changes shape once you cut it by Platform, Placement, Language, or Ac.
- **Audience ad group report** — ask the audience question at ad group level when the campaign total is too coarse.
- **Playable Ad report** — ask about playable ads without a country cut.
- **Playable Ad report by country** — ask which country rows disagree with the unsplit playable report.
- **Dynamic Showcase Ads (DSA) campaign report** — ask how a DSA campaign looks once Catalog id or Product set id is on the row.
- **Dynamic Showcase Ads (DSA) report** — the general DSA performance category. Ask about Product id or Sku id here when the campaign rollup hides the product.
- **Dynamic Showcase Ads (DSA) advertiser report** — ask the DSA question at advertiser level for the accounts on the flow.
- **Dynamic Showcase Ads (DSA) ad group report** — ask which ad group inside a showcase campaign is tied to a product set.

## Why export TikTok Ads to Claude — real life cases

TikTok buyers use Claude for comparisons that Ads Manager keeps on separate screens.

- **Hold campaign, ad group, and advertiser apart**

  Basic campaign report, Basic ad group report, and Basic advertiser report are three flows. Ask Claude where an advertiser's totals disagree with the ad group rows underneath. Campaigns and Ads are the object lists when you need the structure named before you talk about performance.

- **Separate Upgraded Smart+ by ad and by creative**

  Basic ad report (Upgraded Smart+ by ad) and Basic ad report (Upgraded Smart+ by creative) are different report types. Ask Claude which creative is carrying an ad, and keep the two flows apart unless Coupler.io's Join has stitched them. Metrics on each flow should be the ones you are willing to cite.

- **Point GMV Max at the right stores**

  GMV Max campaign report reads Stores as well as Ad accounts. Ask Claude about those store-backed campaigns only after the stores in scope are the ones you mean. Start date and End date still bound the window, using relatives such as *last month* or *this year*.

- **Cut audience reports by Ac and the neighboring dimensions**

  On an Audience ad report or an Audience campaign report, set Audience dimensions and keep the label Ac beside Age, Gender, Country code, or Platform. Ask Claude how those slices differ. Audience ad group report and Audience advertiser report answer the same kind of question at another level.

- **Ask which catalog product sits on a DSA row**

  Dynamic Showcase Ads (DSA) report, Dynamic Showcase Ads (DSA) campaign report, Dynamic Showcase Ads (DSA) advertiser report, and Dynamic Showcase Ads (DSA) ad group report are four categories. Put Catalog id, Product set id, Product id, or Sku id on the row through DSA dimensions, then ask Claude which product set belongs with which campaign. Keep the advertiser-level DSA flow separate when the question is the account rather than one ad group.

- **Review playable ads with and without a country cut**

  Playable Ad report and Playable Ad report by country answer different questions. Ask Claude which country rows disagree with the unsplit playable report. Targeting dimension can add Country code or Ad type on report types that show that field.

- **Look up search terms and the asset that ran**

  Search dimension is the field for Search terms. Asset dimension is where Component name, Video material id, Post id, Room id, Page id, and Image id are chosen, along with the other asset ids the wizard lists. Ask Claude which search term or video material sits with the metrics on the report type you selected.

- **Trim the rows before you ask**

  Advanced filters remove rows you do not want in the answer. Ask a narrow question — one advertiser's Basic ad group report, a short Start date to End date — and the reply stays inside that window. Split data by period tells Claude whether the rows are a total or a series.

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
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

