# Spec: Movie listings

**Status:** Reviewed (worked example: change anything you'd do differently)
**Author:** <your name>  **Date:** <YYYY-MM-DD>

## 1. Problem
Moviegoers need to see what's showing before they can book a seat. Staff need to add, update
and remove movies. (HW2 §1 and §3.3: "View movie listings", `MovieViewSet` "for CRUD operations".)

## 2. User stories
- **US-1:** As a moviegoer, I want to see a list of movies, so that I can pick one to watch.
- **US-2:** As a moviegoer, I want to see a movie's details (description, release date,
  duration), so that I can decide whether to watch it.
- **US-3:** As an API client, I want to create, read, update and delete movies, so that the
  listings can be managed.

## 3. Acceptance criteria

**AC-1 (US-1): List movies in the UI**
- Given the movies "Dune" and "Up" exist
- When I open the movie list page
- Then I see both titles, each with its description and a "Book Now" button

**AC-2 (US-1): Empty state**
- Given no movies exist
- When I open the movie list page
- Then I see "No movies are showing right now" instead of an empty list

**AC-3 (US-2): Movie details shown**
- Given "Dune" has a release date of 2021-10-22 and a duration of 155 minutes
- When I view the movie list
- Then Dune's release date and duration are shown in a readable format

**AC-4 (US-3): List via API**
- Given two movies exist
- When a client sends `GET /api/movies/`
- Then the response is 200 with a JSON list of 2 movies, each with id, title, description,
  release date and duration

**AC-5 (US-3): Create via API**
- Given valid movie data
- When a client sends `POST /api/movies/`
- Then the response is 201 and the movie appears in `GET /api/movies/`

**AC-6 (US-3): Reject invalid data**
- Given movie data with a missing title, or a duration of 0 or less
- When a client sends `POST /api/movies/`
- Then the response is 400 with an error for that field, and nothing is saved

**AC-7 (US-3): Update and delete**
- Given a movie exists
- When a client sends `PUT`/`PATCH /api/movies/<id>/`, then `DELETE /api/movies/<id>/`
- Then the update returns 200 with the new values, the delete returns 204, and the movie is gone

**AC-8 (US-3): Missing movie**
- Given no movie with id 9999 exists
- When a client sends `GET /api/movies/9999/`
- Then the response is 404

**AC-9 (UI): Consistent, responsive layout**
- Given any page in the app
- When it renders
- Then it extends `base.html` (Bootstrap), with a navbar linking to Movies and My Bookings

## 4. Data
| Thing | Information | Rules |
|---|---|---|
| Movie | title, description, release date, duration | title required (max 200 characters); duration in minutes, > 0; release date is a date |

## 5. API / UI behavior
| Action | Input | Success result | Failure result |
|---|---|---|---|
| View movie list page | — | page with every movie and a "Book Now" button | — |
| List movies (API) | — | 200, list | — |
| Get one movie (API) | id | 200, movie | 404 |
| Create movie (API) | title, description, release date, duration | 201, movie | 400 + field errors |
| Update movie (API) | id + fields | 200, movie | 400 / 404 |
| Delete movie (API) | id | 204 | 404 |

## 6. Out of scope
- Showtimes, theaters, posters, ratings, search
- Restricting movie create/update/delete to staff (a decision to note in the README; revisit if time allows)

## 7. Open questions
- [x] Duration in minutes or as `HH:MM`? → **Integer minutes.** Simpler to validate and test.
- [x] Order of the list? → **By release date, newest first.**
