# Test log -- SCS3.5

<!-- The answers are worked out by hand, on paper, BEFORE the script runs. Expected first, actual after, edge case last. -->
<!-- Pass or fail: the result now (fail -> pass after a patch is fine). Where a test fails: trace it, change the one line by hand, run again, commit the patch on its own, and write its line and commit here. -->

| Case | Input rows (made up) | Expected (by hand, before the run) | Actual (after the run) | Pass or fail | Patch (line, commit) |
|---|---|---|---|---|---|
| Test 1 | DASHBOARD A12:C15: Sugar 4 REORDER; Bread 15 OK; Milk 45 OK; Rice 5 REORDER | REMINDERS should contain Sugar (4, REORDER) and Rice (5, REORDER) | Sugar and Rice appeared with REORDER status | PASS | No patch needed |
| Test 2 | RECORD: October 2026 OUT records with sales 200 for 2 units and 450 for 3 units; September OUT sales 400 for 4 units; October IN sales 0 for 5 units | October OUT records only: total sales = 650; units sold = 5 | Not run yet | Not run | Not applicable yet |
| Edge case | INTAKE: Sugar, quantity 0; Rice, quantity -2 | Both quantities should produce INVALID ENTRY | Not run yet | Not run | Not applicable yet |
| Second edge case (optional, SGL menu) | Not selected yet | Not calculated yet | Not run yet | Not run | Not applicable yet |
| Partner as a careless owner | Not tested yet | Not calculated yet | Not run yet | Not run | Not applicable yet |
| Re-run in front of the trainer | Not tested yet | Not calculated yet | Not run yet | Not run | Not applicable yet |
