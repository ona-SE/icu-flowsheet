# MDN110UM3 — Method Inventory

## Unit Purpose

Small patient/doctor selection dialog form with grid display and ward filtering.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | sbt_PtInfoClick | published | (Sender: TObject) | 56-64 | PatList-like logic | LOW |
| 2 | sbt_ActClick | published | (Sender: TObject) | 65-73 | Action button logic | LOW |
| 3 | bbt_CloseClick | published | (Sender: TObject) | 74-78 | Close | LOW |
| 4 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 79-83 | Action := caFree | LOW |
| 5 | FormDestroy | published | (Sender: TObject) | 84-88 | MDN110FM3 := Nil | LOW |
| 6 | FormShow | published | (Sender: TObject) | 89-104 | Ward combo setup, initial data load | LOW |

VALIDATION: Source has 6 implementations, inventory has 6 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (line 89) → ward combo setup, initial data load
  → [User clicks PtInfo] → sbt_PtInfoClick (line 56)
  → [User clicks Act] → sbt_ActClick (line 65)
  → [User clicks Close] → bbt_CloseClick (line 74) → Close
FormClose (line 79) → Action := caFree
FormDestroy (line 84) → MDN110FM3 := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FM3 | TMDN110FM3 | FormCreate (implicit) | External callers | FormDestroy (set to Nil) |

## Middleware Contract Summary

N/A -- no direct middleware calls in this unit's source.

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| UltraGrid | TUltraGrid | Cells[], RowCount | Patient/doctor list grid |

## Repetitive Handler Analysis

N/A — no repetitive handler groups.
