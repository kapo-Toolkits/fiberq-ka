# Batch 4 — `FiberQPlugin` (132)

The last and largest context: menu entries, toolbar tooltips, dialogs, message-bar
banners, file-dialog filters and error text from the plugin's main module. Nine `numerus`
messages. This is the group `docs/TRANSLATING.md` recommends leaving until last, and the
advice is sound — much of it is error text a user meets rarely.

Grouped by function below rather than by file order; the leading number is the position
in the context, so nothing is lost.

---

## First: an answer I asked for that was already in the file

In [issue #43](https://github.com/vukovicvl/fiberq/issues/43) I asked the maintainer what
`List of latent elements` means. **The catalogue already answers it** — string 66 carries
an `<extracomment>` I had not read, because my earlier survey only covered the UI-group
contexts:

> In FiberQ a latent element is a passive optical element (joint closure, ODF, OTB,
> termination box) that sits ON a cable's path at a recorded distance along it, between
> the cable's two endpoints — recorded as data, not drawn as a separate map feature.
> "latent" = intermediate/pass-through, NOT "faulty", "hidden bug" or "dormant".

So: **`latent element` → `შუალედური ელემენტი`** (intermediate element). A follow-up
correction is owed on the issue — the question should be withdrawn, not left standing.

Note this reuses `შუალედური` from `შუალედური მარაგი` (mid-span slack). That is not a
collision: both are things recorded at an intermediate point along a cable rather than at
its ends, and the shared adjective makes the model *more* legible, not less.

---

## Validation results and reporting (1–10, 21–31)

| # | English | ქართული | Note |
|---:|---|---|---|
| 1 | Validation could not run: {details} | ვალიდაცია ვერ გაეშვა: {details} | |
| 2 | Validation found no issues ({rules} rules, {layers} layers). | ვალიდაციამ ხარვეზი ვერ აღმოაჩინა ({rules} წესი, {layers} შრე). | Singular after a numeral. |
| 3 | Could not save the report: {details} | ანგარიშის შენახვა ვერ მოხერხდა: {details} | |
| 4 | Saved {format} report to {path} | {format} ანგარიში შენახულია: {path} | |
| 5 | Could not check lengths: {details} | სიგრძეების შემოწმება ვერ მოხერხდა: {details} | |
| 6 | Skipped {layers}: lengths cannot be measured without an ellipsoid. Set one in Project Properties > General. | გამოტოვებულია {layers}: სიგრძის გაზომვა ელიფსოიდის გარეშე შეუძლებელია. მიუთითეთ ის მენიუში პროექტის თვისებები > ზოგადი. | Menu path uses QGIS's Georgian names; the `>` stays ASCII as in the source. |
| 7 | Could not check {layers}. | {layers} ვერ შემოწმდა. | |
| 8 | Largest change: {field} {old} -> {new} on {layer} | ყველაზე დიდი ცვლილება: {field} {old} -> {new} შრეზე {layer} | Four placeholders, arrow kept ASCII. |
| 9 | {layers} left unchanged: save or discard the open edits there, then run this again. | {layers} უცვლელი დარჩა: შეინახეთ ან გააუქმეთ იქ გახსნილი რედაქტირება და ხელახლა გაუშვით. | |
| 10 | Some layers could not be updated: {details} | ზოგიერთი შრის განახლება ვერ მოხერხდა: {details} | |
| 21 | Run a validation before exporting a report. | ანგარიშის ექსპორტამდე გაუშვით ვალიდაცია. | |
| 22 | Export validation report | ვალიდაციის ანგარიშის ექსპორტი | |
| 23 | No lengths were checked. See the warnings above. | სიგრძეები არ შემოწმებულა. იხილეთ ზემოთ მოცემული გაფრთხილებები. | |
| 24 | No FiberQ layers with stored lengths in this project. | ამ პროექტში შენახული სიგრძეების მქონე FiberQ-ის შრეები არ არის. | |
| 25 | All stored lengths already match the geometry. | ყველა შენახული სიგრძე უკვე ემთხვევა გეომეტრიას. | |
| 27 | Recalculate lengths | სიგრძეების გადათვლა | |
| 28 | Recalculate stored lengths? | გადაითვალოს შენახული სიგრძეები? | Confirmation-dialog question. |
| 29 | Lengths are measured on the project ellipsoid, the same way the QGIS measure tool does. Slack values are read but never changed. | სიგრძეები იზომება პროექტის ელიფსოიდზე, ისევე როგორც QGIS-ის საზომი ხელსაწყოთი. მარაგის მნიშვნელობები იკითხება, მაგრამ არასდროს იცვლება. | "Slack" here is the cable reserve, not a UI notion — `მარაგი`, per the glossary. |
| 31 | This issue is not tied to a map location. | ეს ხარვეზი რუკაზე კონკრეტულ ადგილს არ უკავშირდება. | |

## Language menu (11–12)

| # | English | ქართული | Note |
|---:|---|---|---|
| 11 | Interface language | ინტერფეისის ენა | |
| 12 | Language set to {language}.⏎⏎Language will change when QGIS restarts. | ენა შეიცვალა: {language}.⏎⏎ენა QGIS-ის ხელახლა გაშვების შემდეგ შეიცვლება. | The two `\n` produce the blank line — both kept. |

## Toolbar: main actions (32–33, 48–58, 64–90, 98–106)

| # | English | ქართული | Note |
|---:|---|---|---|
| 32 | Publish to PostGIS | PostGIS-ში გამოქვეყნება | |
| 33 | Health check | მდგომარეობის შემოწმება | Data-integrity check on the project, **not** optical/network health. Must stay identical to the bracketed term in 84. |
| 48 | Undo (FiberQ) | გაუქმება (FiberQ) | **Duplicate of the `FiberQ` context string** — identical translation required. |
| 49 | Undo last FiberQ action (Ctrl+Shift+Z) | FiberQ-ის ბოლო მოქმედების გაუქმება (Ctrl+Shift+Z) | Key names kept in Latin. |
| 50 | Redo (FiberQ) | გამეორება (FiberQ) | |
| 51 | Redo last undone FiberQ action (Ctrl+Shift+Y) | FiberQ-ის ბოლო გაუქმებული მოქმედების გამეორება (Ctrl+Shift+Y) | |
| 52 | Help / About | დახმარება / შესახებ | |
| 53 | Help and information about FiberQ | დახმარება და ინფორმაცია FiberQ-ის შესახებ | |
| 54 | Publish the active (or selected) layer to PostGIS | აქტიური (ან მონიშნული) შრის გამოქვეყნება PostGIS-ში | |
| 55 | Terminal slack (shortcut) | საბოლოო მარაგი (მალსახმობი) | Hidden action that exists only to bind the `R` key; appears in the QGIS shortcuts list. "(shortcut)" = the key binding, not a Windows shortcut file. |
| 56 | Optical schematic view | ოპტიკური სქემის ხედი | |
| 57 | Import points | წერტილების იმპორტი | |
| 58 | Export | ექსპორტი | |
| 64 | Hide locator | ლოკატორის დამალვა | Removes the address marker the Locator dropped. Imperative. |
| 65 | Relations | ოპტიკური კავშირები **(to confirm)** | A FiberQ "relation" is a **named end-to-end optical link** between two sites, that cables get assigned to — telecom sense. Explicitly **not** QGIS layer relations (which Georgian QGIS calls `ურთიერთკავშირები`), so the bare word could not be reused. `ოპტიკური კავშირი` = optical link. Alternative worth a practitioner's view: `ოპტიკური მიმართულებები`. |
| 66 | List of latent elements | შუალედური ელემენტების სია | See the note at the top. |
| 67 | Cut infrastructure | ინფრასტრუქტურის გაჭრა | **Geometry editing** — splits one line feature in two at a click. Not a cable fault. |
| 68 | Fiber break | ბოჭკოს გაწყვეტა | **The fault concept**, unlike 67. Kept lexically apart, as in batches 1–2. |
| 69 | Color catalog | ბოჭკოს ფერთა კოდი | The **fibre colour code** — the standard sequence identifying each tube and fibre in a cable (TIA-598 / IEC). **Not** a QGIS symbology palette, so `ფერების კატალოგი` was rejected as inviting exactly that misreading. |
| 70 | Save all layers to GeoPackage | ყველა შრის შენახვა GeoPackage-ში | |
| 71 | Export all vector layers (including Temporary scratch) to a single .gpkg and redirect the project to it | ყველა ვექტორული შრის (მათ შორის დროებითის) ექსპორტი ერთ .gpkg ფაილში და პროექტის მასზე გადამისამართება | |
| 72 | Auto save to GeoPackage | ავტოშენახვა GeoPackage-ში | |
| 73 | When enabled: every new or memory layer is automatically written to the selected .gpkg and redirected to it | ჩართვისას: ყოველი ახალი ან მეხსიერების შრე ავტომატურად ჩაიწერება არჩეულ .gpkg ფაილში და მასზე გადამისამართდება | |
| 74 | Preview Map | წინასწარი დათვალიერების რუკა | Duplicate of the `FiberQ` context string. |
| 75 | Open the FiberQ Preview Map (PostGIS connection from config.ini) | FiberQ-ის წინასწარი დათვალიერების რუკის გახსნა (PostGIS-კავშირი config.ini-დან) | `config.ini` is a filename — kept. |
| 76 | Create Service Area | მომსახურების ზონის შექმნა | |
| 77 | Create Service Area from selection (buffer around selected cables/elements) | მომსახურების ზონის შექმნა მონიშნულიდან (ბუფერი მონიშნული კაბელების/ელემენტების გარშემო) | |
| 78 | Draw Service Area Manually | მომსახურების ზონის ხელით დახაზვა | |
| 79 | Manual Service Area drawing (like Google Earth) and entry into Service Area layer | მომსახურების ზონის ხელით დახაზვა (Google Earth-ის მსგავსად) და ჩაწერა მომსახურების ზონის შრეში | |
| 80 | Branch info | განშტოების ინფორმაცია | "Branch" = a junction point where cables split off. Not a tree, office or git branch. |
| 81 | Click on cable to show number of cables/types/capacities at that point | დააწკაპუნეთ კაბელზე, რომ ნახოთ კაბელების რაოდენობა/ტიპები/ტევადობები ამ წერტილში | |
| 82 | Show shortcuts | მალსახმობების ჩვენება | |
| 83 | BOM report (XLSX/CSV) | მასალების ნუსხა — BOM (XLSX/CSV) | Bill of Materials. Format names untranslated. |
| 84 | Check (health check) | შემოწმება (მდგომარეობის შემოწმება) | The note asks that the bracketed term stay identical to 33 — it does. |
| 85 | Validate project | პროექტის ვალიდაცია | |
| 86 | Recalculate lengths… | სიგრძეების გადათვლა… | **U+2026 here**, unlike 59/61 — see the ellipsis note below. |
| 87 | Rewrite stored lengths that disagree with the drawn geometry | დახაზულ გეომეტრიას აცდენილი შენახული სიგრძეების გადაწერა | |
| 88 | Settings | პარამეტრები | |
| 89 | Smart selection + change element type (visual style) | ჭკვიანი მონიშვნა + ელემენტის ტიპის შეცვლა (ვიზუალური სტილი) | |
| 90 | Move elements | ელემენტების გადატანა | |
| 91 | Move elements on the map (click-move-click) | ელემენტების გადატანა რუკაზე (დაწკაპუნება-გადატანა-დაწკაპუნება) | |
| 98 | Smart selection | ჭკვიანი მონიშვნა | Matches the `SelectionUI` entry, which adds "(Multiple Layers)". |
| 99 | Click on the elements to select/deselect them. Selections on other layers are not touched. | დააწკაპუნეთ ელემენტებზე მოსანიშნად ან მონიშვნის მოსახსნელად. სხვა შრეებზე მონიშვნა ხელუხლებელი რჩება. | |
| 100 | Click on cable to show number of cables/types/capacities at that point (right click or ESC to exit). | დააწკაპუნეთ კაბელზე, რომ ნახოთ კაბელების რაოდენობა/ტიპები/ტევადობები ამ წერტილში (გამოსასვლელად მარჯვენა დაწკაპუნება ან ESC). | Longer variant of 81 — the two must agree word for word up to the bracket. |
| 101 | Optical schematic | ოპტიკური სქემა | |
| 103 | Delete | წაშლა | |
| 104 | No selected features to delete. | წასაშლელად მონიშნული ობიექტები არ არის. | |
| 105 | Deleted {count} selected features from all layers. | ყველა შრიდან წაიშალა {count} მონიშნული ობიექტი. | |
| 106 | Shortcuts | მალსახმობები | |

## Images attached to elements (37–42, 92–95)

| # | English | ქართული | Note |
|---:|---|---|---|
| 37 | Choose image | აირჩიეთ სურათი | |
| 38 | Images (*.jpg *.jpeg *.png *.gif);;All files (*.*) | სურათები (*.jpg *.jpeg *.png *.gif);;ყველა ფაილი (*.*) | Qt file filter: the `;;` separator and every glob pattern are kept byte for byte; only the human labels are translated. |
| 40 | Image | სურათი | |
| 41 | Click on an element to open its image (ESC to exit). | დააწკაპუნეთ ელემენტზე მისი სურათის გასახსნელად (გამოსასვლელად ESC). | |
| 92 | Import picture to element | სურათის იმპორტი ელემენტზე | The English says *picture* here and *image* elsewhere for the same thing; Georgian uses `სურათი` throughout. |
| 93 | Link a .jpg/.png picture to selected element(s) | .jpg/.png სურათის მიბმა მონიშნულ ელემენტ(ებ)თან | Static text — "(s)" means "one or more", no count is substituted. |
| 94 | Clear picture from element | სურათის მოხსნა ელემენტიდან | |
| 95 | Unlink picture from selected element(s) | სურათის მიბმის მოხსნა მონიშნული ელემენტ(ებ)იდან | Only the link is cleared; the file on disk survives. Same construction as the `DrawingsUI` pair in batch 1. |

## Cutting tool (43–45)

| # | English | ქართული | Note |
|---:|---|---|---|
| 43 | Cutting | ჭრა | Message-bar banner. The act of splitting a line feature, **not** a cable outage. |
| 44 | Tool activated. Move mouse over line (red cross), left click to cut, right/ESC exit. | ხელსაწყო გააქტიურდა. მიიტანეთ კურსორი ხაზთან (წითელი ჯვარი), მარცხენა დაწკაპუნებით გაჭერით, გამოსასვლელად მარჯვენა ან ESC. | |
| 45 | Infrastructure cutting | ინფრასტრუქტურის ჭრა | Error-dialog title for the same tool as 67. |

## Export (59–63, 114–123)

| # | English | ქართული | Note |
|---:|---|---|---|
| 59 | Export selected... | მონიშნულის ექსპორტი... | **Three ASCII dots**, not U+2026 — see below. |
| 60 | Export selected features of the active layer to GPX / KML / KMZ / GeoPackage | აქტიური შრის მონიშნული ობიექტების ექსპორტი GPX / KML / KMZ / GeoPackage ფორმატში | |
| 61 | Export all... | ყველას ექსპორტი... | ASCII dots. |
| 62 | Export all features of the active layer to GPX / KML / KMZ / GeoPackage | აქტიური შრის ყველა ობიექტის ექსპორტი GPX / KML / KMZ / GeoPackage ფორმატში | |
| 63 | Export active layer | აქტიური შრის ექსპორტი | |
| 114 | Please select an active vector layer before exporting. | ექსპორტამდე აირჩიეთ აქტიური ვექტორული შრე. | |
| 115 | There are no selected features on the active layer. | აქტიურ შრეზე მონიშნული ობიექტები არ არის. | |
| 116 | Export format | ექსპორტის ფორმატი | |
| 117 | Select output format: | აირჩიეთ გამომავალი ფორმატი: | |
| 118 | Export layer | შრის ექსპორტი | |
| 119 | Unknown driver for extension '{ext}'. | უცნობი დრაივერი გაფართოებისთვის '{ext}'. | |
| 120 | Error while exporting:⏎{details} | ექსპორტის შეცდომა:⏎{details} | |
| 121 | Export failed: {details} | ექსპორტი ვერ შესრულდა: {details} | |
| 122 | Successfully exported the selected features of layer '{layer}'⏎to:⏎{path} | '{layer}' შრის მონიშნული ობიექტები წარმატებით გატანილია⏎მისამართზე:⏎{path} | The note asks that this stay one whole sentence, not be split — it is. Both line breaks kept. |
| 123 | Successfully exported all features of layer '{layer}'⏎to:⏎{path} | '{layer}' შრის ყველა ობიექტი წარმატებით გატანილია⏎მისამართზე:⏎{path} | Same, for the whole layer. |

## Point import (107–113)

| # | English | ქართული | Note |
|---:|---|---|---|
| 107 | Choose a file with points (KML/KMZ/DWG/Shape/GPX) | აირჩიეთ წერტილების შემცველი ფაილი (KML/KMZ/DWG/Shape/GPX) | |
| 108 | GIS files (*.kml *.kmz *.shp *.dwg *.gpx);;All files (*) | GIS ფაილები (*.kml *.kmz *.shp *.dwg *.gpx);;ყველა ფაილი (*) | Filter patterns and `;;` untouched. |
| 109 | Unable to load or invalid file! | ფაილი ვერ ჩაიტვირთა ან არასწორია! | |
| 110 | The selected file does not contain points! | არჩეული ფაილი წერტილებს არ შეიცავს! | |
| 111 | Unable to create or find the Poles layer! | ბოძების შრის შექმნა ან პოვნა ვერ მოხერხდა! | |
| 112 | Unable to find the target layer! | სამიზნე შრე ვერ მოიძებნა! | |
| 113 | Imported {count} points into layer '{layer}'! | '{layer}' შრეში იმპორტირებულია {count} წერტილი! | `{layer}` moves to the front and takes `-ში` outside the braces — the case-ending pattern from the glossary. |

## Route correction (124–128)

| # | English | ქართული | Note |
|---:|---|---|---|
| 124 | Route correction | ტრასის კორექცია | Duplicate of the `RoutingUI` string. |
| 125 | No errors found! | შეცდომები ვერ მოიძებნა! | |
| 126 | Layer 'Poles' not found! | შრე 'Poles' ვერ მოიძებნა! | `Poles` is the **actual layer name** in the project, not a word — untranslated. |
| 127 | Route layer 'Route' not found! | ტრასის შრე 'Route' ვერ მოიძებნა! | Same: `Route` in quotes is the layer name; the unquoted "Route layer" is translated. |
| 128 | Route has been automatically attached to a pole. | ტრასა ავტომატურად მიება ბოძს. | |

## Manholes (130–132)

| # | English | ქართული | Note |
|---:|---|---|---|
| 130 | Placing manhole | ჭის განთავსება | **Singular**, unlike `DuctingUI`'s `Placing manholes` → `ჭების განთავსება`. |
| 131 | Click on the map to place the manhole (ESC to exit). | დააწკაპუნეთ რუკაზე ჭის განსათავსებლად (გამოსასვლელად ESC). | |
| 132 | Manhole | ჭა | |

## Remaining dialogs and errors (13–16, 34–36, 46–47, 96–97, 102)

| # | English | ქართული | Note |
|---:|---|---|---|
| 13 | BOM report | მასალების ნუსხა (BOM) | Error-dialog title. Bill of Materials — **not** the Unicode byte-order mark. |
| 14 | Error: {details} | შეცდომა: {details} | |
| 15 | Locator | ლოკატორი | |
| 16 | Error opening locator: {details} | ლოკატორის გახსნის შეცდომა: {details} | |
| 34 | Error while running detailed route check:⏎{details} | ტრასის დეტალური შემოწმების შეცდომა:⏎{details} | |
| 35 | Change element type | ელემენტის ტიპის შეცვლა | |
| 36 | Select one or more elements and try again. | მონიშნეთ ერთი ან რამდენიმე ელემენტი და სცადეთ ხელახლა. | |
| 46 | {name} – About | {name} – პროგრამის შესახებ | En-dash kept. |
| 47 | About dialog error: {details} | „შესახებ" ფანჯრის შეცდომა: {details} | Georgian quotation marks „ " around the dialog name. |
| 96 | Placing elements | ელემენტების განთავსება | The note says treat it as a **noun phrase** (the category of passive elements), not the -ing action. Georgian's verbal noun covers both readings, so this stays identical to the `ElementPlacementUI` string. |
| 97 | Error activating: {details} | გააქტიურების შეცდომა: {details} | |
| 102 | Error opening dialog: {details} | ფანჯრის გახსნის შეცდომა: {details} | |

## Counts — `numerus` messages (9)

One translation box each, Georgian having a single CLDR plural form. `%n` is a Qt
placeholder, not a `{}` one — it is what selects the form, so it must survive exactly.

| # | English | ქართული | Note |
|---:|---|---|---|
| 17 | %n error(s) | %n შეცდომა | |
| 18 | %n warning(s) | %n გაფრთხილება | |
| 19 | %n info | %n ინფორმაციული ჩანაწერი | Same treatment as in `ValidationPanel`. |
| 20 | %n rule(s) failed to run; the rules that did found no issues | %n წესი ვერ გაეშვა; დანარჩენებმა ხარვეზი ვერ აღმოაჩინეს | |
| 26 | %n feature(s) will have their stored length rewritten from the drawn geometry. | %n ობიექტს შენახული სიგრძე დახაზული გეომეტრიიდან გადაეწერება. | |
| 30 | Recalculated lengths on %n feature(s). | სიგრძეები გადათვლილია %n ობიექტზე. | |
| 39 | Image linked to %n element(s). | სურათი მიება %n ელემენტს. | The note warns: keep `%n`, do **not** convert it to `{count}`. |
| 42 | Image link removed for %n element(s). | სურათის მიბმა მოხსნილია %n ელემენტს. | Only the link — the file is not deleted. |
| 129 | Drawing link removed for %n element(s). | ნახაზის მიბმა მოხსნილია %n ელემენტს. | The CAD drawing, not the image — parallel wording to 42 on purpose, since the English is parallel too. |

---

## The two ellipsis styles

The catalogue is not uniform, and each string must keep what it has:

| String | Character | |
|---|---|---|
| `Export selected...` (59) | `...` three ASCII full stops | |
| `Export all...` (61) | `...` three ASCII full stops | |
| `Recalculate lengths…` (86) | `…` U+2026 | |
| `Add drawing…` (batch 1) | `…` U+2026 | |
| `Export report…`, `Validating…` (batch 3) | `…` U+2026 | |

Qt Linguist will not warn about this — it is not a placeholder. Worth mentioning to the
maintainer as a small consistency item in the English, but the translation copies whatever
the source has.

## Cross-context duplicates verified

Nine strings in this context also appear elsewhere. Qt stores them as separate entries, so
agreement is not enforced; checked by hand:

| String | Also in | ქართული |
|---|---|---|
| Undo (FiberQ) | `FiberQ` | გაუქმება (FiberQ) |
| Preview Map | `FiberQ` | წინასწარი დათვალიერების რუკა |
| Placing elements | `ElementPlacementUI` | ელემენტების განთავსება |
| Route correction | `RoutingUI` | ტრასის კორექცია |
| Smart selection | `SelectionUI` (+ "(Multiple Layers)") | ჭკვიანი მონიშვნა |
| Terminal slack | `SlackUI` | საბოლოო მარაგი |
| Fiber break | `ValidationRules` rule name | ბოჭკოს გაწყვეტა |
| Health check ↔ Check (health check) | within this context (33 ↔ 84) | მდგომარეობის შემოწმება |
| Cut infrastructure ↔ Infrastructure cutting | within this context (67 ↔ 45) | ინფრასტრუქტურის გაჭრა / ჭრა |

## Self-check against the three rules

- **Rule 1** — no `<source>` touched.
- **Rule 2** — placeholders in this batch: `{details}` ×11, `{layers}` ×5, `{layer}` ×4,
  `{path}` ×3, `{count}` ×2, `{format}`, `{rules}`, `{field}`, `{old}`, `{new}`,
  `{language}`, `{name}`, `{ext}`, plus `%n` in the nine numerus messages. All reproduced
  exactly. Three strings reorder them for Georgian syntax (8, 113, 122/123). Six line
  breaks preserved (12 has two, 34, 120, 122, 123). Two Qt file filters (38, 108) keep
  their `;;` separators and every glob pattern.
- **Rule 3** — nothing compiled.

## Not translated, deliberately

`Poles`, `Route` (in quotes — actual layer names) · `config.ini` · `Ctrl+Shift+Z`,
`Ctrl+Shift+Y`, `ESC`, `R` · `.gpkg`, `.jpg`, `.png`, `GPX`, `KML`, `KMZ`, `DWG`, `Shape`,
`XLSX`, `CSV`, `GeoPackage`, `PostGIS` · `Google Earth` · glob patterns in file filters.

## Terms this batch added to the glossary

`latent element` → შუალედური ელემენტი · `relation (optical link)` → ოპტიკური კავშირი
**(to confirm)** · `colour code (fibre)` → ბოჭკოს ფერთა კოდი · `branch` → განშტოება ·
`file filter` → ფაილის ფილტრი · `memory layer` → მეხსიერების შრე ·
`redirect (a project)` → გადამისამართება

---

## Progress — catalogue complete

| Batch | Context(s) | Strings | Status |
|---|---|---:|---|
| 1 | toolbar, menus, element names (11 contexts) | 76 | done |
| 2 | `ValidationRules` | 45 | done |
| 3 | `ValidationReport` + `ValidationPanel` | 53 | done |
| 4 | `FiberQPlugin` | 132 | done |
| | **Total** | **306** | **306 (100%)** |

Every string in the catalogue now has a Georgian translation drafted. What remains is
mechanical: the maintainer generates `fiberq/i18n/fiberq_ka.ts`, the strings get typed
into Qt Linguist (which will verify every placeholder automatically), and the `.ts` goes
back as a pull request.

**One open item:** `Relations` (65) is the only term still marked to confirm, and it is a
genuine domain question — whether a Georgian fibre engineer says `ოპტიკური კავშირი` or
`ოპტიკური მიმართულება` for a named end-to-end link.
