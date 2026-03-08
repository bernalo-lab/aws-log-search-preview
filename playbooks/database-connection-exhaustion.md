# Database Connection Exhaustion

This playbook provides a structured approach for diagnosing incidents caused by
**database connection exhaustion** in production systems.

Connection exhaustion is one of the most common causes of application outages
in systems that rely on relational databases.

---

# Typical Symptoms

Engineers may observe:

• sudden API latency spikes  
• increased request timeouts  
• database connection errors in application logs  
• services becoming unresponsive  

Monitoring dashboards may show:

• database connection count at maximum
• increased application error rates
• thread pools waiting for database access

---

# Common Error Messages

Logs frequently contain messages similar to:

too many connections  
connection pool exhausted  
timeout acquiring connection  
unable to obtain database connection  

These messages indicate that the application cannot obtain a free database connection.

---

# Common Causes

Typical root causes include:

• connection leaks in application code  
• long‑running queries holding connections  
• traffic spikes exceeding pool limits  
• improperly configured connection pools  
• database performance degradation  

---

# Initial Triage

Start by determining the **scope of the incident**.

Key questions:

1. Are all services affected or only specific endpoints?
2. Did the issue start after a deployment?
3. Has traffic increased significantly?
4. Is the database itself under heavy load?

Understanding scope helps determine the fastest mitigation strategy.

---

# Investigation Workflow

Follow a structured investigation process.

## Step 1 — Check application logs

Look for repeated messages such as:

• connection pool exhausted  
• unable to obtain connection  
• request timeout waiting for database  

These signals confirm pool exhaustion.

---

## Step 2 — Review database connection count

Check the current number of active database connections.

Compare:

• active connections
• maximum allowed connections

If the limit is reached, new requests will fail until connections are released.

---

## Step 3 — Identify long-running queries

Long-running queries often hold connections longer than expected.

Investigate:

• slow query logs  
• locking queries  
• table scans  
• missing indexes  

---

## Step 4 — Check for connection leaks

A connection leak occurs when application code fails to release connections.

Signs include:

• steadily increasing connection counts
• connections remaining open indefinitely
• transactions never completing

---

# Immediate Mitigation Options

Short-term mitigation strategies may include:

• restarting affected application pods  
• temporarily increasing connection pool limits  
• terminating long-running queries  
• scaling application instances to distribute load  

These steps can restore service while root cause investigation continues.

---

# Prevention Strategies

To reduce future incidents:

• ensure database connections are always closed properly  
• implement connection pool monitoring  
• add slow query alerts  
• optimise database queries and indexing  
• load test connection pool behaviour  

---

# Key Lesson

Database connection exhaustion rarely happens suddenly.

It is usually caused by:

• gradual connection leaks
• inefficient queries
• increasing traffic without scaling

Proactive monitoring and proper connection management prevent most incidents.
