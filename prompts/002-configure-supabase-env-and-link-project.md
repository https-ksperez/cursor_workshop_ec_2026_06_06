# 002 - Configure Supabase Env And Link Project

Configure Supabase for project `<YOUR_PROJECT_REF>`.

Do only this setup task. Do not create schema, run migrations, seed data, or change app code.

## Steps

1. If the Supabase project ref is not provided, ask for it and stop.
2. Run `task db:login`.
3. Complete the Supabase browser login when the window opens, then wait for the command to finish.
4. If the browser does not open, login fails, or the command stalls, stop and report the issue. Do not try unrelated commands.
5. Create or update `.env.local` using the variable names from `.env.example`.
6. Set the project ref and URL.
7. Add the project's public publishable/anon key. Do not use a service-role key.
8. Run `task db:link`.

When done, report which values were set, masking any key value except the first and last few characters.
