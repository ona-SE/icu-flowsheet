# MDN110UM — With-Block Resolutions, Shared State, and Remaining Sections

## With-Block Resolutions

ORIGINAL (line 994): `with iPats do`
RESOLVED: iPats is HmdIcpatt. Members accessed: sBldType[0], sPatNo[i], sAdmDate[i], sActDate[i], sMoniPrd[i] → iPats.sBldType[0], iPats.sPatNo[i], etc.

ORIGINAL (line 1135): `with ugd_EmrList do`
RESOLVED: ugd_EmrList is TUltraGrid. Members accessed: RowCount, ColCount, Cells[col,row] → ugd_EmrList.RowCount, ugd_EmrList.Cells[col,row]

ORIGINAL (line 1796): `with cds_MonItem do`
RESOLVED: cds_MonItem is TClientDataSet. Members accessed: Close, CreateDataSet, FieldDefs → cds_MonItem.Close, cds_MonItem.CreateDataSet

ORIGINAL (line 1997): `with iPats do`
RESOLVED: iPats is HmdIcpatt. Members accessed: sPatNo[0], sAdmDate[0], sWardNo[0], sRoomNo[0], sSetType[0], sActDate[0], sMoniPrd[0] → iPats.sPatNo[0], etc.

ORIGINAL (line 2085): `with cds_MonItem do`
RESOLVED: cds_MonItem is TClientDataSet. Members accessed: Append, FieldByName, Post → cds_MonItem.Append, cds_MonItem.FieldByName(...)

ORIGINAL (line 2136): `with cds_MonItem do`
RESOLVED: cds_MonItem is TClientDataSet. Members accessed: First, Eof, FieldByName, Next → cds_MonItem.First, cds_MonItem.FieldByName(...)

ORIGINAL (line 2563): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: ColCount, RowCount, Cells[col,row], ColWidths[col] → asg_IcuMon.ColCount, asg_IcuMon.Cells[col,row]

ORIGINAL (line 2749): `with iCrect, asg_IcuMon do`
UNRESOLVABLE: Multi-object with — iCrect is HmdIcutot and asg_IcuMon is TAdvStringGrid. Members like Cells[] belong to asg_IcuMon; array fields like sItemCode[], sItemName[] belong to iCrect. Resolution depends on member name: Cells → asg_IcuMon.Cells; sItemCode → iCrect.sItemCode. No ambiguous members detected in this block.

ORIGINAL (line 2976): `with iCrect do`
RESOLVED: iCrect is HmdIcutot. Members accessed: sPatNo[0], sAdmDate[0], sActDate[0], sSetCode[0], sSetType[0] → iCrect.sPatNo[0], etc.

ORIGINAL (line 3173): `with iCrect, asg_IcuMon do`
UNRESOLVABLE: Multi-object with — iCrect is HmdIcutot and asg_IcuMon is TAdvStringGrid. Resolution by member name: Cells → asg_IcuMon.Cells; sItemCode, sItemName → iCrect.sItemCode, iCrect.sItemName. No ambiguous members detected.

ORIGINAL (line 3505): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row], ColCount → asg_IcuMon.Cells[col,row]

ORIGINAL (line 3553): `with iCrect do`
RESOLVED: iCrect is HmdIcutot. Members accessed: sPatNo[0], sAdmDate[0], sActDate[0], sSetCode[0] → iCrect.sPatNo[0], etc.

ORIGINAL (line 3619): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 3793): `with iCrect, asg_IcuMon do`
UNRESOLVABLE: Multi-object with — iCrect is HmdIcutot and asg_IcuMon is TAdvStringGrid. Resolution by member name as above. No ambiguous members detected.

ORIGINAL (line 3948): `with cds_MonItem do`
RESOLVED: cds_MonItem is TClientDataSet. Members accessed: First, Eof, FieldByName, Next → cds_MonItem.First, cds_MonItem.FieldByName(...)

ORIGINAL (line 3993): `with HmdIcutot(l_CodeItem.Items[ARow-1]) do`
RESOLVED: Cast of l_CodeItem.Items[ARow-1] to HmdIcutot. Members accessed: sSetCode[0], sItemCode[0] → HmdIcutot(l_CodeItem.Items[ARow-1]).sSetCode[0]

ORIGINAL (line 3995): `with cds_MonItem do`
RESOLVED: cds_MonItem is TClientDataSet. Members accessed: First, Eof, FieldByName, Next → cds_MonItem.First, cds_MonItem.FieldByName(...)

ORIGINAL (line 4006): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4090): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row], ColCount → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4092): `with cds_SaveItem do`
RESOLVED: cds_SaveItem is TClientDataSet. Members accessed: Append, FieldByName, Post → cds_SaveItem.Append, cds_SaveItem.FieldByName(...)

ORIGINAL (line 4468): `with cds_SaveItem do`
RESOLVED: cds_SaveItem is TClientDataSet. Members accessed: First, Eof, FieldByName, Next → cds_SaveItem.First, cds_SaveItem.FieldByName(...)

