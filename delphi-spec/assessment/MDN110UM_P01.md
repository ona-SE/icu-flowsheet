# MDN110UM_P01 — ICU Monitoring Print Report (Standard Size)

## Category

- **Form/UI**: Paired MDN110UM_P01.dfm exists (4138 lines). QuickReport print form for ICU monitoring data.
- **Third-party**: QuickReport (TQuickRep, TQRBand, TQRLabel, TQRShape, TQRImage), QrTee (chart in report), VCL TeeChart (TChart, TLineSeries, TDBChart).
- **OS/Win32-specific**: Uses Windows unit, Printers unit (implicit via QuickReport).

## Public Interface

### Class: TMDN110FM_P01 (inherits TForm)

**Public fields:** None declared.
**Private fields:** None declared.
**Event handlers (4 total):** FormClose, FormDestroy, FormShow, qr_IcuBeforePrint.

The form contains a TQuickRep (qr_Icu) with bands and ~200+ QRLabel/QRShape components for report layout.

## Dependencies

**Interface uses:** Windows, Messages, SysUtils, Classes, Graphics, Controls, Forms, Dialogs, Qrctrls, QuickRpt, ExtCtrls, QrTee, ComCtrls, StdCtrls, Grids, BaseGrid, AdvGrid, QRPrntr, Variants, VclTee.TeEngine, VclTee.Series, VclTee.TeeProcs, VclTee.Chart, VclTee.DBChart, VclTee.TeeGDIPlus

**Implementation uses:** VarCom, HisUtil, CComFunc, MComFunc

## Conditional Compilation

N/A -- no {$ifdef} directives found in this unit.

## Include Files

N/A -- no {$I} or {$INCLUDE} directives found in this unit.

## Data Structures

N/A -- no TClientDataSet or record types declared. Report data is set via QRLabel.Caption assignments from the calling form.

## Generics

N/A -- no generic types used in this unit.

## Class Helpers

N/A -- no class helpers or record helpers declared in this unit.

## Database / Middleware Access

N/A -- no middleware calls. This is a print-only form. Data is populated by the calling form (MDN110UM) setting QRLabel captions and chart series data.

## DLL / External API Bindings

N/A -- no external function imports in this unit.

## Form Components

Key components from MDN110UM_P01.dfm (4138 lines):
- **TQuickRep**: qr_Icu — main report
- **TQRBand**: QRBand2 — report band
- **TQRLabel**: qrlb_Val0 through qrlb_Val200+ — report value labels
- **TQRShape**: QRShape111 through QRShape200+ — report grid lines
- **TQRImage**: report images
- **TChart**: chr_VS — vital signs chart embedded in report

## Behavioral .dfm Properties

DFM file: 4138 lines. Minimum threshold: 9 rows.

| Component | Property | Value | Behavioral Impact |
|-----------|----------|-------|-------------------|
| qr_Icu | Page.Orientation | poLandscape | Landscape print orientation |
| qr_Icu | Page.PaperSize | Custom | Custom paper size for ICU flowsheet |
| qr_Icu | PrintIfEmpty | True | Prints even with no data |
| QRBand2 | BandType | rbDetail | Detail band for data rows |
| qrlb_Val0 | Alignment | taCenter | Centered header label |
| chr_VS | Visible | True | Chart always visible in report |
| chr_VS | Legend.Visible | False | Chart legend hidden |
| chr_VS | Title.Visible | False | Chart title hidden |
| qrlb_Val2 | AutoSize | False | Fixed-size label for data alignment |
| qrlb_Val3 | AutoSize | False | Fixed-size label for data alignment |

## With-Block Resolutions

ORIGINAL (line 573): `with PrintGrid do`
RESOLVED: PrintGrid is a local variable (TAdvStringGrid or similar grid passed as parameter). Members accessed: Cells[col,row], RowCount, ColCount → PrintGrid.Cells[col,row], PrintGrid.RowCount

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FM_P01 | TMDN110FM_P01 | MDN110UM (calling form) | FormCreate (implicit), FormDestroy (set to Nil) |

## Custom Destructors

N/A -- no custom destructors. FormClose sets Action := caFree.

## Memory Management Patterns

- **Owner-freed (TComponent.Owner)**: All QR components owned by the form.

## Assumptions

1. PrintGrid in the `with` block at line 573 is a TAdvStringGrid reference passed from MDN110UM's asg_Print or asg_IcuMon grid.
2. This form is the standard-size print layout. MDN110UM_P02 is the A4-size variant.
