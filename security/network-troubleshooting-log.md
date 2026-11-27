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

## Fault 3 -- fault card, I was the fixer

Card number: 27
Sealed log fingerprint: 0123456789ab
Symptom: Lab device could not reach the network or gateway
My guess (device, cable or network): network

| Step | What I did (one swap or one look) | What changed | Rung |
|---|---|---|---|
| 1 | Checked lights and ran ipconfig /all on lab device | nothing | 2 |
| 2 | Compared with own laptop on same wifi using net-look and pinged gateway | Gateway did not reply | 3 |

The rung that failed: 3
The fault was: Lab device network configuration prevented normal gateway reachability
Fixed by: Restored automatic DHCP and network configuration on the lab device
Proved on the lab device (the rungs that passed after the fix): rungs 2, 3, 4, 5 passed after fix
Put back: Lab device back on automatic DHCP and rejoined; partner and SA checked

## The card I planted

Card number: 27
The step break.sh printed, done by hand on the lab device (in my words, no passwords): Applied fault card step by hand on the lab device with SA watching
The undo, done by hand after the fixer finished, and how we checked it: Undid the step by hand and checked ipconfig /all, DHCP/wifi state, and rungs 2 to 5 with SA

## Printer

Printer's address: 10.10.51.50
Reserved on the router: yes
Added on a lab laptop: yes
Added on a phone: yes
