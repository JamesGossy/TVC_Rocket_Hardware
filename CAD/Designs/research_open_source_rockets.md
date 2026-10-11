# Research notes - open-source / documented TVC landers and printed airframes
Compiled 10 Oct 2026 for the forward-body design. Numbers marked "calc" are my own arithmetic from the cited sources.

## 1. Comparable landers
| Project | Mass | Motor(s) | What transfers |
|---|---|---|---|
| BPS.space Scout F (Joe Barnard) | 1.2 kg | separate ascent + F15 landing | F15 picked for consistent curve; landing on ignition timing alone failed (ignition delay / thrust not repeatable) -> ceramic thrust "pincers" (up to 80 % block); printed PLA gimbal flexed -> machined alu; FC "as low as possible"; parachute abort; Scout E tipped over from residual lateral velocity blamed on GPS antenna placement; ~40 % landing rate. https://hackaday.com/2020/11/27/so-close-to-landing-a-model-rocket-on-its-tail/ , https://thenewstack.io/one-mans-dream-to-build-a-working-spacex-style-model-rocket/ |
| BPS Falcon Heavy model | - | 2 motors stacked in one TVC mount | Lower motor thrown out when the upper lights (hot staging). https://tompaton.com/blog/cached/makezine.com/2019/10/25/build-your-own-thrust-vectored-rockets-for-vertical-landings-like-spacex/index.html |
| JRD Propulsion lander (A. Kapoor) | n/p | 2 stacked solids, printed gimbal +/-7 deg | Spent ascent motor FAILED to eject on the successful flight -> extra mass, bounced, landed off-plumb. 4 failures first. https://hackaday.com/2024/07/10/model-rocket-nails-vertical-landing-after-three-year-effort/ |
| UConn AIAA propulsive landing | n/p | 74 mm, "two-stage motor system" | Steady attitude error tracked off-axis mass -> spin-balanced the vehicle. https://aiaa.engr.rso.uconn.edu/pl |
| "Starship Moon Lander" (TRF) | 1020 g | 1 x F15 | T/W ~2.6 for 0.25 s then ~1.5; ~40 m apogee; builder wanted 70 g less. https://www.rocketryforum.com/threads/starship-moon-lander-variant-with-thrust-vector-control.160104/ |
| Reddit custom F9 TVC | ~950 g | F15 | Legs ~200 g (!), fins 75 g, camera 65 g. |
| RocketFC (Teensy F15 lander FW) | 0.95 kg descent | F15 | F15 can only cancel ~15-80 m apogee; expect 1-3 m/s touchdown; +/-150 ms ignition-delay error ~ +/-10 % thrust error; baro in vented bay behind foam, shielded from exhaust. https://github.com/trooper7652-commits/RocketFC |
| Hack Club Blueprint lander | - | 76 mm body | Avionics as one removable "unibody" block; leg base is a sleeve over the tube so loads spread. https://blueprint.hackclub.com/projects/7459 |
| Starkit (Hack Club) | - | electric | Friction fits unpredictable (moisture, orientation) -> moved to bolt locks. |
| Nerys "99 % printed" 80 mm rocket | 400-500 g | F32/F44 | Vase-mode PLA/PETG; under-extruded seams split. https://www.printables.com/model/414637 |
| Astrorizzicist 3" printed L2 | - | H/J | Printed threads 0.15 mm/side still too tight; over-torque sheared threads; ejection gas leaked through threads. |
| Estes Scorpio 3D (printed kit) | 482 g, 51 mm | F15 class | Printed nose needs 260 mm build height. |

Estes rates the F15-0 for max lift weight 539 g - every TVC lander above flies 0.95-1.2 kg anyway (slow liftoff).

## 2. Motor facts (cert PDF in Reference_Models)
- F15-0 loaded 94.0 g (avg of 3), burnt 33.0 g (F15-0 tests ES111201-3). 102-104 g is the F15-4/6/8. Propellant 60.0 g.
- Avg thrust 14.38 N, peak 25.26 N (sigma 4.97 N!), burn 3.45 s, It 49.6 Ns. Plateau after 0.6 s: ~15.4 -> 13.0 N.
- The sim's motors/Estes_F15.eng header says 0.103 kg total - that is an F15-4 mass.

## 3. Burn-through (IMPORTANT, outside body scope)
- A "-0" motor bursts forward at burnout and is designed to light whatever is above it ("seamless staging").
- Gap staging is reliable over gaps far larger than our 12 mm (Stine: ~100 % up to ~12 in).
- So the ascent F15-0 will very likely light the landing motor at ascent burnout (~3.5 s, still climbing) unless physically blocked. Vents near the upper nozzle make ignition MORE likely.
- Nobody documents protecting a delayed upper motor. Candidate fixes (untested): solid blast cap on the ascent motor's forward end that leaves with it, with side vents below the cap; or a nozzle plug on the landing motor.
- Same physics at landing burnout: the landing motor dumps hot gas forward through the cartridge cap -> the avionics bulkhead must seal and the cavity must vent.

