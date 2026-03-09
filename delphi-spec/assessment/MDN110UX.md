# MDN110UX — NICU Quality Check (Nursing Quality Indicator) Form

## Category

- **Form/UI**: Paired MDN110UX.dfm exists (16447 lines). NICU quality check form with scroll boxes, panels, checkboxes, radio buttons, combo boxes, edit fields, and UltraGrids organized by duty shifts (Day/Evening/Night). Adapted from ICU quality check (MDN110UV) for NICU use.
- **Database**: Tuxedo middleware via HmdIcqcit (ICU quality check items — load/save/delete), HmdIcuinf (ICU info — component values), HmdPatinf (patient info), HmdIcpatt (ICU patient), HmdBdspmt (bedsore/pressure measurement), HmdPaindt (pain data), Hmdpainmt (pain measurement), HmdOrderv (order verification).
- **Third-party**: TMS AdvPanel, Bianco_Panel, QuickReport (TQuickRep, TQRLabel), UltraGrid, SComFunc (HSComReport), LoadEMRFunc, KUMC.Packet, KUMC.Json.
- **OS/Win32-specific**: Uses Windows unit, Printers unit.

## Public Interface

### Class: TMDN110FX (inherits TForm)

**Published properties (25 total):**
- `propPatNo, propPatName, propAdmDate: String`
- `propDschDate, propPreviewYn, propEMRPrintYn, propEMRTitle, propPatFlag, propRgtDate: String`
- `propEMRFromDt, propEMRToDt: String`
- `prop_SComReport: HSComReport`, `prop_Patsect, prop_Patno, prop_Meddate, prop_Reptid: String`
- `prop_Fromdate, prop_Todate: String`
- `propAge, propSex, propBirthymd, propAcptNo, propCodvCd, propMedTime: String`

**Published methods:**
- `procedure AutoScanPrint` — EMR auto-scan print
- `procedure AutoScanPrint_New` — EMR auto-scan print (optimized)
- `procedure AssignBdScore(Sender: TObject)` — callback from bedsore scoring form
- `procedure AssignPainRslt(Sender: TObject)` — callback from pain assessment form

**Public fields:**
- `P_DschDate, P_PreviewYn, P_EMRPrintYn, P_EMRTitle, P_PatFlag, P_RgtDate: String`
- `G_EmrYn: String`, `G_EmrPrtIdx: Integer`, `G_LastEmrDateYn: String`, `G_LastPageIdx: Integer`
- `P_EMRFromDt, P_EMRToDt: String`

**Private fields:**
- `FsPatNo, FsPatName, FsAdmDate, FsCurDuty: String`
- `FPatient: HmdPatinf`, `FSysDate: TDateTime`, `FIsRoot: Boolean`, `FsSelDuty: String`
- EMR fields: `pv_SComReport, pv_Patsect, pv_Patno, pv_Meddate, pv_Reptid: String`
- `FsAge, FsSex, FsBirthymd, FsAcptNo, FsCodvCd, FsMedTime: String`

**Private methods (17 total):**
- `procedure Initialize`, `procedure SetAssessDateAndCurrentDuty(AdtSysDateTime: TDateTime)`
- `procedure SetControlStatusOfDuty(AsDuty: String)`, `procedure DisplayCurrentDuty(AsDuty: String)`
- `procedure ClearValueOf(AsDuty: String)`, `procedure LoadPatientInfo`
- `procedure LoadQualityCheck`, `procedure LoadQualityCheckInfo`, `procedure LoadQualityCheckResult`
- `function SaveQualityCheckOfDuty(AsDuty: String): Boolean`
- `function IsNoData(AsDuty: String): Boolean`
- `function DeleteQualityCheckOfDuty(AsDuty: String): Boolean`
- `procedure SetAuthority`, `procedure SelOrderList`, `procedure GridClear(in_Grid: TUltraGrid)`
- `procedure GetIcuInfo(sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String)`
- `function CopyLastQualCheckOfDuty(AsDuty: String): Boolean`

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, Mask, StdCtrls, ExtCtrls, Buttons, ComCtrls, MDCLASS1, AdvPanel, Grids, UltraGrid, Bianco_Panel, Printers, QRPrntr, QuickRpt, Qrctrls, Variants, SComFunc, LoadEMRFunc, KUMC.Packet, KUMC.Json

