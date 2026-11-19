# Reading log -- SCS3.5

Script: workspace/automation/kiosk-automation.gs
Read to the last line before the first run: yes / no
Label: AI-assisted, directed by belisha -- the FS5a label, the same words as the receipt log

<!-- Every line of the script in your own words, BEFORE the first run.  One row per line, or a range such as 12-14 -->
<!-- when the lines are one statement.  Which word: variable, sequence, condition, loop, trigger.  Blank lines,  -->
<!-- comment lines and lines that are only a closing bracket need no row.  A line you cannot say is rewritten in   -->
<!-- words you can, or deleted.  If a patch adds a line, renumber the rows below it.                               -->

| Line no. | The line, first words | In my own words | Which word |
|---|---|---|---|
| 5 | `function checkStock()` | Starts a function that checks which products need restocking. | function |
| 6 | `const ss =` | Gets the spreadsheet currently being used. | variable |
| 7 | `const dashboard =` | Finds the sheet called DASHBOARD. | variable |
| 8 | `const stockData =` | Reads the stock information from cells A12 to C15. | variable |
| 10 | `const lowStockItems =` | Selects only the rows whose status is REORDER. | variable |
| 12 | `let reminders =` | Looks for the REMINDERS sheet. | variable |
| 14 | `if (!reminders)` | Checks whether the REMINDERS sheet is missing. | condition |
| 15 | `reminders = ss.insertSheet` | Creates the REMINDERS sheet if it does not exist. | sequence |
| 18 | `reminders.clearContents()` | Removes old contents from the reminders sheet. | sequence |
| 20 | `reminders.getRange("A1:C1").setValues(` | Selects the heading cells and starts writing their values. | sequence |
| 21 | `[["ITEM", "CURRENT STOCK", "STATUS"]]` | Supplies the three column headings for the reminders sheet. | sequence |
| 24 | `if (lowStockItems.length > 0)` | Checks whether there are any products that need reordering. | condition |
| 25 | `reminders.getRange(2, 1, lowStockItems.length, 3)` | Selects enough cells starting at row 2 for the low-stock items. | sequence |
| 26 | `.setValues(lowStockItems)` | Writes the low-stock item information into the selected cells. | sequence |
| 30 | `function generateMonthlyReport()` | Starts a function that prepares a report for one month. | function |
| 31 | `const ss =` | Gets the active spreadsheet. | variable |
| 32 | `const record =` | Finds the sheet named RECORD. | variable |
| 33 | `const data =` | Reads the records from cells A2 to F1000. | variable |
| 35 | `const reportMonth = 9` | Sets the month number to 9, which represents October in JavaScript. | variable |
| 36 | `const reportYear = 2026` | Sets the report year to 2026. | variable |
| 38 | `const monthName = new Date` | Creates a date using the selected year and month. | variable |
| 39 | `.toLocaleString("en-US"` | Converts the date into a readable month name using the English format. | sequence |
| 41 | `const monthLabel =` | Combines the month name and year into one label. | variable |
| 43 | `const monthlySales = data.filter` | Starts selecting records that match the report conditions. | variable |
| 44 | `row[0] &&` | Checks that the record has a date value. | condition |
| 45 | `typeof row[0].getMonth` | Checks that the date value has a getMonth method. | condition |
| 46 | `row[0].getMonth() === reportMonth` | Checks whether the record belongs to the selected month. | condition |
| 47 | `row[0].getFullYear() === reportYear` | Checks whether the record belongs to the selected year. | condition |
| 48 | `row[2] === "OUT"` | Keeps only records marked as outgoing transactions. | condition |
| 51 | `const totalSales = monthlySales.reduce` | Starts calculating the total sales amount. | variable |
| 52 | `(sum, row) => sum + Number` | Adds each record's sales amount to the running total. | loop |
| 55 | `const unitsSold = monthlySales.reduce` | Starts calculating the total number of units sold. | variable |
| 56 | `(sum, row) => sum + Number` | Adds each record's quantity to the running total. | loop |
| 59 | `let report =` | Looks for the MONTHLY REPORT sheet. | variable |
| 61 | `if (!report)` | Checks whether the report sheet is missing. | condition |
| 62 | `report = ss.insertSheet` | Creates the report sheet if it does not exist. | sequence |
| 65 | `report.clearContents()` | Clears old report contents. | sequence |
| 67 | `report.getRange("A1:C1").setValues(` | Selects the heading cells and starts writing report headings. | sequence |
| 68 | `[["REPORT MONTH", "TOTAL SALES", "UNITS SOLD"]]` | Supplies the three headings for the monthly report. | sequence |
| 71 | `report.getRange("A2:C2").setValues(` | Selects the cells where the report results will be written. | sequence |
| 72 | `[[monthLabel, totalSales, unitsSold]]` | Supplies the month, total sales and units sold as the report results. | sequence |
| 76 | `function onEdit(e)` | Starts a function that responds when someone edits the spreadsheet. | trigger |
| 77 | `const sheet =` | Identifies the sheet where the edit happened. | variable |
| 79 | `if (sheet.getName() !== "INTAKE")` | Stops the function if the edit was not on the INTAKE sheet. | condition |
| 81 | `const row =` | Gets the row number that was edited. | variable |
| 82 | `const column =` | Gets the column number that was edited. | variable |
| 84 | `if (row === 1 || column > 2)` | Ignores the heading row and edits outside the first two columns. | condition |
| 86 | `const item =` | Reads the item entered in column A. | variable |
| 87 | `const quantity =` | Reads the quantity entered in column B. | variable |
| 89 | `if (item === "" || quantity === "")` | Stops if the item or quantity is empty. | condition |
| 91 | `const isValid =` | Checks that the quantity is a number greater than zero. | variable |
| 93 | `const dateCell =` | Identifies the date cell in column C. | variable |
| 95 | `if (dateCell.getValue() === "")` | Checks whether the date cell is empty. | condition |
| 96 | `dateCell.setValue(new Date())` | Adds the current date if no date has been entered. | sequence |
| 97 | `dateCell.setNumberFormat` | Displays the date in day/month/year format. | sequence |
| 100 | `const checkCell =` | Identifies the checking-status cell in column D. | variable |
| 102 | `if (isValid)` | Checks whether the quantity passed validation. | condition |
| 103 | `checkCell.setValue("OK")` | Writes OK when the entry is valid. | sequence |
| 104 | `} else {` | Provides the alternative action when the quantity is not valid. | condition |
| 105 | `checkCell.setValue("INVALID ENTRY")` | Writes INVALID ENTRY when the quantity is invalid. | sequence |
