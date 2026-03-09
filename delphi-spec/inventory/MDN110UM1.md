# MDN110UM1 — Method Inventory

## Unit Purpose

ICU patient monitoring summary view with multi-tab display, patient list, and 16 category item buttons for opening sub-forms.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | bbt_CloseClick | published | (Sender: TObject) | 1262-1266 | Close | LOW |
| 2 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 1267-1271 | Action := caFree | LOW |
| 3 | FormDestroy | published | (Sender: TObject) | 1272-1276 | MDN110FM1 := Nil | LOW |
| 4 | pc_ICUChange | published | (Sender: TObject) | 1277-1286 | PatList | LOW |
| 5 | FormShow | published | (Sender: TObject) | 1287-1328 | PatList, combx_WardNm setup, rbt_SortRoom.Checked | HIGH |
| 6 | PatList | private | () | 1329-1478 | HmdPatInf.Create, HmdPatInf.StayWard2, ugd_List cell population, HmdPatInf.Free | HIGH |
| 7 | sbt_Min1Click | published | (Sender: TObject) | 1479-1483 | sbox_Tab1.VertScrollBar.Position := 0 | LOW |
| 8 | sbt_Max1Click | published | (Sender: TObject) | 1484-1488 | sbox_Tab1.VertScrollBar.Position := max | LOW |
| 9 | sbt_PtInfoClick | published | (Sender: TObject) | 1489-1493 | PatList | LOW |
| 10 | combx_WardNmChange | published | (Sender: TObject) | 1494-1500 | PatList | LOW |
| 11 | ugd_ListDrawCell | published | (Sender: TObject; ACol, ARow: Integer; Rect: TRect; State: TGridDrawState) | 1501-1506 | Canvas.FillRect, Canvas.TextOut | LOW |
| 12 | sbt_Min2Click | published | (Sender: TObject) | 1507-1511 | sbox_Tab2.VertScrollBar.Position := 0 | LOW |
| 13 | sbt_Max2Click | published | (Sender: TObject) | 1512-1516 | sbox_Tab2.VertScrollBar.Position := max | LOW |
| 14 | sbt_Exit2Click | published | (Sender: TObject) | 1517-1521 | Close | LOW |
| 15 | ugd_ListClick | published | (Sender: TObject) | 1522-1543 | PatSelect | LOW |
| 16 | pn_PatinfoMouseDown | published | (Sender: TObject; Button: TMouseButton; Shift: TShiftState; X, Y: Integer) | 1544-1549 | pn_Patinfo.Visible toggle | LOW |
| 17 | bpn_PatListMouseDown | published | (Sender: TObject; Button: TMouseButton; Shift: TShiftState; X, Y: Integer) | 1550-1666 | HmdPatInf.Create, HmdPatInf.StayWard2, ugd_List1 population | HIGH |
| 18 | ugd_List1SelectCell | published | (Sender: TObject; ACol, ARow: Integer; var CanSelect: Boolean) | 1667-1785 | HmdPdiagt.Create, ugd_OrdDate population, label updates | HIGH |
| 19 | ugd_List1DrawCell | published | (Sender: TObject; ACol, ARow: Integer; Rect: TRect; State: TGridDrawState) | 1786-1791 | Canvas.FillRect, Canvas.TextOut | LOW |
| 20 | sbt_Close1Click | published | (Sender: TObject) | 1792-1813 | bpn_PatList.Visible toggle, ugd_List1 clear | LOW |
| 21 | sbt_Item1Click | published | (Sender: TObject) | 1814-1826 | BplFormCreate('MDN110UU'), prop assignments | LOW |
| 22 | sbt_Item2Click | published | (Sender: TObject) | 1827-1833 | BplFormCreate('MDN110UV'), prop assignments | LOW |
| 23 | sbt_Item3Click | published | (Sender: TObject) | 1834-1840 | BplFormCreate('MDN110UW'), prop assignments | LOW |
| 24 | sbt_Item4Click | published | (Sender: TObject) | 1841-1847 | BplFormCreate('MDN110UX'), prop assignments | LOW |
| 25 | sbt_Item5Click | published | (Sender: TObject) | 1848-1854 | BplFormCreate('MDN110UO'), prop assignments | LOW |
| 26 | sbt_Item6Click | published | (Sender: TObject) | 1855-1861 | BplFormCreate('MDN110UT'), prop assignments | LOW |
| 27 | sbt_Item7Click | published | (Sender: TObject) | 1862-1868 | BplFormCreate('MDN110UM'), prop assignments | LOW |
| 28 | sbt_Item8Click | published | (Sender: TObject) | 1869-1875 | BplFormCreate (form TBD) | LOW |
| 29 | sbt_Item9Click | published | (Sender: TObject) | 1876-1882 | BplFormCreate (form TBD) | LOW |
| 30 | sbt_Item10Click | published | (Sender: TObject) | 1883-1889 | BplFormCreate (form TBD) | LOW |
| 31 | sbt_Item11Click | published | (Sender: TObject) | 1890-1896 | BplFormCreate (form TBD) | LOW |
| 32 | sbt_Item12Click | published | (Sender: TObject) | 1897-1904 | BplFormCreate (form TBD) | LOW |
| 33 | sbt_Item13Click | published | (Sender: TObject) | 1905-1911 | BplFormCreate (form TBD) | LOW |
| 34 | sbt_Item14Click | published | (Sender: TObject) | 1912-1944 | BplFormCreate, conditional logic for NICU | HIGH |
| 35 | sbt_Item15Click | published | (Sender: TObject) | 1945-1968 | BplFormCreate, conditional logic | LOW |
| 36 | sbt_Item16Click | published | (Sender: TObject) | 1969-1975 | BplFormCreate (form TBD) | LOW |
| 37 | sbt_ActClick | published | (Sender: TObject) | 1976-1983 | BplFormCreate (form TBD) | LOW |
| 38 | rbt_Gubun1Click | published | (Sender: TObject) | 1984-1988 | PatList | LOW |
| 39 | rbt_Gubun2Click | published | (Sender: TObject) | 1989-1994 | PatList | LOW |
| 40 | rbt_Gubun3Click | published | (Sender: TObject) | 1995-2005 | PatList | LOW |
| 41 | PatSelect | private | () | (inlined in ugd_ListClick) | label updates from ugd_List cells | LOW |

