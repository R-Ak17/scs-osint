# SCS OSINT Dashboard

South China Sea OSINT analyst dashboard with AI chat, interactive map, claim matrix, infrastructure tracking, and claimant posture analysis.

## Project structure

```
scs-osint/
├── api/
│   └── chat.js          ← Serverless function (proxies Anthropic API securely)
├── public/
│   └── index.html       ← Full dashboard
├── vercel.json          ← Routing config
└── README.md
```

---

## Deploy to Vercel (step by step)

### 1. Get your Anthropic API key

1. Go to https://console.anthropic.com
2. Sign in (or create a free account)
3. Click **API Keys** in the left sidebar
4. Click **Create Key** — give it a name like "scs-dashboard"
5. Copy the key immediately (starts with `sk-ant-...`) — you only see it once

### 2. Push to GitHub

1. Go to https://github.com and create a new repository (e.g. `scs-osint`)
2. Upload all files maintaining this folder structure:
   - `api/chat.js`
   - `public/index.html`
   - `vercel.json`
3. Commit and push

### 3. Deploy on Vercel

1. Go to https://vercel.com and log in
2. Click **Add New Project**
3. Select your `scs-osint` GitHub repo and click **Import**
4. Leave all build settings as default — Vercel auto-detects the structure
5. Before clicking Deploy, click **Environment Variables**
6. Add one variable:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** paste your `sk-ant-...` key
7. Click **Deploy**

Your site will be live at `https://your-project-name.vercel.app` in ~30 seconds.

### 4. Custom domain (optional)

In your Vercel project → Settings → Domains → add your domain and follow the DNS instructions.

---

## How the AI chat works

- The frontend sends messages to `/api/chat` (your serverless function)
- The function reads `ANTHROPIC_API_KEY` from the server environment (never exposed to the browser)
- It calls `api.anthropic.com/v1/messages` and returns the response
- The API key is never visible in client-side code

---

## Updating the dashboard

Edit `public/index.html` directly — push to GitHub and Vercel auto-redeploys in seconds.
