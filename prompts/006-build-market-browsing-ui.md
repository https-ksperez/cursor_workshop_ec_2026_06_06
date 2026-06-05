# 006 - Build MarketLab Market Browsing UI

Build the MarketLab market browsing UI.

Create a clean, modern market list page that feels like a simple fake-money market dashboard.

The page should quickly communicate: "Browse fictional Yes/No markets using fake money."

## Design Requirements

- Use a clean dashboard-style layout.
- Do not use a large hero image, stock image, or decorative picture.
- If the starter/template image is still being shown, remove it from the UI.
- If that image file is unused after removal, delete it.
- The market list should be the main focus of the page.
- Use clear spacing, readable typography, simple cards, and good visual hierarchy.
- Make the layout responsive.
- Support both light and dark theme.
- If the project already has theme support, reuse it.
- If theme support is missing, add the smallest reasonable light/dark theme implementation.
- Add a simple theme toggle in the header.
- Persist the selected theme when practical.
- Respect system theme by default when practical.
- Avoid adding dependencies unless clearly necessary.

## Header Requirements

- Add or update a simple app header.
- Include:
  - app name: MarketLab
  - navigation to the markets page
  - theme toggle
- Keep the header ready for auth state later, but do not implement auth in this step unless it already exists.
- Do not add unnecessary navigation items.

## Market List Requirements

- Create or update the market list page.
- Fetch markets from Supabase.
- Display markets in clean cards.
- Each card should show:
  - title
  - description
  - status
  - close date
  - link or button to view details
- Add a good empty state.
- Make the page work for signed-in and signed-out visitors.
- Reuse existing components where possible.
- Keep styling consistent with the project.

## Market Creation Rules

- Do not add a create market form.
- Do not add market creation UI.
- Do not add client-side insert/update/delete behavior for markets.
- Do not add user-owned markets.
- Do not add admin behavior in this step.
- Markets should come from existing seed data.
- Do not create fake/mock market data in the UI, tests, or fallback code; use Supabase seed data only.
- Run `task db:push` as part of this task so seeded markets are available; do not stop to ask for confirmation first.

## Testing / Verification

If the repo already has a test setup, add focused tests for:

- rendering a list of markets
- empty market state
- status display
- close date display
- theme toggle rendering
- no hero/template image rendered on the market page

If adding tests is not practical yet, document a small manual verification path:

- run the app
- open the market list page
- confirm seeded markets appear
- confirm title, description, status, and close date are visible
- confirm the starter/template image is gone
- confirm light mode works
- confirm dark mode works
- confirm the page works while signed out
- confirm the layout is responsive
