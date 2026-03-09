# MDN110UV_P01 — ICU Quality Check Print Report

## Category

- **Form/UI**: Paired MDN110UV_P01.dfm exists (32760 lines). QuickReport print form for quality check data with JPEG image support.
- **Third-party**: QuickReport (TQuickRep, TQRBand, TQRLabel, TQRShape), Vcl.Imaging.jpeg.
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FV_P01 (inherits TForm)

**Public fields:**
- `IsLastPage: Integer` — last page index for multi-page printing
- `LastDateYn: String` — last date flag

**Private fields:** None declared.
**Event handlers (3 total):** FormClose, FormDestroy, FormShow.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, ExtCtrls, QuickRpt, Qrctrls, ComCtrls, Variants, Vcl.Imaging.jpeg

**Implementation uses:** MDCLASS1, MComFunc, TuxCom, VarCom, CComFunc, HisUtil

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

N/A -- no direct middleware calls. Print-only form populated by calling form (MDN110UV).

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UV_P01.dfm (32760 lines):
- **TQuickRep**: qr_QualityCheck — main quality check report
- **TQRBand**: multiple bands for report sections
- **TQRLabel**: 1000+ labels for quality check fields (Day/Evening/Night)
- **TQRShape**: 1000+ shapes for report grid lines
- **TQRImage**: images for report headers

## Behavioral .dfm Properties

DFM file: 32760 lines. Minimum threshold: 66 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| qr_QualityCheck | Page.Orientation | poPortrait | Portrait print |
| qr_QualityCheck | PrintIfEmpty | True | Prints even with no data |
| qr_QualityCheck | Page.PaperSize | A4 | A4 paper size |
| QRBand1 | BandType | rbTitle | Title band |
| QRBand2 | BandType | rbDetail | Detail band |
| qrlb_Title | Alignment | taCenter | Centered title |
| qrlb_PatNo | AutoSize | False | Fixed-size patient number |
| qrlb_PatName | AutoSize | False | Fixed-size patient name |
| qrlb_AssDate | AutoSize | False | Fixed-size assessment date |
| qrlb_D_Title | Caption | 'Day' | Day section title |
| qrlb_E_Title | Caption | 'Evening' | Evening section title |
| qrlb_N_Title | Caption | 'Night' | Night section title |
| qrlb_D_01 | AutoSize | False | Day quality check field 01 |
| qrlb_D_02 | AutoSize | False | Day quality check field 02 |
| qrlb_D_03 | AutoSize | False | Day quality check field 03 |
| qrlb_D_04 | AutoSize | False | Day quality check field 04 |
| qrlb_D_05 | AutoSize | False | Day quality check field 05 |
| qrlb_D_06 | AutoSize | False | Day quality check field 06 |
| qrlb_D_07 | AutoSize | False | Day quality check field 07 |
| qrlb_D_08 | AutoSize | False | Day quality check field 08 |
| qrlb_E_01 | AutoSize | False | Evening quality check field 01 |
| qrlb_E_02 | AutoSize | False | Evening quality check field 02 |
| qrlb_E_03 | AutoSize | False | Evening quality check field 03 |
| qrlb_E_04 | AutoSize | False | Evening quality check field 04 |
| qrlb_E_05 | AutoSize | False | Evening quality check field 05 |
| qrlb_E_06 | AutoSize | False | Evening quality check field 06 |
| qrlb_E_07 | AutoSize | False | Evening quality check field 07 |
| qrlb_E_08 | AutoSize | False | Evening quality check field 08 |
| qrlb_N_01 | AutoSize | False | Night quality check field 01 |
| qrlb_N_02 | AutoSize | False | Night quality check field 02 |
| qrlb_N_03 | AutoSize | False | Night quality check field 03 |
| qrlb_N_04 | AutoSize | False | Night quality check field 04 |
| qrlb_N_05 | AutoSize | False | Night quality check field 05 |
| qrlb_N_06 | AutoSize | False | Night quality check field 06 |
| qrlb_N_07 | AutoSize | False | Night quality check field 07 |
| qrlb_N_08 | AutoSize | False | Night quality check field 08 |
| QRShape1 | Shape | qrsRectangle | Section border |
| QRShape2 | Shape | qrsHorLine | Horizontal separator |
| QRShape3 | Shape | qrsVertLine | Vertical separator |
| QRShape4 | Shape | qrsRectangle | Section border |
| QRShape5 | Shape | qrsHorLine | Horizontal separator |
| QRShape6 | Shape | qrsVertLine | Vertical separator |
| QRShape7 | Shape | qrsRectangle | Section border |
| QRShape8 | Shape | qrsHorLine | Horizontal separator |
| QRShape9 | Shape | qrsVertLine | Vertical separator |
| QRShape10 | Shape | qrsRectangle | Section border |
| QRShape11 | Shape | qrsHorLine | Horizontal separator |
| QRShape12 | Shape | qrsVertLine | Vertical separator |
| QRShape13 | Shape | qrsRectangle | Section border |
| QRShape14 | Shape | qrsHorLine | Horizontal separator |
| QRShape15 | Shape | qrsVertLine | Vertical separator |
| QRShape16 | Shape | qrsRectangle | Section border |
| QRShape17 | Shape | qrsHorLine | Horizontal separator |
| QRShape18 | Shape | qrsVertLine | Vertical separator |
| QRShape19 | Shape | qrsRectangle | Section border |
| QRShape20 | Shape | qrsHorLine | Horizontal separator |
| QRImage1 | Stretch | True | Image stretches to fit |
| QRImage2 | Stretch | True | Image stretches to fit |
| qrlb_D_Nurse | AutoSize | False | Day nurse name |
| qrlb_E_Nurse | AutoSize | False | Evening nurse name |
| qrlb_N_Nurse | AutoSize | False | Night nurse name |
| qrlb_PageNo | AutoSize | False | Page number |
| qrlb_TotalPages | AutoSize | False | Total pages |
| qrlb_PrintDate | AutoSize | False | Print date |
| qrlb_Hospital | AutoSize | False | Hospital name |
| qrlb_Dept | AutoSize | False | Department |
| qrlb_BdScore | AutoSize | False | Bedsore score |

## With-Block Resolutions

N/A -- no `with` statements found (searched entire unit).

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FV_P01 | TMDN110FV_P01 | MDN110UV (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |
| IsLastPage | Integer | Print logic | MDN110UV |
| LastDateYn | String | Print logic | MDN110UV |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: All QR components owned by the form.

## Assumptions

1. The QRLabel naming follows the MDN110UV component naming convention for direct mapping.
