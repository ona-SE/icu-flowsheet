# MDN110UO — Method Inventory (Part 1: Methods 1-50)

## Unit Purpose

ICU information entry/edit form with multi-tab layout for patient data entry, dynamic component loading via FindComponent, and print report generation.

## Method Inventory

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 1 | bbt_CloseClick | published | (Sender: TObject) | 819-823 | Close | LOW |
| 2 | FormDestroy | published | (Sender: TObject) | 824-828 | MDN110FO := Nil | LOW |
| 3 | FormClose | published | (Sender: TObject; var Action: TCloseAction) | 829-833 | Action := caFree | LOW |
| 4 | FormShow | published | (Sender: TObject) | 834-883 | GetPatInfo, GetIcuInfo, tab setup, label population | HIGH |
| 5 | GetPatInfo | private | () | 884-931 | HmdPatinf.Create, HmdPatinf.ListPatbat, patient info population | HIGH |
| 6 | GetIcuInfo | private | (patno: String, Admdate: String): Boolean | 932-981 | HmdIcuinf.Create, HmdIcuinf.getIcuinflist, FindComponent-based field population | HIGH |
| 7 | GetIcuSelect | private | () | 982-1052 | HmdIcuinf.Create, HmdIcuinf.getIcuinfwt, FindComponent-based field save | HIGH |
| 8 | pc_ICUChange | published | (Sender: TObject) | 1053-1058 | Tab change | LOW |
| 9 | B0201_1Click | published | (Sender: TObject) | 1059-1072 | Field click handler | LOW |
| 10 | B0201_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1073-1081 | Field key handler | LOW |
| 11 | B0201_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1082-1092 | Field key handler | LOW |
| 12 | B0203_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1093-1101 | Field key handler | LOW |
| 13 | B0206_2Click | published | (Sender: TObject) | 1102-1115 | Field click handler | LOW |
| 14 | B0206_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1116-1126 | Field key handler | LOW |
| 15 | B0207_2Click | published | (Sender: TObject) | 1127-1146 | Field click handler with validation | LOW |
| 16 | B0207_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1147-1165 | Field key handler with validation | LOW |
| 17 | C0201_6Click | published | (Sender: TObject) | 1166-1179 | Checkbox click handler | LOW |
| 18 | B0208_2Click | published | (Sender: TObject) | 1180-1193 | Field click handler | LOW |
| 19 | B0208_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1194-1204 | Field key handler | LOW |
| 20 | B0210_2Click | published | (Sender: TObject) | 1205-1224 | Field click handler with validation | LOW |
| 21 | B0210_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1225-1242 | Field key handler with validation | LOW |
| 22 | C0210_5Click | published | (Sender: TObject) | 1243-1256 | Checkbox click handler | LOW |
| 23 | B0211_2Click | published | (Sender: TObject) | 1257-1276 | Field click handler with validation | LOW |
| 24 | B0211_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1277-1294 | Field key handler with validation | LOW |
| 25 | C0211_5Click | published | (Sender: TObject) | 1295-1308 | Checkbox click handler | LOW |
| 26 | B0212_2Click | published | (Sender: TObject) | 1309-1328 | Field click handler with validation | LOW |
| 27 | B0212_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1329-1346 | Field key handler with validation | LOW |
| 28 | C0212_5Click | published | (Sender: TObject) | 1347-1360 | Checkbox click handler | LOW |
| 29 | B0213_2Click | published | (Sender: TObject) | 1361-1382 | Field click handler with validation | LOW |
| 30 | B0213_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1383-1403 | Field key handler with validation | LOW |
| 31 | C0213_7Click | published | (Sender: TObject) | 1404-1417 | Checkbox click handler | LOW |
| 32 | B0301_2Click | published | (Sender: TObject) | 1418-1434 | Field click handler | LOW |
| 33 | B0301_2KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1435-1450 | Field key handler | LOW |
| 34 | B0407_1Click | published | (Sender: TObject) | 1451-1464 | Field click handler | LOW |
| 35 | B0407_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1465-1476 | Field key handler | LOW |
| 36 | B0501_1Click | published | (Sender: TObject) | 1477-1495 | Field click handler | LOW |
| 37 | B0805_1Click | published | (Sender: TObject) | 1496-1519 | Field click handler | LOW |
| 38 | B0808_1Click | published | (Sender: TObject) | 1520-1535 | Field click handler | LOW |
| 39 | B0901_1Click | published | (Sender: TObject) | 1536-1554 | Field click handler | LOW |
| 40 | B0901_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1555-1572 | Field key handler | LOW |
| 41 | C0901_5Click | published | (Sender: TObject) | 1573-1586 | Checkbox click handler | LOW |
| 42 | C0901_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1587-1598 | Checkbox key handler | LOW |
| 43 | B0902_3Click | published | (Sender: TObject) | 1599-1617 | Field click handler | LOW |
| 44 | B0902_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1618-1635 | Field key handler | LOW |
| 45 | C0902_5Click | published | (Sender: TObject) | 1636-1649 | Checkbox click handler | LOW |
| 46 | C0902_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1650-1661 | Checkbox key handler | LOW |
| 47 | B0903_3Click | published | (Sender: TObject) | 1662-1680 | Field click handler | LOW |
| 48 | B0903_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1681-1698 | Field key handler | LOW |
| 49 | C0903_5Click | published | (Sender: TObject) | 1699-1712 | Checkbox click handler | LOW |
| 50 | C0903_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1713-1724 | Checkbox key handler | LOW |
# MDN110UO — Method Inventory (Part 2: Methods 51-91)

