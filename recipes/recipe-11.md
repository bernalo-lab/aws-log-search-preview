# Recipe 11 — Detect Retry Storms and Amplification

**Detect Retry Storms and Amplification**

**Confidence:** High  
**Use when:** Traffic spikes, cascading failures, “everything is timing out” incidents

---

## Problem

Retries can multiply load during partial failures, turning a small issue into a full outage. You need to spot retry loops early.

## Before You Run The Query

> **Note:** This recipe assumes your logs include a field such as `tenantId` (or `requestId`).
> If not, replace it with the identifier your system uses (e.g. `accountId`, `customerId`, endpoint name).

## Query

```sql
fields @timestamp, @message, requestId
| filter @message like /retry|retrying|attempt \d+/i
| stats count() as retries by requestId
| sort retries desc
| limit 20
```

## Why This Works

High retry counts per request often indicate an amplification loop: the system is working harder and getting less done, accelerating failure.

## Operational Insight

Retries are a load multiplier. Under failure, they can become the incident.

## When It Fails

- Retries aren’t logged explicitly  
- requestId is missing or reused

## Variations

- Group by endpoint/operation if logged: stats count() by operation, bin(5m)
- Add time binning to see if retries are accelerating: stats count() by bin(1m)

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="./recipe-08.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Previous</div>
    <div style="font-weight:600; color:#111827;">Recipe 08 — Find the Noisiest Customer or Tenant</div>
  </a>
  <a href="./recipe-17.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Next</div>
    <div style="font-weight:600; color:#111827;">Recipe 17 - Identify Feature Flags Causing Partial Failures</div>
  </a>
</div>

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../introduction.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Introduction</a> | 
  <a href="../foundations.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Foundation</a> |
  <a href="../recipes.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a> |
  <a href="../advanced-patterns.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Advanced Patterns</a> |
  <a href="../how-to-use-during-an-incident.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Operational guidance</a> |
  <a href="../glossary.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Glossary</a> |
  <a href="../changelog.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Changelog</a>
</div>
