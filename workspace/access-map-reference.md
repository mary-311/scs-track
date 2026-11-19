# Access map -- the reference shop (an invented business) -- SCS3.1

Who should have which access, and why?  One row per person, or per identical job.
Groups are people; units are settings; every person is in one unit and many groups.
Why: the three questions in one line -- what the job needs, what goes wrong with more, who decided.
This map is of an invented business and may be committed.  Your client's map never comes here:
it lives in the client folder (Clients, in your Windows SCS folder).

| Person (job) | What the job needs | OU | Groups | Admin role | Why (one line) |
|---|---|---|---|---|---|
| The owner | Runs the business, signs everything, full domain control | Staff | all-staff@, finance@ | super-admin | Needs full domain authority to sign off all operations, sharing super-admin risks total account takeover, the owner decided |
| The accountant (a sandbox user, ticket 4) | Invoices, books, M-Pesa statements, counter password resets when owner travels | Staff | all-staff@, finance@ | Help Desk Administrator | Needs finance mail and Front Desk password resets while owner travels, full admin risks unauthorized billing or settings changes, the owner decided |
| The shop manager | Opens and closes, orders stock, answers customer emails | Staff | all-staff@, sales@ | none | Needs staff updates and customer sales mail, admin rights risk accidental user or policy changes, the owner decided |
| Counter staff (four) | Serve customers on one shared counter machine without Chat | Front Desk | all-staff@, sales@ | none | Needs sales mail and staff announcements without Chat distractions on the shared counter PC, broader access risks customer or finance leaks, the owner decided |
| The new starter (a sandbox user, ticket 1) | Starts on the counter tomorrow serving customers | Front Desk | all-staff@, sales@ | none | Needs counter email and sales group without Chat on the shared machine, extra privileges risk unauthorized settings or finance access, the owner decided |
| Welders (three) | Workshop work on personal phones needing rota only | Workshop | all-staff@ | none | Needs company rota via all-staff mail only, sales or finance groups expose sensitive commercial data, the owner decided |
| Drivers (two) | Deliveries on personal phones needing delivery sheet and shop number | Workshop | all-staff@ | none | Needs delivery updates via all-staff mail only, extra group or admin access risks exposing customer or financial records, the owner decided |
| Me (the admin) | Set up users, groups, OUs, and delegated roles inside trainee unit | /Trainees/belisha | none | Delegated Trainee Admin | Needs scoped admin rights to build and test the sandbox unit, global super-admin risks breaking other trainees' environments, the trainer decided |

## The partner's cold read

Partner: Verified.  One person with more than the job needs, or "none" and why: none — every role is scoped to the minimum unit and groups required for the job.
