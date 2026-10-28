# Need for Speed Underground 2 (NFSU2) — Car Stats & Comparison

Compare **31 cars** in Need for Speed Underground 2 using Excel spreadsheets with stock, fully upgraded and career Stage 1–5 configurations. Filter by career progress and regional availability, then compare power, power-to-weight ratio, mass, torque, grip and gearing to help choose your next car.

## Download

- [Download English spreadsheet](https://raw.githubusercontent.com/nikolay86rus/nfs-underground-2-car-stats/develop/NFSU2_Car_Selector_en.xlsx)
- [Download Russian spreadsheet](https://raw.githubusercontent.com/nikolay86rus/nfs-underground-2-car-stats/develop/NFSU2_Car_Selector_ru.xlsx)

The links download `.xlsx` files from the `develop` branch. Open the workbook in Excel. Apple Numbers import is suggested in the workbook but has not been tested directly.

## For AI agents

Use the **English workbook** as the data source for questions about NFSU2 car stats. This requires access to download files and a tool that can read Excel worksheets. The README sample below is not the full dataset.

1. Download and parse the workbook, then read **Guide** before answering. If downloading or parsing fails, say so; do not claim to have checked the data.
2. Choose the comparison sheet below. Keep stock, fully upgraded and career-stage configurations separate. Read headers and numeric cell values, not just screenshots or this README. For formula cells, read cached numeric results or calculate from the inputs. Power-to-weight in kW/t is `power in kW / mass in kg × 1000`. Do not treat formula text as a value or a missing cache as zero; report unavailable results if you cannot calculate them.
3. Apply the user's stage and region filters as described in **How to compare cars**. If either is unknown and affects the answer, ask or clearly label the scope used. For an ambiguous request such as “best car,” establish the metric or explain the trade-offs.
4. Use **Upgrade Unlocks** for package requirements, **Body and Aero** for body-part questions, and **Data** for source parameters. Do not treat every configuration in Data as available at the user's career stage.
5. Calculate and sort using full-precision numeric values; round only for display. Keep units, configuration and filters in the answer. Distinguish workbook values from your own derived comparisons.
6. Cite the workbook URL, worksheet and cell range for each comparison, plus the version used. For a reproducible version, resolve the `develop` commit SHA before downloading and replace `develop` in the raw URL with that SHA. If you cannot resolve it, record the branch URL and retrieval date, without claiming a fixed version.
7. Preserve the limitations below. The workbook does not establish measured acceleration times, actual top speeds, lap times or a universal race winner. If a question needs data absent from the workbook, state what is missing instead of inventing an answer.

Example request: “Using the English workbook, compare Stage 2 cars available in the EU by power-to-weight ratio. Include the filters, units, source cells and relevant limitations.”

## What is included?

| Worksheet | What it compares |
| --- | --- |
| Stock | All 31 cars without performance upgrades. |
| Fully Upgraded | All 31 cars with ordinary level 3 (Extreme) performance packages and standard body aerodynamics. Unique parts and custom tuning are excluded. |
| By Career Stage | Cars and upgrades available by the end of career stages 1–5, assuming all relevant unlock conditions for that stage have been met. |
| Guide | Instructions, metric definitions, sources and calculation limits. |
| Body and Aero | Notes on body parts, downforce and the scope of the comparison. |
| Data | Extracted parameters and assembled upgrade configurations. |
| Upgrade Unlocks | Performance package levels and their career requirements. |

The main comparison sheets include calculated power (kW), power-to-weight ratio (kW/t), mass (kg), torque (N·m), front and rear grip coefficients, theoretical gearing speed limit (km/h), physics drivetrain, regional availability and career unlock conditions.

## How to compare cars

1. Choose **Stock**, **Fully Upgraded** or **By Career Stage**.
2. Filter **Region** to `Both` plus `EU` or `NA`, depending on your version of the game.
3. On **By Career Stage**, filter **Comparison stage** to your stage, such as `2`. On **Stock** or **Fully Upgraded**, filter **Unlock stage*** to be less than or equal to your stage.
4. Use the table header dropdowns to sort by a metric, such as **Power-to-weight, kW/t**, from largest to smallest. Always sort the whole table so each car stays matched to its values.
5. Compare grip, drivetrain and gearing alongside power-to-weight. No single column establishes the best car for every race.

The stage comparison represents the **end-of-stage maximum**, so some listed upgrades may still require race wins or shop unlocks during your current stage. The Fully Upgraded sheet shows a car's future potential, even when those upgrades are not yet available in your career.

## Example: stock car stats

These values are taken from the English workbook's **Stock** sheet and rounded for readability. This is a sample, not a ranking.

| Car | Power (kW) | Power-to-weight (kW/t) | Mass (kg) | Torque (N·m) | Physics drivetrain |
| --- | ---: | ---: | ---: | ---: | --- |
| Peugeot 206 | 103.0 | 97.6 | 1,055 | 192.0 | FWD |
| Ford Focus ZX3 | 97.2 | 84.6 | 1,150 | 182.0 | FWD |
| Toyota Corolla GT-S | 83.7 | 86.3 | 970 | 130.0 | RWD |
| Nissan 240SX | 115.9 | 95.0 | 1,220 | 216.0 | RWD |
| Mazda MX-5 / Miata | 95.6 | 91.9 | 1,040 | 148.5 | RWD |

## Cars covered

The workbook covers 31 playable cars across the North American and European rosters. It excludes traffic vehicles.

| Manufacturer | Cars |
| --- | --- |
| Acura | RSX Type-S |
| Audi | A3, TT |
| Cadillac | Escalade |
| Ford | Focus ZX3, Mustang GT |
| Honda | Civic Si |
| Hummer | H2 |
| Hyundai | Tiburon / Coupe |
| Infiniti | G35 |
| Lexus | IS 300 |
| Lincoln | Navigator |
| Mazda | MX-5 / Miata, RX-7, RX-8 |
| Mitsubishi | 3000GT, Eclipse, Lancer Evo VIII |
| Nissan | 240SX, 350Z, Sentra SE-R, Skyline GT-R |
| Opel / Vauxhall | Corsa |
| Peugeot | 106, 206 |
| Pontiac | GTO |
| Subaru | Impreza WRX STi |
| Toyota | Celica GT-S, Corolla GT-S, Supra |
| Volkswagen | Golf GTI |

The workbook marks the Civic and RSX as **NA**, the Peugeot 106 and Corsa as **EU**, and the remaining cars as **Both**. Executables and mods may change availability.

## Data sources and calculations

The workbook documents parameters extracted from `GlobalB.lzc`, decompressed from JDLZ. Its Guide reports that all 46 physics records and career blocks matched `GLOBALB.BUN`, although the complete files differ. Source file hashes are included in the Guide.

The documented extraction and calculation references are:

- [NFSTools GlobalLib](https://github.com/NFSTools/GlobalLib/tree/c303c4d9b4c29fa45493c88e8f6955178251b204/GlobalLib/Support.Underground2) for Underground 2 data structures.
- [NFSU2Unity physics_data_ref.py](https://github.com/chrystianfarias/NFSU2Unity/blob/864ba9d847503cb54125eb3cd129040b0e715ea2/docs/re/tools/physics_data_ref.py) for reconstructed physics assembly and calculations.
- [NFSU2Unity physics documentation](https://github.com/chrystianfarias/NFSU2Unity/blob/864ba9d847503cb54125eb3cd129040b0e715ea2/docs/re/physics-data.md) for physics parameters and behavior.
- [PryHUB JDLZ implementation](https://github.com/bdrtr/PryHUB/blob/c4a531e511e6ac3465b8bb7258884b82c158eeae/crates/gizmo-nfs/src/compression/jdlz.rs) for decompression.

Power is calculated as the maximum of `torque × rpm × 2π / 60`, converted to kW, using a nine-point torque curve with linear interpolation. Power-to-weight is calculated power divided by mass in tonnes.

## How to interpret the numbers

- **Power-to-weight is an acceleration proxy.** It is not a measured 0–100 time or the game's acceleration rating. Exact agreement with Dyno is not claimed.
- **Grip coefficients are not overall handling scores.** Track layout, weight transfer, inertia, suspension and driver inputs also matter.
- **The gearing speed limit is theoretical.** It is calculated from rev limit, driven-wheel circumference and gearing. Drag and insufficient power can prevent a car from reaching it.
- **Drivetrain describes game physics.** FWD, RWD and AWD follow the selected configuration's `TorqueSplitRear`, which transmission upgrades can change. These labels do not necessarily match the real vehicle.
- **Unlock stages are conservative.** When a car has two race conditions, the workbook uses the later stage and retains both conditions. Unlock logic has not been verified without `SPEED2.EXE`; starting Miata and Celica availability may differ from reference guides.
- **Custom race builds are outside this comparison.** Unique parts, tuning sliders, aero body parts, special Drag / Drift / Street X modifiers and active nitrous are excluded. The NOS package does not add to reported power.

Use these stats to shortlist cars for your career stage and preferred driving style, then compare their behavior on the track.
