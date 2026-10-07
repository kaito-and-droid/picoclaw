# Extraction Checklist

Use this when reading APP_IDEA.md / IMPLEMENT_PLAN.md / COST.md to decide what counts as a usable video candidate per pillar. The bar is: **could a developer or indie-hacker viewer learn something specific from this in 60 seconds?** Vague statements don't qualify; specific decisions and numbers do.

## Pillar 1 — The Decision

Look for sentences in IMPLEMENT_PLAN.md (and APP_IDEA.md's stack/architecture sections) that follow this pattern:

- "We chose X instead of Y because..."
- "X over Y" comparisons with a stated reason
- Architecture choices with an explicit trade-off acknowledged (not just "we use X" with no reasoning)
- Security/encryption/protocol decisions where the doc explains *why*, not just *what*
- Anything described as harder-to-build-but-better, or a deliberate rejection of the "easier" default approach

**Does NOT qualify:**
- A tech stack list with no reasoning ("Uses Kotlin, Ktor, SQLDelight" alone is not a video — there's no "why")
- Standard/default choices with no trade-off mentioned (e.g. "uses Git for version control")

**Good candidate test:** Could you write "Why I chose X instead of Y" as the hook, and have a real answer? If the doc only states X with no Y or no reason, it's not ready — skip it rather than inventing the missing half.

## Pillar 2 — Building for SEA

Look for:

- Currency/locale handling specific to a SEA market (VND, SJC gold, local payment rails)
- References to local platforms with no equivalent API/integration path (Zalo, Voz.vn, local marketplaces)
- Regulatory or distribution constraints specific to a market (e.g. Play Store restrictions in certain categories, requiring APK-only distribution)
- A stated gap between what a "generic"/Western version of this product does and what the SEA-specific version needs to do differently
- Language/localization requirements beyond simple translation (e.g. CEFR targets for Vietnamese English learners, cultural context for financial behavior)

**Does NOT qualify:**
- Generic "supports Vietnamese language" with no deeper explanation
- Stating the target market without explaining a concrete product difference that results from it

**Good candidate test:** Could a developer building a similar app for a Western market read this and learn something they wouldn't have thought of? If the SEA angle is just "translated into Vietnamese," it's too thin on its own — look for the deeper product implication.

## Pillar 3 — Indie Math

Look for:

- Concrete dollar figures in COST.md at specific user-count tiers (10/100/1000 users)
- Pricing model decisions (one-time vs subscription) with reasoning in APP_IDEA.md
- Margin or cost-driver breakdowns (what's free-tier, what scales per-user, what's the expensive line item)
- Solo-dev time/scope constraints explicitly mentioned (e.g. "CLI first because a dashboard would take 3x longer")
- The three-document planning habit itself, if the user wants a meta video about process (use sparingly — this angle works once or twice per channel, not per project)

**Does NOT qualify:**
- COST.md numbers with no context for why they're notable (just restating a number isn't a story — pair it with the reasoning behind the architecture that produced it)
- Pricing stated without any rationale ("It's $9" alone isn't a video — "$9 one-time because X" is)

**Good candidate test:** Does the number surprise or inform a viewer who's wondered "what does this actually cost to run"? If COST.md is missing or has only placeholder estimates, flag this to the user rather than presenting rough guesses as real numbers.

## General quality bar across all pillars

Before finalizing a candidate list, re-read each one and ask: **if I removed the product name, would this still be a specific, true sentence — or could it apply to literally any app?** If it could apply to any app, it's not specific enough yet. Either find the specific detail in the docs that makes it concrete, or drop the candidate.
