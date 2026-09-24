# Prompt 3 — Break it into tasks

> 📖 **Book:** each task is one [§2.3.2 red–green–refactor](https://www.swebook.org/chapters/02-software-development-processes/index.html#232-testing-make-it-central-to-development) cycle; "every AC is covered" is [§3.4.4 traceability](https://www.swebook.org/chapters/03-user-requirements/index.html#344-tracing-requirements-to-tests-and-backlog-items).

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
