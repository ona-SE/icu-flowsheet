# MDN110UW — Method Inventory

Unit: MDN110UW.pas (6927 lines)
Form class: TMDN110FW
Purpose: NICU nursing assessment form — per-duty (Day/Evening/Night) assessment entry, save, delete, copy, print. NICU-specific variant of MDN110UU.
Uses: VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1, MDN110UW_P01, TpSvc, SComFunc

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1750-1755 | Action := caFree | LOW |
| 2 | FormCreate | published | (Sender: TObject) | 1756-1767 | Initializes form variables | LOW |
| 3 | FormDestroy | published | (Sender: TObject) | 1768-1777 | MDN110FW := Nil | LOW |
| 4 | bbt_CloseClick | published | (Sender: TObject) | 1778-1787 | Close | LOW |
| 5 | Initialize | private | () | 1788-1906 | GetSysDate, LoadPatientInfo, SetAssessDateAndCurrentDuty, GetComp, sets nurse/time defaults, disables controls for read-only modes | HIGH |
| 6 | FormShow | published | (Sender: TObject) | 1907-1935 | Initialize, SearchNursingAssessment | MED |
| 7 | scrlbx_AssessMouseWheelDown | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 1936-1949 | ScrollBar position adjustment | LOW |
| 8 | scrlbx_AssessMouseWheelUp | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 1950-1962 | ScrollBar position adjustment | LOW |
| 9 | SearchNursingAssessment | private | () | 1963-1992 | LoadAssessmentInfo, LoadAssessmentResult, DisplayCurrentDuty, SetControlStatusOfDuty | MED |
| 10 | SetAssessDateAndCurrentDuty | private | (AdtSysDateTime: TDateTime) | 1993-2060 | Determines current duty (D/E/N) from time, sets date picker | MED |
| 11 | ed_D_AssNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2061-2073 | SearchUser for nurse lookup on Enter | LOW |
| 12 | ed_E_AssNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2074-2087 | SearchUser for nurse lookup on Enter | LOW |
| 13 | ed_N_AssNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2088-2101 | SearchUser for nurse lookup on Enter | LOW |
| 14 | ClearValueOf | private | (AsDuty: String) | 2102-2152 | Clears all field values for a given duty prefix | MED |
| 15 | LoadAssessmentInfo | private | () | 2153-2289 | HmdIcasit.Create, getIcasitlist, FindComponent to populate assessment fields for all 3 duties | HIGH |
| 16 | LoadAssessmentResult | private | () | 2290-2427 | HmdIcuinf.Create, getIcuinflist, FindComponent to populate result fields for all 3 duties | HIGH |
| 17 | dtp_AssDateCloseUp | published | (Sender: TObject) | 2428-2464 | SearchNursingAssessment on date change | LOW |
| 18 | sbt_PreviousClick | published | (Sender: TObject) | 2465-2505 | Decrements date, SearchNursingAssessment | LOW |
| 19 | sbt_NextClick | published | (Sender: TObject) | 2506-2550 | Increments date, SearchNursingAssessment | LOW |
| 20 | SaveAssessmentOfDuty | private | (AsDuty: string): Boolean | 2551-2823 | HmdIcasit.Create, reads all form fields via GetComp, calls setIcasit to save | HIGH |
| 21 | sbt_DSaveClick | published | (Sender: TObject) | 2824-2883 | Confirmation dialog, SaveAssessmentOfDuty('D'), SearchNursingAssessment | MED |
| 22 | sbt_ESaveClick | published | (Sender: TObject) | 2884-2944 | Confirmation dialog, SaveAssessmentOfDuty('E'), SearchNursingAssessment | MED |
| 23 | sbt_NSaveClick | published | (Sender: TObject) | 2945-3003 | Confirmation dialog, SaveAssessmentOfDuty('N'), SearchNursingAssessment | MED |
| 24 | D_B0407_1Click | published | (Sender: TObject) | 3004-3018 | Field click handler (Day duty) | LOW |
| 25 | D_B0808_1Click | published | (Sender: TObject) | 3019-3041 | Field click handler (Day duty) | LOW |
| 26 | DeleteAssessmentOfDuty | private | (AsDuty: string): Boolean | 3042-3133 | HmdIcasit.Create, delIcasit, deletes assessment for given duty | HIGH |
| 27 | sbt_DDeleteClick | published | (Sender: TObject) | 3134-3188 | Confirmation dialog, DeleteAssessmentOfDuty('D'), SearchNursingAssessment | MED |
| 28 | sbt_EDeleteClick | published | (Sender: TObject) | 3189-3243 | Confirmation dialog, DeleteAssessmentOfDuty('E'), SearchNursingAssessment | MED |
| 29 | sbt_NDeleteClick | published | (Sender: TObject) | 3244-3299 | Confirmation dialog, DeleteAssessmentOfDuty('N'), SearchNursingAssessment | MED |
| 30 | IsNoData | private | (AsDuty: string): Boolean | 3300-3381 | Checks if all fields for a duty are empty | MED |
| 31 | DisplayCurrentDuty | private | (AsDuty: string) | 3382-3412 | Highlights current duty tab/panel | LOW |
| 32 | CopyLastAssessmentOfDuty | private | (AsDuty: String): Boolean | 3413-3519 | HmdIcasit.Create, getIcasitlist, copies previous duty's assessment data | HIGH |
| 33 | sbt_DCopyClick | published | (Sender: TObject) | 3520-3586 | Confirmation dialog, CopyLastAssessmentOfDuty('D'), SearchNursingAssessment | MED |
| 34 | sbt_ECopyClick | published | (Sender: TObject) | 3587-3654 | Confirmation dialog, CopyLastAssessmentOfDuty('E'), SearchNursingAssessment | MED |
| 35 | sbt_NCopyClick | published | (Sender: TObject) | 3655-3725 | Confirmation dialog, CopyLastAssessmentOfDuty('N'), SearchNursingAssessment | MED |
| 36 | sbt_CalcIntubeClick | published | (Sender: TObject) | 3726-3786 | Calculates intubation duration from dates | MED |
| 37 | D_B0603_1Click | published | (Sender: TObject) | 3787-3815 | Field click handler with date picker | LOW |
| 38 | D_B0901_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 3816-3846 | Field key handler with validation | LOW |
| 39 | bbt_PrintClick | published | (Sender: TObject) | 3847-4155 | Creates MDN110FW_P01, populates QRLabels from form fields, Preview/Print | HIGH |
| 40 | LoadPatientInfo | private | (in_ChkDate: TDate) | 4156-4251 | HmdPatinf.Create, ListPatbat, populates patient info labels (takes date param unlike UU) | MED |
| 41 | AutoScanPrint | private | () | 4252-4285 | Automated print via barcode scan (legacy) | MED |
| 42 | D_B0203_1Click | published | (Sender: TObject) | 4286-4298 | Field click handler (Day duty) | LOW |
| 43 | D_B0304_1Click | published | (Sender: TObject) | 4299-4327 | Field click handler (Day duty) | LOW |
| 44 | D_B0703_1Click | published | (Sender: TObject) | 4328-4356 | Field click handler (Day duty) | LOW |
| 45 | D_B0703_1Exit | published | (Sender: TObject) | 4357-4385 | Field exit handler (Day duty) | LOW |
| 46 | D_B0804_1Click | published | (Sender: TObject) | 4386-4402 | Field click handler (Day duty) | LOW |
| 47 | D_B0809_1Click | published | (Sender: TObject) | 4403-4421 | Field click handler (Day duty) | LOW |
| 48 | D_B0902_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 4422-4451 | Field key handler with validation | LOW |
| 49 | D_C0809_5Click | published | (Sender: TObject) | 4452-4463 | Checkbox click handler (Day duty) | LOW |
| 50 | E_B0203_1Click | published | (Sender: TObject) | 4464-4476 | Field click handler (Evening duty) | LOW |
| 51 | E_B0304_1Click | published | (Sender: TObject) | 4477-4506 | Field click handler (Evening duty) | LOW |
| 52 | E_B0407_1Click | published | (Sender: TObject) | 4507-4519 | Field click handler (Evening duty) | LOW |
| 53 | E_B0808_1Click | published | (Sender: TObject) | 4520-4537 | Field click handler (Evening duty) | LOW |
| 54 | E_B0804_1Click | published | (Sender: TObject) | 4538-4555 | Field click handler (Evening duty) | LOW |
| 55 | E_B0809_1Click | published | (Sender: TObject) | 4556-4574 | Field click handler (Evening duty) | LOW |
| 56 | E_C0809_5Click | published | (Sender: TObject) | 4575-4586 | Checkbox click handler (Evening duty) | LOW |
| 57 | N_B0203_1Click | published | (Sender: TObject) | 4587-4599 | Field click handler (Night duty) | LOW |
| 58 | N_B0304_1Click | published | (Sender: TObject) | 4600-4629 | Field click handler (Night duty) | LOW |
| 59 | N_B0407_1Click | published | (Sender: TObject) | 4630-4642 | Field click handler (Night duty) | LOW |
| 60 | N_B0808_1Click | published | (Sender: TObject) | 4643-4660 | Field click handler (Night duty) | LOW |
| 61 | N_B0804_1Click | published | (Sender: TObject) | 4661-4680 | Field click handler (Night duty) | LOW |
| 62 | N_B0809_1Click | published | (Sender: TObject) | 4681-4699 | Field click handler (Night duty) | LOW |
| 63 | N_C0809_5Click | published | (Sender: TObject) | 4700-4713 | Checkbox click handler (Night duty) | LOW |
| 64 | D_B0503_1Click | published | (Sender: TObject) | 4714-4730 | Field click handler (Day duty) | LOW |
| 65 | E_B0503_1Click | published | (Sender: TObject) | 4731-4747 | Field click handler (Evening duty) | LOW |
| 66 | N_B0503_1Click | published | (Sender: TObject) | 4748-4764 | Field click handler (Night duty) | LOW |
| 67 | D_B0902_1Click | published | (Sender: TObject) | 4765-4787 | Field click handler (Day duty) | LOW |
| 68 | E_B0902_1Click | published | (Sender: TObject) | 4788-4811 | Field click handler (Evening duty) | LOW |
| 69 | N_B0902_1Click | published | (Sender: TObject) | 4812-4838 | Field click handler (Night duty) | LOW |
| 70 | bbt_SelectClick | published | (Sender: TObject) | 4839-4871 | Opens patient selection dialog | LOW |
| 71 | bbt_ToNrRecordDClick | published | (Sender: TObject) | 4872-6604 | Reads all assessment fields for D/E/N duty, builds nursing record string, calls TpSvc for EMR integration | HIGH |
| 72 | GetIcuInfo | private | (sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String) | 6605-6721 | HmdIcuinf.Create, getIcuinflist, populates ICU info fields | HIGH |
| 73 | bbt_OkClick | published | (Sender: TObject) | 6722-6738 | OK button handler | LOW |
| 74 | AutoScanPrint_New | private | () | 6739-6768 | Automated print via barcode scan (new version) | MED |
| 75 | SetControlStatusOfDuty | private | (AsDuty: string) | 6769-6786 | Enables/disables controls based on duty data presence | LOW |
| 76 | D_B0703RemoveClick | published | (Sender: TObject) | 6787-6818 | Clears field (Day) | LOW |
| 77 | D_B0901RemoveClick | published | (Sender: TObject) | 6819-6848 | Clears field (Day) | LOW |
| 78 | bt_printClick | published | (Sender: TObject) | 6849-6927 | Alternative print handler | MED |

