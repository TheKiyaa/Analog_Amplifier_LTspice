# Analog_Amplifier_LTspice
Transistor-level design and LTspice simulation of an AC/DC power supply and a Class AB audio amplifier with a Darlington input stage.

# Analog AC/DC Power Supply & Class AB Amplifier

This repository contains the transistor-level design and LTspice simulation of an integrated power supply and audio amplifier system[cite: 6]. The project was developed as part of the Electronics I course.

## 📌 Project Overview
The goal of this project was to design a complete system capable of driving a 10 Ω speaker load from a 10 kΩ high-impedance sinusoidal source (500 Hz, 3V amplitude), ensuring less than 10% signal attenuation, zero clipping, and an overall system efficiency of over 30%[cite: 6]. 

## ⚙️ System Architecture
1. **AC/DC Adapter:** Features a step-down transformer, a full-wave bridge rectifier (1N4003 diodes), a 6800uF smoothing capacitor, and a series voltage regulator utilizing a BD139 transistor and a 1N759 Zener diode[cite: 6].
2. **Power Amplifier:** 
   * **Input Stage:** Implemented a Darlington pair (2N2222) to provide an exceptionally high input impedance, preventing signal loss across the source's internal resistance[cite: 6].
   * **Output Stage:** A Class AB push-pull amplifier using BD139/BD140 complementary transistors. Diode biasing (1N4007) and emitter degeneration resistors were used to establish the Q-point and eliminate crossover distortion[cite: 6].

## 🛠️ Design Challenges & Solutions (Troubleshooting)
During the design phase, several analog circuit challenges were identified and resolved through physical circuit analysis[cite: 6]:
* **Severe Signal Attenuation:** The initial common-emitter stage suffered from loading effects due to the 10 kΩ source. **Solution:** Upgraded to a Darlington pair input stage with high-value biasing resistors (e.g., 270kΩ, 100kΩ) to maximize input impedance[cite: 6].
* **Signal Clipping & Current Starvation:** The driver stage failed to supply adequate current to the power transistors. **Solution:** Transitioned to a pure emitter-follower Class AB push-pull configuration, fine-tuning the bias diodes and adding thermal emitter resistors (1-2.2 Ω) to secure maximum voltage headroom[cite: 6].
* **Voltage Drop Under Load:** Connecting the 10 Ω load caused a severe Vcc drop and 100 Hz ripple. **Solution:** Adjusted the Zener diode biasing resistor to ~330 Ω, ensuring sufficient base current for the regulator's BD139 transistor to handle peak current demands[cite: 6].
* **Low Efficiency (<40%):** High voltage supply caused excessive thermal dissipation across the output transistors. **Solution:** Selected a specific 12V Zener diode (1N759) to drop the regulated voltage precisely to the safe margin (~11.5V), minimizing heat loss while allowing a full 6V peak-to-peak output swing. This successfully pushed the efficiency to ~33.27%[cite: 6].

## 📊 Simulation Results
* **Output Attenuation:** Maintained under 10% without clipping[cite: 6].
* **Adapter Ripple:** 0.21V at the rectifier, 0.26V post-regulator[cite: 6].
* **Power Efficiency:** 33.27%[cite: 6].

## 📂 Files Included
* `.asc` LTspice simulation files.
* Circuit schematics and transient analysis plots.
* Detailed project report.
