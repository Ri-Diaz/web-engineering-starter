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
├── AGENTS.md
├── LICENSE
├── PROJECT-CONTEXT.md
│
├── .specify/
│   ├── integrations/
│   ├── memory/
│   │   └── constitution.md
│   ├── scripts/
│   ├── templates/
│   └── workflows/
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
│   └── PULL_REQUEST_TEMPLATE.md
│
├── .editorconfig
├── .env.example
├── .gitattributes
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
3. Complete `docs/product/PROJECT-BRIEF.md`.
4. Complete `docs/product/PROJECT-CLASSIFICATION.md`.
5. Initialize `PROJECT-CONTEXT.md`.
6. Define requirements in `docs/product/REQUIREMENTS.md`.
7. Design the appropriate architecture in `docs/architecture/ARCHITECTURE.md`.
8. Select the technology stack.
9. Document significant decisions using ADRs in `docs/architecture/adr/`.
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

GitHub Spec Kit is integrated as the default specification-driven workflow while preserving the core engineering principles and stack-agnostic nature of the starter.

---

## Using Spec Kit

GitHub Spec Kit is included in this starter with the neutral `none` integration.

This keeps the template independent from a specific AI coding assistant.

When a new project is created from this template, select the integration that matches the development environment being used.

Examples:

```text
specify integration switch codex
specify integration switch copilot
```

The selected integration belongs to the derived project and does not change the engineering principles defined by the starter.

A typical Spec Kit workflow is:

```text
Issue / Requirement
        ↓
Specify
        ↓
Clarify (when needed)
        ↓
Plan
        ↓
Tasks
        ↓
Analyze (when useful)
        ↓
Implement
        ↓
Converge
        ↓
Pull Request
```

The amount of process should remain proportional to project risk and complexity:

- `STATIC`: usually a lightweight workflow;
- `WEBAPP`: additional planning, testing, and architectural validation;
- `SENSITIVE`: stronger clarification, analysis, traceability, security, and validation.

Spec Kit feature artifacts should complement the project's permanent documentation rather than duplicate it.

Permanent project-level decisions remain documented in:

- `.specify/memory/constitution.md`;
- `PROJECT-CONTEXT.md`;
- `docs/product/REQUIREMENTS.md`;
- `docs/architecture/ARCHITECTURE.md`;
- `docs/architecture/DATA-MODEL.md`, when applicable;
- Architecture Decision Records, when required.

---

## AI-assisted development

This starter is agent-agnostic. Its guidance and planning documents have distinct roles:

- `AGENTS.md` provides operational instructions for AI agents.
- `.specify/memory/constitution.md` defines engineering principles and governance.
- `PROJECT-CONTEXT.md` is the project's technical memory.
- Spec Kit provides the specification, planning, and feature workflow.

For significant changes, agents should follow `AGENTS.md` and consult the relevant project sources it identifies. Spec Kit feature artifacts complement permanent project documentation rather than replace it.

The template retains Spec Kit's neutral `none` integration. A derived project may select an integration for its development environment without changing this starter's agent-agnostic character.

---

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

**Web Engineering Starter v1.0.0**

The starter should evolve based on lessons learned from real projects rather than hypothetical future requirements.

