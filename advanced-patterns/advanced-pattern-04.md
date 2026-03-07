# Advanced Pattern 04 — Collapse the Search Space Early

**Collapse the Search Space Early**

**When to use:**  
When time pressure is high and logs are huge.

---

## The Pattern

Reduce possibilities aggressively before diving deep

Ways to collapse:

- Narrow time window
- Focus on one failing path
- Exclude known-good components
- Ignore retries initially

---

## Why This Works

Incidents punish breadth.
Depth wins faster.

---

## Common Mistake

Trying to understand everything before acting.

---

## How This Connects to Recipes

- Use **Recipe 06** for time bounding
- Use **Recipe 14** for noise suppression
- Use **Recipe 09** for focused tracing

---

## Operational Insight

You can always widen the search later.
You rarely get time back.

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../advanced-patterns.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Advanced Patterns</a>
</div>