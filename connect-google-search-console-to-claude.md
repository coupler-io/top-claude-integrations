---
title: Connect Google Search Console to Claude with Coupler.io
slug: connect-google-search-console-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-search-console-to-claude.md
source: Google Search Console
destination: Claude
meta_title: Connect Google Search Console to Claude with Coupler.io
meta_description: Ask Claude about Search results performance, Discover performance, and URLs index performance for the Search Console sites you choose.
---

![Google Search Console](https://static.coupler.io/importers/google-search-console.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Google Search Console to Claude with Coupler.io

Google Search Console keeps queries, search appearance, Discover, News, and index coverage in separate reports, and the performance view is easy to outgrow once a question spans more than one site. Coupler.io exports Google Search Console so Claude can answer from the sites and the report type you save. Five report types are available, and Search results performance is the default. You pick the sites, the report type, the dates, the dimensions, and, for the index report, the URLs to inspect. Filters, search type, and aggregation stay on the flow, so the question you ask matches the cut you saved.

## How to export Google Search Console data to Claude

This wizard covers five report types: Search results performance, Search results performance by appearance, Discover performance, Google News performance, and URLs index performance. Search results performance is included as the default.

### Step 1. Basic settings

- **Sites** — Choose the Search Console sites this flow should cover. Claude's answers stay inside that set.
- **Report type** — One report type per flow. The five are Search results performance, Search results performance by appearance, Discover performance, Google News performance, and URLs index performance.
- **Inspection URLs** — Used with the index report. Enter one URL per line so URLs index performance inspects those addresses and nothing you forgot to list.

### Step 2. Report period

- **Start date** — The first day of the performance window. *last year* reaches the prior year, and *days ago* keeps a short recent slice. Relative starts keep their distance from today on every refresh.
- **End date** — Where the performance window stops. *this month* includes the month in progress, *last month* is a month that has closed, and *this year* carries the year to date.

### Step 3. Dimensions

- **Dimensions** — Date, Query, Page, Country, and Device are the dimension names. Which of them apply depends on the report type, so a Discover flow will not offer the same set as Search results performance.
- **Filters by dimensions** — Narrow Country, Device, Page, Query, or Search appearance. The operators are Contains, Equals, Does not contain, Does not equal, Including Regex, and Excluding Regex.

### Step 4. Advanced settings

- **Search results type** — Start from web, and add News, Image, or Video when those surfaces belong in the question. On the appearance report, Discover and Google News are available as well.
- **Aggregate data by** — Roll the rows by Page, by Property, or leave the choice on Auto.
- **Data state** — Set how settled the Search Console rows should be before Claude treats the figures as ready to answer from.

### Step 5. Blend and transform data

- **Column management** — Rename Query and Page to the words your SEO team uses, and drop device columns when the question is only about countries.
- **Join** — Coupler.io's Join attaches URLs index performance to Search results performance on the page URL before Claude explains a change in queries.
- **Append** — Coupler.io's Append stacks Discover performance beneath Google News performance before Claude compares those two surfaces.
- **Aggregate** — Coupler.io's Aggregate sums daily Query rows up to a month before Claude describes the trend.
- **Custom SQL** — Write a tighter query on Query after the dimension filters, and send that result to Claude.

### Step 6. Claude destination

Search Console rows become available to ask about in **Setup Claude integration**. Two tabs cover the step, and there is no extra destination form.

- **Chat and Cowork** — Register a Claude account, then click Connect through Coupler.io's connector listing https://l.rw.rw/couplerio-claude-connector. Someone on a Team or Enterprise plan needs to be an admin to make that click. Coupler.io login is a second Connect, performed in the Connectors menu.
- **Claude Code** — A new session is the starting point on the Claude Code tab. Paste the command below into it. Restart follows the paste, the browser handles sign-in, and Authorize closes the step.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Pick how often the sites refresh: every 15 minutes at the shortest interval, and otherwise hourly, daily, weekly, or monthly. Questions about queries and indexed URLs then use the Search Console rows from that refresh.

### Bonus: or just ask the AI Agent to build it for you

Search Console flows can be handed to the Coupler.io AI Agent. You will find it in the sidebar on the right, inside the Coupler.io app. Claude is reserved for questions after the flow runs. ChatGPT and Cursor are not part of building the importer.

> "Build Search results performance by Query and Page for last year, keep the brand query with Equals, and load the result to Claude."

You still handle:

1. Connect the Google Search Console account. Signing in remains yours.
2. Choose the **Sites** that are in scope.
3. Complete the Claude link personally with Chat and Cowork, or finish Claude Code authorization first.

## What data can you export from Google Search Console to Claude with Coupler.io?

Five categories are available, and Search results performance is one of them. It is the default report type, which is easy to miss beside the other four. Run a separate flow for each report type you want Claude to know. Coupler.io's Join can stitch Search results performance to URLs index performance ahead of Claude.

- **Search results performance** — The default performance category. Ask Claude about queries, pages, countries, and devices for the sites and dates you saved, including a web, News, Image, or Video cut from Search results type.
- **Search results performance by appearance** — The same performance idea, split by how the result looked. Search appearance can be filtered, and this is the report where Discover and Google News show up under Search results type.
- **Discover performance** — Ask Claude how the selected sites did in Discover for the start and end dates, with the dimensions that report type allows.
- **Google News performance** — Ask Claude about Google News on those sites, separate from web search and from Discover.
- **URLs index performance** — The index category. Inspection URLs takes one URL per line, and Claude can then speak to the index status of the addresses you listed.

## Why export Google Search Console to Claude — real life cases

Search Console already stores the queries and the index status. The cases below are the questions Claude should be able to answer once a flow is refreshing.

- **Ask which queries led the window**

  Search results performance with Dimensions set to Query and Page is the everyday cut. Ask Claude which queries led for *last month*, and which Page held them. Aggregate data by Page when you want one row per page, or by Property when the site should stay rolled up. Auto is there when you want the product to choose.

- **See whether appearance changed the story**

  Search results performance by appearance adds Search appearance to the question. Filter it with Equals or Contains, or exclude a pattern with Excluding Regex. Ask Claude whether a given appearance, rather than the query text alone, explains the change between *this year* and *last year*.

- **Ask what Discover did with a page**

  Discover performance is its own report type. Choose the Sites, set Start date to *days ago* for a recent slice, and ask Claude how those pages behaved in Discover. Keep this flow separate from Search results performance so the figures are not mixed before you mean them to be.

- **Ask about Google News on its own**

  Google News performance covers News. Search results type can also add News, Image, or Video onto a web performance flow, and the appearance report can include Discover and Google News. Ask Claude about the News report type when you want that surface alone, and use Coupler.io's Append if you later want it stacked with Discover performance.

- **Check the URLs you care about indexing**

  URLs index performance reads the Inspection URLs you enter, one URL per line. Ask Claude which of those URLs are in the index and which need a closer look. Coupler.io's Join can attach that result to Search results performance on the page URL before Claude connects a query drop to an index change.

- **Keep a brand query, or drop a pattern**

  Filters by dimensions work on Country, Device, Page, Query, and Search appearance. Contains, Equals, Does not contain, Does not equal, Including Regex, and Excluding Regex are the operators. Ask Claude about a Query filter that uses Including Regex for a product family, and a second pass that uses Does not contain to drop an unrelated term.

- **Split web results from video results**

  Search results type starts at web and can add News, Image, or Video. Ask Claude to compare a web flow with a Video flow for the same Sites and the same *this month* window. Device and Country remain available as dimensions when the report type supports them, alongside Date, Query, and Page.

- **Decide whether the rows are ready to trust**

  Data state is where you say how settled the extract should be before Claude answers. Pair it with End date on *last month* when you want a closed month, and with a daily or weekly schedule so the next run picks up the following period. The Sites field still decides which properties are allowed in.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
- [Connect Google Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md)
- [Connect Google Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-analytics-to-claude.md)
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

