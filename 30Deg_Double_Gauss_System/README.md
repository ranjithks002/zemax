# 30° FOV Double-Gauss Imaging System: Design, Tolerance, and Thermal Analysis

An optimized 4-element industrial machine vision lens designed using Ansys Zemax OpticStudio 2026. This project bridges the gap between theoretical lens optimization, manufacturing viability (Monte Carlo yield analysis), and environmental optomechanical ruggedness.

## 1. Nominal Optical Performance
The system leverages a Double-Gauss architecture with an internal aperture stop to naturally cancel out asymmetrical aberrations like coma and lateral color.
* **Effective Focal Length (EFL):** 99.5 mm
* **Total Field of View (FOV):** 30° (±15° Half-FOV)
* **Aperture Speed:** f/2.98
* **Total Axial Length:** 132.99 mm

**Key Performance Metrics:**
* **RMS Spot Radius:** Highly consistent across the field, maintaining a crisp **8.51 µm** on-axis and expanding to only **14.77 µm** at the extreme 15° corner.
* **Distortion & Field Curvature:** Maximum geometric distortion is strictly controlled at **1.0284%**, satisfying the stringent non-warping requirements of automated inspection software. Field curvature is exceptionally flat (Sagittal = 0.298 mm, Tangential = 0.395 mm).
* **Contrast (FFT MTF) & Aberrations:** The Ray Fan plots display balanced S-curves indicative of well-corrected spherical aberration, supporting high spatial frequency contrast across the sensor plane.

![2D Layout View](30Deg_Double_Gauss_System/Simulation_Plots_and_Layouts/Layouts/2DLayout.png)
![Nominal Spot Diagram](Simulation_Plots/Nominal_Spot_Diagram.png)
![FFT MTF](Simulation_Plots/FFT_MTF.png)
![Field Curvature vs Distortion](Simulation_Plots/Field_Curvature_vs_Distortion.png)
![Ray Fan](Simulation_Plots/Ray_Fan.png)

---

## 2. Manufacturing Tolerance Analysis
To evaluate high-volume factory yield predictability, a 500-trial Monte Carlo simulation was executed across three separate fabrication tiers. Mechanical barrel misalignments - specifically element decenters (`TSDX`/`TSDY`) and element tilts (`TSTX`/`TSTY`)—were identified as the dominant "worst offenders" driving off-axis image degradation.

| Manufacturing Tier | Nominal On-Axis Spot | 90% Production Yield Spot Size | Viability Verdict |
| :--- | :--- | :--- | :--- |
| **Loose (Commercial)** | 8.51 µm | 39.00 µm | Fails standard CMOS sensor pixel-pitch requirements. |
| **Medium (Precision)** | 8.51 µm | 15.00 µm | **Optimal.** Excellent cost-to-performance balance for machine vision. |
| **High-Precision** | 8.51 µm | 10.00 µm | Elite optical performance, but drastically inflates assembly/machining costs. |

---

## 3. Environmental Thermal Sweep (20°C vs 40°C)
Industrial inspection lenses rarely operate in climate-controlled cleanrooms. The system was evaluated against a thermal delta of +20°C (transitioning from a 20°C baseline to a 40°C unconditioned factory floor) to observe the impact of geometric expansion and refractive index shifts (dn/dT).

| Field Angle | 20°C Baseline RMS Spot | 40°C Heated RMS Spot | Thermal Degradation Observation |
| :--- | :--- | :--- | :--- |
| **0° (On-Axis)** | 8.510 µm | 15.500 µm | Spot expansion driven by pure thermal defocus. |
| **5°** | 7.238 µm | 12.978 µm | Uniform thermal blur expansion. |
| **10°** | 9.570 µm | 10.862 µm | Minimal drift due to localized focal plane alignment. |
| **15° (Corner)** | 14.769 µm | 19.247 µm | Asymmetric flare growth; amplified off-axis coma. |

Thermal Conclusion:** The microscopic structural expansions heavily impact wave-front propagation, primarily manifesting as systematic focus drift. Deploying this imaging system on a hot factory floor requires an active optomechanical back-focus compensator or a low-expansion housing material to mitigate the 40°C thermal defocus blur.

![40C Spot Diagram](Simulation_Plots/40C_Spot_Diagram.png)

---

## How to Open the Files
1. Download the files inside the `LENS_Data_Files/` folder.
2. Open using **Ansys Zemax OpticStudio 2026 (Sequential Mode)**.
