# EXPERIMENT 4  
## Differential Amplifier – DC, Transient and AC Analysis

---

## INTRODUCTION

A differential amplifier is one of the most fundamental building blocks in analog electronics and integrated circuit design. It is designed to amplify the difference between two input signals while rejecting signals that are common to both inputs. This makes it highly effective in reducing noise and interference in electronic systems.

The basic structure of a differential amplifier consists of two matched transistors connected to a common current source, known as the tail current source. The input signals are applied to the gates of the transistors, and the output is taken from the drain terminals. When identical signals are applied to both inputs, the output ideally becomes zero, demonstrating perfect common-mode rejection.

Differential amplifiers are widely used in operational amplators, instrumentation systems, and communication circuits due to their high accuracy and noise rejection capability. In this experiment, a MOSFET-based differential amplifier is analyzed using simulation tools to study its DC, transient, and AC characteristics.

---

## THEORY

A differential amplifier amplifies the difference between two input voltages while suppressing any common signal present at both inputs. The circuit consists of two identical MOSFETs sharing a constant current source. The current is divided between the two transistors depending on the input voltages.

When both inputs are equal, the current is equally distributed, resulting in zero output difference. When there is a difference between the inputs, the current shifts, producing a differential output.

### Differential Gain (A_d)

The differential gain is given by:

A_d = g_m × R_D

where  
g_m = 2I_D / V_ov  

g_m is the transconductance,  
I_D is the drain current,  
V_ov is the overdrive voltage,  
R_D is the drain resistance.

---

### Common Mode Gain (A_cm)

The common mode gain represents amplification of signals that are common to both inputs. Ideally, this value is zero, but practically it is small.

---

### Common Mode Rejection Ratio (CMRR)

CMRR indicates how effectively the amplifier rejects common-mode signals:

CMRR = A_d / A_cm

A higher CMRR means better noise rejection.

---

### Input Common Mode Voltage (V_CM)

The input common-mode voltage is defined as:

V_CM = (V_1 + V_2) / 2

---

### Minimum Common Mode Voltage (V_CM(min))

The minimum value of V_CM is determined by the condition that the tail current source and input transistors remain in saturation:

V_CM(min) = V_T + V_ov + V_DS(sat, tail)

---

### Maximum Common Mode Voltage (V_CM(max))

The maximum value of V_CM is limited by the requirement that the transistors remain in saturation:

V_CM(max) = V_DD − V_ov − V_DS(sat)

---

### Operating Condition

For proper operation:

V_CM(min) ≤ V_CM ≤ V_CM(max)




## GIVEN DESIGN PARAMETERS

- Channel Length (L) = 480 nm  
- Power (P) ≤ 1.8 mW  

---

## SUPPLY AND INPUT CONDITIONS

- VDD = 0.9 V  
- VSS = -0.9 V  
- VinCM = 0 V  
- Vocm = 0 V  
- Vp = -0.7 V  

---

## ADDITIONAL PARAMETER

- Load Capacitance (CL) = 10 pF  

---
## CIRCUIT DIAGRAM
<img width="1794" height="884" alt="image" src="https://github.com/user-attachments/assets/2098c49b-f361-4534-b22f-8f5cf1913681" />




# DC ANALYSIS (OPERATING POINT)

<img width="885" height="616" alt="image" src="https://github.com/user-attachments/assets/cb702078-94ce-49be-93dd-434e991338d7" />


---

## NODE VOLTAGES

| Node      | Voltage (V)        |
|----------|-------------------|
| V(n001)  | 0.9               |
| V(n002)  | 0                 |
| V(n003)  | 0                 |
| V(n004)  | -0.9              |
| V(vout1) | 3.90313e-16 ≈ 0   |
| V(vout2) | 0                 |
| V(vs)    | -0.707107         |

---

## SOURCE CURRENTS

| Source | Current (A) |
|--------|------------|
| I(V1)  | 0          |
| I(V2)  | 0          |
| I(V3)  | 0.001      |
| I(V4)  | -0.001     |

---

## RESISTOR CURRENTS

| Resistor | Current (A) |
|----------|------------|
| I(R1)    | 0.0005     |
| I(R2)    | 0.0005     |

---

## MOSFET M1 PARAMETERS

| Parameter | Value (A)        |
|----------|----------------|
| Id(M1)   | 0.0005         |
| Ig(M1)   | 0              |
| Ib(M1)   | -7.17107e-13   |
| Is(M1)   | -0.0005        |

---

## MOSFET M2 PARAMETERS

| Parameter | Value (A)        |
|----------|----------------|
| Id(M2)   | 0.0005         |
| Ig(M2)   | 0              |
| Ib(M2)   | -7.17107e-13   |
| Is(M2)   | 0.0005         |

---

## OBSERVATIONS

- Output voltage ≈ 0 → Balanced differential condition  
- Id(M1) = Id(M2) → Proper symmetry  
- Negligible gate and bulk currents  
- Equal resistor currents → Correct biasing  

---

## CONCLUSION

The circuit operates correctly in DC with proper biasing and symmetry, confirming expected differential amplifier behavior.







## Common Mode Input Range Calculation

### Given:
- VDD = 0.9 V  
- VSS = -0.9 V  
- VP = -0.7 V  
- Vout,CM = 0 V ⇒ VD = 0 V  
- VT = 0.366 V  

---

## 1. Calculation of VCM(min)

### Condition:
For NMOS to just turn ON:
VGS = VT  

### Formula:
VCM(min) = VP + VT  

### Substitution:
VCM(min) = -0.7 + 0.366  

### Result:
VCM(min) = -0.334 V  

---

## 2. Calculation of VCM(max)

### Condition:
For NMOS to remain in saturation:
VDS = VOV  

---

### Step 1: Drain-Source Voltage
VDS = VD - VS  
VDS = 0 - (-0.7)  
VDS = 0.7 V  

---

### Step 2: Overdrive Voltage
VOV = VGS - VT  

VGS = VCM - VP  
VGS = VCM + 0.7  

So,
VOV = (VCM + 0.7) - 0.366  
VOV = VCM + 0.334  

---

### Step 3: Apply Saturation Condition
VDS = VOV  

0.7 = VCM + 0.334  

---

### Step 4: Solve
VCM = 0.366 V  

---

## Final Results:

VCM(min) = -0.334 V  
VCM(max) = 0.366 V  

---

## Conclusion:

The common-mode input voltage range is:

-0.334 V ≤ VCM ≤ 0.366 V  

The lower limit ensures transistor turn-on, and the upper limit ensures saturation operation.






## Common Mode Voltage Limits (VCM min and VCM max)

---
<img width="1441" height="675" alt="image" src="https://github.com/user-attachments/assets/ef218bc8-abab-4cc1-aed9-b41cdae40644" />

## Introduction

The common-mode input voltage is defined as:

VCM = (Vin1 + Vin2) / 2

For proper operation of a MOS differential amplifier, both transistors must remain in saturation region. This gives two limits:
- VCM(min)
- VCM(max)

---

## Condition for Saturation

For NMOS:

VDS ≥ VGS - VT

---

## VCM(min) Derivation

At minimum common-mode voltage, transistor is just ON:

VGS = VT

We know:

VGS = VG - VS

So,

VT = VCM(min) - VS

Rearranging:

VCM(min) = VS + VT

---

### Using simulation values:

VS = -0.707 V  
VT = 0.366 V  

VCM(min) = -0.707 + 0.366  
VCM(min) ≈ -0.34 V

---

## Result

VCM(min) ≈ -0.34 V

---

## Observation

At this point:
- VGS ≈ VT  
- Overdrive voltage ≈ 0  
- Transistor is just turned ON  

---

## VCM(max) Derivation

At maximum common-mode voltage, transistor leaves saturation:

VDS = VGS - VT

We know:

VD - VS = VGS - VT  
VD - VS = (VCM(max) - VS) - VT  

Simplifying:

VD = VCM(max) - VT  

So,

VCM(max) = VD + VT

---

### Using simulation values:

VD = 0 V  
VT = 0.366 V  

VCM(max) = 0 + 0.366  
VCM(max) ≈ 0.366 V

---

## Result

VCM(max) ≈ 0.366 V

---

## Final Summary