## Method Inventory (continued)

| # | Method | Visibility | Signature | Lines | Calls | Complexity |
|---|--------|------------|-----------|-------|-------|------------|
| 51 | B0904_3Click | published | (Sender: TObject) | 1725-1743 | Field click handler | LOW |
| 52 | B0904_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1744-1761 | Field key handler | LOW |
| 53 | C0904_5Click | published | (Sender: TObject) | 1762-1775 | Checkbox click handler | LOW |
| 54 | C0904_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1776-1787 | Checkbox key handler | LOW |
| 55 | B0905_3Click | published | (Sender: TObject) | 1788-1806 | Field click handler | LOW |
| 56 | B0905_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1807-1824 | Field key handler | LOW |
| 57 | C0905_5Click | published | (Sender: TObject) | 1825-1838 | Checkbox click handler | LOW |
| 58 | C0905_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1839-1850 | Checkbox key handler | LOW |
| 59 | B0906_3Click | published | (Sender: TObject) | 1851-1869 | Field click handler | LOW |
| 60 | B0906_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1870-1887 | Field key handler | LOW |
| 61 | C0906_5Click | published | (Sender: TObject) | 1888-1901 | Checkbox click handler | LOW |
| 62 | C0906_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1902-1913 | Checkbox key handler | LOW |
| 63 | B0908_3Click | published | (Sender: TObject) | 1914-1932 | Field click handler | LOW |
| 64 | B0908_3KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1933-1950 | Field key handler | LOW |
| 65 | C0908_5Click | published | (Sender: TObject) | 1951-1964 | Checkbox click handler | LOW |
| 66 | C0908_5KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 1965-1976 | Checkbox key handler | LOW |
| 67 | B1001_2Click | published | (Sender: TObject) | 1977-2000 | Field click handler | LOW |
| 68 | dtp_Item01Change | published | (Sender: TObject) | 2001-2005 | Date picker change | LOW |
| 69 | dtp_Item02Change | published | (Sender: TObject) | 2006-2010 | Date picker change | LOW |
| 70 | bbt_AddClick | published | (Sender: TObject) | 2011-2174 | HmdIcuinf.Create, HmdIcuinf.getIcuinfwt, validation, save all fields | HIGH |
| 71 | B0203_1Change | published | (Sender: TObject) | 2175-2185 | Field change handler | LOW |
| 72 | B0204_1Change | published | (Sender: TObject) | 2186-2196 | Field change handler | LOW |
| 73 | bbt_DeleteClick | published | (Sender: TObject) | 2197-2244 | HmdIcuinf.Create, delete ICU info, confirmation dialog | HIGH |
| 74 | Clear_Screen | private | () | 2245-2300 | Clear all form fields | HIGH |
| 75 | bbt_PrintClick | published | (Sender: TObject) | 2301-2368 | MDN110UO_P01 form creation, QRLabel population, report preview/print | HIGH |
| 76 | B0001_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2369-2375 | Field key handler | LOW |
| 77 | B0002_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2376-2382 | Field key handler | LOW |
| 78 | B0004_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2383-2389 | Field key handler | LOW |
| 79 | B0003_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2390-2396 | Field key handler | LOW |
| 80 | B0005_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2397-2403 | Field key handler | LOW |
| 81 | B0006_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2404-2410 | Field key handler | LOW |
| 82 | B0007_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2411-2417 | Field key handler | LOW |
| 83 | B0008_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2418-2424 | Field key handler | LOW |
| 84 | B0009_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2425-2431 | Field key handler | LOW |
| 85 | B0010_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2432-2438 | Field key handler | LOW |
| 86 | B0011_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2439-2445 | Field key handler | LOW |
| 87 | B0012_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2446-2452 | Field key handler | LOW |
| 88 | B0013_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2453-2459 | Field key handler | LOW |
| 89 | B0401_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2460-2466 | Field key handler | LOW |
| 90 | B0402_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2467-2473 | Field key handler | LOW |
| 91 | B0403_1KeyDown | published | (Sender: TObject; var Key: Word; Shift: TShiftState) | 2474-2487 | Field key handler | LOW |

