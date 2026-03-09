# MDN110UO_P01 — Method Inventory

## Unit Purpose

QuickReport print form for ICU information data, rendering patient ICU info fields as a printable report.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 640-644 | Action := caFree | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 645-649 | MDN110FO_P01 := Nil | LOW |
| 3 | qr_Report1BeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 650-662 | Report setup, G_LOCATE check | LOW |

VALIDATION: Source has 3 implementations, inventory has 3 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (implicit) → report data populated by calling form
  → qr_Report1BeforePrint (line 650) → report setup
FormClose (line 640) → Action := caFree
FormDestroy (line 645) → MDN110FO_P01 := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FO_P01 | TMDN110FO_P01 | FormCreate (implicit) | MDN110UO (calling form) | FormDestroy (set to Nil) |

## Middleware Contract Summary

N/A -- no middleware calls. Print-only form.

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| QuickReport | TQuickRep | Preview, Print, BeforePrint | Report generation |
| QuickReport | TQRLabel | Caption | Report field labels |
| QuickReport | TQRShape | (display) | Report grid lines |

## Repetitive Handler Analysis

N/A — no repetitive handler groups.
