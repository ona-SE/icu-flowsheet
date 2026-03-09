# MDN110UU — Method Inventory (Part 1: Methods 1-55)

Unit: MDN110UU.pas (7382 lines)
Form class: TMDN110FU
Purpose: ICU nursing assessment form — per-duty (Day/Evening/Night) assessment entry, save, delete, copy, print
Uses: VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1, MDN110UV, MDN110UU_P01, TpSvc, SComFunc

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1808-1813 | Action := caFree | LOW |
| 2 | FormCreate | published | (Sender: TObject) | 1814-1828 | Initializes form variables, sets FsCurDuty | LOW |
| 3 | FormDestroy | published | (Sender: TObject) | 1829-1841 | MDN110FU := Nil | LOW |
| 4 | bbt_CloseClick | published | (Sender: TObject) | 1842-1854 | Close | LOW |
| 5 | Initialize | private | () | 1855-1979 | GetSysDate, LoadPatientInfo, SetAssessDateAndCurrentDuty, GetComp, sets nurse/time defaults, disables controls for read-only modes | HIGH |
| 6 | FormShow | published | (Sender: TObject) | 1980-2018 | Initialize, SearchNursingAssessment | MED |
| 7 | scrlbx_AssessMouseWheelDown | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 2019-2034 | ScrollBar position adjustment | LOW |
| 8 | scrlbx_AssessMouseWheelUp | published | (Sender: TObject; Shift: TShiftState; MousePos: TPoint; var Handled: Boolean) | 2035-2049 | ScrollBar position adjustment | LOW |
| 9 | SearchNursingAssessment | private | () | 2050-2082 | LoadAssessmentInfo, LoadAssessmentResult, DisplayCurrentDuty, SetControlStatusOfDuty | MED |
| 10 | SetAssessDateAndCurrentDuty | private | (AdtSysDateTime: TDateTime) | 2083-2150 | Determines current duty (D/E/N) from time, sets date picker, sets FsCurDuty | MED |
| 11 | ed_D_AssNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2151-2165 | SearchUser for nurse lookup on Enter | LOW |
| 12 | ed_E_AssNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2166-2181 | SearchUser for nurse lookup on Enter | LOW |
| 13 | ed_N_AssNursNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2182-2197 | SearchUser for nurse lookup on Enter | LOW |
| 14 | ClearValueOf | private | (AsDuty: String) | 2198-2250 | Clears all field values for a given duty prefix using GetComp/FindComponent | MED |
| 15 | LoadAssessmentInfo | private | () | 2251-2389 | HmdIcasit.Create, getIcasitlist, FindComponent to populate assessment fields for all 3 duties | HIGH |
| 16 | LoadAssessmentResult | private | () | 2390-2563 | HmdIcuinf.Create, getIcuinflist, FindComponent to populate result fields for all 3 duties | HIGH |
| 17 | dtp_AssDateCloseUp | published | (Sender: TObject) | 2564-2594 | SearchNursingAssessment on date change | LOW |
| 18 | sbt_PreviousClick | published | (Sender: TObject) | 2595-2631 | Decrements date, SearchNursingAssessment | LOW |
| 19 | sbt_NextClick | published | (Sender: TObject) | 2632-2689 | Increments date, SearchNursingAssessment | LOW |
| 20 | SaveAssessmentOfDuty | private | (AsDuty: string): Boolean | 2690-2947 | HmdIcasit.Create, reads all form fields via GetComp, calls setIcasit to save, handles TList of assessment VOs | HIGH |
| 21 | sbt_DSaveClick | published | (Sender: TObject) | 2948-3006 | Confirmation dialog, SaveAssessmentOfDuty('D'), SearchNursingAssessment | MED |
| 22 | sbt_ESaveClick | published | (Sender: TObject) | 3007-3066 | Confirmation dialog, SaveAssessmentOfDuty('E'), SearchNursingAssessment | MED |
| 23 | sbt_NSaveClick | published | (Sender: TObject) | 3067-3125 | Confirmation dialog, SaveAssessmentOfDuty('N'), SearchNursingAssessment | MED |
| 24 | D_B0301_1Click | published | (Sender: TObject) | 3126-3147 | Field click handler (Day duty) | LOW |
| 25 | E_B0301_1Click | published | (Sender: TObject) | 3148-3169 | Field click handler (Evening duty) | LOW |
| 26 | N_B0301_1Click | published | (Sender: TObject) | 3170-3190 | Field click handler (Night duty) | LOW |
| 27 | D_B0407_1Click | published | (Sender: TObject) | 3191-3205 | Field click handler (Day duty) | LOW |
| 28 | E_B0407_1Click | published | (Sender: TObject) | 3206-3221 | Field click handler (Evening duty) | LOW |
| 29 | N_B0407_1Click | published | (Sender: TObject) | 3222-3237 | Field click handler (Night duty) | LOW |
| 30 | D_B0501_1Click | published | (Sender: TObject) | 3238-3258 | Field click handler (Day duty) | LOW |
| 31 | E_B0501_1Click | published | (Sender: TObject) | 3259-3279 | Field click handler (Evening duty) | LOW |
| 32 | N_B0501_1Click | published | (Sender: TObject) | 3280-3301 | Field click handler (Night duty) | LOW |
| 33 | D_B0805_1Click | published | (Sender: TObject) | 3302-3329 | Field click handler (Day duty) | LOW |
| 34 | E_B0805_1Click | published | (Sender: TObject) | 3330-3356 | Field click handler (Evening duty) | LOW |
| 35 | N_B0805_1Click | published | (Sender: TObject) | 3357-3384 | Field click handler (Night duty) | LOW |
| 36 | D_B0808_1Click | published | (Sender: TObject) | 3385-3404 | Field click handler (Day duty) | LOW |
| 37 | E_B0808_1Click | published | (Sender: TObject) | 3405-3424 | Field click handler (Evening duty) | LOW |
| 38 | N_B0808_1Click | published | (Sender: TObject) | 3425-3445 | Field click handler (Night duty) | LOW |
| 39 | D_B0901_1Click | published | (Sender: TObject) | 3446-3468 | Field click handler (Day duty) | LOW |
| 40 | E_B0901_1Click | published | (Sender: TObject) | 3469-3491 | Field click handler (Evening duty) | LOW |
| 41 | N_B0901_1Click | published | (Sender: TObject) | 3492-3514 | Field click handler (Night duty) | LOW |
| 42 | D_B0902_1Click | published | (Sender: TObject) | 3515-3537 | Field click handler (Day duty) | LOW |
| 43 | E_B0902_1Click | published | (Sender: TObject) | 3538-3560 | Field click handler (Evening duty) | LOW |
| 44 | N_B0902_1Click | published | (Sender: TObject) | 3561-3583 | Field click handler (Night duty) | LOW |
| 45 | D_B0903_1Click | published | (Sender: TObject) | 3584-3606 | Field click handler (Day duty) | LOW |
| 46 | E_B0903_1Click | published | (Sender: TObject) | 3607-3628 | Field click handler (Evening duty) | LOW |
| 47 | N_B0903_1Click | published | (Sender: TObject) | 3629-3651 | Field click handler (Night duty) | LOW |
| 48 | D_B0904_1Click | published | (Sender: TObject) | 3652-3674 | Field click handler (Day duty) | LOW |
| 49 | E_B0904_1Click | published | (Sender: TObject) | 3675-3697 | Field click handler (Evening duty) | LOW |
| 50 | N_B0904_1Click | published | (Sender: TObject) | 3698-3720 | Field click handler (Night duty) | LOW |
| 51 | D_B0905_1Click | published | (Sender: TObject) | 3721-3743 | Field click handler (Day duty) | LOW |
| 52 | E_B0905_1Click | published | (Sender: TObject) | 3744-3766 | Field click handler (Evening duty) | LOW |
| 53 | N_B0905_1Click | published | (Sender: TObject) | 3767-3789 | Field click handler (Night duty) | LOW |
| 54 | D_B0906_1Click | published | (Sender: TObject) | 3790-3812 | Field click handler (Day duty) | LOW |
| 55 | E_B0906_1Click | published | (Sender: TObject) | 3813-3835 | Field click handler (Evening duty) | LOW |
# MDN110UU — Method Inventory (Part 2: Methods 56-110)

