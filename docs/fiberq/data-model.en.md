# Data model

!!! warning "This page is incomplete"
    What follows is what I know **for certain** from the catalogue strings and the code.
    Where I am inferring, it says so. The full layer schema is in the repository and still
    needs checking — noted in the [journal](../journal.md).

## Layers

Confirmed names (the code looks them up by these literal strings):

| Layer | Geometry | How I know |
|---|---|---|
| `Poles` | point | `Unable to create or find the Poles layer!` / `Layer 'Poles' not found!` |
| `Route` | line | `Route layer 'Route' not found!` |
| `ODF` | point | `<extracomment>`: *"it doubles as the layer name"* |
| Service Area | polygon | `entry into Service Area layer` |
| Optical slacks | point | *"the group of slack tools, and the map layer they write to"* |

!!! danger "Layer names are not translated"
    `'Poles'` and `'Route'` in quotes are **actual layer names**, not words. They stay
    untouched in the translation — otherwise the message stops matching reality. The
    unquoted "Route layer" *is* translated: `ტრასის შრე 'Route' ვერ მოიძებნა!`

## The buildings layer

The field set that confirms the `Object` = building reading:

- number of floors
- number of basement levels
- street
- house number

This is exactly the list the maintainer cites as proof that `Object` means a **building**
rather than a generic GIS object.

---

## Identity — `fiberq_uuid`

Every feature carries a unique identifier in the field **`fiberq_uuid`**.

Validation rule **B4** checks three things:

| Message | Georgian |
|---|---|
| `Layer is missing the fiberq_uuid identity field` | შრეს აკლია იდენტიფიკაციის ველი `fiberq_uuid` |
| `Feature has no fiberq_uuid value` | ობიექტს არ აქვს `fiberq_uuid`-ის მნიშვნელობა |
| `Duplicate fiberq_uuid` | `fiberq_uuid` დუბლირებულია |

If the field is missing, the fix is offered too: *"Re-open the project so migration can add
fiberq_uuid, or re-create the layer."* — so there is a **migration mechanism** that adds
the field when the project opens.

!!! info "Schema version"
    The report has its own `Schema version` field, so the schema is versioned and
    migrations apply in sequence. (Repository issues #21 and #22 confirm it: *canonical
    schema model + project schema_version marker*, and *versioned schema migration runner +
    uuid identity invariant*.)

---

## Length fields

The Serbian heritage shows here directly — the field names are Serbian and **are not
translated**:

| Field | What it is |
|---|---|
| `duzina_m` | Length in metres (sr *dužina* = length) |
| `duzina_km` | Length in kilometres |
| `slack_m` | Slack in metres |
| `total_len_m` | Total length in metres |

### Two invariants

Validation checks two arithmetic relationships:

```
total_len_m  ==  duzina_m + slack_m
duzina_km    ==  duzina / 1000
```

The corresponding messages (D3):

- `total_len_m ({total}) should equal duzina_m + slack_m ({expected})`
- `duzina_km ({km}) does not match duzina/1000 ({expected})`
- `Stored {field} ({stored}) does not match the drawn geometry ({computed})`

### Stored vs drawn

This distinction is the whole of rule D3:

- **Stored length** (`stored`) — the number written in the attribute
- **Drawn geometry** (`computed`) — the real length of the line on the map

If someone moved the route, the geometry changed while the attribute stayed behind → an
issue. `Recalculate lengths` is what fixes it.

!!! quote "How it is measured"
    > Lengths are measured on the project ellipsoid, the same way the QGIS measure tool
    > does. Slack values are read but never changed.

---

## CRS

- The project **must have** a CRS set (E1)
- All FiberQ layers must use the **same** CRS
- A geographic CRS is a problem: the snapping tolerance is measured in degrees
- Measuring length needs **either** a projected CRS **or** a project ellipsoid

[:octicons-arrow-right-24: The CRS trap in detail](validation.md)

---

## Still to check

- [ ] The full list of layers and each one's fields
- [ ] Cable attributes — type, subtype, capacity
- [ ] The elements layer — one, or several by type?
- [ ] How `Relations` are stored
- [ ] The storage format for a latent element (distance along the cable)
