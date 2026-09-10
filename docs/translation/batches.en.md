# Batches and progress

The translation was done in four batches, in the order `docs/TRANSLATING.md` recommends:
what a user sees constantly first, error text last.

## Progress

| Batch | Context(s) | Strings | Status |
|---|---|---:|---|
| 1 | toolbar, menus, element names (11 contexts) | 76 | ✅ |
| 2 | `ValidationRules` | 45 | ✅ |
| 3 | `ValidationReport` + `ValidationPanel` | 53 | ✅ |
| 4 | `FiberQPlugin` | 132 | ✅ |
| | **Total** | **306** | **100%** |

Full tables in the repository:
[batch 1](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch1.md) ·
[batch 2](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch2.md) ·
[batch 3](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch3.md) ·
[batch 4](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch4.md)

---

## What each batch taught

### Batch 1 — terminology is born

This is where the core terms were settled, the ones the other three batches stand on:
`ტრასა` (route), `მუფტა` (joint closure), `მარაგი` (slack), `ბოძი` (pole), `ჭა` (manhole),
`შენობა` (building). Each decision was taken once and then applied mechanically.

**Lesson:** the glossary should exist *before* the translation, not alongside it.

### Batch 2 — the real placeholder test

`ValidationRules` uses 20 distinct placeholders across 30 occurrences. Four strings needed
them reordered, because Georgian syntax demands a different sequence:

```
Cable endpoint is {distance} from {target} -- just outside the {tol} snapping tolerance
კაბელის ბოლო წერტილი {target}-იდან {distance}-ითაა დაშორებული — ეს ოდნავ სცდება
მიბმის დაშვებას ({tol})
```

This batch also established that **database column names are not translated** — `duzina_m`,
`slack_m` and `total_len_m` are Serbian, but they are part of the schema.

### Batch 3 — the counting mistake

My message count silently skipped `<message numerus="yes">` elements. It turned out
`ValidationPanel` is 25 strings (not 21) and `FiberQPlugin` is 132 (not 123). The total is
**306**, not 293.

Because those numbers had already been published in issue #43 — and I had suggested the
maintainer copy them into the documentation — a
[correction was posted](https://github.com/vukovicvl/fiberq/issues/43#issuecomment-5607077915).

**Lesson:** a published number is a commitment.

### Batch 4 — the question I should not have asked

`FiberQPlugin`'s notes contained the answer to a question I had already put to the
maintainer: `List of latent elements`. The `<extracomment>` defined the term precisely.

The cause: when preparing the glossary I read the notes in the UI-group contexts but not
those in `FiberQPlugin`. The
[question was withdrawn](https://github.com/vukovicvl/fiberq/issues/43#issuecomment-5607207314).

**Lesson:** all the notes first, then the questions.

---

## Cross-context duplicates

Nine strings appear in more than one context. Qt stores them as **separate entries**, so
nothing enforces agreement — it has to be checked by hand:

| String | Where |
|---|---|
| `Undo (FiberQ)` | `FiberQ` + `FiberQPlugin` |
| `Preview Map` | `FiberQ` + `FiberQPlugin` |
| `Placing elements` | `ElementPlacementUI` + `FiberQPlugin` |
| `Route correction` | `RoutingUI` + `FiberQPlugin` |
| `Smart selection` | `SelectionUI` + `FiberQPlugin` |
| `Terminal slack` | `SlackUI` + `FiberQPlugin` |
| `Severity` `Rule` `Layer` `Feature` `Message` `Error` `Warning` | `ValidationPanel` + `ValidationReport` |

---

## What remains

- [ ] The maintainer generates `fiberq/i18n/fiberq_ka.ts`
- [ ] Typing the strings into Qt Linguist (which verifies placeholders automatically)
- [ ] A pull request with the `.ts` only
- [ ] Adding `'ka': 'ქართული',` to `_LANGUAGE_NAMES`
- [ ] Settling the `Relations` term with a practitioner
