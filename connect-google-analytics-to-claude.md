---
title: Connect Google Analytics to Claude with Coupler.io
slug: connect-google-analytics-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-analytics-to-claude.md
source: Google Analytics 4 (GA4)
destination: Claude
meta_title: Connect Google Analytics to Claude with Coupler.io
meta_description: Ask Claude about Google Analytics 4 (GA4) sessions, purchase revenue, and Landing page trends and get plain-language answers.
---

![Google Analytics](https://static.coupler.io/importers/google-analytics.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Google Analytics to Claude with Coupler.io

The Google Analytics interface is built around one property and one exploration at a time, so a plain question about acquisition, revenue, and landing pages becomes a tour of several screens. Coupler.io connects Google Analytics 4 (GA4) so Claude can answer from the metrics and dimensions you actually pick. This wizard has no report type. You choose properties, a date window, and the labels themselves. There are nearly ninety metrics to pick from, and you can attach up to nine dimensions drawn from several hundred. A scheduled refresh holds the answers to that same rolling window, so Claude describes the current property.

## How to export Google Analytics data to Claude

The wizard covers the GA4 properties you select, a start and end date, and the metrics and dimensions you choose. It does not offer a report type. Anything Claude says has to come from the labels you placed on the flow.

### Step 1. Basic settings

- **Properties** — Choose the GA4 properties in scope. This is the only basic setting. There is no report type field beside it.

### Step 2. Report period

- **Start date** — Set the first day Claude should consider. Relative choices include *last year* for the prior year and *days ago* for a short lookback. When you want a trailing year written out, use `{{365daysago}}`.
- **End date** — Set the last day. *this month* keeps the open month, *last month* stops at the month that already closed, and *this year* carries the year to date. A relative end date advances on later runs.

### Step 3. Metrics and dimensions

- **Metrics** — You pick from nearly ninety metrics, limited to the ones the question needs. Sessions, engagement, revenue, events, and ads measures all live in this same list. Claude will not invent a metric you left off.
- **Dimensions** — Up to nine per report, chosen from several hundred. Page, source, geography, device, item, and time labels are all dimensions you opt into here.

### Step 4. Blend and transform data

- **Column management** — Hide GA4 metrics you did not mean to ask about, and keep sessions beside engagement rate so the extra columns stay out of Claude's way.
- **Join** — Coupler.io's Join aligns one property flow that carries organic search with another that carries purchase revenue, matching them on Date, before Claude talks about both.
- **Append** — Coupler.io's Append stacks session rows from two properties before Claude compares those properties.
- **Aggregate** — Coupler.io's Aggregate rolls Hour rows up to Month before Claude answers a quarterly question.
- **Custom SQL** — Filter a query down to one Landing page and one Event name, then send that slice onward to Claude.

### Step 5. Claude destination

**Setup Claude integration** is the whole destination step for a GA4 property. Two tabs, and no further fields.

- **Chat and Cowork** — The person who will question the property registers a Claude account on this tab. Press Connect on the published Coupler.io connector page https://l.rw.rw/couplerio-claude-connector. If the plan is Team or Enterprise, that person must be an admin. One more Connect, from the Connectors menu, logs you in to Coupler.io.
- **Claude Code** — On the Claude Code tab, start a new session and paste the command below. Restart once the command is in place. Sign-in happens in the browser, and you click Authorize to confirm.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 6. Schedule

Property data can refresh on a monthly, weekly, daily, or hourly schedule, and also as often as every 15 minutes. Afterward, Claude answers from the GA4 metrics and dimensions on that property.

### Bonus: or just ask the AI Agent to build it for you

Property setup goes to the Coupler.io AI Agent, in the sidebar along the right side of the Coupler.io app. It drafts the GA4 flow. Claude is where the questions go after that. ChatGPT and Cursor are unrelated to this sidebar.

> "Pull sessions, engagement rate, Landing page, and purchase revenue for this year from the main property and send the result to Claude."

The agent leaves these three to you:

1. Connect Google Analytics 4 (GA4). Sign-in stays with you.
2. Choose which **Properties** are in scope.
3. Attach Claude on your own, via Chat and Cowork or Claude Code.

## What data can you export from Google Analytics to Claude with Coupler.io?

This source has no report type, so the list below is not a menu of wizard categories and one flow is not limited to one heading. These sixteen bullets are editorial groupings of real GA4 metric and dimension labels. They are a reading guide for what you can place in Metrics and Dimensions. If you build more than one flow, Coupler.io's Join can stitch those flows before Claude sees the combined rows.

- **Traffic acquisition** — Ask how sessions and engaged sessions arrived. Source labels are Session source / medium and Session campaign. Channel labels are Session default channel group together with Session primary channel group. Keep engagement rate on that same flow.
- **User acquisition** — Point Claude at First user dimensions when the question is about the first visit rather than the latest session.
- **Engagement and sessions** — For a depth question, include sessions and also sessions per user. Add average session duration. Engaged sessions and engagement rate still belong here, along with user engagement and views per session.
- **Pages and screens** — Ask which Page path, Page title, Landing page, Full page URL, Hostname, or Content group carried the visit.
- **Events and key events** — Use Event name and Is key event with event count, event count per user, events per session, and event value so Claude can separate ordinary events from the ones you marked.
- **Ecommerce and revenue** — Ask about purchases, transactions, add-to-carts, checkouts, purchase revenue, total revenue, and refund amount together.
- **Product and item detail** — Name Item name, Item ID, Item brand, Item category, and Item variant when the question is about the catalog.
- **Promotions and item lists** — Include Item promotion name, Item list name, and Item promotion creative name when Claude should talk about merchandising.
- **Audience demographics and interests** — Slice with Age, Gender, Interests, Audience name, and New / returning.
- **Geography** — Ask for Country, Region, City, or Continent when place is the question.
- **Technology and platform** — Use Device category, Device brand, Mobile model, Browser, Operating system, and Platform.
- **Paid media linkage** — Pull the Google Ads, SA360, DV360, CM360 dimension families together with ads clicks, ads cost, and return on ad spend.
- **Organic search performance** — Ask about organic Google search clicks, impressions, click-through rate, and average position.
- **Publisher and ad revenue** — Cover publisher ad clicks, publisher ad impressions, total ad revenue, Ad format, Ad source, and Ad unit.
- **Retention and cohorts** — Use Cohort, Daily cohort, Weekly cohort, Monthly cohort, and active users when the question is about who came back.
- **Time grain** — Set the grain with Date, Hour, Day of week, Week, Month, or Year so Claude can move from a single hour to a full year.

## Why export Google Analytics to Claude — real life cases

With a GA4 property on a schedule, these are questions Claude can take in everyday wording from the labels you selected.

- **Say where sessions came from**

  Put Session source / medium on the flow with Session campaign. Add Session default channel group, and add Session primary channel group. Include sessions, engaged sessions, and engagement rate. Ask Claude which channel group produced engaged sessions in *last month*. Traffic acquisition is the grouping those labels belong to, and you still pick them yourself because there is no report type.

- **Separate first visits from later ones**

  First user dimensions are the user-acquisition labels. Ask Claude how first-time users arrived, then compare that with Session source / medium on a second flow. Coupler.io's Join can match the two on Date before Claude describes the gap.

- **Find landing pages that hold a session**

  Landing page, Page path, Page title, and Full page URL tell Claude which screen people met first and where they went. Add engaged sessions, average session duration, and views per session. Ask which Landing page kept people, and which Hostname or Content group it sat on.

- **Tell key events from the rest of the stream**

  Event name and Is key event, plus event count, event count per user, events per session, and event value, are enough for Claude to rank what you marked. Ask which Event name drove event value in *this year*. Leave the other event metrics off if the question is only about key events.

- **Put revenue next to refunds**

  Purchases, transactions, add-to-carts, and checkouts show the path. Purchase revenue, total revenue, and refund amount show the money. Ask Claude what purchase revenue remained after refund amount for *this month*, and which Item name, Item ID, Item brand, Item category, or Item variant sat underneath it.

- **Read paid media beside return on ad spend**

  The Google Ads, SA360, DV360, and CM360 dimension families belong in one flow with ads clicks, ads cost, and return on ad spend. Ask Claude where ads cost ran ahead of return on ad spend. Add Item promotion name, Item list name, or Item promotion creative name when the question is about the merchandising that spend supported.

- **Check organic search without leaving the property**

  Organic Google search clicks, impressions, click-through rate, and average position are GA4 labels you can hand to Claude. Ask whether average position moved with click-through rate for *last year*. Publisher ad clicks, publisher ad impressions, total ad revenue, Ad format, Ad source, and Ad unit answer a different money question, so keep them on a flow of their own when you want Claude to talk about ad revenue.

- **Ask who came back, and on which device**

  Cohort, Daily cohort, Weekly cohort, Monthly cohort, and active users support a retention question. Age, Gender, Interests, Audience name, and New / returning describe who. Country, Region, City, Continent, Device category, Device brand, Mobile model, Browser, Operating system, and Platform describe where and on what. Pick at most nine dimensions, set the grain with Date, Hour, Day of week, Week, Month, or Year, and ask Claude which cohort of active users returned.

## Other Claude integrations

Every other source you can land in Claude with the same no-code setup:

- [Connect Facebook Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-ads-to-claude.md)
- [Connect Facebook Page Insights to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-facebook-page-insights-to-claude.md)
- [Connect Google Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-google-ads-to-claude.md)
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

