# 009 - Buy Yes / No Flow

Implement the full fake-money Buy Yes / No flow.

Assume Supabase is linked and the schema, seed markets, market list/detail pages, auth UI, profile balance display, and buy form UI already exist. Follow `AGENTS.md`, reuse existing patterns, and keep the implementation small and workshop-friendly.

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

Connect buying on `/markets/[id]`.

Signed-in users can:

- choose **Yes** or **No**
- enter fake dollars
- see available fake balance
- submit a buy
- see success/error states
- see updated balance and position after success

Signed-out users should be asked to sign in. Closed, resolved, draft, missing, or expired markets are not buyable.

## Server Mutation

The buy must happen server-side.

Validate:

- authenticated user
- market exists and is buyable
- side is `yes` or `no`
- amount converts to a positive integer cent amount
- user has enough fake balance

On success:

- deduct balance
- create or update the user's position
- increase `yes_shares_cents` or `no_shares_cents`
- increase `invested_cents`
- create a `ledger_entries` row

Prefer an atomic Supabase RPC using `auth.uid()`, called through a Server Action if that matches the project pattern. Do not trust `user_id` from the client, expose privileged keys, or allow concurrent buys to make balances negative.

## Verification

Add focused tests where practical for invalid amounts, invalid side, signed-out users, closed/expired markets, overspending, Yes/No position updates, balance deduction, ledger creation, and `user_id` spoofing.

Run `task verify`. If adding an RPC/migration, run `task db:push` then `task db:types`. Confirm `/markets/[id]` loads without a `next/headers` error from the buy form.
