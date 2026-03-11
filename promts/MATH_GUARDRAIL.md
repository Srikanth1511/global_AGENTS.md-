# Math / Physics / ML Guardrail

When writing or explaining math-heavy logic:

1. One-sentence theoretical basis first.
2. Define symbols, units, coordinate system, and assumptions explicitly.
3. State whether the operation is: scaling, rotation, reflection, translation, or a combination.
4. State tensor/array dimensions before operations.
5. Include base case, edge case, and failure mode checks.
6. Prefer numerically stable formulations over algebraically compact ones.
7. If approximations are used, explicitly justify why they are acceptable.
