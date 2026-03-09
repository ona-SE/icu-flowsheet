# MDN110UU_P01 — Method Inventory

Unit: MDN110UU_P01.pas (1223 lines)
Form class: TMDN110FU_P01
Purpose: QuickReport print form for ICU nursing assessment
Uses: MDCLASS1, MComFunc, TuxCom, VarCom, CComFunc, HisUtil, QuickRpt, jpeg

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1159-1164 | Action := caFree | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 1165-1169 | MDN110FU_P01 := Nil | LOW |
| 3 | qr_AssessBeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 1170-1223 | QRLabel.Caption assignments from parent form data | MED |

VALIDATION: Source has 3 implementations, inventory has 3 rows. Delta = 0%.

## Notes

- Lines 1-1158 are form class declaration with ~1100 QRLabel/QRMemo published fields (nursing assessment has many data points)
- qr_AssessBeforePrint (54 lines) is relatively short — most data is pre-populated in the form designer or passed from the parent form
- Uses MDCLASS1 for business object access, jpeg for image support in report
