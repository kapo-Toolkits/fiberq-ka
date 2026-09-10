# Batch 1 — toolbar, menus and element names

**76 strings** across 11 contexts. This is everything a FiberQ user sees on screen
constantly, and it is the order `docs/TRANSLATING.md` recommends starting in.

Ready to type into Qt Linguist once the maintainer generates `fiberq/i18n/fiberq_ka.ts`.
Workflow per string: select → paste the Georgian → **Ctrl+Enter** (marks done, advances
to the next unfinished) → **Ctrl+S** at the end. Never *File → Release*.

Terms follow [`GLOSSARY-ka.md`](GLOSSARY-ka.md). Where a translation is not a literal
rendering, the reason is in the third column.

Remaining after this batch: `FiberQPlugin` (123), `ValidationRules` (45),
`ValidationReport` (28), `ValidationPanel` (21) = 230 strings.

---

## `FiberQ` — quick toolbar (12)

| English | ქართული | Note |
|---|---|---|
| FiberQ – Preview Map | FiberQ – წინასწარი დათვალიერების რუკა | Window title. En-dash kept as in the source. |
| Error opening the preview map:⏎{details} | წინასწარი დათვალიერების რუკის გახსნის შეცდომა:⏎{details} | ⏎ is a real line break in the file — keep it. |
| Place Pole | ბოძის განთავსება | Same command as `Add pole` in the Routing menu; only the English wording differs. |
| Place Manhole | ჭის განთავსება | Short form of `საკაბელო ჭა` — this is a button caption. |
| Create Route | ტრასის შექმნა | Identical to `Create route` (Routing menu); the English differs only in capitalisation, which Georgian does not have. |
| Aerial Cable | საჰაერო კაბელი | Fixed to the backbone subtype in code; the label mirrors the English's silence about that. |
| Underground Cable | მიწისქვეშა კაბელი | Same. |
| Place ODF | ODF-ის განთავსება | Case suffix attaches to the acronym with a hyphen. |
| Place OTB | OTB-ის განთავსება | |
| Place TO | TO-ს განთავსება | `TO` ends in a vowel, so the genitive is `-ს`, not `-ის`. |
| Optical Slack | ოპტიკური მარაგი | Singular here; the Slack menu uses the plural for the same group. |
| Undo (FiberQ) | გაუქმება (FiberQ) | Brackets and product name kept: this is a separate history from QGIS's own undo. |

## `ElementNames` (12)

| English | ქართული | Note |
|---|---|---|
| ODF | ODF | Acronym kept; it doubles as the layer name. |
| TB | TB | Terminal Box. No established Georgian acronym. |
| Patch panel | პაჩ-პანელი | Kept clearly distinct from ODF, whose scope overlaps. |
| OTB | OTB | |
| Indoor OTB | შიდა OTB | |
| Outdoor OTB | გარე OTB | |
| Pole OTB | ბოძის OTB | One element (an OTB mounted on a pole), not a pole plus a box. |
| TO | TO | **Acronym, not the preposition "to".** |
| Indoor TO | შიდა TO | |
| Outdoor TO | გარე TO | |
| Pole TO | ბოძის TO | |
| Joint Closure TO | TO მუფტაში | A TO housed inside a joint closure — matches sr `TO Izvod u nastavku`. |

## `CableLayingUI` (6)

| English | ქართული | Note |
|---|---|---|
| Cable laying | კაბელის გაყვანა | Reused 4× (menu title, button label, tooltip, status tip) — must stay this short. |
| Underground | მიწისქვეშა | Submenu title, adjective. |
| Backbone | მაგისტრალური | Appears under **both** `მიწისქვეშა` and `საჰაერო`; one translation serves both parents. The concept noun is `მაგისტრალი`; the menu uses the adjective to match `გამანაწილებელი` and `აბონენტური`. |
| Distribution | გამანაწილებელი | Same. |
| Drop | აბონენტური | Same. Noun in English, rendered as an adjective so the three classes read as a parallel set. Never the verb. |
| Aerial | საჰაერო | |

## `RoutingUI` (13)