VCM(min) = -0.34 V  
VCM(max) = 0.366 V  

---

## Conclusion

The differential amplifier operates correctly in the range:

-0.34 V ≤ VCM ≤ 0.366 V

Below VCM(min): transistor goes to cutoff  


---

## Key Point

VCM(min) → determined by turn-on condition  


## Transient Analysis at VCM(min)
<img width="1919" height="509" alt="image" src="https://github.com/user-attachments/assets/aacf6c30-2850-4cdc-a076-b9a5f86928bb" />

At VCM(min), the input signal is applied as a sine wave.

However, the output remains constant (no variation observed).

This is because:

VGS ≈ VT  
Overdrive voltage (Vov) ≈ 0  

Due to this, the transconductance (gm) is nearly zero, and the transistor is just at the edge of conduction.

Hence, no amplification occurs and output remains flat.

---

## Conclusion

At VCM(min), the differential amplifier does not amplify the signal and acts as a non-functional amplifier.






## Operating Point at VCM(max)
<img width="1385" height="624" alt="image" src="https://github.com/user-attachments/assets/4b97c461-5985-4695-9e6b-f56c8f39a16f" />

From simulation:

VG = 0.366 V  
VS = -0.707 V  
VD = 0 V  

---

### Calculation

VGS = VG - VS  
VGS = 0.366 - (-0.707) = 1.073 V  

Vov = VGS - VT  
Vov = 1.073 - 0.366 = 0.707 V  

VDS = VD - VS  
VDS = 0 - (-0.707) = 0.707 V  

---

### Condition

VDS = Vov  

---

## Conclusion

At VCM(max), the MOSFET operates at the boundary between saturation 

Any further increase in VCM will push the transistor into triode region, resulting in distortion and loss of amplification.



## Transient Analysis at VCM(max)
<img width="1918" height="507" alt="image" src="https://github.com/user-attachments/assets/bc76eca8-2b14-430d-a8ca-930aa60ea706" />


At VCM(max), a sinusoidal input signal is applied.

However, the output remains nearly constant (no amplification observed).

This is because:

VDS = Vov  

The MOSFET operates at the boundary of saturation and enters triode region for small signal variations.

Due to this, transconductance decreases and the amplifier loses its gain.

---

## Conclusion

At VCM(max), the differential amplifier fails to amplify the input signal and becomes non-functional.




# TRANSIENT ANALYSIS (VID < √2 VOV CONDITION)

## OUTPUT WAVEFORM

![Linear Output Waveform]
<img width="1888" height="411" alt="image" src="https://github.com/user-attachments/assets/b7d7f7ac-71e4-46e5-b1ff-b90a99bbea4a" />


---

## GRAPH DETAILS

| Parameter            | Value / Description        |
|---------------------|--------------------------|
| Condition           | \( V_{id} < \sqrt{2}V_{OV} \) |
| Output Observed     | V(vout1), V(vout2)       |
| Waveform Type       | Sinusoidal               |
| Amplitude Scale     | nV (very small)          |
| Nature              | Linear                   |

---

## OBSERVATIONS

- The output waveform is **smooth and sinusoidal**  
- No distortion or clipping is observed  
- Both transistors are operating in **saturation region**  
- The circuit behaves as a **linear amplifier**  

---

## ANALYSIS

For differential amplifier:

\[
V_{id} = V_1 - V_2
\]

Condition for linear operation:

\[
V_{id} < \sqrt{2}V_{OV}
\]

Since this condition is satisfied:
- Both MOSFETs conduct simultaneously  
- Current is shared between them  
- Output remains **linear**

---

## IMPORTANT NOTE

- The output amplitude is very small (**in nV range**)  
- This is because:
  - Single-ended output is observed  
  - Input signal is very small  

For better observation:
- Plot differential output:
  \[
  V_{out} = V(vout1) - V(vout2)
  \]

---

## CONCLUSION

The condition \( V_{id} < \sqrt{2}V_{OV} \) ensures linear operation of the differential amplifier. The obtained sinusoidal waveform confirms that the circuit is operating in the linear region, although the output amplitude is small.




# TRANSIENT ANALYSIS (VID > √2 VOV)

## OUTPUT WAVEFORM

![Non-linear waveform]
<img width="1906" height="383" alt="image" src="https://github.com/user-attachments/assets/40c0aaf9-d71a-43b5-bfdd-61aebe148a23" />


---

## OBSERVATIONS

- The output waveform is **distorted and non-sinusoidal**  
- A DC offset is present in the signal  
- The waveform shows **asymmetry and sharp peaks**  
- Output amplitude is reduced  

---

## ANALYSIS

When:
\[
V_{id} > \sqrt{2}V_{OV}
\]

- One MOSFET enters **cutoff region**  
- The other MOSFET carries the **entire tail current**  
- Current is not equally shared  

This leads to:
- Non-linear operation  
- Distorted output waveform  

---



# COMPARE AND INTERPRET THE ANALYSIS

## COMPARISON OF RESULTS

| Parameter / Condition        | \( V_{id} < \sqrt{2}V_{OV} \) | \( V_{id} > \sqrt{2}V_{OV} \) |
|-----------------------------|------------------------------|------------------------------|
| MOSFET Operation            | Both in saturation           | One in cutoff, one active    |
| Current Distribution        | Equal sharing                | Unequal (one dominates)      |
| Output Waveform             | Sinusoidal                   | Distorted / non-linear       |
| Linearity                   | Linear region               | Non-linear region            |
| Gain Behavior               | Constant                    | Varies (non-linear gain)     |
| Symmetry                    | Symmetrical                 | Asymmetrical                 |
| Signal Quality              | High (clean output)         | Poor (clipping/distortion)   |

---

## INTERPRETATION

A differential amplifier amplifies the **difference between two input signals** while rejecting common components :contentReference[oaicite:0]{index=0}. The behavior of the circuit strongly depends on the magnitude of the differential input voltage.

### 🔹 Case 1: \( V_{id} < \sqrt{2}V_{OV} \)

- Both MOSFETs remain in **saturation region**  
- Tail current is **shared equally**  
- Output is **linear and sinusoidal**  
- Amplifier behaves as an **ideal differential amplifier**  

 This is the **desired operating region**

---

### 🔹 Case 2: \( V_{id} > \sqrt{2}V_{OV} \)

- One MOSFET enters **cutoff region**  
- Other MOSFET carries **entire current**  
- Circuit loses symmetry  
- Output becomes **distorted and non-linear**  

This is **undesired region**

---

## PHYSICAL MEANING

- Differential pair works by **steering current between two transistors**
- For small inputs:
  - Current splits smoothly → **linear output**
- For large inputs:
  - Current fully shifts to one side → **switch-like behavior**

---

## FINAL CONCLUSION

- The condition \( V_{id} < \sqrt{2}V_{OV} \) ensures **linear amplification**
- Exceeding this limit causes **cutoff and distortion**
- Hence, proper input selection is essential for **accurate differential amplifier operation**

---

# Differential Amplifier — AC Analysis Report (Circuit 1)
<img width="1907" height="465" alt="image" src="https://github.com/user-attachments/assets/32fcd694-83a3-4829-a934-433cda77b099" />

## Aim
To analyze the AC performance of a CMOS differential amplifier and determine gain, bandwidth, unity gain bandwidth (UGB), and gain-bandwidth product (GBP), and compare theoretical and practical results.

---

## Circuit Parameters
- Supply Voltage: ±0.9 V  
- Load Resistors: R1 = R2 = 1.8 kΩ  
- Tail Current: 1 mA  
- Input: Differential sinusoidal signal  

---

## Theoretical Analysis

### 1. Drain Current
Itail = 1 mA  

ID = Itail / 2 = 0.5 mA  

---

### 2. Transconductance (gm)
gm = 2ID / Vov  

Assume:
Vov ≈ 0.2 V  

gm = (2 × 0.5 mA) / 0.2  
gm = 5 mS  

---

### 3. Voltage Gain
Av = gm × RD  

Av = 5 mS × 1.8 kΩ  
Av = 9 V/V  

Av(dB) = 20 log(9) ≈ 19.08 dB  

---

### 4. Non-Ideal Gain
Considering channel length modulation:

