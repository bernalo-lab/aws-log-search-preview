# Recipe 17 - Identify Feature Flags Causing Partial Failures

**Recipe 17 - Identify Feature Flags Causing Partial Failures**

**Confidence:** Medium-High  
**Use when:** New behaviour affects some users but not others

---

## Problem

A feature flag rollout causes inconsistent behaviour. Some requests succeed, others fail, with no obvious pattern.

## Query

```sql
fields  @timestamp, @message
| filter @message like /feature flag|flag enabled|flag disabled/i
| stats count() as events by @message
| sort events desc
```

## Why This Works

Feature flag evaluations are often logged implicitly. Aggregating by message highlights which flags are active during failures.

## Operational Insight

Partial rollouts are safer — until observability lags behind rollout speed.

## When It Fails

- Feature flags aren’t logged
- Tenant identifiers are embedded in free text instead of a structured field

## Variations

- Group by `customerId` or `accountId` depending on your domain  
- Flag state is evaluated upstream and hidden

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../recipes.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a>
</div>