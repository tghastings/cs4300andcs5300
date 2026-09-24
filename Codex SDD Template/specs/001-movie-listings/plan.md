# Plan: Movie listings

**Spec:** [spec.md](spec.md)   **Status:** Approved (worked example)

## 1. Approach
One `Movie` model, a `ModelSerializer`, and a DRF `ModelViewSet` registered on a
`DefaultRouter` at `/api/movies/`. That gives full CRUD with correct status codes and very little
code. The UI is a plain Django view that renders `movie_list.html` from the same model, so the
page and the API always show the same data.
**Rejected:** writing separate `APIView`s for list, create and detail. It's more code, and the
assignment specifically asks for viewsets.

## 2. Data model
| Model | Field | Type | Constraints | Spec ref |
|---|---|---|---|---|
| Movie | title | CharField | max_length=200, required | AC-6 |
| Movie | description | TextField | blank allowed | AC-1 |
| Movie | release_date | DateField | — | AC-3 |
| Movie | duration | PositiveIntegerField | minutes; > 0 (validator) | AC-3, AC-6 |
| Movie | — | `Meta.ordering = ["-release_date"]`, `__str__` returns title | — | Open Q |

## 3. Endpoints / views
| Method | URL | View / ViewSet | Returns | Spec ref |
|---|---|---|---|---|
| GET | `/api/movies/` | MovieViewSet.list | 200 list | AC-4 |
| POST | `/api/movies/` | MovieViewSet.create | 201 / 400 | AC-5, AC-6 |
| GET | `/api/movies/<id>/` | MovieViewSet.retrieve | 200 / 404 | AC-8 |
| PUT/PATCH | `/api/movies/<id>/` | MovieViewSet.update | 200 / 400 / 404 | AC-7 |
| DELETE | `/api/movies/<id>/` | MovieViewSet.destroy | 204 / 404 | AC-7 |
| GET | `/` (named `movie_list`) | `movie_list` view → `movie_list.html` | HTML | AC-1–3 |

## 4. Files to create / change
| File | Change |
|---|---|
| `movie_theater_booking/settings.py` | add `rest_framework`, `bookings` to `INSTALLED_APPS` |
| `movie_theater_booking/urls.py` | include `bookings.urls` |
| `bookings/models.py` | `Movie` |
| `bookings/serializers.py` | `MovieSerializer` (duration > 0 validation) |
| `bookings/views.py` | `MovieViewSet`, `movie_list` |
| `bookings/urls.py` | router + `movie_list` route |
| `bookings/templates/bookings/base.html` | Bootstrap CSS link, navbar, `{% block content %}` |
| `bookings/templates/bookings/movie_list.html` | list + empty state |
| `bookings/tests.py` | model, API and view tests |
| `features/movie_listings.feature`, `features/steps/`, `features/environment.py` | Behave |

## 5. Test strategy
| Spec ref | Test type | Test name / scenario |
|---|---|---|
| AC-1 | Behave | "Browse the movie list" |
| AC-2 | view test + Behave | `test_movie_list_empty_state`, "No movies showing" |
| AC-3 | view test | `test_movie_list_shows_release_date_and_duration` |
| AC-4 | API | `test_list_movies` |
| AC-5 | API | `test_create_movie` |
| AC-6 | API + unit | `test_create_movie_missing_title_400`, `test_create_movie_zero_duration_400` |
| AC-7 | API | `test_update_movie`, `test_delete_movie` |
| AC-8 | API | `test_get_missing_movie_404` |
| AC-9 | view test | `test_movie_list_uses_base_template` (`assertTemplateUsed`) |

## 6. Risks & decisions
- Anyone can create, update or delete movies for now (see Out of scope). Say so in the README.
- `Seat` and `Booking` are left to features 002 and 003. Don't add them here "while we're at it."
