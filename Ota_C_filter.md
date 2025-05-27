# OTA C FILTER USING SINGLE OTA 
## **Aim of the Project**
Design and simulate a tunable second-order OTA-C low-pass filter using a single OTA in 0.25 μm CMOS technology. The goal is to investigate performance characteristics across current-mode and voltage-mode operations, extract key frequency-domain parameters, and assess its application in low-power and reconfigurable analog systems.

---

## **Introduction**

OTA-C (Operational Transconductance Amplifier - Capacitor) filters are widely used in analog signal processing due to their compactness, electronic tunability, and compatibility with CMOS technology. These filters eliminate bulky resistors by leveraging OTAs, where the resistance is replaced by a voltage-controlled transconductance. This enables frequency tunability essential in modern reconfigurable and adaptive systems.

---

## **Theory**

### **1. Operational Transconductance Amplifier (OTA)**

An OTA acts as a voltage-controlled current source with a transconductance (gm). Its output current is defined by:

**I_out = g_m × (V_in+ - V_in−)**

Where:
- **g_m**: Transconductance (A/V)
- **V_in+**, **V_in−**: Differential input voltages

### **2. Basic OTA-C Filter Block**

A simple OTA-C integrator is structured as:

**V_out(s) = (1 / (s × C)) × g_m × V_in(s)**

A second-order filter with cascaded integrators has a transfer function:

**H(s) = g_m² / (s² × C1 × C2)**

This directly links the cutoff frequency to gm and capacitance.

### **3. Cutoff Frequency**

**f_c = g_m / (2πC)**

This fundamental relation allows dynamic control of f_c by adjusting bias current/voltage.

### **4. g_m Tuning**

**g_m = μ_n × C_ox × (W/L) × I_bias / V_OV**

Where:
- μ_n: Electron mobility
- C_ox: Oxide capacitance
- W/L: Transistor geometry
- V_OV: Overdrive voltage = V_GS − V_TH
- I_bias: Controlled by bias voltage V_b

### **5. Voltage Mode vs Current Mode**

**Voltage Mode**: Both inputs are active. The OTA responds to voltage difference.

