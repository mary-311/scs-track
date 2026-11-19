# Method note -- SCS3.5

## 1. What I set out to do
Build and verify a Google Apps Script automation on a safe test copy of the shop workbook to flag reorder items, summarize October 2026 outgoing sales, and validate new intake entries on edit.

## 2. What I did, in order
Drafted and got the one-page spec initialled, made a copy of the spreadsheet with made-up rows, generated the script with AI, read and explained every line in the reading log, tested all functions against hand-calculated expected answers, and verified the nine breaks.

## 3. What went wrong, and how I fixed it
Running `onEdit(e)` directly from the Apps Script editor threw `TypeError: Cannot read properties of undefined (reading 'range')`, and an initial reporting syntax issue failed validation; I traced `e.range` to trigger-only execution, fixed the syntax at commit `2a540b0`, and tested by editing cells directly on the `INTAKE` sheet.

## 4. How long it took, against the plan
It took about 55 minutes from initialled spec to completing the reading log, test runs, and break checks, which was 10 minutes over plan due to line-by-line documentation.

## 5. One lesson for the next person
Never run an `onEdit(e)` trigger function with the editor's Run button—always test it by editing a cell in the sheet, and always work out expected test results on paper before running the code.

## 6. What I might be wrong about, and how I would find out
I might be wrong about whether the owner's real RECORD sheet has more than 1,000 rows or stores dates as text strings instead of Date objects; I would find out by checking the row count and cell formatting on the owner's real sheet before deploying the script.
