---
tags:
  - design-paradigm
  - concept
created: 2026-04-28
---

**Attribute Based Access Control** (ABAC) is not based around "Who can do this" but "Due the current conditions satisfy the policy set here".

The conditions can be **anything**: User, Type of User, Document Type, Dashboard Type, etc.

The policy is the set of minimum requirements needed to access a specific page.

**You express the rules once, the engine does the rest.**

## The Basics

An **attribute** is any piece of structured information that can be attached to an entity and then evaluated.

In ABAC, there are **four** entity types, each with their own **attributes**.

### The Subject

The subject is the entity that **requests** access. This is, in most cases, a user, but can be a service, a script, a device, etc.

Subject attributes describe **who** or **what** is making the request:
- identity
- organization
- role
- organization role
- location
- department
- security clearance level

**Anything** you know about the requester can be an **attribute**.

### The Resource

The resource is the entity being requested:
- a database row
- a file
- an API endpoint
- an UI element

Resource attributes describe it's properties: owner, classification, creation date, type of contents, etc. These attributes allow you to define rules that vary on **what** and **who** can access them.

### The Action

