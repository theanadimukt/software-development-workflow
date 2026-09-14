# Agent-Assisted SDLC Reference

## Purpose

This is a practical reference for selecting skills across the software-development lifecycle (SDLC), with Addy Osmani's collection as the primary engineering framework and a small set of complementary Matt Pocock skills.

Use it when starting a feature, deciding which skills to install, or routing an agent task. It is a recommendation for a Laravel + React SaaS stack, with extension points for native macOS applications and Chrome extensions.

## Operating Principle

Do not begin implementation until the domain and constraints are clear. Prefer one primary skill per concern: overlapping skills can create inconsistent routing and advice.

The default delivery loop is:

```text
small slice → implement → test → verify → commit → next slice
```

## Recommended Stack

### Primary framework: Addy Osmani

Use this collection as the default for the broad engineering lifecycle:

| Concern | Recommended skill | Use it for |
| --- | --- | --- |
| Context | `context-engineering` | Establishing project context before work begins |
| Shaping an idea | `idea-refine` (optional) | Turning an early idea into a sharper proposal |
| Specification | `spec-driven-development` | Objectives, boundaries, conventions, commands, and test expectations |
| Constraints | `constraint-driven-development` | Recording the quality bar and non-negotiable constraints |
| Planning | `planning-and-task-breakdown` | Small, verifiable tasks with dependencies and acceptance criteria |
| Implementation | `incremental-implementation` | Building and validating one vertical slice at a time |
| APIs and contracts | `api-and-interface-design` | Stable contracts, validation, compatibility, and error semantics |
| Frontend | `frontend-ui-engineering` | Components, state, accessibility, responsive design, and design systems |
| Testing | `test-driven-development` | Red-Green-Refactor across backend, frontend, and browser tests |
| Browser diagnosis | `browser-testing-with-devtools` | DOM, network, console, runtime, and performance investigation |
| Debugging | `debugging-and-error-recovery` | Reproduce, localize, reduce, fix, and guard against regressions |
| Code review | `code-review-and-quality` | Review before merge |
| Security | `security-and-hardening` | Authentication, secrets, dependencies, trust boundaries, and OWASP-style risks |
| Performance | `performance-optimization` | Measured improvements to rendering, bundles, API latency, and queries |
| Git | `git-workflow-and-versioning` | Atomic commits and safe, trunk-oriented workflow |
| CI/CD | `ci-cd-and-automation` | Quality gates, deployments, feature flags, and feedback loops |
| Observability | `observability-and-instrumentation` | Logs, metrics, tracing, alerting, and production monitoring |
| Documentation | `documentation-and-adrs` | Decisions, architecture context, and durable project knowledge |
| Release | `shipping-and-launch` | Validation, staged rollout, rollback, and release monitoring |

### Complementary Matt Pocock skills

Cherry-pick only the skills that fill a distinct gap in the primary framework:

| Skill | Why it belongs |
| --- | --- |
| `grill-with-docs` | Interrogate requirements before implementation and preserve the resulting decisions, ADRs, and domain vocabulary. |
| `codebase-design` | Design deep modules: substantial behavior behind small, clean interfaces. |
| `improve-codebase-architecture` | Periodically find architectural improvements before the system becomes costly to change. |
| `resolving-merge-conflicts` | Resolve conflicts based on the intent of each branch, rather than mechanically choosing one side. |

Avoid installing competing versions of the same default workflow without a deliberate routing rule. In particular, select one TDD skill; this reference uses `test-driven-development` as the default because it applies broadly to PHP, React, Node, Playwright, and Python work.

### Laravel-specific layer

Use Laravel's official agent skills alongside the two layers above for framework conventions and Laravel-specific implementation knowledge.

```text
Primary engineering framework (Addy)
             +
Requirements and module design (Matt)
             +
Laravel conventions (official Laravel skills)
```

## End-to-End Workflow

