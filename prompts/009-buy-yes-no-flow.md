# 009 - Buy Yes / No Flow

Build the complete fake-money Buy Yes / No flow.

Assume Supabase is linked and the schema, seed markets, market list/detail pages, auth UI, and profile balance display already exist. Follow `AGENTS.md`, reuse existing patterns, and keep the implementation small, readable, and workshop-friendly.

## Client / Server Boundary

`MarketBuyForm` is a Client Component. Its import tree must not reach `next/headers`, `cookies()`, or `@/lib/supabase/server`.

- Keep server-only Supabase reads/writes in server-only modules.
- Keep client-safe formatting/parsing in a shared module like `src/lib/fake-money.ts`.
- Keep client-safe shared types in modules with no server imports.
- Render the buy form from a Server Component section that loads auth, balance, and position, then passes plain props to the client form.
- Before finishing, trace imports from `market-buy-form.tsx` and confirm none reach server-only APIs.

## Money Model

Users enter fake dollars in the UI, but the database stores cents.

- Display balances as fake dollars, e.g. `$10.00 fake`.
- Accept inputs like `1`, `1.50`, and `10.00`.
- Reject more than two decimal places.
- Convert dollar strings to integer cents server-side.
- Do not use floating point math for balance-changing logic.
- Rule: **1 fake cent spent = 1 share cent**.

## Buy Flow

Add or complete the buy form on `/markets/[id]`.

Signed-in users can:

- choose **Yes** or **No**
- enter fake dollars
- see available fake balance
- submit a buy
- see pending, success, and error states
- avoid duplicate submissions while submitting
- see updated balance and position after success

Signed-out users should be asked to sign in. Closed, resolved, draft, missing, or expired markets are not buyable.

Keep copy clear that this uses fake money, and avoid language that sounds like real investing, gambling, or trading advice. Keep the form responsive, light/dark compatible, and consistent with the market detail page.

## Server Mutation

The buy must happen server-side.

Validate:

- authenticated user
- market exists, is open, and is not past `close_date`
- side is `yes` or `no`
- amount converts to a positive integer cent amount
- user has enough fake balance

On success:

- deduct balance
- create or update the user's position
- increase `yes_shares_cents` or `no_shares_cents`
- increase `invested_cents`
- create a `ledger_entries` row
- return useful success/error results

Prefer an atomic Supabase RPC using `auth.uid()`, called through a Server Action if that matches the project pattern. Server-side validation is the source of truth.

Do not trust `user_id` from the client, expose privileged keys, allow direct browser writes to balances/positions/ledger entries, or allow concurrent buys to make balances negative. Do not add selling, dynamic pricing, settlement, or market creation.

## Verification

Add focused tests where practical for invalid amounts, invalid side, signed-out users, closed/expired markets, overspending, duplicate submissions, Yes/No position updates, balance deduction, ledger creation, UI refresh after success, and `user_id` spoofing.

Run `task verify`. If adding an RPC/migration, run `task db:push` then `task db:types`. Confirm `/markets/[id]` loads without a `next/headers` error from the buy form.

If automated database/RPC/UI tests are not practical, document a short manual path for a signed-in Yes buy, No buy, balance decrease, position increase, invalid amount, overspend rejection, closed market, and signed-out state.
