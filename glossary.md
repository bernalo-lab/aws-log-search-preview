# Glossary

Key terms used throughout the handbook to describe failure patterns, log signals, and incident investigation concepts. This shared vocabulary helps teams communicate clearly during debugging and post-incident analysis.

> These definitions evolve as you use and strengthen this handbook.

---

## Blast Radius

The scope of impact caused by a failure — including users, services, regions, or operations affected.

A small blast radius often points closer to the root cause.  
A wide blast radius usually indicates propagation, not origin.

---

## Cold Start

The first execution of a service, function, or container before caches, connections, or dependencies are fully initialised.

Cold starts often produce transient failures that disappear once the system stabilises.

---

## Confirmation Bias

The tendency to favour evidence that supports an existing hypothesis while ignoring evidence that contradicts it.

In incident response, confirmation bias commonly appears after the first “reasonable” explanation is found.

---

## Correlation ID / Request ID

A unique identifier used to trace a single request or transaction across multiple services.

Field names vary widely (`requestId`, `traceId`, `correlationId`), but the purpose is the same end‑to‑end visibility.

---

## Drift (Configuration Drift)

A gradual divergence between intended configuration and actual runtime state.

Drift often explains failures that appear “without any recent change”.

---

## Failure Cascade

A sequence where one failure triggers multiple downstream failures, often masking the original cause.

The first error in a cascade is usually quieter than later symptoms.

---

## Near Miss

An incident that degraded service or triggered alarms but recovered before a full outage occurred.

Near misses contain valuable signals and are often easier to analyse than full outages.

---

## Noise

Log entries that are technically correct but operationally unhelpful during an incident.

Noise increases cognitive load and hides meaningful signals.

---

## Partial Failure

A failure that affects only a subset of users, requests, or operations.

Often caused by:

- Feature flags
- Gradual rollouts
- Cached state
- Permission inconsistencies

---

## Root Cause

The underlying defect or condition that made a failure possible.

Root cause is not:

- The trigger
- The symptom
- The moment the incident was noticed

---

## Signal

Log entries or patterns that meaningfully contribute to understanding or resolving an incident.

Good signal reduces uncertainty and narrows decision‑making.

---

## Silent Failure

A failure mode where incorrect behaviour occurs without explicit errors being logged.

Silent failures are often detected through:

- Anomalous results
- Missing expected events
- User reports

---

## Symptom

The observable effect of a failure, such as errors, alerts, or degraded performance.

Symptoms are often far removed from the root cause.

---

## Throttling

Intentional request limiting applied to protect systems under load.

Throttling often appears intermittently and is commonly mistaken for random instability.

---

## Trigger

The event that activates an existing defect, such as:

- A deployment
- A traffic spike
- A failover
- A credential expiry

Triggers expose problems but are not necessarily the cause.

---

## Warm‑up

The process of preparing a service for steady‑state operation (loading caches, establishing connections, priming data).

Warm‑up failures often resemble cold start issues.

---

## Why this glossary works

- Short enough to skim
- Precise enough to reuse in conversation
- Consistent with your Recipes and Advanced Patterns
- Helpful to juniors without patronising seniors

It also gives you a **shared vocabulary**, which quietly improves:

- Incident communication
- Pattern comprehension
- Buyer confidence

---

<div style="display:flex; justify-content:flex-end; margin-top:18px;">
  <a href="./introduction.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Introduction</a> |
  <a href="./foundations.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Foundations</a> |
  <a href="./recipes.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Recipes</a> |
  <a href="./advanced-patterns.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Advanced Patterns</a> |
  <a href="./how-to-use-during-an-incident.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Operational guidance</a> |
  <a href="./changelog.md" style="min-width:260px; border:1px solid #e5e7eb; border-radius:8px; padding:12px; text-decoration:none;">Changelog</a>
</div>