## Method Inventory (continued)

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 56 | N_B0906_1Click | published | (Sender: TObject) | 3836-3858 | Field click handler (Night duty) | LOW |
| 57 | D_B0908_1Click | published | (Sender: TObject) | 3859-3881 | Field click handler (Day duty) | LOW |
| 58 | E_B0908_1Click | published | (Sender: TObject) | 3882-3904 | Field click handler (Evening duty) | LOW |
| 59 | N_B0908_1Click | published | (Sender: TObject) | 3905-3927 | Field click handler (Night duty) | LOW |
| 60 | D_C0901_1Click | published | (Sender: TObject) | 3928-3941 | Checkbox click handler (Day duty) | LOW |
| 61 | E_C0901_1Click | published | (Sender: TObject) | 3942-3955 | Checkbox click handler (Evening duty) | LOW |
| 62 | N_C0901_1Click | published | (Sender: TObject) | 3956-3969 | Checkbox click handler (Night duty) | LOW |
| 63 | D_C0902_1Click | published | (Sender: TObject) | 3970-3983 | Checkbox click handler (Day duty) | LOW |
| 64 | E_C0902_1Click | published | (Sender: TObject) | 3984-3997 | Checkbox click handler (Evening duty) | LOW |
| 65 | N_C0902_1Click | published | (Sender: TObject) | 3998-4011 | Checkbox click handler (Night duty) | LOW |
| 66 | D_C0903_1Click | published | (Sender: TObject) | 4012-4025 | Checkbox click handler (Day duty) | LOW |
| 67 | E_C0903_1Click | published | (Sender: TObject) | 4026-4039 | Checkbox click handler (Evening duty) | LOW |
| 68 | N_C0903_1Click | published | (Sender: TObject) | 4040-4053 | Checkbox click handler (Night duty) | LOW |
| 69 | D_C0904_1Click | published | (Sender: TObject) | 4054-4067 | Checkbox click handler (Day duty) | LOW |
| 70 | E_C0904_1Click | published | (Sender: TObject) | 4068-4081 | Checkbox click handler (Evening duty) | LOW |
| 71 | N_C0904_1Click | published | (Sender: TObject) | 4082-4095 | Checkbox click handler (Night duty) | LOW |
| 72 | D_C0905_1Click | published | (Sender: TObject) | 4096-4109 | Checkbox click handler (Day duty) | LOW |
| 73 | E_C0905_1Click | published | (Sender: TObject) | 4110-4123 | Checkbox click handler (Evening duty) | LOW |
| 74 | N_C0905_1Click | published | (Sender: TObject) | 4124-4137 | Checkbox click handler (Night duty) | LOW |
| 75 | D_C0906_1Click | published | (Sender: TObject) | 4138-4151 | Checkbox click handler (Day duty) | LOW |
| 76 | E_C0906_1Click | published | (Sender: TObject) | 4152-4165 | Checkbox click handler (Evening duty) | LOW |
| 77 | N_C0906_1Click | published | (Sender: TObject) | 4166-4179 | Checkbox click handler (Night duty) | LOW |
| 78 | D_C0908_1Click | published | (Sender: TObject) | 4180-4193 | Checkbox click handler (Day duty) | LOW |
| 79 | E_C0908_1Click | published | (Sender: TObject) | 4194-4207 | Checkbox click handler (Evening duty) | LOW |
| 80 | N_C0908_1Click | published | (Sender: TObject) | 4208-4226 | Checkbox click handler (Night duty) | LOW |
| 81 | DeleteAssessmentOfDuty | private | (AsDuty: string): Boolean | 4227-4321 | HmdIcasit.Create, delIcasit, deletes assessment for given duty | HIGH |
| 82 | sbt_DDeleteClick | published | (Sender: TObject) | 4322-4377 | Confirmation dialog, DeleteAssessmentOfDuty('D'), SearchNursingAssessment | MED |
| 83 | sbt_EDeleteClick | published | (Sender: TObject) | 4378-4432 | Confirmation dialog, DeleteAssessmentOfDuty('E'), SearchNursingAssessment | MED |
| 84 | sbt_NDeleteClick | published | (Sender: TObject) | 4433-4489 | Confirmation dialog, DeleteAssessmentOfDuty('N'), SearchNursingAssessment | MED |
| 85 | IsNoData | private | (AsDuty: string): Boolean | 4490-4567 | Checks if all fields for a duty are empty via GetComp | MED |
| 86 | DisplayCurrentDuty | private | (AsDuty: string) | 4568-4601 | Highlights current duty tab/panel visually | LOW |
| 87 | CopyLastAssessmentOfDuty | private | (AsDuty: String): Boolean | 4602-4701 | HmdIcasit.Create, getIcasitlist, copies previous duty's assessment data | HIGH |
| 88 | sbt_DCopyClick | published | (Sender: TObject) | 4702-4767 | Confirmation dialog, CopyLastAssessmentOfDuty('D'), SearchNursingAssessment | MED |
| 89 | sbt_ECopyClick | published | (Sender: TObject) | 4768-4834 | Confirmation dialog, CopyLastAssessmentOfDuty('E'), SearchNursingAssessment | MED |
| 90 | sbt_NCopyClick | published | (Sender: TObject) | 4835-4899 | Confirmation dialog, CopyLastAssessmentOfDuty('N'), SearchNursingAssessment | MED |
| 91 | D_B0603_1Exit | published | (Sender: TObject) | 4900-4930 | Intubation date calculation on field exit | LOW |
| 92 | sbt_CalcIntubeClick | published | (Sender: TObject) | 4931-4980 | Calculates intubation duration from dates | MED |
| 93 | D_B0603_1Click | published | (Sender: TObject) | 4981-5012 | Field click handler with date picker | LOW |
| 94 | D_B0901_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 5013-5045 | Field key handler with validation | LOW |
| 95 | D_B0306_1Click | published | (Sender: TObject) | 5046-5079 | Field click handler (Day duty) | LOW |
| 96 | E_B0306_1Click | published | (Sender: TObject) | 5080-5114 | Field click handler (Evening duty) | LOW |
| 97 | N_B0306_1Click | published | (Sender: TObject) | 5115-5149 | Field click handler (Night duty) | LOW |
| 98 | bbt_PrintClick | published | (Sender: TObject) | 5150-5474 | Creates MDN110FU_P01, populates QRLabels from form fields, Preview/Print | HIGH |
| 99 | LoadPatientInfo | private | () | 5476-5574 | HmdPatinf.Create, ListPatbat, populates patient info labels | MED |
| 100 | AutoScanPrint | private | () | 5575-5615 | Automated print via barcode scan (legacy) | MED |
| 101 | AutoScanPrint_New | private | () | 5616-5644 | Automated print via barcode scan (new version) | MED |
| 102 | bbt_SelectClick | published | (Sender: TObject) | 5645-5678 | Opens patient selection dialog | LOW |
| 103 | bbt_ToNrRecordDClick | published | (Sender: TObject) | 5679-7057 | Reads all assessment fields for D/E/N duty, builds nursing record string, calls TpSvc for EMR integration | HIGH |
| 104 | GetIcuInfo | private | (sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String) | 7058-7171 | HmdIcuinf.Create, getIcuinflist, populates ICU info fields | HIGH |
| 105 | bbt_OkClick | published | (Sender: TObject) | 7172-7190 | OK button handler | LOW |
| 106 | SetControlStatusOfDuty | private | (AsDuty: string) | 7191-7209 | Enables/disables controls based on duty data presence | LOW |
| 107 | D_B0603RemoveClick | published | (Sender: TObject) | 7210-7242 | Clears intubation date field (Day) | LOW |
| 108 | D_B0703RemoveClick | published | (Sender: TObject) | 7243-7276 | Clears field (Day) | LOW |
| 109 | D_B0909RemoveClick | published | (Sender: TObject) | 7277-7303 | Clears field (Day) | LOW |
| 110 | bt_printClick | published | (Sender: TObject) | 7304-7382 | Alternative print handler | MED |

