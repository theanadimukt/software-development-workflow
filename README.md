# software-development-workflow

A lightweight, command-style router for agentic software development. It selects and uses the smallest appropriate set of **currently installed** specialist skills; it does not vendor their instructions. Updating an upstream specialist therefore updates its behavior independently of this router.

## Commands

`/spec`, `/plan`, `/architect`, `/build`, `/test`, `/debug`, `/review`, `/code-simplify`, `/webperf`, and `/ship`.

Each command inspects the request and project context. For example, `/review Fix the checkout error` may use only a general review skill, while `/review Audit this new public payments API` can additionally select a security specialist.

The workflow is a router, not a set of aliases. `/architect` starts with architecture expertise and adds API/interface design when the decision affects a contract. `/spec` can choose ambiguity, idea, constraint, interface, UI, architecture, or security expertise only when the request signals that need. The same routing behavior applies when no command is supplied: the router infers the appropriate stage from the request.

## Recommended Agent-Assisted SDLC

For Laravel + React SaaS work, use Addy Osmani's skills as the primary engineering framework, supplemented by four Matt Pocock skills for requirements and architecture, plus Laravel's official skills for framework-specific conventions.

```text
Idea → requirements → specification → constraints → architecture → plan
     → incremental implementation → tests → review → CI/CD
     → observability → release
```

The recommended default sequence is:

1. `grill-with-docs` — clarify requirements and preserve decisions, ADRs, and domain language.
2. `idea-refine` (optional), `spec-driven-development`, and `constraint-driven-development` — turn the idea into an implementable, bounded specification.
3. `codebase-design` and `planning-and-task-breakdown` — design narrow modules and split work into verifiable slices.
4. `incremental-implementation` — implement, test, verify, and commit each slice before the next.
5. `frontend-ui-engineering` for React/UI work and `api-and-interface-design` for Laravel/API contracts.
6. `test-driven-development`, `browser-testing-with-devtools`, `debugging-and-error-recovery`, and `code-review-and-quality` — validate behavior before merge.
7. `security-and-hardening`, `performance-optimization`, `ci-cd-and-automation`, `observability-and-instrumentation`, and `shipping-and-launch` — prepare, operate, and release safely.

The complementary Matt skills are `grill-with-docs`, `codebase-design`, `improve-codebase-architecture`, and `resolving-merge-conflicts`. Keep only one default skill for overlapping concerns such as TDD, to avoid ambiguous routing.

See the full [agent-assisted SDLC reference](docs/agentic-sdlc-reference.md) for stack-specific checklists, requirements-interrogation prompts, architecture guidance, and release quality gates.

## Examples

```text
/spec Add organization-level roles with audit history
/plan Implement the approved notification preferences spec
/architect Split the billing module without breaking existing clients
/build Add keyboard navigation to the command palette
/test Prove the password reset flow works in a browser
/debug The dashboard is intermittently blank after refresh
/review Review the current branch before merge
/code-simplify Reduce duplication in the invoice calculation path
/webperf Investigate the slow product-list interaction
/ship Prepare version 2.4.0 for production
```

## Install

Install globally for Codex with the Skills CLI:

```bash
npx skills add theanadimukt/software-development-workflow -g -a codex -y
```

Restart the agent session after installation if the skill catalog does not refresh automatically.

To develop from a local checkout instead, clone the repository into a persistent location and make it discoverable by Codex:

```bash
git clone <repo-url> ~/Projects/software-development-workflow
ln -s ~/Projects/software-development-workflow ~/.codex/skills/software-development-workflow
```

If `~/.codex/skills/software-development-workflow` already exists, remove or rename that link or directory before creating the link.

The router degrades gracefully when a candidate specialist is absent: it reports the missing capability, uses an available equivalent or a proportionate general workflow, and never claims that a missing skill ran.

## Development

Validate the package with the Codex skill validator:

```bash
python3 /path/to/skill-creator/scripts/quick_validate.py .
```

Each command has a focused routing reference under [`references/`](references/). They intentionally contain names and selection cues only, not copied specialist content.
