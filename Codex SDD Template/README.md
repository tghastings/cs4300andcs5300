# HW2 with Codex: Spec-Driven Development Template

**Optional.** Use this if you want to build **Homework 2 (Movie Theater Booking)** with Codex,
the AI coding tool UCCS provides. You are not required to use AI.
Assignment: https://tghastings.github.io/cs4300andcs5300/homework_2.pdf

In spec-driven development (SDD), **you** decide what to build and write it down before any code
exists. Codex then works from your written spec, not from a one-line prompt. You end up with code
you can explain, tests that match your requirements, and the AI citation HW2 requires.

```
 1. SPECIFY   →   2. PLAN   →   3. TASKS   →   4. IMPLEMENT (test first)   →   5. REVIEW
   (you)          (you + AI)    (you + AI)       (AI, one task at a time)       (you)
```

---

## HW2 is split into three features

| Spec folder | Feature (from the HW2 objective) | State in this template |
|---|---|---|
| `specs/001-movie-listings/` | View movie listings (API + UI) | ✅ **Worked example**: spec, plan and tasks filled in. Read it, adjust it, build it. |
| `specs/002-seat-booking/` | Book seats (API + UI) | 🟡 **Started**: user stories and the first criteria are written. You finish the spec. |
| `specs/003-booking-history/` | Check booking history (API + UI) | 🟡 **Started**: user stories and the first criteria are written. You finish the spec. |

Deployment (Render) and documentation aren't features. They're on the checklist at the bottom.

## What's in here

| Path | What it is |
|---|---|
| `AGENTS.md` | Rules and HW2 project context that Codex reads automatically every session. |
| `specs/_template/` | Blank `spec.md`, `plan.md` and `tasks.md`, in case you add a feature of your own. |
| `specs/001–003/` | The three HW2 features above. |
| `prompts/` | Prompts to paste into Codex, one for each step. |
| `AI-USAGE.md` | A log of how you used AI. HW2 requires you to cite AI use in your README. |

---

## Setup

1. Do HW2's **Project Setup** first (section 3.1 of the PDF): create
   `homework2/movie_theater_booking`, the virtual environment, and install `django` and
   `djangorestframework`.
2. Copy everything in this folder into **`homework2/movie_theater_booking/`**, next to
   `manage.py`. Codex reads `AGENTS.md` from the folder you start it in.
3. Install the test tools:
   `pip install coverage behave-django && pip freeze > requirements.txt`
   Plain `behave` doesn't know about Django. **behave-django** (the tool HW2 links to) runs your
   scenarios against a Django test database. Add `behave_django` to `INSTALLED_APPS` and run
   Behave with `python manage.py behave`.
4. Commit before you write any code:
   `git add . && git commit -m "HW2: add SDD template"`
5. Start Codex **from that folder**, then check that it read the rules by asking:
   *"Summarize AGENTS.md in 3 bullets."*

---

## The workflow (repeat for 001, then 002, then 003)

### 1. Specify: what and why (you)
- **001:** read the worked spec. Change anything you'd do differently. It's your app now.
- **002 / 003:** finish `spec.md`. Every `TODO` is a decision **you** make, such as what happens
  when someone books a seat that's already taken. Write acceptance criteria as
  **Given/When/Then**, because they become your Behave scenarios.

Then paste `prompts/01-specify.md`. **Codex reviews your spec; it doesn't write it.**

> A spec is done when a classmate could read it and write the tests without asking you anything.

### 2. Plan: how (you + Codex)
Paste `prompts/02-plan.md`. Codex fills in `plan.md` with the models, serializers, viewsets,
URLs, templates and test strategy. **Read every line.** If you can't explain a decision, ask
Codex why or change it. Then commit.
- 001's plan is already filled in so you can see the level of detail to aim for.

### 3. Tasks: small steps (you + Codex)
Paste `prompts/03-tasks.md`. Each task is one test→code→pass cycle and one commit.

### 4. Implement: one task at a time, test first
Paste `prompts/04-implement.md` **for each task**. Codex writes the failing test (🔴), the least
code that passes (🟢), cleans up (🔵), ticks the box, and **stops**. Then you read `git diff`, run
the tests, `git add` the files you reviewed, and commit with a meaningful message. HW2 asks for frequent pushes with good commit
messages, and one task per commit gives you exactly that.

### 5. Review: your name is on it
Paste `prompts/05-review.md`. Then run the checks yourself:
```bash
python manage.py test
coverage run --source=bookings manage.py test && coverage report   # HW2 needs ≥ 80%
python manage.py behave
python manage.py runserver 0.0.0.0:3000                            # then click "app" in DevEdu
```

---

## How this maps to the HW2 rubric

| Rubric (Table 1) | Pts | Where it comes from |
|---|---|---|
| Functionality | 35 | Features 001–003, each API endpoint **and** its template page |
| User Experience | 15 | The UI criteria in each spec: Bootstrap `base.html`, navigation, empty states |
| Code Quality | 15 | `AGENTS.md` rules: Django conventions, docstrings, small diffs |
| Testing | 20 | Every acceptance criterion → a unit/integration test or Behave scenario; ≥ 80% coverage |
| Deployment | 10 | The Render checklist below |
| Documentation | 5 | README with setup, structure, Render URL **and** your AI citation |

## Before you submit

- [ ] Every acceptance criterion in 001–003 has a passing test
- [ ] `python manage.py test` and `python manage.py behave` both pass
- [ ] Coverage ≥ 80%
- [ ] App runs in DevEdu on port 3000
- [ ] Deployed on Render and the URL works
- [ ] README: setup instructions, project structure, how to run, the Render URL, and the AI
      citation (copy the summary from `AI-USAGE.md`)
- [ ] Pushed to GitHub, and the zip is submitted in Canvas

---

## Rules of thumb

- **The spec is the source of truth.** If the code and the spec disagree, fix one of them on purpose.
- **If the requirements change, update the spec first**, then re-plan.
- **Small diffs.** If Codex wants to change 10 files for one task, the task is too big.
- **You must be able to explain every line.** "Codex wrote it" isn't an answer.
- **Never paste secrets** (such as your Django `SECRET_KEY` or Render environment variables) into Codex.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Codex ignores the rules | Start it in the folder containing `AGENTS.md`. Say "Re-read AGENTS.md." |
| Codex writes code before tests | "Stop. Test first. Revert the code and show me the failing test." |
| Codex invents requirements | "That's not in spec.md. Remove it or add it to Open Questions." |
| Huge diffs | "Undo that. Implement only the next unchecked task." Or run `git restore .` |
| App won't load in DevEdu | Use port 3000: `python manage.py runserver 0.0.0.0:3000` |
| Behave can't find Django | Run `python manage.py behave`, not plain `behave`, and check that `behave_django` is in `INSTALLED_APPS`. behave-django handles the setup, so you don't need a hand-written `features/environment.py`. |
