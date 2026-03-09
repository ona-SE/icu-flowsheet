# MDN110UT — Method Inventory

## Unit Purpose

ICU nursing record (comment/IV line) viewer with AdvStringGrid for header and data display, duty-based data loading, and animated loading indicator.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 121-132 | FDuties.Free, FRecItems.Free, Action := caFree | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 133-146 | MDN110FT := Nil, cleanup | LOW |
| 3 | bbt_CloseClick | published | (Sender: TObject) | 147-160 | Close | LOW |
| 4 | FormCreate | published | (Sender: TObject) | 161-179 | FDuties := TList.Create, FRecItems := TList.Create | LOW |
| 5 | Initialize | private | () | 180-223 | asg_Header setup, asg_Data setup, duty period initialization | HIGH |
| 6 | FormShow | published | (Sender: TObject) | 224-252 | Initialize, Search | HIGH |
| 7 | Search | private | () | 253-278 | LoadRecordItemList, LoadAllItemValues | HIGH |
| 8 | LoadRecordItemList | private | () | 279-465 | HmdIccomt.Create, hierarchical item structure build, asg_Data population | HIGH |
| 9 | asg_HeaderGetAlignment | published | (Sender: TObject; ACol, ARow: Integer; var Alignment: TAlignment) | 466-482 | Column alignment | LOW |
| 10 | asg_DataGetAlignment | published | (Sender: TObject; ACol, ARow: Integer; var Alignment: TAlignment) | 483-500 | Column alignment | LOW |
| 11 | asg_DataCanEditCell | published | (Sender: TObject; ACol, ARow: Integer; var CanEdit: Boolean) | 501-515 | Edit permission check | LOW |
| 12 | asg_DataGetEditorType | published | (Sender: TObject; ACol, ARow: Integer; var AEditor: TEditorType) | 516-576 | Editor type determination based on item type | HIGH |
| 13 | LoadAllItemValues | private | () | 577-669 | HmdIcivlt.Create, cds_ItemValues population, asg_Data cell updates | HIGH |
| 14 | dtp_ActDateCloseUp | published | (Sender: TObject) | 670-689 | Date change, Search reload | LOW |
| 15 | sbt_PreviousClick | published | (Sender: TObject) | 690-714 | Previous date navigation, Search reload | LOW |
| 16 | sbt_NextClick | published | (Sender: TObject) | 715-740 | Next date navigation, Search reload | LOW |
| 17 | asg_HeaderGetEditMask | published | (Sender: TObject; ACol, ARow: Integer; var Value: String) | 741-754 | Edit mask for header cells | LOW |

VALIDATION: Source has 17 implementations, inventory has 17 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (line 161) → FDuties.Create, FRecItems.Create
  → FormShow (line 224) → Initialize → Search
    → LoadRecordItemList (line 279) → HmdIccomt hierarchy build
    → LoadAllItemValues (line 577) → HmdIcivlt data load → grid population
  → [User changes date] → dtp_ActDateCloseUp (line 670) → Search
  → [User clicks Previous] → sbt_PreviousClick (line 690) → Search
  → [User clicks Next] → sbt_NextClick (line 715) → Search
  → [User clicks Close] → bbt_CloseClick (line 147) → Close
FormClose (line 121) → FDuties.Free, FRecItems.Free, Action := caFree
FormDestroy (line 133) → MDN110FT := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FT | TMDN110FT | FormCreate (implicit) | External callers | FormDestroy (set to Nil) |
| FDuties | TList | FormCreate | Search, LoadAllItemValues | Initialize |
| FRecItems | TList | FormCreate | LoadAllItemValues, asg_DataGetEditorType | LoadRecordItemList |

## Middleware Contract Summary

| Class | Method | Input Params (name: type) | Output Shape | Error Convention |
|-------|--------|--------------------------|--------------|-----------------| 
| HmdIccomt | (query) | PatNo: String, AdmDate: String, ActDate: String | Hierarchical item structure: sItemCode[], sItemName[], sParentCode[], sItemType[] | Returns -1 on error, 0 on no data |
| HmdIcivlt | (query) | PatNo: String, AdmDate: String, ActDate: String, DutyCode: String | IV line data: sActTime[], sItemValue[] per duty | Returns -1 on error, 0 on no data |

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| TMS AdvGrid | TAdvStringGrid | Cells[], RowCount, ColCount, GetAlignment, GetCellColor, GetEditorType, CanEditCell | Header grid (asg_Header), data grid (asg_Data) |
| TMS AdvPanel | TAdvPanel | Visible | Loading indicator panel (apn_Loading) |
| TMS AdvPicture | TAdvPicture | (display) | Animated loading image |
| RxLib | RxGIFCtrl | TRxGIFAnimator | Animated GIF for loading indicator |
| Db/DBClient | TClientDataSet | Append, FieldByName, Post, First, Eof, Next | cds_ItemValues dataset |

## Repetitive Handler Analysis

N/A — no repetitive handler groups.
