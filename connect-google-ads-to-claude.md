---
title: Connect Google Ads to Claude with Coupler.io
slug: connect-google-ads-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md
source: Google Ads
destination: Claude
meta_title: Connect Google Ads to Claude with Coupler.io
meta_description: Send Google Ads Campaign performance, Keywords performance, and Shopping performance to Claude and ask where the budget went.
---

![Google Ads](https://static.coupler.io/importers/googleadv.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Google Ads to Claude with Coupler.io

Google Ads will show you Campaign performance, or Keywords performance, or a location split, and then it makes you start a new screen when the question crosses those boundaries. Structure lists such as Campaign budgets sit apart from the performance reports. A Custom GAQL query is easy to run once and then lose. Coupler.io connects Google Ads and refreshes whichever one of the 57 report types you selected. Claude answers in plain language from that report, including a query you typed under Custom GAQL. Ad accounts are chosen up front, and the schedule repeats the pull so the next question does not start with another export.

## How to export Google Ads data to Claude

Two wizard steps cover all 57 report types. One flow carries one report type. Ad accounts and Report type decide the pull. The Custom GAQL field appears only when that report type is selected. Every report type is named in the data section below.

### Step 1. Basic settings

- **Ad accounts** — The Google Ads accounts this flow should include. Tick every account the question covers so Claude is not missing a client or a brand.
- **Report type** — Which of the 57 report types this flow refreshes. Performance reports, structure lists, lookup constants, and Custom GAQL are all chosen here, one per flow.
- **Custom GAQL** — Shown only when Report type is Custom GAQL. Write the query that defines the pull. Claude answers from that result the same way it answers from a preset report type.

### Step 2. Report period

- **Start date** — The first day included in this Google Ads report type. Relative options run from *this year* and *last year* through *this month*, *last month*, and *days ago*, and the window keeps moving. Use `{{365daysago}}` when Claude should see a trailing year.
- **End date** — The last day included. A relative end means the following run still reaches the newest days without an edit.
- **Split data by periods** — Date, Day of week, Month, Quarter, Week, or Year. Keywords performance is the exception: it offers Date, Month, Quarter, Week, and Year, and it does not offer Day of week.

### Step 3. Blend and transform data

- **Column management** — Drop Google Ads columns the question will not use, and rename the rest so a report such as Campaign performance reads in plain labels.
- **Join** — Coupler.io's Join stitches Google Ads report types such as Keywords performance and Search query performance together before Claude reads them as one set. Leaving each report type on its own flow, then asking Claude how the answers correspond, is the alternative.
- **Append** — Coupler.io's Append places other advertising sources on the same column layout as Google Ads before Claude is asked for a combined read.
- **Aggregate** — Coupler.io's Aggregate collapses a Date-level Google Ads report into Month or Quarter before Claude talks about the longer stretch.
- **Custom SQL** — Reshape a Google Ads report after the pull, including rows that came from Custom GAQL, and have Claude answer from that reshaped result. This is separate from choosing Custom GAQL as the Report type.

### Step 4. Claude destination

**Setup Claude integration** is the whole destination step. Two tabs, and nothing else to fill in. Pick the tab that matches how you already talk to Claude.

- **Chat and Cowork** — Register a Claude account if the person asking does not have one yet. Open the Coupler.io connector and click Connect (https://l.rw.rw/couplerio-claude-connector). Admin rights are required when the plan is Team or Enterprise. From that same Connectors menu, click Connect again and log in to Coupler.io so the Google Ads flow is available in chat.
- **Claude Code** — Open a fresh session, paste this command, restart that session, complete the browser sign-in, and click Authorize:

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 5. Schedule

Search query performance and Keywords performance go stale quickly, so every 15 minutes, or hourly, fits those report types. Campaigns, Campaign budgets, and Bidding strategies are fine on a daily, weekly, or monthly refresh. After the run, the next Google Ads answer Claude gives is based on that newer pull.

### Bonus: or just ask the AI Agent to build it for you

Describe the Google Ads report type in the Coupler.io app and let the AI Agent, which lives in the right sidebar, draft the flow. Keep that agent apart from Claude, apart from ChatGPT, and apart from Cursor.

> For *this year*, build Keywords performance split by Month, and load the result to Claude.

Three choices remain yours:

1. Connect Google Ads. The Google sign-in stays with you.
2. Choose which **Ad accounts** this flow includes.
3. Connect Claude using the Chat and Cowork connector, or finish Claude Code authorization.

Naming the report type and the date window in the prompt is enough for the agent to draft the rest. If you asked for Custom GAQL, you still review the query it drafted.

## What data can you export from Google Ads to Claude with Coupler.io?

Fifty-seven report types are available. One flow handles one report type. Coupler.io's Join can stitch a performance report to a structure list before Claude sees them, or you can keep each report type as its own flow and ask Claude to relate the answers.

- Performance totals for the questions you ask most weeks. Start with **Campaign performance** and **Keywords performance**. Under those sit **Ad group performance** and **Ad performance**. **Asset group performance** covers the asset-group layer, and **Account performance** is the rollup. Ask how each of those layers contributed.
- **Custom GAQL** is the report type for a cut none of the presets match. The query you write in the Custom GAQL field is what Claude answers from.
- Audience and demographic cuts: **Ad group audience performance**, **Campaign audience performance**, **Age range performance**, and **Gender performance**. Ask which audience, age range, or gender the delivery reached.
- Place and network: **Ad group performance by country**, **Ad group performance by state**, **Ad group performance by region**, **Campaign performance by country**, **Campaign performance by state**, **Campaign performance by region**, **Campaign performance by ad network type**, and **User location performance**. Ask where delivery was targeted, where the user was, and which network type carried it.
- Conversions, installs, and the click itself: **Ad group performance with install conversion**, **Campaign performance with conversion actions name**, **Campaign performance with unique user stats**, **Click performance**, and **Video campaign performance with conversions**. Ask which named conversion or install a campaign or ad group earned, and use the click and video reports when a single total is too coarse.
- Search, display, shopping, and the page after the click: **Display keyword performance**, **Display topics performance**, **Keywordless query**, **Search query performance**, **Placement performance**, **Responsive search ad performance**, **Shopping performance**, **Landing page**, **Expanded landing page**, **Placeholder**, and **Placeholder feed item**. Ask what was searched, which placement or topic was shown, which product or responsive search ad served, which URL received the visit, and which placeholder or feed item sat behind the ad.
- How the account is built, rather than how it scored. **Accounts** and **Campaigns** are the top of the tree. **Ad groups** and **Ads** sit underneath. **Campaign budgets**, **Campaign labels**, and **Campaign criterion** describe the money, tags, and restrictions on a campaign, and **Ad group criterion** does the same one level down. Ask which of those is attached to a campaign you care about.
- Bidding portfolios: **Accessible bidding strategies** and **Bidding strategies**. Ask which strategies the account can use and which ones are defined.
- Lookup lists that turn a code into a word: **Carrier constant**, **Language constant**, **Mobile app category constant**, **Mobile device constant**, **Operating system version constant**, and **Topic constant**. Ask what a carrier, language, device, operating system version, app category, or topic id refers to before anyone changes targeting.
- The remaining catalogs. **Call details** is the call log. **Feed** and **Feed item** are the dynamic-ad inventory. **Labels** is the label library. **User interest** and **User list** are the audience catalogs. Ask which of those the account actually has before you interpret a performance row.

## Why export Google Ads to Claude — real life cases

The Google Ads question worth scheduling is usually the one the interface will not keep on a single screen.

- **Ask which campaigns and keywords did the work**

  Campaign performance, Ad group performance, and Keywords performance can stay as three flows, or Coupler.io's Join can stitch them before you ask. Ask Claude where delivery concentrated and which keywords sat under the ad groups that moved. Split data by periods on Date for a daily read, or on Month for a longer stretch, remembering Keywords performance will not offer Day of week.

- **Read the queries, including the ones with no keyword**

  Search query performance shows what was searched. Keywordless query is the companion for queries that did not match a keyword you bought. Set Start date and End date to *last month*, or open a trailing year with `{{365daysago}}`, and ask Claude which queries spent without a keyword behind them.

- **Separate where you targeted from where people were**

  Campaign performance by country, Campaign performance by state, and Campaign performance by region describe the targeted geography. User location performance describes where the user was. Ask Claude where those two stories disagree, and switch to Ad group performance by country, Ad group performance by state, or Ad group performance by region when the mismatch sits inside one campaign.

- **Ask whether the click earned the page it landed on**

  Landing page and Expanded landing page name the URLs. Responsive search ad performance and Shopping performance say which format sent the click. Once Coupler.io's Join has stitched those report types, ask Claude which URL collected delivery from shopping and which collected it from responsive search ads.

- **Name the conversion, not a blended total**

  Campaign performance with conversion actions name attaches the conversion's name, while Video campaign performance with conversions and Ad group performance with install conversion cover video campaigns and app installs. Click performance is the fine grain when you need the click itself. Ask Claude which named action the campaign earned.

- **Drop into Custom GAQL when the preset is the wrong shape**

  Set Report type to Custom GAQL and the Custom GAQL field appears for the query. Use it when the cut you need is split across the other report types, such as a combination of Campaign performance by ad network type and a structure list. Ask Claude about that result the same way you would ask about Account performance.

- **Ask how the account is assembled**

  Accounts, Campaigns, Ad groups, Ads, and Campaign budgets describe structure and the money set aside. Campaign labels, Campaign criterion, and Ad group criterion say how campaigns and ad groups are tagged and restricted, while Bidding strategies and Accessible bidding strategies say what bidding exists and what this account can use. Ask Claude which campaigns share a label and whether the budget lines up with Campaign performance.

- **Translate a targeting code, a call, or a list**

  Carrier constant, Language constant, Mobile device constant, Operating system version constant, Mobile app category constant, and Topic constant are the lookup lists, and Call details holds the calls. Feed, Feed item, Labels, User interest, and User list are the catalogs behind dynamic ads, labels, and audiences. Ask Claude what a code in Ad group criterion refers to, and which user list or feed item the account actually has.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
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

