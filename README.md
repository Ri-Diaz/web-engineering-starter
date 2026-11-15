# Web Engineering Starter

A reusable, stack-agnostic engineering foundation for planning and developing web projects with consistent criteria for product definition, software architecture, security, testing, maintainability, and specification-driven development.

The goal is not to impose enterprise-level complexity on every project. The documentation and engineering practices used should always be proportional to the project's actual complexity and risk.

---

## Purpose

Web Engineering Starter provides a common starting point for new web projects.

It helps define:

- what problem is being solved;
- who the users are;
- what the system must do;
- what architecture is appropriate;
- how data should be modeled;
- what security controls are required;
- how the system should be tested;
- why important technical decisions were made.

The starter is intentionally **technology-agnostic**.

It does not assume Astro, React, Next.js, Django, Laravel, Node.js, or any other framework.

Technology should be selected after understanding the project requirements.

---

## Core principle

> Use the simplest architecture that correctly solves the current problem while preserving reasonable paths for future evolution.

Avoid complexity introduced only because it might be useful someday.

---

## Project profiles

Projects are classified into three general profiles.

### STATIC

Suitable for primarily public or informational websites.

Examples:

- portfolios;
- landing pages;
- corporate websites;
- artist or band websites;
- documentation;
- simple catalogs.

Typical characteristics:

- little business logic;
- no authentication;
- little or no persistence;
- low operational risk.

---

### WEBAPP

Suitable for applications with users, persistence, or relevant business logic.

Examples:

- booking systems;
- e-commerce;
- dashboards;
- inventory systems;
- management applications;
- SaaS applications.

Typical characteristics:

- authentication;
- database;
- business rules;
- roles and permissions;
- APIs or external integrations.

---

### SENSITIVE

Suitable for systems processing sensitive, regulated, or operationally critical information.

Examples:

- healthcare systems;
- financial systems;
- institutional systems;
- human resources;
- regulated environments.

Typical characteristics:

- sensitive data;
- stronger access control;
- audit requirements;
- privacy requirements;
- increased traceability;
- stronger security controls.

---

## Recommended workflow

```text
IDEA
 │
 ▼
PROJECT BRIEF
 │
 ▼
PROJECT CLASSIFICATION
 │
 ▼
PROJECT CONTEXT
 │
 ▼
REQUIREMENTS
 │
 ▼
ARCHITECTURE
 │
 ├── DATA MODEL
 │
 └── ADR when required
 │
 ▼
IMPLEMENTATION
 │
 ▼
TESTING
 │
 ▼
DEPLOYMENT
 │
 ▼
MAINTENANCE
```

The process is iterative.

Documentation should evolve when the project changes, but trivial implementation changes should not generate unnecessary documentation work.

---

## Repository structure

```text
web-engineering-starter/
│
├── README.md
├── .specify/
│   └── memory/
│       └── constitution.md
├── PROJECT-CONTEXT.md
│
├── docs/
│   ├── 00-INDEX.md
│   │
│   ├── product/
│   │   ├── PROJECT-BRIEF.md
│   │   ├── PROJECT-CLASSIFICATION.md
│   │   └── REQUIREMENTS.md
│   │
│   ├── architecture/
│   │   ├── ARCHITECTURE.md
│   │   ├── DATA-MODEL.md
│   │   └── adr/
│   │       └── ADR-TEMPLATE.md
│   │
│   ├── security/
│   │   └── SECURITY.md
│   │
│   └── engineering/
│       └── TEST-STRATEGY.md
│
├── .github/
│   ├── ISSUE_TEMPLATE/
│   ├── workflows/
│   └── PULL_REQUEST_TEMPLATE.md
│
├── .editorconfig
├── .env.example
└── .gitignore
```

---

## Documentation

### Engineering Constitution

`.specify/memory/constitution.md`

Defines the engineering principles that govern projects created from this starter.

It should change infrequently.

---

### Project Brief

`docs/product/PROJECT-BRIEF.md`

Defines:

- problem;
- users;
- objectives;
- scope;
- MVP;
- constraints;
- initial risks.

Complete this before making major technical decisions.

---

### Project Classification

`docs/product/PROJECT-CLASSIFICATION.md`

Determines whether the project should be treated as:

- `STATIC`;
- `WEBAPP`;
- `SENSITIVE`.

