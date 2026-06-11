# 555 Timer Monostable Multivibrator (One-Shot Pulse Generator)

A clean, hardware-verified hardware implementation of a monostable multivibrator utilizing the classic NE555 timer IC. When triggered by a tactile pushbutton, the circuit outputs a single, clean pulse of a predetermined duration to drive an LED indicator.

> **Note on Simulation:** This project has been fully built and hardware-verified on a physical breadboard. Minor layout deviations may cause execution errors in rigid web-based simulators (e.g., Tinkercad) due to grid constraints, but physical deployment functions exactly as intended.

---

## Features
* **Hardware-Verified:** Tested and stable using a 9V DC power supply.
* **Debounced Triggering:** Implements a strong pull-up resistor configuration to prevent false trigger cycles from mechanical button bounce.
* **Adjustable Timing Window:** Output pulse duration can be modified easily by swapping the timing resistor ($R_1$) and capacitor ($C_1$).

---

## How It Works 

In its stable state, the 555 timer's output (Pin 3) sits LOW. When the input trigger button is pressed, **Pin 2** drops below $1/3$ of the supply voltage ($V_{CC}$), causing the internal flip-flop to switch the output to HIGH and release the internal short on **Pin 7 (Discharge)**.

The external capacitor ($C_1$) then charges from $V_{CC}$ through the timing resistor ($R_1$). When the voltage across the capacitor reaches $2/3$ of $V_{CC}$, the internal threshold comparator (**Pin 6**) resets the flip-flop. The output drops back to LOW, the capacitor discharges through Pin 7, and the circuit awaits the next trigger event.

The pulse duration ($t$) is mathematically defined by the standard RC charging formula:

$$t = 1.1 \cdot R_1 \cdot C_1$$

### My Timing Configuration:
* **Timing Resistor ($R_1$):** [e.g., 10kΩ]
* **Timing Capacitor ($C_1$):** [e.g., 100µF]
* **Calculated Pulse Duration:** ~[e.g., 1.1 seconds]

---

## Hardware Bill of Materials (BOM)
| Qty | Component Description | Designator |
|-----|-----------------------|------------|
| 1   | NE555 Timer IC        | U1         |
| 1   | LED (Red, 5mm)        | D1         |
| 1   | Pushbutton Switch     | SW1        |
| 1   | Timing Resistor       | R1         |
| 1   | LED Current Limiter   | R2         |
| 1   | Pull-up Resistor      | R3         |
| 1   | Timing Capacitor      | C1         |
| 1   | 9V Battery / Clip     | VCC        |

---

### Schematic Diagram
![Circuit Schematic](<schematics/555 Circut.png>)


### Physical Breadboard Reference
![Physical Breadboard Implementation](<pictures - video/Frontside.jpg>)

---

## Demonstration

Add Youtube Link here
