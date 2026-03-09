# MDN110UQ — Method Inventory

## Unit Purpose

ICU monitoring item input type/value editor with AdvStringGrid for editing monitoring item types and values, combo box input, and save functionality.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 79-95 | FindFormMethod('MDN110FM', 'GetMonitorDayInfo'), FindFormMethod('MDN110FM', 'GetMonitoring'), Action := caFree | HIGH |
| 2 | FormDestroy | published | (Sender: TObject) | 96-100 | MDN110FQ := Nil | LOW |
| 3 | bbt_CloseClick | published | (Sender: TObject) | 101-105 | Close | LOW |
| 4 | FormShow | published | (Sender: TObject) | 106-165 | GetInputType, GetInputValue, grid setup, label population | HIGH |
| 5 | GetInputValue | private | (Sender: TObject) | 166-237 | HmdIcrect.Create, grid population from middleware data | HIGH |
| 6 | GetInputType | private | (Sender: TObject) | 238-306 | HmdIcrect.Create, input type configuration load | HIGH |
| 7 | FormKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 307-318 | Escape key handling | LOW |
| 8 | agd_InputDrawCell | published | (Sender: TObject; ACol, ARow: Integer; Rect: TRect; State: TGridDrawState) | 319-324 | Canvas drawing | LOW |
| 9 | agd_InputGetAlignment | published | (Sender: TObject; ACol, ARow: Integer; var Alignment: TAlignment) | 325-331 | Column alignment | LOW |
| 10 | agd_InputGetCellColor | published | (Sender: TObject; ACol, ARow: Integer; AState: TGridDrawState; ABrush: TBrush; AFont: TFont) | 332-346 | Cell color based on row type | LOW |
| 11 | agd_InputClick | published | (Sender: TObject) | 347-367 | Grid cell click, combo box display | LOW |
| 12 | agd_InputDblClick | published | (Sender: TObject) | 368-471 | Grid double-click, inline editing with combo box, value assignment | HIGH |
| 13 | combx_InputExit | published | (Sender: TObject) | 472-524 | Combo box exit, value save to grid | HIGH |
| 14 | combx_InputKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 525-616 | Combo box key handling, Enter/Escape/Tab navigation | HIGH |
| 15 | bbt_SaveClick | published | (Sender: TObject) | 617-686 | HmdIcrect.Create, save all modified values via middleware | HIGH |
| 16 | med_ActTime2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 687-697 | Time input key handling | LOW |
| 17 | agd_InputKeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 698-716 | Grid key handling | LOW |

VALIDATION: Source has 17 implementations, inventory has 17 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (line 106) → GetInputType → GetInputValue → grid population
  → [User clicks cell] → agd_InputClick (line 347) → combo box display
  → [User double-clicks cell] → agd_InputDblClick (line 368) → inline editing
  → [User exits combo] → combx_InputExit (line 472) → value save to grid
  → [User clicks Save] → bbt_SaveClick (line 617) → HmdIcrect save
  → [User clicks Close] → bbt_CloseClick (line 101) → Close
FormClose (line 79) → FindFormMethod callbacks to MDN110FM, Action := caFree
FormDestroy (line 96) → MDN110FQ := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FQ | TMDN110FQ | FormCreate (implicit) | External callers | FormDestroy (set to Nil) |
| P_PatNo | String | External caller | GetInputType, GetInputValue, bbt_SaveClick | External caller |
| P_AdmDate | String | External caller | GetInputType, GetInputValue, bbt_SaveClick | External caller |
| P_ActTime | String | External caller | GetInputValue, bbt_SaveClick | External caller |
| P_ActDate | String | External caller | GetInputValue, bbt_SaveClick | External caller |
| P_Settype | String | External caller | GetInputType, GetInputValue | External caller |

## Middleware Contract Summary

| Class | Method | Input Params (name: type) | Output Shape | Error Convention |
|-------|--------|--------------------------|--------------|-----------------| 
| HmdIcrect | (query) | PatNo: String, AdmDate: String, ActDate: String, ActTime: String, SetType: String | Arrays: sItemCode[], sItemName[], sInputType[], sItemValue[] | Returns -1 on error, 0 on no data |
| HmdIcrect | (save) | PatNo: String, AdmDate: String, ActDate: String, ActTime: String, item data | Integer (result code) | Returns 0 on failure |

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| TMS AdvGrid | TAdvStringGrid | Cells[], RowCount, ColCount, GetAlignment, GetCellColor | Input type/value grid (agd_Input) |
| TMS AdvEdit | TAdvEdit | Text, Visible | Advanced edit control |
| TMS ImagePicker | TImagePicker | (display) | Visual selection |
| UltraGrid | TUltraGrid | Cells[], RowCount | List grid (ugd_List) |

## Repetitive Handler Analysis

N/A — no repetitive handler groups.
