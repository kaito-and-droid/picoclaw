---
name: tiktok-generator
description: Generates a TikTok video series (storytelling/explainer format, no live coding) from a product's APP_IDEA.md, IMPLEMENT_PLAN.md, and COST.md. Use this skill whenever the user asks to create TikTok content, a video series, short-form content, or social content for a product/project they're building — especially phrases like "make tiktok content for this", "turn this into a series", "content for [project name]", or "make clips for this idea". Also trigger if the user references hy.dev content strategy, indie hacker storytelling videos, or asks to repeat the TikTok content process for a new project. Reads the three planning docs from the project folder, extracts real technical decisions and numbers, and outputs one script file per video plus a posting plan — no fictional content, every video must trace back to something in the actual docs.
---

# TikTok Series Generator

Turns a project's existing planning docs (APP_IDEA.md, IMPLEMENT_PLAN.md, COST.md) into a ready-to-film TikTok script series. This skill exists so every new hy.dev project automatically gets a content pipeline as a side effect of having already done normal product planning — no separate content brainstorm needed.

## Core principle: zero invented content

Every video must be traceable to a specific sentence, decision, or number in the source docs. Do not invent feature details, market claims, or numbers that aren't in the docs. If a pillar (see below) has nothing real to draw on for a given project, skip that pillar rather than padding it with generic advice. This is the entire differentiator of this content style versus generic "learn to code" channels — it only works if it's true.

## Step 1 — Locate and read the source docs

Look in the current working directory and immediate subdirectories for:
- `APP_IDEA.md` (required)
- `IMPLEMENT_PLAN.md` (required)
- `COST.md` (optional, but read it if present — Pillar 3 depends on it)

If `APP_IDEA.md` or `IMPLEMENT_PLAN.md` cannot be found, stop and ask the user for the project folder path rather than guessing or fabricating. Do not proceed on partial/assumed content.

Read all three fully before drafting anything. Take note of:
- The product name and one-line positioning
- Every explicit "we chose X over Y" or "why not Z" statement
- Any SEA/Vietnam-specific market detail (currency, local platform, regulation, language)
- Every concrete number in COST.md (infra cost at different user tiers, pricing model, margin)
- The tech stack list and any non-obvious component (custom protocol, specific encryption, specific architecture pattern)

## Step 2 — Extract video-worthy material per pillar

Use these three pillars (established as the channel's format — see `references/channel-voice.md` for full tone guide). Do not invent a 4th pillar unless the user explicitly asks for one.

1. **The Decision** — architecture/stack trade-offs explicitly justified in IMPLEMENT_PLAN.md ("X instead of Y because...")
2. **Building for SEA** — anything in APP_IDEA.md or IMPLEMENT_PLAN.md tied to Vietnam/SEA market specifics (currency, local competitor gap, local platform constraint, regulation)
3. **Indie Math** — real numbers from COST.md, plus any pricing-model or solo-dev-constraint reasoning in APP_IDEA.md

For each pillar, list every candidate (a single sentence is enough at this stage) before writing scripts. See `references/extraction-checklist.md` for the full checklist of what counts as "video-worthy" per pillar.

## Step 3 — Decide the video count (flexible, not fixed)

Do not default to a fixed number like 30. Count real candidates from Step 2:
- Each pillar needs a minimum of 2 usable candidates to be included at all. If a pillar has 0–1 candidates, drop it for this project and note that to the user (e.g. "this project has no SEA-specific angle in the docs, so Pillar 2 is skipped — let me know if that's wrong and there's context I'm missing").
- Total series length = total usable candidates, with a soft cap: if a pillar has more than 8 strong candidates, pick the 8 most concrete/specific ones (concrete numbers and named trade-offs beat vague statements) rather than including everything.
- Typical range ends up 6–18 videos depending on project complexity. A simple CLI tool with a short IMPLEMENT_PLAN.md should NOT be padded to match a complex KMP app's count.
- State the final count and pillar breakdown to the user before writing full scripts, so they can adjust before you do the writing work.

## Step 4 — Write one script per video

Use this structure for every script (see `references/script-template.md` for the annotated template and `references/example-scripts.md` for five fully-written reference examples in this exact voice):

- **Hook (0–3s)** — a claim or question, no throat-clearing, no "hey guys"
- **Setup (3–15s)** — name the product, one sentence of context
- **Turn/Insight (15–45s)** — the actual decision/number/insight, explained like talking to one friend, not a lecture
- **Payoff/CTA (45–60s)** — the takeaway + soft pointer to the product (waitlist mention only if natural, never forced)

Tone rules (full detail in `references/channel-voice.md`):
- Conversational, contractions allowed, short sentences
- No buzzwords ("game-changer," "revolutionary," "10x")
- One product per video — never stack two products' CTAs in one script
- If a number is in COST.md, state it plainly; do not round dramatically or oversell precision

## Step 5 — Output

Create one file per video, not one combined file. File naming: `tiktok/[project-name]/video-NN-short-slug.md`, zero-padded two-digit numbering across the whole series regardless of pillar (e.g. `video-01-...`, `video-02-...`), ordered per the posting plan in Step 6, not grouped by pillar.

Each video file should contain just the script, ready to read on camera — no meta-commentary, no "here's video 1 about X" framing inside the file itself. Use this minimal frontmatter at the top of each file for tracking:

```markdown
---
pillar: The Decision | Building for SEA | Indie Math
source: [which doc/section this came from]
---

[Hook line]

[Setup]

[Turn/Insight]

[Payoff/CTA]
```

Also create one `tiktok/[project-name]/POSTING_PLAN.md` covering:
- Posting order with one-line rationale per slot (strongest hook first, save-bait content early — see `references/posting-plan-guide.md` for the ordering heuristics used previously)
- Suggested cadence (daily for the first week if this is a new channel; 4-5/week if the channel already has history — ask the user which applies if unclear)
- Bio/CTA setup reminder (one-line channel promise + single landing page link, not a full portfolio link)

## Step 6 — Review with the user before finalizing

Before writing all script files, show the user the pillar/count breakdown from Step 3 and ask if it looks right. This avoids generating 15 files the user didn't want. Do not skip this confirmation step even if the user seems to be in a hurry — generating the wrong count wastes more of their time than one confirmation question.

## Edge cases

- **Project has no COST.md**: skip Pillar 3 entirely, tell the user why, offer to regenerate that pillar once COST.md exists.
- **Project is not SEA/Vietnam-specific at all** (e.g. a pure dev tool with no regional angle): skip Pillar 2, do not force a SEA angle that isn't really there.
- **IMPLEMENT_PLAN.md has very few explicit trade-off justifications**: don't invent reasoning that isn't stated. It's fine for Pillar 1 to be thin — flag it to the user rather than fabricating "why" statements the docs don't actually contain.
- **User wants a 4th pillar or a different format entirely**: accommodate, but confirm explicitly since it deviates from the established channel voice — check `references/channel-voice.md` first to keep continuity with the rest of the channel.
