# AWS Log Search Recipes — Preview

Production incidents rarely start with dashboards.

They start with engineers asking:

**“What is actually failing?”**

This repository contains a preview of the **log interrogation patterns engineers use during real production incidents in AWS CloudWatch**.

These examples demonstrate how structured log searches and investigation playbooks help surface signal quickly during incident triage.

---

## Toolkit Overview

## Toolkit Overview

```mermaid
flowchart TD

A["Production Incident"] --> B["Incident Debugging Framework"]

B --> C["Incident Playbooks"]
B --> D["Log Search Recipes"]
B --> E["Error Pattern Reference"]

C --> C1["API Gateway Failures"]
C --> C2["Database Connection Exhaustion"]
C --> C3["AWS Lambda Timeout"]

D --> D1["Find Error Spikes"]
D --> D2["Trace Requests"]
D --> D3["Detect Timeouts"]

E --> E1["Dependency Failure"]
E --> E2["Resource Exhaustion"]
E --> E3["Deployment Regression"]

---

# What This Preview Includes

This preview repository contains:

• **Incident debugging playbooks**  
• **CloudWatch Logs Insights query recipes**  
• **Common production error patterns**

These examples show how experienced engineers:

- confirm error spikes
- identify failing services
- detect dependency failures
- uncover retry storms
- trace failing requests
- classify production failure patterns

All material is designed for **real production debugging**, not lab demonstrations.

---

# Repository Structure

```
incident-debugging-playbook.md

playbooks/
  api-gateway-failures.md
  database-connection-exhaustion.md
  aws-lambda-timeout-debugging.md

recipes/
  aws-cloudwatch-log-search-recipes.md

patterns/
  common-production-error-patterns.md
```

Together these files provide a **structured approach to production incident debugging**.

---

# Example Query

```sql
fields @timestamp, service, @message
| filter @message like /exception/
| stats count() by service
| sort count desc
```

**Purpose**

Identify which service is generating the majority of failures during an incident.

Instead of manually scanning logs, this query surfaces the **dominant failure source immediately**.

---

# Full Handbook

This repository is a preview of the **AWS Log Search Recipes Handbook**.

The full collection includes:

• 40+ production-ready CloudWatch Logs Insights queries  
• expanded incident debugging playbooks  
• advanced investigation patterns  
• searchable HTML reference  
• downloadable PDF handbook  

Designed for engineers who need answers **during outages, not after them**.

Full handbook:

https://sogekey.gumroad.com/l/aws-log-search-recipes

The full edition also includes a **searchable HTML handbook designed for rapid lookup during incidents**.

---

# Who This Is For

This material is designed for:

• Site Reliability Engineers (SREs)  
• DevOps engineers  
• Cloud engineers  
• platform teams  
• on-call responders

If you have ever asked:

*"I know the answer is in these logs somewhere — where do I start?"*

These patterns will help.

---

# Philosophy

Logs contain the signal.

The challenge is extracting it under pressure.

Structured log interrogation patterns help engineers:

- reduce investigation time
- avoid escalation bias
- detect failure amplification
- isolate root causes faster

---

# About This Project

This repository is part of a broader incident debugging initiative including:

• **Incident Engineering Patterns**  
• **AWS Log Search Recipes (Full Edition)**  
• **ExplainError — structured error signal classification**

Together these projects explore how engineers move from:

```
Raw logs
→ Structured investigation
→ Confident incident decisions
```

---

This folder is GitHub Pages-ready.

**Structure**:

<a href="./introduction.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">introduction.md</a> — entry page

⭐ If these examples are useful, consider **starring the repository**.