![{CF946276-C5B8-4840-A17C-C21F98765F54}](https://github.com/user-attachments/assets/a59b3df6-3c3f-46cd-95de-b7b0d8c8d5a4)

**Current Mode**: One input (V_in−) grounded. High-speed performance with better linearity due to simpler signal path. Enhances performance in low-voltage designs.

![{F3506579-489C-4EB8-981D-40726F2D536F}](https://github.com/user-attachments/assets/721c3f62-5ee5-45b9-9e7f-98271634169d)

---
## Transistor level referred design:
![{30466485-EF1B-4309-9080-695AEBACEC17}](https://github.com/user-attachments/assets/55c21822-fb15-43c4-83ce-de51f13e6fd5)

Fig: shows the transistor level implementation where differential input with cross coupledload architecture is used

## Simulated Circuit Architecture:
![WhatsApp Image 2025-05-26 at 22 12 46_cc3bd3e4](https://github.com/user-attachments/assets/87fb29af-4e5e-4473-b859-c727e0d05389)

## **Reference Design**

| Parameter              | Value             |
|------------------------|------------------|
| CMOS Technology        | 0.25 μm           |
| Supply Voltage         | ±2 V              |
| Bias Voltage (V_b)     | ~0.65 V           |
| Capacitance (C1, C2)   | 5 pF              |
| Target Cutoff f_c      | ~42–45 MHz        |
| Transconductance (g_m) | 200–226 μS        |
| Roll-off Rate          | ~−40 dB/decade    |

![WhatsApp Image 2025-05-26 at 22 13 42_569cc899](https://github.com/user-attachments/assets/96fc7ff4-c37a-41aa-aa4c-266c5dca4ca8)

---

## **Modified Design**

Transistors are resized for power savings. Reduced biasing alters g_m and cutoff frequency.

| Transistor | Type  | Role                         |
|------------|-------|------------------------------|
| M1, M2     | NMOS  | Differential input pair      |
| M3, M4     | PMOS  | Diode-connected active load  |
| M5, M6     | NMOS  | Output stage (sink)          |
| M7, M8     | PMOS  | Output driver                |
| M9, M10    | PMOS  | Current mirror (bias)        |
| M11        | NMOS  | Tail current source          |
| M12        | NMOS  | Bias generator (optional)    |

| Parameter              | Value                  |
|------------------------|------------------------|
| V_b                    | 0.545 V                |
| Capacitors             | 5 pF, 10 pF            |
| Transconductance (g_m) | ~20.55 μS              |
| Cutoff Frequency (f_c) | 655.4 kHz – 9.5 MHz    |
| Roll-Off Rate          | ~−30.4 to −38.5 dB/dec |

![WhatsApp Image 2025-05-26 at 22 12 30_a073d225](https://github.com/user-attachments/assets/a0d4fbee-4898-4b80-bda4-d6c8b16ffec1)

---

## **Simulation and Analysis**

### **Operating Points**

- V_GS (input NMOS): ~1.25 V  
- V_DS: ~1.23 V  
- All MOSFETs confirmed in saturation region  
- Saturation Check: V_DS > V_GS − V_TH where V_TH ≈ 0.35 V
![WhatsApp Image 2025-05-26 at 22 13 41_2ef92fca](https://github.com/user-attachments/assets/cc785fba-01e7-4e8b-b383-b56042c381b9)

![WhatsApp Image 2025-05-26 at 22 13 42_4229e305](https://github.com/user-attachments/assets/7cc50823-403b-4dcf-b296-6dd5a2ef36b6)

![WhatsApp Image 2025-05-26 at 22 13 42_3cca2f5f](https://github.com/user-attachments/assets/311344f6-c3c6-4559-9062-695fcb8dca15)



### **Frequency Response & Phase Shift**

- Phase rolls toward −90° → confirms LPF nature
- Group delay increases near f_c (expected behavior)
- Case 1 (C = 5pF): f_c ≈ 9.5 MHz, Roll-off ≈ −30.4 dB/decade
- Case 2 (C = 10pF): f_c ≈ 100 MHz, Roll-off ≈ −38.5 dB/decade

![WhatsApp Image 2025-05-26 at 22 15 20_680c6235](https://github.com/user-attachments/assets/a50b559e-acf0-401a-83c7-8973439bf65d)


## **Why Deviation Exists**

| Factor                          | Explanation                                    |
|---------------------------------|------------------------------------------------|
| Lower W/L ratios                | Reduces gm → lowers cutoff frequency           |
| Lower bias voltage (V_b)        | Less I_bias → weak tail current → lower gain  |
| Non-idealities in OTA           | Finite output resistance → degraded slope      |
| Parasitic capacitance           | Alters pole locations and frequency response   |
| Measurement range effects       | Changes apparent slope on log-log plots        |
| Real circuit ≠ ideal 2nd order  | Behavior deviates, resembles quasi-2nd order   |

----

### Detailed analysis of the deviation:
| **Deviation Aspect**               | **Explanation**                                                                                                                                                                                                                                                      |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Reduced Transconductance (gm)**  | The modified design uses smaller W/L ratios and a lower bias voltage (Vb = 0.545 V). Since `gm ∝ I_bias ∝ Vb`, reducing Vb limits the tail current. This significantly reduces the gm, shifting the cutoff frequency from \~42 MHz (ideal) to as low as \~655.4 kHz. |
| **Lower Loop Gain**                | OTA's overall loop gain is affected by gm. A low gm means lower loop gain, reducing the OTA’s ability to maintain steep gain roll-off. Thus, the roll-off drops from the ideal −40 dB/decade to \~−30.4 to −38.5 dB/decade.                                          |
| **Parasitic Capacitances**         | Real MOSFET layouts include gate-drain/source overlap and interconnect parasitics. These form additional capacitive paths which modify pole locations and attenuate high-frequency response.                                                                         |
| **Non-Ideal OTA Behavior**         | Real OTAs have finite output resistance, input offset, and bandwidth limitations, all of which introduce error in ideal transfer function behavior.                                                                                                                  |
| **Measurement Span Effects**       | When plotting gain across a smaller span of frequencies, the slope visually deviates from ideal −40 dB/dec because of the filter's quasi-second-order behavior at practical biasing conditions.                                                                      |
| **Mismatch and Layout Tolerances** | Process variations and transistor mismatch affect bias mirroring and current sourcing, further deteriorating uniformity in gain and frequency behavior.                                                                                                              |

---

## **Performance Comparison**

| Feature              | Reference Design   | Modified Design     |
|----------------------|--------------------|----------------------|
| gm                   | 200–226 μS         | 20.55 μS             |
| V_b                  | ~0.65 V            | 0.545 V              |
| f_c                  | 42–45 MHz          | 655.4 kHz – 9.5 MHz  |
| Roll-off             | −40 dB/decade      | −30.4 to −38.5 dB/dec|
| Power Consumption    | Higher             | Lower                |

---

## **Applications**

### **1. Applications in Anti-Aliasing Filters**

#### **Aliasing Problem**

Aliasing occurs when signal components above half the sampling frequency (Nyquist limit) are folded back into the baseband, creating non-recoverable signal distortion.

#### **How OTA-C Filters Help**

- **Cutoff Control:** Using OTA, gm is electronically tunable. This allows precise adjustment of fc below the Nyquist frequency dynamically.
- **Analog Front-End (AFE) Usage:** OTA-C filters act as low-power anti-aliasing filters directly in front of ADCs to attenuate out-of-band noise.
- **Programmable Sampling Systems:** By changing Vb, the same filter can be reused across different signal conditions and ADC specs without redesign.

**Equation Recap:**  
Cutoff frequency: `f_c = gm / (2πC)`  
By adjusting Vb → gm → we tune f_c → anti-aliasing margin.

---

### **2. Broader Circuit Integration Use-Cases**

OTA-C filters are not standalone. They are often embedded within complex systems. Applications include:

- **SoC Analog Modules:** Reconfigurable filtering in analog front-ends, adaptable via bias voltage DACs.
- **Audio Systems:** Selective low-pass filtering in portable audio codecs and preamps.
- **Biomedical Devices:** Compact and tunable filters for ECG, EEG with optimized low power and area.
- **Wireless Communication:** In analog baseband paths for channel selection or interference rejection.
- **Programmable Filters:** Use of OTA-C filters in analog signal processors and configurable analog blocks (CABs) in field-programmable analog arrays (FPAAs).

---

### **. Limitations in Current OTA-C Designs**

| **Limitation**                      | **Impact** |
|------------------------------------|------------|
| **Low gm in modified design**      | Poor cutoff response, slower roll-off |
| **Layout and mismatch sensitivity**| Performance varies across process corners |
| **Non-linearity at large input swings** | Reduces dynamic range |
| **Parasitics from layout/interconnect** | Adds unpredictable poles/zeros |
| **Finite OTA output impedance**    | Limits gain and increases output loading |
| **Difficult to implement high-order filters** | More OTA stages mean more tuning complexity |


- Decreased gain accuracy due to gm variation
- Slower roll-off in non-ideal OTA setup
- Parasitics affect exact tuning and symmetry
- Sensitivity to layout and temperature variation

---

## **Future Improvements**

- Digitally tunable gm (via DAC)
- Add source degeneration for improved linearity
- Implement cascode mirrors for high output impedance
- Transition to fully differential OTA for noise immunity
- Build higher-order (3rd/4th) OTA-C filter chains

---

## **Conclusion**

This project demonstrates the design, simulation, and comparative evaluation of a second-order OTA-C low-pass filter. The reference and modified designs reveal the impact of transistor sizing and bias voltage on transconductance, frequency response, and roll-off. The modified version sacrifices bandwidth for power efficiency, validating its use in portable, low-power applications. With advanced layout and digital tuning, OTA-C filters offer promising scope for future SoC-integrated analog systems.


## **References**

1. B. Razavi, *Design of Analog CMOS Integrated Circuits*, McGraw-Hill, 2001.  
2. R. Schaumann and M. Van Valkenburg, *Design of Analog Filters*, Oxford University Press, 2001.  
3. Y. Tsividis, *Operation and Modeling of the MOS Transistor*, Oxford University Press, 1999.  
4. LTspice: [Analog Devices Design Tool](https://www.analog.com/en/design-center/design-tools-and-calculators/ltspice-simulator.html)
