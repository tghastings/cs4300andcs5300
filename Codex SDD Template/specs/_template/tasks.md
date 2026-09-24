# Tasks: <Feature name>

**Plan:** [plan.md](plan.md)

> Each task is one red → green → refactor cycle and one commit. Do them in order.
> Codex ticks the box when the task's tests pass. **You** commit.
>
> 📖 **Book:** red → green → refactor is TDD, [§2.3.2](https://www.swebook.org/chapters/02-software-development-processes/index.html#232-testing-make-it-central-to-development).

- [ ] **T1** — <what> · test: `<test name>` · covers: AC-?
- [ ] **T2** — …
- [ ] **T3** — …

## Done when
- [ ] Every acceptance criterion in `spec.md` has a passing test
- [ ] Full suite green: `python manage.py test`
- [ ] `python manage.py behave` passes
- [ ] Coverage ≥ 80%
- [ ] `AI-USAGE.md` updated
