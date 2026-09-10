# English → Georgian glossary (draft)

For the FiberQ Georgian catalogue `fiberq/i18n/fiberq_ka.ts`.

Status: **draft, v0.4** (all 306 catalogue strings drafted) — proposed by the Georgian translator, not yet used in the
catalogue. Ten terms reviewed and **decided** on 2026-09-09 (manhole, transition pipe,
mid span slack, patch panel, service area, BOM, backbone, drop, terminal slack, preview
map); their rejected alternatives are kept on the record below. No term is left awaiting
a practitioner's judgement — one term is
so marked (`Relation`). No term is waiting on the maintainer: the one string whose English
looked ambiguous (`List of latent elements`) turned out to be defined in its own
`<extracomment>`.

Structure mirrors the existing English → French and English → Serbian glossaries
in `CONTRIBUTING.md`.

---

## Georgian-specific conventions applied throughout

These are decisions taken once and applied to every entry below, so they are not
repeated term by term.

| Convention | Decision | Why |
|---|---|---|
| **Capitalisation** | Georgian has no letter case. English Title Case is not reproduced. | `Place Pole` → `ბოძის განთავსება`, not an imitation of the capitals. |
| **Imperative menu entries** | Rendered as a verbal noun (`-ება` / `-ვა`), not a true imperative. | Georgian UI convention (and QGIS's own Georgian translation): `ბოძის განთავსება`, not `განათავსე ბოძი`. |
| **Latin acronyms** | `ODF`, `OTB`, `TO`, `TB`, `PE`, `DWG`, `DXF`, `GPKG`, `KML`, `GPX`, `CRS`, `BOM`, `PostGIS`, `GeoPackage`, `XLSX`, `CSV`, `JSON` stay in Latin script. Only the descriptive part around them is translated. | Georgian fibre and GIS practice uses these acronyms in Latin; transliterating them (`ოდიეფი`) would be unreadable to the target user. |
| **Adjective + acronym** | The adjective is translated and precedes the acronym: `Indoor OTB` → `შიდა OTB`. | Matches Georgian word order and keeps the acronym intact. |
| **Plural forms** | Georgian has one plural form in Qt/CLDR. Every `%n` message shows a single `<numerusform>` in Qt Linguist. | No `%n` message needs two variants, unlike French. |
| **Placeholders and case endings** | Case suffixes attach *outside* the braces: `'{layer}'-ში`, `{path}-ზე`, `{count}-მა`. | Keeps the placeholder byte-identical (Rule 2) while letting the sentence decline naturally. This is the most frequent trap in Georgian. |
| **Toolbar-width strings** | Group labels reused 3–4× (`Cable laying`, `Drawings`, `Ducting`, `Routing`, `Selection`, `Drawing object`, `Placing elements`) are kept to one or two words. | One translation must serve a menu title, a button caption, a tooltip and a status tip. |
| **GIS vocabulary** | Follows the existing QGIS Georgian UI translation rather than inventing new terms. | A user runs FiberQ inside QGIS; two vocabularies for `layer` would be worse than an imperfect single one. |

---

## 1. Structures and civil works

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Pole | **ბოძი** | The support carrying aerial cable. One word for both `Place Pole` (quick toolbar) and `Add pole` (Routing menu) — the English differs, the object does not. |
| Manhole | **საკაბელო ჭა** *(short form: **ჭა**)* | The underground inspection chamber on a duct run. **Not** `ლუქი` — that is only the cover. **Decided** (translator, 2026-09-09). Field Georgian also uses the Russianism `კოლოდეცი`; `საკაბელო ჭა` is proposed as the written-document term. |
| Duct / PE pipe | **მილი** *(as a menu entry: **PE მილი**)* | The buried distribution duct (Ø 40 mm). The English says `pipe` in one place and `duct` everywhere else — Georgian uses the single word `მილი` for both, per the translator note. |
| Transition pipe | **გადასასვლელის მილი** | The large protective casing (Ø 110 mm) laid where the route crosses under a road, railway or watercourse; the smaller PE ducts are pulled through it. **Not** an adapter between two pipe sizes. **Decided**; alternative `დამცავი მილი` (protective pipe) rejected — it loses the "crossing" sense the legacy term `prelaz` carries. |
| Ducting | **მილგაყვანილობა** | Noun naming the whole duct infrastructure (manholes + ducts). Toolbar group label. |
| Trench | **თხრილი** | Not currently a UI string; listed for consistency in future work. |
| Route | **ტრასა** | The **physical path on the ground** that cables follow. **Critically not `მარშრუტი`**, which in Georgian means a travel/transport route. `ტრასა` is the established Georgian engineering term for an alignment and is what a surveyor says. Also not a file path or a network path. |
| Routing | **ტრასირება** | Noun naming the group of route tools. The engineering act of setting out an alignment. |
| Breakpoint | **გაყოფის წერტილი** | A **route geometry** operation: splits one route line into two at the clicked point. **Not** a fibre fault. Deliberately avoids `წყვეტა` (break/rupture), which would collide with `Fiber break` below. |
| Span | **მალი** | The run between two supports. Standard Georgian engineering term. Not a bridge span. |
| Infrastructure | **ინფრასტრუქტურა** | |

## 2. Cables

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Cable | **კაბელი** | |
| Cable laying | **კაბელის გაყვანა** | Gerund: the act of installing optical cable on the map. Reused 4× (menu title + button label + tooltip + status tip), so it must stay this short. |
| Underground | **მიწისქვეშა** | Adjective: laid in ducts or a trench. Pairs with `საჰაერო`. |
| Aerial | **საჰაერო** | Adjective: strung overhead on poles. `საჰაერო ხაზი` (overhead line) is the standard Georgian collocation. |
| Backbone | **მაგისტრალი** *(the network: **მაგისტრალური ქსელი**; as a cable class in menus: **მაგისტრალური**)* | The transport/feeder cable between main network nodes. **Decided.** `მაგისტრალი` is the noun for the concept; the menu entry uses the derived adjective `მაგისტრალური` so the three cable classes read as a parallel set — `მაგისტრალური / გამანაწილებელი / აბონენტური` — under both `მიწისქვეშა` and `საჰაერო`. |
| Distribution | **გამანაწილებელი** | Cable class: from a backbone node out to the street distribution points. Same adjective the Georgian power sector uses for distribution networks. |
| Drop | **აბონენტური** | Cable class, a **noun** in English (drop cable / subscriber cable): the final span from the street distribution point to one subscriber's premises. **Never the verb "to drop"** (`ჩამოგდება` would be badly wrong). Rendered as an adjective so the menu reads `მაგისტრალური / გამანაწილებელი / აბონენტური` — three parallel entries under both `მიწისქვეშა` and `საჰაერო`. **Decided**; alternative `აბონენტის` (genitive) rejected — it breaks the parallel adjectival set. |
| Fiber / optical fiber | **ოპტიკური ბოჭკო** *(short: **ბოჭკო**)* | |
| Optical | **ოპტიკური** | |
| Fiber break | **ბოჭკოს გაწყვეტა** | A fibre fault location — a real network defect. Kept lexically distinct from `Breakpoint` above, which is a geometry edit. |
| Capacity | **ტევადობა** | Fibre count / duct count. |
| Cutting / Cut infrastructure | **ჭრა** / **ინფრასტრუქტურის ჭრა** | The tool that cuts a line feature at a clicked point. |

## 3. Splicing and slack

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Joint closure | **ოპტიკური მუფტა** *(short: **მუფტა**)* | The splice enclosure (fr `BPE`, sr `nastavak`). `მუფტა` is the universally used term in Georgian cable practice. |
| Splice | **შედუღება** | The fusion weld between two fibres. Corresponds to the French `soudure`. |
| Slack | **მარაგი** | The spare length of cable coiled and stored at a point so it can be re-spliced later. `მარაგი` = reserve/stock, matching the Russian/Georgian field usage `запас`. |
| Optical slack(s) | **ოპტიკური მარაგი** / **ოპტიკური მარაგები** | Singular on the quick-toolbar button, plural for the tool group and the map layer — the English makes the same distinction. |
| Terminal slack | **საბოლოო მარაგი** *(explanatory form: **საბოლოო წერტილის მარაგი**)* | Slack at a cable **end** (legacy `end slack`, internally `zavrsna`, drawn as a C coil). **Decided.** The short form is used in UI strings; the longer `საბოლოო წერტილის მარაგი` is available where a sentence needs to be unambiguous. Stays clearly distinct from `შუალედური მარაგი`. |
| Mid span slack | **შუალედური მარაგი** | Slack at an intermediate point where the cable runs **through** without being cut (legacy `thru slack`, internally `prolazna`, drawn as an S coil). Must remain clearly distinct from terminal slack — one word cannot serve both. **Decided**; alternative `გამავალი მარაგი` (through slack) rejected, though it is closer to the legacy name. |

## 4. Network elements (equipment)

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Element / network element | **ელემენტი** / **ქსელის ელემენტი** | The passive optical devices (ODF, OTB, TO …), not map features in general. |
| Placing elements | **ელემენტების განთავსება** | Gerund naming the whole drop-down group. Reused as label + tooltip + status tip. |
| ODF | **ODF** | Optical Distribution Frame: the passive frame at the head end where feeder fibres terminate. Acronym kept — it also doubles as the layer name. |
| TB | **TB** | Terminal Box. Acronym kept; Georgian has no established equivalent. |
| OTB | **OTB** | Optical Termination Box. Acronym kept. |
| TO | **TO** | Termination Outlet — the subscriber-side optical outlet, the last element before the customer's equipment. **Warning: this is an acronym, not the English preposition "to".** |
| Patch panel | **პაჩ-პანელი** | The rack panel holding patch connections. Must stay clearly distinct from `ODF`, whose scope overlaps. **Decided**; alternative `კომუტაციური პანელი` rejected as more formal but less recognised in the field. |
| Indoor (OTB / TO) | **შიდა** | Adjective: mounted inside a building. → `შიდა OTB`, `შიდა TO`. |
| Outdoor (OTB / TO) | **გარე** | Adjective: mounted outside, on a wall or façade. → `გარე OTB`, `გარე TO`. |
| Pole (OTB / TO) | **ბოძის** | Adjective: mounted **on** a pole. One element, not a pole plus a box. → `ბოძის OTB`, `ბოძის TO`. |
| Joint Closure TO | **TO მუფტაში** | A TO housed **inside** a joint closure. Matches the Serbian `TO Izvod u nastavku`. One element, not two. |
| Change element type | **ელემენტის ტიპის შეცვლა** | |
| Move elements | **ელემენტების გადატანა** | |

## 5. Network architecture

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Network | **ქსელი** | |
| Service Area | **მომსახურების ზონა** | The coverage polygon, created as a buffer around selected cables/elements or drawn by hand. **Decided**; alternative `სერვის-ზონა` rejected — shorter and common in telecom marketing, but less precise. |
| Branch | **განშტოება** | `Branch info` shows how many cables/types/capacities pass a clicked point. |
| Relations | **კავშირები** | |
| Latent element | **შუალედური ელემენტი** | A passive optical element (joint closure, ODF, OTB, termination box) recorded *on* a cable's path at a distance along it, between its two endpoints — data, not a separate drawn feature. "Latent" = intermediate/pass-through, **not** faulty or dormant. Shares `შუალედური` with `შუალედური მარაგი` (mid-span slack) deliberately: both are things recorded at an intermediate point along a cable. |
| Relation *(optical)* | **ოპტიკური კავშირი** **(to confirm)** | A named end-to-end optical link between two sites, that cables are assigned to. **Not** a QGIS layer relation (`ურთიერთკავშირი`). Alternative worth a practitioner's view: `ოპტიკური მიმართულება`. |
| Colour code *(fibre)* | **ბოჭკოს ფერთა კოდი** | The standard sequence of colours identifying each tube and each fibre in a cable (TIA-598 / IEC). **Not** a QGIS symbology palette — `ფერების კატალოგი` was rejected for inviting exactly that misreading. |

## 6. Buildings — the `Object` trap

> **This is the single most important entry in the glossary.**

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Object | **შენობა** | Throughout FiberQ, `Object` renders the legacy Serbian `objekat` = **building / premises**. Confirmed by the layer it writes to, whose fields are number of floors, basement levels, street and house number. It must **never** be translated as `ობიექტი`. |
| Objects | **შენობები** | Plural, used as a message-box title for the same concept. |
| Object in 3 points | **შენობა 3 წერტილით** | Footprint drawn from 3 clicked points; the 4th corner is derived. |
| Object in N points | **შენობა N წერტილით** | `N` kept as the Latin letter — it is the mathematical placeholder for "any number". |
| Object in N points (90°) | **შენობა N წერტილით (90°)** | Every corner forced to a right angle. Keep the `90` and the degree sign. |
| Digitized object (from selection) | **დიგიტალიზებული შენობა (მონიშნულიდან)** | Turns a polygon already selected in another layer into a FiberQ building. |
| Drawing object | **შენობის დახაზვა** | Toolbar group label (icon-only button, hover text). It means *drawing a building*, i.e. digitising a footprint. It does **not** mean a CAD drawing — see §7. |

> **The clash to be aware of:** Georgian QGIS translates the GIS term **feature** as
> `ობიექტი`. FiberQ's **Object** is a *building*. So in the Georgian catalogue:
> `Feature` → `ობიექტი`, `Object` → `შენობა`. This is correct but counter-intuitive
> and is the easiest way to ruin the translation by autopilot.

## 7. CAD drawings and images

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Drawings | **ნახაზები** | Plural noun: external CAD files (DWG/DXF) **linked** to map elements — documents, not something drawn in QGIS. Reused 4×, so it must stay one word. |
| Add drawing… | **ნახაზის დამატება…** | Attaches an existing CAD file to the selected element(s). The trailing `…` (U+2026) is Qt's "opens a dialog" convention — kept. |
| Link | **მიბმა** | Attach a file to an element. |
| Unlink / Clear … from | **მიბმის მოხსნა** | Removes only the **link**. Neither the file on disk nor the element is deleted — the Georgian must make that unmistakable. |
| DWG / DXF | **DWG / DXF** | AutoCAD file formats, kept as-is. |
| Image / picture | **სურათი** | The English uses both `image` and `picture` for the same thing; Georgian uses one word. |

## 8. Selection

| English | ქართული (proposed) | What it means in FiberQ |
|---|---|---|
| Selection | **მონიშვნა** | Noun naming the tool group. Toolbar-width. |
| Smart selection | **ჭკვიანი მონიშვნა** | Click-to-toggle across several layers at once, without changing the active layer. |
| Smart selection (Multiple Layers) | **ჭკვიანი მონიშვნა (რამდენიმე შრე)** | Brackets kept. |
| Select / deselect | **მონიშვნა** / **მონიშვნის მოხსნა** | |
| Clear selection | **მონიშვნის მოხსნა** | **Non-destructive** — removes the highlight, deletes nothing. |
| Delete selected | **მონიშნულის წაშლა** | **Destructive** — permanently deletes the selected features from every editable layer. Sits directly above `Clear selection` in the menu, so the two Georgian strings must not be confusable. `მოხსნა` (remove/lift) vs `წაშლა` (delete) carries that difference clearly. |

## 9. GIS and QGIS vocabulary

Follows the existing QGIS Georgian UI translation.

| English | ქართული (proposed) | Note |
|---|---|---|
| Layer | **შრე** | |
| Vector layer | **ვექტორული შრე** | |
| Feature | **ობიექტი** | See the warning in §6. |
| Geometry | **გეომეტრია** | |
| Polygon | **პოლიგონი** | |
| Vertex | **წვერო** | |
| Attribute | **ატრიბუტი** | |
| Field | **ველი** | |
| Value | **მნიშვნელობა** | |
| Project | **პროექტი** | |
| CRS / coordinate reference system | **CRS** / **კოორდინატთა სისტემა** | Acronym where the string is tight (table headers), full form in explanatory sentences. |
| Geographic CRS | **გეოგრაფიული CRS** | |
| Projected CRS | **პროექციული CRS** | |
| Reproject | **რეპროექცია** | |
| Ellipsoid | **ელიფსოიდი** | |
| Tolerance | **დაშვება** | The snapping tolerance in the connectivity rules. |
| Snapping | **მიბმა** | Same word as "link" in §7; contexts do not overlap. |
| Length | **სიგრძე** | |
| Stored length | **შენახული სიგრძე** | The attribute value, as opposed to the length measured from the drawn geometry. |
| Import | **იმპორტი** | |
| Export | **ექსპორტი** | |
| Merge | **შერწყმა** | Geometry operation joining selected route lines. |
| Auto save | **ავტოშენახვა** | |
| Undo | **გაუქმება** | `Undo (FiberQ)` → `გაუქმება (FiberQ)`. The qualifier and brackets are kept: FiberQ's undo history is separate from QGIS's own. |
| Redo | **გამეორება** | |
| Shortcut | **მალსახმობი** | Keyboard shortcut. |
| Settings | **პარამეტრები** | |
| Interface language | **ინტერფეისის ენა** | |
| GeoPackage / GPKG / PostGIS / KML / KMZ / GPX / SHP / XLSX / CSV / JSON | *(untranslated)* | Format and product names stay as-is. |

## 10. Validation, reporting and checks

| English | ქართული (proposed) | Note |
|---|---|---|
| Validate project | **პროექტის ვალიდაცია** | The 14-rule validation engine (v1.4.0). |
| Validation | **ვალიდაცია** | |
| Health check | **მდგომარეობის შემოწმება** | A **different**, older feature from `Validate project`. The two must not collapse into one Georgian word. |
| Rule | **წესი** | |
| Issue | **ხარვეზი** | A finding produced by a rule. |
| Severity | **სიმძიმე** | The Error / Warning / Info axis. |
| Error | **შეცდომა** | |
| Warning | **გაფრთხილება** | |
| Info | **ინფორმაცია** | |
| Report | **ანგარიში** | |
| Export report… | **ანგარიშის ექსპორტი…** | |
| Re-run | **ხელახლა გაშვება** | |
| Run at | **გაშვების დრო** | |
| Rules run / Rules skipped | **გაშვებული წესები** / **გამოტოვებული წესები** | |
| Schema version | **სქემის ვერსია** | |
| Recalculate lengths | **სიგრძეების გადათვლა** | |
| BOM report | **მასალების ნუსხა (BOM)** | Bill of Materials. **Decided.** Georgian construction practice also says `ხარჯთაღრიცხვა`, but that is a cost estimate, which this is not. |
| Locator | **ლოკატორი** | QGIS's locator bar. |
| Optical schematic (view) | **ოპტიკური სქემა** | |
| Color catalog | **ფერების კატალოგი** | |
| Preview Map | **წინასწარი დათვალიერების რუკა** | Opens the FiberQ preview map over a PostGIS connection. **Decided**; the shorter `გადახედვის რუკა` was rejected as less precise. Length is not a constraint here — it appears in a window title and a menu entry, not on a toolbar button. |
| Hand over | **ჩაბარება** | `Errors found — not ready to hand over`. The delivery of a finished design to the client or authority — the word a Georgian designer would use, not a generic "give". |
| Structurally sound | **სტრუქტურულად გამართული** | The passing verdict on the report. |
| Issue *(finding)* | **ხარვეზი** | Consistent across `ValidationRules`, `ValidationPanel` and `ValidationReport`. |
| Publish to PostGIS | **PostGIS-ში გამოქვეყნება** | Note the case suffix outside the product name. |

---

## 11. Validation engine vocabulary

Added while translating the `ValidationRules` context (batch 2).

| English | ქართული (proposed) | Note |
|---|---|---|
| Endpoint | **ბოლო წერტილი** | A cable's start or end vertex. The connectivity rules are all about these. |
| Reference *(verb)* | **მითითება** | `Optical slack references an existing cable` — a stored foreign key to another feature. |
| Identity | **იდენტიფიკატორი** | The `fiberq_uuid` invariant. The field name itself is never translated. |
| Near-miss | **ოდნავ დაცილება** | An endpoint just outside the snapping tolerance: not connected, but clearly meant to be. |
| Self-intersecting | **საკუთარ თავს კვეთს** | Used for both `Line crosses itself` and `Polygon boundary is self-intersecting` — sibling geometry faults, so one construction serves both. |
| National grid | **ეროვნული საკოორდინატო ბადე** | Kept generic, as the English is. |
| Plausible range | **გონივრული დიაპაზონი** | Deliberately weaker than `დაშვებული` (allowed) — the English distinguishes a *plausible* numeric range from an *allowed* value domain, and the two rule names must not sound identical. |
| Allowed domain | **დაშვებულ მნიშვნელობათა ნაკრები** *(in messages: **დაშვებულთა შორის**)* | The value domain of an attribute. |
| Migration | **მიგრაცია** | The schema migration runner that adds `fiberq_uuid`. |
| Toolbar | **ხელსაწყოთა პანელი** | |

### Column and schema names — never translated

`fiberq_uuid`, `total_len_m`, `duzina_m`, `slack_m`, `duzina_km`, `duzina`. These are
database column names, including the legacy Serbian ones. Translating them would make
the message impossible to match against the actual schema.

## Open questions for the maintainer

1. ~~**`List of latent elements`** — what does "latent" mean here?~~ **Resolved from the
   catalogue itself.** The string carries an `<extracomment>` that defines it: a latent
   element is a passive optical element sitting *on* a cable's path at a recorded
   distance along it, between the cable's two endpoints — recorded as data rather than
   drawn as a separate map feature; "latent" = intermediate/pass-through, not faulty or
   dormant. Georgian: **შუალედური ელემენტი**. No maintainer input needed.
2. **`Object` vs `Objects`** — the English uses singular for one message-box title and
   plural for two others, for the same feature. Confirmed as an inconsistency in the
   English by the translator note; both will be translated as the same concept in
   Georgian. Flagging in case the English is worth fixing upstream.
3. **`Aerial Cable` / `Underground Cable`** quick-toolbar buttons are hard-wired to the
   **backbone** subtype in code, although the label does not say so. Should the Georgian
   label say `მაგისტრალური` explicitly, or mirror the English's silence?

## Documentation issues noticed while preparing this

Not translation problems, but worth reporting separately:

- `docs/TRANSLATING.md` lists **10** placeholders; the catalogue currently uses **34**
  distinct ones (`{tol}`, `{crs}`, `{fid}`, `{expected}`, `{computed}`, `{bound}`,
  `{allowed}`, `{layers}`, `{rules}`, `{features}`, `{summary}` and more).
- The context table in `docs/TRANSLATING.md` predates v1.4.0. It omits `ElementNames`
  (12), `ValidationPanel` (21), `ValidationReport` (28) and `ValidationRules` (45) —
  **106 strings**, more than a third of the catalogue — and gives `FiberQPlugin` as 105
  where it is now 123. Totals: 293 messages / 306 translatable slots across 15 contexts.
- `fiberq/i18n/__init__.py` `_LANGUAGE_NAMES` has no `ka` entry, so Georgian would appear
  in the language menu as `ka`. One line fixes it: `'ka': 'ქართული',`.
