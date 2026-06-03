# 003 - Repo Orientation for MarketLab Workshop

I am starting the MarketLab workshop and want a concise repo orientation before writing code.

Inspect the repo before answering. Use the actual files, folders, commands, and config in this repo. Do not guess; if something is missing, say it is not present.

Keep each section short. Include only the most important files and commands for a beginner's first pass.

Explain the repo using these sections:

## 1. Mental model

In 3-5 sentences, explain how the app is organized. Cover Next.js App Router routes/layouts, Server Components vs. `"use client"` components, Server Actions if present, and Supabase if present.

## 2. Important folders and files

Provide a table:

| path | purpose | why it matters |
| ---- | ------- | -------------- |

Cover the key existing paths for routes, components, shared libraries, Supabase clients, generated database types, migrations/seed data, global styles, and utilities. Aim for roughly 8-12 rows. Skip anything that does not exist, plus incidental assets or config files that are not useful for a first pass.

## 3. Commands

Use `Taskfile.yml` as the source of truth.

Provide a table:

| task command | what it does | when to use it |
| ------------ | ------------ | -------------- |

Cover the relevant existing tasks for setup, dev, Supabase login/link, database push/types, checks, formatting/linting, typechecking, tests, and full verification. Skip optional build and hook tasks unless they are central to the workshop flow. Mention matching `package.json` scripts only when useful.

## 4. Supabase setup notes

Explain where Supabase clients, generated types, migrations, seed data, and expected environment variables live. Also summarize what a participant needs before running the app locally.

## 5. Testing and quality checks

Explain the test framework, linting/formatting tools, typechecking command, and the single best command to run before considering work complete.
