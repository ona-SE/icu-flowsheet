# MDN110UP_수정 — ICU Order-Monitoring Grid Mapping Form (Modified Version)

## Category

- **Form/UI**: Paired MDN110UP_수정.dfm exists (1006 lines). Modified version of MDN110UP with UltraGrids for day list, monitor data, and monitoring data.
- **Database**: Tuxedo middleware via HmdIcrect (ICU record), HmdOrderv (order verification).
- **Third-party**: UltraGrid (TUltraGrid).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FP (inherits TForm)

Note: This unit declares the same class name TMDN110FP as MDN110UP.pas. ASSUMPTION: Only one of these units is compiled into the final package at a time; the 수정 (modified) version is an alternate implementation.

**Published properties:**
- `prop_Mode: String` — write-only g_Mode (input mode)
- `prop_PatNo: String` — write-only X_PatNo
- `prop_PatName: String` — write-only X_PatName
- `prop_AdmDate: String` — write-only X_AdmDate
- `prop_SexAge: String` — write-only X_SexAge
- `prop_Settype: String` — write-only X_Settype

**Public fields:**
- `dtp_RgtDate_Date: TDateTimePicker`
- `g_Mode: String`
- `X_PatNo, X_PatName, X_AdmDate, X_SexAge, X_Settype: String`

**Private methods:**
- `procedure SelectCell(Sender: TObject; iCol, iRow: Integer; IsSelect: Boolean)`
- `function GetFindProgress(sType1: String; inum: Integer): Boolean`
- `procedure GetDayList` — retrieves day list
- `procedure GetMonitorDayInfo(sTemp: String)` — retrieves interface data
- `procedure GetMonitorDayList` — retrieves monitoring data

**Event handlers (32 total):** FormClose, FormDestroy, FormShow, and 29 grid/button handlers.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, StdCtrls, ExtCtrls, Buttons, ComCtrls, Grids, UltraGrid, Variants

**Implementation uses:** CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet or record types declared.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdIcrect.Create** — ICU record middleware object
   - Used at lines 297, 377, 953, 1086, 1297, 1430
   - Methods called: GetMonitorDayList, InsertDayMonitorList (inferred from usage pattern)
   - Returns: Integer (row count). Output arrays: item codes, names, values

2. **HmdOrderv.Create** — Order verification middleware object
   - Used at line 1127
   - Methods called: order data retrieval

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UP_수정.dfm (1006 lines):
- **TUltraGrid**: ugd_DayList, ugd_Monitor, ugd_Monitoring
- **TDateTimePicker**: dtp_RgtDate_Date
- **TBitBtn**: bbt_Close, bbt_Save
- **TPanel**: layout panels
- **TLabel**: field labels

## Behavioral .dfm Properties

DFM file: 1006 lines. Minimum threshold: 3 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| ugd_DayList | FixedRows | 1 | One header row |
| ugd_Monitor | FixedRows | 1 | One header row |
| ugd_Monitoring | FixedRows | 1 | One header row |

## With-Block Resolutions

ORIGINAL (line 323): `with mdIcrect, ugd_DayList do`
UNRESOLVABLE: Multi-object with — mdIcrect is HmdIcrect and ugd_DayList is TUltraGrid. Resolution by member name: Cells → ugd_DayList.Cells; sActDate, sItemCode → mdIcrect.sActDate. No ambiguous members detected.

ORIGINAL (line 408): `with mdIcrect, ugd_Monitor do`
UNRESOLVABLE: Multi-object with — mdIcrect is HmdIcrect and ugd_Monitor is TUltraGrid. Resolution by member name as above.

ORIGINAL (line 460): `with ugd_Monitor do`
RESOLVED: ugd_Monitor is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_Monitor.RowCount

ORIGINAL (line 572): `with (Sender as TUltraGrid) do`
RESOLVED: Sender cast to TUltraGrid. Members accessed: Cells[col,row], Row → (Sender as TUltraGrid).Cells[col,row]

ORIGINAL (line 776): `with ugd_Monitoring do`
RESOLVED: ugd_Monitoring is TUltraGrid. Members accessed: Cells[col,row] → ugd_Monitoring.Cells[col,row]

ORIGINAL (line 998): `with mdIcrect, ugd_Monitor do`
UNRESOLVABLE: Multi-object with — mdIcrect is HmdIcrect and ugd_Monitor is TUltraGrid. Resolution by member name as above.

ORIGINAL (line 1196): `with mdIcrect, ugd_Monitoring do`
UNRESOLVABLE: Multi-object with — mdIcrect is HmdIcrect and ugd_Monitoring is TUltraGrid. Resolution by member name as above.

ORIGINAL (line 1305): `with mdIcrect do`
RESOLVED: mdIcrect is HmdIcrect. Members accessed: field arrays → mdIcrect.sFieldName[index]

ORIGINAL (line 1384): `with ugd_Monitoring do`
RESOLVED: ugd_Monitoring is TUltraGrid. Members accessed: Cells[col,row] → ugd_Monitoring.Cells[col,row]

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FP | TMDN110FP | External callers | FormCreate (implicit), FormDestroy (set to Nil) |
| g_Mode | String | FormShow, data methods | External caller via property |
| X_PatNo | String | Middleware calls | External caller via property |
| X_AdmDate | String | Middleware calls | External caller via property |
| X_Settype | String | Middleware calls | External caller via property |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdIcrect and HmdOrderv middleware objects.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. This is a modified version of MDN110UP. The Korean suffix 수정 means "modified/corrected". Uses HmdIcrect instead of HmdIcutot, suggesting a different middleware service.
2. Only one of MDN110UP.pas or MDN110UP_수정.pas is compiled at a time since both declare TMDN110FP.
3. The g_Mode field controls the form's behavior mode (view vs edit).
