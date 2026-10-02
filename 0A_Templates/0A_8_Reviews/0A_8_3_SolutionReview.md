---
created:
  - "{{date}} {{time}}"
aliases:
  - "Solution: {{title}}"
tags:
  - Engineering/SolutionReview
---
### **Solution Review & Audit Template**  
**PR Title/Link**: [Insert PR Title or Link]  
**Author**: [Name]  
**Reviewer**: [Name/Team]  

### Method
For an architecture/code review, use a template that moves from **business intent → architecture → patterns → implementation → evidence**.
# Solution Review & Audit Template

## 1. Context & Problem
**What problem is this solution solving?**
- Business problem:
- Technical problem:
- Scope:
- Out of scope:
- Constraints:
- Non-functional requirements:
    - Performance
    - Reliability
    - Security
    - Scalability
    - Maintainability
    - Observability
### Review question

> **Is the problem clearly defined enough that the proposed architecture can be judged against it?**

---
# 2. Architecture Intent
Before looking at individual patterns, understand the intended architecture.

```text
Business requirement [BDR]
        ↓
Architectural decision [ADR]
        ↓
System boundaries [SBR]
        ↓
Responsibilities
        ↓
Interactions
        ↓
Implementation
```

Document:

|Question|Answer|
|---|---|
|What are the major components?||
|Who owns what?||
|What depends on what?||
|Where does state live?||
|Where are the boundaries?||
|What are the important contracts?||
|What can change independently?||
|What must remain invariant?||
### Key review question

> **Does the implementation actually preserve the architectural intent?**

---
# 3. Pattern Inventory
Now identify the patterns being used.

|Pattern|Where?|Why?|Problem solved?|Evidence|
|---|---|---|---|---|
|Builder|User creation|Complex construction|?|Code/tests|
|Strategy|Payment calculation|Variable behavior|?|Tests|
|Observer|Event notification|Decouple producer/consumer|?|Integration|
|Factory|Object creation|Hide creation logic|?|Tests|
|Repository|Data access|Isolate persistence|?|Integration|
|...|||||

The important part is **not merely identifying the pattern**.
For every pattern ask:
> **Why does this pattern exist here?**

Then:
> **What problem would exist if we removed it?**

That's a very powerful audit question.

---
# 4. Pattern Fit
For each pattern:
### Pattern
`Strategy`
### Intended purpose
Allow different algorithms to vary independently.
### Actual implementation
Describe what the code actually does.
### Fit
- Does the problem actually require this abstraction?
- Is the abstraction at the correct boundary?
- Is the pattern reducing coupling?
- Is it increasing complexity unnecessarily?
- Is the pattern being used because it solves a real problem or simply because the pattern is familiar?
### Counterfactual
> **What happens if we remove the pattern?**
This is one of the best architecture-review questions.

---
# 5. Interaction Between Patterns
This is where reviews become more architectural.

Don't only inspect:
```text
Pattern A
Pattern B
Pattern C
```

Inspect:
```text
Pattern A
   ↓
Pattern B
   ↓
Pattern C
```

Ask:
- Do patterns reinforce each other?
- Do they create unnecessary layers?
- Are responsibilities duplicated?
- Is information being passed through too many abstractions?
- Does one pattern undermine another?
- Are there circular dependencies?
- Does the combination create hidden state?
### Example

```text
Controller
   ↓
Facade
   ↓
Factory
   ↓
Strategy
   ↓
Repository
```

Ask:

> **Does every layer represent a meaningful architectural boundary, or are we just wrapping one function with five abstractions?**

---
# 6. State & Data Flow
This is particularly important for React/frontend systems.
Document:
```text
Source of truth
      ↓
State
      ↓
Derived state
      ↓
Side effects
      ↓
External system
```

Ask:
- Where does state originate?
- Who owns it?
- Who can mutate it?
- What is derived?
- Are we duplicating state?
- Where are synchronization boundaries?
- Can two parts of the system disagree?
- What happens when state changes?
- What happens when an operation fails?

---
# 7. Dependency & Coupling Audit
Look at dependencies rather than classes.
```text
A → B
B → C
C → D
```

Ask:
- Which dependencies are stable?
- Which dependencies are volatile?
- Can components be changed independently?
- Are abstractions placed at the correct boundaries?
- Are high-level policies dependent on low-level implementation details?
    

### Useful metric

Think in terms of:

> **What needs to change together?**

If changing one business rule requires modifications across ten unrelated modules, that's architectural coupling.

---
# 8. Failure & Edge Cases
Don't only review the happy path.

For each major operation:
```text
Success
Failure
Timeout
Retry
Duplicate request
Partial failure
Invalid input
Dependency unavailable
Concurrent request
Stale data
Recovery
```

Ask:
> **What state does the system enter after failure?**

And:
> **Can the system recover without manual intervention?**

---
# 9. Non-Functional Requirements
Patterns don't prove architecture is good.

Validate against measurable requirements.

|Requirement|Target|Evidence|Result|
|---|--:|---|---|
|API latency|< 300 ms|Performance test||
|Availability|99.9%|Architecture/design||
|Throughput|1k req/s|Load test||
|Security|OWASP controls|SAST/DAST/pentest||
|Recovery|< 5 min|DR test||
|Memory|< X GB|Profiling||

This is where your earlier question about **"how do I prove an architectural decision?"** becomes important.

You don't prove architecture with one unit test.
You build **evidence against explicit requirements**.

---
# 10. Trade-offs

Every significant architectural decision should answer:

```text
Option A
Option B
Option C

Why was A selected?
```

Document:

|Dimension|A|B|C|
|---|---|---|---|
|Complexity||||
|Performance||||
|Scalability||||
|Maintainability||||
|Operational cost||||
|Failure behavior||||
|Team expertise||||

The goal isn't to find a universally "best" architecture.

It's:

> **Was the decision reasonable given the constraints?**

---

# 11. Evidence

This is the most important part of an audit.
For every major claim:
```text
Claim
 ↓
Requirement
 ↓
Design decision
 ↓
Implementation
 ↓
Evidence
```

For example:
```text
Claim:
"System can handle 1,000 requests/sec."

        ↓

Requirement:
1,000 req/sec

        ↓

Design:
Async processing + queue

        ↓

Implementation:
Kafka + worker pool

        ↓

Evidence:
Load test @ 1,000 req/sec
```

Now you aren't saying:
> "This architecture looks scalable."

You're saying:
> "This design was intended to satisfy X, and this evidence demonstrates behavior Y under condition Z."

That's a much stronger review.

---
# 12. Final Audit Summary

I would finish the review with five sections:
```text
1. Architecture intent
2. Findings
3. Risks
4. Evidence gaps
5. Recommended actions
```

And classify findings as:

|Finding|Impact|Evidence|Recommendation|
|---|---|---|---|
|Missing cleanup|High|Code + test|Add lifecycle test|
|Unnecessary Factory|Medium|Dependency analysis|Simplify|
|Missing timeout|High|Failure analysis|Define timeout policy|
|Good boundary|—|Integration tests|Keep|

---
## References
[[The mental model for Solution Review]]
