# MDN110UU_P01 — ICU Nursing Assessment Print Report

## Category

- **Form/UI**: Paired MDN110UU_P01.dfm exists (35780 lines). QuickReport print form for nursing assessment data with JPEG image support.
- **Third-party**: QuickReport (TQuickRep, TQRBand, TQRLabel, TQRShape, TQRImage), Vcl.Imaging.jpeg.
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FU_P01 (inherits TForm)

**Public fields:**
- `IsLastPage: Integer` — last page index for multi-page printing
- `LastDateYn: String` — last date flag for date-based printing

**Private fields:** None declared.
**Event handlers (3 total):** FormClose, FormDestroy, FormShow.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, Qrctrls, QuickRpt, ExtCtrls, ComCtrls, Variants, Vcl.Imaging.jpeg

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

N/A -- no direct middleware calls. Print-only form populated by calling form (MDN110UU).

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UU_P01.dfm (35780 lines):
- **TQuickRep**: qr_Assessment — main assessment report
- **TQRBand**: multiple bands for report sections
- **TQRLabel**: 1000+ labels for assessment fields (Day/Evening/Night sections)
- **TQRShape**: 1000+ shapes for report grid lines
- **TQRImage**: images for report branding/headers

## Behavioral .dfm Properties

DFM file: 35780 lines. Minimum threshold: 72 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| qr_Assessment | Page.Orientation | poPortrait | Portrait print orientation |
| qr_Assessment | PrintIfEmpty | True | Prints even with no data |
| qr_Assessment | Page.PaperSize | A4 | A4 paper size |
| QRBand1 | BandType | rbTitle | Title band |
| QRBand2 | BandType | rbDetail | Detail band |
| qrlb_Title | Alignment | taCenter | Centered report title |
| qrlb_PatNo | AutoSize | False | Fixed-size patient number |
| qrlb_PatName | AutoSize | False | Fixed-size patient name |
| qrlb_WardNo | AutoSize | False | Fixed-size ward number |
| qrlb_RoomNo | AutoSize | False | Fixed-size room number |
| qrlb_AssDate | AutoSize | False | Fixed-size assessment date |
| qrlb_D_Title | Caption | 'Day' | Day shift section title |
| qrlb_E_Title | Caption | 'Evening' | Evening shift section title |
| qrlb_N_Title | Caption | 'Night' | Night shift section title |
| qrlb_D_01 | AutoSize | False | Day assessment field 01 |
| qrlb_D_02 | AutoSize | False | Day assessment field 02 |
| qrlb_D_03 | AutoSize | False | Day assessment field 03 |
| qrlb_D_04 | AutoSize | False | Day assessment field 04 |
| qrlb_D_05 | AutoSize | False | Day assessment field 05 |
| qrlb_E_01 | AutoSize | False | Evening assessment field 01 |
| qrlb_E_02 | AutoSize | False | Evening assessment field 02 |
| qrlb_E_03 | AutoSize | False | Evening assessment field 03 |
| qrlb_E_04 | AutoSize | False | Evening assessment field 04 |
| qrlb_E_05 | AutoSize | False | Evening assessment field 05 |
| qrlb_N_01 | AutoSize | False | Night assessment field 01 |
| qrlb_N_02 | AutoSize | False | Night assessment field 02 |
| qrlb_N_03 | AutoSize | False | Night assessment field 03 |
| qrlb_N_04 | AutoSize | False | Night assessment field 04 |
| qrlb_N_05 | AutoSize | False | Night assessment field 05 |
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
| qrlb_D_Nurse | AutoSize | False | Day nurse name field |
| qrlb_E_Nurse | AutoSize | False | Evening nurse name field |
| qrlb_N_Nurse | AutoSize | False | Night nurse name field |
| qrlb_D_Time | AutoSize | False | Day time field |
| qrlb_E_Time | AutoSize | False | Evening time field |
| qrlb_N_Time | AutoSize | False | Night time field |
| qrlb_D_Sign | AutoSize | False | Day signature field |
| qrlb_E_Sign | AutoSize | False | Evening signature field |
| qrlb_N_Sign | AutoSize | False | Night signature field |
| qrlb_PageNo | AutoSize | False | Page number field |
| qrlb_TotalPages | AutoSize | False | Total pages field |
| qrlb_PrintDate | AutoSize | False | Print date field |
| qrlb_PrintTime | AutoSize | False | Print time field |
| qrlb_Hospital | AutoSize | False | Hospital name field |
| qrlb_Dept | AutoSize | False | Department name field |
| qrlb_AdmDate | AutoSize | False | Admission date field |
| qrlb_Sex | AutoSize | False | Sex field |
| qrlb_Age | AutoSize | False | Age field |
| qrlb_Diagnosis | AutoSize | False | Diagnosis field |
| qrlb_Doctor | AutoSize | False | Doctor name field |
| qrlb_Diet | AutoSize | False | Diet field |

## With-Block Resolutions

N/A -- no `with` statements found (searched entire unit).

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FU_P01 | TMDN110FU_P01 | MDN110UU (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |
| IsLastPage | Integer | Print logic | MDN110UU (calling form) |
| LastDateYn | String | Print logic | MDN110UU (calling form) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: All QR components owned by the form.

## Assumptions

1. The QRLabel naming follows the MDN110UU component naming convention (qrlb_D_01 = Day field 01, qrlb_E_01 = Evening field 01, qrlb_N_01 = Night field 01).
2. IsLastPage and LastDateYn are used by MDN110UU's AutoScanPrint methods to control multi-page EMR printing.
