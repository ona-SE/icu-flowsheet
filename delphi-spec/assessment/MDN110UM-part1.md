# MDN110UM — ICU Patient Monitoring & OCS Flowsheet

## Category

- **Form/UI**: Paired MDN110UM.dfm exists (5729 lines). Main ICU patient monitoring form with grids, charts, panels, and popup menus.
- **Database**: Tuxedo middleware via HmdIcpatt (patient info), HmdIcutot (monitoring totals), HmdNrrect (nursing records), HmdInsamt (insurance), HmdIochkt (I/O check), HmdHuockt (HUO check), HmdWrkLst (work list), HmdTemplt (templates), HmdNbabyt (newborn baby), HmdPatInf (patient info), HmdPdiagt (diagnosis).
- **Third-party**: TMS AdvStringGrid (AdvGrid unit — TAdvStringGrid, TAdvPanel), UltraGrid (TUltraGrid), Bianco_Panel (TBianco_Panel), QuickReport (TQuickRep, TQRLabel), VCL TeeChart (TChart, TLineSeries), SComFunc (HSComReport for EMR reporting), TpSvc (EMR service calls).
- **OS/Win32-specific**: Uses Windows unit (messages, API types). Uses Printers unit for direct printing.

## Public Interface

### Class: TMDN110FM (inherits TForm)

**Published properties:**
- `prop_PatNo: String` — read/write P_PatNo
- `prop_PatName: String` — read/write P_PatName
- `prop_SexAge: String` — read/write P_SexAge
- `prop_AdmDate: String` — read/write P_AdmDate
- `prop_WardNo: String` — read/write P_WardNo
- `prop_RoomNo: String` — read/write P_RoomNo
- `prop_RgtDate: String` — read/write P_RgtDate
- `prop_PatFlag: String` — read/write P_PatFlag (values: 'D', 'W', 'MDP110F2')
- `prop_DschDate: String` — read/write P_DschDate
- `prop_PreviewYn: String` — read/write P_PreviewYn
- `prop_EMRPrintYn: String` — read/write P_EMRPrintYn
- `prop_EMRTitle: String` — read/write P_EMRTitle
- `prop_NicuFlag: String` — read/write P_NicuFlag (values: 'Y'=NICU, 'S'=SU)
- `prop_ChaDr: String` — read/write P_ChaDr
- `prop_MedDept: String` — read/write P_MedDept
- `prop_KoihaPrtyn: String` — read/write FsKoihaPrtyn
- `prop_SComReport: HSComReport` — write-only pv_SComReport
- `prop_Patsect: String` — write-only pv_Patsect
- `prop_Meddate: String` — write-only pv_Meddate
- `prop_Reptid: String` — write-only pv_Reptid
- `prop_Fromdate: String` — write-only P_EMRFromDt
- `prop_Todate: String` — write-only P_EMRToDt
- `prop_EMRFromDt: String` — read/write P_EMRFromDt
- `prop_EMRToDt: String` — read/write P_EMRToDt

**Public fields:**
- `ActCont: String`
- `P_PatNo, P_PatName, P_SexAge, P_AdmDate, P_WardNo, P_RoomNo: String`
- `G_SetFlag: String` — monitoring set status (Y/N)
- `P_RgtDate, P_PatFlag, P_DschDate, P_PreviewYn, P_EMRPrintYn, P_EMRTitle: String`
- `P_NicuFlag, P_ChaDr, P_MedDept: String`
- `G_EmrYn: String` — EMR enabled (Y/N)
- `G_EmrPrtIdx: Integer` — EMR print index
- `G_LastEmrDateYn: String`
- `G_LastPageIdx: Integer`
- `P_EMRFromDt, P_EMRToDt: String`

**Public methods:**
- `procedure Refresh` — Reloads Code/Time/Data and refreshes grid display
- `procedure AutoScanPrint` — EMR auto-scan print (legacy, CPU-intensive)
- `procedure Refresh_AutoScan` — Refresh for auto-scan mode
- `procedure AutoScanPrint_New` — EMR auto-scan print (optimized, ~1/3 CPU)

