Extend the existing `/markets/[id]` page. Read the current implementation first and build on what already exists: list page routing, `fetchMarketById`, `notFound()`, back link, info card, `MarketOutcomes`, `MarketBuyPlaceholder`, `isMarketBuyable()`, seed data, and tests.

## Chart

Add a read-only probability chart section to the market detail page. The graph must render; do not replace it with an unavailable state.

- Use only the existing prompt 005 schema: `markets`, `positions`, and `ledger_entries`.
- Do not add a price-history table, extra table, seed data, script, or hard-coded market-price records.
- Do not create mock/generated market-price data or a deterministic fake series.
- Compute the current **Yes** chance from aggregate `positions` for this market:
  `yes_total = sum(yes_shares_cents)`, `no_total = sum(no_shares_cents)`, `yes_chance = yes_total / (yes_total + no_total)`.
- If there are no positions yet, use a documented neutral baseline of `50%` because no Yes/No activity exists.
- For the line chart, use real `ledger_entries` for this market when they include enough existing side information in `entry_type`, `description`, or metadata to reconstruct Yes/No activity over time.
- If ledger history is not available yet, render a flat line from `market.created_at` to now at the current computed Yes chance. This is a calculated current-state visualization, not mock market data.
- Label the flat fallback honestly as current market balance/sentiment, not historical price movement.
- Show a line chart with a `0-100%` Y axis, a time X axis, and simple range toggles if practical.
- Never expose per-user positions or ledger rows in the UI; fetch or aggregate server-side and return only market-level totals/points.
- Keep the chart stable for tests.
- Use SVG/CSS or a small local component; do not add chart packages unless unavoidable.
- Keep the card layout consistent with the market list/detail pages.
- Make it responsive and light/dark compatible.
- Do not add trading, auth, or mutations.

## Tests

Add or update focused tests for:

- chart renders on the market detail page
- current Yes chance is calculated from aggregate positions
- neutral `50%` baseline is shown when a market has no positions
- flat current-state line renders when ledger history is unavailable
- closed market shows buying unavailable
- existing market detail behavior still works
