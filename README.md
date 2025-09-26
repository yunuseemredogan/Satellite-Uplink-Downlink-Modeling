# Satellite Uplink and Downlink Simulation

![Project Banner](https://github.com/yunuseemredogan/screenshots-.gitkeep/blob/main/uplink-downlink.png)

## 📖 Overview
Satellite Uplink and Downlink Simulation is a MATLAB Simulink-based model designed to simulate the uplink (ground to satellite) and downlink (satellite to ground) processes for Low Earth Orbit (LEO) satellite communication systems. The model includes QPSK modulation/demodulation, frequency conversion, power amplification, channel effects (AWGN and FSPL), and error rate calculations, offering a comprehensive view of satellite link performance.

This project is perfect for:
- Testing satellite communication protocols, such as IoT-based space networks or remote sensing.
- Simulating real-world scenarios with metrics like BER (0.0015), RSSI (-77.4418 dBm), and SNR (23.5355 dB).
- Educational use to demonstrate modulation, channel coding, and RF concepts.

The simulation starts with a Bernoulli binary source, processes it through the uplink and downlink chains, and calculates performance metrics in real-time. Created on September 26, 2025, at 04:42 PM +03, this is a simulation-only model requiring a MATLAB/Simulink license.

## ✨ Key Features
- **End-to-End Simulation**: Covers data source to demodulation with frequency conversions and amplification. 🛰️
- **QPSK Processing**: Utilizes QPSK for efficient modulation/demodulation. 🔄
- **Channel Effects**: Incorporates AWGN noise and FSPL for LEO realism. 🌌
- **Amplification**: Features high power (uplink) and low noise (downlink) amplifiers with memory polynomial distortion. 📡
- **Performance Metrics**: Real-time BER (163/105691 = 0.0015), RSSI, and SNR monitoring. 📊
- **Customizable**: Adjust SNR, modulation, or channel parameters easily. ⚙️
- **Visual Scopes**: Displays signals, error rates, and metrics. 📈
- **Error Analysis**: Computes BER and SER by comparing transmitted and received data. ❌
- **Modular Design**: Extensible blocks for modulators, channels, and demodulators.

## 📋 Requirements
Requires MATLAB R2018b+ with Simulink and relevant toolboxes, compatible with Windows, Linux, and macOS.

### Software Dependencies:
- **MATLAB R2018b+**: With Simulink ([mathworks.com](https://www.mathworks.com/products/matlab.html)). 🧮
- **Communications Toolbox**: For QPSK and error rate blocks.
- **DSP System Toolbox**: Optional for signal processing.

### Hardware Requirements:
- **Standard PC**: 8 GB RAM, i5 processor minimum.
- **License**: Valid MATLAB/Simulink license.

## 🛠️ Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yunuseemredogan/Satellite-Uplink-Downlink-Modeling.git
   cd Satellite-Uplink-Downlink-Modeling
   ```
2. **Open in MATLAB**:
   ```matlab
   open('satellite-uplink-downlink.slx')
   ```
3. **Verify Toolboxes**: Run `ver('Communications Toolbox')`.

## ▶️ Usage
1. **Run the Model**: Click "Run" in Simulink.
2. **Adjust Parameters**: Modify SNR, data length, or frequencies in blocks.
3. **Monitor**: Check scopes for BER, RSSI, and SNR.
4. **Stop**: Use the "Stop" button.

**Pro Tip**: Start with defaults for a quick test.

## 🔍 How It Works
- **Uplink**: Bernoulli binary → QPSK modulation → Up-conversion → HPA → FSPL.
- **Downlink**: LNA → Down-conversion → AWGN → QPSK demodulation → BER calc.
- Metrics: BER (0.0015), RSSI (-77.4418 dBm), SNR (23.5355 dB).

## 🧱 Structure
Single .slx file with ~25 blocks, including input (Bernoulli), modulation, uplink/downlink subsystems, and scopes.

## ⚠️ Troubleshooting
- **License Issues**: Run `license checkout Simulink`.
- **Slow Performance**: Reduce sample count.
- **Empty Scopes**: Extend run time.

## 📉 Limitations
- Simulation-only; no hardware support.
- LEO-focused; adapt for GEO.
- Basic BER calc; no advanced coding.

## 🤝 Contributing
Fork, modify, and submit PRs. Suggest 16QAM or Doppler effects.

## 📜 License
MIT License - See [LICENSE](LICENSE) file.

*Built with ❤️ on September 26, 2025, 04:42 PM +03. Open an issue for feedback!*
