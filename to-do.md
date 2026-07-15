# Plant LED PCB Status and To-Do

## To-Do

The next step is to prepare the components and assembly equipment.

### 4. Parts and Assembly Preparation

- [ ] Prepare the LEDs, resistors, and spare parts listed in `parts_list.md`.
- [ ] Prepare solder paste compatible with the MCPCB and components.
- [ ] Prepare a PTC hot plate capable of heating the 80 mm MCPCB evenly.
- [ ] Set the USB-C PD trigger board to 12 V and verify the actual output with a multimeter.
- [ ] Prepare an approximately 4 mm outer-diameter power cable and a grommet or strain relief for the center hole.
- [ ] Prepare six each of the M3 screws, nuts, washers, and insulating shoulder washers.
- [ ] Prepare `UPSIREN UTP-8` and any additional insulating film required.

### 5. MCPCB Assembly

1. Inspect the received MCPCB outline, pads, solder mask, silkscreen, and hole positions.
2. Use a multimeter to check for a short between `+12V` and `GND`.
3. Verify the different polarities of the red and blue LEDs.
4. Apply a thin, uniform layer of solder paste.
5. Place the LEDs and resistors, then inspect their positions and polarities under magnification.
6. Heat the board on the PTC hot plate and inspect every solder joint.
7. Pass the cable through the central 5.3 mm hole and apply strain relief.
8. Measure the cable polarity, then solder it to `J1 +12V` and `J2 GND`.
9. Recheck polarity, shorts, and solder bridges before applying power.
10. Apply power briefly and confirm that every LED string illuminates normally.
11. Apply `UPSIREN UTP-8` in a thin, uniform layer and tighten the six M3 screws evenly.
12. After final fastening, verify isolation between the aluminum cup and fasteners and both `+12V` and `GND`.

### 6. Operating Verification and Results

- [ ] Measure the input voltage and total current at first power-on.
- [ ] Verify the illumination of each of the four red strings and the one blue string.
- [ ] Measure the MCPCB and aluminum cup temperatures after 10 and 15 minutes.
- [ ] Check the PD trigger board and cable temperatures during extended operation.
- [ ] If the temperature is excessive, increase the resistor values or reduce the supply power.
- [ ] Record actual current, temperature, assembly issues, and improvements in the table below.

| Item | Initial Power-On | 10 Minutes | 15 Minutes | Notes |
|---|---:|---:|---:|---|
| Input voltage |  |  |  |  |
| Total current |  |  |  |  |
| MCPCB temperature |  |  |  |  |
| Aluminum cup temperature |  |  |  |  |
| PD trigger board temperature |  |  |  |  |

### Future Improvement Candidates

- [ ] Decide whether to adjust resistor values based on measured current and temperature.
- [ ] If diffuser lenses are used, verify the 8 mm x 8 mm clearance and actual mechanical interference.
- [ ] Verify the long-term durability of the cable grommet and external bracket.
- [ ] Consider an independent FR4 derivative only if a comparison experiment or separate use case arises.

## Current Status

- Current phase: `MCPCB ordered / awaiting production and delivery`
- Manufacturing type: `1-layer Aluminum MCPCB`
- Board version: `v1.0.2` (`2026-07-11`)
- Board outline: 80 mm diameter circle
- Power: 12 V USB-C PD trigger board
- LED configuration: 20 red LEDs and 3 blue LEDs
- Routing: all components, tracks, and copper zones on `F.Cu`
- Mechanical enclosure: Daiso medium aluminum makgeolli cup
- Final ordered Gerber: `gerber/grow light gerber 1.0.2 2026-0711.zip`
- DRC: 0 active errors, 0 active warnings, and 1 graphic-related exclusion

The medium aluminum cup was evaluated first, and the board design began after selecting an 80 mm diameter. The `v1.0.2` Gerber manufacturing files were inspected and used to order the MCPCB. The KiCad stackup metadata was then updated to match the order specification. There are no active DRC errors or warnings; the only exclusion is for the unavailable library source of a board-embedded silkscreen graphic.

## Completed History

### 2026-07-13 — Stackup, DRC, and Order Status Finalized

