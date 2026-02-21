#  05: Transient Response of RC Networks

## 📌  Overview
This module explores the time-domain behavior of a first-order RC circuit. The focus is on analyzing how a capacitor stores energy when subjected to a sudden change in DC voltage (Step Response). This is a foundational concept for timing circuits, filters, and digital signal integrity.

## 🛠️ Circuit Configuration
* **Voltage Source ($V_1$):** Configured as a **PULSE** source ($0V$ to $5V$) to simulate an ideal switch closure.
* **Time Constant ($\tau$):** Defined by $R_1 = 1k\Omega$ and $C_1 = 1\mu F$.
  $$\tau = R \cdot C = 1k\Omega \cdot 1\mu F = 1ms$$



## 📐 Theoretical Derivation
The charging voltage across the capacitor is governed by the first-order differential equation:
$$V_c(t) = V_{in}(1 - e^{-t/\tau})$$

### Critical Benchmarks:
* **$1\tau$ ($1ms$):** Voltage reaches 63.2 % of $V_{in}$ ($\approx 3.16V$).
* **$5\tau$ ($5ms$):** Voltage reaches >99 % of $V_{in}$, effectively reaching steady-state.
* **Energy Stored:** At steady-state, the energy stored in the electric field is:
  $$E = \frac{1}{2} C V^2 = \frac{1}{2} (1\mu F) (5V)^2 = 12.5 \mu J$$

## 📊 LTspice Analysis
**Simulation Type:** `.tran 10m` (with a $1ms$ `Tdelay` for initial condition visualization).



### Key Observations:
1. **Continuity of Voltage:** The capacitor voltage $V(Vc)$ starts at $0V$ and rises exponentially, confirming that voltage across a capacitor cannot change instantaneously.
2. **Current Decay:** The charging current $I(C_1)$ spikes to $5mA$ ($V_{in}/R$) at the instant of switching and decays to zero as the capacitor acts as a DC open circuit.
3. **Automated Extraction:** Used the `.meas` directive to calculate the `FinalEnergy` from the SPICE Error Log, verifying the $12.5 \mu J$ theoretical value.

## 🚀 How to Run
1. Open `RC_Transient.asc` in LTspice.
2. Run the simulation.
3. Press `Ctrl+L` to view the **SPICE Error Log** for energy measurements and time constant verification.
