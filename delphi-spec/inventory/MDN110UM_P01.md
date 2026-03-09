# MDN110UM_P01 — Method Inventory

Unit: MDN110UM_P01.pas (803 lines)
Form class: TMDN110FM_P01
Purpose: QuickReport print form for ICU flowsheet (main print layout)
Uses: VarCom, HisUtil, CComFunc, MComFunc, QuickRpt, AdvGrid, VclTee.Chart

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | qr_IcuBeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 256-700 | FindComponent, QRLabel.Caption assignments, loop over grid rows/cols, chart data population | HIGH |
| 2 | qr_IcuNeedData | published | (Sender: TObject; var MoreData: Boolean) | 701-781 | Sets MoreData := False (single-page report), additional label assignments | MED |
| 3 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 782-787 | Action := caFree | LOW |
| 4 | FormDestroy | published | (Sender: TObject) | 788-793 | MDN110FM_P01 := Nil | LOW |

VALIDATION: Source has 4 implementations, inventory has 4 rows. Delta = 0%.

## Notes

- Lines 1-255 are form class declaration with ~200+ QRLabel/QRMemo published fields
- qr_IcuBeforePrint (445 lines) is the main report population method: reads data from the parent form's grid and populates QRLabel captions
- Uses FindComponent pattern extensively to map field names to QRLabel captions
- Chart components (VclTee) used for graphical data display in the report