VALIDATION: Source has 110 implementations, inventory has 110 rows. Delta = 0%.

## Event Chain Map

```
FormCreate → FormShow → Initialize → LoadPatientInfo + SetAssessDateAndCurrentDuty
  → SearchNursingAssessment → LoadAssessmentInfo + LoadAssessmentResult + DisplayCurrentDuty + SetControlStatusOfDuty
  → [User edits fields] → {D|E|N}_B{NNNN}_{N}Click handlers
  → [User clicks checkbox] → {D|E|N}_C{NNNN}_{N}Click handlers
  → [User clicks Save] → sbt_{D|E|N}SaveClick → SaveAssessmentOfDuty → HmdIcasit.setIcasit
  → [User clicks Delete] → sbt_{D|E|N}DeleteClick → DeleteAssessmentOfDuty → HmdIcasit.delIcasit
  → [User clicks Copy] → sbt_{D|E|N}CopyClick → CopyLastAssessmentOfDuty → HmdIcasit.getIcasitlist
  → [User clicks Print] → bbt_PrintClick → MDN110FU_P01 report
  → [User clicks ToNrRecord] → bbt_ToNrRecordDClick → TpSvc EMR integration
  → [User navigates dates] → sbt_PreviousClick / sbt_NextClick / dtp_AssDateCloseUp → SearchNursingAssessment
FormClose → Action := caFree
FormDestroy → MDN110FU := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FU | TMDN110FU | FormCreate | MDN110UU_P01 (print) | FormDestroy (set to Nil) |
| FsPatNo | String | Initialize/LoadPatientInfo | SaveAssessmentOfDuty, LoadAssessmentInfo, bbt_ToNrRecordDClick | LoadPatientInfo |
| FsPatName | String | LoadPatientInfo | bbt_PrintClick, bbt_ToNrRecordDClick | LoadPatientInfo |
| FsAdmDate | String | LoadPatientInfo | SaveAssessmentOfDuty, LoadAssessmentInfo | LoadPatientInfo |
| FsCurDuty | String ('D','E','N') | SetAssessDateAndCurrentDuty | Initialize, DisplayCurrentDuty | SetAssessDateAndCurrentDuty |
| FSysDate | TDateTime | Initialize | SetAssessDateAndCurrentDuty | GetSysDate |

## Middleware Contract Summary

| Class | Method | Input Params | Output Shape | Error Convention |
|-------|--------|-------------|--------------|-----------------|
| HmdIcasit | getIcasitlist | sFlag1, sType1-sType5 | Assessment field arrays per duty | Returns -1 on error, 0 on no data |
| HmdIcasit | setIcasit | sFlag1, sType1-sType5, TList of VOs | Integer result code | Returns -1 on error |
| HmdIcasit | delIcasit | sFlag1, sType1-sType5 | Integer result code | Returns -1 on error |
| HmdIcuinf | getIcuinflist | sFlag1, sType1-sType4, G_LOCATE | ICU info field arrays | Returns -1 on error, 0 on no data |
| HmdPatinf | ListPatbat | Cond, PatNo, PatName | Patient info arrays | Returns -1 on error, 0 on no data |
| TpSvc | (EMR integration) | Nursing record string | - | Via SComFunc |

## Repetitive Handler Analysis

TEMPLATE GROUP 1: {D|E|N}_B{NNNN}_{N}Click → field click handlers, triplicated per duty
Each field section (B0301, B0407, B0501, B0805, B0808, B0901-B0906, B0908) has D/E/N variants.

| Section | D Method | E Method | N Method | Lines each | Deviates? |
|---------|----------|----------|----------|------------|-----------|
| B0301 | D_B0301_1Click | E_B0301_1Click | N_B0301_1Click | ~22 | No |
| B0407 | D_B0407_1Click | E_B0407_1Click | N_B0407_1Click | ~16 | No |
| B0501 | D_B0501_1Click | E_B0501_1Click | N_B0501_1Click | ~21 | No |
| B0805 | D_B0805_1Click | E_B0805_1Click | N_B0805_1Click | ~28 | No |
| B0808 | D_B0808_1Click | E_B0808_1Click | N_B0808_1Click | ~20 | No |
| B0901 | D_B0901_1Click | E_B0901_1Click | N_B0901_1Click | ~23 | No |
| B0902 | D_B0902_1Click | E_B0902_1Click | N_B0902_1Click | ~23 | No |
| B0903 | D_B0903_1Click | E_B0903_1Click | N_B0903_1Click | ~22 | No |
| B0904 | D_B0904_1Click | E_B0904_1Click | N_B0904_1Click | ~23 | No |
| B0905 | D_B0905_1Click | E_B0905_1Click | N_B0905_1Click | ~23 | No |
| B0906 | D_B0906_1Click | E_B0906_1Click | N_B0906_1Click | ~23 | No |
| B0908 | D_B0908_1Click | E_B0908_1Click | N_B0908_1Click | ~23 | No |

TEMPLATE GROUP 2: {D|E|N}_C{NNNN}_{N}Click → checkbox click handlers, triplicated per duty

| Section | D Method | E Method | N Method | Lines each | Deviates? |
|---------|----------|----------|----------|------------|-----------|
| C0901 | D_C0901_1Click | E_C0901_1Click | N_C0901_1Click | ~14 | No |
| C0902 | D_C0902_1Click | E_C0902_1Click | N_C0902_1Click | ~14 | No |
| C0903 | D_C0903_1Click | E_C0903_1Click | N_C0903_1Click | ~14 | No |
| C0904 | D_C0904_1Click | E_C0904_1Click | N_C0904_1Click | ~14 | No |
| C0905 | D_C0905_1Click | E_C0905_1Click | N_C0905_1Click | ~14 | No |
| C0906 | D_C0906_1Click | E_C0906_1Click | N_C0906_1Click | ~14 | No |
| C0908 | D_C0908_1Click | E_C0908_1Click | N_C0908_1Click | ~14 | No |

TEMPLATE GROUP 3: sbt_{D|E|N}SaveClick / sbt_{D|E|N}DeleteClick / sbt_{D|E|N}CopyClick → triplicated save/delete/copy

| Action | D Method | E Method | N Method | Lines each | Deviates? |
|--------|----------|----------|----------|------------|-----------|
| Save | sbt_DSaveClick | sbt_ESaveClick | sbt_NSaveClick | ~59 | No |
| Delete | sbt_DDeleteClick | sbt_EDeleteClick | sbt_NDeleteClick | ~56 | No |
| Copy | sbt_DCopyClick | sbt_ECopyClick | sbt_NCopyClick | ~66 | No |

KEY MIGRATION NOTE: The D/E/N triplication pattern means 57 of 110 methods (52%) are near-identical copies differing only in the duty prefix string. In the web migration, these should be parameterized into a single handler per field section that accepts a duty parameter.
