# MDN110UP — Method Inventory

## Unit Purpose

Order-to-monitoring grid mapping form for ICU, allowing users to map medical orders to monitoring grid items with day list navigation and copy operations.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 173-192 | Action := caFree, cleanup | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 193-197 | MDN110FP := Nil | LOW |
| 3 | bbt_CloseClick | published | (Sender: TObject) | 198-203 | Close | LOW |
| 4 | ugd_MonitorDrawCell | published | (Sender: TObject; ACol, ARow: Integer; Rect: TRect; State: TGridDrawState) | 204-211 | Canvas drawing | LOW |
| 5 | pc_MonitorChange | published | (Sender: TObject) | 212-306 | GetDayList, GetMonitorDayList, GetMappingDayList, grid setup | HIGH |
| 6 | FormShow | published | (Sender: TObject) | 307-369 | pc_MonitorChange, label setup, date init | HIGH |
| 7 | GetDayList | private | () | 370-452 | HmdIcutot.Create, HmdIcutot.GetMonitorDayList, ugd_DayList population | HIGH |
| 8 | rbt_MoniClick | published | (Sender: TObject) | 453-544 | HmdIcutot.Create, ugd_Monitor population | HIGH |
| 9 | ugd_MonitorMouseDown | published | (Sender: TObject; Button: TMouseButton; Shift: TShiftState; X, Y: Integer) | 545-665 | SelectCell, checkbox toggle, HmdIcutot.InsertDayMonitorList | HIGH |
| 10 | SelectCell | private | (Sender: TObject; iCol, iRow: Integer; IsSelect: Boolean) | 666-702 | ugd_Monitor cell selection logic | HIGH |
| 11 | cbx_AllClick | published | (Sender: TObject) | 703-734 | Bulk select/deselect all monitoring items | HIGH |
| 12 | ugd_MonitorMouseUp | published | (Sender: TObject; Button: TMouseButton; Shift: TShiftState; X, Y: Integer) | 735-753 | Post-click processing | LOW |
| 13 | rbt_MedClick | published | (Sender: TObject) | 754-764 | Filter toggle | LOW |
| 14 | rbt_IntakeClick | published | (Sender: TObject) | 765-904 | HmdIcutot.Create, intake data load, ugd_Monitor population | HIGH |
| 15 | sbt_MonitorCopyClick | published | (Sender: TObject) | 905-1057 | HmdIcutot.Create, copy monitoring data between dates | HIGH |
| 16 | GetFindProgress | private | (sType1: String; inum: Integer): Boolean | 1058-1101 | Progress check logic | HIGH |
| 17 | sbt_MonitorCopyAllClick | published | (Sender: TObject) | 1102-1112 | Bulk copy all | LOW |
| 18 | ugd_MonitoringDrawCell | published | (Sender: TObject; ACol, ARow: Integer; Rect: TRect; State: TGridDrawState) | 1113-1120 | Canvas drawing | LOW |
| 19 | ed_InputEnter | published | (Sender: TObject) | 1121-1130 | Input field focus | LOW |
| 20 | ed_InputExit | published | (Sender: TObject) | 1131-1154 | Input field validation | LOW |
| 21 | ed_InputKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1155-1163 | Key handling | LOW |
| 22 | ed_InputKeyPress | published | (Sender: TObject; var Key: Char) | 1164-1202 | Input validation, save on Enter | HIGH |
| 23 | ugd_MonitorDblClick | published | (Sender: TObject) | 1203-1208 | Double-click handler | LOW |
| 24 | bbt_FirstDateClick | published | (Sender: TObject) | 1209-1264 | Navigate to first date, reload data | HIGH |
| 25 | GetMonitorDayInfo | private | (sTemp: String) | 1265-1399 | HmdIcutot.Create, interface data retrieval, ugd_Monitor population | HIGH |
| 26 | GetMonitorDayList | private | () | 1400-1516 | HmdIcutot.Create, HmdOrderv.Create, monitoring day list load | HIGH |
| 27 | bbt_AddClick | published | (Sender: TObject) | 1517-1791 | HmdIcutot.Create, add monitoring items, complex validation | HIGH |
| 28 | bbt_DeleteClick | published | (Sender: TObject) | 1792-1969 | HmdIcutot.Create, delete monitoring items, confirmation dialog | HIGH |
| 29 | dtp_RgtDateChange | published | (Sender: TObject) | 1970-1982 | Date change, reload | LOW |
| 30 | FormKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1983-1990 | Escape key handling | LOW |
| 31 | bbt_PrevDateClick | published | (Sender: TObject) | 1991-2006 | Previous date navigation | LOW |
| 32 | bbt_NextDateClick | published | (Sender: TObject) | 2007-2022 | Next date navigation | LOW |
| 33 | dtp_OrdDateCloseUp | published | (Sender: TObject) | 2023-2028 | Order date picker close | LOW |
| 34 | dtp_OrdDateChange | published | (Sender: TObject) | 2029-2041 | Order date change | LOW |
| 35 | ugd_MonitoringDblClick | published | (Sender: TObject) | 2042-2066 | Monitoring grid double-click | LOW |
| 36 | ugd_MonitoringKeyPress | published | (Sender: TObject; var Key: Char) | 2067-2106 | Monitoring grid key handling | HIGH |
| 37 | GetMappingDayList | private | () | 2107-2197 | Mapping day list retrieval, grid population | HIGH |
| 38 | dtp_AppDateChange | published | (Sender: TObject) | 2198-2203 | Application date change | LOW |
| 39 | dtp_AppDateCloseUp | published | (Sender: TObject) | 2204-2209 | Application date picker close | LOW |
| 40 | sbt_PrevDate2Click | published | (Sender: TObject) | 2210-2223 | Previous date navigation (secondary) | LOW |
| 41 | sbt_NextDate2Click | published | (Sender: TObject) | 2224-2238 | Next date navigation (secondary) | LOW |
| 42 | GridClear | private | (in_Grid: TUltraGrid) | 2239-2262 | Clear grid with title row | LOW |
| 43 | ugd_MonitoringMouseMove | published | (Sender: TObject; Shift: TShiftState; X, Y: Integer) | 2263-2303 | Mouse move tooltip | HIGH |
| 44 | ugd_MonitorMouseMove | published | (Sender: TObject; Shift: TShiftState; X, Y: Integer) | 2304-2353 | Mouse move tooltip | HIGH |

