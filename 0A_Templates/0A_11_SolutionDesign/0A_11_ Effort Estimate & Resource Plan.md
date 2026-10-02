---
created:
  - "{{date}} {{time}}"
tags:
  - SolutionDesign
---
## 📊 Effort Estimate & Resource Plan Template

This document translates architecture decisions into **time, people, and money**. It's what stakeholders actually care about because it answers: *"How much will this cost and when will it be done?"*

---

## 📋 Document Structure

```
┌─────────────────────────────────────────────────────────────┐
│              EFFORT ESTIMATE & RESOURCE PLAN                 │
│                    [Project Name]                            │
│                    Version 1.0                               │
└─────────────────────────────────────────────────────────────┘
```

---

### Section 1: Executive Summary

| Metric | Value |
|--------|-------|
| **Total Duration** | 14 weeks (3.5 months) |
| **Total Effort** | 620 hours (approx. 4 person-months) |
| **Team Size** | 4-6 people |
| **Total Cost** | $XXX,XXX (hardware + licensing + labor) |
| **Go-Live Date** | [Date] |

**Summary Statement:**
> *This plan outlines the effort required to implement Apollo GraphQL Federation across 6 microservices. The project will require 4 engineers for 14 weeks, with a total estimated cost of $XXX,XXX. The phased approach delivers value incrementally, with the first production traffic expected in Week 6.*

---

### Section 2: Assumptions & Constraints

| Type | Item |
|------|------|
| **Assumptions** | Existing microservices are stable and documented |
| | Teams are available for 80% of their time (not 100%) |
| | Dev/Staging environments are already provisioned |
| | No major refactoring of existing services required |
| **Constraints** | Must use existing AWS account and Kubernetes cluster |
| | Cannot migrate more than 1 subgraph per sprint |
| | No new headcount approved—must use existing teams |
| | Production deployments only during business hours |

---

### Section 3: Work Breakdown Structure (WBS)

#### Phase 1: Foundation (Weeks 1-4)

| Task ID | Task Description | Effort (Hours) | Role | Dependencies |
|---------|------------------|----------------|------|--------------|
| **1.1** | Environment setup (K8s namespaces, networking) | 16 | Platform Eng | None |
| **1.2** | Apollo Router deployment (staging) | 8 | Platform Eng | 1.1 |
| **1.3** | Observability stack (Prometheus, Grafana, Jaeger) | 24 | Platform Eng | 1.2 |
| **1.4** | Authentication gateway (JWT validation) | 16 | Backend Eng | 1.2 |
| **1.5** | First subgraph migration (Users service) | 32 | Backend Eng | 1.2 |
| **1.6** | Basic schema federation | 8 | Backend Eng | 1.5 |
| **1.7** | Documentation & runbooks | 16 | All | Throughout |
| | **Phase 1 Total** | **120** | | |

**Milestone:** Router accepting queries from 1 subgraph ✅

---

#### Phase 2: Migration (Weeks 5-8)

| Task ID | Task Description | Effort (Hours) | Role | Dependencies |
|---------|------------------|----------------|------|--------------|
| **2.1** | Migrate Orders subgraph | 40 | Backend Eng | 1.5 |
| **2.2** | Migrate Products subgraph | 32 | Backend Eng | 1.5 |
| **2.3** | Cross-subgraph entity resolution | 24 | Backend Eng | 2.1, 2.2 |
| **2.4** | Performance baseline testing | 16 | QA Eng | 2.3 |
| **2.5** | Caching strategy implementation | 24 | Backend Eng | 2.3 |
| **2.6** | Error handling & timeouts | 16 | Backend Eng | 2.3 |
| **2.7** | Security review | 8 | Security | 2.3 |
| | **Phase 2 Total** | **160** | | |

**Milestone:** 3 subgraphs federated; cross-subgraph queries work ✅

---

#### Phase 3: Scale (Weeks 9-12)

| Task ID | Task Description | Effort (Hours) | Role | Dependencies |
|---------|------------------|----------------|------|--------------|
| **3.1** | Migrate Payments subgraph | 32 | Backend Eng | 2.3 |
| **3.2** | Migrate Inventory subgraph | 24 | Backend Eng | 2.3 |
| **3.3** | Migrate Analytics subgraph | 40 | Backend Eng | 2.3 |
| **3.4** | Load testing & optimization | 32 | QA Eng | 3.1-3.3 |
| **3.5** | Rate limiting & quota management | 16 | Backend Eng | 3.4 |
| **3.6** | Production readiness review | 8 | All | 3.4 |
| | **Phase 3 Total** | **152** | | |

**Milestone:** All 6 subgraphs federated; performance within targets ✅

---

