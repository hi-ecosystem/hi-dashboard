# hi-dashboard

Central launcher and overview dashboard for the [hi. ecosystem](https://github.com/hi-ecosystem).

**Live:** [hi-health-industry.vercel.app](https://hi-health-industry.vercel.app) *(or your Vercel URL)*

---

## What it does

- **SSO launcher** — sign in once, open any hi. app without logging in again. Session is passed via URL hash.
- **Ecosystem overview** — quick stats, active competitions, and app shortcuts in one place.
- **Animated splash** — `hi.` expands to `health industry.` on load, then collapses back.
- **Mobile view** — on phones, shows a stripped-down screen with direct app links instead of the full dashboard.

---

## Auth flow

1. User enters email → receives a 6-digit OTP via Supabase
2. On verify → session stored in Supabase Auth
3. On clicking an app link → `access_token` + `refresh_token` appended to the target URL as a hash fragment
4. The target app (e.g. DoubleDo) reads the hash and calls `supabase.auth.setSession()` — no second login required

---

## Stack

![HTML](https://img.shields.io/badge/HTML-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=flat-square&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)

Vanilla HTML/CSS/JS — no build step, no framework.

---

## Files

```
index.html   — markup: splash, login overlay, desktop dashboard, mobile screen
style.css    — all styles
app.js       — auth, SSO token passing, charts, dashboard data
vercel.json  — Vercel routing config
```

---

## Local development

```bash
git clone https://github.com/hi-ecosystem/hi-dashboard
cd hi-dashboard
# open index.html in a browser — no build needed
```

Supabase credentials are hardcoded in `app.js` (anon/public key — safe to expose).

---

## Deployment

Connected to Vercel. Every push to `main` auto-deploys.

---

## Part of hi.

| Product | Repo | Description |
|---|---|---|
| **hi-dashboard** | this repo | Central launcher + overview |
| **DoubleDo** | [hi-ecosystem/DoubleDo](https://github.com/hi-ecosystem/DoubleDo) | Habit competition app |
