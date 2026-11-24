## Overkill test
1. How many people type into it? One or two who trust each other.
2. How many rows a month? Tens to a few hundred.
3. Does it need to talk to anything else? Nothing, or statements read by hand.
4. What happens if a number is wrong? The owner adds a correcting row instead of overwriting history.
5. Who supports it next year? The owner, using the printed card left in the client folder.

Verdict: Sheets.  Pattern: inventory.  Because: A single kiosk owner with a phone or laptop tracking dozens to a few hundred stock events a month benefits from a structured three-tab sheet without paying for a server, software vendor, or ongoing developer support.

## Validation
| column | rule | the garbage I typed | refused? |
| --- | --- | --- | --- |
| Records!Item | Dropdown from Lists!A:A, Reject input | UnknownItemXYZ | Yes |
| Records!Date | Valid date | NotADate | Yes |
| Records!Quantity | Number greater than 0 | -3 | Yes |

## Protection
| range | who can edit | warning or restriction | entry columns still open? |
| --- | --- | --- | --- |
| Dashboard | Only you (owner/builder) | Restriction | Yes, entry happens on Records |
| Records!F:F (Line total formula) | Only you (owner/builder) | Restriction | Yes, date/item/in-out/qty/price/note remain open |

## AI receipts
| the ask (headings only) | the formula | what I changed | the hand check (the log row) |
| --- | --- | --- | --- |
| Tab names Lists, Records, Dashboard; columns Date, Item, In or out, Quantity, Unit price, Line total; summarize monthly out total | =SUMIFS(Records!F:F, Records!C:C, "out", Records!A:A, ">="&EOMONTH(B2,-1)+1, Records!A:A, "<="&EOMONTH(B2,0)) | Verified cell reference for As of date in B2 and whole-column ranges | Row 2 |

## Break the books
| the attack | what I said would happen | what happened | held or the fix |
| --- | --- | --- | --- |
| Item name not on Lists | Refused by dropdown validation | Refused with validation error | Held |
| Quantity of -3 | Refused by positive-number rule | Refused with validation error | Held |
| Date next year | Accepted if valid date rule only | Accepted as a valid date | Held (expected; noted on owner card) |
| Blank amount on new row | Accepted because rule checks typed values | Row added with blank amount | Held (expected; noted on owner card) |
| Number typed over a formula | Refused on protected range/column | Refused for non-owner account | Held |
| Delete a row from middle of Records | Entry cells clear or protected cell blocks | Cleared or blocked per protection | Fix: restore via Version history if needed |
| Change a price in Lists | Past sales stay unchanged if price stored in Records | Historical totals stayed consistent | Held by shape (unit price kept in Records) |