#### Phase 4: Governance & Handoff (Weeks 13-14)

| Task ID | Task Description | Effort (Hours) | Role | Dependencies |
|---------|------------------|----------------|------|--------------|
| **4.1** | Schema registry setup | 16 | Platform Eng | 3.6 |
| **4.2** | CI/CD integration | 24 | Platform Eng | 4.1 |
| **4.3** | Team training (2 sessions) | 16 | All | None |
| **4.4** | Runbooks & troubleshooting guides | 16 | Backend Eng | 3.6 |
| **4.5** | Handoff to operations team | 8 | All | 4.1-4.4 |
| | **Phase 4 Total** | **80** | | |

**Milestone:** Teams self-serve; operational handoff complete ✅

---

### Section 4: Summary by Role

| Role | Phase 1 | Phase 2 | Phase 3 | Phase 4 | **Total Hours** |
|------|---------|---------|---------|---------|-----------------|
| **Platform Engineer** | 48 | 24 | 24 | 40 | **136** |
| **Backend Engineer (2)** | 64 | 128 | 128 | 32 | **352** (176 each) |
| **QA Engineer** | 0 | 16 | 32 | 0 | **48** |
| **Security** | 0 | 8 | 0 | 0 | **8** |
| **Solution Architect** | 8 | 8 | 8 | 8 | **32** |
| **Tech Lead** | 0 | 0 | 0 | 0 | **Included in Backend** |
| **Total** | **120** | **184** | **192** | **80** | **576** |

> *Note: Tech Lead effort is included within Backend Engineer allocation (20% leadership, 80% implementation)*

---

### Section 5: Timeline & Milestones

```
Week:     1    2    3    4    5    6    7    8    9   10   11   12   13   14
          │    │    │    │    │    │    │    │    │    │    │    │    │    │
Phase 1   ████████████████████████████
(Foundation)

Phase 2             ████████████████████████████████
(Migration)

Phase 3                         ████████████████████████████████
(Scale)

Phase 4                                                 ████████████████
(Governance)

          │    │    │    │    │    │    │    │    │    │    │    │    │    │
Milestones:
          M1: Router + 1 subgraph
                    M2: 3 subgraphs
                                       M3: 6 subgraphs
                                                            M4: Handoff
```

| Milestone | Week | Success Criteria |
|-----------|------|------------------|
| **M1: Foundation Complete** | 4 | Router accepts queries; 1 subgraph online; metrics visible |
| **M2: Migration Complete** | 8 | 3 subgraphs federated; cross-subgraph queries work |
| **M3: Scale Complete** | 12 | All 6 subgraphs; P99 < 100ms; load test passes |
| **M4: Handoff Complete** | 14 | Teams trained; docs complete; operations transitioned |

---

### Section 6: Cost Breakdown

#### 6.1 Labor Cost

| Role | Rate (USD/hour) | Hours | Total |
|------|-----------------|-------|-------|
| Platform Engineer | $100 | 136 | $13,600 |
| Backend Engineer (2) | $90 | 352 | $31,680 |
| QA Engineer | $80 | 48 | $3,840 |
| Security | $120 | 8 | $960 |
| Solution Architect | $130 | 32 | $4,160 |
| **Total Labor** | | **576** | **$54,240** |

#### 6.2 Infrastructure Cost (Monthly)

| Resource | Dev/Staging | Production | Monthly Total |
|----------|-------------|------------|---------------|
| Kubernetes nodes | 2 × t3.large ($150) | 6 × c5.2xlarge ($1,200) | $1,350 |
| Apollo Router | 2 × t3.medium ($50) | 6 × c5.xlarge ($600) | $650 |
| Load balancers | 1 × $20 | 2 × $20 | $60 |
| Monitoring (Prometheus/Grafana) | $100 | $200 | $300 |
| Logging (CloudWatch) | $50 | $200 | $250 |
| Redis Cache | 1 × cache.t2.micro ($15) | 3 × cache.m5.large ($450) | $465 |
| **Total Monthly** | **$385** | **$2,670** | **$3,055** |

**Total Infrastructure (14 weeks ≈ 3.5 months):** ~$10,700

#### 6.3 Licensing Cost

| Item | Cost | Notes |
|------|------|-------|
| Apollo GraphOS Enterprise | $40,000/year | Annual commitment; includes Studio, metrics, schema registry |
| **Pro-rated (3.5 months)** | **$11,667** | Assuming annual paid upfront |

#### 6.4 Total Project Cost

| Category | Amount |
|----------|--------|
| Labor (576 hours) | $54,240 |
| Infrastructure (3.5 months) | $10,700 |
| Licensing (pro-rated) | $11,667 |
| Contingency (15%) | $11,490 |
| **Total Estimated Cost** | **$88,097** |

