# 06: MOSFET Characterization 📈

## 📌 Project Overview
This module marks the transition from passive circuit theory to **Active Semiconductor Devices**. By characterizing a Power MOSFET (**Si7336ADP**), I analyzed the non-linear relationship between terminal voltages and drain current ($I_D$), establishing the analytical foundation required for Analog IC design and power electronics.

---

## 🔬 1. DC Drain Characteristics ($I_D$ vs. $V_{DS}$)
**Objective:** To visualize the three regions of operation and identify the boundary between Triode and Saturation.

* **Simulation Setup:** Nested DC Sweep.
    * **Primary Sweep:** $V_{DS}$ from $0\text{V}$ to $5\text{V}$.
    * **Secondary Sweep (Steps):** $V_{GS}$ from $0\text{V}$ to $5\text{V}$ in $1\text{V}$ increments.
* **Engineering Insights:**
    * **Ohmic (Triode) Region:** For $V_{DS} < V_{GS} - V_{th}$, the MOSFET acts as a voltage-controlled resistor.
    * **Saturation Region:** For $V_{DS} \ge V_{GS} - V_{th}$, the current levels off, and the device acts as a voltage-controlled current source.
    * **Channel Length Modulation:** The slight positive slope in the saturation region indicates a finite output resistance ($r_o$), modeled by the term $(1 + \lambda V_{DS})$.

---

## 📐 2. Transfer Characteristics ($I_D$ vs. $V_{GS}$)
**Objective:** To verify the **Square-Law Model** and extract the Threshold Voltage ($V_{th}$).

* **Simulation Setup:** $V_{DS}$ held constant at $5\text{V}$ (Saturation) while $V_{GS}$ is swept from $0\text{V}$ to $5\text{V}$.
* **Mathematical Model:** The drain current follows the quadratic relationship:
    $$I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2$$
* **Extraction Results:** The x-intercept of the curve provides the measured $V_{th}$. For the Si7336ADP, $V_{th}$ was observed at approximately **1.9V - 2.1V**.

---

## 🧪 3. Transconductance Analysis ($g_m$ vs. $V_{GS}$)
**Objective:** To evaluate the device "gain" or sensitivity, which dictates amplifier performance.

* **Methodology:** Utilized the LTspice derivative function `d(Id(M1))` to plot the slope of the transfer curve.
* **Engineering Insights:**
    * **Linearity:** The resulting linear plot confirms that transconductance is directly proportional to $V_{GS}$ in the saturation region.
    * **Equation:** $g_m = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})$.
    * **Measured Value:** At a bias of $V_{GS} = 2.5\text{V}$, the extracted $g_m$ is approximately **$50\mu\text{S}$**.

---

## ⚙️ Technical Implementation
* **Model:** Manufacturer-specific **Si7336ADP** SPICE model.
* **Analysis Types:** DC Sweep and Derivative.
* **Validation:** Cursors were utilized to confirm specific coordinate points and slopes against theoretical calculations.

---
