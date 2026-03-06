# How to Use This During an Incident

A practical guide for using this handbook during live incidents. Learn when to apply recipes, when to switch to investigation patterns, and how to reduce uncertainty quickly while systems are under pressure.

---

## How to Use This During an Incident

This handbook is designed to be used while something is breaking, not read end‑to‑end in calm conditions.

You do not need to follow it linearly.  
You use it situationally, based on what kind of problem you’re facing.

---

## First: Stabilise Before You Optimise

When an incident starts, the goal is not deep understanding.  
The goal is reducing uncertainty quickly.

Start by answering three questions:

- Is this affecting many users or a few?
- Is the failure consistent or intermittent?
- Is it getting worse, better, or stable?

You don’t need perfect answers — just direction.

---

## When the Problem Is Concrete

Use the **Recipes** first.

Examples:

- Clear errors in logs
- Authentication failures
- Timeouts
- Throttling
- Retries
- Known services misbehaving

In those cases:

- Pick a recipe that matches the symptom
- Run it as‑is
- Narrow the time window aggressively
- Ignore anything that doesn’t reduce uncertainty

Recipes are for execution.

---

## When the Problem Is Ambiguous

Switch to **Advanced Patterns** when:

- Logs contradict each other
- Errors appear unrelated
- Multiple theories exist
- The “obvious” explanation keeps shifting
- Searching just amplifies confusion

Advanced Patterns help you decide:

- Where to look next
- What to stop looking at
- Whether you’re chasing symptoms

Patterns are for orientation.

---

## How to Move Between Recipes and Patterns

Most incidents require both.

A common flow looks like:

1. Use a Recipe to collect initial signal
2. Apply an Advanced Pattern to interpret what you’re seeing
3. Run a second, narrower Recipe
4. Reassess impact and direction

This loop repeats until:

- The system stabilises, or
- Risk is reduced enough to pause

---

## What to Do Under Time Pressure

When time is limited:

- Reduce the search space early
- Prefer aggregation over raw logs
- Avoid perfect explanations
- Focus on what changes decisions

If a search doesn’t change what you’d do next, stop running it.

---

## What “Done” Looks Like

An incident does not need full understanding to be considered “handled”.

You are done when:

- Impact is contained or mitigated
- The system is stable
- You can explain roughly what happened and why

Deep root cause analysis can — and often should — wait.

---

## After the Incident

Once pressure drops:

- Revisit near‑miss signals
- Reconstruct timelines
- Capture what was confusing
- Note which searches helped and which didn’t

This is where the handbook grows.

---

## Final Note

This handbook is not a replacement for judgement.  
It exists to support it under pressure.

If you’re unsure what to do next, that’s normal — and usually a sign to pause, simplify, and narrow.

---

<div style="display:flex; justify-content:flex-end; margin-top:18px;">
  <a href="./introduction.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Introduction</a> |
  <a href="./foundations.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Foundations</a> |
  <a href="./recipes.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a> |
  <a href="./advanced-patterns.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Advanced Patterns</a> |
  <a href="./glossary.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Glossary</a> |
  <a href="./changelog.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Changelog</a>
</div>
