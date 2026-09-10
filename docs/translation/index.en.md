# The translation project

The Georgian translation of FiberQ's interface — 306 catalogue strings.

## Status

| | |
|---|---|
| Upstream issue | [vukovicvl/fiberq#43](https://github.com/vukovicvl/fiberq/issues/43) — **open** |
| Catalogue | `fiberq/i18n/fiberq_ka.ts` — **does not exist yet** |
| Drafted | **306 / 306 (100%)** |
| Next step | the maintainer generates the empty `.ts` file |

!!! info "Why we do not create the file ourselves"
    `CONTRIBUTING.md` is explicit: for a new language you open an issue first and the
    **maintainer generates the empty catalogue** — *"you do not need to create the file
    yourself"*. This is a technical requirement, not etiquette: a `.ts` file is produced
    by `pylupdate` from the source, with the right `language` attribute and `<location>`
    references.

## Georgian will be the first real translation

This was a surprise. FiberQ ships two catalogues and **neither is actually translated**:

| File | Strings | Translated |
|---|---:|---:|
| `fiberq_fr.ts` | 306 | **0** |
| `fiberq_sr.ts` | 306 | **3** |

The Serbian file has three test strings filled in. The maintainer is Serbian and has not
translated his own language either — the i18n pipeline is built and waiting for
volunteers.

So we translate **from English**: the `<source>` element is always English, and the `fr`
and `sr` files are byte-identical in that half.

## Catalogue shape

15 contexts, 306 messages, 13 of them `numerus` (counters):

| Context | Strings | numerus |
|---|---:|---:|
| `FiberQPlugin` | 132 | 9 |
| `ValidationRules` | 45 | — |
| `ValidationReport` | 28 | — |
| `ValidationPanel` | 25 | 4 |
| `RoutingUI` | 13 | — |
| `ElementNames` | 12 | — |
| `FiberQ` | 12 | — |
| `ObjectsUI` | 10 | — |
| `DrawingsUI` | 7 | — |
| `CableLayingUI` | 6 | — |
| `DuctingUI` · `SelectionUI` · `SlackUI` | 12 | — |
| `ElementPlacementUI` | 3 | — |
| `QuickToolbar` | 1 | — |

!!! warning "The guide's own table is out of date"
    `docs/TRANSLATING.md` predates v1.4.0. It omits `ElementNames`, `ValidationPanel`,
    `ValidationReport` and `ValidationRules` — **110 strings**, more than a third of the
    catalogue — and names ten placeholders where the catalogue now uses 34. Both reported
    in [issue #43](https://github.com/vukovicvl/fiberq/issues/43).

## What is specific about Georgian

**One plural form.** Georgian has a single CLDR plural form, so all 13 `numerus` messages
show one translation box in Qt Linguist rather than French's two. A noun stays singular
after a numeral: `5 შეცდომა`, never `5 შეცდომები`.

**Case endings on placeholders.** The suffix attaches *outside* the braces:

```
Imported {count} points into layer '{layer}'!
'{layer}' შრეში იმპორტირებულია {count} წერტილი!
```

`{layer}` stays byte-identical; `-ში` sits outside it. This is the most frequent trap.

**No letter case.** English Title Case is not reproduced — Georgian has no capitals.

**Imperatives become verbal nouns.** `ბოძის განთავსება` ("placing of the pole"), not a
true imperative.

## How the work is organised

1. **In batches**, not one large file months from now — see
   [batches and progress](batches.md).
2. **Glossary first.** Terminology is settled once, then applied mechanically.
3. **`<extracomment>` is a primary source.** The "obvious" translation from English alone
   turned out to be wrong several times.
4. **Doubt stays flagged.** `TRANSLATING.md` says it plainly: a flagged gap is more useful
   than a confident wrong term.

[:octicons-arrow-right-24: The three rules](rules.md)
