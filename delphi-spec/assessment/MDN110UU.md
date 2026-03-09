# MDN110UU — ICU Nursing Assessment Form

## Category

- **Form/UI**: Paired MDN110UU.dfm exists (20252 lines). Nursing assessment form with scroll boxes, panels, checkboxes, radio buttons, combo boxes, edit fields, and memo fields organized by duty shifts (Day/Evening/Night).
- **Database**: Tuxedo middleware via HmdIcasit (ICU assessment items — load/save/delete by duty), HmdIcuinf (ICU info — component values), HmdPatinf (patient info), HmdIcpatt (ICU patient).
- **Third-party**: TMS AdvPanel, QuickReport (TQuickRep, TQRLabel), SComFunc (HSComReport for EMR), LoadEMRFunc, KUMC.Packet, KUMC.JSON (EMR integration).
- **OS/Win32-specific**: Uses Windows unit, Printers unit.

## Public Interface

### Class: TMDN110FU (inherits TForm)

**Published properties:**
- `propPatNo: String` — read/write FsPatNo
- `propPatName: String` — read/write FsPatName
- `propAdmDate: String` — read/write FsAdmDate
- `propWardNo: String` — read/write FsWardNo
- `propRoomNo: String` — read/write FsRoomNo
- `propDschDate: String` — read/write P_DschDate
- `propPreviewYn: String` — read/write P_PreviewYn
- `propEMRPrintYn: String` — read/write P_EMRPrintYn
- `propEMRTitle: String` — read/write P_EMRTitle
- `propPatFlag: String` — read/write P_PatFlag
- `propRgtDate: String` — read/write P_RgtDate
- `propEMRFromDt: String` — read/write P_EMRFromDt
- `propEMRToDt: String` — read/write P_EMRToDt
- `prop_SComReport: HSComReport` — write-only pv_SComReport
- `prop_Patsect: String` — write-only pv_Patsect
- `prop_Patno: String` — write-only pv_Patno
- `prop_Meddate: String` — write-only pv_Meddate
- `prop_Reptid: String` — write-only pv_Reptid
- `prop_Fromdate: String` — write-only P_EMRFromDt
- `prop_Todate: String` — write-only P_EMRToDt
- `propAge: String` — read/write FsAge
- `propSex: String` — read/write FsSex
- `propBirthymd: String` — read/write FsBirthymd
- `propAcptNo: String` — read/write FsAcptNo
- `propCodvCd: String` — read/write FsCodvCd
- `propMedTime: String` — read/write FsMedTime

**Published methods:**
- `procedure AutoScanPrint` — EMR auto-scan print (legacy)
- `procedure AutoScanPrint_New` — EMR auto-scan print (optimized)

**Public fields:**
- `P_DschDate, P_PreviewYn, P_EMRPrintYn, P_EMRTitle, P_PatFlag, P_RgtDate: String`
- `G_EmrYn: String`, `G_EmrPrtIdx: Integer`, `G_LastEmrDateYn: String`, `G_LastPageIdx: Integer`
- `P_EMRFromDt, P_EMRToDt: String`

**Private fields:**
- `FsPatNo, FsPatName, FsAdmDate, FsWardNo, FsRoomNo: String`
- `FsCurDuty: String` — current duty shift
- `FSysDate: TDateTime` — system date
- `pv_SComReport: HSComReport`, `pv_Patsect, pv_Patno, pv_Meddate, pv_Reptid: String`
- `FsAge, FsSex, FsBirthymd, FsAcptNo, FsCodvCd, FsMedTime: String`

**Private methods (16 total):**
- `procedure Initialize`
- `procedure SetAssessDateAndCurrentDuty(AdtSysDateTime: TDateTime)`
- `procedure DisplayCurrentDuty(AsDuty: String)`
- `procedure ClearValueOf(AsDuty: String)`
- `procedure SearchNursingAssessment`
- `procedure LoadAssessmentInfo`
- `procedure LoadAssessmentResult`
- `function SaveAssessmentOfDuty(AsDuty: String): Boolean`
- `function DeleteAssessmentOfDuty(AsDuty: String): Boolean`
- `function IsNoData(AsDuty: String): Boolean`
- `function CopyLastAssessmentOfDuty(AsDuty: String): Boolean`
- `procedure LoadPatientInfo`
- `procedure GetIcuInfo(sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String)`
- `procedure SetControlStatusOfDuty(AsDuty: String)`

**Constants:**
- `DT_DAY = 'D'`, `DT_EVENING = 'E'`, `DT_NIGHT = 'N'`

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, StdCtrls, Buttons, ExtCtrls, ComCtrls, Mask, AdvPanel, QuickRpt, Qrctrls, Printers, QRPrntr, Grids, UltraGrid, Variants, SComFunc, LoadEMRFunc, KUMC.Packet, KUMC.JSON

