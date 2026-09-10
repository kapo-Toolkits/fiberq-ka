# Batch 3 — `ValidationReport` (28) + `ValidationPanel` (25)

The two faces of the same validation run: the **panel** is the live results dock inside
QGIS, the **report** is the exported HTML/PDF document. They are done together because
seven strings are word-for-word identical between them, and a user who sees them differ
will assume the two views are showing different things.

Ready to type into Qt Linguist once the maintainer generates `fiberq/i18n/fiberq_ka.ts`.

---

## A note on the counts

An earlier count in this project undercounted two contexts, because `<message numerus="yes">`
does not match a plain `<message>` search. Corrected figures, from `fiberq_fr.ts`:

| Context | Messages | of which numerus |
|---|---:|---:|
| `ValidationPanel` | **25** | 4 |
| `FiberQPlugin` | **132** | 9 |
| everything else | 149 | 0 |
| **Total** | **306** | **13** |

All 306 are untranslated in the French catalogue, so messages and translatable slots are
the same number — there is no separate "slots" figure. A correction has been posted to
[issue #43](https://github.com/vukovicvl/fiberq/issues/43).

---

## `ValidationPanel` (25)

The results dock: a toolbar, three filter combos, a five-column table, and the status
line that summarises the run.

### Summary and status lines

| English | ქართული | Note |
|---|---|---|
| No issues found — {rules} rules ran over {layers} layers, {features} features. | ხარვეზი ვერ მოიძებნა — {rules} წესი გაეშვა {layers} შრეზე, {features} ობიექტზე. | Georgian takes the **singular** after a numeral, so `წესი`/`შრე`/`ობიექტი` stay singular here even though English pluralises. |
| {summary} — showing {shown} of {total} | {summary} — ნაჩვენებია {total}-იდან {shown} | `{total}` moves in front and takes the ablative `-იდან`; `{shown}` follows. All three placeholders present, none renamed. |
| FiberQ validation | FiberQ-ის ვალიდაცია | Dock title. |
| No validation run yet. | ვალიდაცია ჯერ არ გაშვებულა. | Empty state. |
| Validating… | მიმდინარეობს ვალიდაცია… | In-progress state. Ellipsis is U+2026 — kept. |

### Toolbar

| English | ქართული | Note |
|---|---|---|
| Re-run | ხელახლა გაშვება | Button caption — kept short. |
| Validate the project again | პროექტის ხელახლა ვალიდაცია | Tooltip for the button above. |
| Export report… | ანგარიშის ექსპორტი… | Ellipsis kept: it opens a dialog. |
| Save the results as a report | შედეგების ანგარიშად შენახვა | Tooltip for the entry above. |

### Filter labels

| English | ქართული | Note |
|---|---|---|
| Severity: | სიმძიმე: | Trailing colon kept. |
| Layer: | შრე: | |
| Rule: | წესი: | |
| All | ყველა | The "no filter" option in each combo. |

### Table column headers

| English | ქართული | Note |
|---|---|---|
| Severity | სიმძიმე | **Identical to the report's header** — see the consistency table below. |
| Rule | წესი | |
| Layer | შრე | |
| Feature | ობიექტი | The QGIS sense of *feature*, not FiberQ's `Object` (= building). |
| Message | შეტყობინება | |

### Severity values

| English | ქართული | Note |
|---|---|---|
| Error | შეცდომა | |
| Warning | გაფრთხილება | |
| Info | ინფორმაცია | |

### Counts — `numerus` messages (4)

Qt Linguist shows **one** translation box for each of these in a Georgian catalogue,
because Georgian has a single plural form in CLDR. Where French needs two forms and
English writes `(s)`, Georgian needs neither: the noun stays singular after a numeral.

| English | ქართული | Note |
|---|---|---|
| %n error(s) | %n შეცდომა | `%n` is a Qt placeholder — kept exactly, and it is what selects the form. |
| %n warning(s) | %n გაფრთხილება | |
| %n info | %n ინფორმაციული ჩანაწერი | The English is elliptical here (`info`, not `info item(s)`), and a bare `%n ინფორმაცია` does not read as a count in Georgian. `ჩანაწერი` (entry) supplies the missing noun. |
| %n rule(s) failed to run | %n წესი ვერ გაეშვა | |

---

## `ValidationReport` (28)

The exported document. Longer, more formal register than the panel — this is what gets
handed to a client or an authority, which is exactly what one of its strings says.

### Document header

| English | ქართული | Note |
|---|---|---|
| FiberQ validation report | FiberQ-ის ვალიდაციის ანგარიში | Document title. |
| Untitled project | უსახელო პროექტი | Fallback when the QGIS project has no title. |

### Verdict lines

| English | ქართული | Note |
|---|---|---|
| No errors — project is structurally sound | შეცდომები არ არის — პროექტი სტრუქტურულად გამართულია | The pass verdict. |
| Errors found — not ready to hand over | აღმოჩენილია შეცდომები — ჩასაბარებლად მზად არ არის | The fail verdict. "Hand over" is the delivery of the design to the client or authority; Georgian `ჩაბარება` carries exactly that sense, and is the word a designer would use. |

### Totals block

| English | ქართული | Note |
|---|---|---|
| Errors | შეცდომები | Plural here — a column total, not a count after a numeral. |
| Warnings | გაფრთხილებები | |
| Info | ინფორმაცია | |
| Total | სულ | |

### Run metadata

| English | ქართული | Note |
|---|---|---|
| Coordinate system | კოორდინატთა სისტემა | Written out in full here, unlike the terse `CRS` used inside the rule messages — this is a formal document. |
| Schema version | სქემის ვერსია | |
| Plugin version | პლაგინის ვერსია | |
| Run at | გაშვების დრო | Timestamp label. |
| Rules run | გაშვებული წესები | |
| Rules skipped | გამოტოვებული წესები | |
| Run | გაშვება | Section heading for the metadata block above. |
| Rules that failed to run | წესები, რომლებიც ვერ გაეშვა | Relative clause — Georgian cannot compress this the way English does. |

### Issues section

| English | ქართული | Note |
|---|---|---|
| Issues | ხარვეზები | |
| No issues found. | ხარვეზი ვერ მოიძებნა. | Matches the panel's summary line wording. |
| Issues by layer | ხარვეზები შრეების მიხედვით | The breakdown table. |
| Severity | სიმძიმე | |
| Rule | წესი | |
| Layer | შრე | |
| Feature | ობიექტი | |
| Message | შეტყობინება | |
| Error | შეცდომა | |
| Warning | გაფრთხილება | |

### Footer

| English | ქართული | Note |
|---|---|---|
| Generated by the FiberQ QGIS plugin. | შექმნილია FiberQ-ის QGIS პლაგინით. | |
| Machine-readable JSON and CSV of the same run are available from the same export menu. | იმავე გაშვების მანქანურად წაკითხვადი JSON და CSV ხელმისაწვდომია იმავე ექსპორტის მენიუდან. | `JSON` and `CSV` are format names — untranslated. |

---

## Cross-context consistency

These seven strings appear in **both** contexts. Qt keeps them separate entries, so
nothing enforces agreement — but the panel and the report show the same run, and a user
who sees `სიმძიმე` in one and something else in the other will assume they are looking
at different data. Verified identical:

| English | ქართული | Panel | Report |
|---|---|---|---|
| Severity | სიმძიმე | ✓ | ✓ |
| Rule | წესი | ✓ | ✓ |
| Layer | შრე | ✓ | ✓ |
| Feature | ობიექტი | ✓ | ✓ |
| Message | შეტყობინება | ✓ | ✓ |
| Error | შეცდომა | ✓ | ✓ |
| Warning | გაფრთხილება | ✓ | ✓ |

`Info` also appears in both and is `ინფორმაცია` in both — but note the panel's
`%n info` count becomes `%n ინფორმაციული ჩანაწერი`, because a bare noun cannot follow a
numeral there. That is a deliberate divergence, not an inconsistency.

Two further pairs tie this batch to batch 2, where the same concepts were named:

| Concept | Batch 2 (`ValidationRules`) | Batch 3 |
|---|---|---|
| Issue / finding | ხარვეზი | ხარვეზი / ხარვეზები |
| Rule | წესი | წესი |

---

## Self-check against the three rules

- **Rule 1** — no `<source>` touched.
- **Rule 2** — five placeholders in this batch: `{rules}`, `{layers}`, `{features}`
  (one string), `{summary}`, `{shown}`, `{total}` (one string), plus `%n` in the four
  numerus messages. All reproduced exactly; `{total}` and `{shown}` are reordered, which
  Rule 2 permits. Two ellipses (`Export report…`, `Validating…`) preserved as U+2026.
  Three trailing colons (`Severity:`, `Layer:`, `Rule:`) preserved.
- **Rule 3** — nothing compiled.

## Georgian note worth recording

Georgian takes a **singular** noun after any numeral: `5 შეცდომა`, not `5 შეცდომები`.
This is why the four `%n` messages need only one form, and why the count strings differ
grammatically from the totals block in the report, where `Errors`/`Warnings` are plural
column labels with no numeral attached. Both are correct; they are not the same string.

---

## Progress

| Batch | Context(s) | Strings | Status |
|---|---|---:|---|
| 1 | toolbar, menus, element names (11 contexts) | 76 | done |
| 2 | `ValidationRules` | 45 | done |
| 3 | `ValidationReport` + `ValidationPanel` | 53 | done |
| 4 | `FiberQPlugin` | 132 | to do |
| | **Total** | **306** | **174 (57%)** |
