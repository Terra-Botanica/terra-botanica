# Automation Strategy Manual

**Project:** Essential Oils Guide — side income business
**Purpose:** Understand exactly what runs automatically, what Claude does, what you do, and how the Raspberry Pi fits in

---

## Table of Contents

1. [The Core Idea](#1-the-core-idea)
2. [What Runs Automatically (24/7 without anyone)](#2-what-runs-automatically-24-7-without-anyone)
3. [What Claude Does (only during your sessions)](#3-what-claude-does-only-during-your-sessions)
4. [What You Do (minimal, scheduled)](#4-what-you-do-minimal-scheduled)
5. [What Claude Cannot Do](#5-what-claude-cannot-do)
6. [The Raspberry Pi as Your Server](#6-the-raspberry-pi-as-your-server)
7. [Full System Architecture](#7-full-system-architecture)
8. [Concrete Weekly / Monthly Schedule](#8-concrete-weekly--monthly-schedule)
9. [How Each Piece Gets Built](#9-how-each-piece-gets-built)

---

## 1. The Core Idea

The goal is a system where most of the work happens once — in setup — and then repeats automatically forever. You and Claude do the upfront work. The Pi and the automation scripts do the ongoing work.

Think of it in three layers:

```
LAYER 1 — Infrastructure (set up once, runs forever)
  Raspberry Pi serving the website
  Cron jobs sending scheduled emails
  Stripe handling payments automatically
  GitHub storing all code and content

LAYER 2 — Content (created in batches, consumed over time)
  12 months of newsletters written in one session, sent one per month
  3 months of Instagram posts written in one session, posted 3x per week
  PDF products written once, sold forever

LAYER 3 — Human attention (minimal, maybe 2–3 hours per month)
  Review and approve content Claude prepares
  Check analytics once a month
  Handle any customer questions
```

Once all three layers are running, the business operates largely without daily involvement.

---

## 2. What Runs Automatically (24/7 without anyone)

These things happen on their own once set up:

### The website
- The Raspberry Pi serves the essential oils app 24 hours a day
- Visitors can browse, search, and use the guide at any time
- No action needed from you

### Email welcome sequence
- Someone signs up on the website
- They automatically receive Email 1 immediately
- Email 2 arrives 3 days later
- Email 3 arrives 7 days later
- Email 4 (with product offer) arrives 14 days later
- This runs for every new subscriber, forever, without you doing anything

### Monthly newsletter
- On the first Monday of every month, the next newsletter sends automatically
- These are written in advance and loaded into a queue
- With 12 written in advance, the system runs for a full year without new content

### Product delivery
- Customer finds the website, clicks "Buy PDF"
- Stripe processes the payment
- Customer receives a download link by email within seconds
- Money arrives in your bank account
- You are notified by email
- You do nothing — the whole transaction is automatic

### Social media posting
- Buffer or Later posts to Instagram automatically on the scheduled dates
- Posts were loaded in a batch session, now publish themselves
- 3 posts per week for 3 months from one loading session

### Analytics
- Website visitor data collected automatically
- Email open rates tracked automatically
- Sales tracked automatically
- You just check the dashboard when you want to

---

## 3. What Claude Does (only during your sessions)

Claude works only when you open a conversation and talk to it. It has no persistent presence — it does not run in the background, it does not check anything, it does not send anything on its own.

What Claude does during sessions:

### Building
- Adds new oils, features, or sections to the website
- Writes and deploys code for new functionality (payment system, email signup, blog)
- Sets up automation scripts (the scripts then run on the Pi without Claude)
- Fixes bugs or updates the design

### Writing content
- Writes the next batch of newsletter emails (e.g. 6 months at a time)
- Writes the next batch of social media posts (e.g. 3 months at a time)
- Writes new PDF products
- Writes blog posts for SEO
- Writes product descriptions, landing pages, about pages

### Strategy and decisions
- Analyzes what is working and suggests changes
- Compares tools and recommends options
- Reviews content you or Gordana write

### Typical session pattern
You open Claude, say "write the next 3 months of Instagram posts" or "add 5 new oils to the app" or "something broke, here is the error." Claude does the work, you review, done. The session might be 30–60 minutes. Then everything runs on its own again until the next session.

**Recommended session schedule:**
- Once a month: review analytics, ask Claude to write next batch of content
- Once a quarter: review strategy, add new features or products
- As needed: fix anything that breaks

---

## 4. What You Do (minimal, scheduled)

With the system fully running, your actual work is:

### Monthly (30–60 minutes)
- Open Claude, ask it to prepare next month's newsletter (review and approve)
- Check sales and subscriber numbers
- Reply to any customer emails (usually very few for digital products)

### Quarterly (2–3 hours)
- Load next 3 months of Instagram posts into Buffer (Claude prepares them)
- Review which products are selling, discuss with Claude what to add next
- Possibly create a new PDF product

### Once a year (half a day)
- Renew domain (~€10)
- Review pricing and products
- Plan next year's content direction with Claude

### Gordana's involvement
- The above work is for you (the technical person)
- Gordana's involvement can be minimal: review newsletter drafts before they send, occasionally record a short video or write a personal note
- Or Gordana can be more involved if she wants — that is her choice
- The system works either way

---

## 5. What Claude Cannot Do

These are hard limits, not temporary limitations:

### Cannot run persistently
Claude has no ongoing existence between conversations. When you close the chat, Claude is gone. There is no background process, no timer, no scheduled task running inside Claude. All automation must live in your own infrastructure (the Pi, a cron job, a service).

### Cannot send emails
Claude cannot access your email server or any external service between sessions. All email sending is handled by your newsletter service (Brevo, Mailchimp, etc.) or a script running on the Pi.

### Cannot post to social media
Claude has no Instagram, Facebook, or any social media access. Scheduling tools (Buffer, Later) handle posting. Claude writes the content, you load it into the scheduler, the scheduler posts it.

### Cannot monitor your website
Claude cannot check if your site is down, watch for new signups, or respond to events happening on your server. You need a simple monitoring tool for that (UptimeRobot — free).

### Cannot make decisions without you
Claude will not decide to change your prices, add new content, or modify your website without you explicitly asking in a session. It has no autonomous goals.

### Cannot log in to external accounts
Claude cannot log in to Stripe, your hosting panel, your email service, or any other account. You always remain in control of your accounts.

---

## 6. The Raspberry Pi as Your Server

Your Raspberry Pi running at home continuously is a powerful resource. Used correctly, it can replace €10–20/month of paid hosting costs and give you full control.

### What the Pi can do for this project

**Serve the website**
Run a lightweight web server (Nginx) that serves your essential oils app to the world. Fast enough for a content site — a Pi 3 or 4 easily handles hundreds of visitors per hour.

**Send newsletters automatically**
A Node.js or Python script runs on a cron job (scheduled task). On the first Monday of every month at 9am, it reads the next newsletter from a queue file and sends it via the Brevo or SendGrid API. No human action required. This costs nothing — Brevo free tier covers up to 300 emails/day.

**Deliver purchased files**
When someone buys a PDF, Stripe sends a notification to the Pi. The Pi's script automatically emails the download link to the customer. Fully automated, zero cost.

**Run a database**
SQLite (zero setup, just a file) or PostgreSQL stores subscriber emails, purchase records, newsletter queue. Runs fine on a Pi.

**Auto-deploy from GitHub**
Every time you push new content to GitHub (a new newsletter, updated oil guide), the Pi automatically pulls the changes and updates the live site. You push to GitHub on your Mac, the Pi updates within seconds.

### The one problem: your home IP address

Home internet connections have a dynamic IP — the address changes periodically. Visitors cannot reliably reach your Pi at a fixed address. Two free solutions:

**Option A — Cloudflare Tunnel (recommended)**
Cloudflare provides a free tunnel service. You install a small program on the Pi (cloudflared). It creates a permanent, secure connection between the Pi and Cloudflare's servers. Your domain points to Cloudflare, Cloudflare forwards traffic to your Pi through the tunnel. Your IP can change freely — the tunnel adapts automatically. No port forwarding on your router needed.

**Option B — DuckDNS (simpler but less reliable)**
Free dynamic DNS service. A script on the Pi updates your IP address at DuckDNS every few minutes. Your domain points to DuckDNS which points to your current IP. Requires port forwarding on your router.

Cloudflare Tunnel is better — more reliable, more secure (your router ports stay closed), and free.

### What the Pi setup looks like

```
Your Pi runs:
  - Nginx (web server) → serves the website
  - Node.js app → handles payments, email delivery
  - Cron jobs → sends newsletters on schedule
  - Cloudflare tunnel → makes it accessible from the internet
  - SQLite database → stores subscribers, purchases, newsletter queue

Your Mac is used for:
  - Writing and editing content (with Claude)
  - Pushing updates to GitHub
  - Checking analytics in a browser

The Pi handles everything automatically once set up.
```

### Hardware requirements

Any of these is sufficient:
- Raspberry Pi 3B+ or newer
- 4GB+ SD card (16GB recommended for comfort)
- Always-on internet connection at home
- That's it — you said you already have this running

### What this replaces (cost comparison)

| Service | Monthly cost | Pi alternative | Pi monthly cost |
|---|---|---|---|
| Web hosting | €5–10 | Nginx on Pi | €0 |
| Newsletter service | €0–30 | Script + Brevo API free tier | €0 |
| Email delivery | €0–20 | SendGrid free tier (100/day) | €0 |
| Database | €0–15 | SQLite on Pi | €0 |
| **Total** | **€5–75/month** | | **€0/month** |

Your only costs are: domain name (~€10/year) and electricity for the Pi (negligible — a Pi 4 uses about 3–5 watts, roughly €2–4/year in electricity).

---

## 7. Full System Architecture

Here is how all the pieces connect:

```
VISITOR                          YOUR TEAM
    |                               |
    | types yourdomain.com          | pushes to GitHub
    |                               |
    v                               v
CLOUDFLARE (free CDN + tunnel)    GITHUB (code + content storage)
    |                               |
    |                               | auto-pull on push
    |                               |
    v                               v
RASPBERRY PI (your home server)
    |
    |-- Nginx serves website (index.html)
    |
    |-- Node.js app:
    |     - Email signup → saves to SQLite
    |     - Stripe webhook → sends download link
    |     - Newsletter queue management
    |
    |-- Cron jobs:
          - 1st Monday 9am: send next newsletter via Brevo API
          - Daily: backup database to GitHub
          - Every 5 min: update Cloudflare tunnel health

VISITOR JOURNEY:
1. Visits site → Pi serves it
2. Signs up → Pi saves email, triggers welcome sequence via Brevo
3. Gets 4 automated emails over 14 days
4. Buys PDF → Stripe charges card, notifies Pi, Pi emails download link
5. Gets monthly newsletter (sent from Pi via Brevo API, from pre-written queue)

YOUR JOURNEY:
1. Open Claude session (monthly or as needed)
2. Claude writes next batch of content
3. You review and approve
4. Push to GitHub
5. Pi updates automatically
6. Done until next month
```

---

## 8. Concrete Weekly / Monthly Schedule

### What happens with zero action from you

| When | What happens automatically |
|---|---|
| Any time | Visitors browse the oil guide |
| Any time | New subscribers receive welcome email sequence |
| Any time | Product purchases processed and delivered |
| 3x per week | Instagram posts published (loaded in advance) |
| 1st Monday of month | Monthly newsletter sends to all subscribers |
| Daily | Database backed up to GitHub |

### Your actual schedule

**Monthly session with Claude (30–60 min)**
```
You: "Here are the open rates from last month. Write next month's newsletter
     about lavender and sleep protocols."
Claude: writes it
You: read, approve or ask for changes
You: add it to the newsletter queue file on the Pi
Done.
```

**Quarterly session with Claude (2–3 hours)**
```
You: "Write the next 3 months of Instagram posts, focus on emotional oils."
Claude: writes 36 posts with captions and hashtags
You: create images in Canva (Claude gives you the exact text for each)
You: load into Buffer and schedule
Done for 3 months.

You: "Create a new PDF product on essential oils for digestive health."
Claude: writes and formats the full PDF content
You: export to PDF, upload to payment system
Done.
```

---

## 9. How Each Piece Gets Built

Everything below is something Claude builds in a session with you. None of it requires you to write code.

### Step 1 — Pi web server setup
Claude writes a setup script. You run it on the Pi. It installs Nginx, configures it to serve your HTML file, sets up Cloudflare Tunnel. One session, maybe 45 minutes including you running commands on the Pi.

### Step 2 — Email signup + welcome sequence
Claude writes the Node.js app that:
- Receives email signups from the website form
- Saves emails to the database
- Triggers the welcome sequence via Brevo API

Claude also writes all 4 welcome emails. You deploy the app on the Pi, enter your Brevo API key, done.

### Step 3 — Newsletter queue system
Claude writes a simple system:
- A folder on the Pi with numbered text files (01-january.html, 02-february.html, etc.)
- A cron job that on the 1st Monday of each month sends the next file to all subscribers via Brevo
- Claude writes the newsletters. You add the files to the folder. They send on schedule.

### Step 4 — Payment + PDF delivery
Claude writes the Stripe integration:
- A payment button on the website
- A webhook listener on the Pi that receives Stripe's "payment succeeded" notification
- Automatic email to customer with download link
- The PDF file lives on the Pi

### Step 5 — Auto-deploy from GitHub
Claude writes a webhook script. When you push to GitHub, GitHub notifies the Pi, the Pi runs `git pull`, the website updates live. No manual SSH needed.

### Step 6 — Monitoring
Claude sets up UptimeRobot (free) to ping your site every 5 minutes and email you if it goes down. One form to fill in, done.

---

*Manual written by Claude (Anthropic) — March 2026*
