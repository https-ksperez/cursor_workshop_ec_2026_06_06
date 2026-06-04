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

## Tests

Add or update focused tests for:

- chart renders on the market detail page
- current Yes chance is shown
- closed market shows buying unavailable
- existing market detail behavior still works
