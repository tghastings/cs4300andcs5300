# Prompt 5 — Review the feature against the spec

```
Read specs/<NNN-feature>/spec.md. Don't change any code.

For every acceptance criterion, report:
- ✅ met: name the test that proves it
- ⚠️ partial: what's missing
- ❌ not met

Then list:
- Behavior in the code that is NOT in the spec (scope creep)
- Edge cases with no test
- Places where plan.md and the code disagree
- Anything a code reviewer would flag (naming, duplication, missing docstrings, security)
```

**Then you:** fix the gaps (each fix is a new task), run `coverage report` and `behave`, and
work through the "Before you submit" checklist in README.md.
