# Agent Instructions

This file provides operational guidance for AI coding agents working in projects derived from Web Engineering Starter. It complements the project's permanent documentation; it does not replace the Engineering Constitution or the project context.

## Read before significant changes

Review the relevant sources in this order:

1. `.specify/memory/constitution.md`
2. `PROJECT-CONTEXT.md`
3. approved requirements in `docs/product/REQUIREMENTS.md`
4. the relevant feature specification under `specs/`, when one exists
5. `docs/architecture/ARCHITECTURE.md`
6. relevant Architecture Decision Records
7. the existing implementation and tests

Use these sources to understand the task and its constraints. Follow the project's documented source-of-truth rules when sources conflict; do not assume the current code is correct when it conflicts with an approved requirement, specification, ADR, or architectural decision.

## Scope and architecture

Keep changes within the requested scope, check whether equivalent behavior already exists, and extend established patterns where appropriate. Preserve the existing architecture and module boundaries. Introduce architectural changes only to meet a concrete need, and document significant decisions in an ADR when appropriate.

## Dependencies

Before adding a dependency, identify the problem it solves, check existing alternatives, assess maintenance, security, complexity, and runtime impact, and explain why it is preferable to a simpler option.

## Specification-driven work

Use Spec Kit for relevant features and significant changes. Keep requirements, feature specifications, plans, tasks, architecture, ADRs, tests, and implementation consistent; feature artifacts should complement permanent project documentation. Small, low-risk changes do not need unnecessary process.

## Validation

When behavior changes, update or add appropriate tests. Match testing and validation to risk, prioritize critical business rules and flows, and do not remove or weaken tests to make a change pass. Run relevant available validation before considering the work complete.

## Security and data

Do not add secrets, credentials, tokens, private keys, or production data to the repository. Follow the project's security and data-classification requirements. For `SENSITIVE` projects, account for privacy, authorization, auditability, data integrity, logging, backup, and recovery; avoid exposing personal or sensitive data in logs and generated artifacts.

## Documentation and technical debt

Update permanent documentation when the project materially changes, including `PROJECT-CONTEXT.md` when its architecture, stack, modules, integrations, security constraints, scope, business rules, or significant technical debt change. Make temporary compromises explicit. Track relevant technical debt as an issue instead of leaving it only in a permanent `TODO` comment.

## Completion

Before considering a task complete, confirm that the requested behavior and acceptance criteria are met, relevant tests and validation pass, no unrelated changes were introduced, architecture and security constraints are respected, needed documentation is updated, temporary debugging code is removed, and new technical debt is documented. Surface material ambiguity instead of inventing a lasting product or architectural decision.
