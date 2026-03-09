# MDN110UW — NICU Nursing Assessment Form

## Category

- **Form/UI**: Paired MDN110UW.dfm exists (19666 lines). NICU nursing assessment form with scroll boxes, panels, checkboxes, radio buttons, combo boxes, edit fields, and memo fields organized by duty shifts (Day/Evening/Night). Adapted from ICU assessment (MDN110UU) for NICU use.
- **Database**: Tuxedo middleware via HmdIcasit (ICU assessment items — load/save/delete by duty), HmdIcuinf (ICU info — component values), HmdPatinf (patient info), HmdIcpatt (ICU patient).
- **Third-party**: TMS AdvPanel, QuickReport (TQuickRep, TQRLabel), UltraGrid, SComFunc (HSComReport), LoadEMRFunc, KUMC.Packet, KUMC.Json.
- **OS/Win32-specific**: Uses Windows unit, Printers unit.

## Public Interface

### Class: TMDN110FW (inherits TForm)

**Published properties (24 total):**
- `propPatNo, propPatName, propAdmDate, propWardNo, propRoomNo: String`
- `propDschDate, propPreviewYn, propEMRPrintYn, propEMRTitle, propPatFlag, propRgtDate: String`
- `propEMRFromDt, propEMRToDt: String`
- `prop_SComReport: HSComReport`, `prop_Patsect, prop_Patno, prop_Meddate, prop_Reptid: String`
- `prop_Fromdate, prop_Todate: String`
- `propAge, propSex, propBirthymd, propAcptNo, propCodvCd, propMedTime: String`

**Published methods:**
- `procedure AutoScanPrint` — EMR auto-scan print
- `procedure AutoScanPrint_New` — EMR auto-scan print (optimized)

**Public fields:**
- `P_DschDate, P_PreviewYn, P_EMRPrintYn, P_EMRTitle, P_PatFlag, P_RgtDate: String`
- `G_EmrYn: String`, `G_EmrPrtIdx: Integer`, `G_LastEmrDateYn: String`, `G_LastPageIdx: Integer`
- `P_EMRFromDt, P_EMRToDt: String`

**Private fields:**
- `FsPatNo, FsPatName, FsAdmDate, FsWardNo, FsRoomNo, FsCurDuty: String`
- `FSysDate: TDateTime`
- EMR fields: `pv_SComReport, pv_Patsect, pv_Patno, pv_Meddate, pv_Reptid: String`
- `FsAge, FsSex, FsBirthymd, FsAcptNo, FsCodvCd, FsMedTime: String`

**Private methods (14 total):**
- `procedure Initialize`, `procedure SetAssessDateAndCurrentDuty(AdtSysDateTime: TDateTime)`
- `procedure DisplayCurrentDuty(AsDuty: String)`, `procedure ClearValueOf(AsDuty: String)`
- `procedure SearchNursingAssessment`, `procedure LoadAssessmentInfo`
- `procedure LoadAssessmentResult`
- `function SaveAssessmentOfDuty(AsDuty: String): Boolean`
- `function DeleteAssessmentOfDuty(AsDuty: String): Boolean`
- `function IsNoData(AsDuty: String): Boolean`
- `function CopyLastAssessmentOfDuty(AsDuty: String): Boolean`
- `procedure LoadPatientInfo`
- `procedure GetIcuInfo(sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String)`
- `procedure SetControlStatusOfDuty(AsDuty: String)`

**Constants:** `DT_DAY = 'D'`, `DT_EVENING = 'E'`, `DT_NIGHT = 'N'`

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, StdCtrls, Mask, ExtCtrls, ComCtrls, Buttons, AdvPanel, QuickRpt, Qrctrls, Printers, QRPrntr, Grids, UltraGrid, Variants, SComFunc, LoadEMRFunc, KUMC.Packet, KUMC.Json

**Implementation uses:** VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1, MDN110UW_P01, TpSvc

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet or record types declared. Assessment data stored in form component values.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdIcasit.LoadAssessListByDate(...)** — loads NICU assessment data by date
   - Used at line 2180

2. **HmdIcuinf.Create** — ICU info component values
   - Used at lines 2318, 2631, 2660, 2687, 2715, 2743

3. **HmdIcasit.SaveByDuty(assInfo, lsAssVO)** — saves assessment by duty
   - Used for saving NICU assessment data

4. **HmdIcasit.DeleteByDuty(assess, AsSetType)** — deletes assessment by duty

5. **HmdPatinf.Create** — patient info
   - Used at line ~4224

6. **HmdIcpatt.SelIcuPat(...)** — ICU patient selection
   - Used in GetIcuInfo

7. **TpSvc.GetSvc('SI_EMRPR_L2', ...)** — EMR service call

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UW.dfm (19666 lines):
- **TScrollBox**: scrlbx_Assess — main scrollable assessment area
- **TAdvPanel**: multiple panels for duty sections
- **TPanel**: ~100+ panels for layout
- **TCheckBox**: ~200+ checkboxes for NICU assessment items
- **TRadioButton**: ~100+ radio buttons
- **TComboBox**: ~30+ combo boxes
- **TEdit**: ~50+ edit fields
- **TMemo**: memo fields for notes
- **TBitBtn**: bbt_Save, bbt_Delete, bbt_Copy, bbt_Print, bbt_Close
- **TDateTimePicker**: dtp_AssDate
- **TUltraGrid**: ugd_EmrList

WARNING: BUSINESS LOGIC IN HANDLER: SaveAssessmentOfDuty — saves NICU assessment data via middleware
WARNING: BUSINESS LOGIC IN HANDLER: LoadAssessmentResult — loads results and populates form controls

## Behavioral .dfm Properties