VALIDATION: Source has 91 implementations, inventory has 91 rows. Delta = 0%.

## Event Chain Map

```
FormCreate (implicit)
  → FormShow (line 834) → GetPatInfo → GetIcuInfo → field population
  → [User edits fields] → B{NNNN}_{N}Click/KeyDown handlers → field validation
  → [User clicks checkbox] → C{NNNN}_{N}Click handlers → checkbox toggle
  → [User clicks Add] → bbt_AddClick (line 2011) → GetIcuSelect → HmdIcuinf save
  → [User clicks Delete] → bbt_DeleteClick (line 2197) → HmdIcuinf delete
  → [User clicks Print] → bbt_PrintClick (line 2301) → MDN110UO_P01 report
  → [User clicks Close] → bbt_CloseClick (line 819) → Close
FormClose (line 829) → Action := caFree
FormDestroy (line 824) → MDN110FO := Nil
```

## Shared State

| Variable | Type | Initialized in | Read by | Written by |
|----------|------|----------------|---------|------------|
| MDN110FO | TMDN110FO | FormCreate (implicit) | MDN110UO_P01 (print data) | FormDestroy (set to Nil) |

## Middleware Contract Summary

| Class | Method | Input Params (name: type) | Output Shape | Error Convention |
|-------|--------|--------------------------|--------------|-----------------| 
| HmdPatinf | ListPatbat | Cond: String, PatNo: String, PatName: String | Arrays: sPatName[], sSex[], sBirtDate[], sAdmDate[], sMedDept[] | Returns -1 on error, 0 on no data |
| HmdIcuinf | getIcuinflist | sFlag1: String, sType1: String (PatNo), sType2: String (AdmDate), sType3: String (WardNo), sType4: String (filter), G_LOCATE: String | ICU info field arrays | Returns -1 on error, 0 on no data |
| HmdIcuinf | getIcuinfwt | sFlag1: String, sType1-sType5: String | Integer (result code) | Returns -1 on error |

## Third-Party API Surface

| Library | Class | Methods Used | Purpose |
|---------|-------|-------------|---------|
| UltraGrid | TUltraGrid | Cells[], RowCount | Patient list grid |
| QuickReport | TQuickRep | Preview, Print | Print report (via MDN110UO_P01) |

