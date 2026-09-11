# Snip

**Find all your subscriptions in one place.**
And see what each one costs you a year, not a month.

*(prototype folder still named kitna-prototype, from the working name)*

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

## Worth it? Per-use comparison

Snip already reads every debit, not only the recurring ones. v2 spends that on
the job it already has rather than on a general expense ledger.

Every figure on a card is one of three kinds, and the card says which:

- **Seen in your debits** — order count, amounts, totals, cost per order
- **Usage access** — days opened, last opened
- **Published rate** — a small price list Snip ships and dates

Nothing is inferred silently. Where the answer depends on something this phone
cannot see, the card says **potential saving** and asks you.

| Verdict | Example | Why |
|---|---|---|
| Certain saving | Cult.fit, Rs 15,000/yr | Rs 3,750 paid in 90 days, zero opens. Stopping a charge you can see saves exactly that. |
| Potential saving | Amazon Prime, up to Rs 699/yr | 6 of your 11 orders were over Rs 499, where delivery is free anyway |
| Potential saving | Netflix, up to Rs 1,800/yr | Rs 649 matches Premium. Snip cannot see how many screens you use. |
| Earning its keep | Swiggy One | Rs 13 an order against a fee that usually runs Rs 35 to Rs 60 |

Rs 15,000 is certain. Rs 8,475 is possible and openly marked as resting on your
answer.

This deliberately is **not** an expense tracker. No categories, no budgets, no
monthly report, nothing for the user to maintain. That category is a commodity
in India and it is what killed Walnut.

## Help and feedback

There is no account and no server, so support cannot look you up. It is built
around that instead of fighting it:

- **Help** — six common problems answered on the phone, each with steps
- **Report a problem** — category, description, optional diagnostic
- **What gets sent** — the full payload shown in plain text before it goes. No
  amounts, no bank names, no account numbers, no merchants, no message text.
  Only the *shape* of a message Snip failed to read, labelled `AXIS-01 x5`
- **Suggest something** — one sentence, plus how much it matters
- **This charge is wrong** — five corrections from any charge. Stays on the
  phone and teaches the parser

## Identity

The mark is a subscription drawn as what it is: a loop
that repeats until somebody stops it. A ring with one arc cut free and sprung
slightly clear of the gap.

Two arcs of one circle, radius 15 on a 48 grid, stroke 6.4, round caps. Drawn
with `currentColor` so it takes the colour of whatever it sits beside. No
scissors, no rupee sign, no palette of its own.

Full sheet, including construction, app icon, lockups, size tests down to 16px
and misuse: `snip-identity.html`

Not yet checked: trademark, Play Store name availability, domain.

## Files

| File | Purpose |
|---|---|
| `index.html` | v1 prototype. Open it directly, no server needed. |
| `v2.html` | v2 prototype, 23 screens. Current version. |
| `artifact.html`, `v2-artifact.html` | Same pages with the document wrapper stripped, for hosts that supply their own. Generated — do not edit by hand. |

## Product scope

Deliberately narrow. No bank linking, no Account Aggregator, no concierge
cancellation, no budgeting. Snip cannot move money and never asks for a UPI
PIN — it deep-links you to your own UPI app to revoke a mandate.

All figures in the prototype are designed sample data.
