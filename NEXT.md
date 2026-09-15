# Next

## Parked, agreed to build

**1. The notification**
The surface a user sees most often, and the only one that reaches them without
opening the app. Every retention argument rests on it and it does not exist yet.

Needs: lock screen, expanded shade, low-balance warning, price-rise alert. Each
has different urgency and different actions. The constraint that makes it
interesting: *Stop it* cannot be an action, because Snip cannot stop anything.
So the actions have to be honest, something like *Remind me after* or *Open*.

**2. Home screen widget**
Snip gets opened monthly at best. A 4x1 with the annual number, the next charge
and its date turns a monthly app into a daily glance. Cheap to design.

**3. How Snip makes money**
No pricing anywhere in 40 screens. It shapes onboarding, the value story and
the permission ask, so it cannot be bolted on later.

The awkward part: a subscription tracker that charges a subscription is a joke
people will make in the first review. With no server and no account, a one-time
unlock is cheaper to run and thematically right. Decide before more visual work.

## Second tier

- **Shared subscriptions.** Snip assumes every charge is yours. Netflix split
  with a sibling changes Rs 7,788 to Rs 2,596 and changes the verdict with it.
- **Annual renewal runway.** Prime at Rs 1,499 hits once and is forgotten for
  eleven months. The 7-day view is useless for those; they need 30 days.
- **The no-permission path.** Declining notification access currently leads to
  one manual-entry screen. A real share of users will decline an unknown app
  reading their messages, so that is a dead end rather than a product.
- **Year in review.** "You cut Rs 34,000 this year" is what makes someone keep
  the app, and gives it a reason to reach out once a year that is not a nag.

## Decisions to record, not build

| | Where it stands |
|---|---|
| Dark mode | Deliberately skipped. Airbnb ships none, and the preference is light. Android users expect it, so this should stay a written decision |
| Hindi | The app is for India and the UI is English. Devanagari went with the rename. A language toggle is a real question |
| Accessibility | Font scaling, TalkBack labels and the 44px touch target rule are unchecked |
| Motion | Screen transitions undefined. Only the splash has specified motion |

## Deliberate departures from the Airbnb spec

Three so far, all considered, none of them drift:

1. Section headings 18px/600, where the spec says 22px/500
2. Inter standing in for Airbnb Cereal VF, which is proprietary
3. Canvas warmed from #ffffff to #fdfbf4
