# MDN110UX — Method Inventory (Part 1: Methods 1-57)

Unit: MDN110UX.pas (7746 lines)
Form class: TMDN110FX
Purpose: NICU quality check form — per-duty (Day/Evening/Night) quality indicator entry, save, delete, copy, print. NICU-specific variant of MDN110UV.
Uses: VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1, MDN110UU, MDN110UV_P01, MDN110UX_P01, TpSvc, SComFunc

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1512-1520 | Action := caFree | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 1521-1530 | MDN110FX := Nil | LOW |
| 3 | bbt_CloseClick | published | (Sender: TObject) | 1531-1542 | Close | LOW |
| 4 | FormCreate | published | (Sender: TObject) | 1543-1568 | Initializes form variables | LOW |
| 5 | Initialize | private | () | 1569-1710 | GetSysDate, LoadPatientInfo, SetAssessDateAndCurrentDuty, GetComp, sets nurse/time defaults, disables controls for read-only modes | HIGH |
| 6 | FormShow | published | (Sender: TObject) | 1711-1742 | Initialize, LoadQualityCheck | MED |
| 7 | SetAssessDateAndCurrentDuty | private | (AdtSysDateTime: TDateTime) | 1743-1810 | Determines current duty (D/E/N) from time, sets date picker | MED |
| 8 | DisplayCurrentDuty | private | (AsDuty: string) | 1811-1842 | Highlights current duty tab/panel | LOW |
| 9 | ClearValueOf | private | (AsDuty: String) | 1843-1893 | Clears all field values for a given duty prefix | MED |
| 10 | scrlbx_QualityCheckMouseWheelDown | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 1894-1908 | ScrollBar position adjustment | LOW |
| 11 | scrlbx_QualityCheckMouseWheelUp | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 1909-1924 | ScrollBar position adjustment | LOW |
| 12 | LoadPatientInfo | private | (in_ChkDate: TDate) | 1925-2028 | HmdPatinf.Create, ListPatbat, populates patient info labels | MED |
| 13 | LoadQualityCheck | private | () | 2029-2063 | LoadQualityCheckInfo, LoadQualityCheckResult, DisplayCurrentDuty, SetControlStatusOfDuty | MED |
| 14 | LoadQualityCheckInfo | private | () | 2064-2193 | HmdIcasit.Create, getIcasitlist, FindComponent to populate quality check fields | HIGH |
| 15 | LoadQualityCheckResult | private | () | 2194-2333 | HmdIcuinf.Create, getIcuinflist, FindComponent to populate result fields | HIGH |
| 16 | SaveQualityCheckOfDuty | private | (AsDuty: string): Boolean | 2334-2623 | HmdIcasit.Create, reads all form fields via GetComp, calls setIcasit to save | HIGH |
| 17 | sbt_DSaveClick | published | (Sender: TObject) | 2624-2687 | Confirmation dialog, SaveQualityCheckOfDuty('D'), LoadQualityCheck | MED |
| 18 | IsNoData | private | (AsDuty: string): Boolean | 2688-2770 | Checks if all fields for a duty are empty | MED |
| 19 | sbt_ESaveClick | published | (Sender: TObject) | 2771-2831 | Confirmation dialog, SaveQualityCheckOfDuty('E'), LoadQualityCheck | MED |
| 20 | sbt_NSaveClick | published | (Sender: TObject) | 2832-2893 | Confirmation dialog, SaveQualityCheckOfDuty('N'), LoadQualityCheck | MED |
| 21 | ed_D_ChkNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2894-2907 | SearchUser for nurse lookup on Enter | LOW |
| 22 | ed_E_ChkNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2908-2921 | SearchUser for nurse lookup on Enter | LOW |
| 23 | ed_N_ChkNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2922-2935 | SearchUser for nurse lookup on Enter | LOW |
| 24 | sbt_PreviousClick | published | (Sender: TObject) | 2936-2969 | Decrements date, LoadQualityCheck | LOW |
| 25 | sbt_NextClick | published | (Sender: TObject) | 2970-3005 | Increments date, LoadQualityCheck | LOW |
| 26 | SetControlStatusOfDuty | private | (AsDuty: string) | 3006-3042 | Enables/disables controls based on duty data presence | LOW |
| 27 | dtp_ChkDateCloseUp | published | (Sender: TObject) | 3043-3074 | LoadQualityCheck on date change | LOW |
| 28 | DeleteQualityCheckOfDuty | private | (AsDuty: String): Boolean | 3075-3168 | HmdIcasit.Create, delIcasit, deletes quality check for given duty | HIGH |
| 29 | sbt_DDeleteClick | published | (Sender: TObject) | 3169-3223 | Confirmation dialog, DeleteQualityCheckOfDuty('D'), LoadQualityCheck | MED |
| 30 | sbt_EDeleteClick | published | (Sender: TObject) | 3224-3279 | Confirmation dialog, DeleteQualityCheckOfDuty('E'), LoadQualityCheck | MED |
| 31 | sbt_NDeleteClick | published | (Sender: TObject) | 3280-3334 | Confirmation dialog, DeleteQualityCheckOfDuty('N'), LoadQualityCheck | MED |
| 32 | SetAuthority | private | () | 3335-3344 | Sets user authority level for form controls | LOW |
| 33 | D_B0101_1Click | published | (Sender: TObject) | 3345-3364 | Field click handler (Day duty) | LOW |
| 34 | D_B0102_1Click | published | (Sender: TObject) | 3365-3385 | Field click handler (Day duty) | LOW |
| 35 | D_B0103_1Click | published | (Sender: TObject) | 3386-3406 | Field click handler (Day duty) | LOW |
| 36 | D_B0201_1Click | published | (Sender: TObject) | 3407-3424 | Field click handler (Day duty) | LOW |
| 37 | D_B0401_1Click | published | (Sender: TObject) | 3425-3456 | Field click handler (Day duty) | LOW |
| 38 | D_B0402_1Click | published | (Sender: TObject) | 3457-3469 | Field click handler (Day duty) | LOW |
| 39 | D_B0501_1Click | published | (Sender: TObject) | 3470-3507 | Field click handler (Day duty) | LOW |
| 40 | D_B0601_1Click | published | (Sender: TObject) | 3508-3567 | Field click handler (Day duty) | MED |
| 41 | D_B0701_1Click | published | (Sender: TObject) | 3568-3589 | Field click handler (Day duty) | LOW |
| 42 | D_B0703_5Click | published | (Sender: TObject) | 3590-3605 | Field click handler (Day duty) | LOW |
| 43 | D_C0102_2Exit | published | (Sender: TObject) | 3606-3634 | Intubation date calculation on field exit | LOW |
| 44 | sbt_CalcIntubeClick | published | (Sender: TObject) | 3635-3682 | Calculates intubation duration from dates | MED |
| 45 | D_B0702_1Click | published | (Sender: TObject) | 3683-3727 | Field click handler with special logic | MED |
| 46 | AssignBdScore | private | (Sender: TObject) | 3728-3783 | Calculates and assigns Braden score | MED |
| 47 | D_C0102_2Click | published | (Sender: TObject) | 3784-3813 | Checkbox click with date picker | LOW |
| 48 | SelOrderList | private | () | 3814-3914 | Opens order selection dialog, populates grid | MED |
| 49 | bbt_CancelClick | published | (Sender: TObject) | 3915-3924 | Cancel button handler | LOW |
| 50 | dtp_FromaddChange | published | (Sender: TObject) | 3925-3930 | Date picker change handler | LOW |
| 51 | dtp_FromaddCloseUp | published | (Sender: TObject) | 3931-3937 | Date picker close handler | LOW |
| 52 | bbt_AddClick | published | (Sender: TObject) | 3938-3948 | Add button handler | LOW |
| 53 | E_B0302_1EClick | published | (Sender: TObject) | 3949-3969 | Field click handler (Evening duty, special) | LOW |
| 54 | ugd_AddListDblClick | published | (Sender: TObject) | 3970-3977 | Grid double-click handler | LOW |
| 55 | GridClear | private | (in_Grid: TUltraGrid) | 3978-4004 | Clears all grid cells | LOW |
| 56 | D_B0505_1Click | published | (Sender: TObject) | 4005-4035 | Field click handler (Day duty) | LOW |
| 57 | D_B0607_1Click | published | (Sender: TObject) | 4036-4082 | Field click handler (Day duty) | LOW |
# MDN110UX — Method Inventory (Part 2: Methods 58-113)

