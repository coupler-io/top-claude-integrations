---
title: Connect QuickBooks to Claude with Coupler.io
slug: connect-quickbooks-to-claude
canonical: https://github.com/coupler-io/top-claude-integrations/blob/main/connect-quickbooks-to-claude.md
source: QuickBooks, QuickBooks Reports
destination: Claude
meta_title: Connect QuickBooks to Claude with Coupler.io
meta_description: Send QuickBooks Profit and Loss Detail, Balance Sheet, and AR Aging Summary to Claude and ask finance questions in plain language.
---

![QuickBooks](https://static.coupler.io/importers/quickbooks.svg) → ![Claude](https://static.coupler.io/importers/claude.svg)

# Connect QuickBooks to Claude with Coupler.io

QuickBooks will run Profit and Loss Detail, a Balance Sheet, and an AR Aging Summary, each as its own report with its own period. Relating a customer's balance to the general ledger means running those reports one after another and reading them side by side. Coupler.io takes the Report name you choose, keeps the Report period you set, and exposes that report so Claude can answer from it. Close week becomes a question instead of a folder of one-off runs. You still choose the company when you sign in. You still set Query parameters when a report needs them.

## How to export QuickBooks data to Claude

Two connectors feed this page, and one flow still sends one category. QuickBooks is the records connector: Basic settings asks for **Data entity**, and Advanced settings are **Where**, **Order**, and **Split by**. QuickBooks Reports is the statements connector, and the steps below are that wizard. Its reports are Balance Sheet, Cash Flow, Trial Balance, Profit and Loss Summary, Profit and Loss Detail, Tax Summary, the aging and balance reports, the sales and spend cuts, and the ledger lists named further down.

### Step 1. Basic settings

- **Report name** — The QuickBooks report this flow exposes to Claude. One name per flow. All 28 are described later on this page.
- **Display columns by** — How the report is broken out. Summary reports can use Total or Day, Week or Month, Quarter or Year, plus Customers, Vendors, Classes, Departments, Employees, or Products and Services. Transaction lists can group by Name or by Account, and also by Transaction Type, Customer, Vendor, Employee, Location, or Payment Method. Use the breakout the question will actually name.

### Step 2. Report period

- **Report period** — A relative accounting period: today, yesterday, this or last week, this or last month, month-to-date, fiscal quarter and fiscal year and their to-date forms, or a custom span.
- **Start date** — Opening day when the span is custom. *Last month* and *this month* cover a close, *last year* and *this year* cover a longer set of books, and *days ago* covers a short catch-up. On a QuickBooks custom span the trailing-year macro is `{{365daysago}}`.
- **End date** — Closing day of that custom span.
- **Report date** — The aging as-of date. Set it when the report is an aging view, such as AP Aging Detail, AP Aging Summary, AR Aging Detail, or AR Aging Summary.

### Step 3. Columns

- **Columns** — The fields from that report that Claude should be able to use. Drop the ones the question will never mention.

### Step 4. Advanced settings

- **Report structure** — The shape of the rows. Choose QuickBooks-style format, QuickBooks-style format (grouped), Values-by-row format, or Flat structure.
- **Query parameters** — Further parameters for the report request. The user still sets Query parameters. Do not expect the AI Agent to fill this field.

### Step 5. Blend and transform data

- **Column management** — Keep the QuickBooks columns the question needs, hide the rest, and rename headers so a controller recognises them.
- **Join** — Coupler.io's Join lines Profit and Loss Detail up with Sales by Customer before Claude enters the conversation.
- **Append** — Coupler.io's Append puts a Transaction List after General Ledger Detail before Claude sees both reports together.
- **Aggregate** — Coupler.io's Aggregate compresses Profit and Loss Detail to a coarser grain before Claude answers from it.
- **Custom SQL** — When a report needs a figure the other transformations do not build, write the query and Claude receives its result.

### Step 6. Claude destination

**Setup Claude integration** is the whole destination step. There are two tabs, and no second report name to type, because Claude answers from the QuickBooks report already chosen.

- **Chat and Cowork** — Whoever is closing the books should register a Claude account, then press Connect on the Coupler.io connector listed at https://l.rw.rw/couplerio-claude-connector. Team or Enterprise workspaces block that press unless the person is an admin. Coupler.io login happens next: another Connect, from the Connectors menu.
- **Claude Code** — Open a new session you have not used for these books. Put the command below into it, restart, complete the browser sign-in, and click Authorize before you ask about Profit and Loss Detail.

```
claude mcp add coupler-io --transport http https://mcp.coupler.io/mcp
```

### Step 7. Schedule

Most closes are happy with daily or weekly, and the same screen also offers hourly, monthly, or every 15 minutes. Each run refreshes the dataset Claude answers from, which is what you want on close week when the ledger moved yesterday.

### Bonus: or just ask the AI Agent to build it for you

During close, describe the report instead of clicking every control. The Coupler.io app's right sidebar holds the AI Agent, which builds the QuickBooks flow and is distinct from Claude, from ChatGPT, and from Cursor. Ask it for a report and a period:

> Pull AR Aging Summary with Report date set to today, columns as Total, in Flat structure, and send the result to Claude.

Three things remain yours:

1. Connect the QuickBooks account. Signing in stays with you, and that sign-in is the company in scope.
2. Connect Claude, using the Chat and Cowork connector or Claude Code authorization.
3. The user still sets Query parameters. The agent leaves that field blank for you to complete in the wizard.

Report name, Display columns by, Report period, Columns, and Report structure can come from the prompt.

## What data can you export from QuickBooks to Claude with Coupler.io?

Thirty-three QuickBooks records and twenty-eight QuickBooks Reports are available. One flow handles one of them. Coupler.io's Join can stitch a record, such as Invoice, to a report before Claude sees either.

QuickBooks records, chosen with **Data entity**:

- **Account** — Ask which accounts exist on the company file before a statement total needs a name.
- **Attachable** — Ask which files are attached to transactions.
- **Bill** — Ask which supplier bills are on file, as records rather than as an aging report.
- **BillPayment** — Ask which payments have been applied to bills.
- **Budget** — Ask what budget figures the company has stored.
- **Class** — Ask which classes exist when a sales cut needs that label.
- **CompanyInfo** — Ask for the company profile stored on the file.
- **CreditMemo** — Ask which credit memos have been issued to customers.
- **Customer** — Ask who the customers are, separate from Customer Balance.
- **Department** — Ask which departments the file uses.
- **Deposit** — Ask which bank deposits have been recorded.
- **Employee** — Ask who is on the QuickBooks employee list. This is not a payroll report.
- **Estimate** — Ask which estimates are still estimates.
- **ExchangeRate** — Ask which exchange rates the file holds.
- **Invoice** — Ask which customer invoices exist as records, separate from AR Aging Detail.
- **Item** — Ask which products and services are on the item list.
- **JournalEntry** — Ask for journal entries as records. Journal Report is the report view of the same idea.
- **JournalCode** — Ask which journal codes the file uses.
- **Payment** — Ask which customer payments have been recorded.
- **PaymentMethod** — Ask which payment methods the company accepts.
- **Preferences** — Ask what the company preferences contain.
- **Purchase** — Ask which purchases, checks, and expenses are stored as purchases.
- **PurchaseOrder** — Ask which purchase orders are open or recorded.
- **RefundReceipt** — Ask which refund receipts have been issued.
- **SalesReceipt** — Ask which sales receipts have been recorded.
- **TaxAgency** — Ask which tax agencies are set up.
- **TaxCode** — Ask which tax codes the file uses.
- **TaxRate** — Ask which tax rates are stored.
- **Term** — Ask which payment terms exist.
- **TimeActivity** — Ask which time activities have been entered.
- **Transfer** — Ask which transfers between accounts are recorded.
- **Vendor** — Ask who the vendors are, separate from Vendor Balance.
- **VendorCredit** — Ask which credits vendors have issued.

QuickBooks Reports, chosen with **Report name**:

- **Account List Detail** — Ask what each account is and how it is set up before you read a statement that depends on it.
- **AP Aging Detail** — Ask which bills make up what you owe, as of the Report date.
- **AP Aging Summary** — Ask for vendor aging totals on that same as-of date.
- **AR Aging Detail** — Ask which open items make up what customers owe, as of the Report date.
- **AR Aging Summary** — Ask for customer aging totals without opening each customer.
- **Balance Sheet** — Ask where assets, liabilities, and equity stand for the Report period you chose.
- **Cash Flow** — Ask how cash moved across that same period.
- **Customer Balance** — Ask what each customer currently owes, in summary.
- **Customer Balance Detail** — Ask which transactions sit behind a customer balance.
- **Customer Income** — Ask which customers produced income.
- **Expenses by Vendor** — Ask which vendors the expenses went to.
- **General Ledger Detail** — Ask for the ledger lines behind a total on the statements.
- **Inventory Valuation Summary** — Ask what inventory is worth.
- **Journal Report** — Ask what was journaled in the period.
- **Profit and Loss Summary** — Ask for profit and loss in its condensed form.
- **Profit and Loss Detail** — Ask for profit and loss with the lines under each total.
- **Sales by Class Summary** — Ask how sales split by class.
- **Sales by Customer** — Ask how sales split by customer.
- **Sales by Department** — Ask how sales split by department.
- **Sales by Product** — Ask how sales split by product.
- **Tax Summary** — Ask what the tax totals are for the period.
- **Transaction List** — Ask for the transactions as a list you can question.
- **Transaction List by Customer** — Ask for that list gathered by customer.
- **Transaction List by Vendor** — Ask for that list gathered by vendor.
- **Transaction List with Splits** — Ask for transactions with the split lines visible.
- **Trial Balance** — Ask whether the accounts balance for the period.
- **Vendor Balance** — Ask what you owe each vendor, in summary.
- **Vendor Balance Detail** — Ask which transactions sit behind a vendor balance.

## Why export QuickBooks to Claude — real life cases

A controller can put these questions to Claude after the reports refresh.

- **Month-end profit and loss, summary beside detail**

  Run Profit and Loss Summary and Profit and Loss Detail for the same Report period, this month or last month, with Display columns by set to Month. Ask Claude where a summary total does not have a matching story in the detail. Flat structure keeps the rows easy to question when QuickBooks-style format is harder to read in chat.

- **Who owes you, as of a real date**

  AR Aging Summary gives the buckets, and AR Aging Detail gives the items inside them. Set Report date to the as-of day you were asked for, including today when the aging should be current. Ask Claude which customers sit in the older buckets, and pull Customer Balance plus Customer Balance Detail when the follow-up is the open balance rather than the aging bands.

- **Who you owe, vendor by vendor**

  AP Aging Summary and AP Aging Detail use that same Report date. Ask Claude which vendors are past due, then add Vendor Balance and Vendor Balance Detail when someone wants the transactions under a single vendor. Expenses by Vendor answers a different cut: where the spend went, not only what is still unpaid.

- **Does the sheet agree with cash**

  Balance Sheet, Trial Balance, and Cash Flow for one Report period are three flows. Ask Claude whether the cash movement lines up with the sheet, and whether Trial Balance still ties. Display columns by Total is enough when you want the period as a whole. Month or Quarter is the breakout when the question is how the quarter built up.

- **Sales cut four ways**

  Sales by Class Summary, Sales by Customer, Sales by Department, and Sales by Product are the four cuts. Display columns by already includes Classes, Departments, Customers, and Products and Services on summary reports, so the column breakout and the report name can answer different questions. Ask Claude which cut explains a variance, and add Customer Income when the question is income by customer rather than sales alone.

- **Trace a number into the ledger**

  General Ledger Detail, Journal Report, Transaction List, and Transaction List with Splits are how a statement total becomes individual lines. Ask Claude to follow a figure into the journal and then into the splits. Transaction List by Customer and Transaction List by Vendor are the same list gathered around one party. When the report needs a tighter request than Report period, the user still sets Query parameters.

- **What inventory is worth right now**

  Inventory Valuation Summary is the report for that question. Set Report period to today, or to month-to-date if you want the movement so far this month. Ask Claude what inventory is worth, and use Columns to keep the valuation fields the question actually names. Values-by-row format is the structure to pick when each value should stand on its own row.

- **Tax totals and the chart behind them**

  Tax Summary answers the tax question for the Report period, including fiscal quarter and fiscal year and their to-date forms. Account List Detail tells Claude what those accounts are. Ask how the tax totals sit against the accounts, and use a custom span with Start date and End date when the fiscal defaults are the wrong window. `{{365daysago}}` on Start date is the trailing-year version of that custom span.

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
- [Connect Shopify to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-shopify-to-claude.md)
- [Connect TikTok Ads to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-ads-to-claude.md)
- [Connect TikTok Organic to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-tiktok-organic-to-claude.md)
- [Connect WooCommerce to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-woocommerce-to-claude.md)
- [Connect Xero to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-xero-to-claude.md)
- [Connect YouTube Analytics to Claude](https://github.com/coupler-io/top-claude-integrations/blob/main/connect-youtube-analytics-to-claude.md)

