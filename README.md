# Circuit Theory to Implementation 🛠️

A structured series of  circuit simulations documenting my progress in network analysis and DC/AC/transient circuit theory using LTspice. This project bridges the gap between theoretical derivations and practical engineering simulation.

---

## 📁 Repository Structure

| # | Topic | Key Skills & Directives | Status |
| :--- | :--- | :--- | :--- |
| **01** | Wheatstone Bridge Analysis | `.op` Analysis, Power Curves | ✅ Complete |
| **02** | Thevenin & Norton Equivalents | `.tf` Command, `.meas` Parameters | ✅ Complete |
| **03** | Maximum Power Transfer | `.step param` Sweeps, Peak Detection | ✅ Complete |

---

## 🟢 01: Wheatstone Bridge DC Analysis
* **Objective:** To analyze bridge unbalance and understand the operational basis of resistive temperature sensors (like RTDs and Thermistors) through bridge sensitivity.
* **Engineering Insight:** Demonstrated how a small change in resistance ($R_4$) simulates a transducer's response, resulting in a measurable differential error signal $V(b,a)$.

## 🟢 02: Thevenin & Norton Equivalent Circuits
* **Objective:** To simplify complex bridge networks into efficient equivalent models for easier load-line analysis.
* **Engineering Insight:** Cross-verified equivalent parameters using the **1A Test Source method** and the LTspice **`.tf` (Transfer Function)** command to instantly extract $R_{th}$ and gain.

## 🟢 03: Maximum Power Transfer Analysis
* **Objective:** To determine the specific load resistance ($R_L$) that extracts the absolute maximum power from the network.
* **Engineering Insight:** Leveraged **`.step param`** to sweep $R_L$ from $100\Omega$ to $2k\Omega$. Verified that $P_{max}$ occurs exactly when $R_L = R_{th} \approx 1045\Omega$.

---

## ⚙️ Technical Implementation
This project utilizes specific LTspice features to ensure simulation data integrity and analysis efficiency:
* **Analysis Automation:** Implemented `.step` and `.meas` directives to perform multi-point analysis without manual iteration.
* **Data Normalization:** Applied the `ABS()` function within measurement blocks to handle SPICE current sign conventions and ensure consistent power reporting.
* **Analytical Cross-Verification:** Every simulation output is benchmarked against first-principles derivations (KVL/KCL and Thevenin’s Theorem) to validate model accuracy.

---

## 📂 Project Resources
* **Simulation Assets:** Each module folder includes the `.asc` source files for local reproduction in LTspice.
* **Documentation:** Verification screenshots (e.g., `.tf` reports and power curves) and `README` files with step-by-step math are provided for each circuit.
* **Scope:** These files are intended as a reference for verifying fundamental network theorems through software simulation.
*
