# Monostable Multivibrator Using 555 Timer IC

## 1. Aim

To design, simulate, and analyze a monostable multivibrator circuit using a 555 timer IC that generates a single output pulse of 0.5 ms duration in response to a trigger signal.



## 2. Introduction

The 555 timer IC is a widely used integrated circuit for generating precise time delays and oscillations. In monostable mode, it functions as a one-shot pulse generator. It produces a single output pulse of predetermined duration in response to an external trigger.

This behavior is useful in applications such as:
- Switch debouncing
- Pulse stretching
- Frequency-to-time conversion
- Missing pulse detection
- Timed outputs (e.g., logic-level converters, alarms)



## 3. Theory

A monostable multivibrator has:
- One stable state (output LOW)
- One quasi-stable state (output HIGH for time T)

The output of the 555 timer stays LOW until a negative trigger pulse is applied to pin 2. When this happens:
1. The internal flip-flop is set.
2. Output (pin 3) goes HIGH.
3. The capacitor C starts charging through resistor R.
4. Once the voltage across the capacitor reaches 2/3 Vcc, the timer resets.
5. Output returns to LOW (stable state).

The output pulse width is determined by the formula:

\[
T = 1.1 \times R \times C
\]

Where:
- T = Output pulse width (seconds)
- R = Resistance (Ohms)
- C = Capacitance (Farads)

---

## 4. Component Selection

| Component        | Value             | Purpose                             |
|------------------|-------------------|-------------------------------------|
| 555 Timer IC     | NE555             | Main pulse generation               |
| Resistor (R)     | 454.54 Ω          | Controls pulse width                |
| Capacitor (C)    | 1 µF              | Works with R to define time delay   |
| Supply Voltage   | 5V                | DC power source                     |
| Trigger Input    | Pulse generator   | External input to activate output   |
| LED / Probe      | Output Indicator  | Visualize output                    |

For a 0.5 ms pulse:
\[
R = \frac{T}{1.1 \times C} = \frac{0.0005}{1.1 \times 1 \times 10^{-6}} ≈ 454.54 \, \Omega
\]

Use the nearest standard resistor (470 Ω).

---

## 5. Circuit Diagram

> ![Circuit Diagram](https://github.com/user-attachments/assets/f09d2014-f234-4cf1-947f-79f882f99862)

Pin configuration of NE555:
- Pin 1: GND
- Pin 2: Trigger
- Pin 3: Output
- Pin 4: Reset (tied to Vcc)
- Pin 5: Control Voltage (optional; use 0.01 µF to ground)
- Pin 6: Threshold
- Pin 7: Discharge
- Pin 8: Vcc (+5V)

---

## 6. Procedure

1. Connect the 555 timer in monostable mode as per the circuit diagram.
2. Choose R = 470 Ω and C = 1 µF for a pulse width of approximately 0.5 ms.
3. Connect a signal generator or push-button to provide a trigger at pin 2.
4. Observe the voltage at:
   - Output pin 3
   - Capacitor charging at pin 6
5. Measure the width of the output pulse using an oscilloscope or simulation software.
6. Verify the output pulse width matches the theoretical value.

---

## 7. Simulation Results

> ![Waveform](https://github.com/user-attachments/assets/141243cc-a94a-4485-b145-532742e47138)

Waveform legend:
- First trace: Trigger input pulse
- Second trace: Voltage across capacitor
- Third trace: Output pulse from pin 3

The output waveform shows a clean single pulse of ~0.5 ms duration after every trigger pulse. The capacitor voltage ramps up during the output HIGH period and resets after the threshold is crossed.

---

## 8. Observations

| Observation Point     | Expected Result                      | Actual Result (Simulated) |
|------------------------|--------------------------------------|---------------------------|
| Output LOW (idle)      | 0V                                   | 0V                        |
| Output after trigger   | HIGH for 0.5 ms                      | ~0.5 ms                   |
| Capacitor charging     | Exponential rise to 2/3 Vcc          | Matches                   |
| Auto reset             | After T = 0.5 ms, output goes LOW    | Matches                   |

---

## 9. Inference

- The 555 timer operated correctly in monostable mode.
- A single HIGH output pulse of 0.5 ms was generated after each input trigger.
- The capacitor voltage followed the expected exponential charging curve.
- The output returned to LOW after reaching the threshold, as per the timing formula.
- The experiment validated the relation T = 1.1 × R × C.

---

## 10. Applications

This circuit has several practical applications:
- Keypad or switch debouncing
- One-shot pulse generation
- Missing pulse detector
- Timed light or alarm trigger
- Signal edge detector

---

## 11. Conclusion

The 555 timer IC was successfully used to build a monostable multivibrator that produces a consistent pulse of 0.5 ms duration. The experiment demonstrated the theoretical working of the IC and verified it through simulation, confirming that output duration is governed by the RC time constant. This setup can be readily adapted for a wide range of practical timing and pulse-control applications.

---

## 12. References

- NE555 Timer Datasheet – Texas Instruments
- The Art of Electronics – Horowitz & Hill
- https://www.electronics-tutorials.ws
- https://www.allaboutcircuits.com
- Lab simulation in LTspice/Proteus



