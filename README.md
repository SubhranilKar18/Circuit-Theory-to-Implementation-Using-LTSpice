# Circuit Theory to Implementation 🛠️

A structured series of circuit simulations documenting my progress in network analysis, DC/AC/transient theory, and Analog IC analysis using LTspice. This project bridges the gap between theoretical derivations and practical engineering simulation, moving from fundamental laws to active sub-micron semiconductor characterization.

---

## 📁 Repository Structure

| # | Topic | Key Skills & Directives | Status |
| :--- | :--- | :--- | :--- |
| **01** | Wheatstone Bridge Analysis | `.op` Analysis, Power Curves | ✅ Complete |
| **02** | Thevenin & Norton Equivalents | `.tf` Command, `.meas` Parameters | ✅ Complete |
| **03** | Maximum Power Transfer | `.step param` Sweeps, Peak Detection | ✅ Complete |
| **04** | Maxwell Bridge AC Analysis | `.ac` Sweep, Complex Impedance | ✅ Complete |
| **05** | First-Order Transient Response | `.tran` Analysis, RC/RL Duality | ✅ Complete |
| **06** | **MOSFET Characterization** | **Nested `.dc`, $g_m$ & $V_{th}$ Extraction** | ✅ Complete |
| **07** | **Common Source Amplifier** | **AC/Transient Analysis, 180nm CMOS** | ✅ Complete |

---

## 🟢 01: Wheatstone Bridge DC Analysis
* **Objective:** To analyze bridge unbalance and understand the operational basis of resistive sensors through bridge sensitivity.
* **Engineering Insight:** Demonstrated how a small change in resistance ($R_4$) simulates a transducer's response, resulting in a measurable differential error signal $V(b,a)$.

## 🟢 02: Thevenin & Norton Equivalent Circuits
* **Objective:** To simplify complex networks into efficient equivalent models for easier load-line analysis.
* **Engineering Insight:** Cross-verified parameters using the **1A Test Source method** and the LTspice **`.tf` (Transfer Function)** command to instantly extract $R_{th}$ and Gain.

## 🟢 03: Maximum Power Transfer Analysis
* **Objective:** To determine the specific load resistance ($R_L$) that extracts the absolute maximum power from the network.
* **Engineering Insight:** Leveraged **`.step param`** to sweep $R_L$. Verified that $P_{max}$ occurs exactly when $R_L = R_{th} \approx 1045\Omega$.

## 🟢 04: Maxwell Bridge AC Analysis
* **Objective:** To measure unknown inductance ($L_x$) using a frequency-independent AC nulling technique.
* **Engineering Insight:** Demonstrated **Pole-Zero Cancellation** to achieve a "Zero-Order" system response at balance. Bode plot analysis reveals the high-frequency limits caused by numerical precision.

## 🟢 05: First-Order Transient Response (RC & RL)
* **Objective:** To analyze the time-domain behavior of energy storage elements during switching transients.
* **Engineering Insight:** Demonstrated the **Duality** between RC and RL networks. Verified time constants $\tau = RC$ and $\tau = L/R$ through automated pulse edge detection.

## 🔵 06: MOSFET Characterization (Si7336ADP & 180nm)
* **Objective:** To bridge semiconductor physics with SPICE modeling by extracting DC parameters from both discrete Power MOSFETs and sub-micron IC models.
* **Engineering Insight:** * **Drain Characteristics:** Visualized the transition between **Triode** and **Saturation** regions. Observed **Channel Length Modulation ($\lambda$)** as a finite slope in saturation.
    * **Transfer Characteristics:** Verified the **Square-Law** relationship ($I_D \propto V_{GS}^2$) and extracted the **Threshold Voltage ($V_{th}$)** using the x-intercept of the $\sqrt{I_D}$ plot.
    * **Transconductance ($g_m$):** Leveraged the derivative function `d(Id(M1))` to confirm that $g_m$ is linearly proportional to the overdrive voltage ($V_{GS} - V_{th}$).

## 🔵 07: Common Source (CS) Amplifier Analysis
* **Objective:** To design and characterize a voltage gain stage using a 180nm bulk CMOS process, focusing on biasing and frequency response.
* **Engineering Insight:** * **DC Biasing:** Implemented a **Voltage Divider Bias** network to set the Q-point in saturation, ensuring stable transconductance ($g_m \approx 2\text{--}4\text{ mS}$).
    * **Transient Analysis:** Observed a $180^\circ$ **Phase Inversion** between input and output, verifying the inverting nature of the CS topology with a measured gain $A_v \approx 2.56\text{ V/V}$.
    * **Frequency Response (Bode Plot):** Characterized the **Low-Frequency Roll-off** caused by coupling capacitors and the **High-Frequency Roll-off** dominated by device parasitic capacitances and the **Miller Effect**.

---

## ⚙️ Technical Implementation
* **Analysis Automation:** Implemented `.step`, `.meas`, and `.tf` directives for multi-point analysis and automated parameter extraction.
* **Active Device Modeling:** Integrated manufacturer-specific models (Si7336ADP) and sub-micron libraries (`180nm_bulk.lib`) to account for real-world non-linearities and short-channel effects.
* **Analytical Cross-Verification:** Every simulation output is benchmarked against first-principles (e.g., KVL/KCL, Square-Law equations, or Differential Equations) to validate model accuracy.

---

## 📂 Project Resources
* **Simulation Assets:** Each module folder includes the `.asc` source files for local reproduction.
* **Documentation:** Verification screenshots (Bode plots, I-V curves, and transient waveforms) and `README` files with step-by-step math are provided for each circuit.
