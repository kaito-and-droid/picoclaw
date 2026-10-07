# Script Template (annotated)

Use this structure for every video. Total spoken length should land around 50-70 seconds when read at a natural pace — don't pad to hit a time target, and don't worry if a tight, well-told version runs shorter.

```
---
pillar: [The Decision | Building for SEA | Indie Math]
source: [e.g. "IMPLEMENT_PLAN.md, Architecture section, WebSocket vs REST"]
---

[HOOK — 0-3s]
One or two sentences. A claim or a question. Must work with zero prior context.
No "Hey guys," no "So today," no channel-intro framing.

[SETUP — 3-15s]
Name the product once. One sentence on what it does — only as much as needed
for the Turn to make sense. Don't summarize the whole product.

[TURN/INSIGHT — 15-45s]
The actual content. One idea only. This is where the specific decision, number,
or market detail from the source doc goes — stated plainly, with the real reason
behind it. This is the part that has to be true and specific, not generic advice.

[PAYOFF/CTA — 45-60s]
One takeaway sentence. Optional soft mention of the product / what's next.
Never a hard sell, never two products in one CTA.
```

## Worked micro-example (structure only, not full length)

```
---
pillar: The Decision
source: IMPLEMENT_PLAN.md — "Local validate + background sync, not server-only check"
---

[HOOK]
A license check that only works when you're online isn't a license check —
it's an outage waiting to happen.

[SETUP]
This is from lib-license, the licensing SDK behind a payment app I built.

[TURN/INSIGHT]
The easy version checks the license against a server every time the app opens.
But that means the app breaks the moment the network does — bad WiFi, a backend
blip, doesn't matter, the user's locked out of software they paid for. So
lib-license validates locally first, against a signed snapshot, and syncs with
the server in the background. The server is still the source of truth — it's
just not a single point of failure for every single app launch.

[PAYOFF/CTA]
The boring infrastructure decisions are the ones users only notice when they're
missing.
```

## Common mistakes to avoid when filling this in

- **Don't explain too much in Setup.** If Setup runs longer than 2 sentences, the Turn is starting late and the hook's momentum is lost.
- **Don't put the lesson in the Hook.** The Hook should create a question or tension; the Payoff resolves it. If the Hook already states the conclusion, there's nothing left to deliver.
- **Don't write the CTA as a sales line.** "Follow for more" or a waitlist mention should feel like a natural next-step, not a pitch. If in doubt, cut the CTA down to one sentence.
- **One technical term is fine, three is a lecture.** If the Turn needs to introduce more than one piece of jargon to make sense, the topic is probably two videos, not one.
