# CO Consult — Deploy to Vercel in 10 Minutes

## What you need
- A GitHub account (free)
- A Vercel account (free) — sign up at vercel.com with your GitHub
- Your Anthropic API key — get it at console.anthropic.com

---

## Step 1 — Push to GitHub

Open your terminal and run:

```bash
cd co-consult-deploy
git init
git add .
git commit -m "CO Consult v1 — initial deploy"
git branch -M main
```

Then go to github.com → New repository → name it `co-consult` → Create.

Copy the two lines it shows you (git remote add + git push) and run them.

---

## Step 2 — Deploy on Vercel

1. Go to vercel.com and click "Add New Project"
2. Import your `co-consult` GitHub repo
3. Framework Preset: select **Vite**
4. Root Directory: leave as `/`
5. Click "Environment Variables" and add:
   - Key: `ANTHROPIC_API_KEY`
   - Value: your Anthropic API key (starts with `sk-ant-...`)
6. Click **Deploy**

Vercel builds it automatically. In ~60 seconds you get a live URL like:
`https://co-consult.vercel.app`

---

## Step 3 — Custom Domain (optional, looks professional)

1. Buy `coconsult.ai` or `co-consult.app` on Namecheap (~$12/year)
2. In Vercel → Project → Settings → Domains → Add domain
3. Follow the DNS instructions Vercel gives you (takes ~10 minutes to propagate)

---

## File Structure

```
co-consult-deploy/
├── index.html          ← Entry point
├── package.json        ← Dependencies
├── vite.config.js      ← Build config
├── vercel.json         ← Routing rules
├── api/
│   └── proxy.js        ← Serverless function (hides your API key)
└── src/
    ├── main.jsx        ← React entry
    └── App.jsx         ← Full CO Consult app
```

---

## How the API proxy works

In production, the app calls `/api/proxy` instead of Anthropic directly.
The Vercel serverless function adds your API key server-side and forwards to Anthropic.
Users never see your key. You pay per token, they use it free.

---

## Costs at scale

| Monthly active users | Est. API cost |
|---------------------|---------------|
| 50                  | ~$15          |
| 200                 | ~$60          |
| 500                 | ~$150         |
| 1,000               | ~$300         |

Vercel hosting: Free up to 100GB bandwidth/month.

---

## After deploying

Share this link in your cold emails to McKinsey/BCG/Bain partners.
Record a 90-second Loom demo of the full flow.
Add the live URL to your LinkedIn and resume.
