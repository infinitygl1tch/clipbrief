# ClipBrief — Deployment Guide

ClipBrief is now **100% free** — no paid tiers, no API keys required by default. It works out of the box using a built-in generator, or you can add Google AI for better results.

---

## Files Overview

| File | Description |
|------|-------------|
| `index.html` | Landing page with SEO meta tags |
| `app.html` | App with usage counter (5/day), built-in clip generator |
| `worker.js` | Optional Cloudflare Worker using Google AI (free tier) |

---

## Quick Start (No Setup Needed!)

1. Go to https://github.com → create a free account
2. Click **New repository** → name it `clipbrief` → set to **Public** → click Create
3. On your new repo page, click **Add file → Upload files**
4. Upload these files:
   - `index.html`
   - `app.html`
5. Click **Settings** (top tab) → **Pages** (left sidebar)
6. Under "Branch", select `main** → click Save
7. Wait 1-2 minutes → your site is live at:
   `https://YOUR_USERNAME.github.io/clipbrief/`

Done! The app works immediately with no configuration.

---

## Optional: Add Google AI (Free!)

For better AI-powered clip recommendations, you can add a free Google AI key.

> **Note:** The app works WITHOUT this! Just upload index.html + app.html to GitHub Pages and it works immediately. The Worker is only needed if you want AI-powered suggestions instead of the built-in generator.

### Get Your Free Google AI Key

### Get Your Free Google AI Key
1. Go to https://aistudio.google.com/app/apikey
2. Click **Create API Key**
3. Copy the key (it's 100% free, no credit card)

### Deploy the Worker
1. Go to https://workers.cloudflare.com
2. Click **Create a Worker**
3. Name it `clipbrief-api`
4. Paste the contents of `worker.js`
5. Click **Save and Deploy**

### Add Your API Key
1. In Cloudflare dashboard, click your worker
2. Go to **Settings** → **Variables**
3. Add variable: `GOOGLE_AI_API_KEY` = your Google key
4. Click **Save**

### Update app.html
Find this line in `app.html`:
```javascript
const WORKER_URL = 'https://YOUR_WORKER.workers.dev';
```
Replace with your actual worker URL.

---

## How It Works

- **Default** — Built-in local generator (works without any API)
- **With Google AI** — Better clip recommendations using free Gemini model
- **5 generations per day** (resets at midnight)
- **No signup** — just paste a YouTube/Twitch URL and get results

---

## Features

- Timestamps (start/end)
- Hook lines (scroll-stopping)
- Viral scores (70-98)
- Ready-to-post captions with hashtags
- Platform selection (TikTok, YouTube Shorts, Instagram Reels)

---

## Google AI Free Tier

Google AI Studio gives you **free usage**:
- 15 requests/minute
- 1M tokens/day

More than enough for personal use!

---

## Troubleshooting

**Usage counter not resetting:**
- Resets at midnight (user's local time)

**Worker not working:**
- Make sure you added `GOOGLE_AI_API_KEY` in Cloudflare variables
- Check worker logs in Cloudflare dashboard

---

## Questions?

Built with Claude AI. Fully free — no costs, no subscriptions.
