# MDN110UM3 — ICU Patient Selection / Doctor Selection Form

## Category

- **Form/UI**: Paired MDN110UM3.dfm exists (493 lines). Small patient/doctor selection form with grids, combo boxes, and radio buttons.
- **Database**: Tuxedo middleware via CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc (implementation uses). No direct Hmd* class instantiation found in this unit.
- **Third-party**: UltraGrid (TUltraGrid).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FM3 (inherits TForm)

**Public fields:** None declared.
**Private fields:** None declared.
**Event handlers (6 total):** sbt_PtInfoClick, sbt_ActClick, bbt_CloseClick, FormClose, FormDestroy, FormShow.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, StdCtrls, Buttons, ExtCtrls, Grids, UltraGrid, ComCtrls, Variants

**Implementation uses:** CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet, record types, or in-memory buffers declared in this unit.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

N/A -- no direct Hmd* middleware class instantiation found in this unit's source. ASSUMPTION: Data loading is done via shared utility functions from CComFunc or MComFunc.

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UM3.dfm (493 lines):
- **TUltraGrid**: ugd_List (patient/doctor list), ugd_OrdDate (order dates)
- **TComboBox**: combx_WardNm, combx_WardCd
- **TEdit**: ed_DocNm, ed_DocCd
- **TRadioButton**: rbt_Gubun1, rbt_Gubun2, rbt_Gubun3
- **TCheckBox**: cbx_NowPos
- **TSpeedButton**: sbt_Refresh, sbt_PtInfo, sbt_Act
- **TBitBtn**: bbt_DocSelect, bbt_Close
- **TStatusBar**: stb_Message

## Behavioral .dfm Properties

DFM file: 493 lines. Minimum threshold: 1 row.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| MDN110FM3 | BorderStyle | bsSingle | Non-resizable form |
| combx_WardCd | Visible | False | Hidden ward code combo |
| cbx_NowPos | Checked | True | Default: show current position |
| rbt_Gubun1 | Checked | True | Default category selection |
| ugd_List | FixedRows | 1 | One header row |
| ugd_OrdDate | FixedRows | 1 | One header row |

## With-Block Resolutions

N/A -- no `with` statements found (searched entire unit).

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FM3 | TMDN110FM3 | External callers | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. This is a small selection dialog used to pick a patient or doctor, likely opened from MDN110UM1 or MDN110UM.