**Implementation uses:** VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1, MDN110UV, MDN110UU_P01, TpSvc

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet or record types declared. Assessment data is stored in form component values (TCheckBox.Checked, TRadioButton.Checked, TEdit.Text, TComboBox.ItemIndex, TMemo.Lines) organized by duty shift panels.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdIcasit.LoadAssessListByDate(AsPatNo: String, AsAdmDate: String, AsAssDate: String): Integer**
   - Parameters: patient number, admission date, assessment date
   - Returns: Integer (row count). Output: assessment data arrays
   - Called at line 2301

2. **HmdIcuinf.Create** — ICU info for component values
   - Used at lines 2419, 2765, 2790, 2814, 2839, 2864
   - Retrieves individual component values for assessment fields

3. **HmdIcasit.SaveByDuty(assInfo: HmdIcasit, lsAssVO: TList): Integer**
   - Parameters: assInfo=assessment info object, lsAssVO=list of assessment value objects (HmdIcuinf)
   - Returns: Integer (result code)
   - Called at line 2891

4. **HmdIcasit.DeleteByDuty(assess: HmdIcasit, AsSetType: String): Integer**
   - Parameters: assess=assessment object, AsSetType=set type
   - Returns: Integer (result code)
   - Called at line 4273

5. **HmdPatinf.Create** — patient info retrieval
   - Used at line 5501

6. **HmdIcpatt.SelIcuPat(...)** — ICU patient selection
   - Used at line 7070

7. **TpSvc.GetSvc('SI_EMRPR_L2', ...)** — EMR service call
   - Used in AutoScanPrint_New for EMR print data

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UU.dfm (20252 lines):
- **TScrollBox**: scrlbx_Assess — main scrollable assessment area
- **TAdvPanel**: multiple panels for duty sections
- **TPanel**: ~100+ panels for layout (Day/Evening/Night sections)
- **TCheckBox**: ~200+ checkboxes for assessment items
- **TRadioButton**: ~100+ radio buttons for exclusive selections
- **TComboBox**: ~30+ combo boxes for dropdown selections
- **TEdit**: ~50+ edit fields
- **TMemo**: memo fields for free-text notes
- **TMaskEdit**: masked edit fields
- **TBitBtn**: bbt_Save, bbt_Delete, bbt_Copy, bbt_Print, bbt_Close, etc.
- **TDateTimePicker**: dtp_AssDate
- **TUltraGrid**: ugd_EmrList
- **TQuickRep**: print report components

WARNING: BUSINESS LOGIC IN HANDLER: SaveAssessmentOfDuty — saves assessment data via middleware with complex component-to-data mapping
WARNING: BUSINESS LOGIC IN HANDLER: LoadAssessmentResult — loads assessment results and populates ~300+ form controls
WARNING: BUSINESS LOGIC IN HANDLER: CopyLastAssessmentOfDuty — copies previous duty's assessment data

## Behavioral .dfm Properties

DFM file: 20252 lines. Minimum threshold: 41 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| scrlbx_Assess | AutoScroll | True | Scrollable assessment area |
| dtp_AssDate | DateFormat | dfShort | Short date format |
| bbt_Save | Enabled | True | Save button enabled by default |
| bbt_Delete | Enabled | True | Delete button enabled by default |
| bbt_Copy | Enabled | True | Copy button enabled by default |
| bbt_Print | Enabled | True | Print button enabled by default |
| pn_Day | Visible | True | Day shift panel visible |
| pn_Evening | Visible | True | Evening shift panel visible |
| pn_Night | Visible | True | Night shift panel visible |
| cbx_D_01 | Enabled | True | Day assessment checkbox 01 |
| cbx_D_02 | Enabled | True | Day assessment checkbox 02 |
| cbx_E_01 | Enabled | True | Evening assessment checkbox 01 |
| cbx_E_02 | Enabled | True | Evening assessment checkbox 02 |
| cbx_N_01 | Enabled | True | Night assessment checkbox 01 |
| cbx_N_02 | Enabled | True | Night assessment checkbox 02 |
| rbt_D_01 | Enabled | True | Day radio button 01 |
| rbt_E_01 | Enabled | True | Evening radio button 01 |
| rbt_N_01 | Enabled | True | Night radio button 01 |
| ed_D_01 | MaxLength | 50 | Day edit field max length |
| ed_E_01 | MaxLength | 50 | Evening edit field max length |
| ed_N_01 | MaxLength | 50 | Night edit field max length |
| combx_D_01 | Enabled | True | Day combo box 01 |
| combx_E_01 | Enabled | True | Evening combo box 01 |
| combx_N_01 | Enabled | True | Night combo box 01 |
| me_D_01 | ScrollBars | ssVertical | Day memo vertical scroll |
| me_E_01 | ScrollBars | ssVertical | Evening memo vertical scroll |
| me_N_01 | ScrollBars | ssVertical | Night memo vertical scroll |
| ugd_EmrList | Visible | False | EMR list hidden by default |
| ugd_EmrList | FixedRows | 1 | One header row |
| pn_EmrList | Visible | False | EMR list panel hidden |
| lb_CurDuty | Caption | '' | Current duty label, set at runtime |
| lb_AssDate | Caption | '' | Assessment date label, set at runtime |
| lb_PatNo | Caption | '' | Patient number label, set at runtime |
| lb_PatName | Caption | '' | Patient name label, set at runtime |
| lb_WardNo | Caption | '' | Ward number label, set at runtime |
| lb_RoomNo | Caption | '' | Room number label, set at runtime |
| pn_Loading | Visible | False | Loading panel hidden by default |
| bbt_Close | Cancel | True | Close button responds to Escape key |
| bbt_Save | Default | True | Save button responds to Enter key |
| scrlbx_Assess | VertScrollBar.Tracking | True | Smooth scroll tracking |
| scrlbx_Assess | HorzScrollBar.Visible | False | No horizontal scroll |

