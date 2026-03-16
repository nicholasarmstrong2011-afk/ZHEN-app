# ZHEN DEPLOYMENT GUIDE
## Ship tonight, live on tryzhen.com by morning

---

## STEP 1: Download the zhen-pwa.zip from this chat

Save it to your phone or computer. Unzip it.
You'll see these files:
- index.html (the full app)
- sw.js (service worker for offline)
- manifest.json (PWA config)
- vercel.json (hosting config)
- icons/ (app icons for home screen)

---

## STEP 2: Create a free Vercel account (2 min)

1. Go to https://vercel.com/signup
2. Sign up with your email (no credit card needed)
3. Verify your email

---

## STEP 3: Push files to GitHub first (easiest deploy path)

Option A - If you have GitHub:
1. Go to https://github.com/new
2. Create a new repo called "zhen-app" (public or private, doesn't matter)
3. Upload all the files from the zip (drag and drop works)
4. Click "Commit changes"

Option B - If you don't have GitHub:
1. Go to https://github.com/signup (free, 2 min)
2. Then do Option A above

Option C - Direct deploy without GitHub:
1. Install Vercel CLI: npm install -g vercel
2. Open terminal in the zhen-pwa folder
3. Run: vercel
4. Follow the prompts
5. Skip to Step 5

---

## STEP 4: Deploy on Vercel (2 min)

1. Go to https://vercel.com/new
2. Click "Import Git Repository"
3. Select your "zhen-app" repo
4. Framework Preset: select "Other"
5. Click "Deploy"
6. Wait 30 seconds. Done.

Vercel will give you a URL like: zhen-app.vercel.app
Test it on your phone right now. It works.

---

## STEP 5: Connect tryzhen.com (5 min)

### On Vercel:
1. Go to your project dashboard on Vercel
2. Click "Settings" tab
3. Click "Domains" in the left sidebar
4. Type: tryzhen.com
5. Click "Add"
6. Vercel will show you DNS records to add

### On GoDaddy:
1. Log in to https://dng.godaddy.com (DNS manager)
2. Select tryzhen.com
3. You need to change/add these DNS records:

**Delete any existing A records for @ (the root domain)**

**Add these records (Vercel will show you the exact values):**

| Type  | Name | Value               |
|-------|------|---------------------|
| A     | @    | 76.76.21.21         |
| CNAME | www  | cname.vercel-dns.com|

4. Save changes
5. Wait 5-30 minutes for DNS to propagate

### Back on Vercel:
1. Also add www.tryzhen.com as a domain
2. Vercel will auto-configure SSL (free HTTPS)
3. Once DNS propagates, tryzhen.com is live

---

## STEP 6: Test the PWA (2 min)

On your iPhone:
1. Open Safari
2. Go to tryzhen.com
3. Tap the Share button (square with arrow)
4. Scroll down, tap "Add to Home Screen"
5. Name it "Zhen"
6. Tap "Add"
7. Open it from your home screen - full screen, no browser bar

On Android:
1. Open Chrome
2. Go to tryzhen.com
3. Chrome will show "Add to Home Screen" banner
4. Or tap the three dots menu > "Add to Home Screen"

---

## STEP 7: Push updates (30 seconds each time)

When you make changes:
1. Edit the files
2. Push to GitHub
3. Vercel auto-deploys in 30 seconds
4. Users get the update next time they open the app

---

## TROUBLESHOOTING

**DNS not working yet?**
- Takes up to 30 min. Check https://dnschecker.org for tryzhen.com
- Make sure you deleted old A records on GoDaddy

**App not installing as PWA?**
- Must be on HTTPS (Vercel handles this automatically)
- Must use Safari on iPhone (Chrome on iPhone can't install PWAs)
- Clear Safari cache if it's showing an old version

**Need to update the app?**
- Edit index.html
- Push to GitHub (or re-run vercel CLI)
- Change CACHE_NAME in sw.js to 'zhen-v2' to force update

---

## TIMELINE

- Download zip: 1 min
- Vercel account: 2 min
- GitHub repo: 3 min
- Deploy: 2 min
- DNS setup: 5 min
- DNS propagation: 5-30 min wait
- Test PWA: 2 min

TOTAL ACTIVE TIME: ~15 minutes
TOTAL COST: $0
