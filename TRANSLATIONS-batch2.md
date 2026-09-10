# Batch 2 — `ValidationRules` (45)

The validation engine added in v1.4.0. Two kinds of string live here and they read
differently, so they are separated below:

- **Findings and hints** (31) — what the user is told when a rule fails, plus the
  advice line that follows some of them. Full sentences, most carrying placeholders.
- **Rule names** (14) — the title of each check, phrased in English as an assertion of
  the *passing* state (`Cable endpoints are connected`), not as a command. Georgian
  keeps that: they are statements, not instructions.

This is the densest terminology in the catalogue and the real test of
[`GLOSSARY-ka.md`](GLOSSARY-ka.md). It is also where almost every placeholder in the
project appears, so Rule 2 does the most work here.

---

## Findings and hints (31)

| English | ქართული | Note |
|---|---|---|
| Cable endpoint is not connected to any element or cable (tolerance {tol}) | კაბელის ბოლო წერტილი არცერთ ელემენტს და კაბელს არ უკავშირდება (დაშვება {tol}) | |
| Cable endpoint is {distance} from {target} -- just outside the {tol} snapping tolerance; it probably should connect | კაბელის ბოლო წერტილი {target}-იდან {distance}-ითაა დაშორებული — ეს ოდნავ სცდება მიბმის დაშვებას ({tol}); სავარაუდოდ, კავშირი უნდა არსებობდეს | Three placeholders, all reordered to suit Georgian syntax — permitted by Rule 2. `{target}` takes the ablative `-იდან`, `{distance}` the instrumental `-ითაა`; both suffixes sit outside the braces. The `--` becomes an em dash, which is punctuation, not a placeholder. |
| Element is not on or near any cable or route (tolerance {tol}) | ელემენტი არცერთ კაბელზე ან ტრასაზე არ დევს და არც ახლოსაა (დაშვება {tol}) | |
| Referenced cable layer {layer_id} is not in the project | მითითებული საკაბელო შრე {layer_id} პროექტში არ არის | |
| Referenced cable feature {fid} does not exist in layer {layer} | მითითებული საკაბელო ობიექტი {fid} არ არსებობს შრეში {layer} | `feature` → `ობიექტი` (the QGIS sense). See the §6 warning in the glossary. |
| Referenced layer {layer} is not a cable layer | მითითებული შრე {layer} საკაბელო შრე არ არის | |
| Feature is {distance} from the cable it references (tolerance {tol}) -- the cable may have been re-routed | ობიექტი {distance}-ითაა დაშორებული იმ კაბელისგან, რომელსაც მიუთითებს (დაშვება {tol}) — შესაძლოა კაბელის ტრასა შეიცვალა | "re-routed" rendered with `ტრასა`, tying it back to the routing vocabulary. |
| Layer is missing the fiberq_uuid identity field | შრეს აკლია იდენტიფიკაციის ველი fiberq_uuid | `fiberq_uuid` is a database column name — never translated. |
| Re-open the project so migration can add fiberq_uuid, or re-create the layer. | ხელახლა გახსენით პროექტი, რომ მიგრაციამ დაამატოს fiberq_uuid, ან თავიდან შექმენით შრე. | Hint line: imperative, addressed to the user. |
| Feature has no fiberq_uuid value | ობიექტს არ აქვს fiberq_uuid-ის მნიშვნელობა | Case suffix on a bare field name uses a hyphen, as with acronyms. |
| Duplicate fiberq_uuid — the same identity is already used by feature {fid} in layer {layer} | fiberq_uuid დუბლირებულია — იმავე იდენტიფიკატორს უკვე იყენებს ობიექტი {fid} შრეში {layer} | Em dash in the source is already a real em dash — kept. |
| No FiberQ layers found in this project, so nothing was checked. | ამ პროექტში FiberQ-ის შრეები ვერ მოიძებნა, ამიტომ შემოწმება არ ჩატარებულა. | |
| Open a FiberQ project, or create the layers with the FiberQ toolbar. | გახსენით FiberQ-ის პროექტი, ან შექმენით შრეები FiberQ-ის ხელსაწყოთა პანელით. | Hint line. |
| Required field(s) missing or empty: {fields} | სავალდებულო ველ(ებ)ი აკლია ან ცარიელია: {fields} | Optional plural handled the same way as `ელემენტ(ებ)თან` in batch 1. |
| Field {field}: value {value} is not one of the allowed values ({allowed}) | ველი {field}: მნიშვნელობა {value} დაშვებულთა შორის არ არის ({allowed}) | |
| Field {field}: {value} is out of range (expected {bound}) | ველი {field}: {value} დიაპაზონს სცილდება (მოსალოდნელი {bound}) | |
| Length checks skipped: they need either a projected CRS or a project ellipsoid, but this layer uses {crs} with none set | სიგრძის შემოწმება გამოტოვებულია: საჭიროა პროექციული CRS ან პროექტის ელიფსოიდი, ეს შრე კი იყენებს {crs}-ს და არცერთი მითითებული არ არის | |
| Stored {field} ({stored}) does not match the drawn geometry ({computed}) | შენახული {field} ({stored}) არ ემთხვევა დახაზულ გეომეტრიას ({computed}) | "stored" vs "drawn" is the whole point of the rule — `შენახული` vs `დახაზული`. |
| total_len_m ({total}) should equal duzina_m + slack_m ({expected}) | total_len_m ({total}) უნდა უდრიდეს duzina_m + slack_m ({expected}) | `total_len_m`, `duzina_m`, `slack_m` are **column names**, not words — left exactly as they are, including the Serbian `duzina`. |
| duzina_km ({km}) does not match duzina/1000 ({expected}) | duzina_km ({km}) არ ემთხვევა duzina/1000-ს ({expected}) | Same: column names and the arithmetic stay untouched. |
| The project has no coordinate reference system set | პროექტს კოორდინატთა სისტემა მითითებული არ აქვს | |
| Set it in Project -> Properties -> CRS, to the same system the layers use. Features drawn without one cannot be placed reliably. | მიუთითეთ ის მენიუში პროექტი -> თვისებები -> CRS, იმავე სისტემაზე, რომელსაც შრეები იყენებენ. მის გარეშე დახაზული ობიექტების საიმედოდ განთავსება შეუძლებელია. | Menu path uses the QGIS Georgian menu names. The `->` arrows are kept in the source's ASCII form rather than swapped for `→`, so the string matches how QGIS itself writes paths in this catalogue. |
| Layer uses a geographic CRS ({crs}), where the connectivity tolerance is measured in degrees rather than metres | შრე იყენებს გეოგრაფიულ CRS-ს ({crs}), სადაც კავშირის დაშვება მეტრებში კი არა, გრადუსებში იზომება | |
| Reproject to a national grid, or lower the tolerance to a fraction of a degree. | გადაიყვანეთ ეროვნულ საკოორდინატო ბადეზე, ან შეამცირეთ დაშვება გრადუსის წილადამდე. | Hint line. For a Georgian user the "national grid" is UTM 37N/38N or the national system — the string stays generic, as in the English. |
| No ellipsoid could be resolved for {crs}, so lengths cannot be checked | {crs}-სთვის ელიფსოიდი ვერ განისაზღვრა, ამიტომ სიგრძეების შემოწმება შეუძლებელია | Placeholder moved to the front, taking the dative `-სთვის`. |
| FiberQ layers do not all share one CRS: {list} | FiberQ-ის ყველა შრე ერთსა და იმავე CRS-ს არ იყენებს: {list} | |
| Feature has no geometry | ობიექტს არ აქვს გეომეტრია | |
| Line has zero length | ხაზის სიგრძე ნულის ტოლია | |
| Line crosses itself | ხაზი კვეთს საკუთარ თავს | |
| Polygon has zero area | პოლიგონის ფართობი ნულის ტოლია | |
| Polygon boundary is self-intersecting | პოლიგონის საზღვარი კვეთს საკუთარ თავს | Same construction as `Line crosses itself`, deliberately — they are sibling geometry faults. |

