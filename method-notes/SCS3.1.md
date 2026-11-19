# Method note -- SCS3.1

## 1. What I set out to do
Configure users, groups, organizational units, service settings, and a scoped delegated admin role in my sandbox unit while logging every change before clicking.

## 2. What I did, in order
Created the new starter and accountant users, built the sales and finance groups, created Staff, Front Desk, and Workshop OUs, disabled Chat on Front Desk, tested Help Desk Admin limits, and rolled back the overrides.

## 3. What went wrong, and how I fixed it
My initial change-log audit timestamps were offset by two minutes and I missed a separate row for creating the accountant user; I reconciled the timestamps against the exported CSV and documented the gap under Gaps.

## 4. How long it took, against the plan
It took roughly 45 minutes including partner user-side verification and audit log reconciliation, which was 10 minutes longer than planned due to checking service propagation.

## 5. One lesson for the next person
Always write the change-log row before every single click—even when creating a second user in the same ticket—so every audit event has a matching row.

## 6. What I might be wrong about, and how I would find out
I might be wrong about whether Google Chat service changes propagate immediately to already-signed-in browser sessions; I would verify this by testing in a fresh incognito window and checking the Admin audit log event timestamp.
