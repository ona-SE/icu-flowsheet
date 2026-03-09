# JOB 3A — COMPLETE

## Summary

Method-level inventories created for all 19 Delphi source units (769 total methods).

## Key Findings

1. **D/E/N Triplication**: Units UU, UV, UW, UX contain per-duty (Day/Evening/Night) triplicated handlers. ~50-58% of methods in these units are near-identical copies differing only in a duty prefix string. In the web migration, these collapse to parameterized handlers.

2. **FindComponent Pattern**: Units UO, UU, UV, UW, UX use FindComponent/GetComp extensively to dynamically map field names to form controls. This maps to a data-driven form model in the web app.

3. **Middleware Layer**: All data access goes through HmdIcuinf (ICU info), HmdIcasit (nursing assessment), and HmdPatinf (patient info) business objects that wrap Tuxedo service calls. The web migration needs equivalent API endpoints.

4. **Print Reports**: 6 print units (_P01/_P02 suffix) are QuickReport forms with 3-4 methods each. Most of their line count is QRLabel declarations, not logic. These become PDF/HTML report templates.

5. **Main Form Complexity**: MDN110UM (11893 lines, 125 methods) is the central hub. SetSaveList (742 lines) and SetFormInfo (661 lines) are the largest individual methods. The form manages patient list, monitoring grid, vital signs charting, notes, and launches all sub-forms.

6. **EMR Integration**: Units UU, UV, UW, UX each have a bbt_ToNrRecordDClick method (1000-1700 lines each) that builds nursing record strings for EMR integration via TpSvc.

## Artifacts

- 19 inventory files in `inventory/`
- programs.md updated (all 19 units status → inventoried)
- JOB3A_CHUNKS.md — chunk tracking
