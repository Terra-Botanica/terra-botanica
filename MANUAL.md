# Essential Oils Business — Setup Manual

**Project:** Essential Oils Guide — website, newsletter, digital products, social media
**Status:** Starting from scratch
**Goal:** Automated side income with minimal ongoing effort

---

## Table of Contents

1. [The Website App](#1-the-website-app)
2. [Hosting — Options & Recommendation](#2-hosting--options--recommendation)
3. [Domain Name](#3-domain-name)
4. [Switching Hosts Later — Not a Problem](#4-switching-hosts-later--not-a-problem)
5. [Newsletter System](#5-newsletter-system)
6. [Digital Products to Sell](#6-digital-products-to-sell)
7. [Payment Systems](#7-payment-systems)
8. [Social Media](#8-social-media)
9. [What Claude Can Build](#9-what-claude-can-build)
10. [Full Roadmap & Next Steps](#10-full-roadmap--next-steps)
11. [Realistic Income Timeline](#11-realistic-income-timeline)

---

## 1. The Website App

The essential oils guide is built as a single HTML file (`index.html`). It contains:

- **49 essential oils** with full profiles in English: properties, uses, emotional effects, application methods, blending combinations, cautions
- **Search bar** — search by oil name, condition, or property (e.g. type "anxiety" or "sleep" or "joint pain")
- **Category filters** — Respiratory, Immune, Digestive, Emotional, Pain, Skin, Hormonal, Hair, Sleep, Spiritual, Energy
- **Blends & Combinations tab** — 18 named blends with exact recipes and how-to instructions
- **Mobile responsive** — works on phone and tablet
- No database required, no backend, no login — just one file

**To run it locally:** double-click `index.html` in any browser.

**To add a new oil:** open the file, find the `const oils = [` section in the JavaScript, and add a new entry following the same format as existing oils.

---

## 2. Hosting — Options & Recommendation

These are the realistic options for putting the site online. All prices are approximate annual costs.

### Option A — Netlify (free)

| What it is | Static file hosting — just puts your HTML online |
|---|---|
| Cost | Free tier is fully sufficient |
| Custom domain | Yes, connect your own for free |
| Ads on your site | None |
| Setup time | 60 seconds — drag and drop the file |
| Best for | The current app exactly as it is |
| Limitation | No built-in blog, CMS, shop — those need separate tools |

**How to deploy:**
1. Go to netlify.com, create a free account
2. Drag the `index.html` file onto the Netlify dashboard
3. Your site is live at `yourname.netlify.app`
4. Optional: connect your custom domain in Settings → Domain Management

---

### Option B — WordPress.org Self-Hosted (recommended for long-term)

| What it is | You own everything — full WordPress on your own server |
|---|---|
| Hosting cost | €3–8/month (Hostinger, Hetzner, SiteGround) |
| Domain cost | ~€10–12/year (Namecheap, Porkbun) |
| Total per year | ~€50–110/year |
| Custom domain | Yes, fully yours |
| Blog | Yes, built in |
| Newsletter | Yes, with free MailPoet plugin |
| Online shop | Yes, with free WooCommerce plugin |
| Setup time | 2–3 hours if familiar with WordPress |
| Best for | Long-term, full control, one platform for everything |

**Why self-hosted over WordPress.com:**
- WordPress.com free shows ads you don't control and don't earn from
- WordPress.com Business plan (needed for plugins/shop) costs €25/month = €300/year
- Self-hosted costs €50–110/year and you have full control with no platform restrictions
- No percentage taken from your sales

**Recommended hosting providers:**
- **Hetzner** (Germany/Finland) — €4–5/month, fast, reliable, good for Europe
- **Hostinger** — €2–4/month, very beginner-friendly, one-click WordPress install

---

### Option C — Ghost (best for newsletter-first business)

| What it is | Open-source platform built for content + newsletter + memberships |
|---|---|
| Self-hosted cost | ~€5/month server + free Ghost software |
| Ghost.org managed | From $9/month |
| Newsletter | Built in — no separate service needed |
| Paid memberships | Built in — connects directly to Stripe, takes 0% beyond Stripe fees |
| Setup time | 3–5 hours, some technical comfort needed |
| Best for | If newsletter and memberships are the core business |

---

### Option D — WordPress.com Managed

| Plan | Cost | What you get |
|---|---|---|
| Free | €0 | Ads on your site, no custom domain, limited |
| Personal | ~€4/month | Custom domain, no ads |
| Business | ~€25/month | Plugins, WooCommerce, full features |

Not recommended unless you want zero server management and are willing to pay €25/month for the Business plan.

---

### Summary Recommendation

| If you want... | Choose |
|---|---|
| Fastest start, free | Netlify |
| Full control, cheapest long-term, already know WordPress | Self-hosted WordPress.org |
| Newsletter + memberships as primary focus | Ghost |

---

## 3. Domain Name

A domain name is what people type to reach you — e.g. `essentialoilsguide.com`.

**Where to buy:**
- **Namecheap** (namecheap.com) — reliable, reasonable prices, good interface
- **Porkbun** (porkbun.com) — often the cheapest, clear pricing

**Cost:** €8–15/year depending on extension (.com, .net, .org, .eu)

**Tips for choosing:**
- `.com` is still the most trusted extension
- Keep it short and memorable
- Avoid hyphens
- Ideas: `essentialoilsguide.com`, `gordanaoils.com`, `aromaguide.com`, `oilprotocols.com`

**Important:** Buy your domain from a registrar, not from your hosting provider. This keeps them separate and gives you freedom to switch hosts without losing your domain.

---

## 4. Switching Hosts Later — Not a Problem

The domain name (what customers remember) and the hosting (where files live) are completely separate. You can switch hosting providers at any time — the domain stays the same, customers notice nothing.

**How it works:**
1. You own `yourdomain.com` at Namecheap
2. It currently points to Netlify
3. You later move to WordPress — you just change one DNS setting at Namecheap
4. Within 24 hours the domain points to WordPress
5. Customers type the same URL as always, see the same website

There is no branding problem, no notification needed, no disruption to customers.

---

## 5. Newsletter System

A newsletter is an email sent to subscribers on a schedule. It is the most important asset in an online content business because you own the list — it cannot be taken away by a platform change.

### How it works

1. A visitor comes to your website and enters their email in a signup form
2. They receive a welcome email automatically
3. They receive monthly emails (or whatever schedule you set)
4. If they click a link and buy something, that sale is tracked back to the email

### Tools

**Brevo (formerly Sendinblue)** — recommended starting point
- Free up to 300 emails/day (9,000/month) — plenty for starting out
- Automation included on free tier
- Add signup form to your website, create email sequences

**MailPoet** — if using WordPress
- Free plugin, installs inside WordPress
- Manages your list, sends emails, handles automation
- Emails are sent through your own WordPress install or via Brevo/Mailchimp as a backend

**ConvertKit**
- Free up to 1,000 subscribers
- Well-designed for creators and digital product sellers
- Good automation and tagging features

### What to automate

**Welcome sequence** (sends automatically when someone subscribes):
- Email 1 (immediately): Welcome, introduce Gordana, link to the free oil guide
- Email 2 (day 3): One oil in depth — story, uses, a recipe
- Email 3 (day 7): The Four Thieves blend — story and protocol
- Email 4 (day 14): First offer — introduce the PDF product

**Monthly newsletter** (prepared in advance, scheduled to send):
- Oil of the month: story, therapeutic uses, one recipe blend
- Seasonal protocols (spring detox, winter immunity, summer skin, etc.)
- Can be written 6–12 months in advance and scheduled

**All of this content can be written by Claude in advance** — see section 9.

---

## 6. Digital Products to Sell

These are files that are created once and sold automatically, unlimited times, with no inventory or shipping.

### PDF Protocol Guides

Suggested products and prices:

| Product | Price |
|---|---|
| Essential Oils for Anxiety & Sleep — 10 protocols | €9 |
| Essential Oils for Women's Health — hormones, PMS, menopause | €12 |
| Essential Oils for Pain & Inflammation — joints, muscles, headaches | €9 |
| Seasonal Detox Protocols — spring, autumn, winter cleanse | €9 |
| Printable Blend Recipe Cards — 30 recipes, one per page | €12 |
| The Complete Essential Oils Protocol Bundle (all above) | €35 |

### Online Course

A recorded video course — highest value, most upfront work.

- 6 short video lessons (15–20 min each) with Gordana speaking
- Covers: introduction to aromatherapy, the key 10 oils, blending principles, protocols by condition, safety, sourcing quality oils
- Price range: €75–150
- Hosted on Gumroad, Teachable, or directly on your website
- Once recorded, sells automatically forever

### Monthly Subscription

€5–9/month. Subscribers receive:
- One new protocol PDF per month
- Access to the full archive of past protocols
- Managed via Ko-fi memberships, Patreon, or Ghost memberships

---

## 7. Payment Systems

### Option A — Gumroad (easiest start)

- Create account at gumroad.com
- Upload your PDF, set a price, get a link
- Paste the link on your website
- Customer pays → receives download automatically
- You receive money in your bank account
- **Cost:** 10% of each sale + Stripe processing fees (~3%)
- **No setup cost, no technical work**
- Recommended to validate that people buy before building your own system

### Option B — Stripe directly (own system, lowest fees)

- Create account at stripe.com
- Stripe handles card processing for 2.9% + €0.25 per transaction — no platform percentage on top
- We build the payment form and automatic file delivery on your website
- On a €10 sale you keep ~€9.45 instead of ~€8.70 with Gumroad
- **Setup:** requires technical work — Claude can build this in a few hours
- Recommended once you're making regular sales

### Option C — WooCommerce (if using WordPress)

- Free plugin, installs in WordPress
- Connects to Stripe (free Stripe plugin) or PayPal
- Handles digital downloads automatically
- Full shop on your own site, no platform percentage

### The card processing fee (2.9%) is unavoidable

Every payment method — Gumroad, Stripe, PayPal, WooCommerce — passes on the card network fee of approximately 2.9% + €0.25 per transaction. This is not a platform markup, it is what Visa/Mastercard charge. You cannot avoid it. What you can avoid is the extra platform percentage on top (e.g. Gumroad's 10%).

---

## 8. Social Media

### What to post

Instagram is the most relevant platform for this content. Useful content types:

- **Oil of the week** — one image, short caption with 3 key uses
- **Blend recipes** — simple graphic with ingredients
- **Before/after** — a condition and which oils help
- **Short educational** — "Did you know..." facts from the guide
- **Behind the scenes** — Gordana's practice and approach

### Scheduling (automation)

You write and schedule posts in bulk, the tool posts automatically.

**Buffer** (buffer.com) — free up to 3 channels, 10 scheduled posts at a time
**Later** (later.com) — free tier, strong Instagram focus, visual planning grid

**Workflow:**
1. Once every 3 months, sit down for 2–3 hours
2. Review the batch of posts Claude has prepared (captions, hashtags, image ideas)
3. Create the images in Canva (free)
4. Upload to Buffer/Later and schedule them across the next 3 months
5. They post automatically, 3x per week

### What Claude can prepare in advance

- Full 3-month content calendar (dates, topics, captions)
- All captions written, including hashtags
- Image description prompts for Canva
- Story ideas and poll questions

**What Claude cannot do:** log in to Instagram and post directly. The scheduling tool (Buffer/Later) handles the actual posting once you load the content.

---

## 9. What Claude Can Build

Claude (the AI assistant used to build this project) can do the following within your sessions:

### Technical builds
- Add features to the essential oils app (new oils, new filters, search improvements)
- Build an email signup form and connect it to Brevo/Mailchimp via API
- Build a Stripe payment integration for selling PDFs directly from your site
- Build a simple blog for WordPress or as static HTML pages
- Set up automated email sending scripts (run on your server, no manual work)
- Add SEO meta tags, structured data, sitemap to your website
- Build a membership/login system if needed later

### Content creation
- Write all newsletter emails — welcome sequences, 12 months of monthly content
- Write all social media captions and content calendars
- Write product descriptions, about pages, FAQ pages
- Write blog posts optimized for search engines
- Design PDF layouts (as printable HTML, exportable to PDF)
- Translate content between English, Spanish, Serbian, or other languages

### Strategy
- Answer questions, compare tools, help make decisions
- Review anything you create and suggest improvements

### What Claude cannot do
- Run in the background when you're not in a conversation
- Post to social media directly
- Send emails on its own (the automation runs on your server or in a service)
- Log in to external websites on your behalf

Everything Claude builds runs automatically once deployed — it does not require Claude to be present.

---

## 10. Full Roadmap & Next Steps

Work through these steps in order. Each step is roughly one session with Claude.

### Phase 1 — Get Online (Priority: do first)

- [ ] Choose a domain name (discuss options with Claude)
- [ ] Register domain at Namecheap or Porkbun
- [ ] Choose hosting: Netlify (fastest) or self-hosted WordPress (recommended long-term)
- [ ] Deploy the essential oils app online
- [ ] Connect custom domain
- [ ] Add email signup form to the site

**Outcome:** The site is live and you can start collecting email addresses.

---

### Phase 2 — Newsletter Setup

- [ ] Choose newsletter service: Brevo (free) or MailPoet (WordPress plugin)
- [ ] Set up account and connect to website signup form
- [ ] Claude writes 4-email welcome sequence
- [ ] Claude writes 6 months of monthly newsletters
- [ ] Schedule all emails in advance
- [ ] Test the flow end to end

**Outcome:** Every new subscriber gets automatic emails for 6+ months. Zero ongoing work.

---

### Phase 3 — First Product

- [ ] Decide which PDF guide to create first (suggest: Anxiety & Sleep or Women's Health)
- [ ] Claude writes and formats the PDF content
- [ ] Export to PDF
- [ ] Set up on Gumroad (easiest) or WooCommerce
- [ ] Add "Buy" button to website
- [ ] Test purchase flow end to end

**Outcome:** First product available for automatic sale 24/7.

---

### Phase 4 — Social Media

- [ ] Create Instagram account (or activate existing one)
- [ ] Create free Buffer or Later account
- [ ] Claude prepares 3-month content calendar with all captions
- [ ] Create images in Canva using Claude's prompts
- [ ] Load posts into Buffer/Later and schedule
- [ ] Repeat every 3 months

**Outcome:** Instagram posts automatically 3x/week for 3 months at a time.

---

### Phase 5 — Expand (after Phase 1–4 are stable)

- [ ] Add second and third PDF products
- [ ] Build direct Stripe payment (cut out Gumroad's 10%)
- [ ] Create online course (record videos with Gordana)
- [ ] Add blog posts for SEO (Claude writes, you publish)
- [ ] Consider paid ads on Instagram (€5-10/day to test)

---

## 11. Realistic Income Timeline

This is an honest estimate, not a guarantee. Results depend heavily on Gordana's existing network.

| Timeframe | Expected situation | Realistic monthly income |
|---|---|---|
| Month 1–2 | Site live, first subscribers, first product available | €0–50 |
| Month 3–6 | Small email list, steady trickle from Gordana's network | €50–200 |
| Month 6–12 | Growing search traffic, email list 200–500 people | €200–500 |
| Year 2 | Course added, subscription tier, established SEO | €500–1500 |

**The most important lever:** Gordana sharing the link with existing clients and professional contacts. People who already trust her convert immediately. Cold internet traffic takes 6–12 months to build through search.

**Key principle:** Every hour of setup work done now pays off indefinitely. A newsletter written once sends forever. A PDF created once sells forever. A scheduled social media batch runs for 3 months. The goal is to front-load the work so the system runs itself.

---

*Manual written by Claude (Anthropic) — March 2026*
*Essential Oils Guide app built by Claude based on source material by Gordana Žikić*
