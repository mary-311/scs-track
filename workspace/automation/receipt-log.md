# AI receipt log -- SCS3.5

Label: AI-assisted, directed by belisha
Tool: Gemini
Spec initialled on (YYYY-MM-DD): 2026-11-19
First prompt sent on (YYYY-MM-DD HH:MM): 2026-11-19 15:15

## The one prompt, word for word
Write Google Apps Script on Google Sheets with a comment on every line for a small shop workbook with three tabs:
1. DASHBOARD: read items in A12:C15 (columns: ITEM, CURRENT STOCK, STATUS). Copy rows where STATUS is "REORDER" into a REMINDERS tab with headers ITEM, CURRENT STOCK, STATUS.
2. RECORD: read rows in A2:F1000 (columns: DATE, ITEM, TYPE, QTY, UNIT PRICE, TOTAL). Filter for October 2026 rows where TYPE is "OUT", calculate total sales and total units sold, and write them to a MONTHLY REPORT tab with headers REPORT MONTH, TOTAL SALES, UNITS SOLD.
3. INTAKE: using an onEdit(e) trigger on rows below row 1 when columns A or B are edited (columns: ITEM, QTY, DATE, CHECK), validate that QTY is a number greater than 0. Fill column C with today's date in dd/MM/yyyy format only if empty, and write "OK" or "INVALID ENTRY" in column D.
Use only made-up sample data and include no real customer names, phone numbers, balances, or addresses.

## What came back, and what I changed by hand
The draft returned all three functions (`checkStock`, `generateMonthlyReport`, `onEdit`). By hand, I added the `AI-assisted, directed by belisha` header label at the top, verified that `reportMonth = 9` maps to October (0-indexed months in JavaScript), ensured `dateCell.getValue() === ""` prevents overwriting existing intake dates, and stripped inline clutter so each line matched my reading log.

## Iteration -- only if the draft missed a line of the spec (which line)
None — all three functions matched the initialled one-page spec on the first pass after minor syntax cleanup in commit 2a540b0.

## The debug move -- one real error: the message pasted whole, what my trace said first, what the tool said
Error: `TypeError: Cannot read properties of undefined (reading 'range')` when running `onEdit` manually from the editor Run button. My trace showed line 77 (`const sheet = e.range.getSheet();`) expects an event object `e` passed automatically by Google Sheets when a cell is edited, which is undefined during a manual editor run. Testing by actually editing cell B2 on the `INTAKE` tab triggered `onEdit(e)` with a valid event object and resolved the error.
