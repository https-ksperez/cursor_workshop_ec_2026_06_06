# 010 - My Positions View

Build a My Positions page where signed-in users can see the markets they have positions in.

Assume Supabase is linked and the schema, seed markets, market list/detail pages, auth UI, and Buy Yes/No flow already exist. Follow `AGENTS.md`, reuse existing patterns, and keep the implementation small, readable, and workshop-friendly.

## Requirements

- Create a My Positions page.
- Add header navigation to it.
- Signed-in users see only their own positions.
- Signed-out users see a clear sign-in message.
- Fetch positions from Supabase using the authenticated user context.
- Include related market information.
- Link each position back to the market detail page.
- Show a good empty state when the user has no positions.

Each position should show:

- market title
- market status
- market close date
- Yes shares
- No shares
- invested fake amount

## Security

- Do not trust `user_id` from the client.
- Rely on RLS so users can only read their own positions.
- Do not expose another user's positions.
- Do not add client-side insert/update/delete behavior for positions.

## Design

- Use a clean dashboard-style layout.
- Use simple cards or a compact table, whichever fits the existing UI better.
- Keep styling consistent with the rest of the app.
- Make it responsive and light/dark compatible.
- Do not add charts, images, or decorative hero sections.

## Testing / Verification

If the repo already has a test setup, add focused tests for:

- signed-out state
- empty positions state
- rendering positions with Yes shares
- rendering positions with No shares
- displaying invested fake amount
- linking back to market detail pages
- not exposing positions for another user, if practical

If automated tests are not practical, document a small manual verification path:

- run the app
- sign in
- buy Yes or No shares in an open market
- open My Positions
- confirm the market appears
- confirm Yes/No shares are shown correctly
- confirm invested fake amount is shown
- confirm the position links back to the market detail page
- sign out
- confirm positions are not visible
