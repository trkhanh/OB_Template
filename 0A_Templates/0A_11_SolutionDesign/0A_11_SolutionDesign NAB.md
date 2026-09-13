---
created:
  - "{{date}} {{time}}"
tags:
  - SolutionDesign
---
## Document Purpose
This document provides an overview of the design intended to fill the void between the [[High Level Solution Impact Document (HLSI)]] which show architecturally significant aspects for the solution and individual [[Detailed Design Specification (DDS)]]) which provide granular on the design of each of the individual components that makeup the complete solution 

## Scope
- In scope
	- item 1:..
	- item 2: ..
- Out of scope
- Pending item: 
	- item 1:
	- item 2:
##  Architecture Overview
The `Form` component is a sophisticated form management solution built on top of [Formik](https://github.com/jaredpalmer/formik) that provides:
## System components

| Component | Description | Delivery Team |
| --------- | ----------- | ------------- |
|           |             |               |
## Design Elaboration
## UX
## APIs
| Name | End points | URL |
| ---- | ---------- | --- |
|      |            |     |
## Capability Check
## Feature flag
## UI/APIs attribute mapping
## Bio Catch requirements
### Audit Events
## Error Mapping
#### API 1

| HTTP Response Code | Error Reason            | Screen Mapping | Retry option |
| ------------------ | ----------------------- | -------------- | ------------ |
| 400                | Invalid request         |                | N            |
| 401                | Unauthorized            |                | N            |
| 403                | Forbidden               |                | N            |
| 404                | Resources not available |                | N            |
| 429                | Too many requests       |                | N            |
| 500                | Internal Server Error   |                | N            |
| 503                | Service Unavailable     |                | N            |
| 504                | Service Timeout         |                | N            |
## NFR requirements
| Item                             | Description                                                     | Note |
| -------------------------------- | --------------------------------------------------------------- | ---- |
| Source Consumer System           | NABC Shell                                                      |      |
| Target Provider System           | FX Deal MS                                                      |      |
| Operation window                 | 24x7                                                            |      |
| Avaiablility                     | 99.95                                                           |      |
| Authentications & Authorisastion | AWS server Encryption with key managed by KMS                   |      |
| Criticalality                    | CAT D [[Solution design pattern]]                               |      |
| Response time                    | Page load <= 3 secs, Avg response time: Single API call : 500ms |      |
| Constraints                      |                                                                 |      |
| Policy & Regulation              | Standard                                                        |      |
| Data Classification              | Confidential                                                    |      |
| Securiry                         | KMS, SSM, HIP proxy                                             |      |
| Channel Encryption               | YES                                                             |      |
| Message/Date Encryption          | TLS                                                             |      |
| Disaster Recovery                | RTO less that 24hrs, RPO 48hrs, MAO 3-5 days                    |      |
| Message Format (Content Type)    | Miniapp->BFF: GrapQL, BFF-> BE: JSON                            |      |
| Kong Endpoint(s)                 | Client Kong, Services Kong                                      |      |
| Event and Logging                | Splunk log, NABX framework log                                  |      |
|                                  |                                                                 |      |
## Appendix 
## Decisions
## References
| Reference | Description | Link |
| --------- | ----------- | ---- |
|           |             |      |
## Stake holder
| Stakeholder name | Stackholder role | Reponsibility |
| ---------------- | ---------------- | ------------- |
|                  |                  |               |