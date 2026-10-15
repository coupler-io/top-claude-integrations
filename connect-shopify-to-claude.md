---
title: Connect Shopify to Claude with Coupler.io
slug: connect-shopify-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md
source: Shopify
destination: Claude
meta_title: Connect Shopify to Claude with Coupler.io
meta_description: Send Shopify Orders, Customers, Products, and Inventory to Claude and ask about fulfillment, refunds, and stock in plain language.
---

![Shopify](https://static.coupler.io/importers/shopify.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Shopify to Claude with Coupler.io

Shopify's admin is built to fulfill a single order and edit a single product. A question that crosses customers, inventory, and last month's refunds turns into another filtered view or a download that is stale by afternoon. Coupler.io schedules the entity you select and exposes it so you can ask Claude about the store in your own words. Fulfillment stays in Shopify. The questions land in Claude, against a refresh you set once.

## How to export Shopify data to Claude

Each flow carries one category. The wizard's **Data entity** list covers Orders, Customers, Inventory, Products, Products with variants, Orders with line items, Orders with activities, Orders transactions, Orders refunds transactions, Orders with refunded items, Orders with shipping lines, and Order fulfillments with line items. Ready-made reports also exist as dataset templates, and those names are listed with the entities further down.

### Step 1. Basic settings

- **Data entity** — The category this flow sends for Claude to answer from. Pick one. The full set, including the older entities that remain selectable, is listed further down.

### Step 2. Columns

- **Columns** — Choose which Shopify fields travel with that entity. Leave out anything you will never ask about, and rename the keepers into words the team already uses.

### Step 3. Date filters

- **Created after date** — Opening bound on when the record was created. Roll it with *this year* or *last year*, with *this month* or *last month*, or with a short *days ago* lookback, and the window keeps moving. For one fixed trailing year on a Shopify order, type `{{365daysago}}`.
- **Created before date** — Closing bound on created time, using the same kind of relative choice so the window does not freeze on a calendar date you typed once.
- **Changed after date** — Opening bound on when the record last changed. Pair it with Orders with activities when the question is about edits rather than new checkouts.
- **Changed before date** — Closing bound on that change window.

### Step 4. Advanced filters

- **Filter after ID** — Keep records whose ID is past the value you enter, so a later run can continue through the store instead of rereading the earliest history every time.
- **Status** — For orders: Any, Open, Closed, or Cancelled. Use it when Claude should ignore orders that are already Closed or only talk about the ones still Open.
- **Financial status** — Any, Authorized, Pending, Paid, Partially paid, Refunded, Voided, Partially refunded, or Unpaid. This is how a question about money gets a real boundary.
- **Fulfillment status** — Any, Shipped, Partial, or Unshipped. Use it when the question is about what has left the building.
- **Status** — For products: Any, Active, Archived, or Draft. Use it so a catalog question can stay on live listings or include the ones you have parked.

### Step 5. Blend and transform data

- **Column management** — Hide Shopify columns nobody will ask about, rename the rest into store language, and put the order fields in a sequence that reads straight through.
- **Join** — Coupler.io's Join stitches Orders to Customers, or line items to Products, before Claude sees one combined result. Each entity can also stay on its own flow if you would rather ask Claude to relate them.
- **Append** — Coupler.io's Append stacks a second Shopify flow under this one before Claude reads the combined rows.
- **Aggregate** — Coupler.io's Aggregate rolls order rows up by Financial status before Claude receives the shorter summary.
- **Custom SQL** — Write a query when the store question needs a figure the clicks do not build, and Claude receives what that query returns.

### Step 6. Claude destination

The destination step is **Setup Claude integration**. It has two tabs and no fields of its own, because Claude reads the Shopify entity you already chose.

- **Chat and Cowork** — Fulfillment questions in chat start when you register a Claude account and use the Connect button on the Coupler.io connector (https://l.rw.rw/couplerio-claude-connector). That button requires an admin if the workspace plan is Team or Enterprise. You then return to the Connectors menu for another Connect click, which logs you in to Coupler.io.
- **Claude Code** — In a brand-new session, paste the command that follows, restart, finish browser sign-in, and click Authorize. An Unshipped-order question can then run against this Shopify flow.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Match the cadence to the store: every 15 minutes when a fulfillment question cannot wait, or hourly, daily, weekly, or monthly when it can. Every run refreshes the dataset Claude answers from, so a question about today's checkouts is not stuck on an afternoon download.

### Bonus: or just ask the AI Agent to build it for you

Unshipped-order requests can be spoken instead of clicked through. In the Coupler.io app the AI Agent sits in the right sidebar and drafts the flow. Claude answers afterward, while ChatGPT and Cursor stay out of this setup. Describe the extract:

> Pull Orders created this year with Financial status Paid and Fulfillment status Unshipped, and send the result to Claude.

You still do two things yourself:

1. Connect the Shopify account. Signing in stays with you, and the store you authorize is the store in scope.
2. Connect Claude, either with the Chat and Cowork connector or with Claude Code authorization.

The agent can take Data entity, Columns, the date filters, and the advanced filters from that prompt.

## What data can you export from Shopify to Claude with Coupler.io?

Twelve current **Data entity** categories are listed first, and one flow handles one category. Coupler.io's Join can stitch two of those categories together before Claude sees them. After them are the Shopify reports published as dataset templates.

- **Orders** — Ask which checkouts became real purchases, and narrow the reply with Financial status or Fulfillment status so it comes back as a work list.
- **Customers** — Ask who bought, who returned, and who has gone quiet, from the customer records rather than a page-by-page browse.
- **Inventory** — Ask what is on hand before you promise a ship date.
- **Products** — Ask which listings are Active, which are Archived, and which are still Draft, without opening each product page.
- **Products with variants** — Ask how a product breaks into its options, so a question about a particular variant has those rows attached.
- **Orders with line items** — Ask what was purchased on each order, line by line, when the question is about units rather than order counts.
- **Orders with activities** — Ask what happened to an order after checkout, and pair the flow with Changed after date when only recent edits matter.
- **Orders transactions** — Ask how each order was paid, so a payment question does not depend on opening the order in the admin.
- **Orders refunds transactions** — Ask which payments were reversed, as their own rows, when you want the refund movement rather than the original charge.
- **Orders with refunded items** — Ask which products came back, not only which payments were undone.
- **Orders with shipping lines** — Ask what shipping was charged and which method was used, on the order that carried it.
- **Order fulfillments with line items** — Ask what has already been fulfilled, down to the lines inside each fulfillment.

Older entities remain selectable on Data entity for flows that already use them: Orders (legacy), Products (legacy), Inventory (legacy), Customers (legacy), Products with variants (legacy), Orders with line items (legacy), Orders with activities (legacy), Order fulfillments with line items (legacy), Orders with shipping lines (legacy), Orders refunds transactions (legacy).

Shopify reports available as dataset templates:

- **Shopify Returning customer rate** — Ask how many customers came back, against new customers, and what the returning customer rate was.
- **Shopify inventory monthly stockout forecast** — Ask how many months of stock remain from net items sold, average sales, and available stock.
- **Shopify inventory weekly stockout forecast** — Ask the same stock question in weeks, when a month is too coarse for replenishment.
- **Shopify inventory daily stockout forecast** — Ask how many days of stock remain when a fast seller can empty a shelf inside a week.
- **Shopify Sales by product variant** — Ask which variant sold, which came back, and what gross sales, net sales, and total sales that left.
- **Shopify Sales by sources** — Ask which source produced the orders, the customers, and the average order value.
- **Shopify top customers** — Ask who ordered the most, what they returned, and what total sales they account for.
- **Shopify sales by order fulfillment status** — Ask how gross sales and returns split by fulfillment status.
- **Shopify sales by order financial status** — Ask how orders, taxes, and total sales split by financial status.
- **Shopify Sales by billing location** — Ask which billing country produced the orders, the customers, and the shipping charges.
- **Shopify Total customers & Avg order value** — Ask how many customers you have and what the average order value is beside gross sales, net sales, and taxes.
- **Shopify Top selling products** — Ask which products lead on net items sold, and what share of those units came back.
- **Shopify Sales by new vs returning customers** — Ask how orders and total sales split between new customers and returning customers.
- **Shopify Line Items with Shipping and Taxes** — Ask, line by line, for quantity, discount, returns, taxes, shipping charged, and total sales.
- **Shopify Total sales by line item** — Ask for net items sold, discounts, returns, taxes, and total sales on each line.
- **Shopify Total sales by order** — Ask for discounts, returns, taxes, and shipping charged on each order.
- **Shopify Orders with COGS** — Ask for cost of goods, gross profit, and gross margin on the order, next to net sales and total sales.
- **Shopify Line items with COGS** — Ask for the same profit figures on the line, including net returns and gross margin.
- **Shopify and GA4 monthly performance** — A template that also uses Google Analytics. Ask how monthly sessions and checkouts sit next to Shopify orders and total sales.
- **Shopify and GA4 weekly performance** — The same pairing, on a weekly grain: sessions, cart additions, and Shopify total sales.
- **Shopify and GA4 daily performance** — The same pairing, day by day, so a traffic change can be read against that day's orders.

## Why export Shopify to Claude — real life cases

A store lead can put these questions to Claude once the entities are refreshing.

- **See which paid orders have not shipped**

  Load Orders with Financial status Paid and Fulfillment status Unshipped. Ask Claude which of those are still Open, and set Created after date to *this month* when last quarter's backlog should stay out of the reply. Status set to Open keeps Closed and Cancelled orders from mixing into the same answer.

- **Ask what changed on an order overnight**

  Orders with activities is the record of what happened after checkout. Set Changed after date to *days ago* when you want the overnight edits, and Changed before date when the window should stop. Ask Claude what moved to Closed or Cancelled inside that slice.

- **Separate refunded items from refunded money**

  Orders refunds transactions holds the reversed payments, and Orders with refunded items holds the products that went back. Ask Claude which refunded payments also name a returned item, and use Financial status Refunded or Partially refunded on an Orders flow when you want a header-level check beside those two extracts.

- **Ask which variants show up on real orders**

  Products with variants lists each option under its product, and Orders with line items lists what was bought. Ask Claude which variants appear on orders created *last month*, with Created after date and Created before date holding that month. Status set to Active keeps Archived and Draft listings from crowding the reply.

- **Check stock before you announce a sale**

  Inventory answers what is on hand, and Products tells you whether the listing is Active, Archived, or Draft. Ask Claude which Active products look thin before the promotion goes out. Run the two entities as separate flows, or stitch them with Coupler.io's Join before Claude sees them.

- **Ask what shipping sat on each order**

  Orders with shipping lines keeps the method on the order it belonged to. Ask Claude which methods were used on orders created *this year*, with Created after date and Created before date marking the year. Fulfillment status Unshipped versus Shipped tells you whether that shipping line is still a promise.

- **Read each fulfillment down to the line**

  Order fulfillments with line items is what already went out, line by line, rather than the order header alone. Ask Claude which lines sit inside Partial fulfillments and which orders are fully Shipped. Filter after ID when you want the next batch of fulfillment records instead of the whole history.

- **Ask who bought, and who bought again**

  Customers is the person list and Orders is the purchase list. Ask Claude which customers have more than one order inside a Created after date window such as *this year* or *last year*. Status Any on the order side keeps Open, Closed, and Cancelled in view when the question is everyone who checked out.

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
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

