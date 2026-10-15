---
title: Connect Facebook Page Insights to Claude with Coupler.io
slug: connect-facebook-page-insights-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md
source: Facebook Page Insights
destination: Claude
meta_title: Connect Facebook Page Insights to Claude with Coupler.io
meta_description: "Connect Page: followers daily snapshot and Post: reels lifetime performance from Facebook Page Insights so Claude can compare those pages."
---

![Facebook Page Insights](https://static.coupler.io/importers/facebook.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Facebook Page Insights to Claude with Coupler.io

Facebook's page screens are built around the page you have open, which is a hard place to ask how a follower snapshot, a reel's lifetime, and a video's daily line fit together. Coupler.io takes the pages you select and the single report type you select, and it keeps that selection refreshing. Claude can then be asked which posts are hidden, which permalink belongs to a message, or how performance insights compare with the overview. Post columns travel with the post reports, and the video publish window is a pair of dates you set once. Daily and monthly splits live on the flow, so the grain of the question does not depend on whichever toggle was last clicked in the page UI.

## How to export Facebook Page Insights data to Claude

Six categories are in this wizard. Three describe the page: Page: general overview, Page: performance insights, and Page: followers daily snapshot. Three describe the content: Post: posts lifetime performance, Post: reels lifetime performance, and Post: video daily performance.

### Step 1. Basic settings

- **Pages** — the Facebook pages this flow includes. Claude's answers stay inside that list.
- **Report type** — one of the six categories. A second category means a second flow.

### Step 2. Report period

- **Start date** — where the page window opens. Relative choices are *days ago*, then *this month*, *last month*, *this year*, or *last year*. A year of page history can be written as `{{365daysago}}`.
- **End date** — the closing bound, with the same relative choices, so the next refresh does not keep yesterday's end date.
- **Created after** — on this report period step, the lower bound on when the content was created.
- **Created before** — the matching upper bound on the report period step. The same titles appear again later as the video publish window.
- **Split data by period** — Daily or Monthly. Pick the grain you want Claude to reason over.

### Step 3. Metrics

- **Metrics** — the measures for the report type you selected. Keep the ones you will cite and drop the rest.

### Step 4. Metrics and dimensions

- **Metrics and dimensions** — two fields on this step share the title Metrics and dimensions. This one is the metric picker for the selected report type.
- **Metrics and dimensions** — the dimension picker, under that same title. Choose the breakdowns the report type allows. There is no second name to look for.

### Step 5. Advanced filters

- **Created after** — the start of the video publish window. Set it when the question is about when a video was published, using the same relative dates as the report period.
- **Created before** — the end of that video publish window.

### Step 6. Advanced settings

- **Post columns** — attributes that travel with post, reel, and video rows. The list includes Message, Call to action, Attachments, Created time, Permalink URL, Posted by, Status type, Is published, Is hidden, Promotion status, and Instagram eligibility, plus the rest of the post-column list.
- **Data behavior** — for a page report, choose Latest data or Track changes over time. Latest data is the current picture. Track changes over time is the path those page rows took.

### Step 7. Blend and transform data

- **Column management** — hide Facebook Page Insights columns you will not cite, rename the rest into words you would actually say, and keep Message beside Permalink URL.
- **Join** — Coupler.io's Join stitches Page: general overview to Post: posts lifetime performance before Claude sees a combined result. Run the page report and the post report as two flows when you want the question itself to do the relating.
- **Append** — Coupler.io's Append stacks rows for every Page on the flow when they share a report type, and Claude answers across those pages.
- **Aggregate** — Coupler.io's Aggregate rolls Daily rows up to a monthly figure before Claude is asked about the month.
- **Custom SQL** — a query can reshape post columns when column management is not enough. Ask Claude about that reshaped result.

### Step 8. Claude destination

Nothing here is a destination field. The product step is **Setup Claude integration**, with two tabs.

- **Chat and Cowork** — Registration of a Claude account comes first for whoever will ask about these pages. Open the Coupler.io connector after the pages are selected and click Connect (https://l.rw.rw/couplerio-claude-connector) so the page list can be asked about. On a Team or Enterprise plan, only an admin can finish the Facebook page connection. Stay inside the Connectors menu until the page list is confirmed, click Connect once more, and log in to Coupler.io before any page question.
- **Claude Code** — Open a new session for this Facebook page flow. Paste the command, restart the session afterward, walk through the browser sign-in, and click Authorize.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 9. Schedule

The schedule offers every 15 minutes, and also hourly, daily, weekly, and monthly. Whenever it fires, it refreshes the dataset Claude answers from for the pages on this flow, so a Monday follower question reads that run.

### Bonus: or just ask the AI Agent to build it for you

If you would rather describe the flow than click every control, open the Coupler.io AI Agent in the right sidebar of the Coupler.io app. That sidebar assistant is neither Claude nor ChatGPT nor Cursor.

> Set up Page: performance insights and Post: posts lifetime performance for the pages I choose, keep Message and Permalink URL, and send the result to Claude.

The agent can fill the page and post fields from that sentence. You still complete these yourself:

1. Connect Facebook Page Insights. Signing in to Facebook stays on your side.
2. Choose the **Pages** Claude is allowed to read.
3. Connect Claude for those pages with the Chat and Cowork connector, or by completing Claude Code authorization.

The page list and the Claude connection are the parts you still sign.

## What data can you export from Facebook Page Insights to Claude with Coupler.io?

Facebook Page Insights is six categories wide. Keep each category on its own flow. Coupler.io's Join is how a page category gets stitched to a post category before Claude sees either.

- **Page: general overview** — the wide view of the pages you ticked. Ask Claude what that overview contains before you open a deeper report.
- **Page: performance insights** — the performance companion to the overview. Ask what moved for those same pages over the start and end dates you set.
- **Page: followers daily snapshot** — follower counts at Daily or Monthly grain. Ask whether followers stepped up, or only look larger once the split is Monthly.
- **Post: posts lifetime performance** — lifetime figures for posts, with whichever Post columns you included. Ask which published posts are hidden, or which Message belongs to a Permalink URL.
- **Post: reels lifetime performance** — lifetime figures for reels, separate from the posts report. Ask about Status type, Instagram eligibility, or Promotion status when those columns are on the row.
- **Post: video daily performance** — daily video rows. Ask about videos whose publish dates fall inside the Created after and Created before window on Advanced filters.

## Why export Facebook Page Insights to Claude — real life cases

Page managers use Claude when the question crosses the page, the post, the reel, and the video.

- **Start from the overview, then go deeper**

  Page: general overview is the wide view of the pages selected under Pages. Ask Claude what that overview shows for *this month* or *last month* before you open anything narrower. One flow is this report type only.

- **Ask what performance insights add**

  Page: performance insights is the performance companion to the overview. Ask Claude what moved for those same pages between Start date and End date. Coupler.io's Join can stitch the overview to the insights first, or you can ask Claude to relate two flows.

- **Watch followers at the grain you mean**

  Page: followers daily snapshot with Split data by period set to Daily or Monthly is how you ask whether followers actually stepped up. A Monthly split can make a slow week look like a jump. Set the dates with a relative window such as *last month* so the question stays current after the next refresh.

- **Identify posts by message and link**

  Post: posts lifetime performance plus Post columns such as Message, Permalink URL, Posted by, Is hidden, and Is published gives Claude something concrete to point at. Ask which published posts are hidden, or which message belongs to a permalink. Call to action, Attachments, Created time, Status type, Promotion status, and Instagram eligibility are on that same list, along with the rest of the post-column list.

- **Keep reels off the posts report**

  Post: reels lifetime performance is its own lifetime category. Ask Claude about reels on their own, including Status type or Instagram eligibility if you included those Post columns. Promotion status is in the same column list when you need to know a reel was promoted.

- **Bound videos by when they were published**

  Post: video daily performance uses Created after and Created before on the Advanced filters step as the video publish window. Ask Claude about videos published in that window, with Split data by period on Daily. The report period step has its own Created after and Created before; use the Advanced filters pair when the question is the publish window.

- **Choose a current picture or a change track**

  Data behavior is either Latest data or Track changes over time. Ask Claude for the current picture, or ask what changed, and set the matching option before you rely on the answer. The field applies on the report types that show it.

- **Compare several pages without mixing categories**

  Select every page under Pages, and keep Report type to one category per flow. Ask Claude which page leads on Page: performance insights, and run Post: posts lifetime performance as a second flow when the question turns to individual posts. Coupler.io's Append stacks pages that share a shape; Coupler.io's Join relates different report types before Claude sees them.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
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

