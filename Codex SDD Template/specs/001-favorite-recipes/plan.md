# Plan: Favorite recipes

**Spec:** [spec.md](spec.md)   **Status:** Approved

## 1. Approach
Add a `Favorite` join model between `User` and `Recipe`, with a unique constraint on the pair.
Expose it through a DRF `FavoriteViewSet` whose queryset is always filtered to `request.user`,
and add one template page that lists the user's favorites.
**Rejected:** a `ManyToManyField` on `Recipe`. It's simpler, but it can't store the favorited
date that newest-first ordering needs.

## 2. Data model
| Model | Field | Type | Constraints | Spec ref |
|---|---|---|---|---|
| Favorite | user | FK → User | on_delete=CASCADE | AC-4 |
| Favorite | recipe | FK → Recipe | on_delete=CASCADE | AC-1, AC-7 |
| Favorite | created_at | DateTimeField | auto_now_add; default ordering `-created_at` | Open Q |
| Favorite | — | UniqueConstraint(user, recipe) | — | AC-2 |

## 3. Endpoints / views
| Method | URL | View / ViewSet | Returns | Spec ref |
|---|---|---|---|---|
| GET | `/api/favorites/` | FavoriteViewSet.list | 200, the user's favorites | AC-4, AC-5 |
| POST | `/api/favorites/` `{recipe}` | FavoriteViewSet.create (get_or_create) | 201 new / 200 existing; 404 bad recipe | AC-1, AC-2, AC-7 |
| DELETE | `/api/favorites/<recipe_id>/` | FavoriteViewSet.destroy | 204; 404 if not a favorite | AC-6 |
| GET | `/favorites/` | `favorite_list` template view | HTML page | AC-5 |
| all | — | `IsAuthenticated` / `@login_required` | 401/403 or sign-in redirect | AC-3 |

## 4. Files to create / change
| File | Change |
|---|---|
| `recipes/models.py` | add `Favorite` |
| `recipes/serializers.py` | add `FavoriteSerializer` |
| `recipes/views.py` | add `FavoriteViewSet`, `favorite_list` |
| `recipes/urls.py` | register routes |
| `recipes/templates/recipes/favorite_list.html` | new |
| `recipes/tests/test_favorites.py` | new |
| `features/favorites.feature` + `features/steps/favorites_steps.py` | new |

## 5. Test strategy
| Spec ref | Test type | Test name / scenario |
|---|---|---|
| AC-1 | integration | `test_post_creates_favorite` |
| AC-2 | unit + integration | `test_unique_constraint`, `test_post_twice_is_idempotent` |
| AC-3 | integration | `test_anonymous_gets_403` |
| AC-4 | integration | `test_list_only_shows_own_favorites` |
| AC-5 | integration + Behave | `test_empty_list`, scenario "Empty favorites" |
| AC-6 | integration | `test_delete_removes_favorite_not_recipe` |
| AC-7 | integration | `test_favorite_missing_recipe_404` |
| AC-1, AC-6 | Behave | scenario "Favorite then un-favorite a recipe" |

## 6. Risks & decisions
- DELETE uses the recipe id rather than the favorite id, because the UI knows the recipe, not the favorite.
- Filtering the queryset to `request.user` is what enforces AC-4, so a missing filter would leak
  data. It has its own test.
