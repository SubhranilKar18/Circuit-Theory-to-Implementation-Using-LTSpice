#  08: Common Drain (Source Follower) Amplifier 

## 📌 Project Overview
In this module, I designed and characterized a **Common Drain (Source Follower)** amplifier stage using a 180nm bulk CMOS process library. This topology acts as a voltage buffer, offering exceptionally high input impedance and low output impedance, making it ideal for impedance matching and driving heavy loads without gain degradation.

---

## 📐 Circuit Topology & Small-Signal Theory
The input signal is AC-coupled to the **Gate** terminal, the **Drain** is tied directly to the $V_{DD}$ supply rail (serving as an AC ground), and the output is extracted from the **Source** terminal.



* **Theoretical Voltage Gain ($A_v$):**
  $$A_v = \frac{g_m R_S}{1 + (g_m + g_{mb})R_S} \approx \frac{R_S}{R_S + \frac{1}{g_m}}$$
  *Due to the body effect gmb inherent to sub-micron bulk processes where the substrate is grounded, the maximum achievable gain is limited to approximately 0.82 V/V (-1.72 dB).*
* **Phase Relationship:** Non-inverting ($0^\circ$ phase shift across the mid-band).

---

## 📊 Simulation Analysis Results

### 1. Transient Time-Domain Verification
* **Simulation Command:** `.tran 5m` with an input source configuration of `SINE(0 10m 1k)`.
* **Automated Parameter Extraction (`.meas` Output):**
  * `vin_p2p` = $19.97\text{ mV}$
  * `vout_p2p` = $16.36\text{ mV}$
  * `vol_gain` = **$0.8192\text{ V/V}$**
* **Observations:** The output waveform tracks the input synchronously without phase inversion, verifying stable buffer performance.

### 2. Frequency Response (Bode Plot)
* **Simulation Command:** `.ac dec 100 1 100Meg`
* **Mid-band Gain:** $-1.72\text{ dB}$ flat bandwidth extending into high-frequency RF domains.
* **Low-Frequency Response:** Characterized by high-pass filtering networks formed by the $1\mu\text{F}$ coupling stages interacting with the gate bias resistances ($R_3 \parallel R_2$).
* **High-Frequency Response:** Shows a exceptionally wide flat band up to $100\text{ MHz}$ due to the lack of Miller capacitance multiplication in this topology.
