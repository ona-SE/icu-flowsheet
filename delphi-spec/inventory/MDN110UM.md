# MDN110UM — Method Inventory (Part 1: Methods 1-42)

Unit: MDN110UM.pas (11893 lines)
Form class: TMDN110FM
Purpose: Main ICU/NICU/SU patient monitoring and OCS nursing flowsheet system. The central form that manages patient list, vital signs grid, charting, monitoring items, notes, print, and launches sub-forms (UO, UU, UV, UW, UX).
Uses: CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil, MDN110UM_P01, MDN110UM_P02, TpSvc, SComFunc, AdvGrid, UltraGrid, TeeChart

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | bbt_CloseClick | published | (Sender: TObject) | 649-660 | Close | LOW |
| 2 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 661-691 | Frees sub-forms (MDN110FU, FV, FW, FX, FO), Action := caFree | MED |
| 3 | FormDestroy | published | (Sender: TObject) | 692-703 | MDN110FM := Nil | LOW |
| 4 | FormShow | published | (Sender: TObject) | 704-931 | SetPatInfo, CheckFormSet, SetFormInfo, GetPatList, SelectPatInfo, GetIcuInfo, GetAllItems, SelectMonItem, Drawchart, InitChart, SetLoadingBar | HIGH |
| 5 | GetIcuInfo | private | (sFlag1, sType1, sType2, sType3, sType4, sType5, sType6: String) | 932-1246 | HmdIcuinf.Create, getIcuinflist, populates ICU info fields, handles multiple flag types for different data sections | HIGH |
| 6 | Drawchart | private | (Sender: TObject) | 1247-1554 | Reads grid data, populates TeeChart series for vital signs (temp, pulse, resp, BP, SpO2, etc.) | HIGH |
| 7 | bbt_MonitorClick | published | (Sender: TObject) | 1555-1622 | Toggles monitoring panel visibility, refreshes data | MED |
| 8 | dtp_RgtDateChange | published | (Sender: TObject) | 1623-1674 | Date change handler, refreshes monitoring data | MED |
| 9 | FormCreate | published | (Sender: TObject) | 1675-1743 | Initializes form variables, grid setup, chart setup | MED |
| 10 | asg_IcuMonGetAlignment | published | (Sender: TObject; ARow, ACol: Integer; var HAlign: TAlignment; var VAlign: TVAlignment) | 1744-1785 | Grid cell alignment callback | LOW |
| 11 | asg_IcuMonGetCellColor | published | (Sender: TObject; ARow, ACol: Integer; AState: TGridDrawState; ABrush: TBrush; AFont: TFont) | 1786-1842 | Grid cell color callback based on data type | MED |
| 12 | asg_IcuMonSelectCell | published | (Sender: TObject; ACol, ARow: Integer; var CanSelect: Boolean) | 1843-1862 | Grid cell selection callback | LOW |
| 13 | cbx_InterfaceClick | published | (Sender: TObject) | 1863-1950 | Interface checkbox toggle — enables/disables medical device interface data import | MED |
| 14 | bbt_MoniprdClick | published | (Sender: TObject) | 1951-2074 | Monitoring period button — sets time interval for data display | HIGH |
| 15 | asg_IcuMonKeyPress | published | (Sender: TObject; var Key: Char) | 2075-2273 | Grid key press handler — validates input per cell type (numeric, text, special codes) | HIGH |
| 16 | bbt_MoniSaveClick | published | (Sender: TObject) | 2274-2351 | Save monitoring data — calls GetSaveList for each modified cell, then SetSaveList | HIGH |
| 17 | SetPatInfo | private | (in_Flag: String) | 2352-2498 | Sets patient info from external parameters (P_PatNo, P_AdmDate, etc.) or from patient list grid | HIGH |
| 18 | CheckFormSet | private | () | 2499-2600 | Checks form configuration — determines ICU/NICU/SU mode, sets visible panels/tabs | MED |
| 19 | SetCodeList | private | (sGubun: String) | 2601-3050 | Loads monitoring item code list from HmdIcuinf into grid rows — maps item codes to display names | HIGH |
| 20 | GetCodeList | private | (sPatNo, sAdmDate: String): Integer | 3051-3432 | Retrieves saved monitoring data for a patient/date, populates grid cells | HIGH |
| 21 | SetTimeList | private | (sGubun: String) | 3433-3706 | Sets up time column headers in the monitoring grid based on period setting | HIGH |
| 22 | GetTimeList | private | (sPatNo, sAdmDate: String): Integer | 3707-3835 | Retrieves time-based monitoring data for grid columns | HIGH |
| 23 | bbt_AssClick | published | (Sender: TObject) | 3836-3865 | Opens nursing assessment form (MDN110FU or MDN110FW depending on ICU/NICU mode) | LOW |
| 24 | GetAllItems | private | () | 3866-3986 | Loads all monitoring items into the grid — calls SetCodeList, GetCodeList, SetTimeList, GetTimeList | HIGH |
| 25 | asg_IcuMonGetEditorType | published | (Sender: TObject; ACol, ARow: Integer; var AEditor: TEditorType) | 3987-4073 | Grid editor type callback — determines edit control per cell (text, combo, checkbox) | MED |
| 26 | GetSaveList | private | (sSetCode, sActTime, sItemVal, sIntFlag, sAddInfo: String) | 4074-4192 | Builds save list from grid cell values for a single item/time | MED |
| 27 | SetSaveList | private | (sGubun: String) | 4193-4934 | Saves all monitoring data — HmdIcuinf.Create, setIcuinflist, handles multiple data types and validation | HIGH |
| 28 | SelectMonItem | private | (dtp_ActDate: TDateTime) | 4935-5121 | Selects and highlights monitoring items based on date/time | HIGH |
| 29 | asg_IcuMonEditingDone | published | (Sender: TObject) | 5122-5149 | Grid editing done callback — marks cell as modified | LOW |
| 30 | asg_IcuMonClickCell | published | (Sender: TObject; ARow, ACol: Integer) | 5150-5380 | Grid cell click handler — opens popup editors for special cell types (notes, codes, checkboxes) | HIGH |
| 31 | bbt_PrevDateClick | published | (Sender: TObject) | 5381-5455 | Previous date button — decrements date, refreshes all data | MED |
| 32 | bbt_NextDateClick | published | (Sender: TObject) | 5456-5550 | Next date button — increments date, refreshes all data | MED |
| 33 | dtp_RgtDateCloseUp | published | (Sender: TObject) | 5551-5595 | Date picker close handler — refreshes data | MED |
| 34 | InitDataSet | private | (cds_Temp: TClientDataSet) | 5596-5612 | Initializes a TClientDataSet with field definitions | LOW |
| 35 | InitChart | private | () | 5613-5667 | Initializes TeeChart components — clears series, sets axes | MED |
| 36 | Refresh | private | () | 5668-5733 | Full data refresh — GetAllItems, SelectMonItem, Drawchart, CheckAllNote | HIGH |
| 37 | bbt_CancelInputNoteClick | published | (Sender: TObject) | 5734-5747 | Cancel note input | LOW |
| 38 | bbt_ConfirmInputNoteClick | published | (Sender: TObject) | 5748-5770 | Confirm note input — saves note text to grid cell | LOW |
| 39 | asg_IcuMonMouseMove | published | (Sender: TObject; Shift: TShiftState; X, Y: Integer) | 5771-5853 | Grid mouse move — shows tooltip for cell content | MED |
| 40 | bbt_QualityClick | published | (Sender: TObject) | 5854-5877 | Opens quality check form (MDN110FV or MDN110FX depending on ICU/NICU mode) | LOW |
| 41 | bbt_ShowNoteClick | published | (Sender: TObject) | 5878-5952 | Shows/hides note panel | MED |
| 42 | CheckAllNote | private | () | 5953-6036 | Checks all grid cells for notes, marks cells with note indicators | MED |
# MDN110UM — Method Inventory (Part 2: Methods 43-84)

