---
tags:
  - design-paradigms
  - reliability
  - fault-tolerant
created: 2026-05-26
---

Reliability means that your software works as intended even when things go wrong.

"Working as intended" varies from project to project, but it generally translates to:
1. The application performs the function that the **user expected**
2. It can **tolerate** the user making **mistakes** or using the software in **unexpected** ways
3. Its performance is **good enough** for the required use case, under the expected load and data volume
4. The system **prevents** any **unauthorized** access and abuse

The things that can go wrong are called [[Faults]], and systems that anticipate that are called *fault-tolerant* systems. 

When designing *fault-tolerant* systems, sometimes one should **increase** the rate of faults by triggering them **deliberately**, as to end them early and avoid [[Failure|failures]].