## Rule names (14)

These are the titles shown in the results panel's **Rule** column and in the report.
English states the condition that *holds when the check passes*; Georgian does the same.

| English | ქართული | Note |
|---|---|---|
| Cable endpoints are connected | კაბელის ბოლო წერტილები დაკავშირებულია | A1 — topology. |
| Cable endpoints are not near-misses | კაბელის ბოლო წერტილები ოდნავ დაცილებული არ არის | A2. "Near-miss" = just outside the snapping tolerance; `ოდნავ დაცილებული` matches the wording of the corresponding finding above. |
| Elements are attached to the network | ელემენტები ქსელზეა მიბმული | A3. |
| Optical slack references an existing cable | ოპტიკური მარაგი არსებულ კაბელს მიუთითებს | B1 — referential integrity. |
| Fiber break references an existing cable | ბოჭკოს გაწყვეტა არსებულ კაბელს მიუთითებს | B2. Note this is the fibre **fault**, not the route breakpoint. |
| Cable references are spatially coherent | კაბელზე მითითებები სივრცობრივად თანხვედრილია | B3. |
| Feature identity present and unique | ობიექტის იდენტიფიკატორი არსებობს და უნიკალურია | B4 — the `fiberq_uuid` invariant. |
| Required attributes present | სავალდებულო ატრიბუტები არსებობს | C1. |
| Project contains FiberQ layers | პროექტი შეიცავს FiberQ-ის შრეებს | D1. |
| Attribute values within allowed domain | ატრიბუტების მნიშვნელობები დაშვებულთა შორისაა | D2. Worded to match the finding `დაშვებულთა შორის არ არის` above, so a user sees the same phrase pass and fail. |
| Numeric attributes within plausible ranges | რიცხვითი ატრიბუტები გონივრულ დიაპაზონშია | D2. `გონივრული` (reasonable) rather than `დასაშვები` (permitted) — the English says *plausible*, which is a weaker claim than *allowed*, and the two rules must not sound identical. |
| Stored lengths agree with geometry | შენახული სიგრძეები გეომეტრიას ემთხვევა | D3. |
| Coordinate reference systems are consistent | კოორდინატთა სისტემები თანხვედრილია | E1. |
| Geometries are present and well formed | გეომეტრიები არსებობს და გამართულია | E2. |

