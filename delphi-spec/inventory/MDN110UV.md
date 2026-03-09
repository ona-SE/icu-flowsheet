# MDN110UV — Method Inventory (Part 1: Methods 1-58)

Unit: MDN110UV.pas (8125 lines)
Form class: TMDN110FV
Purpose: ICU quality check form — per-duty (Day/Evening/Night) quality indicator entry, save, delete, copy, print
Uses: VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1, MDN110UU, MDN110UV_P01, TpSvc, SComFunc

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1622-1633 | Action := caFree | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 1634-1646 | MDN110FV := Nil | LOW |
| 3 | bbt_CloseClick | published | (Sender: TObject) | 1647-1661 | Close | LOW |
| 4 | FormCreate | published | (Sender: TObject) | 1662-1689 | Initializes form variables | LOW |
| 5 | Initialize | private | () | 1690-1884 | GetSysDate, LoadPatientInfo, SetAssessDateAndCurrentDuty, GetComp, sets nurse/time defaults, disables controls for read-only modes | HIGH |
| 6 | FormShow | published | (Sender: TObject) | 1885-1997 | Initialize, LoadQualityCheck | HIGH |
| 7 | SetAssessDateAndCurrentDuty | private | (AdtSysDateTime: TDateTime) | 1998-2063 | Determines current duty (D/E/N) from time, sets date picker | MED |
| 8 | DisplayCurrentDuty | private | (AsDuty: string) | 2064-2098 | Highlights current duty tab/panel | LOW |
| 9 | ClearValueOf | private | (AsDuty: String) | 2099-2151 | Clears all field values for a given duty prefix | MED |
| 10 | scrlbx_QualityCheckMouseWheelDown | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 2152-2168 | ScrollBar position adjustment | LOW |
| 11 | scrlbx_QualityCheckMouseWheelUp | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 2169-2228 | ScrollBar position adjustment | LOW |
| 12 | LoadPatientInfo | private | () | 2229-2315 | HmdPatinf.Create, ListPatbat, populates patient info labels | MED |
| 13 | LoadQualityCheck | private | () | 2316-2352 | LoadQualityCheckInfo, LoadQualityCheckResult, DisplayCurrentDuty, SetControlStatusOfDuty | MED |
| 14 | LoadQualityCheckInfo | private | () | 2353-2484 | HmdIcasit.Create, getIcasitlist, FindComponent to populate quality check fields for all 3 duties | HIGH |
| 15 | LoadQualityCheckResult | private | () | 2485-2621 | HmdIcuinf.Create, getIcuinflist, FindComponent to populate result fields for all 3 duties | HIGH |
| 16 | SaveQualityCheckOfDuty | private | (AsDuty: string): Boolean | 2622-2893 | HmdIcasit.Create, reads all form fields via GetComp, calls setIcasit to save | HIGH |
| 17 | sbt_DSaveClick | published | (Sender: TObject) | 2894-2955 | Confirmation dialog, SaveQualityCheckOfDuty('D'), LoadQualityCheck | MED |
| 18 | IsNoData | private | (AsDuty: string): Boolean | 2956-3034 | Checks if all fields for a duty are empty | MED |
| 19 | sbt_ESaveClick | published | (Sender: TObject) | 3035-3093 | Confirmation dialog, SaveQualityCheckOfDuty('E'), LoadQualityCheck | MED |
| 20 | sbt_NSaveClick | published | (Sender: TObject) | 3094-3153 | Confirmation dialog, SaveQualityCheckOfDuty('N'), LoadQualityCheck | MED |
| 21 | ed_D_ChkNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 3154-3169 | SearchUser for nurse lookup on Enter | LOW |
| 22 | ed_E_ChkNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 3170-3185 | SearchUser for nurse lookup on Enter | LOW |
| 23 | ed_N_ChkNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 3186-3201 | SearchUser for nurse lookup on Enter | LOW |
| 24 | sbt_PreviousClick | published | (Sender: TObject) | 3202-3232 | Decrements date, LoadQualityCheck | LOW |
| 25 | sbt_NextClick | published | (Sender: TObject) | 3233-3277 | Increments date, LoadQualityCheck | LOW |
| 26 | SetControlStatusOfDuty | private | (AsDuty: string) | 3278-3315 | Enables/disables controls based on duty data presence | LOW |
| 27 | dtp_ChkDateCloseUp | published | (Sender: TObject) | 3316-3344 | LoadQualityCheck on date change | LOW |
| 28 | DeleteQualityCheckOfDuty | private | (AsDuty: String): Boolean | 3345-3442 | HmdIcasit.Create, delIcasit, deletes quality check for given duty | HIGH |
| 29 | sbt_DDeleteClick | published | (Sender: TObject) | 3443-3499 | Confirmation dialog, DeleteQualityCheckOfDuty('D'), LoadQualityCheck | MED |
| 30 | sbt_EDeleteClick | published | (Sender: TObject) | 3500-3556 | Confirmation dialog, DeleteQualityCheckOfDuty('E'), LoadQualityCheck | MED |
| 31 | sbt_NDeleteClick | published | (Sender: TObject) | 3557-3613 | Confirmation dialog, DeleteQualityCheckOfDuty('N'), LoadQualityCheck | MED |
| 32 | SetAuthority | private | () | 3614-3626 | Sets user authority level for form controls | LOW |
| 33 | D_B0101_1Click | published | (Sender: TObject) | 3627-3647 | Field click handler (Day duty) | LOW |
| 34 | E_B0101_1Click | published | (Sender: TObject) | 3648-3668 | Field click handler (Evening duty) | LOW |
| 35 | N_B0101_1Click | published | (Sender: TObject) | 3669-3689 | Field click handler (Night duty) | LOW |
| 36 | D_B0102_1Click | published | (Sender: TObject) | 3690-3724 | Field click handler (Day duty) | LOW |
| 37 | E_B0102_1Click | published | (Sender: TObject) | 3725-3758 | Field click handler (Evening duty) | LOW |
| 38 | N_B0102_1Click | published | (Sender: TObject) | 3759-3792 | Field click handler (Night duty) | LOW |
| 39 | D_B0103_1Click | published | (Sender: TObject) | 3793-3825 | Field click handler (Day duty) | LOW |
| 40 | E_B0103_1Click | published | (Sender: TObject) | 3826-3858 | Field click handler (Evening duty) | LOW |
| 41 | N_B0103_1Click | published | (Sender: TObject) | 3859-3891 | Field click handler (Night duty) | LOW |
| 42 | D_B0201_1Click | published | (Sender: TObject) | 3892-3919 | Field click handler (Day duty) | LOW |
| 43 | E_B0201_1Click | published | (Sender: TObject) | 3920-3946 | Field click handler (Evening duty) | LOW |
| 44 | N_B0201_1Click | published | (Sender: TObject) | 3947-3973 | Field click handler (Night duty) | LOW |
| 45 | D_B0203_1Click | published | (Sender: TObject) | 3974-3994 | Field click handler (Day duty) | LOW |
| 46 | E_B0203_1Click | published | (Sender: TObject) | 3995-4015 | Field click handler (Evening duty) | LOW |
| 47 | N_B0203_1Click | published | (Sender: TObject) | 4016-4036 | Field click handler (Night duty) | LOW |
| 48 | D_C0203_3Click | published | (Sender: TObject) | 4037-4049 | Checkbox click handler (Day duty) | LOW |
| 49 | E_C0203_3Click | published | (Sender: TObject) | 4050-4062 | Checkbox click handler (Evening duty) | LOW |
| 50 | N_C0203_3Click | published | (Sender: TObject) | 4063-4077 | Checkbox click handler (Night duty) | LOW |
| 51 | D_B0301_1Click | published | (Sender: TObject) | 4078-4090 | Field click handler (Day duty) | LOW |
| 52 | E_B0301_1Click | published | (Sender: TObject) | 4091-4103 | Field click handler (Evening duty) | LOW |
| 53 | N_B0301_1Click | published | (Sender: TObject) | 4104-4118 | Field click handler (Night duty) | LOW |
| 54 | D_B0302_1Click | published | (Sender: TObject) | 4119-4131 | Field click handler (Day duty) | LOW |
| 55 | E_B0302_1Click | published | (Sender: TObject) | 4132-4144 | Field click handler (Evening duty) | LOW |
| 56 | N_B0302_1Click | published | (Sender: TObject) | 4145-4158 | Field click handler (Night duty) | LOW |
| 57 | D_B0401_1Click | published | (Sender: TObject) | 4159-4200 | Field click handler (Day duty) | LOW |
| 58 | E_B0401_1Click | published | (Sender: TObject) | 4201-4242 | Field click handler (Evening duty) | LOW |
# MDN110UV — Method Inventory (Part 2: Methods 59-115)

