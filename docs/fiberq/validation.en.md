# Validation

The headline feature of v1.4.0: **14 rules** that check the whole project. Results appear
in two places — a live panel inside QGIS, and an exported report.

## Why it exists

The report's two verdicts explain the whole idea in one phrase each:

> `No errors — project is structurally sound`

> `Errors found — not ready to hand over`

So this is a **pre-handover check**. "Hand over" is the delivery of the design to the
client or the authority — Georgian `ჩაბარება`.

## The 14 rules

In English a rule name states the condition that holds **when the check passes** — an
assertion, not a command. Georgian keeps that.

### Topology and connectivity

| # | Rule | Georgian |
|---|---|---|
| A1 | `Cable endpoints are connected` | კაბელის ბოლო წერტილები დაკავშირებულია |
| A2 | `Cable endpoints are not near-misses` | კაბელის ბოლო წერტილები ოდნავ დაცილებული არ არის |
| A3 | `Elements are attached to the network` | ელემენტები ქსელზეა მიბმული |

!!! info "What a \"near-miss\" is"
    An endpoint that falls **just outside the snapping tolerance** — not connected, but
    clearly meant to be. It is a separate rule from A1 because it is a different problem:
    A1 says "connects to nothing", A2 says "almost connects".

### Referential integrity

| # | Rule | Georgian |
|---|---|---|
| B1 | `Optical slack references an existing cable` | ოპტიკური მარაგი არსებულ კაბელს მიუთითებს |
| B2 | `Fiber break references an existing cable` | ბოჭკოს გაწყვეტა არსებულ კაბელს მიუთითებს |
| B3 | `Cable references are spatially coherent` | კაბელზე მითითებები სივრცობრივად თანხვედრილია |
| B4 | `Feature identity present and unique` | ობიექტის იდენტიფიკატორი არსებობს და უნიკალურია |

B3 catches the case where a feature has drifted **geographically** away from the cable it
references. The message names the likely cause outright: *"the cable may have been
re-routed."*

### Attributes and domains

| # | Rule | Georgian |
|---|---|---|
| C1 | `Required attributes present` | სავალდებულო ატრიბუტები არსებობს |
| D1 | `Project contains FiberQ layers` | პროექტი შეიცავს FiberQ-ის შრეებს |
| D2 | `Attribute values within allowed domain` | ატრიბუტების მნიშვნელობები დაშვებულთა შორისაა |
| D2 | `Numeric attributes within plausible ranges` | რიცხვითი ატრიბუტები გონივრულ დიაპაზონშია |
| D3 | `Stored lengths agree with geometry` | შენახული სიგრძეები გეომეტრიას ემთხვევა |

!!! tip "`allowed` is not `plausible`"
    Two similar rules, and the English distinguishes them deliberately: an `allowed domain`
    is a strict **enumeration** of permitted values; a `plausible range` is a **soft**
    sanity check. Georgian `დაშვებული` vs `გონივრული` preserves that difference.

### CRS and geometry

| # | Rule | Georgian |
|---|---|---|
| E1 | `Coordinate reference systems are consistent` | კოორდინატთა სისტემები თანხვედრილია |
| E2 | `Geometries are present and well formed` | გეომეტრიები არსებობს და გამართულია |

E2 catches five specific faults:

- `Feature has no geometry`
- `Line has zero length`
- `Line crosses itself`
- `Polygon has zero area`
- `Polygon boundary is self-intersecting`

---

## The CRS trap

One E1 message deserves separate attention because it has a practical consequence:

> `Layer uses a geographic CRS ({crs}), where the connectivity tolerance is measured in
> degrees rather than metres`

**If a layer is in a geographic CRS (EPSG:4326, say), the snapping tolerance is measured in
degrees, not metres.** A "5 metre tolerance" is then actually 5 degrees — roughly 550 km.

The advice is in the message itself: *"Reproject to a national grid, or lower the tolerance
to a fraction of a degree."*

!!! example "For Georgia"
    That means UTM 37N / 38N or the national system. The FiberQ string is generic
    ("national grid") and the Georgian translation stays generic too —
    `ეროვნული საკოორდინატო ბადე`.

Also: **length cannot be measured without an ellipsoid.** If there is neither a projected
CRS nor a project ellipsoid, the length checks are skipped.

---

## Where results appear

=== "Panel (live)"

    `ValidationPanel` — a dock inside QGIS: a five-column table (severity / rule / layer /
    feature / message), three filters, and `Re-run` and `Export report` buttons.

    Three levels: **Error** · **Warning** · **Info**

=== "Report (exported)"

    `ValidationReport` — the document you hand over: verdict, totals, run metadata (CRS,
    schema version, plugin version, timestamp), the issues table and issues by layer.

    **JSON and CSV** of the same run are available from the same export menu.

!!! note "Seven strings appear in both"
    `Severity`, `Rule`, `Layer`, `Feature`, `Message`, `Error` and `Warning` occur in both
    contexts. Qt stores them separately — so the Georgian translation has to be kept
    identical by hand, or a user will assume the two views show different data.
