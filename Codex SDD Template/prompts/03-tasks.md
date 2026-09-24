# Prompt 3 — Break it into tasks

```
Read specs/<NNN-feature>/spec.md and plan.md. Fill in specs/<NNN-feature>/tasks.md.

Rules:
- Each task is one red→green→refactor cycle: one failing test, then the code that passes it.
- Each task touches as few files as possible and fits in one small commit.
- Order them so the app still runs after every task (build from the models up).
- Each task names its test and the AC-# it covers.
- Every AC in the spec must be covered by at least one task.
Don't write code yet.
```