**Implementation uses:** VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDN110UU, MDN110UV_P01, MDN110UX_P01, TpSvc

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

### FPatient: HmdPatinf (private field)
Holds patient information loaded once and reused.
Populated by: LoadPatientInfo.
Consumed by: display methods, print methods (lines 1660, 1997, 4596, 7199).

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdPatinf.Create** — patient info
   - Used at line 1951

2. **HmdIcqcit.Create** — quality check items
   - Used at lines 2091, 2336, 2341
   - Methods: LoadQualityCheckByDate, SaveByDuty, DeleteByDuty

3. **HmdIcuinf.Create** — ICU info component values
   - Used at lines 2222, 2346, 2422, 2452, 2482, 2510, 2538

4. **HmdBdspmt.Create** — bedsore/pressure measurement

5. **HmdPaindt.Create / Hmdpainmt.Create** — pain data/measurement

6. **HmdOrderv.Create** — order verification

7. **HmdIcpatt.SelIcuPat(...)** — ICU patient selection

8. **TpSvc.GetSvc('SI_EMRPR_L2', ...)** — EMR service call

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UX.dfm (16447 lines):
- **TScrollBox**: scrlbx_QualityCheck — main scrollable quality check area
- **TAdvPanel**: multiple panels for duty sections
- **TPanel**: ~80+ panels for layout
- **TCheckBox**: ~150+ checkboxes for NICU quality check items
- **TRadioButton**: ~80+ radio buttons
- **TComboBox**: ~20+ combo boxes
- **TEdit**: ~40+ edit fields
- **TMemo**: memo fields for notes
- **TBitBtn**: bbt_Save, bbt_Delete, bbt_Copy, bbt_Print, bbt_Close, bbt_BdScore, bbt_Pain
- **TUltraGrid**: ugd_OrderList, ugd_EmrList
- **TDateTimePicker**: dtp_AssDate

WARNING: BUSINESS LOGIC IN HANDLER: SaveQualityCheckOfDuty — saves NICU quality check data via middleware
WARNING: BUSINESS LOGIC IN HANDLER: LoadQualityCheckResult — loads results and populates form controls
WARNING: BUSINESS LOGIC IN HANDLER: AssignBdScore — receives bedsore score from external form
WARNING: BUSINESS LOGIC IN HANDLER: AssignPainRslt — receives pain assessment result from external form

## Behavioral .dfm Properties

DFM file: 16447 lines. Minimum threshold: 33 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| scrlbx_QualityCheck | AutoScroll | True | Scrollable quality check area |
| dtp_AssDate | DateFormat | dfShort | Short date format |
| bbt_Save | Enabled | True | Save button enabled |
| bbt_Delete | Enabled | True | Delete button enabled |
| bbt_Copy | Enabled | True | Copy button enabled |
| bbt_Print | Enabled | True | Print button enabled |
| bbt_BdScore | Enabled | True | Bedsore score button enabled |
| bbt_Pain | Enabled | True | Pain assessment button enabled |
| pn_Day | Visible | True | Day shift panel visible |
| pn_Evening | Visible | True | Evening shift panel visible |
| pn_Night | Visible | True | Night shift panel visible |
| cbx_D_01 | Enabled | True | Day NICU quality check 01 |
| cbx_E_01 | Enabled | True | Evening NICU quality check 01 |
| cbx_N_01 | Enabled | True | Night NICU quality check 01 |
| rbt_D_01 | Enabled | True | Day radio 01 |
| rbt_E_01 | Enabled | True | Evening radio 01 |
| rbt_N_01 | Enabled | True | Night radio 01 |
| ed_D_01 | MaxLength | 50 | Day edit max length |
| ed_E_01 | MaxLength | 50 | Evening edit max length |
| ed_N_01 | MaxLength | 50 | Night edit max length |
| ugd_OrderList | FixedRows | 1 | One header row |
| ugd_OrderList | Visible | True | Order list visible |
| ugd_EmrList | Visible | False | EMR list hidden |
| pn_EmrList | Visible | False | EMR list panel hidden |
| lb_CurDuty | Caption | '' | Set at runtime |
| lb_AssDate | Caption | '' | Set at runtime |
| pn_Loading | Visible | False | Loading panel hidden |
| bbt_Close | Cancel | True | Responds to Escape |
| bbt_Save | Default | True | Responds to Enter |
| scrlbx_QualityCheck | VertScrollBar.Tracking | True | Smooth scroll |
| scrlbx_QualityCheck | HorzScrollBar.Visible | False | No horizontal scroll |
| combx_D_01 | Enabled | True | Day combo 01 |
| combx_E_01 | Enabled | True | Evening combo 01 |
| combx_N_01 | Enabled | True | Night combo 01 |

