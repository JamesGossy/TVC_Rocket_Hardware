# TVC_Rocket_Gimbal_v3 - parts list (excluding motors)

## Printed (PAHT-CF) - 3
- Aft airframe / thrust structure: OD 79.5, ID 74.5, z -14..82, 3" tube spigot z 82..97 (OD 75.9), 8.75 deg circular stop ring, TVC servo pockets x2, yaw bearing bosses
- Cartridge (sleeve + inner ring + TVC drive lugs + blocker pads/servo pockets)
- Outer ring (compact yaw bosses, r 32.25)

## Steel / ceramic
- Blocker claw, Macor x2
- Blocker clevis plate, 1.2 mm 304, laser cut x2 (identical, one rotated 180 deg)
- Blocker link 9.87 mm c-c, 1.5 mm 304 x2
- Claw axle 3 mm A2 dowel x2 + E-clip DIN 6799-2.3 x4
- Tab pin 2 mm x2 + E-clip x4

## Gimbal pivots
- Pitch: shoulder screw 4x10 M3 x2, bronze bush 4x6x9 x2, MF84ZZ x2, M3 nut x2
- Yaw: shoulder screw 4x6 M3 x2, bronze bush 4x6x4 x2, MF84ZZ x2, M3 nut x2

## Drives
- KST X08H Plus x4 (2 TVC, 2 blocker)
- Servo horn 6 mm clamped alu x4
- TVC pushrod 33.5 mm c-c (M2 rod + 2 metal ball links, set length on assembly) x2
- M2 ball stud 4.8: 5 mm shank x2 (horns), 9 mm shank x2 (cartridge lugs)
- M2x4 button head (ISO 7380, A2) x12 - the ONLY M2 screw: 4 TVC servo ears, 2 blocker servo ears, 4 clevis plate, 2 horn pins
- M2x3 heat-set insert x12 - the ONLY insert: 4 TVC ears, 2 blocker ears, 4 clevis pads, 2 TVC lugs

Total ~79 parts (v2: 93), 3 prints (v2: 7).

## Key numbers
- Gimbal: 8.5 deg joint limits, hard stop ~8.75 deg any direction. Fly with an 8 deg circular command clip.
- TVC horns clocked -14.47 deg on the spline at neutral + pushrods 33.5 mm -> symmetric: +/-45 deg servo for +/-8.4 deg (+/-42.6 deg for 8 deg).
- Flight software: firmware_snippets/tvc_command_map.h (8 deg circular clip + 2-D servo map incl. cross-coupling).
- Blocker: closed at linkage dead-centre (servo -0.5 deg limit), open -55 deg claw at -79 deg servo. Claw tips trimmed for a 1.0 mm meeting gap (absorbs +/-0.1 mm link tolerance).
- Blocker servo ear screw head sits on the ear inside a 4 mm clearance hole in the plate (screw clamps ear to the cartridge lip).
- Clearance sweep (8.4 deg circle x claws open/closed): clean. See v3_checks/sweep_v3c.txt
  (only ball-link housing vs stud neck touching at extremes - simplified link model).