## Method Inventory (continued)

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 43 | sbt_AddTimeClick | published | (Sender: TObject) | 6037-6120 | Adds a new time column to the monitoring grid | MED |
| 44 | bbt_PrintClick | published | (Sender: TObject) | 6121-6443 | Creates MDN110FM_P01/P02, populates QRLabels from grid data, chart data, patient info, Preview/Print | HIGH |
| 45 | SetLoadingBar | private | (AsStatus: String) | 6444-6483 | Shows/hides loading progress bar with status text | LOW |
| 46 | chr_VSAfterDraw | published | (Sender: TObject) | 6484-6552 | Chart after-draw event — draws custom annotations/markers on vital signs chart | MED |
| 47 | sbt_RefreshClick | published | (Sender: TObject) | 6553-6602 | Refresh button — calls Refresh | MED |
| 48 | chr_VSMouseMove | published | (Sender: TObject; Shift: TShiftState; X, Y: Integer) | 6603-6650 | Chart mouse move — shows tooltip for data points | LOW |
| 49 | sbt_DelTimeClick | published | (Sender: TObject) | 6651-6760 | Deletes a time column from the monitoring grid, with confirmation and data deletion | HIGH |
| 50 | bbt_CancelClick | published | (Sender: TObject) | 6761-6773 | Cancel button handler | LOW |
| 51 | asg_PrintDblClick | published | (Sender: TObject) | 6774-6787 | Print grid double-click handler | LOW |
| 52 | sbt_NrrecClick | published | (Sender: TObject) | 6788-7012 | Nursing record button — builds nursing record string from grid data, calls TpSvc for EMR integration | HIGH |
| 53 | SelNote | private | (in_ActDate, in_ActTime: String) | 7013-7203 | Selects and displays notes for a given date/time — HmdIcuinf.Create, getIcuinflist | HIGH |
| 54 | ed_RecNameKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 7204-7306 | Record name field key handler — SearchUser for nurse lookup, populates user list grid | MED |
| 55 | ugd_UserListDblClick | published | (Sender: TObject) | 7307-7325 | User list grid double-click — selects user | LOW |
| 56 | AutoScanPrint | private | () | 7326-7348 | Automated print via barcode scan (legacy) | LOW |
| 57 | sbt_SelVsClick | published | (Sender: TObject) | 7349-7418 | Select vital signs items for display | MED |
| 58 | sbt_TemplSelClick | published | (Sender: TObject) | 7419-7442 | Select template for monitoring items | LOW |
| 59 | sbt_TemplInsClick | published | (Sender: TObject) | 7443-7468 | Insert template monitoring items | LOW |
| 60 | bbt_SetInsertClick | published | (Sender: TObject) | 7469-7570 | Insert monitoring item set — adds items to grid from template | MED |
| 61 | bbt_SetExitClick | published | (Sender: TObject) | 7571-7590 | Exit set insertion mode | LOW |
| 62 | Popup_ActPopup | published | (Sender: TObject) | 7591-7713 | Popup menu for grid actions — shows context menu with insert/delete options | MED |
| 63 | mi_InsBsActClick | published | (Sender: TObject) | 7714-7753 | Menu item: Insert blood sugar action into grid | LOW |
| 64 | asg_IcuMonDrawCell | published | (Sender: TObject; ACol, ARow: Integer; ARect: TRect; AState: TGridDrawState) | 7754-7800 | Custom grid cell drawing — icons, colors, borders | MED |
| 65 | bbt_ActExitClick | published | (Sender: TObject) | 7801-7812 | Exit action mode | LOW |
| 66 | bbt_InsActingClick | published | (Sender: TObject) | 7813-7859 | Insert acting item into grid | MED |
| 67 | mi_DelActClick | published | (Sender: TObject) | 7860-7898 | Menu item: Delete action from grid | LOW |
| 68 | sbt_SelRespClick | published | (Sender: TObject) | 7899-7968 | Select respiratory items for display | MED |
| 69 | mi_InsCvpActClick | published | (Sender: TObject) | 7969-8007 | Menu item: Insert CVP action into grid | LOW |
| 70 | mi_InsVsActClick | published | (Sender: TObject) | 8008-8043 | Menu item: Insert vital signs action into grid | LOW |
| 71 | asg_IcuMonGetEditMask | published | (Sender: TObject; ACol, ARow: Integer; var Value: String) | 8044-8080 | Grid edit mask callback — sets input masks per cell type | LOW |
| 72 | sbt_SelBstClick | published | (Sender: TObject) | 8081-8136 | Select blood sugar test items for display | MED |
| 73 | sbt_SelO2Click | published | (Sender: TObject) | 8137-8216 | Select O2/respiratory items for display | MED |
| 74 | SetFormInfo | private | () | 8217-8877 | Master form configuration — sets up all panels, grids, buttons, labels based on ICU/NICU/SU mode and user permissions | HIGH |
| 75 | GetPatList | private | (Sender: TObject) | 8878-9140 | Retrieves patient list — HmdPatinf.Create, ListPatbat, populates patient list grid | HIGH |
| 76 | ugd_PatListDrawCell | published | (Sender: TObject; ACol, ARow: Integer; ARect: TRect; AState: TGridDrawState) | 9141-9156 | Patient list grid custom drawing | LOW |
| 77 | ugd_PatListMouseMove | published | (Sender: TObject; Shift: TShiftState; X, Y: Integer) | 9157-9183 | Patient list grid mouse move — tooltip | LOW |
| 78 | SelectPatInfo | private | (in_Flag: String) | 9184-9392 | Selects patient from list, loads all patient data, refreshes monitoring grid | HIGH |
| 79 | ugd_PatListClick | published | (Sender: TObject) | 9393-9476 | Patient list grid click — calls SelectPatInfo | MED |
| 80 | combx_WardNmChange | published | (Sender: TObject) | 9477-9506 | Ward name combo change — refreshes patient list | LOW |
| 81 | cbx_DschClick | published | (Sender: TObject) | 9507-9525 | Discharge checkbox click — toggles discharged patient visibility | LOW |
| 82 | rbt_SortNameClick | published | (Sender: TObject) | 9526-9563 | Sort by name radio button — re-sorts patient list | LOW |
| 83 | SetNicuInfoAdded | private | (in_PatNo, in_AdmDate: String) | 9564-9715 | Sets NICU-specific additional info (gestational age, birth weight, etc.) | HIGH |
| 84 | CalcNowDay | private | (in_FstWks, in_FstDay, in_BornDate, in_RgtDate: String): String | 9716-9852 | Calculates current gestational day from birth date and registration date | HIGH |
# MDN110UM — Method Inventory (Part 3: Methods 85-125)