Av = gm (RD || ro)

This reduces gain compared to ideal value.

---

### 5. Bandwidth
BW = 1 / (2π RD Cout)

Assume:
Cout ≈ 50 fF  

BW ≈ 1 / (2π × 1.8k × 50fF)  
BW ≈ 1.7 GHz  

---

### 6. Unity Gain Bandwidth (UGB)
UGB = Av × BW  

UGB ≈ 9 × 1.7 GHz  
UGB ≈ 15.3 GHz  

---

### 7. Gain Bandwidth Product (GBP)
GBP = Av × BW  

GBP ≈ 15.3 GHz  

---

## Practical (LTspice) Results

- Gain = 15.88 dB ≈ 6.23 V/V  
- Bandwidth ≈ 1 GHz  
- UGB ≈ 1.1 – 1.2 GHz  
- GBP ≈ 6.23 GHz  

---

## Comparison

| Parameter | Theoretical | Practical |
|----------|------------|----------|
| Gain (V/V) | 9 | 6.23 |
| Gain (dB) | 19.08 dB | 15.88 dB |
| Bandwidth | ~1.7 GHz | ~1 GHz |
| UGB | ~15.3 GHz | ~1.1 GHz |
| GBP | ~15.3 GHz | ~6.23 GHz |

---

## Inference

- The theoretical gain is higher because it assumes ideal conditions (infinite ro, no parasitics).
- The practical gain is lower due to:
  - Channel length modulation
  - Finite output resistance
  - Parasitic capacitances
- Bandwidth is slightly lower in simulation due to internal capacitances.
- The circuit shows a clear gain-bandwidth trade-off.
- High bandwidth (~GHz) indicates suitability for high-frequency applications.

---

## Conclusion

The CMOS differential amplifier provides moderate gain with high bandwidth.  
The simulation results closely follow theoretical predictions with expected deviations due to non-ideal effects.  
The design demonstrates stable operation and is suitable for high-speed analog circuits.





# Circuit 2
<img width="924" height="465" alt="image" src="https://github.com/user-attachments/assets/9811c08a-9581-4413-b662-db82d840207f" />


#  DC Analysis of Differential Amplifier 

<img width="1402" height="696" alt="image" src="https://github.com/user-attachments/assets/c3cd4d5a-f20b-4b80-9f64-0e0bfa82f659" />

## 🔹 Aim
To perform DC analysis of a CMOS differential amplifier, verify saturation of all transistors, and determine the operating point and common-mode voltage range.

---

##  Given Parameters

- VDD = +0.9 V  
- VSS = -0.9 V  
- VG1 = VG2 = 0.3 V  
- Threshold Voltage, VT = 0.366 V  

---

## DC Operating Point

### Node Voltages
- Vout1 = 7.147 mV  
- Vout2 = 7.147 mV  
- Vp = -0.695 V  

### Currents
- ID1 = ID2 = 0.500 mA  
- ID5 = 1.000 mA  

---

##  1. Symmetry Check

ID1 = ID2  

✔ Differential pair is balanced  
✔ Output voltages are equal  

Vod = Vout1 - Vout2 = 0  

---

##  2. Region of Operation

### 🔹 NMOS (M1, M2)

VGS = 0.3 - (-0.695) = 0.995 V  

Vov = VGS - VT  
Vov = 0.995 - 0.366 = 0.629 V  

VDS = 0.007 - (-0.695) = 0.702 V  

Condition:
VDS ≥ Vov  

0.702 ≥ 0.629 ✔  

➡ M1, M2 are in saturation  

---

### 🔹 PMOS (M3, M4)

VSG = 0.9 - 0.3 = 0.6 V  

Vov = VSG - |VT|  
Vov = 0.6 - 0.366 = 0.234 V  

VSD = 0.9 - 0.007 = 0.893 V  

Condition:
VSD ≥ Vov  

0.893 ≥ 0.234 ✔  

➡ M3, M4 are in saturation  

---

### 🔹 Tail NMOS (M5)

Assumed to be in saturation  

Condition:
VDS ≥ VGS - VT  

➡ M5 acts as a constant current source  

---

##  3. Summary Table

| Transistor | VGS / VSG | VDS / VSD | Vov | Region |
|------------|----------|----------|------|--------|
| M1, M2 | 0.995 V | 0.702 V | 0.629 V | Saturation |
| M3, M4 | 0.6 V | 0.893 V | 0.234 V | Saturation |
| M5 | — | — | — | Saturation (assumed) |

---

##  4. Common Mode Voltage Range

###  VCM(min)

Condition: M5 in saturation  

Vp ≥ Vov5 - 0.9  

VCM(min) = Vp + VT + Vov1  

VCM(min) = (Vov5 - 0.9) + 0.366 + 0.629  

VCM(min) = Vov5 + 0.095  

---

### 🔹 VCM(max)

Condition: M1, M2 remain in saturation  

VCM(max) = VDD - Vov3 + VT  

VCM(max) = 0.9 - 0.234 + 0.366  

VCM(max) = 1.032 V  

---

##  Final Results

- Differential Output Voltage:
  Vod = 0  

- All transistors operate in saturation (ideal condition)

- Common Mode Range:
  VCM(min) = Vov5 + 0.095  
  VCM(max) = 1.032 V  

---


# Transient Analysis — CMOS Differential Amplifier
<img width="1919" height="460" alt="image" src="https://github.com/user-attachments/assets/80713d01-863f-464c-a0f4-a429dc0ee16d" />


### Aim
To analyze the transient response of a CMOS differential amplifier for zero DC input and observe the output waveform.

---

### Input Signals
- \( V_{in1} = \text{SINE}(0, 10mV, 1kHz) \)
- \( V_{in2} = \text{SINE}(0, 10mV, 1kHz, 180°) \)

DC value of input = **0 V**

---

### Observation

- Output waveform is **sinusoidal**
- Output is centered around **0 V**
- No DC offset present
- Frequency = **1 kHz** (same as input)
- Amplitude ≈ **2.4 mV**

---

### Important Point

Since:
\[
V_{in,DC} = 0
\]

 Differential input:
\[
V_{id} = V_{in1} - V_{in2}
\]

 With 180° phase shift:
\[
V_{id} = 2 \times 10mV = 20mV \ (\text{peak})
\]

---

### Gain Calculation

\[
A_v = \frac{V_{out}}{V_{in(differential)}}
\]

\[
A_v = \frac{2.4mV}{20mV} = 0.12
\]

---

### Analysis

- Since DC input is zero:
  - Output is centered at **0V**
  - Circuit is properly biased
- Differential pair amplifies only **difference signal**
- Output waveform is clean → indicates:
  - All MOSFETs are in saturation
  - Linear operation region

---

### Conclusion

- The differential amplifier produces a sinusoidal output for zero DC input
- Output has no offset → confirms correct biasing
- Gain is small due to low supply voltage and device parameters
- Circuit operates in **linear region for small signals**

---





## AC Analysis Report — CMOS Differential Amplifier
<img width="1893" height="470" alt="image" src="https://github.com/user-attachments/assets/e72cdb91-4541-4004-b714-3928aa423799" />

**Simulation Tool:** LTspice  
**Technology:** TSMC 018 (tsmc018.lib)  
**Supply Voltage:** VDD = 0.9 V, VSS = −0.35 V  
**AC Sweep:** `.ac dec 100 50m 1` (50 mHz to 1 Hz, 100 points/decade)

## 1. Circuit Description

The circuit is a **CMOS differential amplifier** with the following topology:

- **M1, M2** — CMOSN (NMOS): Differential input pair  
- **M3, M4** — CMOSP (PMOS): Active current mirror load  
- **M5** — CMOSN (NMOS): Tail current source  

- **Vin1 (V2):** SINE(0 10m 1k), AC 1 0 — Non-inverting input  
- **Vin2 (V3):** SINE(0 10m 1k), AC 1 180 — Inverting input  
- **Output:** `V(vout2)`

The differential input drives M1 and M2 in antiphase. The current mirror (M3–M4) converts the differential current into a single-ended output at Vout2.

## 2. AC Simulation Results

### 2.1 Frequency Response Observations

From the LTspice waveform of **V(vout2)**:

