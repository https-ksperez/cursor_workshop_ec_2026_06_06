# 003 - Repo Orientation for MarketLab Workshop

I am starting the MarketLab workshop and want to understand the existing repo before writing code.

Inspect the repo before answering. Use the actual files, folders, commands, and config that exist in this repo. Do not guess; if something is missing, say it is not present.

Keep the explanation concise, beginner-friendly, and workshop-focused.

Explain the repo using these sections:

## 1. Mental model

Summarize how the app is organized in 3-5 sentences.

Include:

- How the Next.js App Router is structured with routes and layouts
- That components are Server Components by default unless marked with `"use client"`
- How Server Actions are used for mutations, if present
- How Supabase is used for auth, data, and storage, if present

## 2. Important folders and files

Provide a table with these columns:

| path | purpose | why it matters |
| ---- | ------- | -------------- |

Cover the important existing paths only, including:

- `src/app`
- `src/components`
- `src/lib`
- `src/lib/supabase`
- `supabase/`
- global styles
- shared utilities
- Supabase browser client
- Supabase server client
- generated database types

Skip anything that does not exist in this repo.

## 3. Commands

Use `Taskfile.yml` as the source of truth.

Provide a table with these columns:

| task command | what it does | when to use it |
| ------------ | ------------ | -------------- |

Cover the relevant tasks that exist for:

- setup
- dev
- Supabase login
- Supabase link
- database push
- database types
- check
- lint
- format
- typecheck
- tests
- full verification

When useful, mention the matching `package.json` script, but treat `Taskfile.yml` as the main source of truth.

## 4. Supabase setup notes

Explain where these live in the repo:

- Supabase clients
- generated database types
- migrations
- seed data
- expected environment variables

Also explain what a participant needs before running the app locally, such as:

- dependency installation
- local environment variables
- Supabase project connection
- database migrations/types, if required

## 5. Testing and quality checks

Explain:

- The test framework used by the repo
- The linting tool
- The formatting tool
- The typechecking command
- The single best command to run before considering work complete
