# API Gateway 502 / 504 Failures

This playbook describes a structured approach for diagnosing API Gateway failures,
particularly HTTP **502 Bad Gateway** and **504 Gateway Timeout** errors.

These incidents are common in distributed systems where API gateways sit between
clients and multiple backend services.

---

# Typical Symptoms

Engineers may observe:

• sudden spike in HTTP 502 or 504 responses  
• intermittent client timeouts  
• partial outage affecting specific endpoints  
• upstream services reporting connection resets  

Monitoring dashboards may show:

• increased error rate  
• elevated latency  
• dependency health degradation  

---

# Common Causes

API Gateway failures are often symptoms of deeper system problems.

Typical root causes include:

• upstream service crash  
• container restart loops  
• load balancer misconfiguration  
• dependency timeout  
• DNS resolution issues  
• recent deployment regressions  

---

# Initial Triage

The first step is determining **scope and blast radius**.

Key questions:

1. Which endpoints are failing?
2. Did the incident start after a deployment?
3. Are failures occurring across all regions?
4. Is the gateway reachable but upstream services failing?

Understanding blast radius helps determine urgency and mitigation strategy.

---

# Example CloudWatch Logs Insights Query

Use a simple query to surface recent gateway errors:

fields @timestamp, @message  
| filter status >= 500  
| sort @timestamp desc  
| limit 50  

This query helps identify:

• failing endpoints  
• repeating error patterns  
• dependency references in logs  

---

# Investigation Workflow

Follow a structured sequence.

## Step 1 — Confirm error patterns

Check logs for:

• repeated endpoints
• identical upstream errors
• dependency timeout messages

---

## Step 2 — Check upstream services

Verify:

• service container health
• Kubernetes pod status
• ECS / container restart activity
• dependency availability

If upstream services are down, the gateway errors are secondary symptoms.

---

## Step 3 — Review recent deployments

Deployment regressions frequently trigger gateway failures.

Check:

• latest application release
• infrastructure changes
• configuration updates
• feature flag rollouts

---

## Step 4 — Validate load balancer routing

Misconfigured routing rules can produce gateway failures.

Verify:

• target groups
• health checks
• listener rules
• SSL certificates

---

# Immediate Mitigation Options

Depending on root cause, common mitigation actions include:

• rollback recent deployment
• restart unhealthy service containers
• temporarily route traffic to healthy instances
• enable retry logic
• shift traffic between availability zones

The goal is **restoring service quickly** while deeper investigation continues.

---

# Key Lesson

API Gateway errors are rarely the root cause.

They usually signal:

• dependency outages
• infrastructure instability
• deployment regressions

Treat gateway errors as **symptoms**, not the failure itself.
