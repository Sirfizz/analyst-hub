# Analyst Hub — Deployment Guide

## Project Structure
```
analyst-hub/
├── api/
│   └── search.js          ← Serverless API route (hides your API key)
├── public/
│   └── index.html          ← The full app (frontend)
├── package.json
├── vercel.json
└── README.md
```

## Deploy to Vercel (3 steps)

### Step 1: Push to GitHub
```bash
cd analyst-hub
git init
git add .
git commit -m "Analyst Hub v1.0"
git remote add origin https://github.com/YOUR_USERNAME/analyst-hub.git
git push -u origin main
```

### Step 2: Deploy on Vercel
1. Go to [vercel.com/new](https://vercel.com/new)
2. Import your `analyst-hub` GitHub repo
3. Click **Deploy** (no build settings needed — it works out of the box)

### Step 3: Add your API Key
1. In your Vercel project dashboard, go to **Settings → Environment Variables**
2. Add:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-...` (your key from console.anthropic.com)
3. Click **Save**
4. Go to **Deployments** → click the **⋮** menu on the latest deployment → **Redeploy**

## Done!
Your Analyst Hub is now live at `https://analyst-hub.vercel.app` (or your custom domain).

Share the URL with your team — no API key needed on their end.

## Notes
- The API key is stored securely in Vercel's environment variables (never sent to the browser)
- All API calls go through `/api/search` which proxies to Anthropic server-side
- Web search is enabled for real-time results
- Free Vercel tier supports ~100K requests/month

---
*Desk of Mafia's Creatives*
