# Tasks: Movie listings

**Plan:** [plan.md](plan.md)

> Each task is one red → green → refactor cycle and one commit. Codex ticks the box. **You** commit.

- [ ] **T1** — `Movie` model + migration + `__str__` + ordering · test: `test_movie_str_and_ordering` · covers: Data
- [ ] **T2** — `MovieSerializer` + `MovieViewSet` + router; `GET /api/movies/` · test: `test_list_movies` · covers: AC-4
- [ ] **T3** — `POST /api/movies/` · test: `test_create_movie` · covers: AC-5
- [ ] **T4** — Validation: title required, duration > 0 · tests: `test_create_movie_missing_title_400`, `test_create_movie_zero_duration_400` · covers: AC-6
- [ ] **T5** — Retrieve, update, delete, 404 · tests: `test_update_movie`, `test_delete_movie`, `test_get_missing_movie_404` · covers: AC-7, AC-8
- [ ] **T6** — `base.html` (Bootstrap + navbar) + `movie_list` view/template · tests: `test_movie_list_uses_base_template`, `test_movie_list_shows_release_date_and_duration` · covers: AC-1, AC-3, AC-9
- [ ] **T7** — Empty state · test: `test_movie_list_empty_state` · covers: AC-2
- [ ] **T8** — Behave setup + scenarios "Browse the movie list", "No movies showing" · covers: AC-1, AC-2

## Done when
- [ ] Every acceptance criterion in `spec.md` has a passing test
- [ ] `python manage.py test` and `behave` pass
- [ ] Coverage ≥ 80% for `bookings`
- [ ] `AI-USAGE.md` updated
