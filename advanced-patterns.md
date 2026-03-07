# Advanced Patterns

A guide to incident investigation strategies used when log searches alone are not enough. This section introduces practical mental models and heuristics that help engineers reason through ambiguous, noisy, or overlapping failures during real-world incident response. 

---

The recipes in this handbook focus on *what to search and how to search it*.

Advanced Patterns focus on something different: **how to think when the search itself becomes unclear**.

These patterns are not tied to a specific query or tool.  
They describe common ways experienced engineers approach incidents when:

- Logs are noisy or contradictory
- Multiple failures overlap
- The obvious error is not the real problem
- Time pressure distorts decision-making

Rather than providing copy‑paste queries, this section captures **mental models and heuristics** that help you decide:

- Where to look first
- What to ignore initially
- How to separate cause from symptoms
- When to stop searching and start acting

You don’t need to read these patterns in order.  
They’re designed to be dipped into when a situation feels confusing or stalled.

If you’re unsure where to start:

- Use the **Recipes** when the problem is concrete
- Use **Advanced Patterns** when the problem is ambiguous

Both are intended to be used together, often during the same incident.

These patterns are distilled from repeated incident response scenarios.

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="./introduction.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-weight:600; color:#111827;">Introduction</div>
  </a>
  <a href="./advanced-patterns/advanced-pattern-01.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-weight:600; color:#111827;">Advanced Pattern 01 — Work Backwards from Impact</div>
  </a>
  <a href="./advanced-patterns/advanced-pattern-04.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-weight:600; color:#111827;">Advanced Pattern 04 — Collapse the Search Space Early</div>
  </a>
  <a href="./advanced-patterns/advanced-pattern-07.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-weight:600; color:#111827;">Advanced Pattern 07 - Actively Counter Confirmation Bias</div>
  </a>
</div>
