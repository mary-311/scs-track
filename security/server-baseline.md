# scs-server baseline -- my server, known good (SCS4.3)

Written the day the baseline was set, before any fault card.  An audit compares the server with this page and with
server-baseline.txt beside it (the snapshot baseline-look kept).  No password, no PIN, no archive here -- ever.

Server: scs-server on my laptop (Hyper-V)   Address today: ...   Baseline set on: 2026-11-26
Checkpoints: before-scs4.3 (before the firewall and the job)  --  before-faults (before the card round)

## The doors -- one row per ufw rule

| Rule (as ufw show added prints it) | Why it is open -- which service, which session | Checked from the laptop |
|---|---|---|
| default: deny incoming, allow outgoing | Nothing comes in unless a row below lets it in | |
| | | |
| | | |
| | | |

How I proved my page on port 80 still answers with the firewall on: ...

## The backup job

| Part | Mine |
|---|---|
| What it copies | |
| Where it writes (the destination) | |
| When it runs (the schedule) | |
| How long it keeps | |
| The job line | |
| The receipt (the log) | |
| Last restore test | |

## Updates and admins

Security updates: ...   Admins (sudo): ...