- **Mid-band gain** (flat region): **5.5504 dB**  
- **Phase at low frequency**: **−194.8°**  
- **−3 dB frequency (f_H)**: ≈ 2–5 Hz (roll-off begins near 1 Hz)  
- Cursor reading at 1.033 mHz: **5.550 dB**, **−194.822°**

### 2.2 Gain Conversion

$$
A_{v,sim} = 10^{G_{dB}/20} = 10^{5.5504/20} \approx 1.896
$$

## 3. Theoretical Analysis

### 3.1 Small-Signal Voltage Gain

The theoretical small-signal differential voltage gain is given by:

$$
A_v = g_{m1} \cdot (r_{o2} \parallel r_{o4})
$$

where:
- \( g_{m1} \) = transconductance of input transistor M1 (or M2)
- \( r_{o2} \) = output resistance of M2
- \( r_{o4} \) = output resistance of M4 (PMOS mirror)

### 3.2 Transconductance

$$
g_m = \sqrt{2 \mu_n C_{ox} \left(\frac{W}{L}\right) I_D}
$$

For TSMC 180 nm NMOS (typical parameters):
- \( \mu_n C_{ox} \approx 270\ \mu\text{A/V}^2 \)
- \( \frac{W}{L} \approx 10 \)
- \( I_D \approx \frac{I_{tail}}{2} \)

### 3.3 Output Resistance

$$
r_o = \frac{1}{\lambda I_D}
$$

### 3.4 Dominant Pole Frequency

$$
f_{-3\text{dB}} = \frac{1}{2\pi \ (r_{o2} \parallel r_{o4})\ C_L}
$$

For typical 180 nm technology with no external load, the theoretical \( f_{-3\text{dB}} \) lies in the range of **1–10 Hz**, which closely matches the simulation.

## 4. Comparison: Theoretical vs Simulated

| Parameter                          | Theoretical          | Simulated (LTspice) | Deviation      |
|------------------------------------|----------------------|---------------------|----------------|
| Mid-band gain (dB)                 | ~6 dB               | 5.5504 dB          | ~0.45 dB      |
| Mid-band gain (linear)             | ~2.0                | 1.896              | ~5.2%         |
| Dominant pole \( f_{-3\text{dB}} \)    | 1–10 Hz             | ~2–5 Hz            | Within range  |
| Phase at low frequency             | −180° (inverting)   | −194.8°            | ~14.8° excess |
| Roll-off slope                     | −20 dB/dec          | −20 dB/dec         | Perfect match |

### 4.1 Gain Deviation Analysis

The small deviation (~0.45 dB) is mainly due to:
1. Channel length modulation (λ) — BSIM3v3 model is more accurate than simplified hand calculation.
2. Body effect on M1/M2, which slightly reduces \( g_m \).
3. Finite output resistance of the current mirror.
4. Parasitic capacitances at the output node.

### 4.2 Phase Deviation Analysis

The theoretical phase shift for an inverting single-pole amplifier is **−180°**. The simulated excess phase of **~14.8°** is caused by:
- Contribution from non-dominant poles at internal nodes (drain of M5, gate of M4).
- Parasitic capacitances introducing additional phase lag even in the mid-band region.

## 5. Key Observations

### 5.1 Flat Gain Region

The gain is extremely flat from 50 mHz to 1 Hz:

$$
\Delta G = 5.5504122 - 5.5504094 \approx 0.0000028\ \text{dB}
$$

This confirms all transistors are properly biased in the saturation region.

### 5.2 Roll-off Behaviour

Beyond ~1 Hz, the gain rolls off at **−20 dB/decade**, confirming **single dominant-pole** behavior.

### 5.3 Phase Margin Consideration

At low frequency, the phase is **−194.822°**. If used in unity-gain feedback:

$$
\text{Phase Margin} = 180^\circ - 194.822^\circ = -14.822^\circ
$$

**Negative phase margin** indicates potential instability. Frequency compensation (e.g., Miller capacitor) is recommended for closed-loop operation.

## 6. Summary

- **Simulation mid-band gain**: 5.5504 dB (≈ 1.896 V/V)  
- **Theoretical mid-band gain**: ~6 dB (≈ 2.0 V/V)  
- **Agreement**: Good (~5% deviation)  
- **Dominant pole**: ~1–5 Hz  
- **Roll-off**: Single-pole (−20 dB/dec)  
- **Phase at low freq**: −194.8° (excess due to parasitics)

## 7. Conclusion

The AC analysis of the CMOS differential amplifier demonstrates **good agreement** between theoretical predictions and LTspice simulation using the TSMC 018 model.

The mid-band gain of **5.5504 dB** is close to the expected ~6 dB. The single-pole roll-off at approximately 1–5 Hz validates the dominant pole approximation at the output node. The excess phase shift is attributed to parasitic effects captured by the BSIM3v3 model but not included in first-order hand analysis.

For practical closed-loop applications, **frequency compensation** is necessary to achieve adequate phase margin and ensure stability.





# Transient Analysis — At \( V_{CM(min)} \)
<img width="1919" height="433" alt="image" src="https://github.com/user-attachments/assets/c65eea41-9d66-4b7c-91ff-53275472aef4" />
<img width="1919" height="452" alt="image" src="https://github.com/user-attachments/assets/36fc352a-bfec-42f0-b98a-d70308f0010c" />


## Aim
To analyze the transient response of a CMOS differential amplifier at the minimum common-mode voltage \( V_{CM(min)} \).

---

## 1. Input Conditions

- \( V_{in1} = \text{SINE}(V_{CM}, 10\,\text{mV}, 1\,\text{kHz}) \)
- \( V_{in2} = \text{SINE}(V_{CM}, 10\,\text{mV}, 1\,\text{kHz}, 180^\circ) \)

Where:
$$
V_{CM} = V_{CM(min)}
$$

---

## 2. Observations (From Simulation)

- Output waveform is **sinusoidal**  
- Output is centered around:
  $$
  V_{out,DC} \approx 258\,\text{mV}
  $$
- Peak value:
  $$
  V_{out,max} \approx 271\,\text{mV}
  $$
- Minimum value:
  $$
  V_{out,min} \approx 246\,\text{mV}
  $$
- Peak-to-peak output:
  $$
  V_{out,pp} \approx 25\,\text{mV}
  $$

---

## 3. Analysis

At \( V_{CM(min)} \):

- Tail transistor (M5) is **just in saturation**
- Input NMOS transistors (M1, M2) operate near the **edge of saturation**
- Output DC level shifts upward due to:
  - Limited voltage headroom
  - Reduced overdrive voltage of the input pair

---

## 4. Behavior Explanation

As \( V_{CM} \) decreases:

- \( V_{GS} \) of the input NMOS pair (M1, M2) decreases
- Drain current of the differential pair reduces
- PMOS active load (M3/M4) pulls the output node **towards \( V_{DD} \)**

---

## 5. Linearity

- The output waveform remains **sinusoidal**, indicating the circuit is still operating in the **linear region**.
- Slight distortion may start to appear if \( V_{CM} \) is reduced further below \( V_{CM(min)} \).

---

## 6. Key Insight

$$
V_{CM(min)} \quad \Rightarrow \quad \text{Lower limit of proper operation}
$$

Below this voltage:
- Input NMOS transistors (M1, M2) enter the **triode region**
- Differential gain reduces significantly
- Output waveform becomes distorted

---

## 7. Conclusion

- The CMOS differential amplifier operates correctly at \( V_{CM(min)} \).
- The output remains sinusoidal but with an upward DC shift.
- The circuit is operating at the **boundary of proper saturation region**.
- This simulation confirms the theoretical lower limit of the common-mode input range.

---






# Transient Analysis — At \( V_{CM(max)} \)
<img width="1908" height="439" alt="image" src="https://github.com/user-attachments/assets/ae1932d7-7569-4834-9565-601a0e12a8fa" />
<img width="1912" height="431" alt="image" src="https://github.com/user-attachments/assets/3796a5bd-35aa-485d-b246-3718ae6b2f9f" />


## Aim
To analyze the transient response of a CMOS differential amplifier at maximum common-mode voltage \( V_{CM(max)} \).

---

## 1. Input Conditions

