# Circuit Theory to Implementation 🛠️

A structured series of circuit simulations documenting my progress in network analysis and DC/AC/transient circuit theory and Analog Circuits analysis using LTspice. This project bridges the gap between theoretical derivations and practical engineering simulation, moving from fundamental laws to active semiconductor characterization.

---

## 📁 Repository Structure

| # | Topic | Key Skills & Directives | Status |
| :--- | :--- | :--- | :--- |
| **01** | Wheatstone Bridge Analysis | `.op` Analysis, Power Curves | ✅ Complete |
| **02** | Thevenin & Norton Equivalents | `.tf` Command, `.meas` Parameters | ✅ Complete |
| **03** | Maximum Power Transfer | `.step param` Sweeps, Peak Detection | ✅ Complete |
| **04** | Maxwell Bridge AC Analysis | `.ac` Sweep, Complex Impedance | ✅ Complete |
| **05** | First-Order Transient Response | `.tran` Analysis, RC/RL Duality | ✅ Complete |
| **06** | **MOSFET Characterization** | **Nested `.dc` Sweeps, $g_m$ Extraction** | 🟢 **New** |

---

## 🟢 01: Wheatstone Bridge DC Analysis
* **Objective:** To analyze bridge unbalance and understand the operational basis of resistive temperature sensors through bridge sensitivity.
* **Engineering Insight:** Demonstrated how a small change in resistance ($R_4$) simulates a transducer's response, resulting in a measurable differential error signal $V(b,a)$.

## 🟢 02: Thevenin & Norton Equivalent Circuits
* **Objective:** To simplify complex bridge networks into efficient equivalent models for easier load-line analysis.
* **Engineering Insight:** Cross-verified equivalent parameters using the **1A Test Source method** and the LTspice **`.tf` (Transfer Function)** command to instantly extract $R_{th}$ and gain.

## 🟢 03: Maximum Power Transfer Analysis
* **Objective:** To determine the specific load resistance ($R_L$) that extracts the absolute maximum power from the network.
* **Engineering Insight:** Leveraged **`.step param`** to sweep $R_L$ from $100\Omega$ to $2k\Omega$. Verified that $P_{max}$ occurs exactly when $R_L = R_{th} \approx 1045\Omega$.

## 🟢 04: Maxwell Bridge AC Analysis
* **Objective:** To measure unknown inductance ($L_x$) and internal resistance ($R_x$) using a frequency-independent AC nulling technique.
* **Engineering Insight:** Demonstrated **Pole-Zero Cancellation** to achieve a "Zero-Order" system response at the balance point. Analysis of the Bode plot reveals the high-frequency limits of bridge balance caused by numerical precision and the underlying second-order nature of the reactive network.

## 🟢 05: First-Order Transient Response (RC & RL)
* **Objective:** To analyze the time-domain behavior of energy storage elements during switching transients.
* **Engineering Insight:** Demonstrated the **Duality** between RC and RL networks. Verified the time constant $\tau = RC$ and $\tau = L/R$ through automated pulse edge detection.

## 🔵 06: MOSFET Characterization (Si7336ADP)
* **Objective:** To bridge semiconductor physics with SPICE modeling by extracting DC parameters from a high-performance Power MOSFET.
* **Engineering Insight:** * **Drain Characteristics:** Visualized the transition between **Triode** and **Saturation** regions. Observed the effect of **Channel Length Modulation ($\lambda$)** as a finite slope in the saturation curves.
    * **Transfer Characteristics:** Verified the **Square-Law** relationship ($I_D \propto V_{GS}^2$) and extracted the **Threshold Voltage ($V_{th} \approx 2V$)**.
    * **Transconductance ($g_m$):** Utilized the derivative function `d(Id(M1))` to plot $g_m$ vs. $V_{GS}$, confirming the linear gain relationship essential for amplifier design.

---

## ⚙️ Technical Implementation
This project utilizes specific LTspice features to ensure simulation data integrity and analysis efficiency:
* **Analysis Automation:** Implemented `.step` and `.meas` directives for multi-point analysis and automated parameter extraction.
* **Active Device Modeling:** Integrated manufacturer-specific SPICE models (e.g., Si7336ADP) to account for real-world non-linearities, parasitic capacitances, and switching effects.
* **Signal Synthesis:** Configured high-fidelity **PULSE** and **SINE** sources to simulate ideal step-inputs and steady-state AC signals.
* **Analytical Cross-Verification:** Every simulation output is benchmarked against first-principles (e.g., KVL/KCL, Square-Law equations, or Differential Equations) to validate model accuracy.

---

## 📂 Project Resources
* **Simulation Assets:** Each module folder includes the `.asc` source files for local reproduction in LTspice.
* **Documentation:** Verification screenshots (e.g., Bode plots, I-V curves, and transient waveforms) and `README` files with step-by-step math are provided for each circuit.
