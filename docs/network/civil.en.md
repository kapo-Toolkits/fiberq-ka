# Civil works

The part that lives in the ground and on the poles — and costs the most.

## Pole

**The support that carries aerial cable.**

- **Georgian:** `ბოძი`
- **Two names in FiberQ:** `Place Pole` (quick toolbar) and `Add pole` (Routing menu) —
  **the same command**, only the English wording differs. Georgian uses `ბოძი` for both.

Elements can be mounted directly on a pole: `Pole OTB`, `Pole TO`.

## Span

**The run between two supports.**

- **Georgian:** `მალი` — the established Georgian engineering term
- **Not** a bridge span, though the word is the same

This term matters for understanding `mid span slack` → [Optical slack](slack.md).

## Manhole

**The underground inspection chamber on a duct run.**

This is where the cable can be reached — for splicing, placing slack, joining a new duct.

- **Georgian:** `საკაბელო ჭა`, short form `ჭა`
- **Not `ლუქი`** — that is only the cover
- **The field says `კოლოდეცი`** (a Russianism); `საკაბელო ჭა` is preferred in writing
- **French:** `chambre de tirage`, and **never** `trou d'homme` — the maintainer notes this
  explicitly

!!! note "Singular and plural"
    FiberQ has both: `Placing manholes` (in the Ducting menu, a multi-step workflow) →
    `ჭების განთავსება`, and `Placing manhole` (placing a single one) → `ჭის განთავსება`.

## Duct / PE pipe

**The buried pipe the cable is pulled through.**

The English uses two words for the same thing — `pipe` in the menu, `duct` everywhere else
in the plugin. The maintainer says plainly: **translate both with one word**.

- **Georgian:** `მილი`
- **Menu entry:** `Place PE pipe` → `PE მილის განთავსება`
- **PE** = polyethylene, Ø 40 mm (the ordinary distribution duct)
- **Capacity:** 1×1 to 3×3 — how many ducts form the bank

## Transition pipe

**The large protective casing (Ø 110 mm) laid where the route crosses under a road, railway
or watercourse.**

The smaller PE ducts are pulled through it.

- **Georgian:** `გადასასვლელის მილი`
- **Material:** PVC, PE, Oki, galvanised steel
- **Not** an adapter between two pipe diameters

!!! info "Where the name comes from"
    "Transition" here translates the legacy Serbian term `prelaz`, which means a
    **crossing**. That is why `გადასასვლელის მილი` ("crossing pipe") was chosen over
    `დამცავი მილი` ("protective pipe") — the second loses the crossing sense.

## Ducting

**The whole duct infrastructure together: manholes plus ducts.**

In FiberQ this is a tool-group label reused three times (button caption, tooltip, status
tip), so the Georgian has to be a single word.

## Trench

**The open excavation where a duct or cable is laid.**

Not a UI string yet; listed here for completeness.
