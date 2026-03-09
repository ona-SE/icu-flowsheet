# MDN110UX_P01 — Method Inventory

Unit: MDN110UX_P01.pas (1049 lines)
Form class: TMDN110FX_P01
Purpose: QuickReport print form for ICU quality indicators (alternate form)
Uses: MDCLASS1, MComFunc, TuxCom, VarCom, CComFunc, HisUtil, QuickRpt, jpeg

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | qr_QualityBeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 1006-1030 | QRLabel.Caption assignments from parent form data | LOW |
| 2 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1031-1036 | Action := caFree | LOW |
| 3 | FormDestroy | published | (Sender: TObject) | 1037-1042 | MDN110FX_P01 := Nil | LOW |

VALIDATION: Source has 3 implementations, inventory has 3 rows. Delta = 0%.

## Notes

- Lines 1-1005 are form class declaration with ~950 QRLabel published fields
- qr_QualityBeforePrint (25 lines) is short — populates summary labels
- Structurally similar to MDN110UV_P01 but for a different quality indicator form
