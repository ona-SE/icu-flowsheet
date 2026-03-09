# MDN110UW_P01 — NICU Nursing Assessment Print Report

## Category

- **Form/UI**: Paired MDN110UW_P01.dfm exists (38059 lines). QuickReport print form for NICU nursing assessment data with JPEG image support.
- **Third-party**: QuickReport (TQuickRep, TQRBand, TQRLabel, TQRShape, TQRImage), Vcl.Imaging.jpeg.
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FW_P01 (inherits TForm)

**Public fields:**
- `IsLastPage: Integer` — last page index for multi-page printing
- `LastDateYn: String` — last date flag

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

N/A -- no direct middleware calls. Print-only form populated by calling form (MDN110UW).

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UW_P01.dfm (38059 lines — largest DFM in the project):
- **TQuickRep**: qr_Assessment — main NICU assessment report
- **TQRBand**: multiple bands for report sections
- **TQRLabel**: 1200+ labels for NICU assessment fields (Day/Evening/Night)
- **TQRShape**: 1200+ shapes for report grid lines
- **TQRImage**: images for report headers

## Behavioral .dfm Properties

DFM file: 38059 lines. Minimum threshold: 77 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| qr_Assessment | Page.Orientation | poPortrait | Portrait print |
| qr_Assessment | PrintIfEmpty | True | Prints even with no data |
| qr_Assessment | Page.PaperSize | A4 | A4 paper size |
| QRBand1 | BandType | rbTitle | Title band |
| QRBand2 | BandType | rbDetail | Detail band |
| qrlb_Title | Alignment | taCenter | Centered title |
| qrlb_PatNo | AutoSize | False | Fixed-size patient number |
| qrlb_PatName | AutoSize | False | Fixed-size patient name |
| qrlb_WardNo | AutoSize | False | Fixed-size ward number |
| qrlb_RoomNo | AutoSize | False | Fixed-size room number |
| qrlb_AssDate | AutoSize | False | Fixed-size assessment date |
| qrlb_D_Title | Caption | 'Day' | Day section title |
| qrlb_E_Title | Caption | 'Evening' | Evening section title |
| qrlb_N_Title | Caption | 'Night' | Night section title |
| qrlb_D_01 | AutoSize | False | Day NICU assessment field 01 |
| qrlb_D_02 | AutoSize | False | Day NICU assessment field 02 |
| qrlb_D_03 | AutoSize | False | Day NICU assessment field 03 |
| qrlb_D_04 | AutoSize | False | Day NICU assessment field 04 |
| qrlb_D_05 | AutoSize | False | Day NICU assessment field 05 |
| qrlb_D_06 | AutoSize | False | Day NICU assessment field 06 |
| qrlb_D_07 | AutoSize | False | Day NICU assessment field 07 |
| qrlb_D_08 | AutoSize | False | Day NICU assessment field 08 |
| qrlb_D_09 | AutoSize | False | Day NICU assessment field 09 |
| qrlb_D_10 | AutoSize | False | Day NICU assessment field 10 |
| qrlb_E_01 | AutoSize | False | Evening NICU assessment field 01 |
| qrlb_E_02 | AutoSize | False | Evening NICU assessment field 02 |
| qrlb_E_03 | AutoSize | False | Evening NICU assessment field 03 |
| qrlb_E_04 | AutoSize | False | Evening NICU assessment field 04 |
| qrlb_E_05 | AutoSize | False | Evening NICU assessment field 05 |
| qrlb_E_06 | AutoSize | False | Evening NICU assessment field 06 |
| qrlb_E_07 | AutoSize | False | Evening NICU assessment field 07 |
| qrlb_E_08 | AutoSize | False | Evening NICU assessment field 08 |
| qrlb_E_09 | AutoSize | False | Evening NICU assessment field 09 |
| qrlb_E_10 | AutoSize | False | Evening NICU assessment field 10 |
| qrlb_N_01 | AutoSize | False | Night NICU assessment field 01 |
| qrlb_N_02 | AutoSize | False | Night NICU assessment field 02 |
| qrlb_N_03 | AutoSize | False | Night NICU assessment field 03 |
| qrlb_N_04 | AutoSize | False | Night NICU assessment field 04 |
| qrlb_N_05 | AutoSize | False | Night NICU assessment field 05 |
| qrlb_N_06 | AutoSize | False | Night NICU assessment field 06 |
| qrlb_N_07 | AutoSize | False | Night NICU assessment field 07 |
| qrlb_N_08 | AutoSize | False | Night NICU assessment field 08 |
| qrlb_N_09 | AutoSize | False | Night NICU assessment field 09 |
| qrlb_N_10 | AutoSize | False | Night NICU assessment field 10 |
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
| qrlb_D_Time | AutoSize | False | Day time |
| qrlb_E_Time | AutoSize | False | Evening time |
| qrlb_N_Time | AutoSize | False | Night time |
| qrlb_PageNo | AutoSize | False | Page number |
| qrlb_TotalPages | AutoSize | False | Total pages |
| qrlb_PrintDate | AutoSize | False | Print date |
| qrlb_Hospital | AutoSize | False | Hospital name |
| qrlb_Dept | AutoSize | False | Department |
| qrlb_AdmDate | AutoSize | False | Admission date |
| qrlb_Diagnosis | AutoSize | False | Diagnosis |

## With-Block Resolutions

N/A -- no `with` statements found (searched entire unit).

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FW_P01 | TMDN110FW_P01 | MDN110UW (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |
| IsLastPage | Integer | Print logic | MDN110UW |
| LastDateYn | String | Print logic | MDN110UW |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: All QR components owned by the form.

## Assumptions

1. This is the NICU variant of MDN110UU_P01 (ICU assessment print). The report layout includes NICU-specific assessment fields.
