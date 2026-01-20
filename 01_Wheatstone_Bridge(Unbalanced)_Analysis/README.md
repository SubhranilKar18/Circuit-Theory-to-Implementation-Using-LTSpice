#  01: Wheatstone Bridge DC Analysis

This simulation investigates the behavior of a resistive bridge network under unbalanced conditions using LTspice 24.

## 🛠️ Circuit Parameters
- *Resistors R1, R2, R3:* $1k\Omega$
- *Resistor R4 (Unbalanced Arm):* $1.2k\Omega$ (representing a 20% deviation)
- *Load Resistor (R5):* $500\Omega$
- *Input Source (V1):* DC Sweep from $0V$ to $20V$

## 🎯 Objectives
1. Perform a DC Operating Point analysis to find nodal voltages $V(a)$ and $V(b)$.
2. Analyze the sensitivity of the bridge by observing the differential voltage $V(b,a)$.
3. Verify the Power Law by plotting power dissipation across the load resistor $R5$.

## 📈 Key Technical Results
- *Differential Sensitivity:* The bridge produces a linear error signal as $V1$ increases, which is critical for sensor application theory.
- *Quadratic Power Scaling:* While the current $I(R5)$ is linear, the power plot shows a distinct parabolic curve, verifying the $P = I^2 \times R$ relationship.

## 📂 Files in this Folder
- Wheatsone Bridge (Unbalanced) Circuit.asc: The main LTspice schematic file.
- Wheatsone Bridge (Unbalanced) Circuit.plt: The plot configuration file for organized 3-pane visualization.
- Waveforms_Wheatstone Bridge (unbalanced).jpeg: Exported simulation results showing current, voltage, and power.

---
Verified