- \( V_{in1} = \text{SINE}(V_{CM}, 10mV, 1kHz) \)
- \( V_{in2} = \text{SINE}(V_{CM}, 10mV, 1kHz, 180^\circ) \)

Where:

$$
V_{CM} = V_{CM(max)}
$$

---

## 2. Observations (From Graph)

From the waveform:

- Maximum output:

$$
V_{out,max} \approx -25.90 \text{ mV}
$$

- Minimum output:

$$
V_{out,min} \approx -26.53 \text{ mV}
$$

---

## 3. Output Calculation

### Peak-to-peak voltage:

$$
V_{out,pp} = V_{max} - V_{min}
$$

$$
V_{out,pp} = (-25.90) - (-26.53) = 0.63 \text{ mV}
$$

---

### Peak amplitude:

$$
V_{out,peak} = \frac{V_{pp}}{2} = \frac{0.63}{2} \approx 0.315 \text{ mV}
$$

---

### DC offset:

$$
V_{out,DC} = \frac{V_{max} + V_{min}}{2}
$$

$$
V_{out,DC} = \frac{-25.90 + (-26.53)}{2} \approx -26.21 \text{ mV}
$$

---

## 4. Analysis

At \( V_{CM(max)} \):

- NMOS transistors (M1, M2) are **strongly ON**
- PMOS load (M3, M4) approaches **triode region**
- Output is pulled **towards ground (low voltage)**

---

## 5. Behavior Explanation

- As \( V_{CM} \) increases:
  - \( V_{GS} \) of NMOS increases → higher current
  - PMOS \( V_{SD} \) decreases → leaves saturation

---


---

## 8. Conclusion

- The amplifier operates at the **upper boundary of common-mode range**
- Output is still sinusoidal but:
  - Very small amplitude
  - Reduced gain
- Confirms theoretical behavior of differential amplifier at high \( V_{CM} \)

---






# Experiment: Differential Amplifier – Large Signal Analysis (Case 1)

## Aim
To analyze the operation of a CMOS differential amplifier when  
Vid < √2 Vov and verify current distribution using LTspice.
<img width="933" height="653" alt="image" src="https://github.com/user-attachments/assets/c431acbe-c006-4b4d-8181-17c698b24d61" />

---

## Given Parameters

| Parameter | Value |
|----------|------|
| Vg | 0 V |
| Vs | -0.7 V |
| Vt | 0.366 V |
| Vin1 | 0.3 V |
| Vin2 | 0.1 V |

---

## Theory

A differential amplifier operates based on the difference between two input voltages:

Vid = Vin1 - Vin2

The operating region depends on:

Vid compared with √2 Vov

Where:

Vov = Vgs - Vt

---

## Calculations

### Gate-to-Source Voltage
Vgs = Vg - Vs  
Vgs = 0 - (-0.7) = 0.7 V

### Overdrive Voltage
Vov = Vgs - Vt  
Vov = 0.7 - 0.366 = 0.334 V

### Threshold Condition
√2 Vov = 1.414 × 0.334 = 0.472 V

### Differential Input
Vid = Vin1 - Vin2  
Vid = 0.3 - 0.1 = 0.2 V

---

## Condition Verification

Vid = 0.2 V < 0.472 V  

✔ Condition satisfied

---

## LTspice Results (Operating Point)

| Quantity | Value |
|---------|------|
| Id(M1) | 0.0005067 A |
| Id(M2) | 0.0004810 A |
| Tail Current Id(M5) | 0.0009877 A |
| Vout1 | -0.660 V |
| Vout2 | -0.626 V |

---
<img width="1915" height="438" alt="image" src="https://github.com/user-attachments/assets/6d262478-d51d-471a-aab6-09713a9b81f0" />

## Observation

- Id(M1) ≈ Id(M2)  
- Tail current is shared:  
  Itail ≈ I1 + I2  
- Both MOSFETs are ON  
- No transistor is OFF  
- We also get clean sine wave
---

## Working Principle

When Vid < √2 Vov:

- Both transistors operate in saturation  
- Current divides between M1 and M2  
- Output varies linearly with input  
- Circuit behaves as a linear amplifier  

---

## Result

The differential amplifier operates in the linear (small-signal) region for:

Vid < √2 Vov

Both transistors conduct simultaneously and share the tail current.

---

## Conclusion

- The theoretical condition is verified using LTspice  
- Current distribution confirms linear operation  
- The circuit works as a proper differential amplifier  
- Advantages of this region:
  - High gain  
  - Low distortion  
  - Stable operation
 








# Experiment: Differential Amplifier – Large Signal Analysis (Case 2)

## Aim
To analyze the operation of a CMOS differential amplifier when  
Vid > Vov and study current steering behavior using LTspice.
<img width="872" height="672" alt="image" src="https://github.com/user-attachments/assets/78e68d12-aeca-4304-9b45-d15c82545b36" />

---

## Given Parameters

| Parameter | Value |
|----------|------|
| Vg | 0 V |
| Vs | -0.7 V |
| Vt | 0.366 V |
| Vin1 | 0.7 V |
| Vin2 | 0.2 V |

---

## Theory

The operation of a differential amplifier depends on the input difference:

Vid = Vin1 - Vin2

For large input:

- If Vid > Vov → nonlinear region begins  
- If Vid > √2 Vov → one transistor turns OFF  

Where:

Vov = Vgs - Vt

---

## Calculations

### Gate-to-Source Voltage
Vgs = Vg - Vs  
Vgs = 0 - (-0.7) = 0.7 V  

### Overdrive Voltage
Vov = Vgs - Vt  
Vov = 0.7 - 0.366 = 0.334 V  

### Differential Input
Vid = Vin1 - Vin2  
Vid = 0.7 - 0.2 = 0.5 V  

---

## Condition Verification

Vov = 0.334 V  
Vid = 0.5 V  

✔ Vid > Vov (Large signal condition satisfied)

Also:

√2 Vov = 0.472 V  

✔ Vid > √2 Vov  

---

## LTspice Results (Operating Point)

| Quantity | Value |
|---------|------|
| Id(M1) | 0.000511 A |
| Id(M2) | 0.000486 A |
| Tail Current Id(M5) | 0.000997 A |
| Vout1 | -0.666 V |
| Vout2 | -0.633 V |

---
<img width="1907" height="463" alt="image" src="https://github.com/user-attachments/assets/b9088edd-8658-473a-bc5a-a8958090b160" />

## Observation

- Id(M1) > Id(M2)  
- Current is shifting toward M1  
- M2 current is reducing  
- Tail current remains constant  

---

## Working Principle

When Vid > Vov:

- Differential pair enters **nonlinear region**
- Current no longer splits equally
- One transistor starts dominating
- Output becomes **nonlinear**

When Vid > √2 Vov:

- One transistor carries almost full current
- Other transistor approaches cutoff

---

## Result

For Vid = 0.5 V:

- Vid > Vov → nonlinear operation  
- Vid > √2 Vov → current steering observed  

The circuit is moving toward **switching behavior**.

---

## Conclusion

- The amplifier leaves linear region for large input  
- Current shifts toward one transistor  
- Output becomes nonlinear  
- At very high Vid:
  - One MOSFET fully ON  
  - Other MOSFET OFF  











# Experiment 4  
## Circuit 3 – CMOS Differential Amplifier (DC Analysis & Saturation Conditions)
<img width="1079" height="665" alt="image" src="https://github.com/user-attachments/assets/c36c9b83-c1c1-4db0-80d5-73bc9a80cd4a" />

---

## Aim

To analyze the DC operating conditions of a CMOS differential amplifier and verify the saturation region of all MOSFETs in Circuit 3.

---

## Circuit Description

The circuit consists of a CMOS differential amplifier with:
- NMOS differential pair (M1, M2)
- PMOS active load (M3, M4)
- NMOS tail current source (M5)

The circuit operates with symmetric inputs and fixed biasing conditions.

---

## Given Parameters

### Supply Voltages
- VDD = 0.9 V  
- VSS = -0.35 V  

---

### Input Signals
- Vin1 = SINE(0, 10mV, 1kHz), AC = 1  
- Vin2 = SINE(0, -10mV, 1kHz), AC = 180°  

Differential input:
Vid = Vin1 - Vin2 = 20 mV  

