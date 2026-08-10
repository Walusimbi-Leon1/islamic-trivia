# Islamic Trivia 🕌

Fast-paced multiplayer Islamic trivia for **Discord Activities** — a dedicated
site that shares the **exact same backend, questions, and real-time database**
as [Quran Trivia](https://github.com/Walusimbi-Leon1/quran-trivia).

- **Live:** https://islamic-trivia.walusimbileon1.workers.dev
- **Discord app:** Islamic Trivia (client ID `1536204473582489650`)
- **Question bank:** generated from the SGSS Quran (same Firebase bank as Quran Trivia)
- **Leaderboard:** shared with Quran Trivia (same namespace — one leaderboard for both apps)

## Architecture

- Cloudflare Worker (static + `/firebase/*` RTDB proxy + `/api/exchange` confidential OAuth)
- Firebase Realtime Database: `bible-game-21-default-rtdb.firebaseio.com`
- Question generation via GitHub Actions + opencode.ai (big-pickle) — see `.github/workflows/generate-questions.yml`

## Deploy

```bash
CF_API_TOKEN=... DISCORD_CLIENT_ID=1536204473582489650 DISCORD_CLIENT_SECRET=... bash deploy.sh
# or register/update the workers.dev route:
npx wrangler deploy
```

Secrets policy: **no secrets in this repo.** `DISCORD_CLIENT_SECRET` is an
encrypted Cloudflare Worker secret; `OPENCODE_API_KEY` is a GitHub Actions secret.
