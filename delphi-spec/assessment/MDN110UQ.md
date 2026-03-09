# MDN110UQ — ICU Monitoring Item Input Type/Value Editor

## Category

- **Form/UI**: Paired MDN110UQ.dfm exists (11973 lines). Item input type and value editor form with AdvStringGrid, image picker, and various input controls.
- **Database**: Tuxedo middleware via HmdIcrect (ICU record) — note: comment at line 75 states "MDCLASS1.pas의 HmdIcumot Class가 이상이 있습니다" (HmdIcumot class has issues), so HmdIcrect is used instead.
- **Third-party**: TMS AdvStringGrid (AdvGrid), TMS AdvEdit, TMS ImagePicker, TMS AsgLinks.
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FQ (inherits TForm)

**Public fields:**
- `P_PatNo: String` — patient number
- `P_AdmDate: String` — admission date
- `P_ActTime: String` — action time
- `P_ActDate: String` — action date
- `P_Settype: String` — set type

**Private methods:**
- `procedure GetInputType(Sender: TObject)` — retrieves input type configuration
- `procedure GetInputValue(Sender: TObject)` — retrieves input values

**Event handlers (17 total):** FormClose, FormDestroy, FormShow, and 14 component handlers.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ExtCtrls, StdCtrls, Mask, Buttons, Grids, BaseGrid, AdvGrid, ComCtrls, UltraGrid, AsgLinks, ImgList, ImagePicker, AdvEdit, Variants, AdvObj

**Implementation uses:** CComFunc, VarCom, TuxCom, MDCLASS1, MComFunc, HisUtil

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

1. **HmdIcrect.Create** — ICU record middleware
   - Used at lines 178, 253, 624
   - Retrieves input type definitions and input values for monitoring items
   - Returns: Integer (row count). Output arrays: item types, values, constraints

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UQ.dfm (11973 lines):
- **TAdvStringGrid**: asg_InputType (input type grid), asg_InputValue (input value grid)
- **TImageList**: ImageList1
- **TImagePicker**: image picker for visual selection
- **TAdvEdit**: advanced edit controls
- **TUltraGrid**: ugd_List
- **TBitBtn**: bbt_Close, bbt_Save
- **TPanel**: layout panels

WARNING: BUSINESS LOGIC IN HANDLER: FormClose (lines 80-100) — calls back to MDN110FM methods via FindFormMethod for refresh

## Behavioral .dfm Properties

DFM file: 11973 lines. Minimum threshold: 24 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| asg_InputType | FixedRows | 1 | One header row |
| asg_InputType | FixedCols | 0 | No fixed columns |
| asg_InputType | ColCount | 5 | Five columns for input type data |
| asg_InputType | DefaultRowHeight | 20 | Row height for input types |
| asg_InputValue | FixedRows | 1 | One header row |
| asg_InputValue | FixedCols | 0 | No fixed columns |
| asg_InputValue | ColCount | 3 | Three columns for input values |
| asg_InputValue | DefaultRowHeight | 20 | Row height for input values |
| ImageList1 | Width | 16 | Icon width |
| ImageList1 | Height | 16 | Icon height |
| ugd_List | FixedRows | 1 | One header row |
| ugd_List | DefaultRowHeight | 18 | Compact row display |
| bbt_Close | ModalResult | mrCancel | Closes form with cancel result |
| bbt_Save | ModalResult | mrOk | Closes form with OK result |
| asg_InputType | Options | [goEditing, goTabs] | Grid is editable with tab navigation |
| asg_InputValue | Options | [goEditing, goTabs] | Grid is editable with tab navigation |
| asg_InputType | ScrollBars | ssVertical | Vertical scroll only |
| asg_InputValue | ScrollBars | ssVertical | Vertical scroll only |
| asg_InputType | SelectionColor | clHighlight | Selection highlight color |
| asg_InputValue | SelectionColor | clHighlight | Selection highlight color |
| asg_InputType | ShowSelection | True | Shows selected cell |
| asg_InputValue | ShowSelection | True | Shows selected cell |
| asg_InputType | TabStop | True | Tab stop enabled |
| asg_InputValue | TabStop | True | Tab stop enabled |

## With-Block Resolutions

ORIGINAL (line 629): `with mdIcrect do`
RESOLVED: mdIcrect is HmdIcrect. Members accessed: field arrays for ICU record data → mdIcrect.sFieldName[index]

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FQ | TMDN110FQ | External callers | FormCreate (implicit), FormDestroy (set to Nil) |
| P_PatNo | String | Middleware calls | External caller |
| P_AdmDate | String | Middleware calls | External caller |
| P_ActTime | String | Middleware calls | External caller |
| P_ActDate | String | Middleware calls | External caller |
| P_Settype | String | Middleware calls | External caller |

## Custom Destructors

N/A -- no custom destructors. FormClose uses FindFormMethod to call back to MDN110FM for refresh, then sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdIcrect middleware objects.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.
- **Dynamic method resolution**: FormClose uses FindFormMethod('MDN110FM', 'GetMonitorDayInfo') and FindFormMethod('MDN110FM', 'GetMonitoring') to call methods on the parent form by name at runtime. This is a reflection-like pattern.

## Assumptions

1. FindFormMethod is a utility function (from MComFunc or CComFunc) that locates a method on a named form instance at runtime, enabling loose coupling between forms.
2. HmdIcumot was the intended middleware class but has issues (per comment at line 75), so HmdIcrect is used as a substitute.
