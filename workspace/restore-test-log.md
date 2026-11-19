# Restore test log -- the practice business (2026-11-18)

A backup nobody has restored from is a hope.  'It worked' is not an entry: say what did not come back,
or what you checked to be sure nothing is missing.

| # | Restore | What I deleted or suspended | How I restored it | How long | What came back | What did not come back |
|---|---|---|---|---|---|---|
| 1 | The suspended user, restored whole | Suspended practice leaver account `amina.otieno@practice-shop.local` in `/Trainees/belisha` | Admin console > Directory > Users > Reactivate user | 2 minutes | Account sign-in access, OU placement, group memberships, email, and Drive files | Active browser sign-in sessions and OAuth app tokens remained revoked |
| 2 | A file from the shared drive's trash | Deleted `shift-rota-nov.xlsx` from the practice Shared Drive | Opened Shared Drive > Trash > selected file > Restore | 1 minute | File content, formatting, and original folder placement inside the Shared Drive | Nothing missing; Shared Drive parent permissions re-applied automatically |
| 3 | A user's deleted file, restored by the admin | Permanently deleted `supplier-prices.xlsx` from `david.kamau` My Drive Trash | Admin console > Directory > Users > Restore data > Drive | 4 minutes | File content and revision history restored to the user's My Drive | Custom external sharing links and individual file permissions were reset to private |
| 4 | One file from the export | Extracted `inventory-sheet.xlsx` from the Takeout export zip `takeout-20261119T180000Z-001.zip` | Uploaded `inventory-sheet.xlsx` from the extracted Takeout/Drive folder back into Drive | 2 minutes | All worksheet tabs, formulas, cell values, and formatting | Google Sheets comments, version history, and original sharing permissions did not return |
