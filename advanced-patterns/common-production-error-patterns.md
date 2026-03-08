# Common Production Error Patterns

This document summarises **common error patterns observed in production systems**.
Recognising these patterns quickly can significantly reduce the time required to
diagnose incidents.

The goal is not to memorise every error message but to recognise the **category of
failure** and apply the appropriate investigation playbook.

---

# Pattern 1 — Dependency Unavailable

Typical Symptoms:

• HTTP 502 / 503 / 504 errors  
• upstream connection reset messages  
• sudden spike in request failures  

Example Log Messages:

Service unavailable  
Upstream connection reset  
502 Bad Gateway  

Typical Root Causes:

• downstream service outage  
• DNS resolution failure  
• dependency deployment failure  
• network connectivity issues  

Recommended Investigation:

• check dependency health  
• confirm service endpoints  
• review recent deployments  
• inspect load balancer health checks  

---

# Pattern 2 — Resource Exhaustion

Typical Symptoms:

• sudden latency spikes  
• request timeouts  
• thread or connection pool errors  

Example Log Messages:

connection pool exhausted  
too many open files  
out of memory  

Typical Root Causes:

• traffic spikes  
• inefficient queries or code paths  
• insufficient infrastructure scaling  
• connection leaks  

Recommended Investigation:

• inspect resource utilisation metrics  
• review connection pools and thread usage  
• check scaling configuration  
• identify long‑running processes  

---

# Pattern 3 — Timeout Cascades

Typical Symptoms:

• requests gradually slowing down  
• increasing timeout errors across services  
• retries amplifying system load  

Example Log Messages:

request timeout  
upstream timeout  
task timed out after X seconds  

Typical Root Causes:

• slow dependency services  
• overloaded infrastructure  
• network congestion  
• retry storms

Recommended Investigation:

• identify the slowest dependency  
• inspect service latency metrics  
• review retry configurations  
• confirm system capacity

---

# Pattern 4 — Deployment Regression

Typical Symptoms:

• incidents immediately after deployment  
• new error types appearing suddenly  
• specific endpoints failing

Example Log Messages:

null reference exception  
configuration missing  
unexpected runtime error

Typical Root Causes:

• code defects  
• configuration errors  
• environment variable issues  
• incompatible dependency versions

Recommended Investigation:

• review latest deployment changes  
• compare configuration between environments  
• check feature flag states  
• consider rollback if necessary

---

# Pattern 5 — Logging Noise vs Real Failures

Typical Symptoms:

• large volume of log messages  
• difficulty identifying true failure signals  
• repeated non‑critical warnings

Example Log Messages:

warning messages repeating  
retry attempts logged repeatedly

Typical Root Causes:

• overly verbose logging levels  
• noisy dependency libraries  
• poorly structured log messages

Recommended Investigation:

• search for true ERROR level events  
• filter logs using keywords  
• correlate logs with metrics and alerts

---

# Using Error Patterns During Incidents

When diagnosing incidents:

1. Identify the **dominant error pattern**.
2. Map it to the appropriate **incident playbook**.
3. Use **log search recipes** to collect evidence.
4. Apply mitigation while deeper investigation continues.

Recognising patterns quickly helps engineers move from:

confusion → signal → diagnosis

---

# Part of the Production Incident Debugging Toolkit

This reference complements:

• Incident Playbooks  
• CloudWatch Log Search Recipes  
• Structured Debugging Framework  

Together they provide a practical toolkit for diagnosing production incidents faster.

---

<div style="display:flex; gap:12px; justify-content:space-between; flex-wrap:wrap; margin-top:18px;">
  <a href="../advanced-patterns.md" style="flex:1; min-width:240px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Advanced Patterns</a>
</div>
