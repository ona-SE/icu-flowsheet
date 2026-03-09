# MDN110UV_P01 — Method Inventory

Unit: MDN110UV_P01.pas (1133 lines)
Form class: TMDN110FV_P01
Purpose: QuickReport print form for ICU quality indicators
Uses: MDCLASS1, MComFunc, TuxCom, VarCom, CComFunc, HisUtil, QuickRpt, jpeg

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | qr_QualityBeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 1062-1114 | QRLabel.Caption assignments from parent form data | MED |
| 2 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1115-1120 | Action := caFree | LOW |
| 3 | FormDestroy | published | (Sender: TObject) | 1121-1126 | MDN110FV_P01 := Nil | LOW |

VALIDATION: Source has 3 implementations, inventory has 3 rows. Delta = 0%.

## Notes

- Lines 1-1061 are form class declaration with ~1000 QRLabel published fields (quality indicator report)
- qr_QualityBeforePrint (53 lines) populates report labels from parent form data
- Uses MDCLASS1 for business object access, jpeg for image support