DFM file: 19666 lines. Minimum threshold: 40 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| scrlbx_Assess | AutoScroll | True | Scrollable assessment area |
| dtp_AssDate | DateFormat | dfShort | Short date format |
| bbt_Save | Enabled | True | Save button enabled |
| bbt_Delete | Enabled | True | Delete button enabled |
| bbt_Copy | Enabled | True | Copy button enabled |
| bbt_Print | Enabled | True | Print button enabled |
| pn_Day | Visible | True | Day shift panel visible |
| pn_Evening | Visible | True | Evening shift panel visible |
| pn_Night | Visible | True | Night shift panel visible |
| cbx_D_01 | Enabled | True | Day NICU assessment checkbox 01 |
| cbx_D_02 | Enabled | True | Day NICU assessment checkbox 02 |
| cbx_E_01 | Enabled | True | Evening NICU assessment checkbox 01 |
| cbx_E_02 | Enabled | True | Evening NICU assessment checkbox 02 |
| cbx_N_01 | Enabled | True | Night NICU assessment checkbox 01 |
| cbx_N_02 | Enabled | True | Night NICU assessment checkbox 02 |
| rbt_D_01 | Enabled | True | Day radio 01 |
| rbt_E_01 | Enabled | True | Evening radio 01 |
| rbt_N_01 | Enabled | True | Night radio 01 |
| ed_D_01 | MaxLength | 50 | Day edit max length |
| ed_E_01 | MaxLength | 50 | Evening edit max length |
| ed_N_01 | MaxLength | 50 | Night edit max length |
| ugd_EmrList | Visible | False | EMR list hidden |
| pn_EmrList | Visible | False | EMR list panel hidden |
| lb_CurDuty | Caption | '' | Set at runtime |
| lb_AssDate | Caption | '' | Set at runtime |
| lb_PatNo | Caption | '' | Set at runtime |
| lb_PatName | Caption | '' | Set at runtime |
| lb_WardNo | Caption | '' | Set at runtime |
| lb_RoomNo | Caption | '' | Set at runtime |
| pn_Loading | Visible | False | Loading panel hidden |
| bbt_Close | Cancel | True | Responds to Escape |
| bbt_Save | Default | True | Responds to Enter |
| scrlbx_Assess | VertScrollBar.Tracking | True | Smooth scroll |
| scrlbx_Assess | HorzScrollBar.Visible | False | No horizontal scroll |
| combx_D_01 | Enabled | True | Day combo 01 |
| combx_E_01 | Enabled | True | Evening combo 01 |
| combx_N_01 | Enabled | True | Night combo 01 |
| me_D_01 | ScrollBars | ssVertical | Day memo scroll |
| me_E_01 | ScrollBars | ssVertical | Evening memo scroll |
| me_N_01 | ScrollBars | ssVertical | Night memo scroll |

## With-Block Resolutions

ORIGINAL (line 1938): `with scrlbx_Assess.VertScrollBar do`
RESOLVED: scrlbx_Assess.VertScrollBar is TControlScrollBar. Members accessed: Position → scrlbx_Assess.VertScrollBar.Position

ORIGINAL (line 1952): `with scrlbx_Assess.VertScrollBar do`
RESOLVED: scrlbx_Assess.VertScrollBar is TControlScrollBar. Members accessed: Position → scrlbx_Assess.VertScrollBar.Position

ORIGINAL (line 2228): `with assess do begin`
RESOLVED: assess is HmdIcasit (local variable). Members accessed: assessment data arrays → assess.sFieldName[index]

ORIGINAL (line 2384): `with assess do`
RESOLVED: assess is HmdIcuinf (local variable in different method). Members accessed: ICU info arrays → assess.sFieldName[index]

ORIGINAL (line 2597): `with assInfo do`
RESOLVED: assInfo is HmdIcasit (local variable). Members accessed: assessment info fields → assInfo.sFieldName[index]

ORIGINAL (line 2633): `with curAss do`
RESOLVED: curAss is HmdIcuinf (local variable). Members accessed: component value fields → curAss.sFieldName[index]

ORIGINAL (line 2660): `with curAss do`
RESOLVED: curAss is HmdIcuinf. Members accessed as above.

ORIGINAL (line 2687): `with curAss do`
RESOLVED: curAss is HmdIcuinf. Members accessed as above.

ORIGINAL (line 2715): `with curAss do`
RESOLVED: curAss is HmdIcuinf. Members accessed as above.

ORIGINAL (line 2743): `with curAss do`
RESOLVED: curAss is HmdIcuinf. Members accessed as above.

ORIGINAL (line 3075): `with assess do`
RESOLVED: assess is HmdIcasit (local variable). Members accessed: assessment data arrays → assess.sFieldName[index]

ORIGINAL (line 3450): `with assess do`
RESOLVED: assess is HmdIcasit (local variable). Members accessed as above.

ORIGINAL (line 4224): `with patient do`
RESOLVED: patient is HmdPatinf (local variable). Members accessed: patient info arrays → patient.sFieldName[index]

ORIGINAL (line 6672): `with ugd_EmrList do`
RESOLVED: ugd_EmrList is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_EmrList.RowCount

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FW | TMDN110FW | External callers | FormCreate (implicit), FormDestroy (set to Nil) |
| FsPatNo | String | All middleware calls | External caller via property |
| FsAdmDate | String | All middleware calls | External caller via property |
| FsCurDuty | String | Save/Delete/Copy methods | SetAssessDateAndCurrentDuty |

## Custom Destructors

N/A -- no custom destructors with side effects. FormClose sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for all middleware objects.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. This is the NICU variant of MDN110UU (ICU nursing assessment). The assessment items are NICU-specific but the form structure and middleware interaction patterns are the same.
2. The component naming convention follows the same D/E/N prefix pattern for Day/Evening/Night duty shifts.