ORIGINAL (line 4501): `with HmdIcutot(l_SaveItem.Last) do`
RESOLVED: Cast of l_SaveItem.Last to HmdIcutot. Members accessed: sSetCode[0], sActTime[0], sItemValue[0] → HmdIcutot(l_SaveItem.Last).sSetCode[0]

ORIGINAL (line 4555): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4581): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4601): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4622): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4870): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 4995): `with items do`
RESOLVED: items is HmdIcutot (local variable). Members accessed: sItemCode[], sItemName[], sItemValue[] → items.sItemCode[], items.sItemName[]

ORIGINAL (line 5126): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row], Col, Row → asg_IcuMon.Cells[col,row]

ORIGINAL (line 5185): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 5778): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row], ColCount → asg_IcuMon.Cells[col,row]

ORIGINAL (line 5961): `with asg_Note do`
RESOLVED: asg_Note is TAdvStringGrid. Members accessed: Cells[col,row], RowCount → asg_Note.Cells[col,row]

ORIGINAL (line 5974): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 6154): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row], ColCount → asg_IcuMon.Cells[col,row]

ORIGINAL (line 6209): `with srcPrt do`
RESOLVED: srcPrt is a local QuickReport variable. Members accessed: report properties for print setup.

ORIGINAL (line 6685): `with iCrect do`
RESOLVED: iCrect is HmdIcutot. Members accessed: sPatNo[0], sAdmDate[0], sActDate[0] → iCrect.sPatNo[0], etc.

ORIGINAL (line 6889): `with iCrect do`
RESOLVED: iCrect is HmdIcutot. Members accessed: sPatNo[0], sAdmDate[0], sActDate[0] → iCrect.sPatNo[0], etc.

ORIGINAL (line 7145): `with asg_Note, iNrect do`
UNRESOLVABLE: Multi-object with — asg_Note is TAdvStringGrid and iNrect is HmdNrrect. Resolution by member name: Cells → asg_Note.Cells; sActDate, sActTime, sContent → iNrect.sActDate, etc. No ambiguous members detected.

ORIGINAL (line 7360): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7377): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7524): `with mdTemplt do`
RESOLVED: mdTemplt is HmdTemplt. Members accessed: sTemplTitle[], sTemplContent[] → mdTemplt.sTemplTitle[], mdTemplt.sTemplContent[]

ORIGINAL (line 7725): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7823): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7870): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7911): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7929): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 7980): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 8019): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 8092): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 8150): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 8171): `with asg_IcuMon do`
RESOLVED: asg_IcuMon is TAdvStringGrid. Members accessed: Cells[col,row] → asg_IcuMon.Cells[col,row]

ORIGINAL (line 9420): `with ugd_PatList do`
RESOLVED: ugd_PatList is TUltraGrid. Members accessed: RowCount, Cells[col,row] → ugd_PatList.RowCount, ugd_PatList.Cells[col,row]

ORIGINAL (line 9627): `with iWrkLst do`
RESOLVED: iWrkLst is HmdWrkLst. Members accessed: sPatNo[], sAdmDate[], sWardNo[], sRoomNo[] → iWrkLst.sPatNo[], etc.

ORIGINAL (line 10419): `with ugd_BsData, mdiochkt do`
UNRESOLVABLE: Multi-object with — ugd_BsData is TUltraGrid and mdiochkt is HmdIochkt. Resolution by member name: Cells → ugd_BsData.Cells; sActDate, sActTime, sItemValue → mdiochkt.sActDate, etc. No ambiguous members detected.

ORIGINAL (line 10592): `with ugd_IoData, mdIochkt do`
UNRESOLVABLE: Multi-object with — ugd_IoData is TUltraGrid and mdIochkt is HmdIochkt. Resolution by member name: Cells → ugd_IoData.Cells; sActDate, sActTime → mdIochkt.sActDate, etc. No ambiguous members detected.

ORIGINAL (line 10713): `with ugd_IoData, mdHuockt do`
UNRESOLVABLE: Multi-object with — ugd_IoData is TUltraGrid and mdHuockt is HmdHuockt. Resolution by member name: Cells → ugd_IoData.Cells; sActDate, sActTime → mdHuockt.sActDate, etc. No ambiguous members detected.

ORIGINAL (line 11461): `with asg_Crrt, iCrrt do`
UNRESOLVABLE: Multi-object with — asg_Crrt is TAdvStringGrid and iCrrt is HmdIcutot. Resolution by member name: Cells → asg_Crrt.Cells; sItemCode, sItemValue → iCrrt.sItemCode, etc. No ambiguous members detected.

ORIGINAL (line 11564): `with asg_Crrt, iCrrt do`
UNRESOLVABLE: Multi-object with — asg_Crrt is TAdvStringGrid and iCrrt is HmdIcutot. Resolution as above.

ORIGINAL (line 11633): `with asg_Crrt, iCrrt do`
UNRESOLVABLE: Multi-object with — asg_Crrt is TAdvStringGrid and iCrrt is HmdIcutot. Resolution as above.

ORIGINAL (line 11688): `with iCrect do`
RESOLVED: iCrect is HmdIcutot. Members accessed: sPatNo[0], sAdmDate[0] → iCrect.sPatNo[0], etc.

