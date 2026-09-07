---
name: software-development-workflow
description: Routes software-development requests to the smallest relevant set of installed specialist skills. Use for command-style requests such as /spec, /plan, /architect, /build, /test, /debug, /review, /code-simplify, /webperf, or /ship, and for choosing an engineering workflow without embedding upstream skill content.
---

# Software Development Workflow

Interpret a leading command as a workflow intent. The command is a routing hint, not a fixed alias: inspect the request, repository context, risk, and requested outcome before selecting skills.

## Discovery and delegation

1. Discover the skills available in the active environment and verify a candidate's exact name before using it.
2. Select the smallest set that materially improves the work. Do not load unrelated lifecycle stages.
3. Read and follow each selected skill's current `SKILL.md`; this router never copies, summarizes, or overrides specialist instructions.
4. State the selected skills briefly when doing meaningful work, then perform the request.

Read [the routing guide](references/routing.md) for command candidates and selection signals. It names skills only; their implementation guidance remains upstream.

## Missing-skill fallback

If a useful candidate is unavailable, do not fail the user request solely for that reason. Say which capability is absent, continue with a proportionate general workflow, and use a locally available equivalent when one exists. Suggest installing a specialist only when its absence materially limits the result. Never invent a skill or claim an unavailable skill was used.

## Command behavior

- `/spec` — clarify scope and produce a testable specification; add interface, UI, constraints, or research specialists only when the request warrants them.
- `/plan` — turn an approved or sufficiently clear objective into a dependency-aware, verifiable implementation plan.
- `/architect` — assess structure, boundaries, interfaces, migrations, and consequential trade-offs before proposing a design.
- `/build` — implement the smallest coherent slice; add focused UI, API, source-verification, or testing help only when applicable.
- `/test` — choose the relevant test level and validate the requested behavior rather than merely increasing coverage.
- `/debug` — reproduce and isolate the fault before changing code; add browser or performance investigation only when evidence points there.
- `/review` — review the requested change for correctness and maintainability; add security or performance review only for relevant risk.
- `/code-simplify` — reduce accidental complexity while preserving externally observable behavior.
- `/webperf` — measure the user-facing bottleneck, diagnose its cause, and verify an improvement.
- `/ship` — prepare the requested release or delivery step, including version-control, automation, and launch work only when needed.

If no command is supplied, infer the best entry point from the user's actual request. Ask a focused question only when a missing decision would materially change the work.