**Form components (declared in type section):**
- `stb_Message: TStatusBar`
- `pn_ICU: TPanel`
- `asg_IcuMon: TAdvStringGrid` — main monitoring grid
- `cds_MonItem: TClientDataSet` — monitoring item dataset
- `cds_SaveItem: TClientDataSet` — save item dataset
- `apn_Note: TAdvPanel`
- `chr_VS: TChart` — vital signs chart (8 series)
- `chr_VS_Su: TChart` — SU vital signs chart
- `asg_IoSum: TAdvStringGrid` — I/O summary grid
- `asg_Note: TAdvStringGrid` — notes grid
- `asg_Print: TAdvStringGrid` — print grid
- `asg_Crrt: TAdvStringGrid` — CRRT grid
- `ugd_PatList: TUltraGrid` — patient list
- `ugd_EmrList: TUltraGrid` — EMR list
- `ugd_UserList: TUltraGrid` — user list
- `ugd_BsData: TUltraGrid` — blood sugar data
- `ugd_IoData: TUltraGrid` — I/O data
- `dtp_RgtDate: TDateTimePicker` — registration date
- `dtp_RecDate: TDateTimePicker` — record date
- `dtp_Fromdate, dtp_Todate: TDateTimePicker` — note search range
- `dtb_Crrt: TDateTimePicker` — CRRT date
- `combx_Moniprd: TComboBox` — monitoring period
- `combx_WardNm, combx_WardCd: TComboBox` — ward selection
- `combx_DiagName: TComboBox` — diagnosis name
- `combx_ActList: TComboBox` — action list
- `med_ActTime: TMaskEdit` — action time input
- `me_Content: TMemo` — note content
- `me_Note: TMemo` — note memo
- `me_CrrtNrrec: TMemo` — CRRT nursing record
- `Memo1: TMemo` — log memo
- Various TBitBtn, TSpeedButton, TCheckBox, TRadioButton controls

## Dependencies

**Interface uses:**
Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ComCtrls, StdCtrls, ExtCtrls, Grids, UltraGrid, Buttons, Bianco_Panel, Mask, Menus, CheckLst, BaseGrid, AdvGrid, AdvPanel, Db, DBClient, Printers, QRPrntr, FileCtrl, QuickRpt, Qrctrls, Variants, VclTee.TeEngine, VclTee.Series, VclTee.TeeProcs, VclTee.Chart, AdvObj, VclTee.TeeGDIPlus, SComFunc

**Implementation uses:**
CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil, MDN110UM_P01, MDN110UM_P02, TpSvc

## Conditional Compilation

N/A -- no {$ifdef}, {$ifndef}, {$if}, or {$ifopt} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

### cds_MonItem: TClientDataSet
Fields:
- `setcode: TStringField` — monitoring set code
- `setname: TStringField` — monitoring set name
- `itemcode: TStringField` — item code
- `itemname: TStringField` — item name
- `dispseq: TStringField` — display sequence
- `inputtyp: TStringField` — input type
- `limit: TStringField` — limit value
- `upcode: TStringField` — upper code

Populated by: middleware call via HmdIcutot.GetMonitorDayList, then iterated and stored.
Consumed by: grid display in asg_IcuMon, used to determine editor types and validation.

### cds_SaveItem: TClientDataSet
Fields:
- `setcode: TStringField` — monitoring set code
- `acttime: TStringField` — action time
- `itemvalue: TStringField` — item value
- `modflag: TStringField` — modification flag
- `intflag: TStringField` — interface flag
- `addinfo: TStringField` — additional info

Populated by: user input from grid, assembled in SetSaveList.
Consumed by: middleware call via HmdIcutot.InsertMonItem for saving.

### sl_CodeList: TStringList (private)
Populated by: SetCodeList procedure from middleware data.
Consumed by: grid column mapping for monitoring codes.

### sl_TimeList: TStringList (private)
Populated by: SetTimeList procedure from middleware data.
Consumed by: grid row mapping for time slots.

### l_CodeItem: TList (private)
Holds HmdIcutot objects per set code.
Populated by: GetCodeList/SetCodeList from middleware.
Consumed by: grid display and editor type determination.

### l_SaveItem: TList (private)
Holds HmdIcutot objects for items to save.
Populated by: GetSaveList procedure.
Consumed by: InsertMonItem middleware call.

## Generics

