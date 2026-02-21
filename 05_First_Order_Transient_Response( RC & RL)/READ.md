# 05: First-Order Transient Response (RC & RL)

## 📌 Overview
This module explores the time-domain behavior of first-order networks. The focus is on the "Dual Nature" of energy storage: how Capacitors oppose changes in voltage and Inductors oppose changes in current. This analysis is fundamental for understanding timing circuits, filtering, and switching transients in power electronics.

## 🛠️ Circuit Configurations

### 1. RC Charging Circuit
* **Components:** $R = 1k\Omega, C = 1\mu F$.
* **Time Constant ($\tau$):** $\tau = R \cdot C = 1ms$.
* **Behavior:** The capacitor voltage ($V_c$) rises exponentially as it stores energy in an electric field.

### 2. RL Energizing Circuit
* **Components:** $R = 100\Omega, L = 100mH$.
* **Time Constant ($\tau$):** $\tau = L / R = 1ms$.
* **Behavior:** The inductor current ($I_L$) rises exponentially as it stores energy in a magnetic field.



---

## 📐 Mathematical Framework
The response of these first-order systems to a step input $V_{in}$ follows the general exponential growth equation:

**For RC (Voltage Focus):** $$V_c(t) = V_{in}(1 - e^{-t/\tau})$$

**For RL (Current Focus):** $$I_L(t) = \frac{V_{in}}{R}(1 - e^{-t/\tau})$$

### Critical Benchmarks:
* **$1\tau$:** System reaches **63.2%** of final steady-state value.
* **$5\tau$:** System is considered to be at **Steady State** (>99%).



---

## 📊 LTspice Implementation
**Simulation Type:** `.tran 10m`  
**Source Type:** `PULSE(0 5 1m 1n 1n 10m 20m)` to simulate a clean step-input at $t = 1ms$.

### Automated Measurement (`.meas`):
I utilized SPICE directives to precisely extract timing parameters without manual cursor error:
```spice
.meas TRAN tau_reach FIND time WHEN V(out)=3.16  ; Finds 63.2% point
.meas TRAN rise_time TRIG V(out)=0.5 RISE=1 TARG V(out)=4.5 RISE=1 ; 10% to 90% Rise Time
