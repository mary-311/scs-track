# The nine breaks -- SCS3.5

<!-- Checked with the script open.  Every answer is a line number or a patch -- never "it should be fine".        -->
<!-- Break 8 is checked on the trigger settings: what fires it, and how often.  Break 9 is caught by the test log. -->

| # | Break | Cannot happen because ... (line) | Found -- patched at (line, commit) |
|---|---|---|---|
| 1 | The header row counted | Cannot happen because line 8 (`A12:C15`), line 33 (`A2:F1000`), and line 84 (`if (row === 1 || column > 2) return;`) exclude header rows | |
| 2 | The wrong tab | Cannot happen because line 7 (`getSheetByName("DASHBOARD")`), line 32 (`getSheetByName("RECORD")`), and line 79 (`sheet.getName() !== "INTAKE"`) target exact tab names | |
| 3 | The number read as text | Cannot happen because line 52 (`Number(row[5] || 0)`), line 56 (`Number(row[3] || 0)`), and line 91 (`typeof quantity === "number"`) enforce numeric conversion and type checks | |
| 4 | The boundary | Cannot happen because line 8 (`A12:C15`), line 33 (`A2:F1000`), and line 91 (`quantity > 0`) strictly enforce range and positive-number boundaries | |
| 5 | The overwrite | Cannot happen because line 18 and line 65 only clear generated output sheets (`REMINDERS`, `MONTHLY REPORT`), while line 95 (`if (dateCell.getValue() === "")`) preserves existing intake dates | |
| 6 | The invented piece | Cannot happen because lines 5-107 use only standard SpreadsheetApp methods verified by running `checkStock`, `generateMonthlyReport`, and `onEdit` on the test sheet | |
| 7 | The silent assumption | Cannot happen because line 14 (`if (!reminders)`), line 61 (`if (!report)`), and lines 44-45 (`row[0] && typeof row[0].getMonth === "function"`) handle missing tabs and blank/non-date cells safely | |
| 8 | The trigger that runs too often | Cannot happen because simple `onEdit(e)` at line 76 only fires on manual user cell edits (not script edits or time triggers) and exits immediately at line 79 and line 84 if not `INTAKE` columns A–B | |
| 9 | The confident wrong answer | | Found -- patched at lines 35 and 48, commit 2a540b0 (caught by Test 2 in test-log.md where month index 9 = October and `row[2] === "OUT"` isolate October outgoing sales) |
