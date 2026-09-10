> **POSTED — 2026-09-09** as https://github.com/vukovicvl/fiberq/issues/43#issuecomment-5607207314

---

Two things: withdrawing the question I asked, and a status update.

## Withdrawing the `latent elements` question

I asked what "latent" means in `List of latent elements`. **You had already answered it in
the catalogue** — the string carries an `<extracomment>` defining a latent element as a
passive optical element sitting on a cable's path at a recorded distance along it, between
the cable's two endpoints; recorded as data rather than drawn as a separate map feature;
"latent" = intermediate/pass-through, not faulty or dormant.

My mistake: when I prepared the glossary I had read the translator notes in the UI-group
contexts but not yet those in `FiberQPlugin`, which is where that string lives. Sorry for
making you read a question you had already answered in writing.

Georgian: **`შუალედური ელემენტი`** — "intermediate element". It shares its adjective with
`შუალედური მარაგი` (mid span slack), which I think is right rather than a collision: both
are things recorded at an intermediate point along a cable rather than at its ends, so the
shared word makes the model more legible.

For what it is worth, those notes did a lot of work. `Object` = building, `Drop` as a noun,
`Cut infrastructure` as geometry editing rather than a fault, `Color catalog` as the fibre
colour code rather than a symbology palette, `Branch` as a cable junction, `Relations` as
end-to-end optical links rather than QGIS layer relations — I would have got several of
those wrong from the English alone, and a couple of them wrong in ways nobody reviewing
the Georgian would have caught.

## Status: all 306 strings drafted

| Context(s) | Strings | |
|---|---:|---|
| `FiberQ`, `ElementNames`, `CableLayingUI`, `RoutingUI`, `ObjectsUI`, `DrawingsUI`, `SlackUI`, `DuctingUI`, `SelectionUI`, `ElementPlacementUI`, `QuickToolbar` | 76 | drafted |
| `ValidationRules` | 45 | drafted |
| `ValidationReport` + `ValidationPanel` | 53 | drafted |
| `FiberQPlugin` | 132 | drafted |
| **Total** | **306** | **100%** |

Everything is drafted against the English in `fiberq_fr.ts`, with the placeholder,
line-break and ellipsis handling worked out per string. Once you generate
`fiberq/i18n/fiberq_ka.ts` it is a typing exercise in Qt Linguist, which will verify every
placeholder as I go, and then a PR with the `.ts` only.

## One terminology question left

`Relations` (the toolbar button opening "Optical relations management"). Your note defines
it precisely, so the concept is clear; what I am unsure of is which Georgian term the trade
actually uses for a named end-to-end optical link — `ოპტიკური კავშირი` (optical link) or
`ოპტიკური მიმართულება` (optical direction). I have drafted the first. This is the one
place where I would genuinely rather a Georgian fibre engineer decided, so I will leave it
flagged in the glossary and it can be corrected later without touching anything else.

## One small consistency item in the English

Not a translation problem, and no action needed unless you want it: the catalogue mixes
two ellipsis characters. `Export selected...` and `Export all...` use three ASCII full
stops; `Recalculate lengths…`, `Add drawing…`, `Export report…` and `Validating…` use
U+2026. Qt Linguist does not flag it, since it is not a placeholder, and translations just
copy whatever the source has — so it is cosmetic. Mentioning it only because the rest of
the catalogue is unusually consistent about Qt conventions.
