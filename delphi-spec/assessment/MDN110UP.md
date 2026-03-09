# MDN110UP — ICU Order-Monitoring Grid Mapping Form

## Category

- **Form/UI**: Paired MDN110UP.dfm exists (1364 lines). Order-to-monitoring grid mapping form with UltraGrids for day list, monitor data, and monitoring data.
- **Database**: Tuxedo middleware via HmdIcutot (monitoring totals), HmdOrderv (order verification).
- **Third-party**: UltraGrid (TUltraGrid).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FP (inherits TForm)

**Published properties:**
- `prop_PatNo: String` — write-only P_PatNo
- `prop_PatName: String` — write-only P_PatName
- `prop_AdmDate: String` — write-only P_AdmDate
- `prop_SexAge: String` — write-only P_SexAge
- `prop_Settype: String` — write-only P_SetType

**Public fields:**
- `dtp_FromDate: TDateTimePicker`

**Private fields:**
- `g_PrevPageIdx: String` — grid page index for initialization
- `P_PatNo, P_PatName, P_AdmDate, P_SexAge, P_Settype: String`

**Private methods:**
- `procedure SelectCell(Sender: TObject; iCol, iRow: Integer; IsSelect: Boolean)` — cell selection handler
- `function GetFindProgress(sType1: String; inum: Integer): Boolean` — checks progress status
- `procedure GetDayList` — retrieves day list from middleware
- `procedure GetMonitorDayInfo(sTemp: String)` — retrieves specific interface data
- `procedure GetMonitorDayList` — retrieves order-monitoring mapping data
- `procedure GetMappingDayList` — retrieves mapping day list
- `procedure GridClear(in_Grid: TUltraGrid)` — clears grid with title row

**Event handlers (44 total):** FormClose, FormDestroy, FormShow, bbt_CloseClick, and 40 grid/button event handlers.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, StdCtrls, ExtCtrls, Buttons, ComCtrls, Grids, UltraGrid, Variants

**Implementation uses:** CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet or record types declared. Data displayed directly in UltraGrid cells from middleware output arrays.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdIcutot.GetMonitorDayList(sType1: String, sType2: String, sType3: String, sType4: String, sType5: String): Integer**
   - Parameters: sType1=PatNo, sType2=AdmDate, sType3=ActDate, sType4=SetCode, sType5=SetType
   - Returns: Integer (row count). Output arrays: item codes, names, values, times
   - Error: returns -1 on system error, 0 on no data
   - Called at lines 387, 474, 829, 1285

2. **HmdIcutot.InsertDayMonitorList(sType1: String, j: Integer): Integer**
   - Parameters: sType1=flag, j=index
   - Returns: Integer (row count)
   - Called for saving mapping data

3. **HmdOrderv (order verification)** — retrieves order data for mapping
   - Called at line 1420

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UP.dfm (1364 lines):
- **TUltraGrid**: ugd_DayList (day list), ugd_Monitor (monitor data), ugd_Monitoring (monitoring data)
- **TDateTimePicker**: dtp_FromDate
- **TBitBtn**: bbt_Close, bbt_Save, bbt_Refresh
- **TSpeedButton**: various navigation buttons
- **TPanel**: layout panels
- **TLabel**: field labels

WARNING: BUSINESS LOGIC IN HANDLER: GetDayList — loads day list from middleware
WARNING: BUSINESS LOGIC IN HANDLER: GetMonitorDayList — loads and maps order-monitoring data
WARNING: BUSINESS LOGIC IN HANDLER: GetMappingDayList — loads mapping data

## Behavioral .dfm Properties

DFM file: 1364 lines. Minimum threshold: 3 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| ugd_DayList | FixedRows | 1 | One header row |
| ugd_Monitor | FixedRows | 1 | One header row |
| ugd_Monitoring | FixedRows | 1 | One header row |
| ugd_DayList | DefaultRowHeight | 18 | Compact row display |
| ugd_Monitor | DefaultRowHeight | 18 | Compact row display |

## With-Block Resolutions

ORIGINAL (line 415): `with iMons, ugd_DayList do`
UNRESOLVABLE: Multi-object with — iMons is HmdIcutot and ugd_DayList is TUltraGrid. Resolution by member name: Cells → ugd_DayList.Cells; sActDate, sItemCode → iMons.sActDate, iMons.sItemCode. No ambiguous members detected.

ORIGINAL (line 505): `with iMons, ugd_Monitor do`
UNRESOLVABLE: Multi-object with — iMons is HmdIcutot and ugd_Monitor is TUltraGrid. Resolution by member name as above.

ORIGINAL (line 557): `with ugd_Monitor do`
RESOLVED: ugd_Monitor is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_Monitor.RowCount, ugd_Monitor.Cells[col,row]

ORIGINAL (line 672): `with (Sender as TUltraGrid) do`
RESOLVED: Sender cast to TUltraGrid. Members accessed: Cells[col,row], Row → (Sender as TUltraGrid).Cells[col,row]

ORIGINAL (line 1335): `with iMons, ugd_Monitor do`
UNRESOLVABLE: Multi-object with — iMons is HmdIcutot and ugd_Monitor is TUltraGrid. Resolution by member name as above.

ORIGINAL (line 1643): `with iMons, ugd_Monitoring do`
UNRESOLVABLE: Multi-object with — iMons is HmdIcutot and ugd_Monitoring is TUltraGrid. Resolution by member name as above.

ORIGINAL (line 1880): `with ugd_Monitoring do`
RESOLVED: ugd_Monitoring is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_Monitoring.RowCount

ORIGINAL (line 2083): `with ugd_Monitoring do`
RESOLVED: ugd_Monitoring is TUltraGrid. Members accessed: Cells[col,row] → ugd_Monitoring.Cells[col,row]

ORIGINAL (line 2269): `with ugd_Monitoring do`
RESOLVED: ugd_Monitoring is TUltraGrid. Members accessed: Cells[col,row] → ugd_Monitoring.Cells[col,row]

ORIGINAL (line 2313): `with ugd_Monitor do`
RESOLVED: ugd_Monitor is TUltraGrid. Members accessed: Cells[col,row] → ugd_Monitor.Cells[col,row]

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FP | TMDN110FP | MDN110UM (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |
| P_PatNo | String | Middleware calls | External caller via property |
| P_PatName | String | Display | External caller via property |
| P_AdmDate | String | Middleware calls | External caller via property |
| P_SexAge | String | Display | External caller via property |
| P_Settype | String | Middleware calls | External caller via property |
| g_PrevPageIdx | String | Grid initialization | GetMappingDayList |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdIcutot and HmdOrderv middleware objects.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. This form is opened from MDN110UM to map orders to monitoring grid items.
2. The form name in the .dpk is MDN110FP, matching the published class name.