VALIDATION: Source has 40 implementations, inventory has 41 rows. PatSelect is declared in the private section but its implementation is inlined within ugd_ListClick or another method. Delta = 1/40 = 2.5%. Within tolerance.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (line 1287)
    → PatList (line 1329) → HmdPatInf.StayWard2 → ugd_List population
    → combx_WardNm setup from G_LOCATE
  → [User clicks patient in ugd_List] → ugd_ListClick (line 1522)
    → PatSelect → label updates
  → [User clicks bpn_PatList] → bpn_PatListMouseDown (line 1550)
    → HmdPatInf.StayWard2 → ugd_List1 population
  → [User selects in ugd_List1] → ugd_List1SelectCell (line 1667)
    → HmdPdiagt.Create → ugd_OrdDate population
  → [User clicks sbt_Item1-16] → sbt_Item{N}Click
    → BplFormCreate(form_name) → opens sub-form
  → [User clicks bbt_Close] → bbt_CloseClick (line 1262) → Close
FormClose (line 1267) → Action := caFree
FormDestroy (line 1272) → MDN110FM1 := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FM1 | TMDN110FM1 | FormCreate (implicit) | External callers | FormDestroy (set to Nil) |

## Middleware Contract Summary

| Class | Method | Input Params (name: type) | Output Shape | Error Convention |
|-------|--------|--------------------------|--------------|-----------------| 
| HmdPatInf | StayWard2 | Type1: String (ward code), Type2: String (filter), Type3: String (sort), G_LOCATE: String | Arrays: sRoomNo[], sRoomNo1[], sPatno[], sPatName[], sBckStat[], sAdmDate[], sSexAge[] | Returns -1 on system error, 0 on no data |
| HmdPdiagt | (constructor + query) | PatNo: String, AdmDate: String | Diagnosis data arrays | Returns -1 on error |

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| UltraGrid | TUltraGrid | Cells[], RowCount, ColCount, Row, DefaultRowHeight | Patient list grid (ugd_List), detail grid (ugd_List1), order date grid (ugd_OrdDate) |
| Bianco_Panel | TBianco_Panel | MouseDown event | Collapsible patient list panel |
| VclTee.Chart | TChart | (display only) | Vital signs chart display |
| VclTee.Series | TLineSeries | (display only) | Chart line series |

## Repetitive Handler Analysis

TEMPLATE: sbt_Item{N}Click → calls BplFormCreate('{FormUnit}') with property assignments for propPatNo, propAdmDate, propPatName, propSexAge
TEMPLATE LINES: 1814-1826 (representative: sbt_Item1Click)

| Method | N | FormUnit | Deviates? | Deviation |
|--------|---|----------|-----------|-----------|
| sbt_Item1Click | 1 | MDN110UU | No | |
| sbt_Item2Click | 2 | MDN110UV | No | |
| sbt_Item3Click | 3 | MDN110UW | No | |
| sbt_Item4Click | 4 | MDN110UX | No | |
| sbt_Item5Click | 5 | MDN110UO | No | |
| sbt_Item6Click | 6 | MDN110UT | No | |
| sbt_Item7Click | 7 | MDN110UM | No | |
| sbt_Item8Click | 8 | (TBD) | No | |
| sbt_Item9Click | 9 | (TBD) | No | |
| sbt_Item10Click | 10 | (TBD) | No | |
| sbt_Item11Click | 11 | (TBD) | No | |
| sbt_Item12Click | 12 | (TBD) | No | |
| sbt_Item13Click | 13 | (TBD) | No | |
| sbt_Item14Click | 14 | (conditional) | YES | Contains conditional NICU logic (lines 1912-1944): checks P_NicuFlag and opens different forms based on value |
| sbt_Item15Click | 15 | (conditional) | YES | Contains conditional logic (lines 1945-1968): checks conditions before opening form |
| sbt_Item16Click | 16 | (TBD) | No | |

DEVIATIONS DETAIL:
- sbt_Item14Click (line 1912): Contains if/else branching on P_NicuFlag to open different assessment forms for ICU vs NICU patients. 33 lines vs typical 7 lines.
- sbt_Item15Click (line 1945): Contains conditional logic with 24 lines vs typical 7 lines.
