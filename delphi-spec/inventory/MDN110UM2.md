# MDN110UM2 — Method Inventory

## Unit Purpose

ICU patient monitoring detail view (Tab 2) displaying assessment data in read-only checkboxes and radio buttons.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | bbt_CloseClick | published | (Sender: TObject) | 560-564 | Close | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 565-569 | MDN110FM2 := Nil | LOW |
| 3 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 570-574 | Action := caFree | LOW |
| 4 | FormShow | published | (Sender: TObject) | 575-583 | Tab setup, label population | LOW |
| 5 | pc_ICUChange | published | (Sender: TObject) | 584-596 | Tab page change handling | LOW |

VALIDATION: Source has 5 implementations, inventory has 5 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (line 575) → tab setup, label population
  → [User changes tab] → pc_ICUChange (line 584)
  → [User clicks Close] → bbt_CloseClick (line 560) → Close
FormClose (line 570) → Action := caFree
FormDestroy (line 565) → MDN110FM2 := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FM2 | TMDN110FM2 | FormCreate (implicit) | External callers | FormDestroy (set to Nil) |

## Middleware Contract Summary

N/A -- no middleware calls in this unit.

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| UltraGrid | TUltraGrid | (display only) | Grid display |

## Repetitive Handler Analysis

N/A — no repetitive handler groups.