## Method Inventory (continued)

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 58 | D_B0401_4EClick | published | (Sender: TObject) | 4083-4142 | Pain score field click handler (Day duty) | MED |
| 59 | AssignPainScore | private | (Sender: TObject) | 4143-4246 | Calculates and assigns pain score from component values | MED |
| 60 | bbt_PrintClick | published | (Sender: TObject) | 4247-4572 | Creates MDN110FX_P01, populates QRLabels from form fields, Preview/Print | HIGH |
| 61 | AutoScanPrint | private | () | 4573-4626 | Automated print via barcode scan (legacy) | MED |
| 62 | D_B0302_1Click | published | (Sender: TObject) | 4627-4636 | Field click handler (Day duty) | LOW |
| 63 | D_B0301_1Click | published | (Sender: TObject) | 4637-4653 | Field click handler (Day duty) | LOW |
| 64 | D_B0609_1Click | published | (Sender: TObject) | 4654-4717 | Field click handler (Day duty) | MED |
| 65 | E_B0101_1Click | published | (Sender: TObject) | 4718-4732 | Field click handler (Evening duty) | LOW |
| 66 | E_B0102_1Click | published | (Sender: TObject) | 4733-4750 | Field click handler (Evening duty) | LOW |
| 67 | E_B0103_1Click | published | (Sender: TObject) | 4751-4766 | Field click handler (Evening duty) | LOW |
| 68 | E_B0201_1Click | published | (Sender: TObject) | 4767-4782 | Field click handler (Evening duty) | LOW |
| 69 | E_B0301_1Click | published | (Sender: TObject) | 4783-4797 | Field click handler (Evening duty) | LOW |
| 70 | E_B0302_1Click | published | (Sender: TObject) | 4798-4806 | Field click handler (Evening duty) | LOW |
| 71 | E_B0401_1Click | published | (Sender: TObject) | 4807-4839 | Field click handler (Evening duty) | LOW |
| 72 | E_B0501_1Click | published | (Sender: TObject) | 4840-4871 | Field click handler (Evening duty) | LOW |
| 73 | E_B0505_1Click | published | (Sender: TObject) | 4872-4905 | Field click handler (Evening duty) | LOW |
| 74 | E_B0601_1Click | published | (Sender: TObject) | 4906-4962 | Field click handler (Evening duty) | MED |
| 75 | E_B0609_1Click | published | (Sender: TObject) | 4963-5025 | Field click handler (Evening duty) | MED |
| 76 | E_B0701_1Click | published | (Sender: TObject) | 5026-5046 | Field click handler (Evening duty) | LOW |
| 77 | N_B0101_1Click | published | (Sender: TObject) | 5047-5061 | Field click handler (Night duty) | LOW |
| 78 | N_B0102_1Click | published | (Sender: TObject) | 5062-5078 | Field click handler (Night duty) | LOW |
| 79 | N_B0103_1Click | published | (Sender: TObject) | 5079-5094 | Field click handler (Night duty) | LOW |
| 80 | N_B0201_1Click | published | (Sender: TObject) | 5095-5110 | Field click handler (Night duty) | LOW |
| 81 | N_B0301_1Click | published | (Sender: TObject) | 5111-5125 | Field click handler (Night duty) | LOW |
| 82 | N_B0302_1Click | published | (Sender: TObject) | 5126-5134 | Field click handler (Night duty) | LOW |
| 83 | N_B0401_1Click | published | (Sender: TObject) | 5135-5168 | Field click handler (Night duty) | LOW |
| 84 | E_B0402_1Click | published | (Sender: TObject) | 5169-5180 | Field click handler (Evening duty) | LOW |
| 85 | N_B0402_1Click | published | (Sender: TObject) | 5181-5192 | Field click handler (Night duty) | LOW |
| 86 | N_B0501_1Click | published | (Sender: TObject) | 5193-5223 | Field click handler (Night duty) | LOW |
| 87 | N_B0505_1Click | published | (Sender: TObject) | 5224-5256 | Field click handler (Night duty) | LOW |
| 88 | N_B0601_1Click | published | (Sender: TObject) | 5257-5313 | Field click handler (Night duty) | MED |
| 89 | N_B0609_1Click | published | (Sender: TObject) | 5314-5377 | Field click handler (Night duty) | MED |
| 90 | N_B0701_1Click | published | (Sender: TObject) | 5378-5398 | Field click handler (Night duty) | LOW |
| 91 | D_B0801_4Click | published | (Sender: TObject) | 5399-5411 | Field click handler (Day duty) | LOW |
| 92 | E_B0801_4Click | published | (Sender: TObject) | 5412-5423 | Field click handler (Evening duty) | LOW |
| 93 | N_B0801_4Click | published | (Sender: TObject) | 5424-5437 | Field click handler (Night duty) | LOW |
| 94 | D_B0504_1Click | published | (Sender: TObject) | 5438-5455 | Field click handler (Day duty) | LOW |
| 95 | E_B0504_1Click | published | (Sender: TObject) | 5456-5473 | Field click handler (Evening duty) | LOW |
| 96 | N_B0504_1Click | published | (Sender: TObject) | 5474-5491 | Field click handler (Night duty) | LOW |
| 97 | D_B0508_1Click | published | (Sender: TObject) | 5492-5508 | Field click handler (Day duty) | LOW |
| 98 | E_B0508_1Click | published | (Sender: TObject) | 5509-5526 | Field click handler (Evening duty) | LOW |
| 99 | N_B0508_1Click | published | (Sender: TObject) | 5527-5543 | Field click handler (Night duty) | LOW |
| 100 | E_B0703_5Click | published | (Sender: TObject) | 5544-5555 | Field click handler (Evening duty) | LOW |
| 101 | N_B0703_5Click | published | (Sender: TObject) | 5556-5571 | Field click handler (Night duty) | LOW |
| 102 | bbt_SelectClick | published | (Sender: TObject) | 5572-5603 | Opens patient selection dialog | LOW |
| 103 | bbt_ToNrRecordDClick | published | (Sender: TObject) | 5604-7025 | Reads all quality check fields for D/E/N duty, builds nursing record string, calls TpSvc for EMR integration | HIGH |
| 104 | GetIcuInfo | private | (sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String) | 7026-7162 | HmdIcuinf.Create, getIcuinflist, populates ICU info fields | HIGH |
| 105 | bbt_OkClick | published | (Sender: TObject) | 7163-7180 | OK button handler | LOW |
| 106 | AutoScanPrint_New | private | () | 7181-7227 | Automated print via barcode scan (new version) | MED |
| 107 | sbt_DCopyClick | published | (Sender: TObject) | 7228-7292 | Confirmation dialog, CopyLastQualCheckOfDuty('D'), LoadQualityCheck | MED |
| 108 | sbt_ECopyClick | published | (Sender: TObject) | 7293-7357 | Confirmation dialog, CopyLastQualCheckOfDuty('E'), LoadQualityCheck | MED |
| 109 | sbt_NCopyClick | published | (Sender: TObject) | 7358-7424 | Confirmation dialog, CopyLastQualCheckOfDuty('N'), LoadQualityCheck | MED |
| 110 | CopyLastQualCheckOfDuty | private | (AsDuty: String): Boolean | 7425-7526 | HmdIcasit.Create, getIcasitlist, copies previous duty's quality check data | HIGH |
| 111 | D_B0401_3EClick | published | (Sender: TObject) | 7527-7576 | Pain score field click handler (Day duty) | MED |
| 112 | AssignPainRslt | private | (Sender: TObject) | 7577-7667 | Calculates and assigns pain result from component values | MED |
| 113 | bt_printClick | published | (Sender: TObject) | 7668-7746 | Alternative print handler | MED |