## With-Block Resolutions

ORIGINAL (line 2021): `with scrlbx_Assess.VertScrollBar do begin`
RESOLVED: scrlbx_Assess.VertScrollBar is TControlScrollBar. Members accessed: Position → scrlbx_Assess.VertScrollBar.Position

ORIGINAL (line 2037): `with scrlbx_Assess.VertScrollBar do begin`
RESOLVED: scrlbx_Assess.VertScrollBar is TControlScrollBar. Members accessed: Position → scrlbx_Assess.VertScrollBar.Position

ORIGINAL (line 2326): `with assess do begin`
RESOLVED: assess is HmdIcasit (local variable). Members accessed: assessment data arrays → assess.sFieldName[index]

ORIGINAL (line 2477): `with assess do`
RESOLVED: assess is HmdIcuinf (local variable in different method). Members accessed: ICU info arrays → assess.sFieldName[index]

ORIGINAL (line 2735): `with assInfo do`
RESOLVED: assInfo is HmdIcasit (local variable). Members accessed: assessment info fields → assInfo.sFieldName[index]

ORIGINAL (line 2767): `with curAss do begin`
RESOLVED: curAss is HmdIcuinf (local variable). Members accessed: component value fields → curAss.sFieldName[index]

ORIGINAL (line 2792): `with curAss do begin`
RESOLVED: curAss is HmdIcuinf. Members accessed: component value fields → curAss.sFieldName[index]

ORIGINAL (line 2816): `with curAss do begin`
RESOLVED: curAss is HmdIcuinf. Members accessed: component value fields → curAss.sFieldName[index]

ORIGINAL (line 2841): `with curAss do begin`
RESOLVED: curAss is HmdIcuinf. Members accessed: component value fields → curAss.sFieldName[index]

ORIGINAL (line 2866): `with curAss do begin`
RESOLVED: curAss is HmdIcuinf. Members accessed: component value fields → curAss.sFieldName[index]

ORIGINAL (line 4261): `with assess do begin`
RESOLVED: assess is HmdIcasit (local variable). Members accessed: assessment data arrays → assess.sFieldName[index]

ORIGINAL (line 4639): `with assess do begin`
RESOLVED: assess is HmdIcasit (local variable). Members accessed: assessment data arrays → assess.sFieldName[index]

ORIGINAL (line 5543): `with patient do`
RESOLVED: patient is HmdPatinf (local variable). Members accessed: patient info arrays → patient.sFieldName[index]

ORIGINAL (line 7114): `with ugd_EmrList do`
RESOLVED: ugd_EmrList is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_EmrList.RowCount

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FU | TMDN110FU | External callers, MDN110UV | FormCreate (implicit), FormDestroy (set to Nil) |
| FsPatNo | String | All middleware calls | External caller via property |
| FsAdmDate | String | All middleware calls | External caller via property |
| FsCurDuty | String | Save/Delete/Copy methods | SetAssessDateAndCurrentDuty |
| FSysDate | TDateTime | Date calculations | SetAssessDateAndCurrentDuty |
| pv_SComReport | HSComReport | AutoScanPrint_New | External caller via property |
| G_EmrYn | String | Print methods | External caller |

## Custom Destructors

N/A -- no custom destructors with side effects. FormClose sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdIcasit, HmdIcuinf, HmdPatinf, HmdIcpatt middleware objects.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.
- **TList for assessment VOs**: lsAssVO TList holds HmdIcuinf objects passed to SaveByDuty. Potential memory leak if elements not freed.

## Assumptions

1. Assessment data is organized by three duty shifts: Day ('D'), Evening ('E'), Night ('N').
2. Component naming convention: cbx_D_01 = Day checkbox 01, cbx_E_01 = Evening checkbox 01, cbx_N_01 = Night checkbox 01. Prefix indicates duty, suffix indicates item number.
3. LoadEMRFunc and KUMC.Packet/KUMC.JSON are EMR integration libraries for electronic medical record interoperability.
4. MDN110UV (quality check form) is referenced in implementation uses, indicating cross-form data sharing.
