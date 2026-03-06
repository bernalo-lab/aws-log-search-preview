# Incident Debugging Playbook
## AWS CloudWatch Log Search Recipes for Production Incidents

During production incidents, engineers rarely search logs randomly.

They follow **repeatable investigation patterns**.

This playbook documents practical AWS CloudWatch log search queries that help engineers:

- Detect incidents quickly
- Identify impacted services
- Locate dependency failures
- Detect retry storms
- Trace failed requests
- Confirm recovery

These recipes are designed for **SREs, DevOps engineers, and platform teams** responsible for investigating production issues.

---

# Who This Playbook Is For

This guide is designed for:

• Site Reliability Engineers (SREs)  
• DevOps Engineers  
• Platform Engineers  
• Backend Developers  
• Incident Response Teams  

If you have ever asked:

- *“Which service is actually failing?”*
- *“Is this a dependency issue?”*
- *“Why are retries suddenly spiking?”*

These log search patterns will help.

---

# Typical Incident Investigation Flow

Most production incidents follow a similar investigation pattern:

Incident Trigger
↓
Confirm error spike
↓
Identify failing service
↓
Check dependency failures
↓
Detect retry behaviour
↓
Trace specific request
↓
Locate root cause
↓
Confirm recovery


The queries below follow this exact workflow.

---

# Stage 1 — Confirm the Error Spike

The first step during any incident is confirming that errors are actually occurring.

Query:

fields @timestamp, @message
| filter @message like /ERROR/
| sort @timestamp desc
| limit 20


Purpose:

- Confirm that the incident is real
- Identify the most recent errors
- Get a quick sense of the failure type

This is usually the **first query engineers run during triage**.

---

# Stage 2 — Identify the Impacted Service

Once errors are confirmed, the next step is identifying which service is responsible.

Query:

fields @timestamp, service, @message
| filter @message like /exception/
| stats count() by service
| sort count() desc


Purpose:

- Identify which service is generating the most errors
- Quickly narrow investigation scope

This step often reduces **a system-wide incident to a single failing service**.

---

# Stage 3 — Detect Dependency Failures

Many outages originate from upstream dependency failures.

Examples include:

- Payment APIs
- Authentication services
- Databases
- Third-party services

Query:


Purpose:

- Identify which service is generating the most errors
- Quickly narrow investigation scope

This step often reduces **a system-wide incident to a single failing service**.

---

# Stage 3 — Detect Dependency Failures

Many outages originate from upstream dependency failures.

Examples include:

- Payment APIs
- Authentication services
- Databases
- Third-party services

Query:


Purpose:

- Identify which service is generating the most errors
- Quickly narrow investigation scope

This step often reduces **a system-wide incident to a single failing service**.

---

# Stage 3 — Detect Dependency Failures

Many outages originate from upstream dependency failures.

Examples include:

- Payment APIs
- Authentication services
- Databases
- Third-party services

Query:


Purpose:

- Identify which service is generating the most errors
- Quickly narrow investigation scope

This step often reduces **a system-wide incident to a single failing service**.

---

# Stage 3 — Detect Dependency Failures

Many outages originate from upstream dependency failures.

Examples include:

- Payment APIs
- Authentication services
- Databases
- Third-party services

Query:


Purpose:

- Identify which service is generating the most errors
- Quickly narrow investigation scope

This step often reduces **a system-wide incident to a single failing service**.

---

# Stage 3 — Detect Dependency Failures

Many outages originate from upstream dependency failures.

Examples include:

- Payment APIs
- Authentication services
- Databases
- Third-party services

Query:

fields @timestamp, status, dependency
| filter status = 503
| stats count() by dependency
| sort count() desc


Purpose:

- Identify failing upstream dependencies
- Detect external service outages

If one dependency dominates the results, it is often the **root cause**.

---

# Stage 4 — Detect Retry Storms

Retry storms occur when applications repeatedly retry failed requests.

This can dramatically amplify outages.

Query:

fields @timestamp, requestId
| stats count() by requestId
| filter count > 5
| sort count desc


Purpose:

- Detect excessive retry behaviour
- Identify requests being repeatedly retried

Retry storms often indicate:

- Dependency timeouts
- network instability
- poorly configured retry policies

---

# Stage 5 — Trace a Specific Request

When investigating failures, engineers often need to reconstruct a single request.

Query:

fields @timestamp, requestId, service, @message
| filter requestId = "abc123"
| sort @timestamp asc


Purpose:

- Rebuild the full request timeline
- Track request movement across services
- Identify where the failure occurred

This technique is particularly useful in **microservice architectures**.

---

# Stage 6 — Detect Latency Spikes

Some incidents are caused by slow services rather than outright failures.

Query:

fields @timestamp, duration, service
| filter duration > 5000
| stats avg(duration), max(duration) by service
| sort max(duration) desc


Purpose:

- Detect services with abnormal latency
- Identify slow downstream dependencies

Latency spikes often precede **timeouts and cascading failures**.

---

# Stage 7 — Identify the Dominant Error Signal

Once investigation narrows, engineers need to identify the dominant error type.

Query:

fields @timestamp, errorCode, @message
| stats count() by errorCode
| sort count() desc


Purpose:

- Identify the most frequent error condition
- Surface the likely root cause signal

This helps determine whether the incident involves:

- authentication failures
- dependency outages
- configuration errors
- resource exhaustion

---

# Stage 8 — Confirm Recovery

Once mitigation is applied, engineers must confirm that the system is recovering.

Query:

fields @timestamp
| filter @message like /success/
| stats count() by bin(5m)


Purpose:

- Track successful requests over time
- Confirm recovery trend

If success rates begin increasing again, recovery is underway.

---

# Common Incident Root Causes

Many incidents ultimately trace back to a small number of causes.

Typical examples include:

• Dependency service outages  
• Database connection pool exhaustion  
• API rate limiting  
• Misconfigured retries  
• Infrastructure scaling issues  
• Configuration changes  

Structured log search patterns significantly reduce the time required to detect these issues.

---

# Advanced Incident Patterns (Full Edition)

The **Full Edition** includes additional advanced investigation recipes, such as:

- Dependency cascade detection
- Lambda cold start analysis
- Kubernetes restart patterns
- Memory leak detection
- API throttling detection
- Connection pool exhaustion signals
- JSON structured log filtering
- Cross-service trace correlation

These advanced patterns are used by **production SRE teams** during complex incident investigations.

---

# About AWS Log Search Recipes

This playbook is part of the **AWS Log Search Recipes** collection.

The full collection includes:

- 40+ production-ready queries
- JSON log search patterns
- incident debugging playbooks
- advanced troubleshooting recipes
- searchable HTML reference
- downloadable PDF handbook

Designed for engineers who want to **debug production systems faster using CloudWatch logs**.

---

<div style="display:flex; justify-content:flex-end; margin-top:18px;">
  <a href="../introduction.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Introduction</a>
</div>



