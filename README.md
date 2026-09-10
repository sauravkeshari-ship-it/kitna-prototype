# Kitna (कितना)

An on-device tracker for recurring debits in India. It reads the bank and UPI
notifications already on your phone, groups the charges that repeat, and puts
one number on the screen: what this is costing you a year.

**Live**
- **v2 (current)** → https://sauravkeshari-ship-it.github.io/kitna-prototype/v2.html
- v1 → https://sauravkeshari-ship-it.github.io/kitna-prototype/

## Why now

On 21 April 2026 the RBI's Digital Payments E-mandate Framework removed the OTP
requirement on recurring debits up to Rs 15,000. UPI Autopay was already running
roughly 926M transactions a month across the top 10 banks. India just lost the
last signal that told people money was leaving.

## What this is

A clickable HTML prototype. 19 screens, no build step, no dependencies beyond
two Google Fonts and the brand icons.

- **Getting in** — welcome, three education screens, name and mobile, OTP,
  the permission ask, and the notification scan
- **Home** — three states: loaded, just a few mandates, and empty
- **Upcoming** — grouped by date, with a balance warning
- **Idle** — what you pay for and never open
- **Detail** — evidence first, then the kill switch
- **Settings** — including full notification controls

Every toggle, chip and disclosure works. On a phone it runs full-screen; on
desktop it renders inside a device frame with a screen picker.

## Design

Built on the Airbnb design system. Rausch `#ff385c` is reserved for primary
actions and the active tab; Ink Black `#222222` carries everything else. Idle
mandates use Plus Magenta `#92174d`, deliberate spends use Luxe Purple
`#460479`. Airbnb Cereal VF is proprietary, so this uses Inter with -0.01em
tracking at display sizes — the substitute Airbnb's own spec names.

## v2: only claim what you can prove

v1 flagged three subscriptions as idle based on app opens. That logic is wrong
for most categories, and v2 fixes it.

Every subscription is graded on whether this phone can actually observe it
being used:

| Tier | Meaning | Example |
|---|---|---|
| `direct` | You open the app to use the service, so app opens are a fair proxy | Cult.fit, Swiggy |
| `multi` | Also runs on TVs, laptops, cars, speakers. Silence here proves nothing | Netflix, Audible, JioHotstar |
| `passive` | Always-on, or has no app to open at all. There is no signal | iCloud+, Airtel, insurance, SIP |

Only `direct` is ever called unused. `multi` gets a softer claim and a one-tap
"I use this elsewhere". `passive` is never flagged, because calling iCloud+
dead weight for not being opened would simply be wrong.

The visible effect: v1 claimed Rs 20,976 of waste. v2 claims Rs 15,000 and says
plainly that it cannot vouch for the other Rs 5,976.

Usage access is also demoted to an optional, skippable, second permission with
its limits stated on the screen. The app works without it.

## Files

| File | Purpose |
|---|---|
| `index.html` | v1 prototype. Open it directly, no server needed. |
| `v2.html` | v2 prototype, 23 screens. Current version. |
| `artifact.html`, `v2-artifact.html` | Same pages with the document wrapper stripped, for hosts that supply their own. Generated — do not edit by hand. |

## Product scope

Deliberately narrow. No bank linking, no Account Aggregator, no concierge
cancellation, no budgeting. Kitna cannot move money and never asks for a UPI
PIN — it deep-links you to your own UPI app to revoke a mandate.

All figures in the prototype are designed sample data.
