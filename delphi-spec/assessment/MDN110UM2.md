# MDN110UM2 — ICU Patient Monitoring Detail View (Tab 2)

## Category

- **Form/UI**: Paired MDN110UM2.dfm exists (6612 lines). Secondary detail form with page control, scroll boxes, checkboxes, radio buttons, and edit fields for patient monitoring data entry.
- **Database**: Tuxedo middleware via CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc (implementation uses). No direct Hmd* class instantiation found in this unit.
- **Third-party**: UltraGrid (TUltraGrid).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FM2 (inherits TForm)

**Public fields:** None declared.
**Private fields:** None declared.
**Event handlers (5 total):** FormClose, FormDestroy, FormShow, bbt_CloseClick, pc_ICUChange.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ExtCtrls, StdCtrls, Buttons, Grids, UltraGrid, Mask, ComCtrls, Variants

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

N/A -- no direct Hmd* middleware class instantiation found. This unit appears to be a display-only form that receives data from parent forms. ASSUMPTION: Data is populated by the calling form (MDN110UM1 or MDN110UM) setting component values directly.

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UM2.dfm (6612 lines):
- **TPageControl**: pc_ICU (2 tabs: ts_ICU1, ts_ICU2)
- **TScrollBox**: sbox_Tab1, sbox_Tab2
- **TPanel**: ~40+ panels for layout
- **TEdit**: ~25+ edit fields (Edit1-Edit22, etc.)
- **TCheckBox**: ~50+ checkboxes (CheckBox1-CheckBox47, etc.)
- **TRadioButton**: ~20+ radio buttons (RadioButton1-RadioButton20, etc.)
- **TBevel**: ~60+ bevels for visual separation
- **TLabel**: ~40+ labels

WARNING: BUSINESS LOGIC IN HANDLER: FormShow — populates form fields from parent data

## Behavioral .dfm Properties

DFM file: 6612 lines. Minimum threshold: 14 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| MDN110FM2 | BorderStyle | bsSingle | Non-resizable form |
| pc_ICU | ActivePage | ts_ICU1 | Tab 1 shown by default |
| sbox_Tab1 | AutoScroll | True | Scrollable content |
| sbox_Tab2 | AutoScroll | True | Scrollable content |
| Edit19 | ReadOnly | True | Read-only display field |
| Edit20 | ReadOnly | True | Read-only display field |
| Edit21 | ReadOnly | True | Read-only display field |
| Edit22 | ReadOnly | True | Read-only display field |
| CheckBox45 | Enabled | False | Disabled checkbox (display only) |
| CheckBox46 | Enabled | False | Disabled checkbox (display only) |
| CheckBox47 | Enabled | False | Disabled checkbox (display only) |
| RadioButton19 | Enabled | False | Disabled radio (display only) |
| RadioButton20 | Enabled | False | Disabled radio (display only) |
| Panel23 | Visible | True | Assessment section visible |
| Panel36 | Visible | True | Additional data section visible |

## With-Block Resolutions

N/A -- no `with` statements found (searched entire unit).

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FM2 | TMDN110FM2 | External callers | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. This form is a detail view opened from MDN110UM1. It displays assessment data in a read-only format with checkboxes and radio buttons showing patient status.
