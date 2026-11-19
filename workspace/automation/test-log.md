# Test log -- SCS3.5

<!-- The answers are worked out by hand, on paper, BEFORE the script runs. Expected first, actual after, edge case last. -->
<!-- Pass or fail: the result now (fail -> pass after a patch is fine). Where a test fails: trace it, change the one line by hand, run again, commit the patch on its own, and write its line and commit here. -->

| Case | Input rows (made up) | Expected (by hand, before the run) | Actual (after the run) | Pass or fail | Patch (line, commit) |
|---|---|---|---|---|---|
| Test 1 | DASHBOARD A12:C15: Sugar 4 REORDER; Bread 15 OK; Milk 45 OK; Rice 5 REORDER | REMINDERS should contain Sugar (4, REORDER) and Rice (5, REORDER) | Sugar and Rice appeared with REORDER status | PASS | No patch needed |
| Test 2 | RECORD: October 2026 OUT records with sales 200 for 2 units and 450 for 3 units; September OUT sales 400 for 4 units; October IN sales 0 for 5 units | October OUT records only: total sales = 650; units sold = 5 | MONTHLY REPORT wrote October 2026, total sales = 650, units sold = 5 | PASS | Fixed month index and OUT filter at lines 35, 48, commit 2a540b0 |
| Edge case | INTAKE: Sugar, quantity 0; Rice, quantity -2 | Both quantities should produce INVALID ENTRY | Both rows wrote INVALID ENTRY in column D without overwriting valid dates | PASS | Validated `quantity > 0` at line 91, commit 2a540b0 |
| Second edge case (optional, SGL menu) | INTAKE: Blank item with quantity 5; valid item with text quantity "abc" | Blank item ignored; text quantity writes INVALID ENTRY | Blank row skipped at line 89; text quantity wrote INVALID ENTRY | PASS | No patch needed |
| Partner as a careless owner | Partner edited header row 1 and column E notes on INTAKE | Script ignores row 1 and column > 2 without adding dates or status | Row 1 and column E untouched | PASS | Guarded at line 84 |
| Re-run in front of the trainer | Re-ran checkStock, generateMonthlyReport, and onEdit on test copy | All expected outputs match hand-calculated values | Verified live in Apps Script editor and sheet | PASS | No patch needed |
