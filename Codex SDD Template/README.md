# Spec-Driven Development with Codex — CS 4300/5300 Template

**Optional.** Use this if you want to build with Codex, the AI coding tool UCCS provides.
You are not required to use AI on any assignment.

In spec-driven development (SDD), **you** decide what to build, and you write it down before
any code exists. Codex then works from your written spec, not from a one-line prompt. You end up
with code you can explain, tests that match your requirements, and a record of what the AI did.

```
 1. SPECIFY   →   2. PLAN   →   3. TASKS   →   4. IMPLEMENT (test first)   →   5. REVIEW
   (you)          (you + AI)    (you + AI)       (AI, one task at a time)       (you)
```

---

## What's in here

| Path | What it is |
|---|---|
| `AGENTS.md` | Rules Codex reads automatically every session: follow the spec, write tests first, work in small steps. |
| `specs/_template/` | Blank `spec.md`, `plan.md` and `tasks.md`. Copy this folder once per feature. |
| `specs/001-favorite-recipes/` | A finished example for a made-up app, so you can see what "good" looks like. |
| `prompts/` | Prompts to paste into Codex, one for each step. |
| `AI-USAGE.md` | A log of how you used AI. The course requires you to cite AI use in your README. |

---

## Setup (5 minutes)

1. Copy everything in this folder into the **root of your project**. For HW2 that's your
   `homework2/` folder. For your team project it's the repo root.
   - Codex reads `AGENTS.md` from the folder you start it in and from every parent folder up to
     the git root.
2. Commit the template before you write any code:
   `git add . && git commit -m "Add SDD template"`
3. Start Codex from that folder, then check that it read the rules by asking:
   *"Summarize the rules in AGENTS.md in 3 bullets."*

---

## The workflow

Build **one feature at a time**. A feature is something a user can do, such as "book a seat" or
"see my booking history." It is not a layer of the app, such as "the models."

### 1. Specify: what and why (you write this)
```bash
cp -r specs/_template specs/002-<short-feature-name>
```
Fill in `spec.md` yourself: the user stories, the acceptance criteria and what's out of scope.
Write the acceptance criteria as **Given/When/Then**, because they become your Behave scenarios.

Then paste `prompts/01-specify.md` into Codex. **Codex reviews your spec; it doesn't write it.**
It points out gaps, ambiguities and missing edge cases, and you decide what to change.

> A spec is done when a classmate could read it and write the tests without asking you anything.

### 2. Plan: how (you + Codex)
Paste `prompts/02-plan.md`. Codex drafts `plan.md`, covering the models, endpoints, files and
test strategy. **Read every line.** If you can't explain a decision in the plan, ask Codex why
or change it. Then commit.

### 3. Tasks: small steps (you + Codex)
Paste `prompts/03-tasks.md`. Codex breaks the plan into a checklist in `tasks.md`. Each task
should be small enough to finish in one test→code→pass cycle.

### 4. Implement: one task at a time, test first
Paste `prompts/04-implement.md` for **each task**. Codex will:
1. write the failing test and show you it fails (🔴),
2. write the least code that makes it pass (🟢),
3. clean up while keeping the tests green (🔵),
4. tick the box in `tasks.md` and stop.

You then read the diff, run the tests yourself, and commit with a meaningful message.
**One task = one commit.** Don't let Codex run several tasks without stopping.

### 5. Review: your name is on it
Paste `prompts/05-review.md`. Codex checks the finished feature against the spec's acceptance
criteria and reports what's met, what's missing and where tests are thin. Then **you** run:
```bash
python manage.py test          # or: pytest
coverage run manage.py test && coverage report
behave
```
Finally, add an entry to `AI-USAGE.md`.

---

## Rules of thumb

- **The spec is the source of truth.** If the code and the spec disagree, fix one of them on
  purpose. Don't let them drift apart.
- **If the requirements change, update the spec first**, then re-plan. Don't just re-prompt.
- **Small diffs.** If Codex wants to change 10 files for one task, the task is too big. Split it.
- **You must be able to explain every line.** "Codex wrote it" isn't an answer in a code review,
  a demo or an exam.
- **Never paste secrets** (API keys, `.env` contents, passwords) into Codex. Keep them in
  environment variables.
- **Cite your AI use.** Put the `AI-USAGE.md` summary in your README, as the assignment requires.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Codex ignores the rules | Make sure you started it in the folder containing `AGENTS.md`. Say "Re-read AGENTS.md." |
| Codex writes code before tests | Say "Stop. Test first. Revert the code and show me the failing test." |
| Codex invents requirements | Say "That's not in spec.md. Either remove it or add it to Open Questions." |
| Huge diffs | Say "Undo that. Implement only the next unchecked task in tasks.md." Or run `git restore .` |
| Django app not loading in DevEdu | Run on port 3000: `python manage.py runserver 0.0.0.0:3000` |
