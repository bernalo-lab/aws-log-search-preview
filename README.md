# AWS Log Search Recipes — Preview

Production incidents rarely start with dashboards.

They start with engineers asking:

**“What is actually failing?”**

This repository contains a small preview of the **log interrogation patterns engineers use during real production incidents in AWS CloudWatch**.

These examples demonstrate how structured log searches can quickly surface signal during incident triage.

---

# What This Preview Includes

This preview repository contains:

• 5 CloudWatch Logs Insights query recipes  
• 3 incident investigation patterns  

These examples show how experienced engineers:

- confirm error spikes
- identify failing services
- detect dependency failures
- uncover retry storms
- trace failing requests

All patterns are designed for **real production debugging**, not lab demonstrations.

---

# Example Query

```sql
fields @timestamp, service, @message
| filter @message like /exception/
| stats count() by service
| sort count desc
```

**Purpose**:

Identify which service is generating the majority of failures during an incident.

Instead of manually scanning logs, this query surfaces the **dominant failure source immediately**.

---

# Full Handbook

This repository is a preview of the **AWS Log Search Recipes Handbook**.

The full collection includes:

• 40+ production-ready CloudWatch Logs Insights queries  
• structured incident debugging playbooks  
• advanced investigation patterns  
• searchable HTML reference  
• downloadable PDF handbook  

Designed for engineers who need answers **during outages, not after them**.

Full handbook:

https://sogekey.gumroad.com/l/aws-log-search-recipes

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

⭐ If these examples are useful, consider **starring the repository**.