## Repetitive Handler Analysis

TEMPLATE GROUP 1: B{NNNN}_{N}KeyDown → handles Enter key to move focus to next field, handles Escape to close
TEMPLATE LINES: 2369-2375 (representative: B0001_1KeyDown)

| Method | Field | Deviates? | Deviation |
|--------|-------|-----------|-----------|
| B0001_1KeyDown | B0001_1 | No | |
| B0002_1KeyDown | B0002_1 | No | |
| B0003_1KeyDown | B0003_1 | No | |
| B0004_1KeyDown | B0004_1 | No | |
| B0005_1KeyDown | B0005_1 | No | |
| B0006_1KeyDown | B0006_1 | No | |
| B0007_1KeyDown | B0007_1 | No | |
| B0008_1KeyDown | B0008_1 | No | |
| B0009_1KeyDown | B0009_1 | No | |
| B0010_1KeyDown | B0010_1 | No | |
| B0011_1KeyDown | B0011_1 | No | |
| B0012_1KeyDown | B0012_1 | No | |
| B0013_1KeyDown | B0013_1 | No | |
| B0201_1KeyDown | B0201_1 | No | |
| B0201_3KeyDown | B0201_3 | No | |
| B0203_1KeyDown | B0203_1 | No | |
| B0206_2KeyDown | B0206_2 | No | |
| B0207_2KeyDown | B0207_2 | YES | Additional validation for numeric range |
| B0208_2KeyDown | B0208_2 | No | |
| B0210_2KeyDown | B0210_2 | YES | Additional validation for numeric range |
| B0211_2KeyDown | B0211_2 | YES | Additional validation for numeric range |
| B0212_2KeyDown | B0212_2 | YES | Additional validation for numeric range |
| B0213_2KeyDown | B0213_2 | YES | Additional validation for numeric range |
| B0301_2KeyDown | B0301_2 | No | |
| B0401_1KeyDown | B0401_1 | No | |
| B0402_1KeyDown | B0402_1 | No | |
| B0403_1KeyDown | B0403_1 | No | |
| B0407_1KeyDown | B0407_1 | No | |
| B0901_1KeyDown | B0901_1 | No | |
| B0902_3KeyDown | B0902_3 | No | |
| B0903_3KeyDown | B0903_3 | No | |
| B0904_3KeyDown | B0904_3 | No | |
| B0905_3KeyDown | B0905_3 | No | |
| B0906_3KeyDown | B0906_3 | No | |
| B0908_3KeyDown | B0908_3 | No | |

DEVIATIONS DETAIL:
- B0207_2KeyDown (line 1147): Validates numeric input range before allowing focus change. 19 lines vs typical 7 lines.
- B0210_2KeyDown (line 1225): Validates numeric input range. 18 lines vs typical 7 lines.
- B0211_2KeyDown (line 1277): Validates numeric input range. 18 lines vs typical 7 lines.
- B0212_2KeyDown (line 1329): Validates numeric input range. 18 lines vs typical 7 lines.
- B0213_2KeyDown (line 1383): Validates numeric input range. 21 lines vs typical 7 lines.

TEMPLATE GROUP 2: C{NNNN}_{N}Click → checkbox click toggles related field visibility/enabled state
TEMPLATE LINES: 1166-1179 (representative: C0201_6Click)

| Method | Checkbox | Deviates? | Deviation |
|--------|----------|-----------|-----------|
| C0201_6Click | C0201_6 | No | |
| C0210_5Click | C0210_5 | No | |
| C0211_5Click | C0211_5 | No | |
| C0212_5Click | C0212_5 | No | |
| C0213_7Click | C0213_7 | No | |
| C0901_5Click | C0901_5 | No | |
| C0902_5Click | C0902_5 | No | |
| C0903_5Click | C0903_5 | No | |
| C0904_5Click | C0904_5 | No | |
| C0905_5Click | C0905_5 | No | |
| C0906_5Click | C0906_5 | No | |
| C0908_5Click | C0908_5 | No | |
