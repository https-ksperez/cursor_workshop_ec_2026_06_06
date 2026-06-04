# 007 - Add Market Detail Chart And Buy Copy Cleanup

Extend the existing `/markets/[id]` page. Read the current implementation first and build on what already exists: list page routing, `fetchMarketById`, `notFound()`, back link, info card, `MarketOutcomes`, `MarketBuyPlaceholder`, `isMarketBuyable()`, seed data, and tests.

## Chart

Add a read-only Polymarket-style chart section to the market detail page:

- Show a hero number for the current **Yes** chance, e.g. `62%`.
- Show a line chart of Yes probability over time.
  - Y axis: `0-100%`
  - X axis: time
- Add simple range toggles if practical: `1D` / `1W` / `ALL`.
- Use `market_price_history` seed data if it exists.
- If not, create a deterministic mock series from `market.id` in `src/lib/`.
- Keep the chart stable for tests.
- Use SVG/CSS or a small local component; do not add chart packages unless unavoidable.
- Keep the card layout consistent with the market list/detail pages.
- Make it responsive and light/dark compatible.
- Do not add trading, auth, or mutations.

## Buy Section

Update the existing buy placeholder copy:

- Heading: **Buy shares**
- Copy: **1 fake cent spent = 1 share cent**
- Muted placeholders for **Buy Yes** and **Buy No**
- Remove "coming soon" wording.
- No inputs, server actions, RPCs, or database writes.
- If the market is closed, resolved, or draft, show buying as unavailable.
- Closed markets should clearly mention they are closed.

## Tests

Add or update focused tests for:

- chart renders on the market detail page
- current Yes chance is shown
- buy section does not include "coming soon"
- closed market shows buying unavailable
- existing market detail behavior still works

Run `task verify` when done.