## Method Inventory (continued)

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 85 | Refresh_AutoScan | private | () | 9853-9898 | Auto-scan refresh for barcode-triggered data reload | MED |
| 86 | bbt_SelectClick | published | (Sender: TObject) | 9899-9949 | Opens patient selection dialog | MED |
| 87 | bbt_OkClick | published | (Sender: TObject) | 9950-9992 | OK button handler — confirms patient selection | MED |
| 88 | AutoScanPrint_New | private | () | 9993-10009 | Automated print via barcode scan (new version) | LOW |
| 89 | isYunYear | private | (in_Year: Integer): Boolean | 10010-10037 | Leap year check for date calculations | LOW |
| 90 | GetDiffDay | private | (in_BornDate, in_RgtDate: String): Integer | 10038-10196 | Calculates day difference between two dates (manual implementation) | HIGH |
| 91 | GetMainDiag | private | (in_PatNo, in_MedDept, in_AdmDate, in_Locate, in_Gubun, in_DiagType, in_ChaDr, in_PatCls: String) | 10197-10252 | Retrieves main diagnosis for patient | MED |
| 92 | chr_VS_SuAfterDraw | published | (Sender: TObject) | 10253-10317 | SU (Stroke Unit) chart after-draw event — custom annotations | MED |
| 93 | mi_InsBsDataClick | published | (Sender: TObject) | 10318-10356 | Menu item: Insert blood sugar data view | LOW |
| 94 | GetBsData | private | () | 10357-10466 | Retrieves blood sugar data — HmdIcuinf.Create, getIcuinflist, populates BS data grid | MED |
| 95 | bbt_BstCloseClick | published | (Sender: TObject) | 10467-10475 | Close blood sugar data panel | LOW |
| 96 | ugd_BsDataDblClick | published | (Sender: TObject) | 10476-10495 | Blood sugar data grid double-click — inserts value into monitoring grid | LOW |
| 97 | ugd_BsDataDrawCell | published | (Sender: TObject; ACol, ARow: Integer; ARect: TRect; AState: TGridDrawState) | 10496-10510 | Blood sugar data grid custom drawing | LOW |
| 98 | GetIoCheck | private | (in_Gubun: Integer) | 10511-10777 | Retrieves I/O (intake/output) check data — HmdIcuinf.Create, getIcuinflist, populates I/O grid | HIGH |
| 99 | mi_InsIoDataClick | published | (Sender: TObject) | 10778-10891 | Menu item: Insert I/O data view — calls GetIoCheck | MED |
| 100 | bbt_IoCloseClick | published | (Sender: TObject) | 10892-10900 | Close I/O data panel | LOW |
| 101 | ugd_IoDataDblClick | published | (Sender: TObject) | 10901-10918 | I/O data grid double-click — inserts value into monitoring grid | LOW |
| 102 | ugd_IoDataDrawCell | published | (Sender: TObject; ACol, ARow: Integer; ARect: TRect; AState: TGridDrawState) | 10919-10925 | I/O data grid custom drawing | LOW |
| 103 | bbt_NoteSearchClick | published | (Sender: TObject) | 10926-11006 | Note search button — searches notes by date range | MED |
| 104 | asd_NoteSearchGetAlignment | published | (Sender: TObject; ARow, ACol: Integer; var HAlign: TAlignment; var VAlign: TVAlignment) | 11007-11016 | Note search grid alignment callback | LOW |
| 105 | SetNoteSearch | private | () | 11017-11057 | Sets up note search grid headers and formatting | LOW |
| 106 | bbt_ShowNoteSearchClick | published | (Sender: TObject) | 11058-11072 | Shows note search results | LOW |
| 107 | bbt_NurseWriteClick | published | (Sender: TObject) | 11073-11095 | Opens nurse writing form | LOW |
| 108 | GetNbabyBorndate | private | () | 11096-11165 | Retrieves newborn baby birth date for NICU | MED |
| 109 | asg_IcuMonExit | published | (Sender: TObject) | 11166-11193 | Grid exit handler — validates and saves pending edits | LOW |
| 110 | asg_IcuMonCellChanging | published | (Sender: TObject; OldRow, OldCol, NewRow, NewCol: Integer) | 11194-11224 | Grid cell changing handler — validates cell transitions | LOW |
| 111 | asg_CrrtCanEditCell | published | (Sender: TObject; ARow, ACol: Integer; var CanEdit: Boolean) | 11225-11231 | Correction grid edit permission callback | LOW |
| 112 | asg_CrrtKeyPress | published | (Sender: TObject; var Key: Char) | 11232-11262 | Correction grid key press handler | LOW |
| 113 | asg_CrrtKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 11263-11272 | Correction grid key down handler | LOW |
| 114 | bbt_CrrtSaveClick | published | (Sender: TObject) | 11273-11422 | Save correction data — validates and saves corrected monitoring values | HIGH |
| 115 | bbt_CrrtBeforClick | published | (Sender: TObject) | 11423-11487 | Previous correction record | MED |
| 116 | bbt_CrrtCloseClick | published | (Sender: TObject) | 11488-11492 | Close correction panel | LOW |
| 117 | bbt_CrrtClick | published | (Sender: TObject) | 11493-11506 | Open correction mode | LOW |
| 118 | bbt_CrrtClearClick | published | (Sender: TObject) | 11507-11526 | Clear correction data | LOW |
| 119 | bbt_CrrtAfterClick | published | (Sender: TObject) | 11527-11592 | Next correction record | MED |
| 120 | CrrtnMaxData | private | () | 11593-11662 | Gets max correction data for date range | MED |
| 121 | CrrtNrrecSave | private | () | 11663-11731 | Saves correction nursing record | MED |
| 122 | dtb_CrrtChange | published | (Sender: TObject) | 11732-11742 | Correction date change handler | LOW |
| 123 | CrrtCheck | private | (in_Patno, in_Orddate: String): String | 11743-11790 | Checks if correction exists for patient/date | LOW |
| 124 | sbt_PrinterClick | published | (Sender: TObject) | 11791-11812 | Printer selection button | LOW |
| 125 | bt_printClick | published | (Sender: TObject) | 11813-11893 | Alternative print handler | MED |

