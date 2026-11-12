# Valtus — Dashboard prototype + production backend foundation

## Open the HTML version
Open `index.html` in a browser, or run `python3 -m http.server 8000` from this directory and visit http://localhost:8000.

This is an interactive standalone HTML demo. It includes dashboard, properties, expense analyzer, findings, report export, pricing, and settings. Properties and findings are saved in localStorage in your browser. Sample financial data is illustrative. CSV analysis occurs locally. No cloud uploads or real charges occur.

## Included production foundations
- `supabase/schema.sql`: multi-tenant organization/property/import/transaction/finding/report schema with read policies and tenant checks.
- `server/index.js`: Express API scaffold with verified Stripe webhook, authenticated organization lookup, and checkout session creation with membership checks.
- `server/.env.example`: configuration variables.

## To run backend scaffold
1. Create a Supabase project and apply `supabase/schema.sql` in the SQL editor.
2. Configure Supabase authentication and **implement secure atomic organization onboarding**. This is NOT included yet.
3. Create three recurring Stripe prices and set `.env` variables in `server/` (copy `.env.example` to `.env`).
4. `cd server && npm install && npm start`.
5. Configure Stripe to send subscription events to `/api/stripe/webhook` and use a valid signing secret.
6. Wire the HTML front end to Supabase Auth and the backend API before offering live subscriptions.

## Not yet implemented
- Front-end Supabase login, signup, and tenant-scoped data fetching
- Secure storage/upload ingestion, server-side CSV normalization and reconciliation
- Production financial analysis workers and test coverage
- Automated monthly jobs, email delivery, retries, and alerting
- Customer self-service billing portal, idempotent webhook event persistence
- Organization onboarding, privacy/legal terms, rate limits, complete security review

**Do not upload confidential customer records or accept live payments until those features are implemented, tested, and reviewed.**

## Updated proposed pricing
Starter: $29/month or $290/year (5 properties). Professional: $79/month or $790/year (25 properties). Business: $149/month or $1490/year (100 properties). Annual billing gives two months free. A 14-day no-card trial is shown in the HTML demo but is **not implemented** in the backend; do not advertise an active trial until a secure entitlement and expiry system is built. The backend checkout scaffold now accepts `tier` (`starter`, `professional`, `business`) and `cycle` (`monthly`, `annual`), with matching environment variable names.

## Branding update
Modern Minimalist theme: stone background, charcoal sidebar, sage accents, DM Sans headings and Inter body text. Fonts load from Google Fonts when online and use system fallbacks offline. All existing demo interactions and backend scaffold remain unchanged.


## Heritage Finance + Financial Intelligence update
- Valtus Heritage Finance palette (forest green, champagne gold, ivory) and serif headings.
- New Income & Financials page: monthly property financial inputs, CSV import/export, effective gross income, NOI, net income and cash flow.
- New financial KPI cards, interactive income/NOI trend chart, financial statement, and property comparison table with hover previews and clickable right-hand detail panels.
- Financials are seeded with clearly labeled synthetic demo values, stored in browser localStorage, not a production financial ledger.
- CSV columns: month,property,grossRent,otherIncome,vacancyLoss,operatingExpenses,interest,depreciation,principal,capex. Import matches existing properties by name.
- Existing expense analyzer, properties, findings, reports and pricing are retained.
- No production authentication, payment processing, or server-side financial storage is enabled.

## Sponsored banner (prototype)

A single, clearly labeled sponsored banner appears beneath the top navigation on every page. In Settings, a demo administrator can change sponsor name, copy, link, or turn it off. Settings are saved in the current browser only. No third-party advertising scripts, impression tracking, billing, or real campaign management are connected. A production rollout needs server-side admin permissions, sponsor approval, inventory management, and privacy review.


## Google AdSense (one banner)

In Settings, enter an approved AdSense publisher ID (`ca-pub-` plus 16 digits), a numeric ad slot ID, and enable the banner. Only one manual ad placement is created below the top bar. Disable **Auto ads** in the AdSense dashboard; other scripts or external page configuration can otherwise create additional ads. No ad is displayed until valid IDs are entered and enabled. Ad blockers, consent requirements, account approval, and inventory may prevent rendering.

This prototype stores configuration in localStorage, so it does not centrally configure all users. Production needs server-side site-wide configuration and privacy/consent implementation. Never send confidential property information to ad targeting parameters.


## Entity performance & report studio (new)
- Overview entity dropdown filters financial KPIs, financial statement, 6-month trend, drilldowns and comparison table.
- Reports > Report Studio supports entity/month/report selection, on-screen preview, Excel-compatible CSV exports, and print/save-as-PDF reports.
- Reports: income statement, performance analytics, trend, property comparison, expense findings, and underlying financial data.
- All calculations use existing browser-local demo financial data. This is not a cloud reporting service or verified accounting integration.
- Export CSV values are escaped according to CSV rules; only import trusted CSV files into spreadsheet applications.


## Budget & Forecast module
Select Budget & Forecast from the sidebar. Choose a property or the entire portfolio, and a 3-, 6-, or 12-month horizon. Forecasts use trailing available historical monthly averages and editable annual growth assumptions. Add dated one-time or recurring bills (property taxes, insurance, renewals), click chart months for detail, and export a forecast CSV. Bills are incremental to historical expenses; avoid double counting bills already included in the baseline. Data remains in local browser storage; forecasts are illustrative, not tax or accounting advice.
