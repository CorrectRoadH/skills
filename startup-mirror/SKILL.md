---
name: startup-mirror
description: Startup-failure stress test based on the Loot Drop (loot-drop.io) methodology — diagnose a startup idea against the 7 failure antipatterns (Hallucination, Bonfire, Civil War, Crushed, Lemon, Math Problem, Outlaw), surface cascade risks, and produce a Rebuild Plan. Use when the user wants to pressure-test an idea, run a "创业模式挑战", do a startup self-assessment, evaluate a new venture, or turn a concept into an actionable plan. Triggers on "review my startup idea", "创业挑战", "startup stress test", "validate this business", "Loot Drop style review", or any new-venture concept the user wants challenged before building.
version: 1.0.0
---

# Startup Mirror — 创业模式挑战

A rigorous, adversarial review of a startup idea, modeled on Loot Drop's framework of 1,628+ dead-company autopsies. The goal is not to be nice — it is to find the antipattern that will kill the company before the founder spends a year finding it themselves.

Source methodology: https://www.loot-drop.io/why-they-fail

## When to use

- User presents a new idea ("I'm thinking about building X…")
- User asks for honest feedback, a pre-mortem, or a "challenge"
- User wants a go/no-go decision before committing
- User wants a structured plan (Rebuild Plan format)

Don't use for: already-shipped products doing post-mortems (use a different retro framework); purely technical architecture reviews.

## The 7 Antipatterns

The patterns are not independent — most deaths are cascades (e.g., Hallucination → Bonfire → Crushed). Name the dominant one, then trace the cascade.

| # | Name | Root cause | Share of deaths | Median lifespan |
|---|------|-----------|----------------|-----------------|
| 1 | **The Hallucination** 🔮 | Building for a customer that does not exist | 11.6% | — |
| 2 | **The Bonfire** 🔥 | Spending as if revenue is a formality | 11.2% | ~4 years |
| 3 | **The Civil War** ⚔️ | Team/founder conflict destroys the company | 1.0% | — |
| 4 | **The Crushed** 🏴 | Out-executed, out-spent, out-gunned | **54.1%** | — |
| 5 | **The Lemon** 🍋 | Product cannot deliver the promise | 3.4% | — |
| 6 | **The Math Problem** 📉 | Every sale loses money at scale | — | — |
| 7 | **The Outlaw** ⚖️ | Regulation is the immovable object | — | ~7 years |

Note: The Crushed dominates by a wide margin. If the idea is in a crowded category, that is the first place to probe.

## Workflow

Run these phases in order. Don't skip to the plan until the diagnosis is done — a plan built around the wrong antipattern is worse than no plan.

### Phase 1 — Gather the idea

Ask (at minimum):
- What is the product in one sentence?
- Who is the customer, and what are they doing today instead?
- How will it make money?
- What stage is it (pre-idea, pre-revenue, ramping)?
- What is the founder's runway and team structure?

If any of these are hand-wavy, that is itself a signal — note which antipattern the vagueness maps to.

### Phase 2 — The Mirror (diagnose)

Ask the user these exact 7 questions, one per antipattern. Score each 0 (safe), 1 (caution), 2 (danger). Be ruthlessly honest on their behalf — if an answer is evasive, press on it.

1. **Hallucination**: "When potential customers hear about your product, what happens next without any prompting from you?"
2. **Bonfire**: "If all fundraising became impossible tomorrow, how long would it take you to cut burn enough to reach profitability on your current revenue trajectory?"
3. **Civil War**: "When you and your co-founder disagree on a major strategic decision, what typically happens?"
4. **Crushed**: "When you lost your last three competitive deals, what was the primary reason customers chose the competitor?"
5. **Lemon**: "When your most experienced engineer privately tells you the core technology will not scale to production requirements, what is your honest first reaction?"
6. **Outlaw**: "If a regulator showed up tomorrow with full enforcement authority and required you to operate in complete compliance with existing laws, what would happen to your business?"
7. **Math Problem**: "Take your fully-loaded cost per customer and current revenue per customer. Assuming costs improve 25%, what price would customers need to pay for you to achieve 20% gross margins?"

Roll up the total:
- **0–2**: SAFE
- **3–5**: CAUTION
- **6–8**: DANGER
- **9–11**: HIGH RISK
- **12–14**: WATCH CLOSELY (near-death)

### Phase 3 — The Web (cascade)

Pick the top 1–2 scoring antipatterns and trace how they likely cascade. Typical chains:
- Hallucination → Bonfire (spending chasing fake demand) → Crushed (a real competitor wins the real market)
- Lemon → Math Problem (fixing the product inflates unit cost) → Bonfire
- Outlaw → Civil War (co-founders split on how to handle the regulator)

Name the chain explicitly. This is what kills companies — not a single antipattern but the cascade.

### Phase 4 — The Autopsies (ground it)

Give 2–3 real dead-startup examples from the user's sector that died of the same dominant antipattern. Cite the company, the year, rough capital burned, and the one-line cause. If you don't know specific cases, say so rather than fabricate — the user can look them up on loot-drop.io's `/deep-dives` (22 sectors) or `/lists.html` (death lists).

### Phase 5 — The Rebuild Plan (act)

Only after Phases 1–4. Produce a 5-section plan in this exact structure, and ensure every section explicitly addresses the dominant antipattern(s):

```
# Rebuild Plan: <idea name>

## 1. What to Build
<The minimum version that tests the riskiest assumption — not the full vision>

## 2. Market Analysis
<Who the customer actually is, what they do today, why they'd switch, sizing>

## 3. Build Steps
<Concrete sequence, each step designed to retire one antipattern's risk>

## 4. Tech Stack
<Chosen to avoid Lemon risk; pragmatic, not fashionable>

## 5. Revenue Model
<Unit economics that survive the Math Problem test; pricing that clears gross-margin bar>
```

End with a **Risk Retirement Ledger**: a table listing each antipattern and the specific step in the plan that is supposed to retire it. Any antipattern without a retirement step is a known unretired risk — call it out.

## Output structure

Default output template (use unless the user asks for something shorter):

```
# Startup Mirror Review: <idea>

## Phase 1 — Idea Snapshot
<1 paragraph>

## Phase 2 — The Mirror
| Antipattern | Score | Evidence |
...
**Total: X/14 — <risk level>**

## Phase 3 — The Cascade
<dominant chain, 2-3 sentences>

## Phase 4 — Autopsies
<2-3 cases or "no specific cases recalled, see loot-drop.io/deep-dives">

## Phase 5 — Rebuild Plan
<as above>

## Risk Retirement Ledger
| Antipattern | Retired by | Residual risk |
```

## Style

- Be an adversarial second opinion, not a cheerleader. The user asked to be challenged; softening the diagnosis defeats the skill.
- When the user pushes back, re-examine with them — don't capitulate just because they're frustrated. Reference the failure data.
- Prefer concrete over abstract ("your CAC math needs $X LTV" beats "unit economics matter").
- When data is missing, say "unknown — this is itself a risk" rather than guessing.

## References

- Site: https://www.loot-drop.io
- 7 antipatterns detail: https://www.loot-drop.io/why-they-fail
- Sector failure matrix: https://www.loot-drop.io/deep-dives
- Death lists (curated): https://www.loot-drop.io/lists.html
- Rebuild Plans (examples of the target format): https://www.loot-drop.io/rebuilds
