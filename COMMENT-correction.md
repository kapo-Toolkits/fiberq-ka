> **POSTED — 2026-09-09** as https://github.com/vukovicvl/fiberq/issues/43#issuecomment-5607077915

---

A correction to the string counts in my opening comment — they were undercounted, and
since one of my suggestions was that you fix the table in `docs/TRANSLATING.md`, I would
rather you not copy my wrong numbers into it.

I counted `<message>` elements with a plain text search, which silently skips
`<message numerus="yes">`. Two contexts were affected. Corrected, from the current
`fiberq_fr.ts`:

| Context | I said | Actually | of which `numerus` |
|---|---:|---:|---:|
| `ValidationPanel` | 21 | **25** | 4 |
| `FiberQPlugin` | 123 | **132** | 9 |
| `ValidationReport` | 28 | 28 | 0 |
| `ValidationRules` | 45 | 45 | 0 |
| `ElementNames` | 12 | 12 | 0 |
| everything else | — | 124 | 0 |
| **Total** | 293 / 306 | **306** | **13** |

Two things follow from that:

1. **There is no separate "slots" figure.** I reported "293 messages / 306 slots". In
   fact there are 306 messages and 306 `type="unfinished"` slots — the 13 numerus
   messages carry a single `<numerusform>` each in this catalogue, so the two numbers are
   the same. My distinction was an artefact of the bad count, not a real one.

2. **The gap in the `docs/TRANSLATING.md` table is 110 strings, not 106** —
   `ElementNames` (12), `ValidationPanel` (25), `ValidationReport` (28) and
   `ValidationRules` (45) are absent, and `FiberQPlugin` is listed as 105 against an
   actual 132. So the table accounts for 196 of 306 strings, or 64%.

Progress against the corrected total: 174 of 306 (57%). `FiberQPlugin` (132) is all that
is left.

One thing the recount made concrete, which may be worth a line in the guide for future
translators: **Georgian has a single CLDR plural form**, so all 13 numerus messages show
one translation box rather than French's two, and the noun stays singular after a
numeral (`5 შეცდომა`, never `5 შეცდომები`). Turkish, Japanese, Korean, Vietnamese and
Chinese behave the same way. A translator coming from `TRANSLATING.md`'s French examples
might reasonably expect to be filling in two boxes and wonder what is wrong.

Apologies for the noise.
