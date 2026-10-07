# Example Scripts (voice reference)

These five scripts were written for the channel launch and represent the target voice exactly. When drafting new scripts for a new project, read these first to calibrate tone, sentence length, and how technical detail is balanced against plain-language explanation.

---

### Example 1 — Pillar: The Decision
**Source: MacPilot APP_IDEA.md/IMPLEMENT_PLAN.md — local-first architecture, BYOK**

**Hook (0–3s):**
"I'm building an app that lets you control your Mac from your phone. I could've made this a $10/month subscription. I didn't. Here's why."

**Setup (3–15s):**
"It's called MacPilot — Android app, talks to your Mac over WebSocket, on your local network. No cloud relay in the middle by default."

**Turn/Insight (15–45s):**
"Most remote-control apps route through a server because it's easier to build. But that means your screen, your clipboard, your files — all passing through someone else's infrastructure. For a tool that touches your whole computer, that's a trust problem, not just a technical one. So MacPilot is local-first: your phone and your Mac talk directly. And for the AI features, you bring your own API key — I never see your data, and I don't pay for your usage either."

**Payoff/CTA (45–60s):**
"Trade-off? It's harder to build than 'just use a server.' But I think for this category, that's the right trade. Following along as I build this — more decisions like this coming."

---

### Example 2 — Pillar: Indie Math
**Source: ClauManager APP_IDEA.md — pricing model**

**Hook (0–3s):**
"Every indie app has one feature that decides if anyone pays you. Here's how I find mine."

**Setup (3–15s):**
"I'm building ClauManager — a terminal tool for managing Claude CLI sessions. Free tier does the basics: list sessions, search them."

**Turn/Insight (15–45s):**
"The Pro tier — one-time $9, not a subscription — is full-text search across every session you've ever had, plus token cost tracking. Why that line and not another feature? Because 'search' and 'cost' are the two things people only miss once they have a LOT of sessions. That's the moment they're already convinced the tool is useful — they're not paying to try it, they're paying because they outgrew the free version. That's the line: free proves the tool works, paid removes a limit you only hit after you're already convinced."

**Payoff/CTA (45–60s):**
"One-time price, not subscription — for a CLI tool you open 10 times a day, recurring billing is the wrong model. More indie pricing breakdowns coming."

---

### Example 3 — Pillar: Building for SEA
**Source: WealthLens APP_IDEA.md — SJC gold as asset class**

**Hook (0–3s):**
"If you build a finance app and your first market is Vietnam, you're going to get one asset type wrong if you copy a US app."

**Setup (3–15s):**
"I'm building WealthLens — tracks VN stocks, crypto, real estate, fixed deposits. And gold. Specifically SJC gold."

**Turn/Insight (15–45s):**
"In most Western finance apps, gold is a commodity ticker, maybe an ETF. In Vietnam, SJC gold bars are a primary household savings vehicle — comparable to how Americans think about a savings account, not how they think about a gold ETF. If I'd modeled it as 'just another commodity price feed,' the app would feel foreign to the exact users I'm building it for. So gold gets first-class treatment, same tier as stocks, with its own pricing source."

**Payoff/CTA (45–60s):**
"Small modeling decision, but it's the difference between an app that feels translated and an app that feels built for you. That's the SEA-first approach for this whole project."

---

### Example 4 — Pillar: The Decision
**Source: DropBridge APP_IDEA.md/IMPLEMENT_PLAN.md — X25519 + AES-256-GCM over LAN**

**Hook (0–3s):**
"This file transfer is happening entirely on your own WiFi. I encrypted it anyway. Here's why that's not overkill."

**Setup (3–15s):**
"DropBridge moves files between your Android phone and your Mac over the local network — no cloud upload, no internet required."

**Turn/Insight (15–45s):**
"'It's just my home WiFi' is exactly the assumption that gets people on shared networks — cafes, offices, co-working spaces — into trouble. So every transfer uses X25519 for key exchange and AES-256-GCM for the actual file data. Same network discovery convenience as something like AirDrop, but the wire protocol doesn't trust the network it's running on. mDNS finds the device. The encryption protects you in case that network isn't as private as it looks."

**Payoff/CTA (45–60s):**
"'Local' and 'private' aren't the same word. Built it as if it weren't local at all."

---

### Example 5 — Pillar: Indie Math
**Source: Generic COST.md pattern — 10/100/1000 user tiers**

**Hook (0–3s):**
"Everyone asks indie devs the same question: what does this actually cost to run? So I did the math. For real."

**Setup (3–15s):**
"Every product I build gets a COST.md before I write a line of code — projected infra cost at 10, 100, and 1000 active users."

**Turn/Insight (15–45s):**
"At 10 users, almost everything is free-tier — database, hosting, auth, all under the free quotas. At 100 users, you start paying for the database tier, maybe $10–25/month total. At 1000 users, that's where people assume costs explode — but if your architecture is right, it's usually still under three figures a month, because the expensive part was never hosting. It's things like AI API calls or SMS/email sending, if you have those, that scale per-user. Hosting almost never bankrupts a solo dev. The features that call external APIs per-request do."

**Payoff/CTA (45–60s):**
"That's why I cost out every feature before building it, not after launch. I'll break down a real COST.md from one of my apps in a future video — let me know which one you want to see."

---

## What to notice across all five

- Every hook is a claim or implicit question that needs zero setup to understand
- Every Setup is exactly one sentence naming the product + one sentence of context, never more
- Every Turn has exactly one idea — none of these try to teach two things
- Every Payoff is short — one sentence of takeaway, at most one soft CTA sentence
- Technical terms (WebSocket, X25519, AES-256-GCM, TimescaleDB-style reasoning) appear but are always immediately grounded in a plain-language consequence
- None of these name or disparage a specific competitor