VALIDATION: Source has 44 implementations, inventory has 44 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (line 307) → pc_MonitorChange → GetDayList → GetMonitorDayList
  → [User clicks day in ugd_DayList] → rbt_MoniClick (line 453) → ugd_Monitor reload
  → [User clicks cell in ugd_Monitor] → ugd_MonitorMouseDown (line 545) → SelectCell → InsertDayMonitorList
  → [User clicks Add] → bbt_AddClick (line 1517) → HmdIcutot add items
  → [User clicks Delete] → bbt_DeleteClick (line 1792) → HmdIcutot delete items
  → [User clicks Copy] → sbt_MonitorCopyClick (line 905) → copy monitoring data
  → [User clicks Close] → bbt_CloseClick (line 198) → Close
FormClose (line 173) → cleanup, Action := caFree
FormDestroy (line 193) → MDN110FP := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FP | TMDN110FP | FormCreate (implicit) | External callers | FormDestroy (set to Nil) |
| P_PatNo | String | External caller via property | GetDayList, GetMonitorDayList, bbt_AddClick, bbt_DeleteClick | prop_PatNo setter |
| P_AdmDate | String | External caller via property | GetDayList, GetMonitorDayList | prop_AdmDate setter |
| P_Settype | String | External caller via property | GetDayList, GetMonitorDayList | prop_Settype setter |
| g_PrevPageIdx | String | GetMappingDayList | Grid initialization | GetMappingDayList |

## Middleware Contract Summary

| Class | Method | Input Params (name: type) | Output Shape | Error Convention |
|-------|--------|--------------------------|--------------|-----------------| 
| HmdIcutot | GetMonitorDayList | sType1: String (PatNo), sType2: String (AdmDate), sType3: String (ActDate), sType4: String (SetCode), sType5: String (SetType) | Arrays: sItemCode[], sItemName[], sItemValue[], sActTime[] | Returns -1 on error, 0 on no data |
| HmdIcutot | InsertDayMonitorList | sType1: String (flag), j: Integer (index) | Integer (row count) | Returns 0 on failure |
| HmdOrderv | (query) | Order parameters | Order data arrays | Returns -1 on error |

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| UltraGrid | TUltraGrid | Cells[], RowCount, ColCount, Row, Col, DefaultRowHeight | Three grids: ugd_DayList, ugd_Monitor, ugd_Monitoring |

## Repetitive Handler Analysis

N/A — no repetitive handler groups (no >10 similar methods).