N/A -- no generic types used in this unit. TList and TStringList are non-generic Delphi classic collections.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdIcpatt.SelIcuPat(sType1: String, sType2: String, sType3: String, sType4: String, sType5: String, sType6: String, sFlag1: String): Integer**
   - Parameters: sType1=PatNo, sType2=AdmDate, sType3=WardNo, sType4=RoomNo, sType5=FromDate, sType6=ToDate, sFlag1=flag ('FORMSHOW', 'REFRESH', etc.)
   - Returns: Integer (row count). Output arrays: iPats.sBldType[], iPats.sPatNo[], iPats.sAdmDate[], iPats.sActDate[], iPats.sMoniPrd[]
   - Error: returns 0 on no data, negative on error

2. **HmdIcpatt.InsertIcuPat: Integer**
   - Parameters: set via property assignments before call (sPatNo, sAdmDate, sWardNo, sRoomNo, sSetType, sActDate, sMoniPrd)
   - Returns: Integer. Output: iPats.iRtnCd[0] ('0'=success, '1'=already exists)
   - Error: exception on failure

3. **HmdIcutot.GetMonitorDayList(sType1: String, sType2: String, sType3: String, sType4: String, sType5: String): Integer**
   - Parameters: sType1=PatNo, sType2=AdmDate, sType3=ActDate, sType4=SetCode, sType5=SetType
   - Returns: Integer (row count). Output arrays on iCrect: item codes, names, values, times
   - Error: returns 0 on no data

4. **HmdIcutot.InsertDayMonitorList(sType1: String, j: Integer): Integer**
   - Parameters: sType1=flag, j=index
   - Returns: Integer (row count)
   - Error: returns 0 on failure

5. **HmdIcutot.InsertMonItem(l_SaveItem: TList): Integer**
   - Parameters: l_SaveItem=TList of HmdIcutot objects containing save data
   - Returns: Integer (result code)
   - Error: exception on failure

6. **HmdIcutot.LoadMonItem(sPatNo: String, sAdmDate: String, sFromActDate: String, sToActDate: String): Integer**
   - Parameters: patient number, admission date, date range
   - Returns: Integer (row count)
   - Error: returns 0 on no data

7. **HmdNrrect (nursing record)** — used in SelNote procedure for note retrieval
   - Called at line ~7080 area

8. **HmdInsamt (insurance)** — used for insurance amount lookup
   - Called at line ~7230 area

9. **HmdWrkLst (work list)** — used in GetPatList for patient list retrieval
   - Called at line ~9627

10. **HmdIochkt (I/O check)** — used in GetBsData and GetIoCheck
    - Called at lines ~10419, ~10592

11. **HmdHuockt (HUO check)** — used in GetIoCheck for HUO data
    - Called at line ~10713

12. **HmdTemplt (template)** — used for template selection/insertion
    - Called at line ~7524

13. **HmdPatInf (patient info)** — used in GetPatList
    - Called at line ~8984

14. **HmdPdiagt (diagnosis)** — used in GetMainDiag
    - Called at line ~10197 area

15. **HmdNbabyt (newborn baby)** — used in GetNbabyBorndate
    - Called at line ~11096 area

16. **TpSvc.GetSvc('SI_EMRPR_L2', ...)** — EMR service call for print data
    - Called at line 11832
    - Output: GetOutputDataS('Meddept', 0), GetOutputDataS('Chadrid', 0)

## DLL / External API Bindings

N/A -- no external function imports or GetProcAddress/LoadLibrary calls in this unit.

## Form Components

### Components from MDN110UM.dfm (234 components total):

Key components by type:
- **TAdvStringGrid**: asg_IcuMon (main monitoring grid), asg_IoSum, asg_Note, asg_Print, asg_Crrt, asd_NoteSearch
- **TUltraGrid**: ugd_PatList, ugd_EmrList, ugd_UserList, ugd_BsData, ugd_IoData
- **TChart**: chr_VS (8 series: Series2-Series10), chr_VS_Su (7 series: LineSeries1-LineSeries7)
- **TClientDataSet**: cds_MonItem (7 fields), cds_SaveItem (6 fields)
- **TAdvPanel**: apn_Note, apn_InsTempl, apn_InsActing, apn_PatList, apn_Bst, apn_IoChk, apn_NoteSearch, apn_Crrt, Advpn_Log
- **TDateTimePicker**: dtp_RgtDate, dtp_RecDate, dtp_Fromdate, dtp_Todate, dtb_Crrt
- **TBitBtn**: bbt_MoniSave, bbt_Monitor, bbt_Quality, bbt_Ass, bbt_Close, bbt_Print, bbt_ShowNote, bbt_Moniprd, bbt_VS, bbt_Cancel, bbt_Ok, bbt_Select, bbt_ListExit, bbt_SetInsert, bbt_SetExit, bbt_InsActing, bbt_ActExit, bbt_BstClose, bbt_IoClose, bbt_NoteSearch, bbt_ShowNoteSearch, bbt_NurseWrite, bbt_CrrtSave, bbt_CrrtBefor, bbt_CrrtClose, bbt_CrrtClear, bbt_CrrtAfter, bbt_Crrt, bbt_ConfirmInputNote, bbt_CancelInputNote
- **TSpeedButton**: sbt_Refresh, sbt_PrevDate, sbt_NextDate, sbt_AddTime, sbt_DelTime, sbt_Print, sbt_Nrrec, sbt_TemplSel, sbt_TemplIns, sbt_SelVs, sbt_SelResp, sbt_SelBst, sbt_SelO2, sbt_Printer
- **TPopupMenu**: Popup_Act (items: mi_InsBsAct, mi_DelAct, mi_InsCvpAct, mi_InsVsAct, mi_InsBsData, mi_InsIoData)

