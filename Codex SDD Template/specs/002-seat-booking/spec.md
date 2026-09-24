# Spec: Seat booking

**Status:** Draft: **you finish this spec**
**Author:** <your name>  **Date:** <YYYY-MM-DD>

> The user stories and first criteria are started for you. Every `TODO` is a decision **you**
> make. Compare with `001-movie-listings/spec.md` for the level of detail to aim for.

## 1. Problem
A moviegoer who has picked a movie needs to see which seats are free and reserve one.
(HW2 §1 "Book seats via the API"; §3.3 `SeatViewSet` "for seat availability and booking";
§3.5 `/api/seats/`; template `seat_booking.html`.)

## 2. User stories
- **US-1:** As a moviegoer, I want to see which seats are available for a movie, so that I can choose one.
- **US-2:** As a moviegoer, I want to book an available seat, so that it's reserved for me.
- **US-3:** As an API client, I want to check seat availability and book seats through `/api/seats/`.
- TODO: anything else? (For example, can a moviegoer book more than one seat at a time?)

## 3. Acceptance criteria

**AC-1 (US-1): Seat availability page**
- Given the movie "Dune" and seats A1–A5, where A2 is already booked
- When I click "Book Now" for Dune
- Then I see the seat booking page for Dune, with A2 shown as unavailable and the others as available

**AC-2 (US-2): Book an available seat**
- Given I am signed in and seat A1 is available for Dune
- When I book A1
- Then TODO: what does the user see, and what changes in the data?

**AC-3 (US-2): Seat already taken**
- Given seat A2 is already booked for Dune
- When I try to book A2
- Then TODO: what happens in the UI? What status code does the API return?

- TODO **AC-4:** What if the user isn't signed in?
- TODO **AC-5:** What if the seat or movie doesn't exist?
- TODO **AC-6+:** API criteria for `/api/seats/`: list, availability, booking.

## 4. Data
| Thing | Information | Rules |
|---|---|---|
| Seat | seat number, booking status | TODO: is the seat number unique? What format? |
| Booking | movie, seat, user, booking date | TODO: what stops two bookings of the same seat? |

## 5. API / UI behavior
| Action | Input | Success result | Failure result |
|---|---|---|---|
| View seats for a movie (page) | movie | TODO | TODO |
| List seats (API) | TODO | TODO | TODO |
| Book a seat (API + page) | TODO | TODO | TODO |

## 6. Out of scope
- TODO: e.g., payments, seat maps with rows and aisles, holding a seat for 10 minutes

## 7. Open questions
- [ ] **The assignment's Seat model has no movie field.** Is a seat booked for *every* movie, or
      is availability per movie? How do the Seat and Booking models together answer that? Decide,
      and write down why.
- [ ] Can a booking be cancelled? If so, does that belong in this feature or in 003?
- [ ] TODO
