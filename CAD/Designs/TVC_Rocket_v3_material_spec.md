# TVC_Rocket_v3 - material specification (whole rocket)

Densities are the ones assigned in Fusion. "Override" means the body's density was set so the modelled envelope weighs the datasheet mass.

| Part | Material (density g/cc) | Why |
|---|---|---|
| Upper shell (avionics bay + ogive nose) and lower shell (reaction-wheel bay) | PAHT-CF, Bambu (1.06) | Non-structural cover (thrust and landing loads go through the aft section), so the lightest stiff printable option wins. Split into two prints only because the 0.64 m body exceeds the H2D's 325 mm height; the nose is integral to the upper shell so there is no separate nose joint. Same filament and drying routine as the rest of the rocket. HDT 194 C tolerates the vent puffs. Weak spot: Z-layer impact (13 vs 57 kJ/m2); a tip-over may crack it, and a reprint is cheap. Fallback if the GNSS test fails: reprint in ASA (1.05) or PA6-GF (RF-transparent), no CAD change. |
| Decks x2 (wheel deck = gas barrier, avionics deck) | PAHT-CF (1.06) | The wheel deck sees the landing-motor burn-through jet 10 mm below it at touchdown; nylon-CF has the highest HDT of the printable options. Flat print, so fully isotropic in-plane. Add a 0.1 mm stainless shim or ceramic paper disc on the underside centre if testing shows scorching. |
| Aft airframe / thrust structure | PAHT-CF (1.06) | Carries motor thrust, gimbal loads and the body joint. Stiffness plus heat near the exhaust (HDT 194 C, vs PETG 69 C) rule out PETG/ASA. CF reduces warp on a 134 mm upright print. |
| Cartridge, outer ring | PAHT-CF (1.06) | Holds the motors directly, so the hottest printed part; needs stiffness for TVC accuracy. |
| Blocker claws | Macor (2.52) | Sit in the exhaust plume: machinable ceramic that survives black-powder exhaust (~1650 C). Heaviest non-motor items (2 x 31.9 g) - the main mass-reduction lever if ever needed. |
| Clevis plates, links, pins, axles, screws, E-clips | 304 / A2 stainless (7.9) | Strength in thin sections, heat near the plume, corrosion from BP residue. |
| Heat-set inserts | Brass (8.5) | Standard; melts into PAHT-CF cleanly; repeated assembly of the shell and deck screws. |
| Pivot bushes | Sintered bronze (8.8) | Self-lubricating, low slop in the pivots. |
| MF84ZZ bearings | Bearing steel (7.8) | Purchased standard. |
| Servo horns | 6061 aluminium (2.7) | Clamped spline horn, stiff and light. |
| KST X08H Plus servos (x4) | override: 9.5 g each | Datasheet mass (rotorama 9.5 g; servodatabase 0.32 oz = 9.1 g). Weigh yours. |
| TVC pushrod assemblies (x2) | override: 1.9 g each | Estimate for M2 rod + 2 metal ball links - VERIFY by weighing. |
| Estes F15-0 (x2) | override: 94.0 g loaded | NAR certification (F15-0 tests ES111201-3: 94.0 g initial, 33.0 g burnt). The 102-104 g figures are the F15-4/6/8. |

Why not a COTS 3" tube for the forward body: Blue Tube 2.0 (0.474 g/mm) is ~35 % heavier per length than the 1.2 mm PAHT-CF wall, needs a separate nose with a ~25 g shoulder plus a second joint, and has to be shipped to Australia. It is tougher on impact; that is the trade we accepted.

Reaction-wheel bay note: the 2 mm wheel deck is sized for the current 3-point mounting. When the ~180 g wheel set is designed, either thicken the deck (and use M2x6 screws) or let the wheel cage also locate in the lower-shell bore near its top; landing shock on a 155 mm tall cantilever is the governing load.

## Landing legs and leg keeper (simplified 11 Oct: 9 pieces per leg)
| Part | Material (density g/cc) | Why |
|---|---|---|
| Leg tube, 14 OD x 12 ID x 260 | Carbon fibre tube (1.55), pultruded or roll-wrapped | Each leg is now a single cantilever, so it carries bending instead of the old A-frame's compression. At the 54 N design foot load (1.5 x the 36 N foam crush) the root moment is ~13.6 N m: ~94 MPa at the knuckle socket, well under CF tube strength (500+ MPa) and stiff enough that tip deflection is a few mm. Keep it out of the plume (epoxy ~80 C); the tubes sit 2.25 mm off the skin. |
| Knuckle, tip cap + keeper tab | PAHT-CF (1.06) | Same material and process as the airframe (HDT 194 C near the nozzle). Tube bonded into a 30 mm socket (knuckle) and an 18 mm socket (tip cap) with DP420-class epoxy. Print the knuckle on its side so the lock boss and ramp lie in XY. |
| Hinge cheeks (8) + stop bars (4) | PAHT-CF, printed into the aft airframe | Landing loads go straight into the thrust structure; 3.5 mm cheeks. Only the +y cheek carries the plunger lobe. Risk: a cheek broken in a crash means reprinting the aft section. |
| Hinge pin | 304/A2 3 mm dowel (7.9) + 2 DIN 6799-2.3 E-clips | Same type as the claw axles. |
| Leg lock | Stainless M6 spring plunger, plain 3 mm pin, 3 mm stroke | The pin rides a printed 31 deg ramp, then drops into a 3.2 mm hole at full deploy. At the design load the pin sees ~620 N in shear (fine for hardened steel). The printed hole sees ~70 MPa bearing, SF ~1.3, which is the weak point: if drop tests show the hole going oval, press a 3x4x3 A2 sleeve into the boss. Use a plain-pin plunger, not a ball plunger, because a ball would pop out under load. |
| Deploy spring | 0.7 mm music-wire torsion spring, 6 coils, ID 3.3 | ~0.06 N m at full deploy. It only has to start the leg moving: once a leg passes the vertical, its own weight (under landing-burn deceleration) carries it out. Bench-check deployment against the descent airflow. |
| Foot | EPS craft ball, 25 mm (0.020) | Off-the-shelf with no orientation to get right. Sitting offset outboard, it sticks out ~26 mm in ascent, versus ~45 mm for an angled pad. Crush force builds as it squashes (~35 N at 5 mm), with no spring-back. Treat as a consumable. |
| Keeper ring with integral pegs | PAHT-CF (1.06) | The pegs are 2.4 mm printed arcs on r 36, so they slide straight out of the 3.0 mm tab holes when the ring turns 9 deg. Peg shear is only the spring preload (~1 N). |
| Keeper drive stud | M2x8 A2 set screw, threadlocked into the horn | Replaces the pressed 2 mm dowel; nothing to press-fit. |
| Keeper servo | KST X08H Plus (same part as TVC/blocker) | One spare-part type for every actuator; pre-flight release test on the pad. |
