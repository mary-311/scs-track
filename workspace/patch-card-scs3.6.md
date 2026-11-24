# Patch Card -- SCS3.6

One real bug from the audit.  The fix, not a rewrite.  The spec and the test come before the prompt.

The bug, in one sentence: buildSmsUrl builds the SMS query string without URL-encoding parameters, so an ampersand (&) in text splits or truncates the message parameter.
Which check found it (auth, edge case, wrong version, invented library): edge case
The spec for the fix, one thing: URL-encode `to` and `text` using encodeURIComponent inside `buildSmsUrl` in `workspace/stock-tools/send-sms.js` without changing other functions.
The test that shows the bug (input -> expected): buildSmsUrl("x", "Nuts & bolts") -> URL searchParams.get("text") equals "Nuts & bolts" (fails before patch because it returns "Nuts ").
The prompt, word for word: In workspace/stock-tools/send-sms.js, update only buildSmsUrl to URL-encode `to` and `text` with encodeURIComponent; change nothing else and show the diff.

## The Diff, Read Whole

Every line the patch changed.  A line the spec did not ask for is marked BEYOND in the second column.

| Line | What the patch changed | In the spec? | My adjustment |
|---|---|---|---|
| buildSmsUrl return line | Encoded `to` and `text` with `encodeURIComponent` | Yes | Kept as requested |
| Outside `buildSmsUrl` | No other lines changed | BEYOND check | None needed; diff matched spec |

Tests before the patch: New test fails; 5 baseline tests pass.
Tests after the patch: All 6 tests pass on scs3.6-patch.
Tests after my adjustment: All 6 tests pass on scs3.6-patch.
Commits on scs3.6-patch (the test, the patch, the adjustment): 4c75aee (test), 3e2581d (patch).

## Receipt

1. Label: AI-assisted, directed by me
2. Tool and tier: Programme AI assistant (current session tier)
3. Spec and prompt: above, word for word
4. Tests or checks: node --test in workspace/stock-tools (failed on new test before patch, passed 6/6 after patch)
5. Rights line: not checked
6. Cost: 0
