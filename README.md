
# Design and Simulation of CMOS Inverter in Cadence Virtuoso




## Project Overview

This project involves the design, simulation, and analysis of a CMOS inverter using Cadence Virtuoso at the 90nm technology node.
#### Key Features
- CMOS Inverter Schematic designed using 90nm technology.

- Pulsed Input/Output Waveforms showing switching behavior.

- Voltage Transfer Characteristics (VTC) with extracted VOL, VOH, VIL, VIH.

- Noise Margin Calculation (NMH, NML) from VTC.

- Leakage Power calculation.

- Propagation Delay Analysis with TPHL and TPLH measurement.

- Layout Design with verification checks (DRC, LVS).
## 1. Introduction
CMOS (Complementary MOS) technology combines NMOS and PMOS transistors, enabling low power, high noise immunity, and scalability, making it the standard for digital VLSI.

A CMOS inverter uses a PMOS pull-up and NMOS pull-down, delivering rail-to-rail output and sharp switching, making it the basic building block of all digital circuits.

#### Advantages of CMOS:
- Very low static power

- Strong noise margins

- High density and scalability

- Efficient switching (balanced rise/fall times)


## 2. Tools & Technology
- **EDA Tool**: Cadence Virtuoso

- **Technology Node**: 90nm 

- **Simulations**: Analog Design Environment (ADE)

## 3. Design & Implementation
The CMOS inverter schematic was designed in Cadence Virtuoso using the 90nm technology library. The circuit consists of:

- PMOS transistor (top device): connected between VDD and output, acts as the pull-up network.

- NMOS transistor (bottom device): connected between output and GND, acts as the pull-down network.

- Common gate (Vin): drives both NMOS and PMOS simultaneously.

- Common drain (Vout): provides the inverter’s output.
- The PMOS width (W = 305 nm) is larger (x 2.5) than the NMOS width (W = 120 nm) to balance mobility differences between holes and electrons, ensuring symmetric rise and fall times.
### -View the [schematics](https://github.com/yaman-tewatia/CMOS-Inverter/tree/main/schematic) for this project.

## 4. Simulation Results

### A) Pulsed Input & Output Waveform
Shows inverter switching behavior.
### -View the [pulsed Input & Output waveform](https://github.com/yaman-tewatia/CMOS-Inverter/tree/main/waveforms/pulse_waveform.bmp) for this project.

### B) Voltage Transfer Characteristics (VTC)

Plot of input vs. output and extraction VOL, VOH, VIL, VIH.
(Supply Voltage 1.2V)

| Parameter                         | Symbol     | Value (V)       | Description                                      |
|-----------------------------------|------------|-----------------|--------------------------------------------------|
| Output HIGH voltage (min)         | VOH        | 1.05            | Minimum guaranteed logic HIGH at the output      |
| Output LOW voltage (max)          | VOL        | 0.084           | Maximum guaranteed logic LOW at the output       |
| Input LOW voltage (max)           | VIL        | 0.460           | Maximum input voltage recognized as logic LOW    |
| Input HIGH voltage (min)          | VIH        | 0.750           | Minimum input voltage recognized as logic HIGH   |
| Trip voltage (switching threshold)| VM | 0.585 (≈ VDD/2) | Input voltage at which inverter switches (V<sub>in</sub> = V<sub>out</sub>) |

### -View the [VTC curve](https://github.com/yaman-tewatia/CMOS-Inverter/blob/main/waveforms/VTC.bmp) for this project.

### C) Noise Margin Calculation
| Noise Margin Type | Symbol | Formula | Value (V)             |
|-------------------|--------|-----------|----------------------|
| Noise Margin (LOW)| NM_L   |  NM_L = VIL − VOL   |  0.376   |
| Noise Margin (HIGH)| NM_H  |  NM_H = VOH − VIH   | 0.300    |

### -View the [Noise margin calculation](https://github.com/yaman-tewatia/CMOS-Inverter/blob/main/noise%20margin/noise%20margin%20calculation.bmp) for this project.

### D) Regions of Operation (from Id–Vin curve)
- Low Vin: NMOS cutoff, PMOS linear → leakage only.

- Vin just above Vth_n: NMOS saturation, PMOS linear.

- Switching point (Id max): Both in saturation.

- Higher Vin: NMOS linear, PMOS saturation.

- High Vin (~VDD): PMOS cutoff, NMOS linear → output pulled low.
### -View the [Region of Operations](https://github.com/yaman-tewatia/CMOS-Inverter/tree/main/region%20of%20operation) for this project.

### E) Leakage Power Calculation
| Parameter                     | Value     |
|-------------------------------|-----------|
| NMOS OFF current (`Inmos_off`) | 46.68 nA  |
| PMOS OFF current (`Ipmos_off`) | 27.03 nA  |
| Supply Voltage (`VDD`)         | 1.2 V     |
| Avg. Leakage Current (`I_leakage`) | 36.85 nA  |
| Leakage Power (`P_leakage`)     | 44.22 nW  |

### -View the [Leakage power calculation](https://github.com/yaman-tewatia/CMOS-Inverter/blob/main/leakage%20power/leakage%20power.bmp) for this project.

### F) Propagation Delay
| Parameter                  | Value   |
|----------------------------|---------|
| tPHL (high-to-low delay)   | 6.7 ps  |
| tPLH (low-to-high delay)   | 6.4 ps  |
| Propagation Delay (tp)     | 6.55 ps |

### -View the [Tphl,Tplh curves](https://github.com/yaman-tewatia/CMOS-Inverter/tree/main/propagation%20delay) for this project.

### G) Layout & Verification
- The CMOS inverter layout was created in Cadence Virtuoso following **Micron 90nm design rules** for transistor sizing, spacing, and routing.
-  The design passed DRC and LVS checks, confirming consistency with the schematic.
#### Design Rules Followed (GPDK90)
| Parameter                  | Value            |
|----------------------------|------------------|
| Technology Node            | 90nm             |
| Nominal Power Supply (VDD) | 1.2 V            |
| Metal1-Metal1 Spacing      | 0.12 µm          |
| Nwell-Nwell Spacing        | 0.6/1.2 µm       |
| Contact Size               | 0.12 × 0.12 µm   |
| Contact-Contact Spacing    | 0.14 µm          |
| Poly Width                 | 0.09 µm          |
| Poly-Poly Spacing          | 0.14 µm          |

### -View the [Layout](https://github.com/yaman-tewatia/CMOS-Inverter/blob/main/layout/inverter_layout.png) for this project.

## 5) Conclusion
My project demonstrates the complete design and characterization of a CMOS inverter at 90 nm using Cadence Virtuoso. 
Key outcomes include schematic implementation, VTC analysis with noise margins, ID–V characterization, leakage power estimation, propagation delay measurement, and layout verification under Micron 90 nm rules. The inverter shows correct switching behavior, low leakage at logic levels, and clean DRC/LVS compliance, making it a reliable standard-cell building block for larger VLSI systems.


## 6) References
- N. Weste and D. Harris, CMOS VLSI Design: A Circuits and Systems Perspective, 4th ed., Pearson/Addison-Wesley, 2010.

- S. M. Kang and Y. Leblebici, CMOS Digital Integrated Circuits: Analysis and Design, 3rd ed., McGraw-Hill, 2003.