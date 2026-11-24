# Four-Checks Audit

Run all four on every AI-built piece before a client sees it.  Write what you found, not what you hoped.
'Clean' is allowed only with the evidence beside it: the command you ran and what it printed, or the
page you read and the date you read it.  One section per piece; add a new piece at the bottom each time.

## Piece 1: the stock tool (workspace/stock-tools)

### Auth
Looked for: Hardcoded API keys, tokens, or secrets in tracked files and git history, and missing environment-variable handling.
Found: Hardcoded demo key LLDEMO-SMS-REDACTED in send-sms.js on lines 9 and 14, and present in commit 889263c.
Evidence: git grep -n -i key printed send-sms.js:9 and send-sms.js:14; git log --oneline -S "LLDEMO-SMS" printed 889263c (HEAD -> main) SCS3.6 starting state: stock tool and cards; node send-sms.js stock-export.csv --dry-run | head -1 printed key=LLDEMO-SMS-REDACTED.

### Edge cases
Ugly inputs, written before trying them: Blank stock count, comma or quotes inside a field, boundary reorder equality, Ng'Ombe Salt Lick, ampersand (&) in text, zero stock.
Found: parseCsv splits on commas without handling quotes, shifting columns on index 2, and buildSmsUrl concatenates raw text without encoding &, truncating text after &. Also reorderList uses < instead of <= for items at reorder threshold.
Evidence: node -e 'const r = require("./reorder.js"); console.log(r.parseCsv(require("fs").readFileSync("stock-export.csv", "utf8"))[2])' printed { Item: '"Nails', Supplier: '3 inch"', 'In stock': 'Hardware wholesaler', 'Reorder at': '4', Unit: '10' }; node -e 'const { buildSmsUrl } = require("./send-sms.js"); console.log(new URL(buildSmsUrl("x", "Nuts & bolts")).searchParams.get("text"))' printed Nuts.

### Wrong versions
Looked for: Node.js version on machine vs required Node version for Object.groupBy (Node 21+) in official Node.js docs.
Found: Machine runs Node v22.22.1, which supports Object.groupBy (introduced in Node 21.0.0 per Node.js docs), though running on Node < 21 would fail with Object.groupBy is not a function.
Evidence: node --version printed v22.22.1; Node.js docs (Object.groupBy added in v21.0.0, checked 2026-11-24).

### Invented libraries
Looked for: Non-existent imports or functions in Node built-ins or external modules.
Found: send-sms.js imports { fetchWithRetry } from "node:http", which does not exist in Node's node:http module.
Evidence: node send-sms.js stock-export.csv printed Could not send: fetchWithRetry is not a function (Node.js node:http docs, checked 2026-11-24).

The one to fix first, and why: Fix the hardcoded key / auth and edge-case parsing/encoding first so sensitive credentials are not in code/URLs and stock/SMS data is not misread or truncated before sending orders.

## Piece 2: my own SCS3.5 script

### Auth
Looked for: Over-broad spreadsheet/Drive permissions and hardcoded credentials or personal/client PII in workspace/automation/kiosk-automation.gs.
Found: Initial run requested broad spreadsheet access until @OnlyCurrentDoc was added; no hardcoded API keys or client PII in workspace/automation/kiosk-automation.gs.
Evidence: SCS3.5 test log and check-scs3.5 receipt (SCS3.5-2026-11-20_1035.txt) showing @OnlyCurrentDoc patch and PASS 5 (no email/phone/sheet export in workspace/automation).

### Edge cases
Ugly inputs, written before trying them: Blank intake item, negative or zero quantity (-4, 0), edit on column D, header row (row 1), and lowercase/padded " reorder " status.
Found: Script ignores row === 1 and edits past column B, stamps date and INVALID ENTRY on invalid/non-positive quantities, and leaves existing dates in column C intact.
Evidence: SCS3.5 test log and breaks check (PASS 9 and PASS 10 in SCS3.5-2026-11-20_1035.txt).

### Wrong versions
Looked for: Google Apps Script V8 runtime compatibility and syntax validity.
Found: Syntax and runtime checks passed on Apps Script / node --check v22.22.1 with no Node 21-only APIs used.
Evidence: node --check workspace/automation/kiosk-automation.gs and check-scs3.5 receipt (PASS 3 in SCS3.5-2026-11-20_1035.txt, 2026-11-20).

### Invented libraries
Looked for: Any non-existent Apps Script services, helpers, or unverified external calls.
Found: All SpreadsheetApp and built-in calls matched documented Apps Script behavior and executed cleanly in the test copy.
Evidence: SCS3.5 execution/test log and check-scs3.5 receipt (PASS 9 and PASS 10 in SCS3.5-2026-11-20_1035.txt, 2026-11-20).

What I will do about what I found (a fix on the sheet copy, SCS3.5's test log, or 'clean'): Keep @OnlyCurrentDoc and input validation in place on the sheet copy and document findings in SCS3.5's test log.