---

## Self-check against the three rules

- **Rule 1** — no `<source>` touched.
- **Rule 2** — 20 distinct placeholders appear in this batch: `{tol}` ×3, `{distance}` ×2,
  `{target}`, `{layer_id}`, `{fid}` ×2, `{layer}` ×3, `{fields}`, `{field}` ×3, `{value}` ×2,
  `{allowed}`, `{bound}`, `{crs}` ×3, `{stored}`, `{computed}`, `{total}`, `{expected}` ×2,
  `{km}`, `{list}`. Every one is reproduced lowercase, with both braces, exactly as in the
  English. Four strings reorder placeholders to fit Georgian syntax, which Rule 2 permits.
  **Nothing is renamed and nothing is dropped** — Qt Linguist will confirm this
  automatically when the strings are typed in.
- **Rule 3** — nothing compiled.

## Not translated, deliberately

| Token | Why |
|---|---|
| `fiberq_uuid` | Database column name. |
| `total_len_m`, `duzina_m`, `slack_m`, `duzina_km`, `duzina` | Database column names, including the legacy Serbian ones. Translating them would make the message unmatchable against the actual schema. |
| `CRS` | Kept as the acronym in these strings — they are dense enough already, and `CRS` is what the QGIS dialogs say. |
| `->` | Menu-path arrows, kept in the source's ASCII form. |

## Terms this batch added to the glossary

`endpoint` → ბოლო წერტილი · `reference (v.)` → მითითება · `identity` → იდენტიფიკატორი ·
`near-miss` → ოდნავ დაცილება · `self-intersecting` → საკუთარ თავს კვეთს ·
`national grid` → ეროვნული საკოორდინატო ბადე · `plausible range` → გონივრული დიაპაზონი ·
`allowed domain` → დაშვებულ მნიშვნელობათა ნაკრები · `migration` → მიგრაცია ·
`toolbar` → ხელსაწყოთა პანელი

---

## Progress

| | Strings | Status |
|---|---:|---|
| Batch 1 — toolbar, menus, element names | 76 | translated |
| Batch 2 — `ValidationRules` | 45 | translated |
| `ValidationReport` | 28 | to do |
| `ValidationPanel` | 21 | to do |
| `FiberQPlugin` | 123 | to do |
| **Total** | **293 messages / 306 slots** | **121 done (~40%)** |
