# Japan Part-time Work Check

Free checker for part-time and side jobs on a Japanese status of residence (資格外活動許可): which statuses may work, comprehensive (28-hour) vs individual permission, rolling 7-day hour windows, the students' 8 h/day long-vacation rule, banned 風俗営業 venues, and the 2026-10-01 change letting Dependent (家族滞在) holders work at pachinko, mahjong and game centers with individual permission.

- Full app and API (Vercel): https://japan-parttime-check.vercel.app
- Checker (GitHub Pages): https://akiba-labs.github.io/japan-parttime-check/

- API: `GET /api/check?status=dependent&job=pachinko&permission=comprehensive&weeklyHours=20` (keyless, CORS), `/api/rules`, `/openapi.json`, `/llms.txt`
- MCP: `japan_parttime_work_check` on https://free-agent-tools.vercel.app/mcp

Sources: Immigration Services Agency pages on 資格外活動許可 (general, Student, Dependent, Designated Activities, procedure), ISA amusement-venue notice (10_00274), MHLW employer guide. Rules as of 2026-10-26.

**Disclaimer:** educational, not legal or immigration advice, not affiliated with the Immigration Services Agency. Only your permission and ISA decide.

Dev:

```
npm ci
npm test
npm run build
npm run build:pages
```

`npm run build` is the Vercel app (checker, JSON API, share pages). `npm run build:pages` writes a static `out/` for GitHub Pages and checks that internal links and assets resolve under `/japan-parttime-check`. Server routes stay in the repo; the Pages script only moves them aside for that build.

GitHub settings: **Settings → Pages → Build and deployment → Source: GitHub Actions**. Pushes to `main` deploy with `.github/workflows/pages.yml`. The copy-paste steps for the other tool repos are at the top of `scripts/build-pages.mjs`.