## Shared State

| Variable | Type | Read by | Written by |
|----------|------|---------|------------|
| MDN110FM | TMDN110FM | External callers (MDN110UP, MDN110UQ, etc.) | FormCreate (implicit), FormDestroy (set to Nil) |
| sl_CodeList | TStringList | SetCodeList, GetCodeList, grid display methods | SetCodeList, FormCreate |
| sl_TimeList | TStringList | SetTimeList, GetTimeList, grid display methods | SetTimeList, FormCreate |
| l_CodeItem | TList | asg_IcuMonGetEditorType, GetAllItems, grid methods | SetCodeList, GetCodeList |
| l_SaveItem | TList | SetSaveList, bbt_MoniSaveClick | GetSaveList, SetSaveList |
| gNowRow | Integer | asg_IcuMonSelectCell, asg_IcuMonClickCell | asg_IcuMonSelectCell |
| gNowCol | Integer | asg_IcuMonSelectCell, asg_IcuMonClickCell | asg_IcuMonSelectCell |
| gMF24Row | Integer | Multiple grid methods | Grid navigation methods |
| gMF24Col | Integer | Multiple grid methods | Grid navigation methods |
| gCrrtDate | String | CRRT methods | CrrtnMaxData |
| FsKoihaPrtyn | String | Print methods | External caller via property |
| saveCheck | Boolean | bbt_MoniSaveClick | asg_IcuMonKeyPress, asg_IcuMonEditingDone |
| pv_SComReport | HSComReport | AutoScanPrint_New | External caller via property |
| pv_Patsect | String | AutoScanPrint_New | External caller via property |
| pv_Meddate | String | AutoScanPrint_New | External caller via property |
| pv_Reptid | String | AutoScanPrint_New | External caller via property |
| P_PatNo | String | Most methods | External caller via property, SelectPatInfo |
| P_PatName | String | SetPatInfo, display methods | External caller via property, SelectPatInfo |
| P_AdmDate | String | Most middleware calls | External caller via property, SelectPatInfo |
| P_WardNo | String | GetPatList, middleware calls | External caller via property, SelectPatInfo |
| P_RoomNo | String | Display methods | External caller via property |
| G_SetFlag | String | CheckFormSet, FormShow | CheckFormSet |
| P_RgtDate | String | Date navigation, middleware calls | External caller, dtp_RgtDateChange |
| P_PatFlag | String | FormShow (UI mode control) | External caller via property |
| P_NicuFlag | String | FormShow (NICU/SU/ICU branching) | External caller via property |
| G_EmrYn | String | Print methods | External caller |
| G_EmrPrtIdx | Integer | Print methods | External caller |
| ActCont | String | External callers | Action insertion methods |

## Custom Destructors

N/A -- TMDN110FM does not override Destroy. Cleanup is done in FormClose event handler (lines 661-689): frees sl_CodeList, sl_TimeList, l_CodeItem, l_SaveItem, closes cds_SaveItem and cds_MonItem, sets Action := caFree.

## Memory Management Patterns

- **Explicit try-finally-Free**: Used extensively for middleware objects (HmdIcpatt, HmdIcutot, HmdNrrect, etc.). Pattern: Create → try → use → finally → Free. See lines 947-1180, 2706-2941, etc.
- **Owner-freed (TComponent.Owner)**: Form components (grids, buttons, panels) are owned by the form and freed automatically.
- **FormClose cleanup**: sl_CodeList.Free, sl_TimeList.Free, l_CodeItem.Free, l_SaveItem.Free, cds_SaveItem.Close, cds_MonItem.Close at lines 661-689.
- **FormDestroy nil-out**: MDN110FM := Nil at line 694 to prevent dangling references.
- **TList without element cleanup**: l_CodeItem and l_SaveItem hold HmdIcutot pointers but the TList.Free does not free the contained objects. ASSUMPTION: HmdIcutot objects in l_CodeItem are freed elsewhere or are leaked. This is a potential memory leak pattern.

## Assumptions

1. HmdIcpatt, HmdIcutot, HmdNrrect, HmdInsamt, HmdIochkt, HmdHuockt, HmdWrkLst, HmdTemplt, HmdNbabyt, HmdPatInf, HmdPdiagt are all middleware wrapper classes defined in MDCLASS1.pas (not in this repo). Their array fields (sPatNo[], sAdmDate[], etc.) are populated by Tuxedo service calls.
2. The multi-object `with` blocks (lines 2749, 3173, 3793, 7145, 10419, 10592, 10713, 11461, 11564, 11633) are resolvable because the grid (TAdvStringGrid/TUltraGrid) and middleware (HmdIcutot/HmdIochkt/etc.) types have non-overlapping member names.
3. l_CodeItem and l_SaveItem TList objects may leak their contained HmdIcutot pointers when the list is freed without iterating and freeing each element.
4. The constants C_STARTTM='0601' and C_ENDTM='0600' define a 24-hour monitoring cycle from 06:01 to 06:00 next day.
5. C_MONIPRD=12 means the default monitoring period is 12 entries.
6. Duty shift boundaries: Day=14:00, Evening=22:00, Night=06:00.