This classification determines the level of engineering rigor required.

---

### Project Context

`PROJECT-CONTEXT.md`

Acts as the project's technical memory.

It summarizes:

- current status;
- stack;
- architecture;
- modules;
- restrictions;
- important decisions;
- current work.

This is a living document.

---

### Requirements

`docs/product/REQUIREMENTS.md`

Defines:

- functional requirements;
- non-functional requirements;
- business rules;
- constraints;
- acceptance criteria.

---

### Architecture

`docs/architecture/ARCHITECTURE.md`

Describes:

- system structure;
- responsibilities;
- modules;
- dependencies;
- integrations;
- persistence;
- infrastructure.

Architecture must remain proportional to the problem.

---

### Data Model

`docs/architecture/DATA-MODEL.md`

Used when the project has relevant persistence.

Defines:

- entities;
- relationships;
- invariants;
- integrity rules;
- migrations;
- data sensitivity.

This document is usually unnecessary for simple static sites.

---

### Architecture Decision Records

`docs/architecture/adr/`

ADRs document significant technical decisions.

Examples:

```text
ADR-0001 — Use Astro
ADR-0002 — PostgreSQL as primary database
ADR-0003 — Authentication strategy
```

Not every technical decision requires an ADR.

---

### Security

`docs/security/SECURITY.md`

Defines the project's security baseline.

The required depth depends on the project profile.

```text
STATIC
→ baseline web security

WEBAPP
→ application security

SENSITIVE
→ reinforced controls
```

---

### Test Strategy

`docs/engineering/TEST-STRATEGY.md`

Defines how the system will be validated.

Testing depth should be based on risk rather than arbitrary coverage targets.

---

## Documentation requirements by profile

| Document | STATIC | WEBAPP | SENSITIVE |
|---|:---:|:---:|:---:|
| Constitution | ✓ | ✓ | ✓ |
| Project Brief | ✓ | ✓ | ✓ |
| Classification | ✓ | ✓ | ✓ |
| Project Context | ✓ | ✓ | ✓ |
| Requirements | Lightweight | ✓ | ✓ |
| Architecture | Lightweight | ✓ | ✓ |
| Data Model | Optional | ✓ | ✓ |
| ADR | As needed | As needed | As needed |
| Security | Baseline | ✓ | Reinforced |
| Test Strategy | Lightweight | ✓ | Reinforced |

---

## What this starter does not do

This repository does not prescribe:

- a frontend framework;
- a backend framework;
- a database;
- a hosting provider;
- a cloud platform;
- a CSS framework;
- a testing framework;
- a specific architecture for every project.

Those decisions should emerge from the requirements and constraints of each project.

---

## Creating a new project

This repository is configured as a GitHub Template Repository.

To start a new project:

1. Select **Use this template**.
2. Create a new repository.
3. Complete `PROJECT-BRIEF.md`.
4. Complete `PROJECT-CLASSIFICATION.md`.
5. Initialize `PROJECT-CONTEXT.md`.
6. Define requirements.
7. Design the appropriate architecture.
8. Select the technology stack.
9. Document significant decisions using ADRs.
10. Begin implementation.

---

## Specification-driven development

The starter is designed to support specification-driven workflows.

A typical feature can evolve through:

```text
Requirement
     ↓
Specification
     ↓
Plan
     ↓
Tasks
     ↓
Implementation
     ↓
Tests
```

GitHub Spec Kit or another specification workflow may be added without changing the core engineering principles of the starter.

---

## AI-assisted development

AI tools should not independently redefine the architecture of a project.

Before making significant changes, an AI assistant should review:

```text
.specify/memory/constitution.md
PROJECT-CONTEXT.md
relevant requirements
ARCHITECTURE.md
relevant ADRs
```

Existing architectural decisions should be respected unless there is a documented reason to reconsider them.

---

## Engineering philosophy

This starter intentionally avoids two extremes:

```text
No structure
     ↓
technical chaos
```

and:

```text
Excessive process
     ↓
documentation bureaucracy
```

The objective is a practical middle ground:

```text
Enough structure
      +
Explicit decisions
      +
Automated quality controls
      +
Proportional architecture
```

---

## Version

**Web Engineering Starter v1.0**

The starter should evolve based on lessons learned from real projects rather than hypothetical future requirements.

