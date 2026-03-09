# MDN110UM_P02 — ICU Monitoring Print Report (A4 Size)

## Category

- **Form/UI**: Paired MDN110UM_P02.dfm exists (4071 lines). QuickReport print form for ICU monitoring data in A4 format.
- **Third-party**: QuickReport (TQuickRep, TQRBand, TQRLabel, TQRShape), QrTee, VCL TeeChart (TChart, TLineSeries, TDBChart).
- **OS/Win32-specific**: Uses Windows unit, Printers unit (implicit via QuickReport).

## Public Interface

### Class: TMDN110FM_P02 (inherits TForm)

**Public fields:** None declared.
**Private fields:** None declared.
**Event handlers (4 total):** FormClose, FormDestroy, FormShow, qr_Icu_A4BeforePrint.

The form contains a TQuickRep (qr_Icu_A4) with bands and ~200+ QRLabel/QRShape components.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, Qrctrls, QuickRpt, ExtCtrls, QrTee, ComCtrls, StdCtrls, Grids, BaseGrid, AdvGrid, Variants, VclTee.TeEngine, VclTee.Series, VclTee.TeeProcs, VclTee.Chart, VclTee.DBChart, VclTee.TeeGDIPlus

**Implementation uses:** VarCom, HisUtil, CComFunc, MComFunc

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

N/A -- no middleware calls. Print-only form populated by calling form.

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UM_P02.dfm (4071 lines):
- **TQuickRep**: qr_Icu_A4 — main A4 report
- **TQRBand**: QRBand2 — report band
- **TQRLabel**: qrlb_Val0 through qrlb_Val200+ — report value labels
- **TQRShape**: QRShape111 through QRShape200+ — report grid lines
- **TChart**: chr_VS — vital signs chart embedded in report

## Behavioral .dfm Properties

DFM file: 4071 lines. Minimum threshold: 9 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| qr_Icu_A4 | Page.Orientation | poLandscape | Landscape A4 print |
| qr_Icu_A4 | Page.PaperSize | A4 | A4 paper size |
| qr_Icu_A4 | PrintIfEmpty | True | Prints even with no data |
| QRBand2 | BandType | rbDetail | Detail band |
| qrlb_Val0 | Alignment | taCenter | Centered header |
| chr_VS | Legend.Visible | False | Chart legend hidden |
| chr_VS | Title.Visible | False | Chart title hidden |
| qrlb_Val2 | AutoSize | False | Fixed-size label |
| qrlb_Val3 | AutoSize | False | Fixed-size label |

## With-Block Resolutions

ORIGINAL (line 568): `with PrintGrid do`
RESOLVED: PrintGrid is a local variable (grid reference passed from calling form). Members accessed: Cells[col,row], RowCount, ColCount → PrintGrid.Cells[col,row], PrintGrid.RowCount

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FM_P02 | TMDN110FM_P02 | MDN110UM (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: All QR components owned by the form.

## Assumptions

1. This is the A4-size variant of MDN110UM_P01. The layout and data population logic follow the pattern used in MDN110UM_P01 but with A4 paper dimensions.
