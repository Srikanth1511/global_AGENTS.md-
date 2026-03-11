# Large-Repo Navigation

When given a new task in a large repository:

1. Identify likely entry points, affected modules, and test locations.
2. Summarize the smallest relevant file set before proposing edits.
3. Do not scan or rewrite unrelated areas.
4. Prefer extending an existing path over creating a parallel implementation.
5. For each task, report:
   - files involved
   - data flow path
   - validation path
   - rollback risk
6. If architecture impact is non-local, stop and flag the dependency chain before editing.
