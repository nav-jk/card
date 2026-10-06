# Wallet cards host

Static GitHub Pages site that serves `cards.json` to the ESP32 Wallet app.

## Deploy
1. Rename `w-CHANGE-ME-8f3k29x/` to a long random name (this is your only "password": Pages is public).
2. Create a GitHub repo, push these files to `main`.
3. Repo Settings > Pages > Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
4. After ~1 minute your file is at
   `https://<user>.github.io/<repo>/<your-random-folder>/cards.json`
5. In the firmware set:
   `#define WALLET_URL "https://<user>.github.io/<repo>/<your-random-folder>/cards.json"`
   and leave `WALLET_AUTH ""` (Pages cannot check headers).

## Update cards
Open `index.html` locally (or at `https://<user>.github.io/<repo>/`), edit, download `cards.json`, replace the file in the random folder, commit. Long-press the Wallet screen on the watch to re-sync (Pages caches for about 10 minutes).

## Limits (from the firmware)
8 cards, name 31 bytes, sub 39, code 255, whole JSON under ~8 KB, color as 6 hex digits.

## Privacy
The repo and URL are public. Anyone with the link can read the codes. Don't store anything sensitive; for that, use a private host that checks the `Authorization` header (Cloudflare Worker, etc.).
