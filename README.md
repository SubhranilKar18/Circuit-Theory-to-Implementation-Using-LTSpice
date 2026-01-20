# Circuit Theory to Implementation 🛠️

A structured series of analog circuit simulations documenting my progress in bridge network analysis and DC/AC circuit theory using LTspice.

---

## 🟢 Week 01: Wheatstone Bridge DC Analysis
*Objective:* To analyze bridge unbalance and verify the relationship between nodal voltage, current, and power dissipation.

### 🔍 Engineering Insights
* *Unbalance Analysis:* With $R4$ at $1.2k\Omega$ ($20\%$ mismatch), the bridge creates a clear differential error signal $V(b,a)$.
* *Linearty:* Confirmed that current $I(R5)$ and differential voltage $V(b,a)$ scale linearly with the source voltage $V1$.
* *Power Curve:* Verified that power dissipation follows a quadratic relationship ($P = I^2R$), as shown by the parabolic curve in the simulation.

### 📊 Simulation Results
![Waveforms_Wheatstone Bridge (unbalanced).jpeg](01_Wheatstone_Bridge_Analysis/waveforms.png)

---
