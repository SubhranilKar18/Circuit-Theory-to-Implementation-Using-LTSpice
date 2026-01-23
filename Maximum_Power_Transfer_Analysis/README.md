# 03: Maximum Power Transfer Analysis

## 🎯 Objective
To experimentally verify the Maximum Power Transfer Theorem using an unbalanced Wheatstone bridge. The goal is to determine the specific load resistance ($R_L$) that extracts the absolute maximum power from the network and compare it to the previously calculated $R_{th}$.

## 📝 Theoretical Background
According to the theorem, for a network with a Thevenin resistance $R_{th}$, maximum power is delivered to a load when:
$$R_L = R_{th}$$

From *02*, our calculated $R_{th}$ was *1045.45 $\Omega$*.
The predicted maximum power is:
$$P_{max} = \frac{V_{th}^2}{4R_{th}} = \frac{(-0.4545)^2}{4 \times 1045.45} \approx 49.38 \mu W$$

## 🛠️ Simulation Methodology
I used a automated parameter sweep to characterize the circuit's power delivery:
* *.step param Rload 100 2k 10*: Automatically varied the load resistance from $100\Omega$ to $2k\Omega$ in $10\Omega$ increments.
* *.meas DC max_power MAX(ABS(V(A,B)*I(RL)))*: Used a post-processing directive to scan all 191 simulation runs and identify the mathematical peak power.

## 📊 Results & Verification
| Parameter | Theoretical Value | Simulated (LTspice) |
| :--- | :--- | :--- |
| *Max Power ($P_{max}$)* | 49.38 $\mu$W | 49.407 $\mu$W |
| *Optimal Load ($R_L$)* | 1045.45 $\Omega$ | ~1045.45 $\Omega$ |

Verification: The simulation matches the theoretical prediction with an error of less than 0.1%.

## 🖼️ Verification Gallery
### Power vs. Resistance Curve
![Power Curve](power_curve_peak.jpeg)
Figure 1: The parabolic power curve showing the peak power delivery point.

### SPICE Measurement Log
![Log Verification](log_verification.jpeg)
Figure 2: The SPICE Error Log confirming the calculated maximum power of 49.4µW.

## 🧪 Practical Insights
* *Sign Convention:* Discovered that LTspice current direction can result in negative power values ($V \times -I$). Resolved this by applying the ABS() function in the .meas directive to ensure a correct positive peak detection.
* *Optimization:* Using .step is far more efficient than manual iteration for finding the "Sweet Spot" in an engineering design.
