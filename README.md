# Ohmic vs Non-Ohmic Lab: Potentiometer + LED Build Guide

Group project for **GPII Lab 1: Investigating Ohmic and Non-Ohmic Materials** (Dapdap High School).
Everything runs in the browser. Open `index.html` (or turn on GitHub Pages). The 3D page loads three.js from a CDN, so it needs internet once.

## What the pages do

- **Live schematic (`index.html`):** spin the pot knob, drag the V1 slider (0–6 V), open or close S1, pull J4 or J5 to isolate a branch. The LED glows in rainbow colours in proportion to its current.
- **Meters:** the Ammeter and Voltmeter toggles blank the displays (shown as OFF). The meters stay wired, so the circuit is unchanged.
- **3D breadboard (`3d.html`):** dark workbench, drag the real-looking 3-pin pot to spin it, build up step by step, meter screens show live readings, rainbow LED lights from the simulated current.

## Folder index

```
ohmic-lab/
├── .gitignore
├── README.md                  <- all instructions (this file)
├── index.html                 <- materials tick-list, 15 wiring steps, live schematic (knob + 0-6 V slider)
├── 3d.html                    <- 3D breadboard: spin the 3-pin pot, build step by step
├── assets/
│   ├── circuit-reference.png  <- the circuit we build. Do not change it.
│   └── potentiometer.png      <- photo of the 3-pin pot
└── lab-sheet/
    └── GPII-LAB-1-Investigating-Ohmic-and-Non-Ohmic-Materials.docx
```

## Put it on GitHub

1. Create a new repository on github.com and upload this whole folder (or `git init`, `git add .`, `git commit`, `git push`).
2. Settings → Pages → deploy from branch `main`, folder `/ (root)`. Your groupmates open the page link.

## Reading the 3-pin potentiometer (pins 1-2-3)

| Pin | Name | In this circuit |
|---|---|---|
| 1 | one end of the track | **not connected**, leave the hole empty |
| 2 (middle) | wiper | jumper **J1** to the + rail |
| 3 | other end of the track | jumper **J2** to the − rail |

Which end pin is 3? Put a multimeter on Ω between the middle pin and one end pin and turn the knob clockwise. The end pin whose reading **falls toward 0 Ω** is pin 3. Start with the knob fully counter-clockwise (pin 2↔3 about 10 kΩ).

## The circuit (as drawn in `circuit-reference.png`, unchanged)

| Node | Connected together |
|---|---|
| V1 (+) | V1 +, S1 input, P1 pin 2 (wiper) |
| After S1 | S1 output, ammeter (+) |
| Node A | ammeter (−), R1 100 Ω, 220 Ω → LED anode, voltmeter (+) |
| Node B (ground) | V1 −, P1 pin 3, R1, LED cathode, voltmeter (−) |
| P1 pin 1 | not connected |

## Materials checklist

- [ ] Potentiometer 10 kΩ, 3 pins
- [ ] Half-size breadboard (30 columns)
- [ ] Adjustable 0–6 V DC supply (or 4×AA pack, see Known limits)
- [ ] SPST switch (S1)
- [ ] Resistor 100 Ω (R1)
- [ ] Resistor 220 Ω
- [ ] Red LED
- [ ] 2 digital multimeters (one DC mA, one DC V) with leads
- [ ] 5 jumper wires (J1–J5) plus 2 spare
- [ ] Alligator-clip leads
- [ ] Graph paper and the lab sheet

## Wiring steps (power off, S1 open)

Columns 1–30. The five holes a–e of one column are connected. Rails: top red row = **+**, next row = **−**. Row a is next to the rails, row e next to the centre gap. Rail holes: use the one in the same column number as the jumper.

1. **Pot** in row e: pin 1 → `col 3`, pin 2 (wiper) → `col 4`, pin 3 → `col 5`. Knob fully counter-clockwise.
2. **S1** (open): legs in `col 9` and `col 11`, row e.
3. **R1 100 Ω**: `col 14 row c` ↔ `col 18 row c`.
4. **220 Ω**: `col 14 row d` ↔ `col 21 row d`.
5. **LED**: long leg (anode) `col 21 row b`, short leg (cathode) `col 24 row b`.
6. **J1**: `col 4 row a` → + rail.
7. **J2**: `col 5 row a` → − rail.
8. **J3**: `col 9 row a` → + rail.
9. **J4**: `col 18 row a` → − rail.
10. **J5**: `col 24 row a` → − rail.
11. **Ammeter** (DC mA): red → `col 11 row a`, black/COM → `col 14 row a` (this is Node A).
12. **Voltmeter** (DC V): red → `col 14 row e`, black/COM → − rail (col 16).
13. **Check, power still off:** meter in Ω between + and − rails reads about 10 kΩ. If it reads 0 Ω, re-check J1, J2 and the pot pins.
14. **V1**: red → + rail, black → − rail (col 1). Set 0 V.
15. Close S1 and raise V1 in 0.6 V steps to 6.0 V, recording voltage and current.

## Test procedure

- **Component A (resistor):** pull J5, run the 0–6 V steps, fill Data Table 1.
- **Component B (LED):** put J5 back, pull J4, run the steps, fill Data Table 2.
- Plot both I-V curves and finish the analysis in the lab sheet.

## Known limits (read before building)

- As drawn, P1 uses pin 2 and pin 3 only, so it is a variable resistor across V1. **V1 sets the voltage at Node A**; the knob only changes pot current.
- **Fully clockwise puts about 0 Ω across the supply.** Keep the knob counter-clockwise.
- A fixed 4×AA pack cannot step 0–6 V with this circuit. Use an adjustable 0–6 V supply.
- The voltmeter reads across the whole LED branch (220 Ω + LED).
- Never exceed 6.0 V.

## Suggestions and improvements (none change the circuit)

- Mark the pot's fully counter-clockwise start position with tape.
- If your supply has a current limit, set it near 100 mA to protect the pot, LED and ammeter.
- Take three readings per voltage step and average them.
- Use solid-core wire and seat parts fully to avoid contact resistance.
- Tape flags J1–J5 on the jumpers and photograph the final board for the report.
- Zero both meters first and use the 200 mA range on the ammeter.
- Add a LICENSE file and your names below before sharing the repo.

## Open questions

1. Is V1 an adjustable supply or the fixed 4×AA pack?
2. Is the pot 10 kΩ (B103) with pins that fit the breadboard?
3. Do both meters have a mA jack and a V jack?
4. Should “meter off” ever mean physically removed? It would break the loop, so it only blanks the display now.
5. Do you want a data table in the page with CSV export?

## Team

Add names and roles here.