| English | ქართული | Note |
|---|---|---|
| Add pole | ბოძის დამატება | Same command as `Place Pole`; both use `ბოძი`. |
| Create route | ტრასის შექმნა | Builds the line from the **selected** poles/manholes. |
| Merge selected routes | მონიშნული ტრასების შერწყმა | |
| Import route from file | ტრასის იმპორტი ფაილიდან | A file on disk, not a QGIS project. |
| Add breakpoint | გაყოფის წერტილის დამატება | Splits a route line in two. **Not** a fibre fault — `წყვეტა` deliberately avoided. |
| Create a route manually | ტრასის ხელით შექმნა | Contrasts with `Create route`, which derives the line automatically. |
| Change route type | ტრასის ტიპის შეცვლა | Edits the attribute only; geometry untouched. |
| Route correction | ტრასის კორექცია | Menu entry **and** the dialog title. |
| Routing | ტრასირება | Reused 3×; toolbar-width. |
| Choose GeoPackage file for auto-save | აირჩიეთ GeoPackage ფაილი ავტოშენახვისთვის | File-save dialog title. Format name untranslated. |
| Auto GPKG | ავტო GPKG | Message-bar heading, reused for both the on and the off message. |
| Autosave on GeoPackage. | ავტოშენახვა GeoPackage-ში ჩართულია. | The English "on GeoPackage" means autosaving is now **enabled**, per the translator note — rendered by meaning, not word for word. |
| Autosave off. | ავტოშენახვა გამორთულია. | |

## `ElementPlacementUI` (3)

| English | ქართული | Note |
|---|---|---|
| Place Joint Closure | მუფტის განთავსება | |
| Place {name} | განთავსება: {name} | Article-free construction, exactly as the translator note recommends for gendered languages — one label serves every element type. `{name}` is translated separately in `ElementNames`; do not translate it here. |
| Placing elements | ელემენტების განთავსება | Gerund naming the whole group; reused as label, tooltip and status tip. |

## `SlackUI` (4)

| English | ქართული | Note |
|---|---|---|
| Place terminal slack (interactive) | საბოლოო მარაგის განთავსება (ინტერაქტიული) | Slack at a cable **end** (C coil). |
| Place mid span slack (interactive) | შუალედური მარაგის განთავსება (ინტერაქტიული) | Slack where the cable runs **through** uncut (S coil). `შუალედური` vs `საბოლოო` keeps the two slack types unmistakably apart. |
| Generate terminal slacks at the ends of selected cables | საბოლოო მარაგების გენერირება მონიშნული კაბელების ბოლოებზე | Batch counterpart: both endpoints of every selected cable at once. Long, but it is a menu entry only — no width limit. |
| Optical slacks | ოპტიკური მარაგები | Plural: names the tool group and the map layer. Hover text only. |

## `DuctingUI` (4)

| English | ქართული | Note |
|---|---|---|
| Placing manholes | ჭების განთავსება | Gerund, plural — a multi-step workflow, not a single click. |
| Place PE pipe | PE მილის განთავსება | `PE` = polyethylene, kept. The rest of the app calls this a *duct*; Georgian uses `მილი` for both. |
| Place transition pipe | გადასასვლელის მილის განთავსება | The protective casing at a road/rail/water crossing. Not an adapter between pipe sizes. |
| Ducting | მილგაყვანილობა | Reused 3×; toolbar-width. |

## `SelectionUI` (4)

| English | ქართული | Note |
|---|---|---|
| Smart selection (Multiple Layers) | ჭკვიანი მონიშვნა (რამდენიმე შრე) | Brackets kept. |
| Clear selection | მონიშვნის მოხსნა | **Non-destructive** — `მოხსნა` (remove/lift). |
| Delete selected | მონიშნულის წაშლა | **Destructive** — `წაშლა` (delete). Sits directly below the entry above, so the two must not be confusable. |
| Selection | მონიშვნა | Reused 3×; toolbar-width. |

## `DrawingsUI` (7)

