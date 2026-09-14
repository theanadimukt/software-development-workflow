---
name: software-development-workflow
description: Routes software-development requests to the smallest relevant set of installed specialist skills. Use for command-style requests such as /spec, /plan, /architect, /build, /test, /debug, /review, /code-simplify, /webperf, or /ship; also routes frontend design, motion, mobile, and ADHD-friendly output requests without embedding upstream skill content.
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

## Interface and visual-work routing

For user-facing interface work, use `impeccable` as the broad default for shaping, auditing, polishing, or optimizing an interface. Add one specialized skill only when its focus is clearly needed; do not stack competing visual-direction skills.

| Request | Preferred skill | Use instead / add only when needed |
|---|---|---|
| Build or redesign a web page, landing page, portfolio, or product UI | `design-taste-frontend` | `redesign-existing-projects` for an existing interface; `high-end-visual-design` for visual-direction constraints; `minimalist-ui` or `industrial-brutalist-ui` only when that named aesthetic fits |
| Turn a visual reference into working web UI | `image-to-code` | Generate new section references with `imagegen-frontend-web` when the design source is incomplete |
| Create an original website visual concept | `imagegen-frontend-web` | It generates design references; use a frontend implementation skill afterward to build them |
| Create a mobile-app visual concept | `imagegen-frontend-mobile` | Image generation only; use implementation tooling separately |
| Produce a brand system, identity board, or visual-world deck | `brandkit` | Use only for brand deliverables, not routine product UI |
| Document a premium design system for Google Stitch | `stitch-design-taste` | Prefer it only when Stitch or `DESIGN.md` is the stated target |
| Need complete, unabridged generated code | `full-output-enforcement` | Use sparingly; it governs delivery completeness rather than architecture |
| Need the legacy Taste Skill behavior | `design-taste-frontend-v1` | Default to the current `design-taste-frontend` otherwise |

## Motion and platform routing

- Use `animate` to design and implement web motion. Use `animate-expo` for React Native/Expo motion, gestures, transitions, or haptics.
- Use `review-animations` for a specific motion implementation, `improve-animations` for a read-only codebase-wide motion roadmap, and `find-animation-opportunities` for read-only suggestions of where motion belongs.
- Use `animation-vocabulary` only to name a described effect. Use `apple-design` when physical, gesture-led, or Apple-like interaction principles are central.
- Use `prototype` only when the user explicitly wants several live-comparable UI directions. Use `pick-ui-library` only when explicitly requested to select a frontend library.
- Use `ask-sonner` for Sonner toast integration or troubleshooting. Use `write-swift` for Swift implementation, review, migrations, concurrency, or performance work.
- `gpt-taste` is an intentionally opinionated GSAP/editorial direction; choose it only when its visual language and motion approach match the brief.

## Output accessibility

When the user explicitly invokes `/i-have-adhd`, use `i-have-adhd` and keep that mode active until they say to stop it. Lead with the next action, number multi-step work, restate state across turns, suppress tangents, include concrete time estimates, and make completed progress visible. Do not activate it implicitly.

## Skill sources

- `i-have-adhd` comes from `ayghri/i-have-adhd`.
- The visual and frontend-direction skills above come from `leonxlnx/taste-skill`.
- The motion, interaction, Swift, toast, and explicit-invocation skills above come from `emilkowalski/skills`.
- `impeccable` comes from `pbakaus/impeccable` and is the broad frontend craft default.