### Event handler assignments (from .dfm):

| Component | Event | Handler |
|-----------|-------|---------|
| MDN110FM (Form) | OnCreate | FormCreate |
| MDN110FM (Form) | OnShow | FormShow |
| MDN110FM (Form) | OnClose | FormClose |
| MDN110FM (Form) | OnDestroy | FormDestroy |
| asg_IcuMon | OnGetAlignment | asg_IcuMonGetAlignment |
| asg_IcuMon | OnGetCellColor | asg_IcuMonGetCellColor |
| asg_IcuMon | OnSelectCell | asg_IcuMonSelectCell |
| asg_IcuMon | OnKeyPress | asg_IcuMonKeyPress |
| asg_IcuMon | OnEditingDone | asg_IcuMonEditingDone |
| asg_IcuMon | OnClickCell | asg_IcuMonClickCell |
| asg_IcuMon | OnMouseMove | asg_IcuMonMouseMove |
| asg_IcuMon | OnDrawCell | asg_IcuMonDrawCell |
| asg_IcuMon | OnGetEditorType | asg_IcuMonGetEditorType |
| asg_IcuMon | OnGetEditMask | asg_IcuMonGetEditMask |
| asg_IcuMon | OnExit | asg_IcuMonExit |
| asg_IcuMon | OnCellChanging | asg_IcuMonCellChanging |
| bbt_MoniSave | OnClick | bbt_MoniSaveClick |
| bbt_Monitor | OnClick | bbt_MonitorClick |
| bbt_Close | OnClick | bbt_CloseClick |
| bbt_Quality | OnClick | bbt_QualityClick |
| bbt_Ass | OnClick | bbt_AssClick |
| bbt_Print | OnClick | bbt_PrintClick |
| bbt_ShowNote | OnClick | bbt_ShowNoteClick |
| bbt_Moniprd | OnClick | bbt_MoniprdClick |
| dtp_RgtDate | OnChange | dtp_RgtDateChange |
| dtp_RgtDate | OnCloseUp | dtp_RgtDateCloseUp |
| cbx_Interface | OnClick | cbx_InterfaceClick |
| sbt_Refresh | OnClick | sbt_RefreshClick |
| sbt_PrevDate | OnClick | bbt_PrevDateClick |
| sbt_NextDate | OnClick | bbt_NextDateClick |
| sbt_AddTime | OnClick | sbt_AddTimeClick |
| sbt_DelTime | OnClick | sbt_DelTimeClick |
| chr_VS | OnAfterDraw | chr_VSAfterDraw |
| chr_VS | OnMouseMove | chr_VSMouseMove |
| ugd_PatList | OnClick | ugd_PatListClick |
| ugd_PatList | OnDrawCell | ugd_PatListDrawCell |
| ugd_PatList | OnMouseMove | ugd_PatListMouseMove |
| ugd_BsData | OnDblClick | ugd_BsDataDblClick |
| ugd_BsData | OnDrawCell | ugd_BsDataDrawCell |
| ugd_IoData | OnDblClick | ugd_IoDataDblClick |
| ugd_IoData | OnDrawCell | ugd_IoDataDrawCell |
| Popup_Act | OnPopup | Popup_ActPopup |

