# MDN110UM_P02 — Method Inventory

Unit: MDN110UM_P02.pas (798 lines)
Form class: TMDN110FM_P02
Purpose: QuickReport print form for ICU flowsheet (A4 alternate layout)
Uses: VarCom, HisUtil, CComFunc, MComFunc, QuickRpt, AdvGrid, VclTee.Chart

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | qr_Icu_A4BeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 249-697 | FindComponent, QRLabel.Caption assignments, loop over grid rows/cols, chart data population | HIGH |
| 2 | qr_Icu_A4NeedData | published | (Sender: TObject; var MoreData: Boolean) | 698-778 | Sets MoreData := False, additional label assignments | MED |
| 3 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 779-784 | Action := caFree | LOW |
| 4 | FormDestroy | published | (Sender: TObject) | 785-790 | MDN110FM_P02 := Nil | LOW |

VALIDATION: Source has 4 implementations, inventory has 4 rows. Delta = 0%.

## Notes

- Near-identical structure to MDN110UM_P01 but formatted for A4 paper size
- qr_Icu_A4BeforePrint (449 lines) mirrors qr_IcuBeforePrint with layout adjustments
- Lines 1-248 are form class declaration with QRLabel/QRMemo published fields
- Same chart/grid data population pattern as P01
