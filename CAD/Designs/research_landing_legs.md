# Landing legs - research notes and concept plan (11 Oct 2026)
Numbers marked calc are mine. Plan is a proposal; nothing is in CAD yet.

## What other landers do
- BPS.space Scout E/F: 4 light CF (or alu) rods, held by a rubber band, nichrome burns it, legs spring out "the moment before touchdown". Tuned to absorb impact without bouncing - bounce killed earlier attempts. https://hackaday.com/2022/08/05/bps-space-succesfully-lands-a-model-rocket/
- JRD Propulsion: syringe + rubber-band dampers, long legs. Spent ascent case stayed on -> bounced. https://popsci.com/science/model-rocket-landing
- Hack Club Blueprint lander: 4 CF-rod legs, syringe damper in upper strut, strut slides and LOCKS, 60 deg hard stop, base spreads load around tube. https://blueprint.hackclub.com/projects/7459
- Sparrow TVC hopper (3", ~900 g): fixed CF-rod legs + 0.8" syringe air shocks venting through a hole (no spring-back); swappable legs (expects breakage). https://highway.hackclub.com/projects/waaaaaaaaah/sparrow-tvc-hopper
- Polaris TVC: printed legs, rubber band + nichrome; warped print -> rocket rocked on 3 legs.
- Brocken EDF Falcon: servo legs; printed arms broke on hard landings -> lock at full extension so load bypasses actuators.
- Delta Super Heavy (TRF): elastic too weak, slingshot tubing + fulcrum snapped legs out; fishing line burnt by igniters; tether sets max spread.
- Falcon 9: hinged at base, stowed up, telescoping pneumatic strut, replaceable crush core.
- Pattern: 4 legs, CF rods, elastic/spring deploy, nichrome release, air-syringe or crush damping; bounce = most common failure.

## Materials / hardware
- CF pultruded rod (Rock West): 1.5 g/cc, E 138 GPa, flex 1.83 GPa. Easy Composites pultrusion TDS says 28-40 GPa / 250-400 MPa -> TEST before trusting (plan uses E = 100 GPa).
- Easy Composites (ships to AU): 5x3 tube 18.5 g/m GBP 6.40/m; 6x4 23.5 g/m GBP 7.00/m; 8x6 ~34 g/m.
- Bonding: 0.1-0.2 mm gap, sand 120-240, IPA, DP420/9323 class epoxy, socket depth >= 2-3 x OD.
- Release: Dyneema (melts 150 C) cut by nichrome/resistor; ~1 s; use 2 lines, keep under tension, firmware timeout (AlbertaSat).
- Damping: Al honeycomb ~7.5 J/g (calc); printed TPU springs back (bad); air syringes field-proven; EPS foam crush pads ~free and replaceable.
- Tip-over: NASA TN (Lavender 1965) 3 vs 4 legs similar on slopes at gear dia/CG height 2-3; point-mass estimate for our CG (calc): footprint 0.6 m -> ~1.5 m/s lateral, 0.7 m -> ~1.8 m/s.

## Concept (recommended)
- 4 legs at az 15/105/195/285 (clear of TVC servo pockets at -30.6/59.4, yaw bosses at 90/270, vents, joint screws, baro ports).
- Folding Falcon-style: hinged at the bottom of the aft airframe (z -8), stowed pointing UP along the body (tip z 257, below the upper-shell joint), rotates 107 deg out/down.
- Leg = A-frame of 2 x CF 5x3 tubes, 265 mm (side-load stiffness without bending).
- Telescoping strut CF 8x6 / 5x3, 150 -> 272 mm, anchored on a lug at z 76 (behind the stop ring), printed snap latch at full extension = deployed lock.
- Pendulum foot with replaceable EPS crush pad (~D25 x 60, tuned to 36 N, ~40 mm stroke) = the damper (no spring-back).
- Deploy: small torsion spring per hinge; all 4 held by one Dyneema loop + nichrome cutter block on the lower shell; fire during landing burn at low speed (deployed legs at the tail are destabilising tail-first and airflow > spring force above ~15-20 m/s).
- Loads (calc, 36 N foot crush, x2 design): strut 133/266 N, leg 119/238 N; 5x3 member Pcr ~375 N (E 100 GPa) -> SF ~3; 3 mm A2 pins (existing type).
- Mass ~150 g for the set incl. lugs and release (calc). Landing mass: no wheels 829 g (plateau T/W 1.60), with 180 g wheels 1009 g (plateau T/W 1.31 - marginal).
- Sim: leg_span 0.60, leg_drop 0.083, leg_crush_force 36, leg_stroke 0.04, add leg mass to dry mass; legs stowed vs deployed inertia both to be reported.

## Bench tests before committing
1. 3-point bend / buckling of the actual CF tubes (resolves the 35 vs 138 GPa conflict).
2. EPS pad crush curve (force vs stroke) with a drop rig -> set pad diameter.
3. Nichrome cut time vs current on the real line.
4. Deploy time on the bench (phone slow-mo), with and without airflow from a fan.
5. Full-rocket drop tests 0.3 -> 1.2 m onto grass with dummy motors.
