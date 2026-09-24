# Prompt 4 — Implement ONE task (repeat per task)

```
Read AGENTS.md. Implement ONLY the next unchecked task in specs/<NNN-feature>/tasks.md.

1. Write the test first. Run it and show me that it fails, and why.
2. Write the least code that makes it pass. Run the FULL test suite.
3. Refactor if it helps, keeping the tests green.
4. Tick the task in tasks.md.
5. Stop and tell me: which files changed, what each change does, and the one concept I should
   understand from this step.
Don't commit, and don't start the next task.
```

**Then you:**
1. Read the diff: `git diff`, plus `git status` for any **new** files (tests, migrations, templates)
2. Run the tests yourself
3. Stage only the files you reviewed, then commit:
   `git add <reviewed files>` and then `git commit -m "T#: <what it does>"`
   (Don't use `git commit -am`. It skips new files, so a new migration or template gets left out.)
4. Add a line to `AI-USAGE.md`
