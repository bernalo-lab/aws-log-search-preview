# Ecosystem Overview

This repository forms part of a structured incident intelligence initiative focused on decision acceleration in regulated environments.

The ecosystem is intentionally layered.

---

## Layer 1 – Raw Signals

Production systems emit:
+ Logs
+ Exceptions
+ Error traces
+ Telemetry events

These signals are often noisy and ambiguous under pressure.

---

## Layer 2 – Structured Investigation Patterns

Documented in:

• Incident Engineering Patterns  
• AWS Log Search Recipes – Preview  

These repositories demonstrate how disciplined incident engineers:

+ Extract meaningful signals  
+ Identify temporal failure shape  
+ Avoid escalation bias  
+ Reduce misclassification  

This layer represents structured human judgement.

---

## Layer 3 – Formalised Judgement Signals

Implemented in:

• ExplainError  

ExplainError is a standalone structured judgement service that:

+ Ingests error signals
+ Emits classification
+ Emits severity
+ Emits explicit confidence
+ Emits evidence markers
+ Emits advisory action bias

It externalises uncertainty into auditable outputs.

---

## Pilot & Evaluation

Structured Incident Calibration Pilots evaluate:

+ Alignment between confidence signals and actual severity outcomes
+ Severity agreement rates
+ High-confidence misalignment scenarios
+ Low-confidence critical misses

This ensures judgement signals are meaningful, not cosmetic.

---

## Design Principle

Human judgement remains authoritative.

Structured signals accelerate clarity.

Automation is optional.  
Transparency is not.

---

For evaluation discussions or pilot participation, refer to the ExplainError repository.
