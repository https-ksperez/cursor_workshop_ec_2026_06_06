# 002 - Configure Supabase Env And Link Project

Configure Supabase using the Taskfile commands.

Do only this setup task. Do not create schema, run migrations, seed data, or change app code.

If you do not have the project ref, ask for it and stop.

## Run These Commands

1. If `.env.local` does not exist, run:

```bash
task setup
```

2. Run:

```bash
task db:login
```

Complete the Supabase browser login when the window opens, then wait for the command to finish. If the browser does not open, login fails, or the command stalls, stop and report the issue.

3. Create or update `.env.local` using only the variable names from `.env.example`:

- `SUPABASE_PROJECT_REF`
- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY`

Use the project ref, the matching Supabase project URL, and the public publishable/anon key. Do not use a service-role key.

4. Run:

```bash
SUPABASE_PROJECT_REF=<YOUR_PROJECT_REF> task db:link
```

Use only Taskfile commands for setup and Supabase work. Do not run raw `supabase login`, `supabase link`, migrations, seed data, or unrelated app commands.

When done, report which values were set, masking any key value except the first and last few characters.
