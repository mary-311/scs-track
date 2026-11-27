# Backup and restore log -- scs-server (SCS4.3)

A backup is a restore that has happened.  Open and readable is the test.  No password, no archive in this repo.

## Where the copies are -- 3-2-1 for scs-server

| Copy | Where it is | Kind of place | What it survives | Last checked |
|---|---|---|---|---|
| The live server | scs-server's own virtual disk | the VM on my laptop | nothing -- it is the thing itself | |
| The archive on the server | /srv/scs-backups | the same virtual disk | a mistake or a bad update -- not the disk dying | |
| On my laptop | ~/scs/evidence/scs4.3 | the laptop's disk -- the same disk the VM lives on | the VM breaking -- not the laptop | |
| On my stick | backup-scs | a USB stick | the laptop dying or being stolen | |
| Away from the laptop | | | fire, theft, flood -- the day the bag goes too | |

## Restores

| # | What I restored, from which copy | To where | Time taken | What was missing, and the fix | Witness |
|---|---|---|---|---|---|
| 1 | | | | | |
| 2 | | | | | |

| 26 Nov 2026 | Restored PostgreSQL database kijiji-mary-anyith from the server backup; opened restored Odoo database and found the Upendo Primary School invoice | 251 seconds (4 min 11 sec) | Invoice found; 604 of 604 filestore files restored | [Partner's name] |
