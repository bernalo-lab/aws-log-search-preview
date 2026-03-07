# Recipe 34 - Identify Incorrect Fallback or Default Behaviour

**Identify Incorrect Fallback or Default Behaviour**

**Confidence:** Medium  
**Use when:** Systems “work”, but not as intended

---

## Problem

Fallback logic activates unexpectedly, masking underlying failures.

## Before You Run The Query

> Fallback behaviour is often logged at info level or not logged at all. Absence of results does not rule it out.

## Query

```sql
fields @timestamp, @message
| filter @message like /fallback|default|using cached|degraded mode/i
| sort @timestamp asc
```

## Why This Works

Fallback paths often log informational messages rather than errors.

## Operational Insight

Fallbacks protect uptime — and hide problems.

## When It Fails

- Fallbacks are silent
- Logs are too coarse

## Variations

- Compare fallback frequency over time  
- Correlate with upstream failures

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../recipes.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a>
</div>