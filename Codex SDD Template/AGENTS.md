# AGENTS.md — Rules for Codex

This project uses **spec-driven development**. A student in CS 4300/5300 (UCCS) owns this code
and must be able to explain every line of it. You are a pair programmer, not the author.

## Source of truth
- Features are defined in `specs/<NNN-feature>/spec.md`. Build **only** what the spec says.
- If something is ambiguous or missing, **ask** or add it under "Open Questions" in the spec.
  Never invent requirements, fields, endpoints or UI.
- `plan.md` says *how*. `tasks.md` says *in what order*. Keep all three in sync. If the code has
  to differ from the plan, say so and update `plan.md` in the same change.

## How to work
1. **One task at a time.** Implement only the next unchecked task in `tasks.md`, then stop and
   report back. Don't start the next task until the student says so.
2. **Test first (red → green → refactor).**
   - Write the test first and run it to show that it fails, and why.
   - Write the least code that makes it pass, then run the full test suite.
   - Refactor only while the tests stay green.
3. **Small diffs.** Touch only the files the task needs. No drive-by reformatting or renaming.
4. **Explain.** After each task, summarize in plain language what changed and why, and name
   the one concept the student should understand from this step.
5. Tick the box in `tasks.md` when the task's tests pass.

## Acceptance criteria → tests
- Each Given/When/Then criterion in `spec.md` must map to at least one test:
  a Behave scenario in `features/` for user-visible behavior, and a Django/pytest test for
  model, serializer, view and API logic.
- Test edge cases and error paths, not just the happy path.
- The course requires **≥ 80% coverage**. Check it with `coverage run manage.py test && coverage report`.

## Project conventions (Django)
- Follow Django conventions: apps, models, views, `urls.py`, templates in `<app>/templates/<app>/`.
- For APIs, use Django REST Framework serializers and viewsets. Return correct status codes.
- In DevEdu, run the dev server with `python manage.py runserver 0.0.0.0:3000`.
- Add dependencies to `requirements.txt` in the same change.
- Write docstrings and comments that explain *why*, not *what*.

## Never
- Never put secrets, API keys or passwords in code, tests, fixtures or commits. Use environment variables.
- Never delete or weaken a test just to make it pass. If you think a test is wrong, say so and ask.
- Never run `git push`, `git reset --hard` or force-push, or rewrite history. The student commits and pushes.
- Never change files outside this project folder.

## When you finish a feature
List each acceptance criterion from `spec.md` and mark it ✅ met (naming the test that proves
it), ⚠️ partial, or ❌ missing. Remind the student to update `AI-USAGE.md`.
