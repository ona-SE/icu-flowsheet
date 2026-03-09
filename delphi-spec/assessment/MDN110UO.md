# MDN110UO — ICU Information Entry/Edit Form

## Category

- **Form/UI**: Paired MDN110UO.dfm exists (8740 lines). Multi-tab ICU information entry form with page control, edit fields, checkboxes, radio buttons, combo boxes, and memo fields for patient data entry.
- **Database**: Tuxedo middleware via HmdPatinf (patient info), HmdIcuinf (ICU info read/write).
- **Third-party**: UltraGrid (TUltraGrid).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FO (inherits TForm)

**Public fields:** None declared.

**Private methods:**
- `procedure GetPatInfo` — retrieves patient information
- `procedure GetIcuSelect` — retrieves ICU selection data
- `function GetIcuInfo(patno: String, Admdate: String): Boolean` — retrieves ICU info for patient
- `procedure Clear_Screen` — clears all form fields

**Event handlers (91 total):** FormClose, FormDestroy, FormShow, bbt_CloseClick, pc_ICUChange, and 86 component-specific handlers (B0201_1Click, B0201_1KeyDown, B0203_1KeyDown, B0206_2Click, B0206_2KeyDown, B0207_2Click, B0207_2KeyDown, C0201_6Click, B0208_2Click, B0208_2KeyDown, B0210_2Click, B0210_2KeyDown, C0210_5Click, B0211_2Click, B0211_2KeyDown, C0211_5Click, B0212_2Click, B0212_2KeyDown, C0212_5Click, B0213_2Click, B0213_2KeyDown, etc.)

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ExtCtrls, StdCtrls, Buttons, Grids, UltraGrid, Mask, ComCtrls, Qrctrls, Variants

**Implementation uses:** CComFunc, VarCom, TuxCom, MsgCom, MDCLASS1, MComFunc, HisUtil, MDN110UO_P01

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet or record types declared. Data is stored in form component values (TEdit.Text, TCheckBox.Checked, TComboBox.ItemIndex, TMemo.Lines).

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

1. **HmdPatinf.ListPatbat(Cond: String, PatNo: String, PatName: String): Integer**
   - Parameters: Cond=search condition, PatNo=patient number, PatName=patient name
   - Returns: Integer (row count). Output arrays: sPatName[], sSex[], sBirtDate[], sAdmDate[], sMedDept[]
   - Error: returns -1 on system error, 0 on no data
   - Called at line 901

2. **HmdIcuinf.getIcuinflist(sFlag1: String, sType1: String, sType2: String, sType3: String, sType4: String, G_LOCATE: String): Integer**
   - Parameters: sFlag1=flag, sType1=PatNo, sType2=AdmDate, sType3=WardNo, sType4=filter, G_LOCATE=location
   - Returns: Integer (row count). Output: ICU info field arrays
   - Error: returns -1 on system error, 0 on no data
   - Called at line 948

3. **HmdIcuinf.getIcuinfwt(sFlag1: String, sType1: String, sType2: String, sType3: String, sType4: String, sType5: String): Integer**
   - Parameters: sFlag1=flag, sType1-sType5=various filter/data parameters
   - Returns: Integer (row count)
   - Error: returns -1 on system error
   - Called at lines 1000, 2028, 2214

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UO.dfm (8740 lines):
- **TPageControl**: pc_ICU (multiple tabs for different ICU info sections)
- **TEdit**: ~50+ edit fields (ed_PatNo, ed_PatNm, B0201_1, B0201_3, B0206_2, B0207_2, B0208_2, B0210_2, B0211_2, B0212_2, B0213_2, etc.)
- **TCheckBox**: ~30+ checkboxes (C0201_6, C0210_5, C0211_5, C0212_5, etc.)
- **TComboBox**: ~10+ combo boxes for selection fields
- **TMemo**: memo fields for free-text entry
- **TMaskEdit**: masked edit fields for formatted input
- **TRadioButton**: radio buttons for exclusive selections
- **TPanel**: ~40+ panels for layout
- **TLabel**: ~60+ labels

WARNING: BUSINESS LOGIC IN HANDLER: GetIcuInfo (lines 932-980) — loads ICU info from middleware and populates form fields
WARNING: BUSINESS LOGIC IN HANDLER: GetIcuSelect (lines 982-1052) — saves ICU info via middleware with form field values

