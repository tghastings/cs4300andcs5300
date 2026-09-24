# Tasks: Favorite recipes

**Plan:** [plan.md](plan.md)

- [ ] **T1** — `Favorite` model + migration + unique constraint · test: `test_unique_constraint` · covers: AC-2
- [ ] **T2** — Serializer + `POST /api/favorites/` · test: `test_post_creates_favorite` · covers: AC-1
- [ ] **T3** — Make POST idempotent · test: `test_post_twice_is_idempotent` · covers: AC-2
- [ ] **T4** — 404 for missing recipe · test: `test_favorite_missing_recipe_404` · covers: AC-7
- [ ] **T5** — Require auth on all favorite endpoints · test: `test_anonymous_gets_403` · covers: AC-3
- [ ] **T6** — `GET /api/favorites/`, own favorites only, newest first · tests: `test_list_only_shows_own_favorites`, `test_empty_list` · covers: AC-4, AC-5
- [ ] **T7** — `DELETE /api/favorites/<recipe_id>/` · test: `test_delete_removes_favorite_not_recipe` · covers: AC-6
- [ ] **T8** — `favorite_list.html` page + empty state + favorite/un-favorite buttons · Behave: "Empty favorites", "Favorite then un-favorite a recipe" · covers: AC-1, AC-5, AC-6

## Done when
- [ ] Every acceptance criterion in `spec.md` has a passing test
- [ ] Full suite green: `python manage.py test`
- [ ] `behave` passes
- [ ] Coverage ≥ 80%
- [ ] `AI-USAGE.md` updated
