# 🍽️ What's for Dinner? — Deploy Guide
### From zero to live app in ~30 minutes

---

## What you need before starting
- A computer (Windows, Mac, or Linux)
- Internet connection
- Free accounts on: **GitHub**, **Vercel**, **Anthropic**

---

## STEP 1 — Install the tools (5 mins)

### Install Node.js
1. Go to **https://nodejs.org**
2. Download the **LTS** version (the green button)
3. Install it — just click Next through everything
4. To check it worked, open Terminal (Mac) or Command Prompt (Windows) and type:
   ```
   node --version
   ```
   You should see something like `v20.11.0`

### Install Git
1. Go to **https://git-scm.com/downloads**
2. Download and install for your OS
3. Check it worked:
   ```
   git --version
   ```

---

## STEP 2 — Get your Anthropic API key (5 mins)

1. Go to **https://console.anthropic.com**
2. Sign up for a free account
3. Click **"API Keys"** in the left sidebar
4. Click **"Create Key"**
5. Give it a name like `whats-for-dinner`
6. **Copy the key** — it starts with `sk-ant-...`
7. Save it somewhere safe — you'll need it in Step 4

> 💡 You get free credits when you sign up. The app costs roughly $0.01–0.02 per search.

---

## STEP 3 — Set up the project (5 mins)

Open Terminal (Mac) or Command Prompt (Windows) and run these commands one by one:

```bash
# 1. Download the project files
# (Put the whats-for-dinner folder from Claude somewhere on your computer first)
# Then navigate to it:
cd path/to/whats-for-dinner

# 2. Install all dependencies
npm install

# 3. Check it runs locally
npm run dev
```

Then open your browser and go to **http://localhost:3000**

You should see the app! But the API won't work yet — do Step 4 first.

---

## STEP 4 — Add your API key (2 mins)

1. In the `whats-for-dinner` folder, find the file called `.env.local`
2. Open it in any text editor (Notepad, TextEdit, VS Code)
3. Replace `your_api_key_here` with your actual key:

```
ANTHROPIC_API_KEY=sk-ant-api03-your-actual-key-here
```

4. Save the file
5. Stop the server (press Ctrl+C in Terminal) and restart it:
   ```
   npm run dev
   ```

Now go to **http://localhost:3000** and try the app — it should work! 🎉

---

## STEP 5 — Put it on GitHub (5 mins)

1. Go to **https://github.com** and sign up / log in
2. Click the **+** button → **"New repository"**
3. Name it `whats-for-dinner`
4. Keep it **Private** (so your code is safe)
5. Click **"Create repository"**
6. Follow the commands GitHub shows you, OR run these:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/whats-for-dinner.git
git push -u origin main
```

> ⚠️ The `.gitignore` file makes sure your `.env.local` (with your API key) is NEVER uploaded to GitHub. It stays only on your computer.

---

## STEP 6 — Deploy to Vercel (5 mins)

Vercel hosts your app for free and gives you a live URL.

1. Go to **https://vercel.com** and sign up with your GitHub account
2. Click **"Add New Project"**
3. Find your `whats-for-dinner` repo and click **"Import"**
4. In the settings screen, click **"Environment Variables"**
5. Add this:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** `sk-ant-api03-your-actual-key-here`
6. Click **"Deploy"**

Vercel will build and deploy your app automatically. In about 60 seconds you'll get a live URL like:

```
https://whats-for-dinner-abc123.vercel.app
```

**That's it — your app is live! 🚀**

---

## STEP 7 — Get a custom domain (optional, ~5 mins)

If you want a proper URL like `whatsfordinner.app`:

1. Buy a domain at **Namecheap** or **Google Domains** (~£10/year)
2. In Vercel, go to your project → **"Settings"** → **"Domains"**
3. Add your domain and follow the instructions

---

## How updates work

When you want to change the app:
1. Edit the files on your computer
2. Test locally with `npm run dev`
3. When happy, push to GitHub:
   ```
   git add .
   git commit -m "describe what you changed"
   git push
   ```
4. Vercel automatically detects the push and redeploys in ~60 seconds

---

## Project file structure

```
whats-for-dinner/
│
├── app/
│   ├── layout.js          ← Page title, fonts, metadata
│   ├── page.js            ← Home page (just loads the app)
│   └── api/
│       └── meals/
│           └── route.js   ← 🔐 SECRET — calls Anthropic with your key
│
├── components/
│   └── WFDApp.js          ← The entire app UI and logic
│
├── .env.local             ← 🔐 Your API key — NEVER share this
├── .gitignore             ← Keeps .env.local off GitHub
├── next.config.js         ← Next.js config
└── package.json           ← Project dependencies
```

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `npm install` fails | Make sure Node.js is installed correctly |
| App shows "Something went wrong" | Check your API key in `.env.local` is correct |
| Vercel deploy fails | Check the Environment Variable is set in Vercel settings |
| App works locally but not on Vercel | Double-check the `ANTHROPIC_API_KEY` env var in Vercel |
| `git push` asks for password | Set up a GitHub Personal Access Token |

---

## Costs

| Service | Cost |
|---|---|
| Vercel hosting | **Free** (Hobby plan) |
| GitHub | **Free** |
| Anthropic API | ~£0.01 per search · Free credits to start |
| Domain (optional) | ~£10/year |

**Total to launch: £0** (until you use up free credits)

---

## Need help?

If you get stuck on any step, just share the error message and I can help you fix it.

Good luck — you're building something real! 🍽️
