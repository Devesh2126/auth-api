# Quick setup

1. Unzip this folder somewhere clean, e.g. `C:\AuthAPI` (avoid nesting it
   inside another project folder — that's what caused the "Cannot find
   module" error earlier: a stray subfolder without its own
   `node_modules`).

2. Open a terminal **in this exact folder** and run:
   ```bash
   npm install
   ```

3. Open `.env` and paste in your real Supabase **anon key** (Project
   Settings → API → "anon public" key). The `SUPABASE_URL` is already
   filled in from your earlier session.

4. Start the server:
   ```bash
   node index.js
   ```
   You should see: `Server running and connected to Supabase`

5. Test it:
   ```bash
   curl -i -X POST http://localhost:3000/auth/signup -H "Content-Type: application/json" -d "{\"email\":\"deveshrawat2126+test2@gmail.com\",\"password\":\"password123\"}"
   ```
   (use a fresh +test2 email if +test1 is already registered)

6. Swagger docs: http://localhost:3000/docs

## Everything included

- `index.js` — all 6 routes (signup, login, logout, public/info,
  protected/profile, protected/dashboard) + the `requireAuth` middleware,
  correctly structured as sibling routes (not nested — that was the bug
  from before)
- `openapi.json` — Swagger config with the bearer auth padlock applied to
  the 3 protected routes only
- `package.json` — all 4 dependencies
- `.env` / `.env.example`
- `.gitignore` — `.env` is excluded, `node_modules` is excluded

## If you need to push this to GitHub

```bash
git init
git add .
git commit -m "Complete auth API: signup, login, logout, protected routes, swagger"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/auth-api.git
git push -u origin main
```

Since this is being committed in one shot rather than stage-by-stage, if
your assignment wants ≥6 commits, you can split this into a few follow-up
commits after pushing (e.g. a docs tweak, a README pass, a stretch goal)
rather than needing 6 *right now*.
