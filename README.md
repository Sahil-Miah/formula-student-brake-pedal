# Formula Student Brake Pedal

A brake pedal designed in SolidWorks and tested with FEA, set as a design task by MCR Met Racing (the Formula Student team at Manchester Metropolitan University).

The pedal is a single flat plate of 6061-T6 aluminium, 5 mm thick, and weighs 137.7 g. It has a minimum factor of safety of 1.96 under a 2000 N load.

## The task

- Design a brake pedal that fits two joining holes.
- Meet Formula Student rules T6.1.9 (the pedal must not fail under 2 kN) and T6.1.10 (steel or aluminium, including the pad).
- Run FEA at 2000 N with a minimum factor of safety of 1.
- Make it so the team could build it in house.
- Judged on rule compliance first, then weight.

## Final design (V3)

| Item | Value |
| --- | --- |
| Material | 6061-T6 aluminium |
| Thickness | 5 mm |
| Mass | 137.7 g |
| Arm | 50 mm wide, 190 mm long |
| Pad | 10 mm by 60 mm |
| Joining holes | 22 mm and 25.4 mm, 30 mm apart |
| Fillet | 5 mm |

It is one flat plate, so it can be waterjet cut in one go and the holes reamed to size. No welding or bending is needed.

## Simulation set-up

- SolidWorks Simulation, static study
- Material: 6061-T6 (yield strength 275 MPa)
- Load: 2000 N on the pad, normal to its face
- Fixed geometry on both hole walls
- Fine mesh (blended curvature-based mesher)

## Results

I made the pedal thinner in steps and re-ran the same study each time.

| Version | Thickness | Mass | Peak stress | Minimum factor of safety |
| --- | --- | --- | --- | --- |
| V1 | 10 mm | 275.41 g | 70.2 MPa | 3.92 |
| V2 | 6 mm | 165.24 g | 116.6 MPa | 2.36 |
| V3 (final) | 5 mm | 137.70 g | 140.2 MPa | 1.96 |

V3 is 50% lighter than V1 and the factor of safety is still well above 1. I stopped at 5 mm because the factor of safety was getting close to the minimum, and the study does not check whether a thin plate could bend sideways (see Limits).

<img src="v3_1_Stress_and_FOS_Fine%20(1).png" alt="Stress and factor of safety, V3" width="700">
<img src="v3_2_FOS_Plot_Fine%20(1).png" alt="Factor of safety plot, V3" width="700">
<img src="v3_3_Fixtures_and_Load%20(1).png" alt="Fixtures and load, V3" width="700">

The full numbers for all three versions are in `BrakePedal_Results_SahilMiah (2).xlsx`.

## Rules check

| Rule | Status |
| --- | --- |
| T6.1.9 (2 kN, no failure) | Met in the simulation |
| T6.1.10 (steel or aluminium, pad included) | Met, the whole pedal is 6061-T6 |
| T6.2.1 (Brake Over-Travel Switch) | Not added. It was optional for this task and would be added when the pedal is fitted into the pedal box |

## Limits

- The study is static only. It does not check buckling (a thin plate bending sideways), fatigue or vibration.
- The load is applied as one force on the pad face, not as a real foot load.
- There is no Brake Over-Travel Switch tab yet.
- The pedal has not been made or tested in real life.

## Next steps

- Add lightening holes where the stress is low and re-run the study.
- Make the pad wider. It is only 10 mm by 60 mm now.
- Add a tab for the Brake Over-Travel Switch.
- Check buckling before going any thinner.

## Files

- `BrakePedal_SahilMiah_V3.SLDPRT`: SolidWorks part
- `BrakePedal_SahilMiah_V3.STEP`: STEP file, opens in any CAD software
- `v3_1_Stress_and_FOS_Fine (1).png`, `v3_2_FOS_Plot_Fine (1).png`, `v3_3_Fixtures_and_Load (1).png`: simulation screenshots
- `BrakePedal_Results_SahilMiah (2).xlsx`: results for all three versions

## Author

Sahil Miah, MEng Mechanical Engineering, Manchester Metropolitan University.