| English | ქართული | Note |
|---|---|---|
| Drawings | ნახაზები | External CAD files linked to elements — documents, not something drawn in QGIS. Reused 4×. |
| Add drawing… | ნახაზის დამატება… | Trailing `…` is U+2026, Qt's "opens a dialog" convention — kept. |
| Link a DWG/DXF drawing to selected element(s) | DWG/DXF ნახაზის მიბმა მონიშნულ ელემენტ(ებ)თან | Georgian handles the optional plural naturally with `ელემენტ(ებ)თან`. |
| Open drawing (by click) | ნახაზის გახსნა (დაწკაპუნებით) | Opens the CAD file in the system's default application. |
| Click on an element to open its linked drawing | დააწკაპუნეთ ელემენტზე მასზე მიბმული ნახაზის გასახსნელად | Full instructional sentence. |
| Clear drawing from element | ნახაზის მოხსნა ელემენტიდან | Unlinks only. |
| Unlink drawing from selected element(s) | ნახაზის მიბმის მოხსნა მონიშნული ელემენტ(ებ)იდან | Tooltip confirming nothing is deleted — neither the file on disk nor the element. |

## `ObjectsUI` (10)

> Every `Object` here means a **building**. See §6 of the glossary.

| English | ქართული | Note |
|---|---|---|
| Object in 3 points | შენობა 3 წერტილით | The 4th corner of the rectangle is derived. |
| Object in N points | შენობა N წერტილით | `N` kept as the Latin letter — the mathematical placeholder for "any number". |
| Object in N points (90°) | შენობა N წერტილით (90°) | `90` and the degree sign kept. |
| Digitized object (from selection) | დიგიტალიზებული შენობა (მონიშნულიდან) | Converts an already-selected polygon from another layer. |
| Object | შენობა | Message-box title, singular. |
| Activate a polygon layer and select geometry. | გაააქტიურეთ პოლიგონური შრე და მონიშნეთ გეომეტრია. | "Activate" = make it the active layer in the QGIS Layers panel. |
| Objects | შენობები | Message-box title, plural — same concept as `Object` above; the English is inconsistent. |
| Select one polygon. | მონიშნეთ ერთი პოლიგონი. | Exactly one — the tool handles one at a time. |
| A polygon is required. | საჭიროა პოლიგონი. | The selection was not an area. |
| Drawing object | შენობის დახაზვა | Icon-only button: hover text and fallback label, reused 3×. Means *digitising a building footprint*, **not** a CAD file. |

## `QuickToolbar` (1)

| English | ქართული | Note |
|---|---|---|
| {label} ({shortcut}) | {label} ({shortcut}) | Tooltip pattern, e.g. `ბოძის განთავსება (P)`. Both placeholders unchanged; only punctuation may be adapted, and Georgian needs no change here. |

---

## Self-check against the three rules

- **Rule 1** — no `<source>` text is touched; this file only supplies the right-hand column.
- **Rule 2** — three strings carry placeholders: `{details}` (FiberQ), `{name}`
  (ElementPlacementUI), `{label}` + `{shortcut}` (QuickToolbar). All appear
  byte-identical in the Georgian, in lowercase, with both braces. `Place {name}` moves
  the placeholder to the end, which Rule 2 explicitly permits. The one line break
  (`Error opening the preview map:`) is preserved. The one ellipsis (`Add drawing…`)
  is preserved as U+2026.
- **Rule 3** — nothing is compiled; no `.qm` file is produced or touched.

## Consistency pairs verified

The English says the same thing two ways in several places. These must not diverge in
Georgian, and do not:

| Concept | Strings | Georgian |
|---|---|---|
| Pole | `Place Pole` / `Add pole` | ბოძი |
| Route creation | `Create Route` / `Create route` | ტრასის შექმნა |
| Manhole | `Place Manhole` / `Placing manholes` | ჭა |
| Slack | `Optical Slack` / `Optical slacks` | ოპტიკური მარაგი / მარაგები |
| Element placement | `Place {name}` / `Placing elements` | განთავსება |
| Unlink | `Clear drawing from element` / `Unlink drawing from…` | მიბმის მოხსნა |