## Behavioral .dfm Properties

DFM file: 8740 lines. Minimum threshold: 18 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| MDN110FO | BorderStyle | bsSingle | Non-resizable form |
| pc_ICU | ActivePage | ts_ICU1 | First tab shown by default |
| ed_PatNo | ReadOnly | True | Patient number not editable |
| ed_PatNm | ReadOnly | True | Patient name not editable |
| pn_Sex | Caption | '' | Sex display panel, populated at runtime |
| pn_Age | Caption | '' | Age display panel, populated at runtime |
| pn_AdmDate | Caption | '' | Admission date panel, populated at runtime |
| B0201_1 | MaxLength | 20 | Limits input field to 20 chars |
| B0206_2 | MaxLength | 10 | Limits input field to 10 chars |
| B0207_2 | MaxLength | 10 | Limits input field to 10 chars |
| B0208_2 | MaxLength | 10 | Limits input field to 10 chars |
| B0210_2 | MaxLength | 10 | Limits input field to 10 chars |
| B0211_2 | MaxLength | 10 | Limits input field to 10 chars |
| B0212_2 | MaxLength | 10 | Limits input field to 10 chars |
| B0213_2 | MaxLength | 10 | Limits input field to 10 chars |
| C0201_6 | Enabled | True | Checkbox enabled for user input |
| C0210_5 | Enabled | True | Checkbox enabled for user input |
| C0211_5 | Enabled | True | Checkbox enabled for user input |
| C0212_5 | Enabled | True | Checkbox enabled for user input |

## With-Block Resolutions

ORIGINAL (line 966): `with mdIcuinf do`
RESOLVED: mdIcuinf is HmdIcuinf. Members accessed: field arrays for ICU info data → mdIcuinf.sFieldName[index]

ORIGINAL (line 1016): `with mdIcuinf do`
RESOLVED: mdIcuinf is HmdIcuinf. Members accessed: field arrays → mdIcuinf.sFieldName[index]

ORIGINAL (line 1021): `with FindComponent(sName) as TEdit do`
RESOLVED: FindComponent returns a TComponent, cast to TEdit. Members accessed: Text → (FindComponent(sName) as TEdit).Text

ORIGINAL (line 1024): `with FindComponent(sName) as TEdit do`
RESOLVED: FindComponent returns a TComponent, cast to TEdit. Members accessed: Text → (FindComponent(sName) as TEdit).Text

ORIGINAL (line 1027): `with FindComponent(sName) as TMaskEdit do`
RESOLVED: FindComponent returns a TComponent, cast to TMaskEdit. Members accessed: Text → (FindComponent(sName) as TMaskEdit).Text

ORIGINAL (line 1030): `with FindComponent(sName) as TMaskEdit do`
RESOLVED: FindComponent returns a TComponent, cast to TMaskEdit. Members accessed: Text → (FindComponent(sName) as TMaskEdit).Text

ORIGINAL (line 1033): `with FindComponent(sName) as TComboBox do`
RESOLVED: FindComponent returns a TComponent, cast to TComboBox. Members accessed: ItemIndex → (FindComponent(sName) as TComboBox).ItemIndex

ORIGINAL (line 1036): `with FindComponent(sName) as TCheckBox do`
RESOLVED: FindComponent returns a TComponent, cast to TCheckBox. Members accessed: Checked → (FindComponent(sName) as TCheckBox).Checked

ORIGINAL (line 1039): `with FindComponent(sName) as TRadioButton do`
RESOLVED: FindComponent returns a TComponent, cast to TRadioButton. Members accessed: Checked → (FindComponent(sName) as TRadioButton).Checked

ORIGINAL (line 1042): `with FindComponent(sName) as TMemo do`
RESOLVED: FindComponent returns a TComponent, cast to TMemo. Members accessed: Lines.Text → (FindComponent(sName) as TMemo).Lines.Text

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FO | TMDN110FO | External callers | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used for HmdPatinf and HmdIcuinf middleware objects.
- **Owner-freed (TComponent.Owner)**: Form components freed automatically.

## Assumptions

1. The component naming convention (B0201_1, C0201_6, etc.) follows a structured pattern where the prefix indicates the section/category and the suffix indicates the field number. B=edit/button, C=checkbox.
2. FindComponent-based dynamic access (lines 1021-1042) iterates over component names constructed from middleware field metadata, allowing generic load/save of form fields.
