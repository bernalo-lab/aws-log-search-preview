# Recipe 08 — Find the Noisiest Customer or Tenant

*Find the Noisiest Customer or Tenant*

**Confidence:** High  
**Use when:** Multi-tenant incidents, “only one customer is affected”, uneven error reports

---

## Problem

A single tenant/customer can generate most of the errors and make an incident look global. You need to identify the outlier fast.

## Before You Run The Query

> **Note:** This query assumes you log a tenant identifier as a structured field (e.g., `tenantId`, `customerId`, or `accountId`).  
> If your identifier is embedded in free text, you may need to extract it first (or adjust the field name).

## Query

```sql
fields @timestamp, tenantId, message
| filter message like /error|exception|failed/
| stats count(*) as errors by tenantId
| sort errors desc
| limit 20
```

## Why This Works

Aggregating by tenant reveals concentration. Outliers often indicate bad input data, tenant-specific config, abusive traffic, or unique integration behaviour.

## Operational Insight

Many “platform incidents” are actually one customer’s edge case at scale.

## When It Fails

- `tenantId` is missing or inconsistently logged  
- Tenant identifiers are embedded in free text instead of a structured field

## Variations

- Group by `customerId` or `accountId` depending on your domain  
- Add a time window (e.g., last 30–60 minutes) during active incidents

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="./recipe-07.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Previous</div>
    <div style="font-weight:600; color:#111827;">Recipe 07 — Compare Before vs After a Deploy</div>
  </a>
  <a href="./recipe-09.html" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Next</div>
    <div style="font-weight:600; color:#111827;">Recipe 09 — Trace a Single Request Across Services</div>
  </a>
</div>
