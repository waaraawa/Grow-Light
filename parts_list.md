# Plant LED PCB Parts and Manufacturing Specification

## Current Design Summary

- Board version: `v1.0.2` (`2026-07-11`)
- Manufacturing direction: Direct production as a `1-layer Aluminum MCPCB`, without a preliminary FR4 prototype
- Board outline: 80 mm diameter circle
- Power input: 12 V from a USB-C PD trigger board
- Available supply: 12 V, up to approximately 1.5 A
- Target board power: approximately 2 W to 4 W
- LED configuration: 20 red LEDs and 3 blue LEDs
- Copper usage: all components, tracks, and zones on `F.Cu`; no `B.Cu` copper or thermal vias
- Mechanical holes: six 3.2 mm M3 NPTH holes and one central 5.3 mm NPTH cable pass-through hole
- Latest manufacturing package: `gerber/grow light gerber 1.0.2 2026-0711.zip`

## v1.0.2 Order Specification

| Item | Ordered Value |
|---|---|
| Quantity | 5 boards |
| Base Material | Aluminum |
| Layers | 1 |
| Dimension | 80 mm x 80 mm |
| PCB Thickness | 1.6 mm |
| Specify Stackup | No |
| Outer Copper Weight | 1 oz |
| Solder Mask | White, front only |
| Silkscreen | Black, front only |
| Surface Finish | HASL with lead (`HAL SnPb`) |
| Back Copper | None |
| Thermal Conductivity | 1 W/(m·K) |
| Breakdown Voltage | 3000 V |
| Electrical Test | Not tested |
| Appearance Quality | IPC Class 2 Standard |

## Electrical Configuration

| Channel | LEDs per Series String | Parallel Strings | Total LEDs | Resistor per String | Notes |
|---|---:|---:|---:|---:|---|
| Red | 5 | 4 | 20 | 68 ohm | Conservative configuration for 12 V utilization and thermal control |
| Blue | 3 | 1 | 3 | 82 ohm | Provides margin for the LED forward voltage |

## PCB-Mounted Parts

| References | Part | Quantity | Current Specification | Notes |
|---|---|---:|---|---|
| D1-D20 | Red SMD LED | 20 | ITSWELL `IWS-L5056-UR-N3` | 5050, 650-665 nm, Vf 1.8-2.4 V @ 60 mA |
| D21-D23 | Blue SMD LED | 3 | ITSWELL `IWS-L5056-UB-K3` | 5050, 450-475 nm, Vf 2.8-3.6 V @ 60 mA |
| R1-R4 | Red string resistor | 4 | 68 ohm, 2010, 0.75 W or higher recommended | One per string |
| R5 | Blue string resistor | 1 | 82 ohm, 2010, 0.75 W or higher recommended | One per string |
| J1 | `+12V` input pad | 1 | 3.2 mm x 2.6 mm front SMD solder pad | No through-hole connector |
| J2 | `GND` input pad | 1 | 3.2 mm x 2.6 mm front SMD solder pad | No through-hole connector |
| PCB1 | LED PCB | 1 | 80 mm diameter, 1-layer Aluminum MCPCB | All electrical copper is on `F.Cu` |

## Current PCB Routing and Copper

- `F.Cu` power-track width: 1.2 mm
- Selected LED series-connection track width: 0.6 mm
- `F.Cu` copper zones: 24
- The single-sided routing is completed with a combination of conventional tracks and copper zones.
- The 2010 resistor bodies act as physical jumpers to avoid routing crossings on the 1-layer board.
- `F.Cu` copper around the LEDs provides both electrical connectivity and local heat spreading.
- There are no `B.Cu` tracks or zones.
- FR4-style thermal vias are not used. Heat transfers through the MCPCB dielectric layer into the aluminum core.
- The latest Gerber package contains `F.Cu`, `F.Mask`, `F.Silkscreen`, `Edge.Cuts`, and NPTH drill data.
- There are no plated through holes, and the current `PTH.drl` contains no drill coordinates.

## PCB Manufacturing and Assembly Equipment

| Item | Quantity | Recommended Specification | Notes |
|---|---:|---|---|
| Solder paste | 1 | Compatible with the LED and resistor pads | Apply a thin, uniform layer |
| PTC hot plate | 1 | Large enough to heat the complete MCPCB evenly | For LED and resistor reflow assembly |
| Tweezers | 1 | Precision SMD type | Verify LED polarity before placement |
| Multimeter | 1 | Voltage, resistance, and continuity measurement | Verify PD output, polarity, and isolation |
| USB-C PD trigger board | 1 | Low-voltage model selectable among 5/9/12/15/20 V | Set to 12 V and verify by measurement |
| USB-C PD power source | 1 | Supports 12 V at 1.5 A or more | Maximum available input is approximately 18 W |
| Power cable | 1 | Reused USB cable, approximately 4 mm outer diameter | Measure polarity instead of relying on conductor colors |

## Mechanical and Thermal Parts

| Item | Quantity | Recommended Specification | Notes |
|---|---:|---|---|
| Aluminum cup | 1 | Daiso medium aluminum makgeolli cup | Verify the actual contact area with the 80 mm PCB |
| Thermal interface | 1 | Electrically non-conductive `UPSIREN UTP-8` | Compress into a thin, uniform layer |
| M3 fastener sets | 6 | M3 screws, washers, and nuts | Corresponding to the six 3.2 mm NPTH holes |
| M3 insulation parts | 6 | Nylon shoulder washers or insulating washers | Prevent contact between fasteners and PCB copper |
| Insulating film | As needed | Kapton or PET film | Additional insulation where required |
| Cable grommet | 1 | Fits the 5.3 mm center hole and approximately 4 mm cable | Protects cable insulation and provides strain relief |
| External mounting arm | 1 | Small clamp and 1/4 inch magic arm | Keep as short as practical to reduce torque |
| External adapter plate | 1 | Transfers load into the aluminum cup | Prevent the PCB from carrying the lamp support load |
| Optional diffuser lenses | 23 | 8 mm x 8 mm lenses for 5050 LEDs | Check mechanical interference around each LED |

## Recommended Spare Parts

| Part | Recommended Spare Quantity | Purpose |
|---|---:|---|
| Red LED | 5-10 | Assembly failures and component variation |
| Blue LED | 3-5 | Assembly failures |
| 56 ohm resistor | 5 | Higher-current experiments |
| 68 ohm resistor | 10 | Default red value and replacements |
| 82 ohm resistor | 5 | Default blue value and replacements |
| 100 ohm resistor | 5 | Tests with lower current and heat |

## Polarity and Safety Checks

1. Verify the PD trigger board's 12 V setting and actual output voltage before connecting it to the LED PCB.
2. Identify `+12V` and `GND` with a multimeter rather than relying on cable insulation colors.
3. Verify the different footprint polarities of `IWS-L5056-UR-N3` and `IWS-L5056-UB-K3`.
4. Check for a short between `+12V` and `GND` before applying power after assembly.
5. After final fastening, confirm that the aluminum cup and fasteners are not shorted to `+12V` or `GND`.
6. Apply power briefly at first and verify the total current and illumination of every string.
7. After 10 to 15 minutes of operation, check the temperatures of the MCPCB and aluminum cup.
8. If the temperature is excessive, increase the resistor values or reduce the supply power.

