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

When a command is explicit, read only its matching reference before routing:

- `/spec`: [references/spec.md](references/spec.md)
- `/plan`: [references/plan.md](references/plan.md)
- `/architect`: [references/architect.md](references/architect.md)
- `/build`: [references/build.md](references/build.md)
- `/test`: [references/test.md](references/test.md)
- `/debug`: [references/debug.md](references/debug.md)
- `/review`: [references/review.md](references/review.md)
- `/code-simplify`: [references/code-simplify.md](references/code-simplify.md)
- `/webperf`: [references/webperf.md](references/webperf.md)
- `/ship`: [references/ship.md](references/ship.md)

If no command is supplied, infer the best workflow stage from the actual request, then read that stage's reference. The references contain routing signals and candidate names only; specialist implementation guidance remains upstream.

## Missing-skill fallback

If a useful candidate is unavailable, do not fail the user request solely for that reason. Say which capability is absent, continue with a proportionate general workflow, and use a locally available equivalent when one exists. Suggest installing a specialist only when its absence materially limits the result. Never invent a skill or claim an unavailable skill was used.

Ask a focused question only when a missing decision would materially change the work.
