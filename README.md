# Kitna (कितना)

An on-device tracker for recurring debits in India. It reads the bank and UPI
notifications already on your phone, groups the charges that repeat, and puts
one number on the screen: what this is costing you a year.

**Live prototype → https://sauravkeshari-ship-it.github.io/kitna-prototype/**

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

## Files

| File | Purpose |
|---|---|
| `index.html` | The prototype. Open it directly, no server needed. |
| `artifact.html` | Same page with the document wrapper stripped, for hosts that supply their own. Generated from `index.html` — do not edit by hand. |

## Product scope

Deliberately narrow. No bank linking, no Account Aggregator, no concierge
cancellation, no budgeting. Kitna cannot move money and never asks for a UPI
PIN — it deep-links you to your own UPI app to revoke a mandate.

All figures in the prototype are designed sample data.
