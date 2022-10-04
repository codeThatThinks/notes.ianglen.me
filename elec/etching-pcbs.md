---
title: DIY PCB Etching
parent: Electrical Engineering
---

# DIY PCB Etching with Toner Transfer Method

## Overall Procedure

1. Export design from EDA software.
2. Transfer design onto copper clad using a laminator.
3. Etch exposed copper to create circuit.
4. Drill holes.
5. Double sided boards: repeat transfer and etch for bottom side.
7. Trim to final board dimensions.
8. Apply soldermask and expose.
9. Double sided boards: repeat soldermask for bottom side.
10. Tin all exposed copper.


## Design Rules

* Minimum trace width: 0.3 mm
* Minimum trace clearance: 0.2 mm
* Minimum pour width: 0.3 mm
* Pour clearance: 0.4 mm
* Thermal spoke width: 0.5 mm
* Thermal clearance: 0.4 mm
* Via hole diameter: 0.4 mm
* Via pad diameter: 1.5 mm
* Minimum soldermask width: ?
* Soldermask clearance: ?


## Transfer Procedure

1. Warm up laminator to 325°F.

2. Export design from EDA software as SVG or PDF.
    * __For top layer:__ mirrored; small drill marks; include board edge
    * __For bottom layer:__ actual size drill marks; include board edge
    * Use Inkscape to center it on the page.

3. Prepare transfer paper.
    * Cut out light-colored magazine paper slightly larger than board size
    * Using kapton tape, tape the magazine paper onto regular paper
    * Tape the full width of the magazine paper at the top
    * Tape a small portion of the width at the bottom
    * Print out the design on regular paper to help with alignment
    * Wipe magazine paper with alcohol

4. Print design on transfer paper.
    * Paper type: plain paper
    * Quality: 1200 DPI
    * Toner safe: off

5. Prepare copper clad.
    * Scrub copper with Scotch-Brite and dish soap
    * Rinse and dry
    * Wipe with copper acetone

6. Transfer using the laminator.
    * Tape transfer paper to copper using kapton tape
    * Run through laminator for at least 10 minutes
    * Change position every so often to ensure even transfer
    * Do not let copper clad cool down after laminating

7. Remove transfer paper.
    * Soak in hot water until transfer paper is visibly wetted.
    * Gently rub off transfer paper

8. Touch up any issues with a Sharpie or paint pen.

9. Mask off any remaining areas on the copper clad.
    * Reduce the amount of copper needed to be etched as much as possible
    * Use packaging tape or kapton tape
    * Iron out any bubbles and make sure tape is adhered around edges and holes


## Etch Procedure

1. Make etchant.
    * Mix one part vinegar with one part hydrogen peroxide
    * Note: hydrogen peroxide must be fresh
    * Add salt until solution is saturated

2. Warm up etchant to at least 100°F.

3. Etch copper clad.
    * It will take 30 seconds before enough dissolved copper is in the solution to start the fast etch
    * When fast etching, the correct solution will bubble continuously, turn a blueish-green, and form orange precipitate on copper
    * Every 10 seconds, wipe precipitate off of copper with paint brush or foam brush
    * Make sure not to damage toner with brush
    * Fiberglass will become exposed as the etch process finishes
    * Remove from solution as soon as all areas have completely etched
    * With correct solution at a warm temperature, process should take less than 15 minutes total

4. Rinse board with water to remove any remaining etchant.

5. Remove toner mask.
    * Wipe board with acetone
    * Completely remove all toner so that copper is bright and clean


## Soldermask Procedure

1. Export soldermask from EDA software as SVG or PDF.
    * __For top layer:__ do not tent vias
    * __For bottom layer:__ mirrored; do not tent vias
    * Use Inkscape to create 3 copies with 1/4" margin around each

2. Print out soldermask on transparency and cut out copies.

3. Add alcohol to UV paint to thin it.

4. Clean board with alcohol.

5. Add paint in the center of the board.
    * Do not spread out paint

6. Align all transparency layers and tape to acrylic.
    * Tape must be outside the edge of the board
    * Toner side of transparency should face up

7. Clean transparency with alcohol.

8. Slowly place acrylic on board.
    * Shim bottom acrylic and top acrylic to get correct soldermask thickness
    * Add weights to top acrylic
    * Soldermask shouldn't have any bubbles or thick spots

9. Expose for 20 minutes.

10. Carefully remove acrylic and clean pads with alcohol.
