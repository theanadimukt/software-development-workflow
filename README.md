# software-development-workflow

A lightweight, command-style router for agentic software development. It selects and uses the smallest appropriate set of **currently installed** specialist skills; it does not vendor their instructions. Updating an upstream specialist therefore updates its behavior independently of this router.

## Commands

`/spec`, `/plan`, `/architect`, `/build`, `/test`, `/debug`, `/review`, `/code-simplify`, `/webperf`, and `/ship`.

Each command inspects the request and project context. For example, `/review Fix the checkout error` may use only a general review skill, while `/review Audit this new public payments API` can additionally select a security specialist.

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

Clone the repository into a persistent location, then make it discoverable by Codex:

```bash
git clone <repo-url> ~/Projects/software-development-workflow
ln -s ~/Projects/software-development-workflow ~/.codex/skills/software-development-workflow
```

If `~/.codex/skills/software-development-workflow` already exists, remove or rename that link or directory before creating the link. Restart the agent session after installation if the skill catalog does not refresh automatically.

The router degrades gracefully when a candidate specialist is absent: it reports the missing capability, uses an available equivalent or a proportionate general workflow, and never claims that a missing skill ran.

## Development

Validate the package with the Codex skill validator:

```bash
python3 /path/to/skill-creator/scripts/quick_validate.py .
```

The routing table in [references/routing.md](references/routing.md) intentionally contains names and selection cues only, not copied specialist content.
