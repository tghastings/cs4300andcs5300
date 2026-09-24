# Spec: Booking history

**Status:** Draft: **you finish this spec**
**Author:** <your name>  **Date:** <YYYY-MM-DD>

> The user stories and first criteria are started for you. Every `TODO` is a decision **you** make.

## 1. Problem
Moviegoers need to see what they've booked. (HW2 §1 "Check their booking history via the API";
§3.3 `BookingViewSet` "for users to book seats and view their booking history"; §3.5
`/api/bookings/`; template `booking_history.html`.)

## 2. User stories
- **US-1:** As a moviegoer, I want to see a list of my bookings, so that I know what I've reserved.
- **US-2:** As an API client, I want to view booking history and create bookings through `/api/bookings/`.
- TODO: anything else?

## 3. Acceptance criteria

**AC-1 (US-1): See my bookings**
- Given I am signed in and have booked seat A1 for "Dune"
- When I open My Bookings
- Then I see Dune, seat A1 and the booking date

**AC-2 (US-1): Only my bookings**
- Given users Sam and Alex each have bookings
- When Sam opens My Bookings, or sends `GET /api/bookings/`
- Then TODO: whose bookings appear?

- TODO **AC-3:** Empty state: what does a user with no bookings see?
- TODO **AC-4:** Not signed in: page behavior and API status code.
- TODO **AC-5:** Creating a booking with `POST /api/bookings/`: success, and a seat that's already taken.
  (How does this relate to booking in 002? Avoid building the same rule twice.)
- TODO **AC-6:** Order of the list.

## 4. Data
| Thing | Information | Rules |
|---|---|---|
| Booking | movie, seat, user, booking date | TODO |

## 5. API / UI behavior
| Action | Input | Success result | Failure result |
|---|---|---|---|
| My Bookings page | — | TODO | TODO |
| List bookings (API) | — | TODO | TODO |
| Create booking (API) | TODO | TODO | TODO |

## 6. Out of scope
- TODO

## 7. Open questions
- [ ] Should a user ever be able to see another user's bookings through the API? Why is this a
      **security** question, not just a feature question?
- [ ] TODO
