# Network troubleshooting log -- SCS4.1

Date: 2026-11-25
Station: [Station name from the board, e.g. Station 2]

## Fault 1 -- station fault

Symptom (the owner's words): [Owner's exact words describing the fault]
My guess (device, cable or network): cable
The rung I expected to fail: 1

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked link light on device and switch port; swapped patch cable with a known-good cable | nothing | 1 |
| 2 | Checked IP address and DHCP lease via net-look / ipconfig /all | [What changed, e.g. got 169.254.x.x or valid address] | 2 |

The rung that failed: [1-6, e.g. 2]
The fault was: [Actual fault found, e.g. cable plugged into WAN instead of LAN / DHCP setting]
Fixed by: [Exact fix applied]
Put back: [Restored original cable/settings to station state; SA checked]

## Fault 2 -- station fault

Symptom (the owner's words): [Owner's exact words for fault 2]
My guess (device, cable or network): device
The rung I expected to fail: 3

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked link light and wifi connection state | nothing | 1 |
| 2 | Checked address and pinged gateway 10.10.51.1 | [What changed, e.g. gateway did not answer] | 3 |

The rung that failed: [1-6, e.g. 3]
The fault was: [Actual fault found]
Fixed by: [Exact fix applied]
Put back: [Restored original state; SA checked]

## Fault card (27-30)

Card number: [27, 28, 29, or 30 from reveal]
Sealed log fingerprint: [12 hex chars from head -1 ~/scs-faults/guess-*.txt]
Symptom: [Symptom heard from partner]
My guess (device, cable or network): network

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked lights and ran ipconfig /all on lab device | nothing | 2 |
| 2 | Compared with own laptop on same wifi using net-look and pinged gateway | [What changed] | 3 |

The rung that failed: [1-6]
Fix: [Fix done by hand on the lab device]
Ladder proof on lab device: proved -- rungs [e.g. 2, 3, 4, 5] passed after fix
Put back: [Lab device back on automatic DHCP / rejoined; partner and SA checked]

## The card I planted

Card number: [27, 28, 29, or 30]
Step done by hand: [Manual step performed on lab device with SA watching]
Undo: [Manual undo step performed; no password written]
How I checked it: Checked ipconfig /all, DHCP/wifi state, and rungs 2 to 5 with SA

## Printer

Printer address: [Reserved LAN IP on the station subnet, e.g. 10.10.51.50]
Reserved: [yes or not done: reason]
Added on a lab laptop with a test page: [yes or not done: reason]
Added on a phone with a test page: [yes or not done: reason]
