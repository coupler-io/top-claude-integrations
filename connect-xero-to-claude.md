---
title: Connect Xero to Claude with Coupler.io
slug: connect-xero-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md
source: Xero, Xero Reports
destination: Claude
meta_title: Connect Xero to Claude with Coupler.io
meta_description: Send Xero Invoices, Bank transactions, Contacts, and Pay runs to Claude and ask about cash, tax, and payroll in plain language.
---

![Xero](https://static.coupler.io/importers/xero.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect Xero to Claude with Coupler.io

Xero splits an organisation across invoices, bank lines, payroll, and projects, and each list has its own filters. A question that needs Detailed Invoices and the Pay runs for the same month means two exports and a careful match on dates. Coupler.io sends one Data entity from the Xero tenant you select, on a schedule, for Claude to answer from. Simple is the usual report shape, and Detailed is there for the entities that support it. A UK or New Zealand Pay runs flow stays separate from an Australia Pay runs flow unless you blend them on purpose. When a flow needs the extra field, you configure Advanced settings yourself.

## How to export Xero data to Claude

Each flow carries one category from the tenant you pick. The steps below are the Xero connector: accounting, UK and New Zealand payroll, Australia payroll, and projects. Simple is the default Report type on that connector and is available for every entity. Detailed is available for Bank transactions, Contacts, Credit notes, Invoices, Manual journals, Overpayments, and Prepayments. Statements are a second connector, Xero Reports. There, Basic settings are **Xero tenant**, **Report type**, and **Report structure**. The other steps are Contact (**Contact ID**), Bank account (**Bank Account ID**), Report period (**Date**, **Start date**, **End date**), and Parameters, including **Number of periods to compare**, **Period**, the tracking category and option IDs, **Include cash transactions only**, and **Standard layout**. Every name is listed further down.

### Step 1. Basic settings

- **Xero tenant** — The organisation this flow reads. Pick the tenant whose books, payroll, or projects Claude should answer about.
- **Data entity** — The single entity for this flow. Accounting, payroll, and projects are all chosen here, and two different entities share the name Users: organisation users, and project users.
- **Report type** — Simple is the default and is available for every entity. Detailed is available for Bank transactions, Contacts, Credit notes, Invoices, Manual journals, Overpayments, and Prepayments.
- **Projects** — The projects included in this flow. Set it when the entity is project work and Claude should see only some of them.

### Step 2. Date filters

- **Changed after** — Lower bound on records that have changed. Set *days ago* after a weekend of edits, *this month* during close, or *last month*, *this year*, and *last year* when the question reaches further back. On a Xero change window, `{{365daysago}}` means a trailing year.
- **Start date** — Opening day of the window for entities that take a start.
- **End date** — Closing day of that window.
- **Created after** — Opening bound on created time.
- **Created before** — Closing bound on created time.
- **Expiring after** — Opening bound on an expiry date, for an entity that carries one.
- **Expiring before** — Closing bound on that expiry.

### Step 3. Advanced settings

- **Statuses** — For invoices: one or more of Draft, Submitted, and the other invoice statuses. Claude then sees only the states you ticked.
- **Journal number more than** — Include journals numbered above this value.
- **Journal number less than** — Include journals numbered below this value.
- **Split by** — How the rows are divided, when you want a split rather than the entity's usual shape.
- **Status** — One status, not a mix, for pay runs, for timesheets, for linked transactions, for purchase orders, and for quotes. Claude then answers about that single state.
- **Statuses** — For projects and project time. The title is Statuses by default and Status when the entity is time.
- **Advanced settings** — Further options collected under this field title. You fill this one in directly. The bonus explains why it stays with you.
- **Include archived** — Turn this on when archived records should be part of what Claude can answer about.

### Step 4. Blend and transform data

- **Column management** — Pare a Xero extract down to the columns the question names, and rename tracking labels into everyday words.
- **Join** — Coupler.io's Join matches Invoices to Contacts before Claude reads either extract.
- **Append** — Coupler.io's Append sets Bank transfers after Bank transactions before Claude looks at cash movement as one list.
- **Aggregate** — Coupler.io's Aggregate totals invoice rows by contact before Claude sees the rollup.
- **Custom SQL** — Write a query over the Xero rows when you need a shape the other transformations do not produce, and Claude receives that query's result.

### Step 5. Claude destination

The destination is **Setup Claude integration**, with two tabs and nothing else to name. Claude answers from the Xero tenant and Data entity chosen above.

- **Chat and Cowork** — A tenant question needs a place to land, so register a Claude account and choose Connect beside the Coupler.io connector (https://l.rw.rw/couplerio-claude-connector). Be an admin when that Claude plan is Team or Enterprise. The login to Coupler.io is the next Connect, still in the Connectors menu.
- **Claude Code** — Create a new session for this organisation, insert the command shown next, restart it, walk through the browser sign-in, and click Authorize. Detailed Invoices for the tenant can be asked about once that authorization is done.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 6. Schedule

A quiet ledger can refresh monthly. Weekly or daily suits close, hourly suits a busy bank feed, and every 15 minutes is there when a payroll question cannot lag. What Claude can see is only as fresh as the latest run, and that run refreshes the dataset Claude answers from. Bank lines and pay runs both depend on that freshness.

### Bonus: or just ask the AI Agent to build it for you

Invoice and pay-run setup can be spoken aloud. The right sidebar of the Coupler.io app holds the AI Agent, and it drafts the Xero flow while Claude, ChatGPT, and Cursor stay out of the drafting. Describe the entity and the window:

> Pull Detailed Invoices changed this month for my Xero tenant, and send the result to Claude.

Four steps stay with you:

1. Connect the Xero account. Signing in stays with you.
2. Choose the **Xero tenant** that is in scope.
3. Connect Claude by installing the Chat and Cowork connector, or by authorizing Claude Code.
4. The user still configures Advanced settings. The agent does not fill that field.

Data entity, Report type, Projects, and the date filters can follow the prompt. Statuses, journal-number bounds, Split by, Status, and Include archived can too.

## What data can you export from Xero to Claude with Coupler.io?

The catalogue below is the full set from both connectors: 26 accounting entities, 12 payroll entities for the UK and New Zealand, 15 payroll entities for Australia, 4 project entities, and 9 Xero Reports. Leave types, Pay runs, and Timesheets appear in both payroll lists because each region exposes them. One flow handles one category. Coupler.io's Join can stitch an Invoice to Profit And Loss before either reaches Claude. Accounting includes a Users entity for organisation users. Projects includes a different Users entity for project users.

Accounting entities:

- **Accounts** — Ask what sits in the chart of accounts before you interpret a total.
- **Bank transactions** — Ask what moved through the bank, and switch Report type to Detailed when the lines matter more than the simple list.
- **Bank transfers** — Ask what moved between bank accounts.
- **Branding themes** — Ask which document themes the organisation has when the question is about how invoices are presented.
- **Contact groups** — Ask how contacts are grouped.
- **Contacts** — Ask who the customers and suppliers are. Detailed is available when the simple list is too thin.
- **Credit notes** — Ask which credits have been raised. Detailed is available on this entity.
- **Currencies** — Ask which currencies the organisation uses.
- **Employees** — Ask who is on the accounting employee list, which is separate from Employees (UK or NZ) and Employees (AU).
- **Expense claims** — Ask what has been claimed.
- **Invoices** — Ask what was billed. Detailed is available, and Statuses can limit the rows to Draft, Submitted, or the other invoice statuses.
- **Items** — Ask what the organisation buys or sells as items.
- **Journals** — Ask what was posted, and bound the set with Journal number more than and Journal number less than.
- **Linked transactions** — Ask which transactions are linked, and set the single Status when only one state belongs in the answer.
- **Manual journals** — Ask what was journaled by hand. Detailed is available on this entity.
- **Organisation** — Ask for the organisation details on this Xero tenant.
- **Overpayments** — Ask where an overpayment is sitting. Detailed is available.
- **Payments** — Ask what was paid or received against documents.
- **Prepayments** — Ask what was paid ahead of the document it belongs to. Detailed is available.
- **Purchase orders** — Ask what has been raised to suppliers, with a single Status when you want one state.
- **Receipts** — Ask which receipts are on file.
- **Repeating invoices** — Ask which invoices are set to recur.
- **Tax rates** — Ask which tax rates the organisation has configured.
- **Tracking categories** — Ask how the organisation categorises transactions, separate from Tracking categories (UK or NZ) and Tracking categories (AU).
- **Users** — Organisation users. Ask who can access the organisation. This is not the project Users entity listed under projects.
- **Quotes** — Ask which quotes are outstanding, and set the single Status when you only want one state.

Payroll for the UK and New Zealand:

- **Benefits** — Ask which benefits that payroll has defined.
- **Deductions** — Ask which deductions UK or New Zealand payroll takes.
- **Earning rates** — Ask which earning rates UK or New Zealand payroll uses when a pay run needs explaining.
- **Earnings orders (Statutory deductions)** — Ask about statutory deductions in UK or New Zealand payroll.
- **Employees (UK or NZ)** — Ask who is on the UK or New Zealand payroll employee list.
- **Leave types** — Ask which leave types UK or New Zealand payroll offers.
- **Pay run calendars** — Ask how that payroll is scheduled.
- **Pay runs** — Ask what a UK or New Zealand pay run contained. Status takes a single value for pay runs.
- **Reimbursements** — Ask what UK or New Zealand payroll has reimbursed.
- **Accounts (UK or NZ)** — Ask which accounts that payroll posts to, separate from the accounting chart and from Accounts (AU).
- **Timesheets** — Ask about UK or New Zealand timesheets. Status takes a single value for timesheets.
- **Tracking categories (UK or NZ)** — Ask which tracking categories that payroll uses.

Payroll for Australia:

- **Employees (AU)** — Ask who is on the Australian payroll employee list.
- **Leave applications** — Ask who has applied for leave in Australia.
- **Leave applications with leave periods** — Ask for those applications with the leave periods on the same rows.
- **Earnings rates** — Ask which earnings rates Australian payroll has defined before you read a pay run.
- **Deduction types** — Ask which deduction types Australia has defined.
- **Leave types** — Ask which leave types Australian payroll offers.
- **Reimbursement types** — Ask which reimbursement types are set up for Australia.
- **Pay runs** — Ask what an Australian pay run contained, as its own flow from the UK or New Zealand Pay runs entity.
- **Payroll calendars** — Ask how Australian pay is calendared.
- **Settings** — Ask what the Australian payroll settings contain.
- **Accounts (AU)** — Ask which accounts Australian payroll posts to.
- **Tracking categories (AU)** — Ask which tracking categories Australian payroll uses.
- **Super funds** — Ask which super funds are set up.
- **Timesheets** — Ask about Australian timesheets.
- **Timesheets with timesheet lines** — Ask for those timesheets with the lines included.

Projects:

- **Projects** — Ask which projects exist. The Projects field chooses which of them this flow includes.
- **Tasks by projects** — Ask which tasks sit on those projects.
- **Time by projects** — Ask how time was recorded against projects. For this entity the status control is titled Status.
- **Users** — Project users. Ask who is on the projects. Keep this apart from organisation Users when the question is about access to the books rather than membership of a project.

Xero Reports, chosen with **Report type**:

- **Aged Payables By Contact** — Ask who you owe, contact by contact, as a statement rather than as the Bills list.
- **Aged Receivables By Contact** — Ask who owes you, contact by contact.
- **Balance Sheet** — Ask where assets, liabilities, and equity stand. **Report structure** applies to this report.
- **Bank Statement** — Ask for the statement lines of the **Bank Account ID** you set.
- **Bank Summary** — Ask for a shorter read of bank activity than the statement.
- **Budget Summary** — Ask how the budget compares across the periods you set. **Report structure** applies here.
- **Executive Summary** — Ask for the summary pack Xero builds for the organisation. **Report structure** applies here.
- **Profit And Loss** — Ask for profit and loss as Xero's report, not as a sum you build from Invoices. **Report structure** applies here.
- **Trial Balance** — Ask whether the accounts balance for the period on the report.

## Why export Xero to Claude — real life cases

A bookkeeper can ask Claude the following once the tenant is connected and the flows are refreshing.

- **Invoices that are still unfinished**

  Set Data entity to Invoices and Report type to Detailed. Tick Statuses for Draft and Submitted, and add the other invoice statuses only when the question needs them. Changed after set to *this month* drops the older noise. Ask Claude which of those invoices are still Draft, and who the contact is if you have also run Contacts.

- **What the bank actually did**

  Bank transactions with Report type Detailed, plus Bank transfers and Payments, cover the cash question as three flows. Start date and End date hold the month. Ask Claude what arrived, what left, and what was only a transfer between accounts. Coupler.io's Append can put Bank transfers after Bank transactions before Claude looks at them as one list.

- **Credits, overpayments, and money paid ahead**

  Credit notes, Overpayments, and Prepayments all allow Detailed. Ask Claude which credits are still open, where an overpayment is sitting, and which prepayments have not been drawn down. Include archived if a reversed document should stay visible. Created after and Created before can limit the set to *last month* or *this year*.

- **A UK or New Zealand pay run**

  Pay runs and Pay run calendars say when people were paid and on what calendar. Employees (UK or NZ), Earning rates, Deductions, Benefits, Reimbursements, and Earnings orders (Statutory deductions) are the lists behind a single run. Timesheets takes a single Status, as pay runs do. Ask Claude what the latest pay run contained, and which earning rates and statutory deductions were in play. Accounts (UK or NZ) and Tracking categories (UK or NZ) answer where it posted.

- **Australian leave, calendars, and super**

  Employees (AU), Leave applications, and Leave applications with leave periods are the leave question. Payroll calendars and Pay runs are the pay calendar. Earnings rates, Deduction types, Reimbursement types, Leave types, and Super funds are the setup lists, and Settings is the Australian payroll settings entity. Ask Claude who has leave in, which super fund is on file, and how that sits next to Timesheets with timesheet lines. Accounts (AU) and Tracking categories (AU) are the posting side, separate from the UK or New Zealand names.

- **Time on the right project**

  Choose the Projects field so Claude only sees the work in scope. Tasks by projects and Time by projects are the two follow-on entities. The status control is titled Statuses for projects and Status when the entity is time. Ask Claude how time sits on tasks, and use the project Users entity when the question is who recorded it. That Users list is project users, not the organisation users on the accounting Users entity.

- **Quotes, purchase orders, and what is about to lapse**

  Quotes takes a single Status, and so do purchase orders. Expiring after and Expiring before bound an expiry window when the entity has one, which is the natural pair for a quote that should not die quietly. Ask Claude which quotes expire inside *this month*, and which purchase orders are still in the one Status you care about. Repeating invoices is the related question when the follow-up is what will bill again on its own.

- **Journals, access, and the organisation itself**

  Journals, bounded with Journal number more than and Journal number less than, is how you ask about a slice of the journal list. Manual journals with Report type Detailed covers the ones entered by hand. Ask Claude what was posted in that number range. Organisation answers what this tenant is, and the accounting Users entity answers who can access it. Linked transactions, with a single Status, is the trail when a journal question turns into "what was this tied to". Receipts, Items, Expense claims, Tax rates, Currencies, Branding themes, and Contact groups stay one flow each when the follow-up is setup rather than the journal.

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
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