---

### Section 7: Resource Allocation by Week

| Role | Week 1-2 | Week 3-4 | Week 5-6 | Week 7-8 | Week 9-10 | Week 11-12 | Week 13-14 |
|------|---------|---------|---------|---------|----------|----------|----------|
| **Platform** | 100% | 50% | 50% | 25% | 25% | 25% | 50% |
| **Backend 1** | 50% | 100% | 100% | 100% | 100% | 100% | 50% |
| **Backend 2** | 0% | 50% | 100% | 100% | 100% | 100% | 50% |
| **QA** | 0% | 0% | 25% | 25% | 50% | 50% | 0% |
| **Security** | 0% | 0% | 0% | 25% | 0% | 0% | 0% |
| **Architect** | 25% | 25% | 25% | 25% | 25% | 25% | 25% |

> *Note: Percentages indicate % of time allocated (e.g., 100% = full-time on project)*

---

### Section 8: Dependencies & Critical Path

```
Critical Path (14 weeks):

1.1 Environment Setup (1 week)
  ↓
1.2 Apollo Router Deployment (1 week)
  ↓
1.5 First Subgraph Migration (2 weeks)
  ↓
2.1-2.3 Remaining Subgraphs (3 weeks)
  ↓
3.1-3.3 Final Subgraphs (3 weeks)
  ↓
3.4 Load Testing (1 week)
  ↓
4.1-4.5 Governance & Handoff (2 weeks)
```

| Dependency | Owner | Risk if Delayed |
|------------|-------|-----------------|
| AWS account access | Platform | +1 week to Phase 1 |
| Subgraph team availability | Product | +2 weeks per subgraph |
| Security approval | Security | +1 week before production |
| Apollo contract execution | Finance | Cannot use commercial features |

---

### Section 9: Risk-Adjusted Estimate

| Risk | Probability | Impact | Contingency Added |
|------|-------------|--------|-------------------|
| Subgraph complexity higher than expected | Medium | +40 hours | 40 hours |
| Team availability drops | Medium | +80 hours | 80 hours |
| Apollo Router performance issues | Low | +40 hours | 20 hours |
| Security review requires changes | Medium | +24 hours | 24 hours |
| **Total Contingency** | | | **164 hours** |

**Confidence Levels:**
- P50 (50% confidence): 576 hours (as estimated)
- P80 (80% confidence): 740 hours (with contingency)
- P95 (95% confidence): 860 hours (with full contingency + buffer)

**Recommended Budget:** Use **P80** estimate for stakeholder commitments

---

### Section 10: Comparison: Internal vs. Outsourced

| Option | Duration | Cost | Pros | Cons |
|--------|----------|------|------|------|
| **Internal Team** | 14 weeks | $88k | Knowledge stays internal; team alignment | Slower; competes with other priorities |
| **External Consultants** | 8 weeks | $150k | Faster; expertise; can start immediately | Knowledge transfer risk; higher cost |
| **Hybrid (Internal + 1 Consultant)** | 10 weeks | $110k | Accelerated; knowledge transfer built-in | Coordination overhead |

**Recommended:** Hybrid approach for first GraphQL implementation

---

### Section 11: Approval & Sign-off

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Solution Architect | | | |
| Engineering Manager | | | |
| Product Owner | | | |
| Finance | | | |

---

## 📝 Quick Reference: Estimate Checklist

Before finalizing your estimate:

| ✓ | Item |
|---|------|
| ☐ | Work breakdown structure covers all phases |
| ☐ | Effort hours estimated by task (not just "guess") |
| ☐ | Role allocation clearly defined |
| ☐ | Timeline shows critical path |
| ☐ | Cost breakdown includes labor, infrastructure, licensing |
| ☐ | Contingency added for uncertainty |
| ☐ | Confidence levels communicated (P50/P80) |
| ☐ | Dependencies identified with owners |
| ☐ | Assumptions documented |
| ☐ | Reviewed by at least one peer and one manager |

---

## 💡 Pro Tips for Estimation

| Tip | Why |
|-----|-----|
| **Add 50% to initial estimates** | Engineers are optimistic. Reality is harder. |
| **Include non-coding time** | Meetings, documentation, code review = 30-40% of time |
| **Estimate in hours, present in weeks** | Hours for accuracy; weeks for stakeholder clarity |
| **Never estimate alone** | Get the person doing the work to estimate |
| **Update estimates weekly** | Actual vs. planned. Adjust as you learn. |
| **Document assumptions clearly** | "We assumed no major refactoring" protects you later |

---

Would you like me to create a specific estimate for your Apollo project, or show you how to combine the HLD and Estimate into a complete proposal package?