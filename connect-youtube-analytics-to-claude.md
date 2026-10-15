---
title: Connect YouTube Analytics to Claude with Coupler.io
slug: connect-youtube-analytics-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md
source: YouTube
destination: Claude
meta_title: Connect YouTube Analytics to Claude with Coupler.io
meta_description: Ask Claude about YouTube watch time, subscribers gained, and traffic sources, including Youtube product, and get channel answers in plain language.
---

![YouTube Analytics](https://static.coupler.io/importers/youtube.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect YouTube Analytics to Claude with Coupler.io

YouTube Studio keeps channel totals, subscriber changes, video retention, and traffic sources in different reports, so a question that crosses them means another export. Coupler.io sends YouTube Analytics to Claude so those questions can be typed instead. You choose the channels, one of seven report types, a date window, and an optional split by Day or Month. Metrics run from Views and Watch time (minutes) through subscribers, cards, playlists, and YouTube Premium. Dimensions include geography, device, subscription status, and Youtube product.

## How to export YouTube Analytics data to Claude

Seven report types are covered: Channel detailed statistics, Channel statistics by content and subscriber type, Channel subscribers, Video detailed statistics, Video statistics by content and subscriber type, Traffic sources, and Custom.

### Step 1. Basic settings

- **Channels** — Choose the channels Claude should answer about. A flow can include more than one channel, and each row still belongs to the channel it came from.
- **Report type** — One category for this flow. The seven names are listed in the data section, from the channel statistics through Custom.

### Step 2. Report period

- **Start date** — The first day of watch time Claude should see. *days ago* is a short premiere window, and *last year* is the prior year of the channel. A one-year lookback can be written as `{{365daysago}}`.
- **End date** — The closing day of watch time. *this month* keeps the month that is still open, *last month* stops on a finished month, and *this year* runs through the year to date.
- **Split data by period** — Day or Month. Day is the finer grain when Claude should describe a premiere week. Month is the grain for a longer channel review.

### Step 3. Metrics and dimensions

- **Metrics** — Select Views, Watch time (minutes), Average view duration, Average view percentage, Likes, Dislikes, Comments, Shares, Subscribers gained, Subscribers lost, card and annotation metrics, playlist metrics, YouTube Premium views, and YouTube Premium watch time (minutes). Claude answers only about the metrics you include.
- **Dimensions** — Choose from Age, City, Country, Device type, Gender, Operating system, Province (available for US country only), Sharing service, Day, Month, Content type, Live or on demand, Subscription status, Youtube product, Insight playback location type, Insight traffic source type, Playlist, Video, and the detail dimensions.
- **Additional dimensions** — Attach further dimensions the report type still offers beyond the Dimensions list, when the question needs that extra cut.

### Step 4. Sorting options

- **Sorting column** — Choose the column the rows are ordered by, such as Watch time (minutes) or Views, so Claude meets the strongest rows first.

### Step 5. Advanced settings

- **Video ID** — Limit the flow to one video when the question is about a single upload rather than the whole channel.
- **Insight traffic source type** — Limit the flow to one Insight traffic source type when Claude should talk about a single origin of views.

### Step 6. Blend and transform data

- **Column management** — Keep Watch time (minutes) and Average view percentage on the YouTube flow, and hide card and annotation metrics when the question is about subscribers.
- **Join** — Coupler.io's Join attaches Traffic sources to Video detailed statistics on the video before Claude explains where that video's views came from.
- **Append** — Coupler.io's Append stacks Channel subscribers under Channel detailed statistics for channels that share a calendar, before Claude reads both.
- **Aggregate** — Coupler.io's Aggregate rolls a Day split up to a coarser Month before Claude summarizes the quarter.
- **Custom SQL** — Limit a query to one Youtube product value, then hand that cut to Claude.

### Step 7. Claude destination

Watch time and subscriber figures reach Claude through **Setup Claude integration**. The step is two tabs, with no form beyond them.

- **Chat and Cowork** — Register a Claude account before watch-time questions go to chat. Open https://l.rw.rw/couplerio-claude-connector, the Coupler.io connector, and click Connect. A Team or Enterprise plan blocks that click unless you are an admin. Choose Connect again in the Connectors menu to log in to Coupler.io.
- **Claude Code** — Claude Code needs its own new session. Put the command below in that session and restart. Carry out sign-in in the browser, then click Authorize.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 8. Schedule

A premiere can justify a refresh every 15 minutes. The other intervals are hourly, daily, weekly, and monthly. The finished run updates the channel and video figures Claude reads afterward.

### Bonus: or just ask the AI Agent to build it for you

Channel flows are a job for the Coupler.io AI Agent. Open that agent from the sidebar on the right in the Coupler.io app. It assembles the YouTube importer. Claude is who answers once the rows are refreshing. ChatGPT and Cursor play no part in that sidebar.

> "Load Channel detailed statistics split by Month, with Views and Watch time (minutes), and send the result to Claude."

Left for you:

1. Connect the YouTube account. The sign-in is yours.
2. Choose the **Channels** in scope.
3. Hook Claude up yourself, through Chat and Cowork or a Claude Code authorization.

## What data can you export from YouTube Analytics to Claude with Coupler.io?

Seven categories are available. Keep each report type in its own flow. Coupler.io's Join can stitch Channel subscribers to Traffic sources so Claude receives one combined set of rows.

- **Channel detailed statistics** — The broad channel category. Ask Claude about Views, Watch time (minutes), Average view duration, and the rest of the metrics you ticked, for every channel in the Channels field.
- **Channel statistics by content and subscriber type** — Splits the channel by Content type and Subscription status, including Live or on demand, so Claude can tell subscribed viewers from everyone else.
- **Channel subscribers** — The subscriber category. Subscribers gained and Subscribers lost are the metrics that make a "did we grow?" question concrete.
- **Video detailed statistics** — One video at a time, or the library, with Average view percentage, Likes, Dislikes, Comments, and Shares available beside watch time. Video ID narrows this to a single upload.
- **Video statistics by content and subscriber type** — The video-level twin of the channel content split. Ask Claude how a video did by content type and by whether the viewer was subscribed.
- **Traffic sources** — Where views originated. Insight traffic source type and Insight playback location type are the dimensions, and the advanced Insight traffic source type field can lock the flow to one origin.
- **Custom** — The open category. Combine the metrics you need with dimensions such as Youtube product, Age, Gender, Device type, and Country, then set Sorting column so Claude sees the rows in the order you chose.

## Why export YouTube Analytics to Claude — real life cases

Channel managers can ask Claude the questions below when watch time, subscribers, and traffic sources refresh on the same schedule.

- **Read the channel as a whole**

  Channel detailed statistics with Views, Watch time (minutes), and Average view duration is the standing picture. Split data by period set to Month, and ask Claude how *this year* compares with the shape of *last month*. Sorting column can put the highest watch time first so the answer starts there.

- **Separate content type from subscriber type**

  Channel statistics by content and subscriber type uses Content type, Subscription status, and Live or on demand. Ask Claude whether live viewers who were already subscribed watched longer than on-demand viewers who were not. YouTube Premium views and YouTube Premium watch time (minutes) can sit on the same flow when premium viewing is part of the question.

- **Explain the subscriber change**

  Channel subscribers, with Subscribers gained and Subscribers lost, answers the net-change question. Ask Claude which Day, using Split data by period, accounted for the losses. Country, City, and Province (available for US country only) can wait on a Custom flow when you need the geography of that change.

- **Inspect a single video**

  Set Video ID on Video detailed statistics and include Average view percentage, Likes, Comments, and Shares. Ask Claude whether people finished the video or left, and whether Shares moved with Comments. Average view duration adds the clock to that answer.

- **Compare videos by who was subscribed**

  Video statistics by content and subscriber type is the per-video split. Ask Claude which videos depended on subscribers and which found viewers outside that group. Playlist and Video dimensions keep a playlist question tied to the right uploads.

- **Ask where the views came from**

  Traffic sources plus Insight traffic source type, Insight playback location type, and Sharing service tell Claude the origin and the place of playback. The advanced Insight traffic source type field can restrict the flow to one origin before you ask. Coupler.io's Join can attach this category to Video detailed statistics on the video.

- **Build a custom cut around Youtube product**

  Custom is the report type for a combination the fixed reports do not offer. Include the dimension Youtube product, spelled that way, plus Age, Gender, Operating system, and Device type. Additional dimensions cover a further cut, and the detail dimensions sit with Insight playback location type and Insight traffic source type when you need them. Ask Claude how watch time differs by Youtube product for *days ago*.

- **Check playlists, cards, and a short refresh**

  Playlist metrics and card and annotation metrics belong in Metrics when the question is about playlists, cards, or annotations. Ask Claude about a Playlist over *this month*, with a Day split during a launch and a refresh every 15 minutes while that launch is live. Dislikes can stay in the metric list when you want the full reaction picture beside Likes.

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
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)

