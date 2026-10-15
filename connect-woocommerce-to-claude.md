---
title: Connect WooCommerce to Claude with Coupler.io
slug: connect-woocommerce-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md
source: WooCommerce
destination: Claude
meta_title: Connect WooCommerce to Claude with Coupler.io
meta_description: "Send WooCommerce Orders, Coupons, Products, and Report: Sales report to Claude and ask what sold and which discounts worked."
---

![WooCommerce](https://static.coupler.io/importers/woocommerce.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect WooCommerce to Claude with Coupler.io

WooCommerce keeps orders, coupons, reviews, and sales reports on separate screens. Comparing Report: Top sellers report with the orders underneath it means opening both and hoping the dates still match. Coupler.io moves one Data entity per flow to Claude on a cadence you choose. You can ask which coupons showed up on Completed orders, or what This Month looks like on Report: Sales report. The shop stays where orders are fulfilled. Claude is where the question is typed.

## How to export WooCommerce data to Claude

One flow sends one category. The wizard covers store reference data, commercial records such as orders and the catalogue, WooCommerce's own summary reports, and the shipping and tax setup lists. Every category is named in the data section below.

### Step 1. Basic settings

- **Data entity** — The single category Claude will answer from in this flow. Reports and raw lists are both chosen here, and the date controls in the next step change with that choice.

### Step 2. Advanced settings

- **After date** — Lower bound for Coupons, Products, Product reviews, Orders, and Orders with line items. Pick *days ago* when the slice is the newest orders, *this month* or *last month* for a calendar month, and *this year* or *last year* for a longer shop history. The macro `{{365daysago}}` is how a WooCommerce trailing year is written.
- **Before date** — Upper bound for those same five entities, so the slice Claude sees has a closing edge as well as an opening one.
- **Search** — Optional text match. Use it when you want a narrower set of rows in the answer.
- **Status** — Applies to Orders and Orders with line items. Values are Any, Pending, Processing, On-hold, Completed, Cancelled, Refunded, Failed, and Trash.
- **Period** — Applies to Report: Sales report and Report: Top sellers report. Values are Today, This Week, This Month, Last Month, This Year, and Custom.
- **Start date** — Applies to Report: Sales report and Report: Top sellers report, including when Period is Custom and you need your own opening day.
- **End date** — Closing day for those same two reports.

### Step 3. Columns

- **Columns** — Pick the WooCommerce fields that should be available when you ask. Rename cryptic ones into the labels the shop actually uses.

### Step 4. Blend and transform data

- **Column management** — Drop WooCommerce columns that only clutter a question, and rename the ones a store manager will actually say.
- **Join** — Coupler.io's Join links Orders with line items to Products before Claude is asked anything about what sold.
- **Append** — Coupler.io's Append places a Coupons extract beneath an Orders extract before Claude treats the rows as one series.
- **Aggregate** — Coupler.io's Aggregate collapses Orders by Status before Claude sees a single row for each state.
- **Custom SQL** — A query can reshape coupon rows and order lines into the comparison you want, and Claude receives whatever that query returns.

### Step 5. Claude destination

Choose **Setup Claude integration**. Two tabs, and no extra fields: the WooCommerce entity from the earlier steps is what Claude answers from.

- **Chat and Cowork** — Register a Claude account for the shop manager who will ask the questions. The Connect control sits on the Coupler.io connector at https://l.rw.rw/couplerio-claude-connector, and a Team or Enterprise plan lets only an admin use it. Logging in to Coupler.io is a further Connect, done from the Connectors menu, after that first click succeeds.
- **Claude Code** — Launch a new session that has never seen this shop, drop in the command below, restart so it loads, sign in through the browser, and click Authorize. Report: Sales report can be questioned from that session afterward.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 6. Schedule

Pick a rhythm for the shop: hourly, daily, weekly, monthly, or every 15 minutes when an order question cannot wait until morning. On every run, Coupler.io refreshes the dataset Claude answers from, so weekend Orders are already waiting the next morning.

### Bonus: or just ask the AI Agent to build it for you

Coupon questions are faster to describe than to click. Look in the right sidebar of the Coupler.io app for the AI Agent, a Coupler.io builder that is neither the Claude you will query nor ChatGPT nor Cursor. Hand it a prompt that finishes by loading the rows into Claude:

> Pull Report: Top sellers report for Period Last Month, together with Orders in Status Completed, and load the result to Claude.

Two steps stay in your hands:

1. Connect the WooCommerce account. The sign-in stays with you, and that sign-in chooses the shop.
2. Connect Claude with the Chat and Cowork connector, or authorize Claude Code.

Data entity, the advanced settings that belong to that entity, and Columns can follow the prompt.

## What data can you export from WooCommerce to Claude with Coupler.io?

Twenty-three categories are available, and each flow carries one of them. Coupler.io's Join can stitch a pair, such as Orders with line items and Products, before Claude receives the combined rows.

- **Continents** — Ask which continent a country rolls up to when an order question is really a regional one.
- **Countries** — Ask which countries the shop recognises, so a customer question can name a place.
- **Coupons** — Ask which discount codes exist, and use After date and Before date to keep the list inside the window you care about.
- **Currencies** — Ask which currencies the shop can charge in before you read an order amount.
- **Customers** — Ask who holds an account, and bring Orders into the same conversation when the question is about buyers.
- **Orders** — Ask what was placed, narrowed with Status and with After date and Before date.
- **Orders with line items** — Ask what each order contained, with the same Status values and the same date bounds as Orders.
- **Product attributes** — Ask how products are described beyond the title, so a question about a property has the attribute rows.
- **Product categories** — Ask where a product sits in the catalog when Report: Top sellers report needs that context.
- **Product reviews** — Ask what buyers wrote, bounded with After date and Before date.
- **Product shipping classes** — Ask which shipping class a product uses when a zone question needs that link.
- **Product tags** — Ask how the catalog is tagged, which helps when a promotion was organised around a tag.
- **Products** — Ask what is listed, and bound the list with After date and Before date when only recent catalog edits matter.
- **Report: Coupon totals** — Ask for the coupon scoreboard WooCommerce already totals, instead of rebuilding it from raw orders.
- **Report: Customer totals** — Ask for customer totals in the shape the report already summarises.
- **Report: Order totals** — Ask for order totals as that report states them.
- **Report: Product totals** — Ask for product totals when you want the scoreboard rather than every line item.
- **Report: Review totals** — Ask for review totals beside Product reviews when you want the count and the words.
- **Report: Sales report** — Ask how sales landed for a Period such as Today, This Week, This Month, Last Month, or This Year, or set Start date and End date.
- **Report: Top sellers report** — Ask which products led, using that same Period plus Start date and End date.
- **Shipping zones** — Ask where the shop ships.
- **Tax classes** — Ask which tax classes products can belong to.
- **Tax rates** — Ask which rates are configured, then relate them to orders in the same question.

## Why export WooCommerce to Claude — real life cases

Once the flows are running, a shop manager can ask Claude the kinds of questions that used to mean several admin screens.

- **Orders that still need a person**

  Set Data entity to Orders and Status to Processing, On-hold, or Pending. After date and Before date keep the queue inside *this month*, or use *days ago* when only the newest orders matter. Ask Claude which of those orders are still waiting, and run Orders with line items beside them when the reply needs to say what is in the box.

- **What This Month did on the sales report**

  Choose Report: Sales report and set Period to This Month. Ask Claude how the month is tracking against Last Month by running a second flow with that Period. When the question is a campaign window rather than a calendar bucket, switch Period to Custom and fill Start date and End date.

- **Top sellers with the catalog behind them**

  Report: Top sellers report answers who led for the Period you set. Ask Claude to put that beside Products, Product categories, and Product tags so a bestseller is not just a name. Report: Product totals is the scoreboard view when you want totals without the rank list.

- **Whether the coupons earned the discount**

  Coupons lists the codes, and After date and Before date apply to that entity. Report: Coupon totals is the summarised view. Ask Claude which codes exist in the window and how their totals look, then relate that to Orders whose Status is Completed.

- **Reviews before you restock**

  Product reviews, bounded with After date and Before date, is what buyers actually wrote. Report: Review totals gives the count beside it. Ask Claude what the recent reviews say about a product you are about to reorder, and pull Products in the same conversation when you need the listing next to the comments.

- **Tax on the way out the door**

  Tax classes and Tax rates are the shop's tax setup. Ask Claude which class a question is really about, and which rates are configured, then point the same conversation at Orders or Report: Order totals for the period those rates should explain.

- **Where the shop ships, and under which class**

  Shipping zones is the geography, and Product shipping classes is how products are grouped for shipping. Ask Claude which zones are configured and which class a product uses. Orders with line items is the extract to add when the question is which classes actually left in *last month*.

- **Customers, places, and currencies**

  Customers is the account list. Countries, Continents, and Currencies give Claude the reference lists behind an address or a charge. Ask who bought from a given country, which continent that country sits in, and which currency the shop had available. Report: Customer totals covers the summarised customer view when you do not need every account row. Product attributes stay available when the follow-up question is how those buyers' products were specified.

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
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