## Method Inventory (continued)

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 59 | N_B0401_1Click | published | (Sender: TObject) | 4243-4284 | Field click handler (Night duty) | LOW |
| 60 | D_C0402_6Click | published | (Sender: TObject) | 4285-4298 | Checkbox click handler (Day duty) | LOW |
| 61 | E_C0402_6Click | published | (Sender: TObject) | 4299-4312 | Checkbox click handler (Evening duty) | LOW |
| 62 | N_C0402_6Click | published | (Sender: TObject) | 4313-4326 | Checkbox click handler (Night duty) | LOW |
| 63 | D_B0402_1Click | published | (Sender: TObject) | 4327-4340 | Field click handler (Day duty) | LOW |
| 64 | E_B0402_1Click | published | (Sender: TObject) | 4341-4356 | Field click handler (Evening duty) | LOW |
| 65 | N_B0402_1Click | published | (Sender: TObject) | 4357-4370 | Field click handler (Night duty) | LOW |
| 66 | D_B0501_1Click | published | (Sender: TObject) | 4371-4405 | Field click handler (Day duty) | LOW |
| 67 | E_B0501_1Click | published | (Sender: TObject) | 4406-4440 | Field click handler (Evening duty) | LOW |
| 68 | N_B0501_1Click | published | (Sender: TObject) | 4441-4475 | Field click handler (Night duty) | LOW |
| 69 | D_B0601_1Click | published | (Sender: TObject) | 4476-4522 | Field click handler (Day duty) | LOW |
| 70 | E_B0601_1Click | published | (Sender: TObject) | 4523-4569 | Field click handler (Evening duty) | LOW |
| 71 | N_B0601_1Click | published | (Sender: TObject) | 4570-4616 | Field click handler (Night duty) | LOW |
| 72 | D_B0701_1Click | published | (Sender: TObject) | 4617-4638 | Field click handler (Day duty) | LOW |
| 73 | E_B0701_1Click | published | (Sender: TObject) | 4639-4660 | Field click handler (Evening duty) | LOW |
| 74 | N_B0701_1Click | published | (Sender: TObject) | 4661-4682 | Field click handler (Night duty) | LOW |
| 75 | D_B0703_5Click | published | (Sender: TObject) | 4683-4695 | Field click handler (Day duty) | LOW |
| 76 | E_B0703_5Click | published | (Sender: TObject) | 4696-4709 | Field click handler (Evening duty) | LOW |
| 77 | N_B0703_5Click | published | (Sender: TObject) | 4710-4724 | Field click handler (Night duty) | LOW |
| 78 | D_C0102_2Exit | published | (Sender: TObject) | 4725-4756 | Intubation date calculation on field exit | LOW |
| 79 | sbt_CalcIntubeClick | published | (Sender: TObject) | 4757-4807 | Calculates intubation duration from dates | MED |
| 80 | D_B0702_1Click | published | (Sender: TObject) | 4808-4856 | Field click handler with special logic | MED |
| 81 | AssignBdScore | private | (Sender: TObject) | 4857-4911 | Calculates and assigns Braden score from component values | MED |
| 82 | D_C0102_2Click | published | (Sender: TObject) | 4912-4944 | Checkbox click with date picker | LOW |
| 83 | SelOrderList | private | () | 4945-5035 | Opens order selection dialog, populates grid | MED |
| 84 | bbt_CancelClick | published | (Sender: TObject) | 5036-5045 | Cancel button handler | LOW |
| 85 | dtp_FromaddChange | published | (Sender: TObject) | 5046-5051 | Date picker change handler | LOW |
| 86 | dtp_FromaddCloseUp | published | (Sender: TObject) | 5052-5058 | Date picker close handler | LOW |
| 87 | bbt_AddClick | published | (Sender: TObject) | 5059-5069 | Add button handler | LOW |
| 88 | E_B0302_1EClick | published | (Sender: TObject) | 5070-5089 | Field click handler (Evening duty, special) | LOW |
| 89 | ugd_AddListDblClick | published | (Sender: TObject) | 5090-5096 | Grid double-click handler | LOW |
| 90 | GridClear | private | (in_Grid: TUltraGrid) | 5097-5119 | Clears all grid cells | LOW |
| 91 | D_B0505_1Click | published | (Sender: TObject) | 5120-5146 | Field click handler (Day duty) | LOW |
| 92 | E_B0505_1Click | published | (Sender: TObject) | 5147-5172 | Field click handler (Evening duty) | LOW |
| 93 | N_B0505_1Click | published | (Sender: TObject) | 5173-5197 | Field click handler (Night duty) | LOW |
| 94 | D_B0607_1Click | published | (Sender: TObject) | 5198-5236 | Field click handler (Day duty) | LOW |
| 95 | E_B0607_1Click | published | (Sender: TObject) | 5237-5275 | Field click handler (Evening duty) | LOW |
| 96 | N_B0607_1Click | published | (Sender: TObject) | 5276-5322 | Field click handler (Night duty) | LOW |
| 97 | D_B0401_4EClick | published | (Sender: TObject) | 5323-5375 | Pain score field click handler (Day duty) | MED |
| 98 | AssignPainScore | private | (Sender: TObject) | 5376-5477 | Calculates and assigns pain score from component values | MED |
| 99 | bbt_PrintClick | published | (Sender: TObject) | 5478-5869 | Creates MDN110FV_P01, populates QRLabels from form fields, Preview/Print | HIGH |
| 100 | AutoScanPrint | private | () | 5870-5930 | Automated print via barcode scan (legacy) | MED |
| 101 | AutoScanPrint_New | private | () | 5931-5976 | Automated print via barcode scan (new version) | MED |
| 102 | bbt_SelectClick | published | (Sender: TObject) | 5977-6011 | Opens patient selection dialog | LOW |
| 103 | bbt_ToNrRecordDClick | published | (Sender: TObject) | 6012-7385 | Reads all quality check fields for D/E/N duty, builds nursing record string, calls TpSvc for EMR integration | HIGH |
| 104 | GetIcuInfo | private | (sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String) | 7386-7496 | HmdIcuinf.Create, getIcuinflist, populates ICU info fields | HIGH |
| 105 | bbt_OkClick | published | (Sender: TObject) | 7497-7514 | OK button handler | LOW |
| 106 | sbt_DCopyClick | published | (Sender: TObject) | 7515-7579 | Confirmation dialog, CopyLastQualCheckOfDuty('D'), LoadQualityCheck | MED |
| 107 | sbt_ECopyClick | published | (Sender: TObject) | 7580-7645 | Confirmation dialog, CopyLastQualCheckOfDuty('E'), LoadQualityCheck | MED |
| 108 | sbt_NCopyClick | published | (Sender: TObject) | 7646-7714 | Confirmation dialog, CopyLastQualCheckOfDuty('N'), LoadQualityCheck | MED |
| 109 | CopyLastQualCheckOfDuty | private | (AsDuty: String): Boolean | 7715-7817 | HmdIcasit.Create, getIcasitlist, copies previous duty's quality check data | HIGH |
| 110 | AssignPainRslt | private | (Sender: TObject) | 7818-7938 | Calculates and assigns pain result from component values | MED |
| 111 | D_B0303_1Click | published | (Sender: TObject) | 7939-7957 | Field click handler (Day duty) | LOW |
| 112 | E_B0303_1Click | published | (Sender: TObject) | 7958-7975 | Field click handler (Evening duty) | LOW |
| 113 | N_B0303_1Click | published | (Sender: TObject) | 7976-7990 | Field click handler (Night duty) | LOW |
| 114 | Set_AA_20150306 | private | () | 7991-8046 | Configuration/patch method (dated 2015-03-06) | MED |
| 115 | bt_printClick | published | (Sender: TObject) | 8047-8125 | Alternative print handler | MED |

