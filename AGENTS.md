# Plant LED Project Instructions

## Response and KiCad Terminology Rules

- Communicate with the user in polite, standard Korean.
- The user is currently using KiCad 10.0.3.
- Use menu and tool names as displayed in KiCad 10.0.3. If a name is uncertain, state that it needs verification rather than inventing one.
- Refer to copper layers precisely as `F.Cu` and `B.Cu`.
- Place all components, routing, and copper zones on `F.Cu` for the current board.
- Use the terms `Draw Filled Zone`, `Board Setup...`, `Design Rules -> Net Classes`, `Design Rules -> Pre-defined Sizes`, `Track Width`, `Via Size`, and `Via Hole`.
- For a small copper zone connected to selected pads, instruct the user to select the pads first, click `Draw Filled Zone`, configure `Copper Zone Properties`, and then draw the outline.
- Refer to DRC as `Inspect -> Design Rules Checker`.
- Mention the `B` refill shortcut only after a copper zone exists.
- Distinguish between `Net Classes`, which provide electrical design-rule defaults, and `Pre-defined Sizes`, which provide selectable track and via sizes in the routing toolbar.

## Confirmed Design Direction

- The original `2-layer FR4 prototype -> 1-layer MCPCB` sequence is no longer used.
- The current design skips the FR4 prototype and goes directly to a `1-layer Aluminum MCPCB`.
- The current board version is `v1.0.2`, dated `2026-07-11` on the board.
- The board is circular with an 80 mm diameter.
- The board contains 20 red LEDs, 3 blue LEDs, five 2010 resistors, one `+12V` power pad, and one `GND` power pad.
- Routing is only on `F.Cu`; there are no `B.Cu` tracks or zones and no thermal vias.
- The PCB contains 1.2 mm power tracks, 0.6 mm LED interconnect tracks, and 24 `F.Cu` copper zones.
- Mechanical holes consist of six 3.2 mm M3 NPTH holes at a radius of approximately 22 mm and one central 5.3 mm NPTH cable pass-through hole.
- The latest manufacturing package is `gerber/grow light gerber 1.0.2 2026-0711.zip`.
- The individual Gerber files match the latest ZIP. `plant led-PTH.drl` contains no drill coordinates and is not included in the latest ZIP.

## KiCad Stackup Representation and Project Status

- Because KiCad 10 requires an even number of copper layers, represent the stackup as 2-layer while using only `F.Cu` as real copper and leaving `B.Cu` as an unused dummy layer.
- The current stackup metadata records Aluminum MCPCB, 1.6 mm overall thickness, 0.035 mm `F.Cu`, `HAL SnPb`, white `F.Mask`, and black `F.Silkscreen`.
- The actual manufacturing structure is `F.Silkscreen / F.Mask / F.Cu / thermal dielectric / aluminum base`; KiCad's 2-layer stackup is an effective representation of this structure.
- There are no active DRC errors or warnings after the stackup update. One warning for the board-embedded silkscreen graphic whose `Symbol:mark` library source is unavailable was excluded with a comment as an intentional exception.
- The schematic's `footprints:` library is shared among multiple projects from a common directory. It is intentionally not duplicated inside this project, so another environment must configure the same shared library.
- Do not reintroduce an FR4 preliminary build, `B.Cu` heat-spreading copper, or thermal vias as current design requirements in future documentation updates.

## Electrical Configuration

| Channel | LEDs per Series String | Parallel Strings | Total LEDs | String Resistor |
|---|---:|---:|---:|---:|
| Red | 5 | 4 | 20 | 68 ohm |
| Blue | 3 | 1 | 3 | 82 ohm |

- Power is supplied by a 12 V USB-C PD trigger board, with up to approximately 1.5 A available.
- The target power consumption of the first production board is approximately 2 W to 4 W.
- Each 5050 LED contains three internal LED chips, so all three pads of the same polarity must be connected on the PCB.
- `IWS-L5056-UR-N3` and `IWS-L5056-UB-K3` have opposite footprint polarity. Do not apply the red LED polarity assumption to the blue LED.
- When discussing rotated LEDs, use reference designators, polarities, and net names such as `D1 K`, `D2 A`, `Net-(D1-K)`, and `Net-(D2-A)` instead of left/right directions.

## MCPCB and Assembly Principles

- Place all LEDs, resistors, power pads, routing, and copper zones on `F.Cu`.
- Where routing must cross on the 1-layer board, use the 2010 resistor bodies as physical jumpers, as in the current design.
- Use available `F.Cu` area around the LEDs for local heat spreading.
- Do not add FR4-style thermal vias or `B.Cu` heat-spreading copper because the aluminum core is the MCPCB heat path.
- Use solder paste and a PTC hot plate for LED assembly.
- Use the `+12V` and `GND` solder pads on `F.Cu` instead of a protruding through-hole power connector.
- Do not trust cable colors alone; verify voltage and polarity with a multimeter before soldering.
- If LED lenses are used, maintain at least 8 mm x 8 mm of mechanical clearance around each LED.

## Mechanical and Safety Principles

- Couple the PCB to a Daiso medium aluminum makgeolli cup for heat dissipation.
- Apply electrically non-conductive `UPSIREN UTP-8` in a thin, evenly compressed layer between the PCB and the aluminum cup.
- Use nylon shoulder washers or insulating washers in the M3 holes, and maintain copper clearance around holes and fasteners.
- Use an appropriate grommet or strain relief for the approximately 4 mm outer-diameter cable passing through the central 5.3 mm hole.
- Deburr all machined aluminum edges to prevent damage to the cable and insulation.
- After final assembly, use a multimeter to verify that the aluminum cup and fasteners are not shorted to `+12V` or `GND`.
- Ensure that the aluminum cup and external bracket, not the PCB, carry the lamp support load.

