# Production Incident Debugging Playbook (Preview Edition)

This playbook provides practical debugging workflows used by SREs, DevOps engineers, and backend developers when diagnosing production incidents.

The goal is not just finding the error — but **reducing time‑to‑understanding during an active incident.**

This preview edition contains **3 core incident playbooks** from the full Production Incident Debugging Toolkit.

---

# Incident Debugging Framework

During a production incident engineers often lose time because of:

• misleading error messages  
• incomplete logs  
• noisy monitoring signals  
• unclear dependency failures  

This toolkit follows a simple investigation model:

Signal → Classification → Evidence → Action

Signal  
The observable failure such as:

• error logs  
• latency spikes  
• dependency failures  
• service crashes  

Classification  
Determine the likely failure category:

• dependency unavailable  
• resource exhaustion  
• configuration error  
• deployment regression  

Evidence  
Collect supporting signals:

• logs  
• metrics  
• traces  
• deployment history  

Action  
Choose the safest operational response:

• retry request  
• rollback deployment  
• scale infrastructure  
• isolate dependency  

---

# Incident Playbooks Included in this Preview

<div style="display:flex; justify-content:flex-end; margin-top:18px;">
  <a href="./playbooks/api-gateway-failures.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">API Gateway 502 / 504 Failures</div>
  </a>
  <a href="./playbooks/database-connection-exhaustion.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">Database Connection Exhaustion</div>
  </a>
  <a href="./playbooks/aws-lambda-timeout-debugging.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">
    <div style="font-size:12px; color:#6b7280; margin-bottom:6px;">AWS Lambda Timeout Debugging</div>
  </a>
</div>

Each playbook contains investigation steps commonly used during real production incidents.

---

# Playbook 1 — API Gateway 502 / 504 Failures

Typical Symptoms

• sudden spike in HTTP 502 or 504 errors  
• intermittent client timeouts  
• partial service outage  

Common Causes

• upstream dependency failure  
• container crash loops  
• load balancer routing issues  
• service deployment errors  

Example CloudWatch Logs Insights Query

fields @timestamp, @message  
| filter status >= 500  
| sort @timestamp desc  
| limit 50  

Investigation Steps

1. Confirm which endpoints are failing.
2. Check if failures started after a deployment.
3. Identify upstream service dependencies.
4. Check load balancer health checks.
5. Determine the blast radius of the incident.

Immediate Mitigation

• retry logic  
• temporary traffic shift  
• rollback recent deployment  

---

# Playbook 2 — Database Connection Exhaustion

Typical Symptoms

• API latency spikes  
• request timeouts  
• database connection errors  

Common Error Messages

too many connections  
connection pool exhausted  
timeout acquiring connection  

Common Causes

• connection leaks in application code  
• long running queries  
• insufficient connection pool size  
• sudden traffic spikes  

Investigation Steps

1. Check application logs for pool exhaustion messages.
2. Review current database connection count.
3. Identify slow or blocking queries.
4. Check for long‑running transactions.
5. Verify whether recent code changes affected connection handling.

Immediate Mitigation

• restart affected application pods  
• temporarily increase connection pool size  
• terminate long running queries  

---

# Playbook 3 — AWS Lambda Timeout Debugging

Typical Symptoms

• spike in Lambda error rate  
• increased execution duration  
• functions timing out  

Example Error Messages

Task timed out after 30 seconds  
Process exited before completing request  
Runtime exited with error  

Common Causes

• external API latency  
• database delays  
• insufficient memory allocation  
• cold start delays  

Investigation Steps

1. Review CloudWatch logs for recent failures.
2. Identify dependency calls within the function.
3. Check execution duration metrics.
4. Verify timeout and memory configuration.
5. Determine whether traffic spikes triggered the issue.

Example CloudWatch Logs Insights Query

fields @timestamp, @message  
| filter @message like /ERROR/  
| sort @timestamp desc  
| limit 20  

Immediate Mitigation

• increase memory allocation  
• increase timeout limit  
• retry failed invocations  
• throttle incoming traffic if necessary  

---

# Full Production Toolkit

The full Production Incident Debugging Toolkit contains additional playbooks including:

• Kubernetes CrashLoopBackOff  
• Payment Service Outage  
• Redis Latency Spike  
• CloudWatch Cost Investigation  

These advanced playbooks are available in the **full edition** of the toolkit.

