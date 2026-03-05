# AWS Log Search Recipes – Preview

Structured log interrogation patterns for real production incidents.

This repository contains selected public examples from a broader internal incident investigation corpus.

These patterns demonstrate how disciplined incident engineers extract signal under pressure.

---

## Why This Exists

When incidents occur, logs are abundant.

Clarity is not.

Most teams:
- Search reactively
- Chase keywords
- Escalate prematurely
- Miss subtle failure amplification

These recipes document structured approaches to:

+ Identify failure shape
+ Extract meaningful signals
+ Reduce escalation bias
+ Separate noise from systemic impact

This is not about CloudWatch syntax.

It is about structured investigation discipline.

---

## What This Preview Includes

+ Two practical log search examples
+ Corresponding Markdown versions
+ Static HTML export for GitHub Pages hosting

This preview represents a small subset of a larger internal pattern library used during structured calibration exercises.

---

## Ecosystem Context

This repository forms part of a layered incident intelligence initiative:

• **Incident Engineering Patterns**  
  Conceptual frameworks for analysing production failure structure.

• **AWS Log Search Recipes – Full Edition (private)**  
  Extended pattern corpus used during pilot calibration exercises.

• **ExplainError**  
  A standalone structured judgement service that ingests error signals and emits classification, confidence, evidence, and advisory action bias outputs.

Raw Logs  
→ Structured Investigation Patterns  
→ Formalised Judgement Signals  

This repository documents the middle layer.

---

## Hosting

This folder is GitHub Pages-ready.

Structure:

- `index.html` — entry page
- `*.html` — handbook pages
- `aws-log-search-recipes.css` — shared stylesheet
- `md/` — Markdown versions of the same pages

To publish:

1. Create a new GitHub repo.
2. Upload contents to repo root.
3. Go to **Settings → Pages**
4. Select `Deploy from a branch`
5. Choose `main` branch and `/ (root)` folder

---

## Design Principle

Raw signals are abundant.

Judgement is scarce.

Human decision authority remains central.

Structured confidence and evidence modelling accelerate clarity without replacing accountability.