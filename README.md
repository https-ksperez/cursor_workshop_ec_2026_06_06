# MarketLab

MarketLab is a focused Cursor workshop app: a fake-money prediction market built with Next.js, React, Tailwind CSS, shadcn-style primitives, and Supabase Auth, Database, and Storage.

## Stack

- Next.js App Router, React, TypeScript
- Tailwind CSS and shadcn-style UI primitives
- Supabase Auth, Postgres, Storage, RLS, and RPC
- Zod, Vitest, Playwright, Biome, Bun

## Setup

```bash
mise install
bun install
cp .env.example .env.local
```

Without Supabase env vars, the app renders demo markets and disables mutations.

For live auth, markets, trading, and image uploads, create a Supabase project and set:

```bash
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_PROJECT_REF=
```

The `NEXT_PUBLIC_*` values are used by the app. `SUPABASE_PROJECT_REF` is only for Supabase CLI scripts such as linking the hosted project and generating types.

Apply migrations and seed demo markets to the hosted project:

```bash
bun run db:link
bun run db:push
```

For workshop speed, disable email confirmations in Supabase Auth settings.

Start the app:

```bash
bun run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Commands

- `bun run dev` - start the app.
- `bun run check` - run Biome checks.
- `bun run typecheck` - generate Next route types and run TypeScript.
- `bun run test:run` - run unit tests.
- `bun run e2e` - run the Playwright smoke test.
- `bun run db:link` - link the repo to the hosted Supabase project.
- `bun run db:push` - apply migrations and seed demo markets.
- `bun run db:types` - generate Supabase TypeScript types.
