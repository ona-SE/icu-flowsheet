# MDN110UO_P01 — ICU Information Print Report

## Category

- **Form/UI**: Paired MDN110UO_P01.dfm exists (18507 lines). QuickReport print form for ICU information data.
- **Third-party**: QuickReport (TQuickRep, TQRBand, TQRLabel, TQRShape).
- **OS/Win32-specific**: Uses Windows unit.

## Public Interface

### Class: TMDN110FO_P01 (inherits TForm)

**Public fields:** None declared.
**Private fields:** None declared.
**Event handlers (3 total):** FormClose, FormDestroy, FormShow.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, Qrctrls, QuickRpt, ExtCtrls, Variants

**Implementation uses:** MComFunc, VarCom

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

N/A -- no middleware calls. Print-only form populated by calling form (MDN110UO).

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UO_P01.dfm (18507 lines):
- **TQuickRep**: qr_IcuInfo — main report
- **TQRBand**: multiple bands for report sections
- **TQRLabel**: 500+ labels for ICU info fields
- **TQRShape**: 500+ shapes for report grid lines

## Behavioral .dfm Properties

DFM file: 18507 lines. Minimum threshold: 38 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| qr_IcuInfo | Page.Orientation | poPortrait | Portrait print orientation |
| qr_IcuInfo | PrintIfEmpty | True | Prints even with no data |
| QRBand1 | BandType | rbTitle | Title band |
| QRBand2 | BandType | rbDetail | Detail band |
| qrlb_Title | Alignment | taCenter | Centered report title |
| qrlb_PatNo | AutoSize | False | Fixed-size patient number label |
| qrlb_PatNm | AutoSize | False | Fixed-size patient name label |
| qrlb_Sex | AutoSize | False | Fixed-size sex label |
| qrlb_Age | AutoSize | False | Fixed-size age label |
| qrlb_AdmDate | AutoSize | False | Fixed-size admission date label |
| qrlb_MedDept | AutoSize | False | Fixed-size department label |
| qrlb_B0201 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0203 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0206 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0207 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0208 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0210 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0211 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0212 | AutoSize | False | Fixed-size ICU info field |
| qrlb_B0213 | AutoSize | False | Fixed-size ICU info field |
| qrlb_C0201 | AutoSize | False | Fixed-size checkbox result field |
| qrlb_C0210 | AutoSize | False | Fixed-size checkbox result field |
| qrlb_C0211 | AutoSize | False | Fixed-size checkbox result field |
| qrlb_C0212 | AutoSize | False | Fixed-size checkbox result field |
| QRShape1 | Shape | qrsHorLine | Horizontal separator |
| QRShape2 | Shape | qrsVertLine | Vertical separator |
| QRShape3 | Shape | qrsRectangle | Section border |
| QRShape4 | Shape | qrsRectangle | Section border |
| QRShape5 | Shape | qrsHorLine | Horizontal separator |
| QRShape6 | Shape | qrsVertLine | Vertical separator |
| QRShape7 | Shape | qrsRectangle | Section border |
| QRShape8 | Shape | qrsRectangle | Section border |
| QRShape9 | Shape | qrsHorLine | Horizontal separator |
| QRShape10 | Shape | qrsRectangle | Section border |
| QRShape11 | Shape | qrsVertLine | Vertical separator |
| QRShape12 | Shape | qrsRectangle | Section border |
| QRShape13 | Shape | qrsHorLine | Horizontal separator |
| QRShape14 | Shape | qrsRectangle | Section border |

## With-Block Resolutions

N/A -- no `with` statements found (searched entire unit).

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FO_P01 | TMDN110FO_P01 | MDN110UO (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: All QR components owned by the form.

## Assumptions

1. The QRLabel naming follows the MDN110UO component naming convention (qrlb_B0201, qrlb_C0201, etc.) for direct mapping from form fields to report labels.
