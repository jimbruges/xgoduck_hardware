# UNO Q + expansion-board cover

A lightweight clip-on cover for the Arduino UNO Q and Luwu expansion-board stack on the back of XGO-Duck. It is designed to **retrofit an already-built robot**: no printed part is modified, no screws are removed, and every cable stays connected.

<img src="images/cover_v5_cable_end.png" alt="UNO Q cover v5 over the UNO Q and expansion board, viewed from the open cable end" width="600">

## Files

| File | Contents |
| --- | --- |
| [unoq_cover_v5.stl](unoq_cover_v5.stl) | Print file |
| [unoq_cover_v5.step](unoq_cover_v5.step) | Cover solid for other CAD tools |
| [unoq_cover_v5.solidcraft](unoq_cover_v5.solidcraft) | Editable SolidCraft design: cover feature history plus the UNO Q and expansion-board models it was fitted against |
| [xgoduck_assembly_with_cover.solidcraft](xgoduck_assembly_with_cover.solidcraft) | Whole-robot fit-check assembly (see below) |
| [images/](images/) | Renders used on this page |

## How the cover works

- **Covers both boards.** The shell wraps the UNO Q and the expansion board from the top of the shield down to the underside of the UNO Q's PCB, 1.2 mm walls with 0.4 mm clearance to the board outline (≈ 72.6 × 57.4 × 26.2 mm overall).
- **Clip-on, tool-free.** Two snap tabs on each long side carry a ramped lip that rides over the expansion-board edge and catches 0.6 mm under it; ribs from the roof rest on the board's top edge so the cover cannot be pushed further down. Pull the tabs outward to remove it.
- **Cable end fully open.** The servo, Molex and battery connectors and the UNO Q USB‑C all sit on one edge (facing the neck on the robot); that end is left open so no cable is rerouted. Corner tabs locate the cover sideways.
- **Other openings.** Power-switch access, the expansion board's DC barrel jack, the connector on the UNO Q's opposite edge, and roof vent slots.
- **Mass** about 12–13 g in PLA/PETG.

### Printing

Roof down, no supports. PETG is preferred for the snap tabs (≈ 1 % bending strain); PLA works but tabs may fatigue with repeated removal.

### Assumptions to check on your robot

| Assumption | Why it matters |
| --- | --- |
| Shield sits on standard 2.54 mm headers, its PCB 11.0–12.6 mm above the UNO Q top face | Snap-lip height |
| Nothing behind the UNO Q protrudes past the board outline | Wall length toward the body |
| Roof clearance of 1.3 mm over the DC jack (tallest part) | Roof height |

## Whole-robot fit check

`xgoduck_assembly_with_cover.solidcraft` places the cover on a complete robot so clearances can be inspected:

| Component | Source |
| --- | --- |
| Robot links (trunk, legs, neck, head) | Zero-pose link meshes from the [xgoduck_rl](https://github.com/LuwuDynamics/xgoduck_rl) MuJoCo model (`robot/xgoduck/robot_walk.xml`) |
| UNO Q | Arduino's official simplified STEP (ABX00162) |
| Expansion board | [PCBA/ArduinoUnoQ.step](../../PCBA/ArduinoUnoQ.step) |
| Battery case | [structure/battery.stl](../../structure/battery.stl), registered onto the trunk with [structure/body.stl](../../structure/body.stl) (shared CAD frame) |
| Battery | Two 18650 cells (Ø18.5 × 65.5 mm incl. wrap) as a 2S 8.4 V pack, with a series nickel strip |

<img src="images/xgoduck_assembly_rear.png" alt="Full XGO-Duck assembly with the orange UNO Q cover on its back" width="480"> <img src="images/battery_pack_in_case.png" alt="Two 18650 cells seated in the battery case behind the UNO Q stack, legs and cover hidden" width="420">

Results in SolidCraft:

- No interference between the cover and the trunk, battery, boards, neck or legs at the zero pose; ~9 mm to each thigh.
- With a leg rolled fully inward (−22° hip roll) the thigh still stays ≥ 10.7 mm forward of the cover.
- The 2S pack fits the case cavity (39.1 × 18.6 × 67.1 mm) with ~1 mm side, 0.55 mm rear and 1.3 mm end clearance. Protected 18650 cells (often 67–69 mm long) will **not** fit; use unprotected cells with a separate 2S BMS, which has no room at the cell ends.
- Hip pitch/yaw sweeps and combined poses were not simulated.

The UNO Q stack's stand-off from the body is an estimate (UNO Q underside connectors touching the trunk's electronics envelope); if your stack sits further out, the cover moves straight back with it.

### Measured mass

The complete robot **with battery, back case (this cover) and boards weighs 825 g** (measured).

## Credits

UNO Q 3D model © Arduino. Robot link meshes derive from the XGO-Duck simulation model by Luwu Dynamics, itself based on Microduck by Pollen Robotics — see [UPSTREAM.md](../../UPSTREAM.md) and [LICENSING.md](../../LICENSING.md) for the terms that apply to those models.
