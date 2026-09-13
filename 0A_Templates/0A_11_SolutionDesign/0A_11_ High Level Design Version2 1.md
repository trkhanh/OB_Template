---
created: 2026-09-13T05:32:00
tags:
  - SolutionDesign
---
# Feature {}

## Mental Model

## System Boundary

## Runtime Flow

## Responsibility Map

## Important Invariants

## Failure Modes

## Gotchas

## Why It Is Designed This Way

## Architecture Decisions

## Open Questions

## Evidence

---

The **Evidence** section is particularly important if AI is generating the document.

You don't want:
> "The BFF owns authorization."

You want:
> **Claim:** BFF owns authorization orchestration.  
> **Evidence:** `AgreementService.java`, `authorize()`  
> **Confidence:** High.

That gives you a much stronger bridge between:
**LLM exploration → engineering knowledge → Obsidian → future reason**