WARNING: BUSINESS LOGIC IN HANDLER: bbt_MoniSaveClick (lines 2274-2350) — saves monitoring data via middleware
WARNING: BUSINESS LOGIC IN HANDLER: bbt_MonitorClick (lines 1555-1622) — inserts ICU patient monitoring record
WARNING: BUSINESS LOGIC IN HANDLER: bbt_PrintClick (lines 6121-6443) — generates print output with complex grid-to-report mapping
WARNING: BUSINESS LOGIC IN HANDLER: asg_IcuMonKeyPress (lines 2075-2273) — validates input and triggers save logic
WARNING: BUSINESS LOGIC IN HANDLER: asg_IcuMonClickCell (lines 5150-5380) — handles cell click with note display and data loading
WARNING: BUSINESS LOGIC IN HANDLER: sbt_AddTimeClick (lines 6037-6120) — adds time column with middleware call
WARNING: BUSINESS LOGIC IN HANDLER: sbt_DelTimeClick (lines 6651-6760) — deletes time column with middleware call
WARNING: BUSINESS LOGIC IN HANDLER: bbt_CrrtSaveClick (lines ~11400-11600) — saves CRRT data
WARNING: BUSINESS LOGIC IN HANDLER: FormShow (lines 704-931) — complex initialization with conditional UI setup based on P_PatFlag and P_NicuFlag

## Behavioral .dfm Properties

DFM file: 5729 lines. Minimum threshold: 12 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| med_ActTime | MaxLength | 5 | Limits time input to 5 chars (HH:MM format) |
| ed_SetTitle | MaxLength | 30 | Limits template title to 30 chars |
| ed_ActRemark | MaxLength | 30 | Limits action remark to 30 chars |
| ed_RecName | MaxLength | 30 | Limits recorder name to 30 chars |
| ed_RecDept | MaxLength | 30 | Limits department name to 30 chars |
| ed_RecDept | Enabled | False | Department field is read-only by default |
| combx_WardNm | Enabled | False | Ward combo disabled until patient selected |
| combx_WardCd | Visible | False | Hidden ward code combo (internal use) |
| combx_DiagName | Visible | False | Diagnosis combo hidden by default |
| pn_If | Visible | False | Chart panel hidden by default |
| pn_If_Su | Visible | False | SU chart panel hidden by default |
| pn_Loading | Visible | False | Loading bar hidden until data load |
| pn_EmrList | Visible | False | EMR list panel hidden by default |
| apn_InsTempl | Visible | False | Template insertion panel hidden |
| apn_InsActing | Visible | False | Action insertion panel hidden |
| apn_Bst | Visible | False | Blood sugar panel hidden |
| apn_IoChk | Visible | False | I/O check panel hidden |
| apn_Note | Visible | False | Note panel hidden |
| apn_NoteSearch | Visible | False | Note search panel hidden (ASSUMPTION: shown via bbt_ShowNoteSearchClick) |
| apn_Crrt | Visible | False | CRRT panel hidden (ASSUMPTION: shown via bbt_CrrtClick) |
| asg_Print | Visible | False | Print grid hidden (used for print preview) |
| bbt_VS | Visible | False | VS chart button hidden |
| bbt_ShowNoteSearch | Visible | False | Note search button hidden |
| bbt_Crrt | Visible | False | CRRT button hidden |
| sbt_Print | Visible | False | Print speed button hidden |
| rbt_SortDept | Visible | False | Sort-by-department radio hidden |
| lb_PatName | Visible | False | Patient name label hidden initially |
| lb_SexAge | Visible | False | Sex/age label hidden initially |
| lb_InsUp | Visible | False | Insurance update label hidden |
| lb_ActDate | Visible | False | Action date label hidden |
| lb_ActSeqNo | Visible | False | Action sequence label hidden |
| lb_Flag | Visible | False | Flag label hidden |
| Series5 | Visible | False | Chart series 5 hidden by default |
| Series6 | Visible | False | Chart series 6 hidden by default |
| Series7 | Visible | False | Chart series 7 hidden by default |
| Series8 | Visible | False | Chart series 8 hidden by default |
| LineSeries3 | Visible | False | SU chart series 3 hidden |
| LineSeries4 | Visible | False | SU chart series 4 hidden |
| LineSeries6 | Visible | False | SU chart series 6 hidden |
| LineSeries7 | Visible | False | SU chart series 7 hidden |
| BitBtn1 | Visible | False | SU chart button hidden |