## With-Block Resolutions

ORIGINAL (line 1660): `with FPatient do`
RESOLVED: FPatient is HmdPatinf (private field). Members accessed: patient info arrays → FPatient.sFieldName[index]

ORIGINAL (line 1897): `with scrlbx_QualityCheck.VertScrollBar do`
RESOLVED: scrlbx_QualityCheck.VertScrollBar is TControlScrollBar. Members accessed: Position → scrlbx_QualityCheck.VertScrollBar.Position

ORIGINAL (line 1912): `with scrlbx_QualityCheck.VertScrollBar do`
RESOLVED: scrlbx_QualityCheck.VertScrollBar is TControlScrollBar. Members accessed: Position → scrlbx_QualityCheck.VertScrollBar.Position

ORIGINAL (line 1997): `with FPatient do`
RESOLVED: FPatient is HmdPatinf. Members accessed: patient info arrays → FPatient.sFieldName[index]

ORIGINAL (line 2137): `with QcInfo do`
RESOLVED: QcInfo is HmdIcqcit (local variable). Members accessed: quality check data arrays → QcInfo.sFieldName[index]

ORIGINAL (line 2285): `with check do`
RESOLVED: check is HmdIcuinf (local variable). Members accessed: component value arrays → check.sFieldName[index]

ORIGINAL (line 2382): `with QcInfo do`
RESOLVED: QcInfo is HmdIcqcit (local variable). Members accessed as above.

ORIGINAL (line 2422): `with curChk do`
RESOLVED: curChk is HmdIcuinf (local variable). Members accessed: component value fields → curChk.sFieldName[index]

ORIGINAL (line 2452): `with curChk do`
RESOLVED: curChk is HmdIcuinf. Members accessed as above.

ORIGINAL (line 2482): `with curChk do`
RESOLVED: curChk is HmdIcuinf. Members accessed as above.

ORIGINAL (line 2510): `with curChk do`
RESOLVED: curChk is HmdIcuinf. Members accessed as above.

ORIGINAL (line 2538): `with curChk do`
RESOLVED: curChk is HmdIcuinf. Members accessed as above.

ORIGINAL (line 3109): `with AQcInfo do`
RESOLVED: AQcInfo is HmdIcqcit (parameter). Members accessed: quality check arrays → AQcInfo.sFieldName[index]

ORIGINAL (line 4596): `with FPatient do`
RESOLVED: FPatient is HmdPatinf. Members accessed: patient info arrays → FPatient.sFieldName[index]

ORIGINAL (line 7095): `with ugd_EmrList do`
RESOLVED: ugd_EmrList is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_EmrList.RowCount

ORIGINAL (line 7199): `with FPatient do`
RESOLVED: FPatient is HmdPatinf. Members accessed as above.

ORIGINAL (line 7463): `with QcInfo do`
RESOLVED: QcInfo is HmdIcqcit (local variable). Members accessed as above.

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FX | TMDN110FX | External callers | FormCreate (implicit), FormDestroy (set to Nil) |
| FsPatNo | String | All middleware calls | External caller via property |
| FsAdmDate | String | All middleware calls | External caller via property |
| FPatient | HmdPatinf | Display/print methods | LoadPatientInfo |
| FsCurDuty | String | Save/Delete/Copy methods | SetAssessDateAndCurrentDuty |
| FIsRoot | Boolean | SetControlStatusOfDuty | SetAuthority |

## Custom Destructors

N/A -- no custom destructors with side effects. FPatient (HmdPatinf) must be explicitly freed.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for all middleware objects.
- **Persistent field object**: FPatient (HmdPatinf) stored as field, must be freed on form close.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. This is the NICU variant of MDN110UV (ICU quality check). The quality check items are NICU-specific but the form structure and middleware patterns are the same.
2. MDN110UU is referenced in implementation uses for cross-form data sharing.
3. MDN110UV_P01 is referenced in implementation uses — ASSUMPTION: the NICU quality check reuses the ICU quality check print report form, or this is a copy-paste artifact.
