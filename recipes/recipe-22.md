# Recipe 22 - Detect Background Job or Scheduler Failures

**Detect Background Job or Scheduler Failures**

**Confidence:** Medium-High  
**Use when:** Periodic tasks silently stop running

---

## Problem

Scheduled jobs stop executing or fail quietly, causing delayed or missing processing.

## Query

```sql
fields @timestamp, @message
| filter @message like /scheduled|cron|job started|job failed/i
| sort @timestamp asc
```

## Why This Works

Schedulers usually emit predictable start/failure messages. Missing or repeated failures indicate stalled jobs.

## Operational Insight

If background work fails silently, the system degrades slowly.

## When It Fails

- Jobs don’t log lifecycle events
- Failures occur outside application logs

## Variations

- Count executions per time window
- Alert on missing “job started” events

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../recipes.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a>
</div>