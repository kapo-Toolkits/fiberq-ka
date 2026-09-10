# ბატჩები და პროგრესი

თარგმანი ოთხ ბატჩად გაკეთდა, `docs/TRANSLATING.md`-ის რეკომენდებული რიგით: ჯერ ის, რასაც
მომხმარებელი მუდმივად ხედავს, ბოლოს — შეცდომების ტექსტები.

## პროგრესი

| ბატჩი | კონტექსტი | სტრიქონი | სტატუსი |
|---|---|---:|---|
| 1 | პანელი, მენიუები, ელემენტების სახელები (11 კონტექსტი) | 76 | ✅ |
| 2 | `ValidationRules` | 45 | ✅ |
| 3 | `ValidationReport` + `ValidationPanel` | 53 | ✅ |
| 4 | `FiberQPlugin` | 132 | ✅ |
| | **სულ** | **306** | **100%** |

სრული ცხრილები repo-შია:
[batch 1](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch1.md) ·
[batch 2](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch2.md) ·
[batch 3](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch3.md) ·
[batch 4](https://github.com/kapo-Toolkits/fiberq-ka/blob/main/TRANSLATIONS-batch4.md)

---

## რა ისწავლა თითოეულმა ბატჩმა

### ბატჩი 1 — ტერმინოლოგია იბადება

აქ დაფიქსირდა ის ძირითადი ტერმინები, რომლებზეც დანარჩენი სამი ბატჩი დგას: `ტრასა`,
`მუფტა`, `მარაგი`, `ბოძი`, `ჭა`, `შენობა`. თითოეული გადაწყვეტილება ერთხელ მიიღეს და
შემდეგ მექანიკურად გამოიყენეს.

**გაკვეთილი:** ლექსიკონი თარგმანამდე უნდა არსებობდეს, არა პარალელურად.

### ბატჩი 2 — placeholder-ების ნამდვილი გამოცდა

`ValidationRules`-ში 20 განსხვავებული placeholder-ია, 30 გამოყენებით. ოთხ სტრიქონში
ისინი გადავაადგილე, რადგან ქართული სინტაქსი სხვა რიგს ითხოვს:

```
Cable endpoint is {distance} from {target} -- just outside the {tol} snapping tolerance
კაბელის ბოლო წერტილი {target}-იდან {distance}-ითაა დაშორებული — ეს ოდნავ სცდება
მიბმის დაშვებას ({tol})
```

აქვე გაირკვა, რომ **ბაზის ველების სახელები არ ითარგმნება** — `duzina_m`, `slack_m`,
`total_len_m` სერბულია, მაგრამ სქემის ნაწილია.

### ბატჩი 3 — რიცხვების შეცდომა

`<message numerus="yes">` ფორმებს ჩემი დათვლა ტოვებდა. აღმოჩნდა, რომ `ValidationPanel`
25 სტრიქონია (21-ის ნაცვლად) და `FiberQPlugin` — 132 (123-ის ნაცვლად). სულ **306**, არა
293.

რადგან ეს რიცხვები issue #43-ში უკვე გამოქვეყნებული იყო და მეინთეინერს დოკუმენტაციაში
გადატანა შევთავაზე, [შესწორება დაიდო](https://github.com/vukovicvl/fiberq/issues/43#issuecomment-5607077915).

**გაკვეთილი:** გამოქვეყნებული რიცხვი ვალდებულებაა.

### ბატჩი 4 — კითხვა, რომელიც არ უნდა დამესვა

`FiberQPlugin`-ის შენიშვნებში აღმოჩნდა პასუხი კითხვაზე, რომელიც მეინთეინერს უკვე
დავუსვი — `List of latent elements`. შენიშვნა ზუსტად განმარტავდა ტერმინს.

მიზეზი: ლექსიკონის მომზადებისას მხოლოდ UI-ჯგუფების შენიშვნები წავიკითხე, `FiberQPlugin`-ისა
არა. [კითხვა გამოვიხმე](https://github.com/vukovicvl/fiberq/issues/43#issuecomment-5607207314).

**გაკვეთილი:** ყველა შენიშვნა ჯერ, მერე კითხვები.

---

## ჯვარედინი დუბლიკატები

ცხრა სტრიქონი რამდენიმე კონტექსტში მეორდება. Qt მათ **ცალკე ჩანაწერებად** ინახავს — ანუ
თანხვედრას არაფერი აიძულებს და ხელით უნდა გავაკონტროლოთ:

| სტრიქონი | სად |
|---|---|
| `Undo (FiberQ)` | `FiberQ` + `FiberQPlugin` |
| `Preview Map` | `FiberQ` + `FiberQPlugin` |
| `Placing elements` | `ElementPlacementUI` + `FiberQPlugin` |
| `Route correction` | `RoutingUI` + `FiberQPlugin` |
| `Smart selection` | `SelectionUI` + `FiberQPlugin` |
| `Terminal slack` | `SlackUI` + `FiberQPlugin` |
| `Severity` `Rule` `Layer` `Feature` `Message` `Error` `Warning` | `ValidationPanel` + `ValidationReport` |

---

## რა რჩება

- [ ] მეინთეინერი აგენერირებს `fiberq/i18n/fiberq_ka.ts`-ს
- [ ] სტრიქონების აკრეფა Qt Linguist-ში (placeholder-ებს ავტომატურად შეამოწმებს)
- [ ] PR მხოლოდ `.ts` ფაილით
- [ ] `'ka': 'ქართული',` დამატება `_LANGUAGE_NAMES`-ში
- [ ] `Relations` ტერმინის დაზუსტება ველის სპეციალისტთან
