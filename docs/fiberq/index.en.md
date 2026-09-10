# FiberQ

An open-source QGIS plugin for designing fibre optic networks (FTTH/GPON/FTTx).

| | |
|---|---|
| Repository | [vukovicvl/fiberq](https://github.com/vukovicvl/fiberq) |
| Author | Vladimir Vukovic |
| Licence | GPL-3.0-or-later |
| Funding | NLnet NGI0 Commons Fund |
| Tested on | Qt5 and Qt6 |
| Current version | v1.4.0 — validation and reporting |

## What it does

It builds the physical picture of a fibre network **on the map**:

- **Route** — the line cables follow
- **Poles, manholes, ducts** — the supporting infrastructure
- **Cables** — backbone / distribution / drop, underground or aerial
- **Elements** — ODF, OTB, TB, TO, joint closures
- **Slack** — terminal and mid span
- **Buildings** — subscriber premises
- **Service areas** — coverage polygons

And on top of that: validation, a bill of materials, export, publishing to PostGIS.

## Where things are

<div class="grid cards" markdown>

-   :material-toolbox: **[Toolbar](toolbar.md)**

    ---

    Every button and menu — what it does and how it translates.

-   :material-check-decagram: **[Validation](validation.md)**

    ---

    The 14 rules that check a project before handover.

-   :material-database: **[Data model](data-model.md)**

    ---

    Layers, fields, `fiberq_uuid` and the length arithmetic.

</div>

## Installing

From the QGIS plugin manager, or straight from the repository. Qt Linguist, which the
translation work needs, already ships with QGIS:

```
C:\Program Files\QGIS 3.44.5\apps\Qt5\bin\linguist.exe
C:\Program Files\QGIS 4.2.0\apps\qt6\bin\linguist.exe
```

## Language handling

FiberQ has **its own language setting**, independent of QGIS. The logic lives in
`fiberq/i18n/__init__.py` and resolves in this order:

1. `FiberQ/lang` — the plugin's own language selector (**wins**)
2. `locale/userLocale` — the QGIS-wide language
3. The system locale

!!! quote "Why it works this way"
    The code comment explains it: a user may want FiberQ in one language and QGIS in
    another — common where the local fibre vocabulary differs from the language someone
    prefers for the rest of their GIS.

A language change takes effect **after QGIS restarts** — the catalogue is installed once,
when the plugin loads.

!!! bug "`ka` is not in the list yet"
    `_LANGUAGE_NAMES` has no Georgian entry, so the language menu would show `ka` instead
    of `ქართული`. The code tolerates this deliberately (an unknown code falls back to
    itself, so the menu never breaks), but one line fixes it:

    ```python
    'ka': 'ქართული',
    ```

    Offered in [issue #43](https://github.com/vukovicvl/fiberq/issues/43).