VALIDATION: Source has 115 implementations, inventory has 115 rows. Delta = 0%.

## Event Chain Map

```
FormCreate → FormShow → Initialize → LoadPatientInfo + SetAssessDateAndCurrentDuty
  → LoadQualityCheck → LoadQualityCheckInfo + LoadQualityCheckResult + DisplayCurrentDuty + SetControlStatusOfDuty
  → [User edits fields] → {D|E|N}_B{NNNN}_{N}Click handlers
  → [User clicks checkbox] → {D|E|N}_C{NNNN}_{N}Click handlers
  → [User clicks Save] → sbt_{D|E|N}SaveClick → SaveQualityCheckOfDuty → HmdIcasit.setIcasit
  → [User clicks Delete] → sbt_{D|E|N}DeleteClick → DeleteQualityCheckOfDuty → HmdIcasit.delIcasit
  → [User clicks Copy] → sbt_{D|E|N}CopyClick → CopyLastQualCheckOfDuty → HmdIcasit.getIcasitlist
  → [User clicks Print] → bbt_PrintClick → MDN110FV_P01 report
  → [User clicks ToNrRecord] → bbt_ToNrRecordDClick → TpSvc EMR integration
  → [Score changes] → AssignBdScore / AssignPainScore / AssignPainRslt → auto-calculate scores
  → [User navigates dates] → sbt_PreviousClick / sbt_NextClick / dtp_ChkDateCloseUp → LoadQualityCheck
FormClose → Action := caFree
FormDestroy → MDN110FV := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FV | TMDN110FV | FormCreate | MDN110UV_P01 (print) | FormDestroy (set to Nil) |
| FsPatNo | String | Initialize/LoadPatientInfo | SaveQualityCheckOfDuty, LoadQualityCheckInfo, bbt_ToNrRecordDClick | LoadPatientInfo |
| FsCurDuty | String ('D','E','N') | SetAssessDateAndCurrentDuty | Initialize, DisplayCurrentDuty | SetAssessDateAndCurrentDuty |

## Middleware Contract Summary

| Class | Method | Input Params | Output Shape | Error Convention |
|-------|--------|-------------|--------------|-----------------|
| HmdIcasit | getIcasitlist | sFlag1, sType1-sType5 | Quality check field arrays per duty | Returns -1 on error, 0 on no data |
| HmdIcasit | setIcasit | sFlag1, sType1-sType5, TList of VOs | Integer result code | Returns -1 on error |
| HmdIcasit | delIcasit | sFlag1, sType1-sType5 | Integer result code | Returns -1 on error |
| HmdIcuinf | getIcuinflist | sFlag1, sType1-sType4, G_LOCATE | ICU info field arrays | Returns -1 on error, 0 on no data |
| HmdPatinf | ListPatbat | Cond, PatNo, PatName | Patient info arrays | Returns -1 on error, 0 on no data |
| TpSvc | (EMR integration) | Nursing record string | - | Via SComFunc |

## Repetitive Handler Analysis

Same D/E/N triplication pattern as MDN110UU. Field sections with triplicated handlers:
B0101, B0102, B0103, B0201, B0203, B0301, B0302, B0303, B0401, B0402, B0501, B0505, B0601, B0607, B0701, B0703, C0203, C0402

Triplicated action handlers: sbt_{D|E|N}SaveClick, sbt_{D|E|N}DeleteClick, sbt_{D|E|N}CopyClick

Unique methods not following D/E/N pattern:
- AssignBdScore: Braden scale score calculation
- AssignPainScore: Pain score calculation
- AssignPainRslt: Pain result calculation
- SelOrderList: Order selection dialog
- Set_AA_20150306: Configuration patch
- sbt_CalcIntubeClick: Intubation duration calculation
- D_B0702_1Click: Special field handler (Day only)
- D_B0401_4EClick: Pain score field handler (Day only)
- D_C0102_2Exit/Click: Intubation checkbox handlers (Day only)

KEY MIGRATION NOTE: ~60 of 115 methods (52%) are D/E/N triplicates. Additional unique methods handle score calculations (Braden, Pain) that should become shared utility functions.
