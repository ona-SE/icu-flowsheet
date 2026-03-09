# MDN110UM1 — ICU Patient Monitoring Summary View

## Category

- **Form/UI**: Paired MDN110UM1.dfm exists (15659 lines). Multi-tab patient monitoring summary with scroll boxes, grids, and chart.
- **Database**: Tuxedo middleware via HmdPatInf (patient ward info), HmdPdiagt (diagnosis).
- **Third-party**: UltraGrid (TUltraGrid), Bianco_Panel, VCL TeeChart (TChart, TLineSeries).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FM1 (inherits TForm)

**Public fields:** None declared.

**Private methods:**
- `procedure PatList` — loads patient list
- `procedure PatSelect` — handles patient selection

**Event handlers (40 total):**
- FormClose, FormDestroy, FormShow, bbt_CloseClick
- pc_ICUChange — tab change handler
- sbt_Min1Click, sbt_Max1Click, sbt_Min2Click, sbt_Max2Click — scroll min/max
- sbt_PtInfoClick — patient info button
- combx_WardNmChange — ward selection change
- ugd_ListDrawCell, ugd_ListClick — patient list grid events
- sbt_Exit2Click, sbt_Close1Click — exit/close buttons
- ugd_List1SelectCell, ugd_List1DrawCell — secondary grid events
- sbt_Item1Click through sbt_Item16Click — 16 item selection buttons
- sbt_ActClick — action button
- rbt_Gubun1Click, rbt_Gubun2Click, rbt_Gubun3Click — category radio buttons
- pn_PatinfoMouseDown, bpn_PatListMouseDown — panel mouse events

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ComCtrls, StdCtrls, ExtCtrls, Grids, UltraGrid, Buttons, Bianco_Panel, Mask, Variants, VclTee.TeEngine, VclTee.Series, VclTee.TeeProcs, VclTee.Chart

**Implementation uses:** CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet, record types, or in-memory buffers declared. Data is displayed directly in UltraGrid cells from middleware output arrays.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdPatInf.StayWard2(Type1: String, Type2: String, Type3: String, G_LOCATE: String): Integer**
   - Parameters: Type1=ward code, Type2=filter, Type3=sort option, G_LOCATE=location
   - Returns: Integer (row count). Output arrays: sRoomNo[], sRoomNo1[], sPatno[], sPatName[], sBckStat[], sAdmDate[], sSexAge[]
   - Error: returns -1 on system error, 0 on no data
   - Called at line 1384

2. **HmdPatInf (second call at line 1575)** — patient info retrieval for selected patient

3. **HmdPdiagt (diagnosis at line 1639)** — diagnosis data retrieval for selected patient

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UM1.dfm (15659 lines):
- **TPageControl**: pc_ICU (2 tabs: ts_ICU1, ts_ICU2)
- **TScrollBox**: sbox_Tab1, sbox_Tab2 — scrollable content areas
- **TUltraGrid**: ugd_List (patient list), ugd_List1 (detail list), ugd_OrdDate (order dates)
- **TPanel**: ~90+ panels for layout (Panel1-Panel91)
- **TEdit**: ed_PatNo, ed_PatName, ed_SexAge, ed_MedDept, and many data display edits
- **TLabel**: ~50+ labels for field descriptions
- **TBevel**: ~80+ bevels for visual separation
- **TSpeedButton**: sbt_Min1, sbt_Max1, sbt_Min2, sbt_Max2, sbt_PtInfo, sbt_Exit2, sbt_Close1, sbt_Act, sbt_Item1-sbt_Item16
- **TComboBox**: combx_WardNm, combx_WardCd
- **TCheckBox**: cbx_NowPos, cbx_Dsch, cbx_Cancel
- **TRadioButton**: rbt_Gubun1, rbt_Gubun2, rbt_Gubun3, rbt_SortDept, rbt_SortName, rbt_SortRoom

WARNING: BUSINESS LOGIC IN HANDLER: PatList (private, called from FormShow) — loads patient list via middleware
WARNING: BUSINESS LOGIC IN HANDLER: PatSelect (private) — selects patient and loads detail data

## Behavioral .dfm Properties

DFM file: 15659 lines. Minimum threshold: 32 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| MDN110FM1 | BorderStyle | bsSingle | Non-resizable form |
| pc_ICU | ActivePage | ts_ICU1 | Tab 1 shown by default |
| sbox_Tab1 | AutoScroll | True | Enables scrolling for overflow content |
| sbox_Tab2 | AutoScroll | True | Enables scrolling for overflow content |
| ugd_List | DefaultRowHeight | 18 | Compact row display |
| ugd_List | FixedCols | 0 | No fixed columns |
| ugd_List | FixedRows | 1 | One header row |
| combx_WardCd | Visible | False | Hidden ward code combo |
| cbx_NowPos | Checked | True | Default: show current position |
| rbt_SortDept | Visible | False | Sort-by-dept hidden |
| rbt_SortRoom | Checked | True | Default sort by room |
| ed_PatNo | ReadOnly | True | Patient number not editable |
| ed_PatName | ReadOnly | True | Patient name not editable |
| ed_SexAge | ReadOnly | True | Sex/age not editable |
| ed_MedDept | ReadOnly | True | Department not editable |
| sbt_Item1 | Caption | 'V/S' | Vital signs button |
| sbt_Item2 | Caption | 'Neuro' | Neurological button |
| sbt_Item3 | Caption | 'Hemo' | Hemodynamic button |
| sbt_Item4 | Caption | 'Resp' | Respiratory button |
| sbt_Item5 | Caption | 'I/O' | Input/Output button |
| sbt_Item6 | Caption | 'Lab' | Laboratory button |
| sbt_Item7 | Caption | 'Drug' | Drug button |
| sbt_Item8 | Caption | 'Vent' | Ventilator button |
| sbt_Item9 | Caption | 'Skin' | Skin assessment button |
| sbt_Item10 | Caption | 'Pain' | Pain assessment button |
| sbt_Item11 | Caption | 'Line' | Line/tube button |
| sbt_Item12 | Caption | 'Diet' | Diet button |
| sbt_Item13 | Caption | 'Act' | Activity button |
| sbt_Item14 | Caption | 'Edu' | Education button |
| sbt_Item15 | Caption | 'Etc' | Miscellaneous button |
| sbt_Item16 | Caption | 'Order' | Order button |
| bpn_PatList | Visible | True | Patient list panel visible |
| pn_Patinfo | Visible | True | Patient info panel visible |
| ugd_OrdDate | FixedRows | 1 | One header row for order dates |
| ugd_List1 | FixedRows | 1 | One header row for detail list |

## With-Block Resolutions

ORIGINAL (line 1739): `with ugd_List1 do`
RESOLVED: ugd_List1 is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_List1.RowCount, ugd_List1.Cells[col,row]

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FM1 | TMDN110FM1 | External callers | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdPatInf and HmdPdiagt middleware objects (lines 1382, 1565).
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. The 16 sbt_Item buttons (sbt_Item1 through sbt_Item16) correspond to ICU monitoring categories: V/S, Neuro, Hemo, Resp, I/O, Lab, Drug, Vent, Skin, Pain, Line, Diet, Act, Edu, Etc, Order.
2. G_LOCATE is a global variable from CComFunc or similar shared unit, representing the current hospital location.
