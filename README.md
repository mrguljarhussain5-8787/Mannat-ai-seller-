# Mannat AI Seller

Photo -> AI listing (title, description, keywords, category, variants) for Meesho, Flipkart, Amazon.

## 1. Backend (Cloudflare Worker, free, doable from a phone browser)
1. Create an Anthropic API key at console.anthropic.com.
2. In dash.cloudflare.com > Workers & Pages > Create > Hello World > Deploy, then Edit code.
3. Paste backend/worker.js, Deploy.
4. Settings > Variables and Secrets: add secrets ANTHROPIC_API_KEY and APP_TOKEN (any long random string).
5. Copy the worker URL (https://something.workers.dev).

## 2. Build the APK (GitHub Actions, no computer needed)
1. Create a GitHub repo, upload all files of this project (keep the .github folder), branch main.
2. Actions tab > Build APK > run. After ~5 min, open Releases > "latest" > download MannatAISeller.apk.
3. Install on Android (allow "install unknown apps" for your browser).

## 3. In the app
Setup tab > paste Worker URL + APP_TOKEN > Save. Create tab > pick photo > Generate.

## Marketplace notes
Amazon SP-API and Flipkart Seller API need approved seller credentials; Meesho has no public listing API.
This version never logs in or submits: "Autofill" copies the listing and opens the seller panel; you paste and confirm.

## Notes
- Builds are signed with the fixed key app/mannat.jks, so each new build installs as an update over the old one. This key is for personal sideloading only; make your own before publishing on Play Store.
- Drafts now keep a small thumbnail of the photo.
