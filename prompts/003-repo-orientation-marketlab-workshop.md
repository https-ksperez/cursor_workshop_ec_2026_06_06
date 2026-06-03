# 003 - Repo Orientation for MarketLab Workshop

I am starting the MarketLab workshop and want to understand the existing repo before writing code.

Work in read-only mode:

- Do not edit, create, delete, or rename files.
- Do not install packages.
- Do not run migrations, database pushes, or deployment commands.
- Only inspect the repo and explain what is already there.

Inspect the repo first, especially these files and folders if they exist:

- `README.md`
- `Taskfile.yml`
- `package.json`
- `src/app`
- `src/components`
- `src/lib`
- `src/lib/supabase`
- `supabase/`
- global styles
- shared utilities

Use the actual paths in this repo. Skip any file or folder that does not exist. Do not guess. If something is missing, say it is not present.

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

## 6. Safest first place to edit

Recommend the best first area for a participant to modify during the workshop.

Explain:

- Why it is a safe starting point
- What kind of change is appropriate there
- What files or systems to avoid touching too early, such as auth, database migrations, generated types, or shared Supabase clients

## 7. Setup blockers checklist

End with a short checklist of things that could block a participant from running or completing the workshop.

Examples:

- Missing environment variables
- Supabase project not linked
- Dependencies not installed
- Database migrations not applied
- Generated types out of date
- Wrong Node or package manager version
- Required CLI tools missing

Keep this checklist practical and short.
