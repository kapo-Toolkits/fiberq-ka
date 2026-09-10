# FiberQ ქართულად

[![deploy docs](https://github.com/kapo-Toolkits/fiberq-ka/actions/workflows/deploy.yml/badge.svg)](https://github.com/kapo-Toolkits/fiberq-ka/actions/workflows/deploy.yml)

**📖 საიტი: <https://kapo-toolkits.github.io/fiberq-ka/>** · **[English](https://kapo-toolkits.github.io/fiberq-ka/en/)**

საიტი ორენოვანია: ქართული ძირითადია, ინგლისური `/en/`-ზე. ინგლისურად ჯერ მთავარი გვერდი, [ლექსიკონი](https://kapo-toolkits.github.io/fiberq-ka/en/glossary/) და თარგმანის განყოფილებაა — დანარჩენი გვერდები ქართულზე გადამისამართდება (fallback), ანუ არცერთი ბმული არ იტეხება.

[FiberQ](https://github.com/vukovicvl/fiberq)-ის — ოპტიკური ქსელების დაპროექტების QGIS
პლაგინის — ქართული თარგმანი და სასწავლო ჩანაწერები.

ორი რამ ერთ repo-ში:

1. **სასწავლო ბაზა** — რა არის FTTH ქსელის თითოეული ნაწილი და რას აკეთებს FiberQ-ის
   თითოეული ღილაკი. ავტორი დარგის სპეციალისტი არ არის; ეს ჩანაწერები სწორედ სწავლის
   პროცესშია დაწერილი.
2. **თარგმანის სამუშაო მასალა** — კატალოგის 306 სტრიქონი, ლექსიკონი, upstream მიმოწერა.

---

## თარგმანის სტატუსი

| | |
|---|---|
| upstream issue | [vukovicvl/fiberq#43](https://github.com/vukovicvl/fiberq/issues/43) — ღიაა |
| კატალოგი | `fiberq/i18n/fiberq_ka.ts` — ჯერ არ არსებობს |
| დრაფტში | **306 / 306 (100%)** |
| ველოდებით | მეინთეინერი დააგენერირებს ცარიელ `.ts` ფაილს |

`CONTRIBUTING.md` კრძალავს `.ts` ფაილის თვითონ შექმნას — ის `pylupdate`-ით გენერირდება
კოდიდან. სანამ მოვა, თარგმანი ცხრილებშია მომზადებული, რომ აკრეფა მექანიკური იყოს.

## ფაილები

| ფაილი | რა არის |
|---|---|
| [`GLOSSARY-ka.md`](GLOSSARY-ka.md) | EN→KA ლექსიკონი, ~140 ტერმინი — **ინგლისურად**, upstream-ში გასაგზავნად |
| [`TRANSLATIONS-batch1.md`](TRANSLATIONS-batch1.md) | 76 — პანელი, მენიუები, ელემენტების სახელები |
| [`TRANSLATIONS-batch2.md`](TRANSLATIONS-batch2.md) | 45 — `ValidationRules` |
| [`TRANSLATIONS-batch3.md`](TRANSLATIONS-batch3.md) | 53 — `ValidationReport` + `ValidationPanel` |
| [`TRANSLATIONS-batch4.md`](TRANSLATIONS-batch4.md) | 132 — `FiberQPlugin` |
| `ISSUE-*.md`, `COMMENT-*.md` | upstream მიმოწერის ჩანაწერი |
| `docs/` | საიტის შიგთავსი (ქართულად) |

## საიტის ლოკალურად გაშვება

```bash
pip install -r requirements.txt
mkdocs serve
```

→ <http://127.0.0.1:8000>

`main`-ში push-ის შემდეგ GitHub Actions ავტომატურად აქვეყნებს. Build `--strict` რეჟიმშია,
ანუ გატეხილი ბმული deploy-ს ჩააგდებს.

## რატომ MkDocs და არა Zensical

Zensical (Material for MkDocs-ის გუნდის ახალი გენერატორი) 2026 სექტემბრისთვის **0.0.60**-ია
და `Development Status :: 3 - Alpha`. Material სტაბილურია და `ka` მის 69 UI ენაში შედის.
Zensical `mkdocs.yml`-ს კითხულობს, ანუ მიგრაცია მოგვიანებით მარტივია.

## ლიცენზია

- **შიგთავსი** (`docs/`, ლექსიკონი, ჩანაწერები) — [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **თარგმანი**, როცა FiberQ-ში შევა — GPL-3.0-or-later, პლაგინის ლიცენზიის შესაბამისად
- **FiberQ თვითონ** — © Vladimir Vukovic, GPL-3.0-or-later
