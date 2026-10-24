# Kanso

Habit tracker for phone and laptop: weekly sheet, smooth progress graph, month sheet, yearly stats, timers, streak freezes, weekly review, dark/light mode, installable app (PWA).

## 1. Set up Supabase (accounts, sync, password reset)
1. Create a free project at supabase.com.
2. Open **SQL Editor**, paste everything from `supabase.sql`, press **Run**.
3. **Authentication > URL Configuration**: set **Site URL** to your Vercel address (for example `https://kanso.vercel.app`) and add the same address under **Redirect URLs**. Password-reset links return here.
4. **Project Settings > API**: copy the **Project URL** and the **anon public** key into `config.js`. Never paste the `service_role` key anywhere in this project.
5. Optional: under **Authentication > Providers > Email**, turn "Confirm email" on or off. Supabase's built-in email sender is rate-limited, so add your own SMTP under Authentication settings before sharing the app widely.

If `config.js` is left empty, the app still works in local-only mode (accounts stay in that browser and there is no password reset).

## 2. Deploy
Upload these files to the root of a GitHub repo, then on vercel.com choose Add New > Project, import the repo and press Deploy. No build step.

## How sync works
Each user has one row in `user_data`, protected by row-level security so people can only read and write their own. Changes save on the device first and upload a moment later; the newest copy wins when you sign in or return to the app. Settings shows the sync status.

## Password reset
On the sign-in form press **Forgot password?**, enter your email, open the link from the email on the same device, then choose a new password.

## Manual test checklist
Sign up, confirm email if enabled, add a habit and tick days, sign in on a second device and see the same data, tick a day there and see it on the first, sign out, use Forgot password, set a new one, sign in.
