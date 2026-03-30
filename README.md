# Promt basics

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

Custom Naming: If you prefer the name AGENTS.md, you can configure the CLI to recognize it in your
      ~/.gemini/settings.json:

   1     {
   2       "context": {
   3         "fileName": ["AGENTS.md", "GEMINI.md"]
   4       }
   5     }

Global Subagents (~/.gemini/agents/*.md): If you want to define specific specialized agents (like a reviewer.md or debugger.md) that you can call in any project, you can place their Markdown definitions in this directory.
