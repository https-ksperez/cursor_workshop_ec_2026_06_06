# 003 - Repo Orientation For MarketLab Workshop

I am starting the MarketLab workshop and want to understand the existing repo before writing code. Do not change files. Inspect the repo first, especially `README.md`, `Taskfile.yml`, `package.json`, `src/app`, `src/components`, `src/lib`, and `supabase/`. Keep the explanation concise and beginner-friendly.

Explain the repo in these sections:

## Mental model

Summarize how the app is organized in 3-5 sentences, including App Router routes/layouts, Server Components by default, Server Actions for mutations, and Supabase for auth, data, and storage.

## Key folders and files

Provide a table with columns `path`, `purpose`, and `why it matters`. Cover `src/app`, `src/components`, `src/lib`, `src/lib/supabase`, `supabase/`, global styles, shared utilities, and the Supabase browser/server clients. Use the actual paths in this repo and skip anything that does not exist.

## Commands

Use `Taskfile.yml` as the source of truth. Provide a table with columns `task command`, `what it does`, and `when to use it`. Cover setup, dev, db login/link/push/types, check/lint/format, typecheck, tests, and full verification. Note the matching `package.json` script where useful.

## Supabase notes

Explain where the clients, generated database types, migrations, seed data, and expected environment variables live, plus what is required to run the app locally.

## Testing and quality

Name the test framework, lint/format tooling, and the single command to run before considering work done.

## First-change recommendation

Recommend the safest place to make the first workshop change and what to avoid touching too early.

## Risks or missing setup

End with a short checklist of anything that could block a participant.
