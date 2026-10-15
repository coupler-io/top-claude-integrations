---
title: Connect LinkedIn Public Data to Claude with Coupler.io
slug: connect-linkedin-public-data-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-linkedin-public-data-to-claude.md
source: LinkedIn Company Pages
destination: Claude
meta_title: Connect LinkedIn Public Data to Claude with Coupler.io
meta_description: Ask Claude about LinkedIn Company Pages follower gains, video views, and audience demographics and get plain-language answers.
---

![LinkedIn Public Data](https://static.coupler.io/importers/linkedin.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect LinkedIn Public Data to Claude with Coupler.io

LinkedIn's company-page screens split lifetime totals, follower mix, and video watch time into places that resist a single question. Asking which page gained followers, which post held viewers, and how long those viewers watched means hopping across report types the native UI never lines up. Coupler.io exports LinkedIn Company Pages on a schedule so Claude can take those questions in ordinary language. You choose the pages, one report type, a rolling date window, a breakdown, and the view metrics. Deprecated share and UGC report types remain selectable, and the current page and post report types are the ones worth asking about. After the first run, a question about Views or Time viewed (ms) is something you type, rather than a file you download.

## How to export LinkedIn Public Data company data to Claude

The wizard covers fourteen LinkedIn Company Pages report types. Eight are current: Page: lifetime overview, Page: cumulative posts performance, Page: follower gains trend, Page: follower demographics insights, Page: audience demographics insights, Post: individual posts lifetime performance, Post: video performance, and Post: social reactions & comments count. Six are deprecated and still listed: Posts: shares insights (deprecated), Posts: UGC posts insights (deprecated), Page: shares lifetime overview (deprecated), Time-based (deprecated), Lifetime total statistic (deprecated), and Post: individual posts performance (deprecated).

### Step 1. Basic settings

- **Pages** — Select the company pages Claude should be able to answer about. Several pages can ride in one flow, each still tied to the page it came from.
- **Report type** — Choose one category for this flow. The fourteen names, including the six deprecated ones, are written out in the data section below.

### Step 2. Report period

- **Start date** — Open the window with a rolling choice. *days ago* suits a short lookback, and *last year* gives Claude a full prior year. A trailing year of page history can also be entered as `{{365daysago}}`.
- **End date** — Close the window on *this month* when you want the current month included, on *last month* for a finished month, or on *this year* for a year-to-date read. A relative close moves forward on the next run.
- **Split data by period** — Slice that same window into repeated periods so Claude can be asked how follower gains or post views moved, not only where they stood at the end.

### Step 3. Dimensions

- **Breakdown dimension** — The coarser cut offered for the report type you picked. On a demographics report, this is the split Claude will use when you ask who the page reached.
- **Dimension** — A further cut beside the breakdown, when the report type offers one. Leave it only as wide as the question you plan to ask.

### Step 4. Metrics

- **Metrics** — Pick from Views, Viewers, Time viewed (ms), and Time viewed for views (ms). Claude can speak only to the metrics you keep, so a video question should include both time-viewed measures if you care how long people stayed.

### Step 5. Blend and transform data

- **Column management** — Hide LinkedIn columns nobody will ask about, rename Time viewed (ms) and Time viewed for views (ms) into labels the team says aloud, and place Views next to Viewers.
- **Join** — Coupler.io's Join matches a Page: lifetime overview flow to Post: individual posts lifetime performance on the shared page before Claude receives the combined rows.
- **Append** — Coupler.io's Append stacks Page: follower gains trend from each selected company page into one series before Claude is asked which page added people.
- **Aggregate** — Coupler.io's Aggregate rolls a Split data by period export up to a coarser grain before Claude summarizes the quarter.
- **Custom SQL** — Write a query that keeps posts with a reaction count you care about, then hand that smaller result to Claude.

### Step 6. Claude destination

Company-page figures become available to ask about in the product step **Setup Claude integration**. The step has two tabs and no extra fields.

- **Chat and Cowork** — Register a Claude account so company-page questions have a place to land. Click Connect using the published Coupler.io connector link https://l.rw.rw/couplerio-claude-connector. Team or Enterprise plans accept that Connect only from an admin. The Coupler.io login is another Connect click, made from the Connectors menu.
- **Claude Code** — Paste the command below into a new Claude Code session. Restart that session after the paste, sign in when the browser opens, and click Authorize.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Set the company-page flow to refresh every 15 minutes, or choose an hourly, daily, weekly, or monthly rhythm. Each run updates the LinkedIn figures Claude answers from, using the report type and date window you saved.

### Bonus: or just ask the AI Agent to build it for you

Company-page importers can be drafted by the Coupler.io AI Agent, opened from the sidebar on the right side of the Coupler.io app. Claude is who you ask once the flow exists. ChatGPT and Cursor are other products entirely.

> "Export Page: follower gains trend and Post: video performance for the selected pages from last year through today, with Views and Time viewed (ms), and send the result to Claude."

You still do three things yourself:

1. Connect the LinkedIn Company Pages account. The sign-in stays with you.
2. Choose the **Pages** that belong in the flow.
3. Link Claude yourself, on Chat and Cowork or by authorizing Claude Code.

## What data can you export from LinkedIn Public Data to Claude with Coupler.io?

Fourteen categories are available, one report type per flow. When a question needs two of them, Coupler.io's Join can stitch those flows before Claude reads them together.

- **Page: lifetime overview** — Gives Claude the standing lifetime picture of the company page, so a question about overall page performance is not trapped inside a short date slice.
- **Page: cumulative posts performance** — Lets Claude talk about how the page's posts have added up over time, which is the right category when you care about the body of content rather than one update.
- **Page: follower gains trend** — The category for "are we gaining followers, and when did that change?" Pair it with Split data by period so Claude can describe the shape of the trend.
- **Page: follower demographics insights** — Asks Claude who follows the page, along the Breakdown dimension and Dimension you selected.
- **Page: audience demographics insights** — Asks Claude about the wider audience as distinct from followers, using those same dimension fields.
- **Post: individual posts lifetime performance** — One row of lifetime results per post, so Claude can name the updates that carried the page rather than averaging them away.
- **Post: video performance** — The video category, where Views, Viewers, Time viewed (ms), and Time viewed for views (ms) tell Claude which clips people actually watched.
- **Post: social reactions & comments count** — Gives Claude the reaction and comment totals on each post, which is the conversation side of performance rather than the view side.
- **Posts: shares insights (deprecated)** — Deprecated, and still selectable. Prefer the current post report types when you want Claude's answers to rest on the maintained categories.
- **Posts: UGC posts insights (deprecated)** — Deprecated. It remains in the report type list for older flows, and new questions belong on the current post categories.
- **Page: shares lifetime overview (deprecated)** — Deprecated lifetime share overview. Keep it only for a flow you already depend on; point new questions at Page: lifetime overview.
- **Time-based (deprecated)** — Deprecated. Use Start date, End date, and Split data by period on a current report type when Claude needs a time cut.
- **Lifetime total statistic (deprecated)** — Deprecated lifetime total. Page: lifetime overview is the current category for a standing page summary.
- **Post: individual posts performance (deprecated)** — Deprecated per-post performance. Post: individual posts lifetime performance is the current category for a post-by-post lifetime read.

## Why export LinkedIn Public Data to Claude — real life cases

A social team can put the questions below to Claude once company-page history is refreshing on a schedule.

- **Name the posts that earned a lifetime audience**

  Post: individual posts lifetime performance is the category that keeps each update intact. Ask Claude which posts collected Views and Viewers across their lifetime, and which ones faded. Because the flow is scheduled, the answer can use *this month* without another export.

- **See whether a video was watched or merely opened**

  On Post: video performance, include Views, Viewers, Time viewed (ms), and Time viewed for views (ms). Claude can then separate a clip people started from a clip they stayed with. That distinction is buried when video time lives in a different screen from post totals.

- **Explain a follower gains trend**

  Page: follower gains trend plus Split data by period lets Claude describe when the page added followers. Ask whether gains clustered in *last month* or were spread across *this year*. The Pages field decides which company pages are allowed into that answer.

- **Describe who follows the page**

  Page: follower demographics insights uses Breakdown dimension and Dimension as the cuts. Ask Claude which slice of followers dominates, and whether a second dimension changes the story. You choose the cuts in the wizard; Claude answers inside them.

- **Separate followers from the wider audience**

  Page: audience demographics insights is the wider group, and Page: follower demographics insights is the people who followed. Coupler.io's Join can line those two categories up before Claude compares them. The question "does our audience look like our followers?" then has both sides.

- **Take a lifetime read of the page**

  Page: lifetime overview gives Claude the page's standing picture, and Page: cumulative posts performance adds how the content has accumulated. Ask for both when a quarterly review needs the page and its posts in one reply. Keep each report type in its own flow, then join them.

- **Count reactions and comments per post**

  Post: social reactions & comments count is the category for conversation volume. Ask Claude which posts drew reactions, which drew comments, and whether those posts also led Views on a joined lifetime flow. The ampersand is part of the report type name in the product.

- **Leave the deprecated report types out of new questions**

  Posts: shares insights (deprecated), Posts: UGC posts insights (deprecated), Page: shares lifetime overview (deprecated), Time-based (deprecated), Lifetime total statistic (deprecated), and Post: individual posts performance (deprecated) still appear in Report type. Ask Claude from the current categories unless an older flow must keep running. New pages should start on the maintained report types.

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
- [Connect Microsoft Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-microsoft-ads-to-claude.md)
- [Connect QuickBooks to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-quickbooks-to-claude.md)
- [Connect Shopify to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md)
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

