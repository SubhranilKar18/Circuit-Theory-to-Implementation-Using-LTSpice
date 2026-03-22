# 07: Common Source Amplifier Analysis

  ## 🕒 Transient Analysis (Time Domain)
**Objective:** To verify the voltage gain and phase inversion in real-time.

* **Input:** 10mV peak-to-peak sine wave at 1kHz.
* **Output:** ~22.5mV peak-to-peak sine wave.
* **Phase Relationship:** $180^\circ$ Phase Shift. The output is exactly inverted relative to the input, consistent with Common Source topology.
* **Linearity:** The output waveform maintains a clean sinusoidal shape, confirming that the small-signal approximation holds true and the device is biased in the active (saturation) region.

## 📌 Frequency Response (Bode Plot)
**Objective:** To determine the operational bandwidth and phase characteristics of the 180nm CS gain stage.

### 📊 Measured Data
* **Mid-band Gain:** 8.18 dB ($A_v \approx 2.56$).
* **Mid-band Phase:** -180° (Inverting).
* **Lower 3dB Frequency ($f_L$):** ~100 Hz.
* **Upper 3dB Frequency ($f_H$):** ~10 GHz.

### 🧪 Engineering Insights
1. **Coupling Capacitors:** The $1\mu\text{F}$ capacitors effectively set the lower limit of the bandwidth. For audio applications, these are sufficient; for lower frequency precision work, larger values would be required.
2. **Device Speed:** The 180nm process provides a very high $f_H$, making this topology suitable for high-speed signal processing.
3. **Phase Stability:** The phase remains stable across the entire usable gain bandwidth, ensuring no unexpected oscillations in a feedback loop.
