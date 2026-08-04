# Grow Light v1.0.2 Build Log

This document records the manufacturing, assembly, testing, and installation of the physical `v1.0.2` Grow Light board. The current KiCad design may contain changes made after this board was manufactured.

## 1. PCB Delivery and Inspection

The aluminum MCPCB was received from JLCPCB.

<img src="images/assembly/5213-pcb-received.jpg" alt="Grow Light v1.0.2 board received from JLCPCB" width="600">

During inspection, a few areas were found where the white surface resin coating had peeled away and exposed the copper underneath. The board was still considered usable. Protective resin will be applied to these areas later.

<img src="images/assembly/5214-surface-coating-damage.jpg" alt="Area with exposed copper caused by peeled surface resin" width="600">

## 2. Solder Paste Application

Solder paste was applied to the PCB pads using a watch oiler as a fine dispensing tool.

<img src="images/assembly/5215-solder-paste-tools.jpg" alt="Solder paste and watch oiler used for application" width="600">

After application, the solder paste covered the LED and resistor pads in preparation for component placement.

<img src="images/assembly/5221-paste-applied.jpg" alt="PCB after solder paste application" width="600">

## 3. LED Placement and Hot-Plate Reflow

The LEDs were placed on the pasted pads, and the board was positioned on the hot plate.

<img src="images/assembly/5222-leds-on-hot-plate.jpg" alt="LEDs placed on the PCB before hot-plate reflow" width="600">

At this stage, the resistor footprints were still empty. It was discovered during component placement that the resistors on hand were `2012 Metric (0805 Imperial)`, which had been mistaken for the required `5025 Metric (2010 Imperial)` package. The available resistors therefore did not match the intended PCB footprints.

The hot plate was first heated to approximately 120 °C. At this temperature, the solder paste began to soften and form rounded deposits.

<img src="images/assembly/5223-preheat-120c.jpg" alt="Solder paste beginning to soften at approximately 120 degrees Celsius" width="600">

The temperature was then raised to approximately 220 °C to complete the soldering process.

<img src="images/assembly/5224-reflow-220c.jpg" alt="PCB after reflow at approximately 220 degrees Celsius" width="600">

A temporary resistor arrangement was assembled by hand so that the board could be powered and functionally tested. At each affected footprint, the available `2012 Metric (0805 Imperial)` resistor was combined in series with a `3216 Metric (1206 Imperial)` `1R0` resistor. The two components were manually positioned end-to-end across the larger `5025 Metric (2010 Imperial)` land pattern. This arrangement physically bridged the intended footprint while adding 1 Ω to the resistance of each temporary path.

This hand-assembled configuration is only a temporary workaround for initial operation and testing. It will later be replaced with a single resistor of the correct value in the intended `5025 Metric (2010 Imperial)` package.

<img src="images/assembly/5236-temporary-resistor-workaround.jpg" alt="Temporary resistor arrangement used for functional testing" width="600">

## 4. Cleanup and Functional Test

After the board surface was cleaned, power was applied to verify operation. All red and blue LED channels illuminated during the test.

<img src="images/assembly/5235-functional-test.jpg" alt="Functional test after cleaning the assembled PCB" width="600">

## 5. Aluminum Cup Hole Layout

The mounting-hole positions were checked before drilling the aluminum makgeolli cup. The center hole was based on the M5 cable opening, and the six surrounding M3 mounting holes were positioned at a radius of 22 mm from the center.

<img src="images/assembly/5250-hole-spacing-kicad.jpg" alt="Checking the mounting-hole spacing in KiCad" width="600">

The hole pattern was then drawn on the aluminum cup.

<img src="images/assembly/5251-hole-pattern-marked.jpg" alt="Hole pattern marked on the aluminum cup" width="600">

Small indentations were made at the marked positions to keep the drill bit from wandering.

<img src="images/assembly/5252-drill-points-marked.jpg" alt="Drilling positions marked with small indentations" width="600">

One drop of cutting oil was applied before drilling.

<img src="images/assembly/5253-cutting-oil.jpg" alt="Cutting oil applied at the drilling position" width="600">

The center M5 hole was drilled first.

<img src="images/assembly/5254-center-hole-drilled.jpg" alt="Center M5 hole after drilling" width="600">

The remaining six M3 mounting holes were then drilled.

<img src="images/assembly/5255-all-holes-drilled.jpg" alt="Aluminum cup after all holes were drilled" width="600">

The completed hole pattern was checked against the PCB. There was a small amount of positional error, but the board and cup could still be assembled without redrilling the holes.

<img src="images/assembly/5256-pcb-hole-fit-check.jpg" alt="Checking the drilled holes against the PCB" width="600">

## 6. Thermal Interface Application

Thermal paste was applied between the aluminum MCPCB and the aluminum cup. Because the paste did not spread easily across the metal surface, it was later rolled into long strips, placed around the drilled holes, and compressed during assembly so that it could spread into a thin contact layer.

<img src="images/assembly/5257-thermal-paste-application.jpg" alt="Applying thermal paste to the back of the MCPCB" width="600">

## 7. Final Assembly and Installation

After assembly, the completed light was powered on and tested again.

<img src="images/assembly/5260-final-light-test.jpg" alt="Grow Light operating after final assembly" width="600">

The light was then installed in its intended growing area and powered on for normal use.

<img src="images/assembly/5261-installed-grow-light.jpg" alt="Grow Light powered on after installation" width="600">

## 8. Follow-up Work Identified After Assembly

- Replace the hand-assembled temporary resistor combinations with correctly sized `5025 Metric (2010 Imperial)` resistors.
- Re-evaluate the resistor values. The initial values may have been calculated too conservatively, so different resistor values should be tested while monitoring heat generation before selecting the final configuration.
- During the current preliminary observation, the lamp temperature did not exceed 34 °C even when the indoor ambient temperature was approximately 30 °C. This corresponds to a temperature rise of no more than approximately 4 °C under the observed conditions. Additional temperature testing with alternative resistor values is still required.
