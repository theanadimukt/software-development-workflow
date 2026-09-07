# /code-simplify routing

Goal: remove accidental complexity without changing observable behavior.

Start with `code-simplification`. Add `improve-codebase-architecture` only if the complexity comes from component, module, or dependency boundaries rather than local code. Preserve the behavior with focused tests where the change has regression risk.