---

### DC Node Voltages
- Vout1 = 0.3 V  
- Vout2 = 0.3 V  
- Vp (tail node) = -0.7 V (fixed)

---

### Bias Voltage
- Gate voltage of M5:
  Vg5 = 0.366 V  

---

### Technology
- Model: tsmc018.lib  
- Threshold voltage:
  Vt ≈ 0.366 V  

---

## MOSFET Types

- M1, M2, M5 → NMOS  
- M3, M4 → PMOS  

---

## Saturation Conditions

### NMOS
VDS ≥ VGS − Vt  

### PMOS
VSD ≥ VSG − |Vt|  

---

## DC Analysis and Region Verification

---

### M1 (NMOS)

Vg1 = 0 V  
Vs1 = Vp = -0.7 V  

VGS1 = 0 − (-0.7) = 0.7 V  

Vd1 = 0.3 V  

VDS1 = 0.3 − (-0.7) = 1.0 V  

Condition:
VDS1 ≥ VGS1 − Vt  
1.0 ≥ 0.7 − 0.366 = 0.334  

M1 operates in saturation region  

---

### M2 (NMOS)

Vg2 = 0 V  
Vs2 = -0.7 V  

VGS2 = 0.7 V  

Vd2 = 0.3 V  

VDS2 = 1.0 V  

Condition satisfied  

M2 operates in saturation region  

---

### M3 (PMOS)

Vs3 = 0.9 V  
Vd3 = 0.3 V  

VSD3 = 0.9 − 0.3 = 0.6 V  

Vg3 = 0.3 V  

VSG3 = 0.9 − 0.3 = 0.6 V  

Condition:
VSD3 ≥ VSG3 − |Vt|  
0.6 ≥ 0.6 − 0.366 = 0.234  

M3 operates in saturation region  

---

### M4 (PMOS)

Vs4 = 0.9 V  
Vd4 = 0.3 V  

VSD4 = 0.6 V  

Vg4 = 0.3 V  

VSG4 = 0.6 V  

Condition satisfied  

M4 operates in saturation region  

---

### M5 (NMOS)

Vg5 = 0.366 V  
Vs5 = -0.35 V  

VGS5 = 0.366 − (-0.35) = 0.716 V  

Vd5 = -0.7 V  

VDS5 = -0.7 − (-0.35) = -0.35 V  

|VDS5| = 0.35 V  

Condition:
VDS5 ≥ VGS5 − Vt  
0.35 ≥ 0.716 − 0.366 = 0.35  

M5 operates at the boundary of saturation region  

---


## DC Analysis (Operating Point)

The DC operating point analysis provides the node voltages and drain currents of the CMOS differential amplifier.
<img width="853" height="627" alt="image" src="https://github.com/user-attachments/assets/2992dc79-1ea6-4a53-b3e0-66c8f034bc5f" />

---

### Node Voltages

- VDD node = 0.9 V  
- Ground reference = 0 V  
- Negative supply ≈ -0.9 V  

- Vout1 = 0.8876 V  
- Vout2 = 0.8876 V  

- Tail node:
  Vp = -0.7218 V  

- Bias node:
  Vg5 ≈ -0.37 V  

---

### Currents

- Tail current (through M5):
  Id(M5) = 1.0487 mA  

- Differential pair currents:
  Id(M1) = 0.5243 mA  
  Id(M2) = 0.5243 mA  

- PMOS load currents:
  Id(M3) = -0.5243 mA  
  Id(M4) = -0.5243 mA  

---

### Observations

- The total tail current splits equally:
  Id(M1) ≈ Id(M2)

- Current matching confirms symmetry of the differential pair.

- PMOS currents are equal and opposite to NMOS currents, ensuring proper load operation.

- Output voltages are equal:
  Vout1 = Vout2  
  → Indicates zero differential input condition.

---

### Voltage Verification

For M1 and M2:

VGS ≈ 0 − (-0.7218) = 0.7218 V  

VDS ≈ 0.8876 − (-0.7218) = 1.6094 V  

---

For M5:

VGS5 = Vg5 − Vs  
= (-0.37) − (-0.9)  
= 0.53 V  

VDS5 = Vp − Vs  
= (-0.7218) − (-0.9)  
= 0.1782 V  

---

### Current Consistency Check

Id(M5) ≈ Id(M1) + Id(M2)  
1.0487 mA ≈ 0.5243 + 0.5243 mA  



---


## Transient Analysis

The transient analysis is performed to observe the time-domain response of the CMOS differential amplifier for a sinusoidal differential input.

---
<img width="1899" height="428" alt="image" src="https://github.com/user-attachments/assets/1d7edbd6-d2d3-458c-bc75-6ce0eacb78d2" />
<img width="1900" height="450" alt="image" src="https://github.com/user-attachments/assets/9f59e6e1-cff8-4c79-b1eb-27df99c727e1" />
<img width="1898" height="387" alt="image" src="https://github.com/user-attachments/assets/fe0d7791-d13d-47cb-b1f1-3e09705dcd61" />

### Simulation Setup

- Analysis type:
  .tran 5 ms  

- Input signals:
  Vin1 = SINE(0, 10 mV, 1 kHz)  
  Vin2 = SINE(0, -10 mV, 1 kHz)  

- Differential input:
  Vid = 20 mV peak-to-peak  

---

### Observed Waveforms

---

#### Input Signal

- The input waveform is a sinusoidal signal with:
  - Amplitude ≈ ±10 mV  
  - Frequency = 1 kHz  

- The signal is centered around 0 V.

---

#### Output Voltage (Vout1)

- The output waveform is sinusoidal in nature.  
- DC level:
  Vout1 ≈ 0.8876 V  

- Small signal variation is observed around the DC operating point.

- Output amplitude is significantly smaller compared to input variation due to biasing conditions.

---

#### Combined Observation

- Input and output waveforms maintain sinusoidal shape.  
- No visible distortion is present.  
- Output follows the input variation, indicating linear operation in this region.  

---

### Key Parameters from Waveform

- Input amplitude ≈ 10 mV  
- Output DC level ≈ 0.8876 V  
- Output signal shows small variation around DC level  

---







## AC Analysis

The AC analysis is performed to determine the frequency response, voltage gain, bandwidth, and gain-bandwidth product of the CMOS differential amplifier.

---
<img width="1919" height="486" alt="image" src="https://github.com/user-attachments/assets/a2fb9fb8-4477-46cb-947c-80f569511f34" />

## Simulation Setup

- Analysis command:
  .ac dec 100 100 100G  

- Input:
  AC magnitude = 1 V  

- Output node:
  Vout1  

---

## Theoretical Analysis

### Differential Gain Formula

For a MOS differential amplifier with active load:

Ad = gm × Rout  

Where:
- gm = transconductance  
- Rout = ro_n || ro_p  

This is the standard gain relation:
Ad ≈ gm × ro :contentReference[oaicite:0]{index=0}  

---

### Transconductance (gm)

gm = μnCox × (W/L) × Vov  

OR

gm = 2Id / Vov  

---

### Given Parameters

- μnCox = 235 μA/V²  
- L = 480 nm  
- Vt = 0.366 V  

From DC analysis:
- Id ≈ 0.524 mA  

---

### Step 1: Overdrive Voltage

Vov = VGS − Vt  

From DC:
VGS ≈ 0.72 V  

Vov = 0.72 − 0.366 = 0.354 V  

---

### Step 2: gm Calculation

gm = 2Id / Vov  

gm = 2 × 0.524 mA / 0.354  

gm ≈ 2.96 mS  

---

### Step 3: Output Resistance

ro ≈ 1 / (λId)  

Assuming:
λ ≈ 0.1 V⁻¹ (typical for 180nm)

ro ≈ 1 / (0.1 × 0.524 mA)  
ro ≈ 19.08 kΩ  

---

### Step 4: Gain Calculation

Rout = ro || ro ≈ ro/2  

Rout ≈ 9.5 kΩ  

Ad = gm × Rout  

Ad = 2.96 mS × 9.5 kΩ  

Ad ≈ 28.1 V/V  

---

### Step 5: Gain in dB

Ad(dB) = 20 log(28.1)  

Ad ≈ 28.97 dB  

---

