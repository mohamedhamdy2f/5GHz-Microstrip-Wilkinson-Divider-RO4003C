# 5.0 GHz Equal-Split Microstrip Wilkinson Power Divider (Keysight ADS)

Complete end-to-end RF/Microwave design, full-wave electromagnetic (EM) co-simulation, EM-based retuning, 3D surface current visualization, and PCB fabrication package (Gerber RS-274X & DXF) for a **5.0 GHz Equal-Split Wilkinson Power Divider** ($Z_0 = 50\,\Omega$) implemented on **Rogers RO4003C LoPro** using **Keysight ADS (Momentum)**.

---

## Final Performance Summary (`V2` — Selected Design at 5.000 GHz)

| Parameter | Value at 5.000 GHz | Target / Benchmark |
| :--- | :---: | :---: |
| **Input Return Loss** `dB(S(1,1))` | **-19.500 dB** | < -15 dB |
| **Output Return Loss** `dB(S(2,2))` | **-14.158 dB** | < -14 dB |
| **Port-to-Port Isolation** `dB(S(2,3))` | **-20.780 dB** | < -20 dB |
| **Power Split / Insertion Loss** `S(2,1)` / `S(3,1)` | **-3.254 dB / -3.246 dB** | ~ -3.25 dB (0.008 dB imbalance) |
| **Phase Balance** `Phase(S(2,1))` / `Phase(S(3,1))` | **45.947° / 45.751°** | 0.196° imbalance |
| **Final Dimensions (`V2`)** | `W50 = 1.84 mm`, `W70 = 1.18 mm`, `Lh = 5.6 mm` | `1.16 mm` gap for `0805` 100 Ω SMD |

---

## Substrate Stackup

* **Material:** Rogers `RO4003C LoPro`
* **Dielectric Thickness ($H$):** `0.831 mm` (`~32 mil`)
* **Relative Permittivity ($D_k$):** `3.5`
* **Copper Cladding ($T$):** `0.035 mm` (`1 oz`)
* **Loss Tangent ($\tan\delta$):** `0.0024`
* **Ground Plane:** Full solid unetched bottom copper plane (no vias, no solder mask)

---

## Repository Structure (Organized by Engineering Phase)

Each phase folder contains a **detailed beginner-friendly Word report (`.docx`)**, a quick-read **`README.md`**, and all corresponding **simulation plots, layouts, and screenshots** inside its `images/` directory.

| Phase | Folder | What Was Accomplished |
| :---: | :--- | :--- |
| **01** | [`Phase_01_Theory_Specifications_and_Initial_Design`](./Phase_01_Theory_Specifications_and_Initial_Design) | Wilkinson divider theory (Even/Odd mode), governing equations ($70.71\,\Omega$ quarter-wave arms, $100\,\Omega$ resistor), RO4003C selection, and initial `V1` microstrip synthesis. |
| **02** | [`Phase_02_Baseline_EM_CoSimulation_V1`](./Phase_02_Baseline_EM_CoSimulation_V1) | Transition from schematic to 5-port Momentum EM Co-Simulation, fixing copper thickness loss, baseline `V1` results, and Smith Chart diagnosis ($Z_{in} = Z_0(1.180 - j0.280)$). |
| **03** | [`Phase_03_EM_Retuning_and_Version_Comparison`](./Phase_03_EM_Retuning_and_Version_Comparison) | Iterative EM retuning (`V1` → `V2` → `V3`), Even/Odd-mode parasitic capacitance trade-off analysis, full comparison table & chart, and locking `V2` as the final design. |
| **04** | [`Phase_04_Final_Layout_Cleanup_and_3D_Current_Visualization`](./Phase_04_Final_Layout_Cleanup_and_3D_Current_Visualization) | Fixing layout pin overlaps & misoriented resistor footprint, adding discrete 5 GHz Momentum point, and extracting 3D/Top-Down Surface Current maps (`0.000`–`9.901 A/m`). |
| **05** | [`Phase_05_Fabrication_Preparation_and_CAM_Export`](./Phase_05_Fabrication_Preparation_and_CAM_Export) | Dedicated fabrication cell (`06_Fabrication_Layout`), mechanical clearance checks (`16.68 mm` SMA spacing, `6 mm` feeds, `1.16 mm` 0805 gap), flush Board Outline, Gerber/DXF export, and BOM. |

---

## Quick Fabrication Checklist

* **Gerber Files:** `01_Top_Copper.gbr` (`cond:drawing`) + `02_Board_Outline.gbr` (`bond:drawing`), RS-274X, `mm`, Positive polarity.
* **DXF File:** AutoCAD 2004 Text DXF, `mm`, `Paths as polygons` (for LPKF / CNC milling).
* **BOM:** 3× `50 Ω SMA Female Edge-Launch` connectors + 1× `100 Ω 0805 SMD` resistor.
