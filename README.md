# MLA-868MHz-2.4GHz: Dual-Band PCB Antenna Project Report

## 1. Project Overview
This project presents an integrated Meander Line Antenna (MLA) designed for operation in sub-1 GHz (868 MHz ISM band) and 2.4 GHz frequencies. The design is derived from the Texas Instruments application note SWRA730 (*433 to 930-MHz and 2.4-GHz BOM Tunable PCB Antenna*).

The primary engineering goal is to evaluate the detuning effect resulting from using a non-standard PCB substrate thickness compared to the reference design, and to restore proper impedance matching at target operating frequencies via discrete BOM tuning.

## 2. Reference Geometry and Dimensions
The geometry follows the footprint specifications outlined in Texas Instruments SWRA730 documentation. The antenna is fed via a 50 Ohm miniature u.FL (IPEX) coaxial connector.

The design source project is located in:
`FilesProject/Antenna.PrjPcb`

### Reference Dimensions
<img src="https://raw.githubusercontent.com/Sidowsky-MM/MLA-868MHz-2.4GHz/main/FilesProject/screenshots/swra730_antenna_dims.png" alt="Reference Dimensions" width="100%"/>

Full path:
`FilesProject/screenshots/swra730_antenna_dims.png`

## 3. PCB Implementation and Stackup Analysis
The antenna is fabricated on a standard 2-layer FR-4 substrate. A substrate core thickness different from the reference 1.6 mm board was applied. Variations in dielectric height h alter the effective relative permittivity epsilon_eff and parasitic trace-to-ground capacitance.

### Copper Layers Layout
<img src="https://raw.githubusercontent.com/Sidowsky-MM/MLA-868MHz-2.4GHz/main/FilesProject/screenshots/layerviewPCBAntena.png" alt="PCB Copper Layers" width="100%"/>

Full path:
`FilesProject/screenshots/layerviewPCBAntena.png`

### 3D Model with u.FL Feed Point
<img src="https://raw.githubusercontent.com/Sidowsky-MM/MLA-868MHz-2.4GHz/main/FilesProject/screenshots/3dboardantenna.png" alt="3D Board View" width="100%"/>

Full path:
`FilesProject/screenshots/3dboardantenna.png`

## 4. Detuning Compensation and RF Measurements
Altering PCB thickness shifts the fundamental resonance frequency:
* Increased substrate thickness decreases capacitance to the ground plane, shifting the resonant frequency upward.
* Decreased substrate thickness increases parasitic coupling, pulling the resonant frequency downward.

Impedance compensation is achieved via a dedicated discrete matching network positioned between the u.FL connector and the feed terminal of the meander radiator.

### S11 Return Loss Measurement
<img src="https://raw.githubusercontent.com/Sidowsky-MM/MLA-868MHz-2.4GHz/main/FilesProject/screenshots/measurment.png" alt="S11 Measurement" width="100%"/>

Full path:
`FilesProject/screenshots/measurment.png`

The measured S11 parameter confirms deep return loss notches at both 868 MHz (S11 < -10 dB) and 2.4 GHz (S11 < -15 dB), proving that board thickness variations can be fully compensated via passive component selection.

## 5. Engineering Conclusions
1. Non-standard substrate thickness induces measurable resonance shift on meander line structures.
2. The SWRA730 topology successfully enables frequency correction strictly through BOM tuning without modifying copper track geometry.
3. Stable 50 Ohm matching is maintained at the u.FL connector interface for both operational bands.
