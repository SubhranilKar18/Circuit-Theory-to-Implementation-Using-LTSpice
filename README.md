# Circuit Theory to Implementation 🛠️

A structured series of analog circuit simulations documenting my progress in bridge network analysis and DC/AC/transient circuit theory using LTspice. This project bridges the gap between theoretical derivations at Jadavpur University and practical engineering simulation.

---

## 🟢 01: Wheatstone Bridge DC Analysis
* **Objective:** To analyze bridge unbalance and understand the operational basis of resistive temperature sensors (like RTDs and Thermistors) through bridge sensitivity.
* **Core Task:** Verify the relationship between nodal voltage, current, and power dissipation in a non-equilibrium state.

### 🔍 Engineering Insights
* **Temperature Sensor Basis:** Demonstrated how a small change in resistance ($R_4$) simulates a transducer's response to temperature, resulting in a measurable differential error signal $V(b,a)$.
* **Unbalance Analysis:** With $R_4$ at $1.2k\Omega$ ($20\%$ mismatch), the bridge creates a clear error signal used in instrumentation amplifiers.
* **Linearity & Power:** Confirmed that $V(b,a)$ scales linearly with source voltage, while power dissipation follows the quadratic $P = I^2R$ relationship.

### 📊 Simulation Results
![Waveforms_Wheatstone Bridge (unbalanced)](https://github.com/SubhranilKar18/Circuit-Theory-to-Implementation-Using-LTSpice/blob/main/01_Wheatstone_Bridge(Unbalanced)_Analysis/Waveforms_Wheatstone%20Bridge%20(unbalanced).jpeg?raw=true)

---

## 🟢 02: Thevenin & Norton Equivalent Circuits
* **Objective:** To simplify complex bridge networks into efficient equivalent models for easier load-line analysis.

### 🔍 Engineering Insights
* **Multi-Method Verification:** Cross-verified equivalent parameters using Theoretical KVL/KCL, the **1A Test Source method**, and the LTspice **.tf (Transfer Function)** command.
* **Norton Confirmation:** Verified the Norton Current ($I_{no}$) by short-circuiting nodes A and B, matching the calculated $V_{th}/R_{th}$ ratio exactly.
* **Automation Mastery:** Leveraged the `.tf` command to instantly extract $R_{th}$ and gain, showcasing a professional approach to circuit characterization.

### 📊 Verification Table
| Parameter | Theoretical Value | Simulated (LTspice) | Method |
| :--- | :--- | :--- | :--- |
| **$V_{th}$** | -0.4545 V | -0.4545 V | `.meas PARAM` |
| **$R_{th}$** | 1045.45 $\Omega$ | 1045.45 $\Omega$ | `.tf` Analysis |
| **$I_{no}$** | -434.78 $\mu$A | -434.78 $\mu$A | Short-Circuit Probe |

---

## 🚧 03: Maximum Power Transfer (In Progress)
* **Objective:** Utilizing `.step param` to determine the load resistance that maximizes power delivery from the Thevenin equivalent circuit.
