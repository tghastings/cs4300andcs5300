# Spec: Favorite recipes

**Status:** Reviewed
**Author:** Example Student  **Date:** 2026-09-24

> Worked example for a made-up "Recipe Box" app. It shows the level of detail to aim for.

## 1. Problem
Recipe Box users scroll the full recipe list every time they want a recipe they cook often.
They need a quick way to get back to the recipes they like.

## 2. User stories
- **US-1:** As a signed-in user, I want to mark a recipe as a favorite, so that I can find it later.
- **US-2:** As a signed-in user, I want to see only my favorites, so that I don't scroll the full list.
- **US-3:** As a signed-in user, I want to un-favorite a recipe, so that my list stays useful.

## 3. Acceptance criteria

**AC-1 (US-1): Favorite a recipe**
- Given I am signed in and viewing a recipe I have not favorited
- When I favorite it
- Then it appears in my favorites, and the recipe shows as favorited

**AC-2 (US-1): Favoriting twice does nothing extra**
- Given I have already favorited a recipe
- When I favorite it again
- Then it appears in my favorites exactly once, and I get no error

**AC-3 (US-1): Must be signed in**
- Given I am not signed in
- When I try to favorite a recipe
- Then I am refused (API: 401/403; UI: sent to the sign-in page) and nothing is saved

**AC-4 (US-2): Favorites are private**
- Given users A and B have each favorited different recipes
- When A views their favorites
- Then A sees only A's favorites

**AC-5 (US-2): Empty state**
- Given I have no favorites
- When I view my favorites
- Then I see "No favorites yet" and a link to browse recipes (API: an empty list, 200)

**AC-6 (US-3): Un-favorite**
- Given I have favorited a recipe
- When I un-favorite it
- Then it no longer appears in my favorites, and the recipe itself is not deleted

**AC-7 (US-1): Recipe must exist**
- Given no recipe with id 9999 exists
- When I try to favorite recipe 9999
- Then I get "not found" (API: 404) and nothing is saved

## 4. Data
| Thing | Information | Rules |
|---|---|---|
| Favorite | which user, which recipe, when it was favorited | a user can favorite a given recipe only once |

## 5. API / UI behavior
| Action | Input | Success result | Failure result |
|---|---|---|---|
| Favorite | recipe | favorite created (or the existing one kept) | not signed in; recipe not found |
| List my favorites | — | my favorites, newest first | not signed in |
| Un-favorite | recipe | favorite removed | not signed in; not a favorite (404) |

## 6. Out of scope
- Sharing favorites with other users
- Folders or tags for favorites
- A count of how many users favorited a recipe

## 7. Open questions
- [x] Newest-first or alphabetical? → **Newest first** (decided 9/24)
