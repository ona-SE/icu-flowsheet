# MDN110UT — ICU Nursing Record (Comment/IV Line) Viewer

## Category

- **Form/UI**: Paired MDN110UT.dfm exists (1019 lines). Nursing record viewer with AdvStringGrid for header and data display, animated GIF loading indicator, and AdvPanel.
- **Database**: Tuxedo middleware via HmdIccomt (ICU comment items), HmdIcivlt (ICU IV line items).
- **Third-party**: TMS AdvStringGrid (AdvGrid, BaseGrid), TMS AdvPanel, TMS AdvPicture, RxLib (RxGIF, RxAnimate, RxGIFCtrl — animated GIF support), Db/DBClient.
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FT (inherits TForm)

**Public fields:** None declared.

**Private fields:**
- `FDuties: TList` — duty period list
- `FRecItems: TList` — record item list (holds HmdIccomt objects)

**Private methods:**
- `procedure Initialize` — initializes form and data structures
- `procedure Search` — searches for nursing records
- `procedure LoadRecordItemList` — loads record item list from middleware
- `procedure LoadAllItemValues` — loads all item values for all duties

**Event handlers (17 total):** FormClose, FormDestroy, FormShow, FormCreate, and 13 grid/button handlers.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ComCtrls, StdCtrls, ExtCtrls, Buttons, Grids, BaseGrid, AdvGrid, RxGIF, AdvPicture, AdvPanel, Db, DBClient, Variants, RxAnimate, RxGIFCtrl, AdvObj

**Implementation uses:** VarCom, TuxCom, HisUtil, CComFunc, MComFunc, MDCLASS1

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

### FDuties: TList (private)
Holds duty period objects.
Populated by: Initialize procedure.
Consumed by: Search, LoadAllItemValues.

### FRecItems: TList (private)
Holds HmdIccomt objects representing record items.
Populated by: LoadRecordItemList from middleware.
Consumed by: LoadAllItemValues, grid display via `with HmdIccomt(FRecItems.Items[ARow]) do` at line 522.

### cds_ItemValues: TClientDataSet
Fields: item value fields for nursing record data.
Populated by: LoadAllItemValues from middleware.
Consumed by: grid display in asg_Data.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdIccomt.Create** — ICU comment items middleware
   - Used at lines 321, 375
   - Methods: retrieves comment/record item structure and data
   - Returns: Integer (row count). Output: item codes, names, values per duty
   - Called in LoadRecordItemList (line 321) and within loop for leaf items (line 375)

2. **HmdIcivlt.Create** — ICU IV line items middleware
   - Used at line 602
   - Methods: retrieves IV line item values
   - Returns: Integer (row count). Output: IV line data per time slot

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UT.dfm (1019 lines):
- **TAdvStringGrid**: asg_Header (header grid), asg_Data (data grid)
- **TAdvPanel**: apn_Loading (loading indicator panel)
- **TAdvPicture**: animated loading image
- **TClientDataSet**: cds_ItemValues
- **TBitBtn**: bbt_Close
- **TPanel**: layout panels
- **TLabel**: field labels

## Behavioral .dfm Properties

DFM file: 1019 lines. Minimum threshold: 3 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| asg_Header | FixedRows | 0 | No fixed rows in header grid |
| asg_Header | RowCount | 2 | Two rows for header display |
| asg_Data | FixedRows | 1 | One header row in data grid |
| asg_Data | DefaultRowHeight | 20 | Row height for data display |
| apn_Loading | Visible | False | Loading panel hidden by default |
| cds_ItemValues | Active | False | Dataset inactive until loaded |

## With-Block Resolutions

ORIGINAL (line 194): `with asg_Header do begin`
RESOLVED: asg_Header is TAdvStringGrid. Members accessed: Cells[col,row], ColCount, RowCount → asg_Header.Cells[col,row]

ORIGINAL (line 201): `with asg_Data do begin`
RESOLVED: asg_Data is TAdvStringGrid. Members accessed: Cells[col,row], ColCount, RowCount → asg_Data.Cells[col,row]

ORIGINAL (line 304): `with asg_Data do begin`
RESOLVED: asg_Data is TAdvStringGrid. Members accessed: Cells[col,row] → asg_Data.Cells[col,row]

ORIGINAL (line 353): `with asg_Data do begin`
RESOLVED: asg_Data is TAdvStringGrid. Members accessed: Cells[col,row] → asg_Data.Cells[col,row]

ORIGINAL (line 377): `with leafItem do begin`
RESOLVED: leafItem is HmdIccomt (local variable). Members accessed: sItemCode[0], sItemName[0] → leafItem.sItemCode[0]

ORIGINAL (line 522): `with HmdIccomt(FRecItems.Items[ARow]) do begin`
RESOLVED: Cast of FRecItems.Items[ARow] to HmdIccomt. Members accessed: sItemCode[0], sItemName[0] → HmdIccomt(FRecItems.Items[ARow]).sItemCode[0]

ORIGINAL (line 526): `with cds_ItemValues do begin`
RESOLVED: cds_ItemValues is TClientDataSet. Members accessed: First, Eof, FieldByName, Next → cds_ItemValues.First

ORIGINAL (line 539): `with asg_Data do begin`
RESOLVED: asg_Data is TAdvStringGrid. Members accessed: Cells[col,row] → asg_Data.Cells[col,row]

ORIGINAL (line 635): `with cds_ItemValues do begin`
RESOLVED: cds_ItemValues is TClientDataSet. Members accessed: Append, FieldByName, Post → cds_ItemValues.Append

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FT | TMDN110FT | External callers | FormCreate (implicit), FormDestroy (set to Nil) |
| FDuties | TList | Search, LoadAllItemValues | Initialize |
| FRecItems | TList | LoadAllItemValues, grid display | LoadRecordItemList |

## Custom Destructors

N/A -- no custom destructors with side effects. FormClose sets Action := caFree. ASSUMPTION: FDuties and FRecItems TList objects and their contained items are freed in FormClose or Initialize.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdIccomt and HmdIcivlt middleware objects.
- **TList with element storage**: FRecItems holds HmdIccomt pointers. Potential memory leak if elements are not individually freed before TList.Free.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. FDuties contains duty period definitions (Day/Evening/Night) used to structure the grid columns.
2. FRecItems holds the hierarchical record item structure loaded from HmdIccomt, with leaf items created at line 375.
