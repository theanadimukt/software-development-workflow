# Routing guide

These are candidates, not mandatory chains. Check the active environment before invoking any name, and read its live `SKILL.md` after selection. Do not treat this file as a copy of any specialist skill.

| Command | Start with | Add only when signaled by the request |
|---|---|---|
| `/spec` | `spec-driven-development` | `grill-with-docs` for consequential ambiguity; `constraint-driven-development` for a missing quality bar; `api-and-interface-design` for public contracts; `frontend-ui-engineering` for substantial UI |
| `/plan` | `planning-and-task-breakdown` | `context-engineering` for unfamiliar code; `api-and-interface-design` for contracts; `source-driven-development` for external APIs |
| `/architect` | `improve-codebase-architecture` | `api-and-interface-design`, `documentation-and-adrs`, `deprecation-and-migration`, or `security-and-hardening` when each matches the decision |
| `/build` | `incremental-implementation` | `test-driven-development`, `frontend-ui-engineering`, `api-and-interface-design`, `source-driven-development`, or `context-engineering` |
| `/test` | `test-driven-development` | `browser-testing-with-devtools` for browser behavior; `performance-optimization` for measured performance acceptance criteria |
| `/debug` | `debugging-and-error-recovery` | `browser-testing-with-devtools`, `performance-optimization`, `observability-and-instrumentation`, or `source-driven-development` based on evidence |
| `/review` | `code-review-and-quality` | `security-and-hardening` for trust boundaries or sensitive data; `performance-optimization` for latency, rendering, or resource concerns |
| `/code-simplify` | `code-simplification` | `improve-codebase-architecture` when the problem crosses component or module boundaries |
| `/webperf` | `performance-optimization` | `browser-testing-with-devtools`, `frontend-ui-engineering`, or `observability-and-instrumentation` where measurement and the bottleneck require them |
| `/ship` | `shipping-and-launch` | `git-workflow-and-versioning`, `ci-cd-and-automation`, `observability-and-instrumentation`, `deprecation-and-migration`, or `documentation-and-adrs` only when release scope calls for them |

## Selection rules

- A tiny, clear change usually needs one specialist, not a lifecycle sequence.
- Treat security, migrations, production releases, and public API changes as higher-consequence work; surface unresolved choices before irreversible action.
- Prefer installed equivalents if an organization uses different skill names. Match on the capability described in their frontmatter, not just a familiar filename.
- Do not add a specialist merely because the command could theoretically use it.