VALIDATION: Source has 113 implementations, inventory has 113 rows. Delta = 0%.

## Event Chain Map

```
FormCreate → FormShow → Initialize → LoadPatientInfo + SetAssessDateAndCurrentDuty
  → LoadQualityCheck → LoadQualityCheckInfo + LoadQualityCheckResult + DisplayCurrentDuty + SetControlStatusOfDuty
  → [User edits fields] → {D|E|N}_B{NNNN}_{N}Click handlers
  → [User clicks Save] → sbt_{D|E|N}SaveClick → SaveQualityCheckOfDuty → HmdIcasit.setIcasit
  → [User clicks Delete] → sbt_{D|E|N}DeleteClick → DeleteQualityCheckOfDuty → HmdIcasit.delIcasit
  → [User clicks Copy] → sbt_{D|E|N}CopyClick → CopyLastQualCheckOfDuty → HmdIcasit.getIcasitlist
  → [User clicks Print] → bbt_PrintClick → MDN110FX_P01 report
  → [User clicks ToNrRecord] → bbt_ToNrRecordDClick → TpSvc EMR integration
  → [Score changes] → AssignBdScore / AssignPainScore / AssignPainRslt → auto-calculate scores
FormClose → Action := caFree
FormDestroy → MDN110FX := Nil
```

## Middleware Contract Summary

Same as MDN110UV: HmdIcasit (getIcasitlist, setIcasit, delIcasit), HmdIcuinf (getIcuinflist), HmdPatinf (ListPatbat), TpSvc (EMR integration).

## Repetitive Handler Analysis

D/E/N triplication for field sections: B0101, B0102, B0103, B0201, B0301, B0302, B0401, B0402, B0501, B0504, B0505, B0508, B0601, B0609, B0701, B0703, B0801
Triplicated action handlers: sbt_{D|E|N}SaveClick, sbt_{D|E|N}DeleteClick, sbt_{D|E|N}CopyClick, ed_{D|E|N}_ChkNursNameKeyDown

Unique methods: AssignBdScore, AssignPainScore, AssignPainRslt, SelOrderList, GridClear, sbt_CalcIntubeClick, D_B0702_1Click, D_B0401_4EClick, D_B0401_3EClick, D_C0102_2Exit/Click

KEY MIGRATION NOTE: NICU-specific variant of MDN110UV. Structurally identical pattern. bbt_ToNrRecordDClick is 1422 lines. ~65 of 113 methods (58%) are D/E/N triplicates.