- [x] Kept KiCad's 2-layer representation because of its even-copper-layer requirement, while using only `F.Cu` as real copper.
- [x] Recorded Aluminum MCPCB, 1.6 mm overall thickness, 0.035 mm `F.Cu`, `HAL SnPb`, white `F.Mask`, and black `F.Silkscreen` in the stackup metadata.
- [x] Decided to share the `footprints:` library from a common directory rather than duplicating it in the project.
- [x] Reran `Inspect -> Design Rules Checker` and confirmed that there were no errors.
- [x] Reviewed the warning for the board-embedded silkscreen graphic whose `Symbol:mark` library source was unavailable and excluded it with a comment as an intentional exception.
- [x] Finalized the board outline and hole positions based on the medium aluminum cup evaluation.
- [x] Approved `v1.0.2` as the final manufacturing release.
- [x] Inspected the outline, LED pads, power pads, solder mask, silkscreen, and NPTH data in a Gerber viewer.
- [x] Confirmed that the ZIP contains `F.Cu`, `F.Mask`, `F.Silkscreen`, `Edge.Cuts`, and the NPTH drill file.
- [x] Verified the six 3.2 mm NPTH holes and the central 5.3 mm NPTH hole.
- [x] Confirmed that the design does not require plated through holes.
- [x] Confirmed the 1-layer Aluminum MCPCB, 80 mm outline, and manufacturing specifications with the manufacturer.
- [x] Confirmed that the manufacturer supports the 0.6 mm minimum track width and the current copper clearances.
- [x] Ordered the MCPCB using the final `v1.0.2` manufacturing ZIP.

For any future PCB design or manufacturing-file change, increment the version and silkscreen date and create a new manufacturing ZIP.

### 2026-07-13 — Repository and Documentation Cleanup

- [x] Established the main `plant led.*` project files as the current source of truth.
- [x] Deleted the `wrong_via` variant and Dropbox conflict copies.
- [x] Updated documentation that still described the obsolete FR4 stage to reflect the current MCPCB design.
- [x] Standardized the project instruction filename as `AGENTS.md`.
- [x] Moved datasheets into `references/datasheets/`.
- [x] Moved reference images into `references/images/` and cleaned up their filenames.
- [x] Moved the QR source into `assets/qr.svg`.
- [x] Updated the mechanical enclosure from the Daiso small aluminum makgeolli cup to the medium size and reflected the change in the documentation.

### 2026-07-11 — v1.0.2 Design and Manufacturing Files

- [x] Finalized the 12 V supply and red-heavy LED configuration.
- [x] Configured the red channel as four parallel strings of five LEDs, with one 68 ohm resistor per string.
- [x] Configured the blue channel as one string of three LEDs with an 82 ohm resistor.
- [x] Placed 20 red LEDs and 3 blue LEDs on the circular 80 mm board.
- [x] Placed all components, tracks, and copper zones on `F.Cu`.
- [x] Applied 1.2 mm power tracks and 0.6 mm LED interconnect tracks.
- [x] Used the 2010 resistor bodies as physical jumpers to complete the 1-layer routing.
- [x] Added 24 `F.Cu` copper zones around the LEDs.
- [x] Placed six 3.2 mm M3 NPTH holes at a radius of approximately 22 mm from the board center.
- [x] Added a central 5.3 mm NPTH cable pass-through hole.
- [x] Added the `v1.0.2 2026-07-11` silkscreen marking.
- [x] Generated the `v1.0.2` Gerber ZIP.

### Before Development — Mechanical Verification and Manufacturing Direction

- [x] Measured the medium aluminum makgeolli cup before selecting the PCB size.
- [x] Selected an 80 mm PCB diameter based on the measurements.
- [x] Verified the mechanical fit of the 80 mm PCB with the cup.
- [x] Checked the six M3 holes and central cable hole for interference with the cup geometry.
- [x] Checked the available contact area between the PCB and cup.
- [x] Reviewed the external bracket and M3 fastening structure.
- [x] The original plan was `2-layer FR4 prototype -> 1-layer Aluminum MCPCB`.
- [x] Changed the plan to skip the FR4 prototype and proceed directly to a 1-layer Aluminum MCPCB.
- [x] Confirmed that the current design would not use FR4-style `B.Cu` heat-spreading copper or thermal vias.