```text
Software idea
  ↓
grill-with-docs
  ↓
idea-refine (optional)
  ↓
spec-driven-development
  ↓
constraint-driven-development
  ↓
codebase-design
  ↓
planning-and-task-breakdown
  ↓
incremental-implementation
  ├─ frontend-ui-engineering (React/UI)
  └─ api-and-interface-design (Laravel/API)
  ↓
test-driven-development
  ↓
browser-testing-with-devtools
  ↓
debugging-and-error-recovery
  ↓
code-review-and-quality
  ├─ security-and-hardening
  ├─ performance-optimization
  └─ code-simplification, when appropriate
  ↓
ci-cd-and-automation
  ↓
observability-and-instrumentation
  ↓
shipping-and-launch
  ↓
Production
```

## Requirements Interrogation Checklist

Run `grill-with-docs` for meaningful features and greenfield SaaS work. The goal is to surface decisions that implementation cannot safely invent.

For example, subscription billing should establish:

- Billing cadence: monthly, annual, or both.
- Trial rules and conversion behavior.
- Upgrade and downgrade timing and proration.
- Cancellation timing, retention, and access after cancellation.
- Failed-payment and dunning behavior.
- Subscription states and allowed transitions.
- Ownership of Stripe webhook processing.
- Feature-entitlement model.
- Billing portal and self-service capabilities.
- Whether subscriptions belong to users or organizations.
- Treatment of customer data following cancellation.

Record the resulting decisions as ADRs, a glossary, or a feature specification before planning tasks.

## Stack-Specific Essentials

### Laravel + React

Start with:

```text
context-engineering
spec-driven-development
planning-and-task-breakdown
incremental-implementation
api-and-interface-design
frontend-ui-engineering
test-driven-development
browser-testing-with-devtools
debugging-and-error-recovery
code-review-and-quality
security-and-hardening
git-workflow-and-versioning
```

### SaaS additions

Add:

```text
grill-with-docs
codebase-design
constraint-driven-development
ci-cd-and-automation
observability-and-instrumentation
performance-optimization
documentation-and-adrs
shipping-and-launch
```

### Native macOS client

The core workflow still applies: requirements, specification, modules, contracts, tests, security, CI/CD, observability, and release discipline. Use `write-swift` for Swift implementation, review, migrations, concurrency, and performance work when the client is built with Swift or SwiftUI; the general-purpose skills are not a replacement for platform-specific expertise.

### Chrome extension

Prioritize:

```text
spec-driven-development
frontend-ui-engineering
browser-testing-with-devtools
security-and-hardening
performance-optimization
api-and-interface-design
test-driven-development
ci-cd-and-automation
```

Extensions have unusual security and runtime boundaries: content scripts, background workers, popup UI, browser permissions, DOM interaction, Chrome APIs, and network requests. Treat those boundaries as explicit parts of the specification and security review.

## Practical Architecture Guidance

Favor domain modules with narrow interfaces over scattered helpers. For billing, prefer a boundary such as:

```text
Billing
├── SubscriptionService
├── Entitlements
└── BillingGateway
```

Keep Stripe implementation details behind the billing boundary instead of exposing them through a growing set of controllers and helpers.

For public APIs, define a stable error contract rather than allowing each endpoint to improvise its own response:

```json
{
  "error": {
    "code": "subscription_required",
    "message": "An active subscription is required."
  }
}
```

This becomes especially important as one Laravel API serves multiple clients, such as a React web application, native macOS application, and Chrome extension.

## Quality Gates Before Release

- Requirements decisions are documented and unambiguous.
- The specification includes API boundaries, security implications, and acceptance criteria.
- Work is delivered in small, tested slices with atomic commits.
- Browser-facing flows are validated in a real browser.
- A review covers correctness, security, performance, and maintainability.
- CI verifies formatting, static analysis, unit/integration tests, browser tests, security checks, and production builds as appropriate.
- Production has sufficient logs, metrics, traces, and alerts to answer: what failed, where, for whom, why, since when, and after which deployment.
- Release plans include rollout, monitoring, and rollback steps.

## Source Note

This reference consolidates a prior comparison of Matt Pocock's and Addy Osmani's skill collections. Skill availability and names can change; verify the currently installed skills before relying on a workflow step.
