# Top Claude Integrations for Marketers in 2026

Send data from marketing, sales, and finance apps to Claude with no code. Explore Coupler.io's top integrations: what data you can move, why teams ask Claude about it, and how to set it up in minutes.

Each page in this repo covers one source and answers the same three questions: how do I set the export up, what data can I actually get, and why would I bother.

## Where to find what

| If you want to know | Go to |
| --- | --- |
| Which screens and fields the setup wizard has | **How to export** — one subsection per wizard step, with the real field names |
| How to let the in-app AI Agent build the flow instead | **How to export → Bonus**, at the end of that section |
| Which reports, objects, or entities are available | **What data can you export** — one bullet per data category |
| Whether a specific metric or breakdown exists | **How to export → Metrics and dimensions** step, on sources that have one |
| How often data can refresh | **How to export → Schedule** step |
| How Claude gets connected | **How to export → Claude destination** step |
| What other teams ask Claude | **Why export** — the use cases |
| Another source that Claude can read | **Other Claude integrations**, at the bottom of any page |

## How each page is structured

Every page follows the same order, so once you have read one you can skim the rest.

1. **Frontmatter** — machine-readable metadata (see below).
2. **Source and destination logos**, then the **H1**.
3. **Intro paragraph** — the limitation in the source's own interface, and what Coupler.io does so Claude can answer from that data.
4. **How to export `{source}` data to Claude** — the setup walkthrough. One `###` subsection per wizard step, in the order you meet them. Step names and field names are taken verbatim from the product. The final subsection is a bonus: describe the report in plain language and the Coupler.io AI Agent, in the app's right sidebar, configures the flow for you. That agent is separate from Claude itself.
5. **What data can you export from `{source}` to Claude with Coupler.io?** — every data category the connector exposes, one bullet each, with what it is useful to ask about. Where a source offers dozens of report types, closely related ones are grouped but still named individually. Google Analytics has no report-type field, so its bullets are editorial groupings of real GA4 metric and dimension labels, and the page says so.
6. **Why export `{source}` to Claude — real life cases** — seven or eight concrete questions teams ask once the data is connected.
7. **Other Claude integrations** — links to every other page in this repo.

### Frontmatter fields

| Field | Meaning |
| --- | --- |
| `title` | The page's H1 |
| `slug` | URL-safe identifier, always matches the filename |
| `canonical` | Self-referencing canonical URL for this page |
| `source` | The connector's exact name in the Coupler.io app, which can differ slightly from the title |
| `destination` | Always Claude in this repo |
| `meta_title` | Same as `title` |
| `meta_description` | Search and social summary |

The `source` field is worth a look before you go hunting in the app: the QuickBooks connector is listed as *QuickBooks Reports*, LinkedIn Public Data as *LinkedIn Company Pages*, YouTube Analytics as *YouTube*, Google Analytics as *Google Analytics 4 (GA4)*, Facebook Ads as *Facebook Ads (Meta Ads)*, and Microsoft Ads as *Microsoft Ads (Bing Ads)*.

## Conventions

- **Markdown only.** No HTML, so headings and lists stay machine-readable and the pages chunk cleanly for retrieval.
- **Logos** are referenced from `static.coupler.io`, the same asset host the Coupler.io app uses, rather than committed as files. Claude's destination config key is `claude-desktop`, which has no SVG there. These pages use `claude.svg`, the file the marketing site already hot-links.
- **Cross-page links** are absolute GitHub URLs so they still resolve if a page is quoted or scraped out of context.
- **Field and step names** are verbatim from the product. Only the explanatory copy around them is written for this repo.
- Claude does not store a table. There is no dataset name, region, or replace-versus-append setting on these pages. The schedule refreshes the dataset Claude answers from.

## Integrations

### Ads and paid media

- [Connect Facebook Ads to Claude](./connect-facebook-ads-to-claude.md)
- [Connect Google Ads to Claude](./connect-google-ads-to-claude.md)
- [Connect Instagram Ads to Claude](./connect-instagram-ads-to-claude.md)
- [Connect LinkedIn Ads to Claude](./connect-linkedin-ads-to-claude.md)
- [Connect Microsoft Ads to Claude](./connect-microsoft-ads-to-claude.md)
- [Connect TikTok Ads to Claude](./connect-tiktok-ads-to-claude.md)

### Organic social

- [Connect Facebook Page Insights to Claude](./connect-facebook-page-insights-to-claude.md)
- [Connect Instagram Insights to Claude](./connect-instagram-insights-to-claude.md)
- [Connect LinkedIn Public Data to Claude](./connect-linkedin-public-data-to-claude.md)
- [Connect TikTok Organic to Claude](./connect-tiktok-organic-to-claude.md)
- [Connect YouTube Analytics to Claude](./connect-youtube-analytics-to-claude.md)

### Web and search analytics

- [Connect Google Analytics to Claude](./connect-google-analytics-to-claude.md)
- [Connect Google Search Console to Claude](./connect-google-search-console-to-claude.md)

### Ecommerce

- [Connect Shopify to Claude](./connect-shopify-to-claude.md)
- [Connect WooCommerce to Claude](./connect-woocommerce-to-claude.md)

### Finance and accounting

- [Connect QuickBooks to Claude](./connect-quickbooks-to-claude.md)
- [Connect Xero to Claude](./connect-xero-to-claude.md)
