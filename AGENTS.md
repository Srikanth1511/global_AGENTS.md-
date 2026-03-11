# AGENTS.md — Global Agent Mandates (Srikanth)

Symlink: `ln -s AGENTS.md CLAUDE.md && ln -s AGENTS.md GEMINI.md`

---

## 1. Core Principles

- **Ask before acting** on ambiguous requirements, cascading changes, or conflicting mandates.
- **Prioritize:** Safety > Correctness > Reproducibility > Performance > Convenience.
- **Diff-First:** Existing files → minimal diff. New files → full file.
- **Inspect Before Edit:** Read target function, surrounding logic, and imports before proposing changes.
- **No blind writes. No invented APIs. No claimed verification unless it happened.**

---

## 2. Communication

- Concise by default. Theoretical basis required for math/physics/ML logic.
- Non-trivial implementation choices → propose options, ask for direction.
- Do not over-comment; write self-documenting code.

---

## 3. Environment & Config

- Constants → `config/constants.yaml`. No hard-coded magic numbers.
- Runtime overrides via env vars only (`DEBUG`, `DOE_MODE`, `OFFLINE_MODE`).
- Runtime-tunable params must be env-var-exposed even if config-defaulted (enables sweep comparison).

---

## 4. Debugging

Silent on success. Use `os.getenv("DEBUG")`:

| Level | Output |
|-------|--------|
| `1` | Shapes, sizes, dtypes at function boundaries |
| `2` | Deep value inspection, state transitions |

---

## 5. Verification

- Every script needs `if __name__ == "__main__":` covering Base, Edge, and Physical Boundary cases.
- Project-wide integration tests in `tests/`.

---

## 6. Aerospace / Math / ML

- Explicit units + coordinate system in signatures (`altitude_m_msl`, `velocity_mps`).
- Bounds-check physical values (Mach, altitude, sensor ranges).
- Validate tensor shapes, device placement, NaN/Inf before ops.
- Set and log seeds (`torch.manual_seed`, `numpy.random.seed`). Prefer deterministic ops.
- One-sentence theoretical basis before complex logic.
- Avoid premature abstraction. Prefer simple, explicit modules.

---

## 7. Provenance

- Every run → `results/runs/YYYYMMDD_HHMMSS_run_metadata.json` (params, env vars, seeds, versions, hardware).
- Log failed runs and exceptions. Negative results matter.
- Primary output format: JSON.
- Before major refactor → `git commit` or `git stash`.

---

## 8. Architecture & Sessions

- Read `ARCHITECTURE.md` mermaid diagrams before loading code in new sessions.
- New functionality: identify subsystem, extend existing modules, avoid parallel pipelines.
- Each TODO defines: input, output, affected files, validation method.

**End-of-session:**
1. Summarize changes.
2. Update `ARCHITECTURE.md` if behavior changed.
3. Append to `updates.md`.
4. Suggest next TODO.

---

## 9. MCP Tools

| Server | Purpose |
|--------|---------|
| `filesystem` | Safe file read/write |
| `git` | Diffs, history, rollback |
| `context7` | Live version-specific library docs |
| `memory` | Persist TODOs across sessions |

**Always query `context7` before generating library/API code.**
Config in `.mcp.json` at project root.

---

## 10. Reusable Prompts

Invoke explicitly when needed:

- `prompts/ANTI_HALLUCINATION.md`
- `prompts/MATH_GUARDRAIL.md`
- `prompts/LARGE_REPO.md`

---

## Local Project Bootstrap

```markdown
# Project Context

## Identity
- Domain:
- Tech Stack:

## Active TODO
- Task:
- Input:
- Output:
- Files affected:
- Validation:

## Standards
- Constants: config/constants.yaml
- Tests: pytest tests/ + __main__ blocks
- Docs: ARCHITECTURE.md + updates.md
```
