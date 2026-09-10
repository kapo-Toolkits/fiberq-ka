> **POSTED — 2026-09-09.** This draft was submitted as
> <https://github.com/vukovicvl/fiberq/issues/43> by @ezdanapak.
> The exact text that went up is in `ISSUE-body.md`; it differs from the draft below in
> two ways: the fibre-familiarity answer is *"not familiar with the terminology, but
> fluent in the target language"* and the terminology section says so plainly, and the
> glossary is embedded inline in a `<details>` block rather than attached as a file,
> because the `gh` CLI cannot attach files to an issue.
> Kept here as the record of how the fields were decided.

---

# GitHub issue draft — ready to paste

Open at: <https://github.com/vukovicvl/fiberq/issues/new/choose> → **Translation offer**

The template is a form (`.github/ISSUE_TEMPLATE/translation.yml`), so each block below
maps to one field. Two fields need your decision before posting — marked **[YOU CHOOSE]**.

---

## Title

```
[i18n] Translation for Georgian (ka)
```

*(The template prefills `[i18n] Translation for <language>` — just replace the
placeholder.)*

---

## Field: Language

```
Georgian (ka) — ქართული.

Single script (Mkhedruli), no regional variants: ka_GE is the only locale in
practical use, so one catalogue covers everything. Georgian has one plural form
in Qt/CLDR, so every %n message needs a single numerusform.
```

---

## Field: What would you like to do?

> **Start a brand-new translation for this language**

---

## Field: How familiar are you with fibre optic / FTTH terminology? **[YOU CHOOSE]**

Pick the one that is true — the template says explicitly there is no wrong answer,
and it only tells the maintainer how much terminology support to offer:

- [ ] I work in the field (network design, survey, installation, operations)
- [ ] I work in telecoms but not specifically on fibre plant
- [ ] I have some familiarity — I have used FiberQ or similar GIS/design tools
- [ ] Not familiar with the terminology, but fluent in the target language

---

## Field: How would you prefer to contribute the file?

> **Git clone and pull request — I am comfortable with git**

*(Qt Linguist is already installed here via QGIS — `apps/Qt5/bin/linguist.exe` in
QGIS 3.44 and `apps/qt6/bin/linguist.exe` in QGIS 4.2 — so the editing route is
Qt Linguist and the delivery route is a PR.)*

---

## Field: Terminology notes or questions

```
I have prepared a full English → Georgian glossary draft before starting, in the
same shape as the French and Serbian glossaries in CONTRIBUTING.md — about 120
terms across structures, cables, splicing/slack, elements, architecture,
buildings, CAD drawings, selection, GIS vocabulary and the validation engine. It
is attached to this issue. Happy to have it merged into CONTRIBUTING.md as the
Georgian section, in whatever form suits you.

The <extracomment> translator notes in the catalogue were extremely useful —
several of the decisions below could not have been made without them. Three in
particular changed what I would otherwise have written:

1. "Object" = BUILDING. Georgian QGIS already translates the GIS term "feature"
   as "ობიექტი" (literally "object"). Without the note I would certainly have
   used that word for FiberQ's "Object", which would have been wrong in about
   ten strings. The Georgian catalogue uses "შენობა" (building) for Object and
   keeps "ობიექტი" for Feature.

2. "Route" is the physical alignment on the ground. Georgian has a dedicated
   engineering term for this, "ტრასა", distinct from "მარშრუტი" (a travel
   route), which is what a general translator would reach for.

3. "Drop" as a noun, and "Breakpoint" as a geometry split rather than a fibre
   fault. Both are avoided in Georgian by using terms that cannot be misread as
   the verb or as a cable fault respectively — "Fiber break" is a separate
   string and needs to stay separate.

One question where the English is genuinely ambiguous and I would rather ask
than guess, as TRANSLATING.md advises:

* "List of latent elements" — what does "latent" mean here? Unplaced, pending
  approval, hidden from the map, or something else? I have left it untranslated
  in the glossary until you can confirm.

Two smaller points, no answer needed unless you disagree:

* The quick-toolbar buttons "Aerial Cable" and "Underground Cable" are fixed to
  the backbone subtype in code but the label does not say so. I plan to mirror
  the English's silence rather than add "backbone" in Georgian — tell me if you
  would prefer the label to be explicit.
* "Object" (singular) and "Objects" (plural) are used as titles for the same
  feature in sibling message boxes. Your note already flags this as an
  inconsistency in the English; both will render as the same concept in
  Georgian.
```

---

## Field: Anything else

```
Timescale: I plan to work in batches rather than hold a finished file, in the
order TRANSLATING.md suggests — the toolbar and menu groups first (FiberQ,
ElementNames, CableLayingUI, RoutingUI and the small UI groups, ~75 strings),
then the validation contexts, then FiberQPlugin last.

Credit: [YOU CHOOSE — a name, a GitHub handle, or "no credit please"]

Three small things I noticed while preparing, which are documentation rather
than translation issues. Happy to open them separately, or send a PR, whichever
you prefer:

1. docs/TRANSLATING.md lists ten placeholders. The current catalogue uses 34
   distinct ones — the validation rules added {tol}, {crs}, {fid}, {expected},
   {computed}, {bound}, {allowed}, {layers}, {rules}, {features}, {summary} and
   others.

2. The context table in docs/TRANSLATING.md predates v1.4.0. It omits
   ElementNames (12), ValidationPanel (21), ValidationReport (28) and
   ValidationRules (45) — 106 strings, more than a third of the catalogue — and
   gives FiberQPlugin as 105 where it is now 123. Current totals: 293 messages,
   306 translatable slots, 15 contexts. A translator budgeting their time from
   that table would be planning for roughly two thirds of the real work.

3. fiberq/i18n/__init__.py `_LANGUAGE_NAMES` has no 'ka' entry, so Georgian
   would show up in the language menu as the bare code "ka". The docstring says
   unknown codes fall back to the code deliberately, so nothing breaks — it is
   one line to make it read properly:

       'ka': 'ქართული',

   I can include it in the same PR as the catalogue if you like.
```

---

## Required checkboxes

All three groups are `required: true` in the template — tick every one:

- [x] **Human translation** — I confirm this will be human translation. If I use a
      machine translation engine at all, it will only be as a first draft that I
      review and correct myself.
- [x] **Licence** — I understand my contribution will be released under
      GPL-3.0-or-later, the same licence as the rest of FiberQ.
- [x] **The three rules** — never edit `<source>`; keep placeholders exactly as
      written; submit only the `.ts` file and leave the `.qm` build to the maintainer.

---

## Attachment

Drag `GLOSSARY-ka.md` into the issue comment box before submitting.

## What happens next

Per `CONTRIBUTING.md` § *Starting a brand-new language*: the maintainer generates
the empty `fiberq/i18n/fiberq_ka.ts` and points us at it. **We must not create that
file ourselves.** Once it exists, the pre-translated strings in
`TRANSLATIONS-batch1.md` get typed into Qt Linguist.
