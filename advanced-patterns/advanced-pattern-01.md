# Advanced Pattern 01 — Work Backwards from the Blast Radius

*Work Backwards from the Blast Radius*

---

**When to use:**  
When logs are overwhelming and everything appears broken.

---

## The Pattern

Instead of starting where errors are loudest, start where **impact is smallest**.

Ask:

- Which users are affected?
- Which operations are failing?
- Which paths are still working?

Then move backwards toward shared components.

---

## Why This Works

Failures propagate outward.  
Symptoms spread faster than origins.

By starting at the edge of the blast radius, you avoid chasing secondary failures.

---

## Common Mistake

Starting with the first error you see in the logs rather than the first meaningful failure.

---

## How This Connects to Recipes

- Use **Recipe 01** to find the first error
- Use **Recipe 08** to identify whether impact is concentrated
- Use **Recipe 14** to suppress noise

---

## Operational Insight

Wide impact ≠ root cause.  
It often means the root cause is earlier and quieter.

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="./advanced-patterns.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Previous</div>
    <div style="font-weight:600; color:#111827;">Advanced Patterns</div>
  </a>
  <a href="./advanced-pattern-02.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Next</div>
    <div style="font-weight:600; color:#111827;">Advanced Pattern 02 — Treat Logs as Evidence, Not Truth</div>
  </a>
</div>
