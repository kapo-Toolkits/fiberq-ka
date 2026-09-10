# Toolbar

FiberQ's buttons are organised into groups. Below: what each one does, and how it is
translated.

!!! note "About the Georgian column"
    This is the translation draft. Until `fiberq_ka.ts` is generated, none of these strings
    appear in the plugin yet. [Translation status](../translation/index.md)

---

## Quick toolbar

The twelve most-used buttons. Context: `FiberQ`.

| Button | Georgian | What it does |
|---|---|---|
| `Place Pole` | ბოძის განთავსება | One pole at the clicked point |
| `Place Manhole` | ჭის განთავსება | One manhole |
| `Create Route` | ტრასის შექმნა | Route line from the **selected** poles/manholes |
| `Aerial Cable` | საჰაერო კაბელი | Lay an aerial cable |
| `Underground Cable` | მიწისქვეშა კაბელი | Lay an underground cable |
| `Place ODF` | ODF-ის განთავსება | |
| `Place OTB` | OTB-ის განთავსება | |
| `Place TO` | TO-ს განთავსება | |
| `Optical Slack` | ოპტიკური მარაგი | A **terminal** slack by default |
| `Undo (FiberQ)` | გაუქმება (FiberQ) | FiberQ's own history |

!!! warning "Two buttons understate what they do"
    `Aerial Cable` and `Underground Cable` are hard-wired to the **backbone** subtype in
    code, although the label does not say so. The full choice is in the Cable menu. The
    Georgian mirrors the English's silence — but I asked the maintainer about it in
    [issue #43](https://github.com/vukovicvl/fiberq/issues/43).

---

## Routing

Context: `RoutingUI`. Group label → **ტრასირება**.

| Entry | Georgian | What it does |
|---|---|---|
| `Add pole` | ბოძის დამატება | Same command as `Place Pole` |
| `Create route` | ტრასის შექმნა | **Automatically**, from selected points |
| `Create a route manually` | ტრასის ხელით შექმნა | You click the vertices |
| `Merge selected routes` | მონიშნული ტრასების შერწყმა | Several lines into one feature |
| `Import route from file` | ტრასის იმპორტი ფაილიდან | From an external GIS/CAD file |
| `Add breakpoint` | გაყოფის წერტილის დამატება | Splits a route **geometrically** in two |
| `Change route type` | ტრასის ტიპის შეცვლა | Attribute only; geometry untouched |
| `Route correction` | ტრასის კორექცია | Finds routes whose ends miss a pole or manhole |
| `Auto GPKG` | ავტო GPKG | Autosave to GeoPackage |

---

## Cable laying

Context: `CableLayingUI`. A two-level menu:

```
Cable laying
├── Underground
│   ├── Backbone
│   ├── Distribution
│   └── Drop
└── Aerial
    ├── Backbone
    ├── Distribution
    └── Drop
```

The three classes **use the same string under both parents** — one translation serves both.
[In detail](../network/architecture.md)

---

## Ducting

| Entry | Georgian |
|---|---|
| `Placing manholes` | ჭების განთავსება |
| `Place PE pipe` | PE მილის განთავსება |
| `Place transition pipe` | გადასასვლელის მილის განთავსება |

[:octicons-arrow-right-24: What each one is](../network/civil.md)

---

## Optical slack

[:octicons-arrow-right-24: Separate page](../network/slack.md)

---

## Objects (buildings)

Context: `ObjectsUI`. Group label → **შენობის დახაზვა**.

| Entry | Georgian | What it does |
|---|---|---|
| `Object in 3 points` | შენობა 3 წერტილით | The fourth corner is derived |
| `Object in N points` | შენობა N წერტილით | Any number of vertices |
| `Object in N points (90°)` | შენობა N წერტილით (90°) | Every corner forced to a right angle |
| `Digitized object (from selection)` | დიგიტალიზებული შენობა (მონიშნულიდან) | From a polygon already selected in another layer |

!!! danger "`Object` means building"
    Worth repeating: here `Object` means **building**, not a GIS feature.
    [Why](../network/index.md)

---

## Drawings

CAD files (DWG/DXF) **linked** to elements. These are documents, not something drawn in
QGIS.

| Entry | Georgian |
|---|---|
| `Drawings` | ნახაზები |
| `Add drawing…` | ნახაზის დამატება… |
| `Open drawing (by click)` | ნახაზის გახსნა (დაწკაპუნებით) |
| `Clear drawing from element` | ნახაზის მოხსნა ელემენტიდან |

!!! tip "\"Clear\" is not \"delete\""
    Unlinking deletes **neither the file on disk nor the element**. Only the link is
    dropped. The tooltip confirms it: *"Unlink confirms nothing is deleted."*

---

## Selection

| Entry | Georgian | Destructive? |
|---|---|---|
| `Smart selection (Multiple Layers)` | ჭკვიანი მონიშვნა (რამდენიმე შრე) | No |
| `Clear selection` | მონიშვნის მოხსნა | **No** — only deselects |
| `Delete selected` | მონიშნულის წაშლა | **Yes** — deletes data |

!!! danger "Two adjacent entries"
    They sit directly above one another in the menu. Georgian `მოხსნა` (lift/remove) and
    `წაშლა` (delete) are far enough apart that they cannot be confused — a deliberate
    choice.

---

## Everything else — `FiberQPlugin`

The largest group, 132 strings. The main buttons:

| Button | Georgian | What it does |
|---|---|---|
| `Validate project` | პროექტის ვალიდაცია | The 14 rules → [Validation](validation.md) |
| `Check (health check)` | შემოწმება (მდგომარეობის შემოწმება) | A **different** feature — data integrity |
| `BOM report (XLSX/CSV)` | მასალების ნუსხა — BOM (XLSX/CSV) | Bill of materials |
| `Recalculate lengths…` | სიგრძეების გადათვლა… | Recomputes from geometry |
| `Publish to PostGIS` | PostGIS-ში გამოქვეყნება | |
| `Preview Map` | წინასწარი დათვალიერების რუკა | PostGIS connection from `config.ini` |
| `Create Service Area` | მომსახურების ზონის შექმნა | Buffer around the selection |
| `Branch info` | განშტოების ინფორმაცია | How many cables meet at a point |
| `Relations` | ოპტიკური კავშირები | End-to-end logical links |
| `List of latent elements` | შუალედური ელემენტების სია | [What these are](../network/elements.md) |
| `Color catalog` | ბოჭკოს ფერთა კოდი | **Not** a symbology palette |
| `Cut infrastructure` | ინფრასტრუქტურის გაჭრა | Geometry split |
| `Fiber break` | ბოჭკოს გაწყვეტა | **A real fault** |
| `Move elements` | ელემენტების გადატანა | Click-move-click |
| `Optical schematic view` | ოპტიკური სქემის ხედი | |
| `Import points` | წერტილების იმპორტი | KML/KMZ/DWG/Shape/GPX |
| `Save all layers to GeoPackage` | ყველა შრის შენახვა GeoPackage-ში | Redirects the project too |

## Shortcuts

| Key | Action |
|---|---|
| `Ctrl+Shift+Z` | Undo (FiberQ) |
| `Ctrl+Shift+Y` | Redo (FiberQ) |
| `R` | Terminal slack |
| `ESC` | Exit the active tool |

`Show shortcuts` lists them all.