VALIDATION: Source has 78 implementations, inventory has 78 rows. Delta = 0%.

## Event Chain Map

```
FormCreate → FormShow → Initialize → LoadPatientInfo + SetAssessDateAndCurrentDuty
  → SearchNursingAssessment → LoadAssessmentInfo + LoadAssessmentResult + DisplayCurrentDuty + SetControlStatusOfDuty
  → [User edits fields] → {D|E|N}_B{NNNN}_{N}Click handlers
  → [User clicks Save] → sbt_{D|E|N}SaveClick → SaveAssessmentOfDuty → HmdIcasit.setIcasit
  → [User clicks Delete] → sbt_{D|E|N}DeleteClick → DeleteAssessmentOfDuty → HmdIcasit.delIcasit
  → [User clicks Copy] → sbt_{D|E|N}CopyClick → CopyLastAssessmentOfDuty → HmdIcasit.getIcasitlist
  → [User clicks Print] → bbt_PrintClick → MDN110FW_P01 report
  → [User clicks ToNrRecord] → bbt_ToNrRecordDClick → TpSvc EMR integration
FormClose → Action := caFree
FormDestroy → MDN110FW := Nil
```

## Middleware Contract Summary

Same as MDN110UU: HmdIcasit (getIcasitlist, setIcasit, delIcasit), HmdIcuinf (getIcuinflist), HmdPatinf (ListPatbat), TpSvc (EMR integration).

## Repetitive Handler Analysis

D/E/N triplication for field sections: B0203, B0304, B0407, B0503, B0808, B0804, B0809, B0902, C0809
Triplicated action handlers: sbt_{D|E|N}SaveClick, sbt_{D|E|N}DeleteClick, sbt_{D|E|N}CopyClick, ed_{D|E|N}_AssNursNameKeyDown

KEY MIGRATION NOTE: Structurally identical to MDN110UU but for NICU. LoadPatientInfo takes a date parameter (unlike UU). bbt_ToNrRecordDClick is 1733 lines — the largest single method in this unit.
