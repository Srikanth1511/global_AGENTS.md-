#Promt basics

Place this inside every agents folder. 
4 files. Suggested placement:

```
~/ (or any global config dir)
├── AGENTS.md          ← symlink target
├── CLAUDE.md          ← ln -s AGENTS.md CLAUDE.md
├── GEMINI.md          ← ln -s AGENTS.md GEMINI.md
└── prompts/
    ├── ANTI_HALLUCINATION.md
    ├── MATH_GUARDRAIL.md
    └── LARGE_REPO.md
```

Invoke prompts by pasting contents or referencing the file at the start of a session when that mode is needed.
