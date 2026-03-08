# AWS CloudWatch Log Search Recipes

This document provides practical **CloudWatch Logs Insights queries** used during real
production incidents.

When an incident occurs, engineers often lose time trying to remember the correct
query syntax. These recipes provide **ready-to-use patterns** that can be quickly
adapted to investigate issues.

Each query can be pasted directly into **CloudWatch Logs Insights**.

---

# Recipe 1 — Find Recent Errors

Use this query to quickly identify the most recent error messages across a log group.

```
fields @timestamp, @message
| filter @message like /ERROR/
| sort @timestamp desc
| limit 50
```

Useful for:

• identifying the first appearance of an error  
• spotting repeating error patterns  
• confirming whether an incident is ongoing  

---

# Recipe 2 — Find HTTP 5xx Errors

This query helps identify server-side failures.

```
fields @timestamp, status, @message
| filter status >= 500
| sort @timestamp desc
| limit 50
```

Useful for:

• API Gateway failures  
• backend service errors  
• diagnosing 502 / 504 incidents  

---

# Recipe 3 — Search for Specific Error Codes

During incidents engineers often need to locate a **specific error code** quickly.

Example:

```
fields @timestamp, @message
| filter @message like /E2044/
| sort @timestamp desc
```

Useful for:

• tracking application-specific errors  
• confirming whether an error is widespread  
• identifying affected services  

---

# Recipe 4 — Trace a Specific Request or ID

Many systems log request identifiers or transaction IDs.

```
fields @timestamp, @message
| filter @message like /requestId/
| sort @timestamp desc
```

Replace `requestId` with:

• licenceNumber  
• transactionId  
• userId  
• correlationId  

Useful for reconstructing the flow of a request across services.

---

# Recipe 5 — Identify Latency or Timeout Patterns

Timeout issues often appear in logs before a full outage occurs.

```
fields @timestamp, @message
| filter @message like /timeout/
| sort @timestamp desc
| limit 50
```

Useful for:

• detecting dependency timeouts  
• identifying slow services  
• diagnosing Lambda execution delays  

---

# Tips for Effective Log Searching

During an active incident:

• start with broad searches (ERROR, timeout, exception)  
• narrow queries as patterns emerge  
• correlate logs with metrics and deployment history  

Logs rarely provide the full picture on their own. The most effective debugging
combines **logs, metrics, and system context**.

---

# Part of the Production Incident Debugging Toolkit

These recipes are designed to complement the **incident playbooks** included in this
toolkit.

Together they provide:

• structured investigation workflows  
• ready-to-use log queries  
• faster incident diagnosis

The full toolkit expands this library with additional:

• CloudWatch queries  
• infrastructure debugging patterns  
• incident response playbooks.

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../recipes.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a>
</div>