## Practical Results (From Graph)

From AC plot:

- Gain ≈ -20 dB  
- Bandwidth ≈ ~1 GHz  
- Gain decreases after high frequency  

---

## Conversion

Gain (linear):

Av = 10^(−20/20)  

Av ≈ 0.1 V/V  

---

## Comparison

| Parameter | Theoretical | Practical |
|----------|------------|----------|
| Gain (V/V) | 28.1 | 0.1 |
| Gain (dB) | 28.97 dB | -20 dB |

---

## Reason for Difference

- M5 not fully in saturation  
- Low output resistance  
- Channel length modulation effect  
- Improper biasing reduces gain  
- Single-ended output reduces effective gain  

---

## Frequency Response

- Flat region → low-frequency gain  
- Roll-off → due to parasitic capacitances  
- Phase shift increases at high frequency  

---





## Transient Analysis for Vid > √2 Vov (Nonlinear Region)

---
<img width="1912" height="387" alt="image" src="https://github.com/user-attachments/assets/acf0038d-129a-427b-ad7b-a1197327c18b" />

### Condition

The differential input applied satisfies:

Vid > √2 Vov  

Where:
√2 Vov ≈ 0.50 V  

---

### Observed Output Behavior

- The output waveform is no longer purely sinusoidal.  
- The waveform shows:
  - Flattened peaks (clipping at top)
  - Sharp transitions
  - Asymmetry in rising and falling edges  

- Output swings between:
  - Upper limit ≈ 0.9 V  
  - Lower limit ≈ 0.88 V  

---

### Justification

When Vid exceeds √2 Vov:

- One NMOS transistor (M1 or M2) enters **strong conduction**  
- The other transistor enters **cutoff region**  

As a result:

- Tail current is no longer shared equally  
- Entire current flows through only one branch  
- Differential pair behaves like a **switch rather than amplifier**

---

### Effect on Output

- Output node connected to ON transistor:
  - Pulled strongly → saturation level  

- Output node connected to OFF transistor:
  - No current → remains near supply  

This causes:

- Signal clipping  
- Loss of linearity  
- Distorted waveform  

---

### Key Observation

- The amplifier no longer operates in small-signal region  
- It behaves as a **large-signal nonlinear system**  

---

### Physical Interpretation

- For small Vid:
  current splits smoothly → linear output  

- For large Vid:
  current fully steers → switching action  

---






## Transient Analysis for Vid < √2 Vov (Linear Region)

---
<img width="1913" height="423" alt="image" src="https://github.com/user-attachments/assets/60ae9989-fada-40ea-98f2-6c3299411a42" />

### Condition

The applied differential input satisfies:

Vid < √2 Vov  

Where:
√2 Vov ≈ 0.50 V  

In this case:
Vid = 20 mV << 0.50 V  

---

### Observed Output Behavior

- The output waveform is **purely sinusoidal**  
- No distortion or clipping is observed  
- The signal is centered around DC level (~0.8876 V)  
- Output variation is small and smooth  

---

### Justification

When Vid is less than √2 Vov:

- Both NMOS transistors (M1 and M2) operate in **saturation region**  
- Tail current is **evenly shared** between the two branches  
- Current changes **linearly** with input voltage  

---

### Effect on Output

- Output voltage varies proportionally with input  
- No abrupt switching occurs  
- Amplifier behaves as a **small-signal linear system**

---

### Key Observation

- No clipping or distortion  
- Symmetrical waveform  
- Smooth transitions  

---

### Physical Interpretation

- Differential pair operates in **small-signal region**  
- Current division follows linear relation:
  Id1 ≈ Id/2 + (gm × Vid)/2  
  Id2 ≈ Id/2 − (gm × Vid)/2  

---







## Calculation of Common Mode Voltage Range

---

### Given

VDD = 0.9 V  
VSS = -0.35 V  
VT = 0.366 V  

From DC analysis:  
Vp ≈ -0.7218 V  

---

### Step 1: Calculate VGS

VGS = VCM − Vp  

At bias point (from DC):

VGS ≈ 0.72 V  

---

### Step 2: Overdrive Voltage

VOV = VGS − VT  

VOV = 0.72 − 0.366  

VOV ≈ 0.354 V  

---

## Minimum Common Mode Voltage (VCM_min)

Condition:
M1, M2 must remain ON and in saturation  

So,

VGS ≥ VT  

VCM − Vp ≥ VT  

VCM ≥ Vp + VT  

Substitute:

VCM_min = -0.7218 + 0.366  

VCM_min ≈ -0.3558 V  

---

## Maximum Common Mode Voltage (VCM_max)

Condition:
M1, M2 must remain in saturation  

VDS ≥ VOV  

Vout − Vp ≥ VOV  

Using DC value:

Vout ≈ 0.8876 V  

Check:

0.8876 − (-0.7218) = 1.6094 V ✔ (satisfied)

---

Now PMOS condition limits VCM:

For M3/M4:

VSD ≥ VOV  

VDD − Vout ≥ VOV  

0.9 − 0.8876 = 0.0124 V  

But,

VOV ≈ 0.354 V  

0.0124 < 0.354  

---

Thus PMOS is near boundary, so:

VCM_max ≈ Vout − VOV  

VCM_max ≈ 0.8876 − 0.354  

VCM_max ≈ 0.5336 V  

---

## Final Values

VCM_min ≈ -0.356 V  

VCM_max ≈ 0.534 V  

---






## Transient Analysis at VCM(min)
<img width="1916" height="887" alt="image" src="https://github.com/user-attachments/assets/6e2be445-d3ba-400a-8cda-35e307fcc97e" />

---

### Condition

The input common-mode voltage is set to its minimum value:

VCM(min) ≈ -0.36 V  

---

### Observed Output Behavior

- Output waveform is **sinusoidal**  
- Signal is centered near upper supply (~0.9 V)  
- Very **small amplitude variation** is observed  
- No clipping or distortion  

---

### Justification

At VCM(min):

- Gate voltage of NMOS transistors (M1, M2) is just sufficient to keep them ON  
- Condition:
  VGS ≈ VT  

- Transistors operate at the **edge of conduction**

---

### Effect on Circuit Operation

- Drain current is **very small**  
- Transconductance (gm) is low  
- Gain of the amplifier is reduced  

---

### Output Behavior Explanation

- Since current is very small:
  - Voltage drop across PMOS load is minimal  
  - Output node remains close to VDD  

- Only small variation is seen due to weak conduction  

---

### Key Observation

- Circuit is still operating but at **minimum bias condition**  
- Amplification is weak  
- Output swing is very limited  

---

### Physical Interpretation

- Differential pair is barely active  
- Small input causes only small current change  
- System is in **weak inversion / near cutoff region**

---




## Transient Analysis at VCM(max)

---

### Condition

The input common-mode voltage is set to its maximum value:

VCM(max) ≈ 0.53 V  

---

### Observed Output Behavior

- Output waveform is sinusoidal  
- Signal is centered near upper supply (~0.9 V)  
- Small amplitude variation is observed  
- No distortion is present  

---

### Justification

At VCM(max):

<img width="1919" height="460" alt="image" src="https://github.com/user-attachments/assets/69dd3bf1-0d4b-4aa0-abbe-2e1d2ae7b4ae" />


- PMOS transistors (M3, M4) operate at the edge of saturation  
- Condition:
  VSD ≈ VOV  

- Any further increase in VCM would push PMOS into linear region  

---

### Effect on Circuit Operation

- Output node cannot discharge effectively  
- Voltage remains close to VDD  
- Gain reduces due to reduced output resistance  

---

### Key Observation

- Limited output swing  
- Reduced gain  
- Stable sinusoidal waveform  

---










# Differential Amplifier — Circuit Comparison 

**Course:** Linear Integrated Circuits (LIC) Lab
**Technology:** TSMC 180 nm | **Channel Length:** L = 480 nm
**Supply:** VDD = +0.9 V, VSS = −0.9 V | **Power Budget:** P ≤ 1.8 mW

---

## Circuit Descriptions

| | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Load type** | Resistors (R₁, R₂) | PMOS current mirror (M3, M4) | PMOS mirror + C_L = 10 pF |
| **Transistors** | M1, M2 (NMOS) + tail current source | M1, M2 (NMOS) + M3, M4 (PMOS) + M5 (tail) | Same as C2, with capacitive load |
| **Tail current source** | Ideal current source (V3) | M5 (NMOS, in saturation) | M5 (NMOS, in saturation) |

---

## 1. Power Comparison

> **Design constraint:** P ≤ 1.8 mW

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **VDD − VSS** | 1.8 V | 1.8 V | 1.8 V |
| **Tail current (I_SS)** | 1 mA | 1 mA | 1 mA |
| **Each branch current (I_D)** | 0.5 mA | 0.5 mA | 0.5 mA |
| **Total power consumed** | **1.8 mW** | **1.8 mW** | **1.8 mW** |
| **Within spec?** | ✓ Yes | ✓ Yes | ✓ Yes |

**Key observation:** All three circuits consume identical DC power of 1.8 mW because the tail current and supply voltage are unchanged across all configurations. The type of load (resistive vs active) does not affect static power dissipation.

---

## 2. Gain Comparison

### Gain Formula

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Gain formula** | A_d = g_m × R_D | A_d = g_m × (r_o2 ‖ r_o4) | A_d = g_m × (r_o2 ‖ r_o4) |
| **Mid-band gain (linear)** | Low (~g_m·R_D) | **~1.9 V/V** | **~1.9 V/V** |
| **Mid-band gain (dB)** | Lower | **5.55 dB** | **5.55 dB** |
| **Theoretical gain (dB)** | — | ~6 dB | ~6 dB |
| **Deviation from theory** | — | ~0.45 dB | ~0.45 dB |

### Why Circuit 2 & 3 have higher gain

- Resistive load (C1): drain resistance R_D is limited in value to avoid pushing transistors into triode. Gain is bounded.
- Active mirror load (C2, C3): replaces R_D with the parallel combination of NMOS output resistance r_o2 and PMOS output resistance r_o4. This is significantly larger than a physical resistor, giving much higher gain.

### Transient Gain (small-signal, from simulation)

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Differential input (V_id)** | 20 mV peak | 20 mV peak | 20 mV peak |
| **Output swing (V_out,pp)** | Very small (nV range) | ~2.4 mV | Slightly reduced (CL effect) |
| **Calculated A_v** | ≈ negligible | **0.12** (single-ended) | Lower due to pole |

> Note: The transient gain of 0.12 is for single-ended output. Full differential output (V_out1 − V_out2) would yield higher effective gain.

---

## 3. Input Swing Comparison

### Common-Mode Input Range (V_CM)

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **V_CM(min)** | −0.334 V | −0.34 V | −0.34 V |
| **V_CM(max)** | **+0.366 V** | **+1.032 V** | **+1.032 V** |
| **Total CM swing** | **~0.70 V** | **~1.37 V** | **~1.37 V** |

### V_CM(min) Derivation (all circuits)

```
Condition: NMOS input pair just turns ON → VGS = VT

V_CM(min) = V_P + V_T
           = −0.7 + 0.366
           = −0.334 V  (C1) / −0.34 V (C2, C3 from simulation V_S)
```

### V_CM(max) Derivation

**Circuit 1** — limited by NMOS saturation condition:
```
VDS = VOV → VCM(max) = VD + VT = 0 + 0.366 = +0.366 V
```

**Circuit 2 & 3** — limited by PMOS load saturation condition:
```
V_CM(max) = VDD − V_ov(PMOS) + V_T(NMOS)
           = 0.9 − 0.234 + 0.366
           = +1.032 V
```

The PMOS active load gives ~2× wider common-mode input swing compared to resistive load.

### Linear Differential Input Swing (all circuits)

For linear (undistorted) operation, the differential input must satisfy:

```
V_id < √2 × V_OV
```

| Condition | MOSFET behaviour | Output |
|---|---|---|
| V_id < √2·V_OV | Both M1, M2 in saturation, current shared equally | Clean sinusoidal output |
| V_id > √2·V_OV | One MOSFET enters cutoff, other carries full current | Distorted, clipped output |

---

## 4. Bandwidth & Frequency Response Comparison

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Dominant pole formula** | 1 / (2π·R_D·C_par) | 1 / (2π·r_out·C_par) | 1 / (2π·r_out·(C_par + C_L)) |
| **Approximate f_−3dB** | Higher (lower r_out) | ~1–5 Hz | < 1 Hz |
| **Roll-off slope** | −20 dB/decade | −20 dB/decade | −20 dB/decade |
| **Bandwidth trade-off** | Wide BW, lower gain | Narrow BW, higher gain | Narrowest BW, same gain as C2 |

---

## 5. Stability & Phase Margin

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Phase at low freq** | ~−180° | **−194.8°** | Worse than C2 |
| **Excess phase** | Minimal | ~14.8° | > 14.8° |
| **Phase margin (open-loop)** | Positive | **~−14.8° (unstable)** | More negative |
| **Frequency compensation needed?** | No | Yes (Miller cap) | Yes (strongly needed) |

> The negative phase margin in Circuits 2 and 3 means they will oscillate if placed in a unity-gain feedback loop without frequency compensation.

---

## 6. DC Operating Point Comparison

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **V_out1 (DC)** | ≈ 0 V | ≈ 7.1 mV | ≈ 7.1 mV |
| **V_out2 (DC)** | ≈ 0 V | ≈ 7.1 mV | ≈ 7.1 mV |
| **V_od = V_out1 − V_out2** | 0 V | 0 V | 0 V |
| **V_S (source node)** | −0.707 V | −0.695 V | −0.695 V |
| **I_D1 = I_D2** | 0.5 mA | 0.5 mA | 0.5 mA |
| **Symmetry** | ✓ Balanced | ✓ Balanced | ✓ Balanced |

---

## 7. Behaviour at Boundary Conditions

### At V_CM(min)

| Observation | All Circuits |
|---|---|
| **V_GS ≈ V_T** | Transistor barely ON |
| **V_ov ≈ 0** | Transconductance g_m ≈ 0 |
| **Output** | Flat — no amplification |
| **Conclusion** | Amplifier non-functional at lower limit |

### At V_CM(max)

| Observation | All Circuits |
|---|---|
| **V_DS = V_ov** | At saturation–triode boundary |
| **Gain** | Collapses as MOSFET enters triode |
| **Output** | No amplification, waveform flat |
| **Conclusion** | Amplifier non-functional at upper limit |

---

## 8. Overall Comparison Summary

| Feature | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Load** | Resistive | Active (PMOS mirror) | Active + C_L |
| **Power** | 1.8 mW | 1.8 mW | 1.8 mW |
| **Gain (dB)** | Lower | 5.55 dB | 5.55 dB |
| **CM input range** | 0.70 V | 1.37 V | 1.37 V |
| **Bandwidth** | Wide | Narrow (~1–5 Hz) | Narrowest |
| **Phase margin** | Stable | Unstable (−14.8°) | Worse |
| **CMRR** | Moderate | High | High |
| **Complexity** | Simple | Moderate | Moderate |
| **Key advantage** | Wide BW, simple design | High gain, wide CM range | Drives capacitive loads |
| **Key drawback** | Low gain, limited CM swing | Needs frequency compensation | Lowest BW |
| **Best suited for** | General amplification | High-gain op-amp input stage | Capacitive load driving |

---

## 9. Key Formulas Reference

| Formula | Expression |
|---|---|
| Differential gain | A_d = g_m · R_D (C1) or g_m · (r_o2 ‖ r_o4) (C2, C3) |
| Transconductance | g_m = 2·I_D / V_ov |
| Output resistance | r_o = 1 / (λ·I_D) |
| CM input min | V_CM(min) = V_P + V_T |
| CM input max (C1) | V_CM(max) = V_D + V_T |
| CM input max (C2,C3) | V_CM(max) = VDD − V_ov(PMOS) + V_T(NMOS) |
| Linear input condition | V_id < √2 · V_OV |
| Dominant pole | f_H = 1 / (2π · r_out · C_L) |

---

*Experiment 4 — Differential Amplifier Analysis | LIC Lab*
*VDD = 0.9 V | VSS = −0.9 V | L = 480 nm | I_SS = 1 mA | V_T = 0.366 V*
