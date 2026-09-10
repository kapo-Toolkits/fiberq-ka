# Cables and fibre

## Fibre

**Optical fibre** — the glass strand carrying data as pulses of light. A cable holds many
fibres, grouped into tubes.

| English | Georgian |
|---|---|
| `Fiber`, `optical fiber` | **ოპტიკური ბოჭკო**, short **ბოჭკო** |
| `Capacity` | **ტევადობა** — how many fibres a cable holds |

## Colour code

**`Color catalog` is not a colour palette.**

This was one of my more useful discoveries. In a QGIS context the button label
`Color catalog` reads naturally as picking symbology colours — but the maintainer's note
is unambiguous:

> the FIBRE COLOUR CODE: the standard sequence of colours identifying each tube and each
> fibre within a cable (e.g. the TIA-598 or IEC ordering). This is industry cable
> terminology — it is NOT a QGIS symbology palette or a map-styling colour picker.

So it is the **fibre colour code** — the standard sequence identifying every tube and every
fibre in a cable. Standards: **TIA-598**, **IEC**.

- **Georgian:** `ბოჭკოს ფერთა კოდი`
- **Rejected:** `ფერების კატალოგი` — it invites precisely the misreading the note warns
  against

!!! question "To check"
    Which standard does FiberQ actually use — TIA-598 or IEC? I have not read the code for
    this yet. Noted in the [journal](../journal.md).

## Splicing

| English | Georgian | What it is |
|---|---|---|
| `Splice` | **შედუღება** | The fusion weld between two fibres (fr `soudure`) |
| `Joint closure` | **ოპტიკური მუფტა** | The enclosure where splicing happens |

## Two kinds of "break" that must not merge

This is one of FiberQ's most delicate spots. English calls all three "break" or "cut";
Georgian has to keep them apart:

| String | Georgian | What it actually is |
|---|---|---|
| `Add breakpoint` | **გაყოფის წერტილის დამატება** | **Geometry operation** — splits a route line in two at the clicked point |
| `Cut infrastructure` | **ინფრასტრუქტურის გაჭრა** | **Geometry operation** — splits a line feature in two |
| `Fiber break` | **ბოჭკოს გაწყვეტა** | **A real fault** — the point where a fibre is severed |

The first two are editing; the third is an outage. The maintainer wrote a separate note for
each, precisely because this confusion is typical.

!!! example "How Georgian separates them"
    `გაყოფა` (split) and `გაჭრა` (cut) are editing; `გაწყვეტა` (severance) is damage. The
    word `წყვეტა` was deliberately kept out of the first two so all three do not converge.

## Capacity and ducts

Underground, a cable sits in a duct. FiberQ's PE pipe dialog offers capacities from
**1×1 to 3×3** — how many ducts make up the duct bank.

[:octicons-arrow-right-24: Civil works](civil.md)
