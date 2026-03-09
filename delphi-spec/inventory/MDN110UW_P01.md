# MDN110UW_P01 — Method Inventory

Unit: MDN110UW_P01.pas (1268 lines)
Form class: TMDN110FW_P01
Purpose: QuickReport print form for ICU nursing assessment (alternate form)
Uses: MDCLASS1, MComFunc, TuxCom, VarCom, CComFunc, HisUtil, QuickRpt, jpeg

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1231-1236 | Action := caFree | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 1237-1241 | MDN110FW_P01 := Nil | LOW |
| 3 | qr_AssessBeforePrint | published | (Sender: TCustomQuickRep; var PrintReport: Boolean) | 1242-1268 | QRLabel.Caption assignments from parent form data | LOW |

VALIDATION: Source has 3 implementations, inventory has 3 rows. Delta = 0%.

## Notes

- Lines 1-1230 are form class declaration with ~1170 QRLabel/QRMemo published fields
- qr_AssessBeforePrint (27 lines) is short — populates a few summary labels
- Structurally similar to MDN110UU_P01 but for a different assessment form