VALIDATION: Source has 125 implementations, inventory has 125 rows. Delta = 0%.

## Event Chain Map

```
FormCreate → FormShow:
  → SetPatInfo → CheckFormSet → SetFormInfo (master config)
  → GetPatList → SelectPatInfo → SetPatInfo
  → GetIcuInfo (load ICU data)
  → GetAllItems → SetCodeList + GetCodeList + SetTimeList + GetTimeList
  → SelectMonItem → Drawchart → InitChart
  → SetLoadingBar

[Patient list interaction]:
  ugd_PatListClick → SelectPatInfo → SetPatInfo → GetIcuInfo → GetAllItems → SelectMonItem → Drawchart

[Monitoring grid interaction]:
  asg_IcuMonClickCell → popup editors / SelNote / code selection
  asg_IcuMonKeyPress → input validation
  asg_IcuMonEditingDone → mark modified
  bbt_MoniSaveClick → GetSaveList (per cell) → SetSaveList → HmdIcuinf.setIcuinflist

[Date navigation]:
  bbt_PrevDateClick / bbt_NextDateClick / dtp_RgtDateCloseUp → Refresh → GetAllItems + SelectMonItem + Drawchart + CheckAllNote

[Sub-form launches]:
  bbt_AssClick → MDN110FU (ICU) or MDN110FW (NICU) nursing assessment
  bbt_QualityClick → MDN110FV (ICU) or MDN110FX (NICU) quality check

[Print]:
  bbt_PrintClick → MDN110FM_P01 or MDN110FM_P02 report

[EMR integration]:
  sbt_NrrecClick → builds nursing record → TpSvc

[Correction mode]:
  bbt_CrrtClick → bbt_CrrtSaveClick → CrrtNrrecSave
  bbt_CrrtBeforClick / bbt_CrrtAfterClick → navigate corrections

[Data panels]:
  mi_InsBsDataClick → GetBsData (blood sugar)
  mi_InsIoDataClick → GetIoCheck (intake/output)
  bbt_NoteSearchClick → SetNoteSearch (notes)
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FM | TMDN110FM | FormCreate | Sub-forms (FU, FV, FW, FX, FO), print forms (P01, P02) | FormDestroy (set to Nil) |
| FsPatNo | String | SetPatInfo | GetIcuInfo, GetAllItems, SetSaveList, bbt_PrintClick, sbt_NrrecClick | SetPatInfo, SelectPatInfo |
| FsAdmDate | String | SetPatInfo | GetIcuInfo, GetAllItems, SetSaveList | SetPatInfo, SelectPatInfo |
| FsWardNo | String | SetPatInfo | GetPatList, CheckFormSet | SetPatInfo |
| FsLocate | String | SetPatInfo | GetIcuInfo, SetFormInfo | SetPatInfo |
| FiFormType | Integer | CheckFormSet | SetFormInfo, bbt_AssClick, bbt_QualityClick (0=ICU, 1=NICU, 2=SU) | CheckFormSet |

## Middleware Contract Summary

| Class | Method | Input Params | Output Shape | Error Convention |
|-------|--------|-------------|--------------|-----------------|
| HmdIcuinf | getIcuinflist | sFlag1, sType1-sType4, G_LOCATE | ICU info/monitoring field arrays | Returns -1 on error, 0 on no data |
| HmdIcuinf | setIcuinflist | sFlag1, sType1-sType5, TList of VOs | Integer result code | Returns -1 on error |
| HmdIcuinf | delIcuinflist | sFlag1, sType1-sType5 | Integer result code | Returns -1 on error |
| HmdPatinf | ListPatbat | Cond, PatNo, PatName | Patient info arrays | Returns -1 on error, 0 on no data |
| TpSvc | (EMR integration) | Nursing record string | - | Via SComFunc |

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| AdvGrid | TAdvStringGrid | Cells[], RowCount, ColCount, GetAlignment, GetCellColor, DrawCell, GetEditorType, GetEditMask, ClickCell, EditingDone, KeyPress, SelectCell, MouseMove, Exit, CellChanging | Main monitoring data grid |
| UltraGrid | TUltraGrid | Cells[], RowCount, Click, DblClick, DrawCell, MouseMove | Patient list grid, BS data grid, I/O data grid |
| TeeChart | TChart, TSeries | AddXY, Clear, AfterDraw, MouseMove | Vital signs charting |
| QuickReport | TQuickRep, TQRLabel | Preview, Print, Caption | Print reports |
| TClientDataSet | TClientDataSet | FieldDefs, CreateDataSet, Append, Post | Local data storage for chart data |

## Complexity Summary

This is the most complex unit in the application. Key complexity drivers:
- SetSaveList (742 lines): Handles saving all monitoring data types with extensive validation
- SetFormInfo (661 lines): Master form configuration for ICU/NICU/SU modes
- SetCodeList (450 lines): Monitoring item code mapping
- GetCodeList (382 lines): Data retrieval and grid population
- bbt_PrintClick (323 lines): Report generation
- GetIcuInfo (315 lines): Multi-flag ICU data retrieval
- Drawchart (308 lines): Chart data population
- SetTimeList (274 lines): Time column setup
- GetIoCheck (267 lines): I/O data retrieval
- GetPatList (263 lines): Patient list retrieval