## 4. Printed airframe practice
- Joints: friction fits are unreliable (nylon absorbs ~0.9 % water). Use radial screws into heat-set inserts, or a positively locked bayonet. Printed tubes fail in Z-bending at joints.
- Engagement: couplers ~1-1.5 cal; nose shoulders 0.5-1 cal (those numbers include ejection loads we don't have).
- FDM fits per side: press 0.05-0.15, slide 0.2-0.3 mm. Crush ribs give zero-slop fits independent of print tolerance.
- M2 heat-set insert (CNC Kitchen): OD 3.6, L 3.0, hole 3.2, min 1.3 mm wall around it.
- Nose shape at <40 m/s: any tangent-joined shape (ogive/elliptical/von Karman) has ~zero pressure drag (OpenRocket tech doc); skin friction dominates -> pick for mass and printability. Print tip-up, raise min layer time so the tip doesn't wobble, solid tip.
- Tall thin nylon-CF tubes: dry hard (80 C 8-12 h), glue + brim, low fan, <=70 mm/s.

## 5. Materials (Bambu TDS)
| Material | Density | Bending XY / Z (MPa) | Bend. modulus XY / Z (MPa) | Impact XY / Z (kJ/m2) | HDT C | Price |
|---|---|---|---|---|---|---|
| PAHT-CF | 1.06 | 125-140 / 61-70 | 4120-4230 / 1700-1820 | 57.5 / 13.3 | 194 | ~USD 95/kg |
| PA6-CF | 1.09 | 151 / 80 | 5460 / - | 40.3 / 15.5 | 186 | USD 80/kg |
| PETG-HF | 1.28 | 64 / 48 | 2050 / - | 31.5 / 7.6 | 69 | ~USD 20/kg |
| ASA | 1.05 | 65 / - | 1920 / - | 41.0 / 4.9 | 100 | USD 30/kg |
NOTE: Bambu lists PAHT-CF at 1.06 g/cc, the handoff says 1.20. Masses below use 1.20 (conservative, ~13 % high if 1.06 is right).
- Chopped-CF and GNSS: no measurements found; one RF guide says keep carbon-filled filament away from antennas; one anecdote of no effect. Continuous CF definitely shields. Test lock time/C/N0 inside a printed coupon, or use a non-CF nose.

## 6. 3" COTS tubes (79.5 mm OD class)
| Tube | ID / OD | g/mm | Price | Note |
|---|---|---|---|---|
| Blue Tube 2.0 3.0" | 76.2 / ~79.4 | 0.474 (578 g/48") | USD ~30 / 48" | matches our spigot; very tough |
| PML phenolic PT-3.0 | 76.25 / ~79.4 | 0.375 | USD 26 / 36" | brittle |
| LOC kraft 3.0" | 76.2 / 78.7 | 0.256 | USD 14 / 34" | OD 0.8 mm under ours, soft |
| Wildman G12 3.0" | 76.2 / 79.2 | heaviest (~0.7 est) | USD 63 / 30" | stiff, heavy, RF ok |
| LOC carbon 3.0" | ~73 / 76.2 | - | USD 300+ | wrong size, blocks GNSS |
| Printed PAHT-CF 1.2 mm wall | - | 0.35 (@1.20) / 0.31 (@1.06) | ~USD 3 per 100 mm | |
Shipping 48" tubes to Australia is the dominant cost; no AU stockist confirmed.

## 7. Lessons applied to this design
1. Keep it light, but don't chase grams past ~600 g landing mass: with the blocker's 0.6 throttle floor an F15 can't hover below ~0.8 kg, so a light rocket must hoverslam (zero velocity exactly at ground). Legs (~100-200 g on others) will land it in the sweet spot anyway.
2. One avionics module, removable, all servo/igniter wiring stays on the aft section -> forward body is a cover with no connectors across the joint.
3. Joint = shoulder seat + crush-rib bore + 3 radial M2 screws into inserts (no friction-only fits, no threads).
4. Sealed, heat-shielded bulkhead between motor and avionics; motor cavity vents to outside; baro in the bay behind foam, away from the vent holes.
5. GNSS antenna high in the nose; verify PAHT-CF transparency or print the shell in ASA/PA6-GF/PETG.
6. Spin/static balance: keep battery and GNSS on-axis (UConn).
7. Design the guidance for a failed jettison (spent case 33 g stays attached).
8. Plan for many flights: forward shell is cheap (one ~4 h print) and replaceable after a tip-over.
