# AGENTS.md

## Project

MarketLab is a fake-money prediction market app for a 2-hour Cursor workshop. Keep changes small, teachable, and easy for participants to follow.

## Stack

- Next.js App Router with React Server Components by default.
- Server Actions for mutations.
- Supabase Auth, Database, and Storage via `@supabase/ssr` and `@supabase/supabase-js`.
- Bun, TypeScript, Tailwind CSS, Biome, Vitest, and Task.

Do not add dependencies or replace the stack unless the user explicitly asks. Before editing Next.js APIs or routing behavior, read the relevant local guide in `node_modules/next/dist/docs/`; this repo may use newer conventions than your training data.

## Project Map

- `src/app/`: App Router routes, layouts, and global styles.
- `src/components/`: Reusable UI and MarketLab components.
- `src/lib/`: Shared utilities and Supabase clients.
- `supabase/`: Supabase configuration, migrations, and seed data.
- `Taskfile.yml`: Source of truth for project commands.

## Commands

Run commands through `task` when a task exists.

- Setup: `task setup`
- Dev server: `task dev`
- Format/lint check: `task check`
- Typecheck: `task typecheck`
- Unit tests once: `task test:run`
- Full verification: `task verify`
- List tasks: `task --list`

If `task` is unavailable, activate mise in the current shell first, then retry the `task` command. Do not use `mise exec -- task`.

## Implementation Rules

- Prefer Server Components. Add `"use client"` only for browser-only state, effects, or event handlers.
- Keep UI components focused and workshop-readable; avoid broad refactors and clever abstractions.
- Use existing components and utilities before creating new ones.
- Keep markets fictional and non-political.
- Treat balances as fake cents. Do not add real payments, financial claims, trading advice, email, analytics, or production monitoring.

## Supabase Rules

- Supabase migrations are the schema source of truth.
- Every Server Action must verify authentication and authorization before mutation.
- Prefer RLS and Supabase RPC functions for balance-changing operations.
- Public market data may be readable; profiles, positions, and settlements must stay owner-scoped.
- After adding migrations or seed data, run `task db:push` and `task db:types` once the repo is linked to the hosted Supabase project.

## Validation

- Run the smallest relevant checks while iterating.
- For code changes, finish with `task verify` when practical.
- For hook changes, run `task hooks:validate` and `task hooks:run`.
- If a required check cannot run, report the reason and the remaining risk.
