# Satellite Uplink and Downlink Simulation 🚀

<img width="1059" height="627" alt="uplink-downlink" src="https://github.com/user-attachments/assets/48f59653-ec67-4161-94e7-3cdd955d9dd1" />

## 📖 Overview
Satellite Uplink and Downlink Simulation is a communication system model developed using MATLAB Simulink. This project simulates the uplink (ground to satellite) and downlink (satellite to ground) processes in satellite-based systems. The model includes QPSK modulation/demodulation, frequency conversions, power amplifiers, channel effects (AWGN and FSPL), and error rate calculations. It is specifically designed for Low Earth Orbit (LEO) satellite systems.

This project is ideal for:
- Testing satellite communication protocols, such as IoT-based space networks or remote sensing systems.
- Simulating real-world scenarios; analyzing channel performance with metrics like SNR, RSSI, and BER.
- Educational use; a practical tool for teaching modulation, channel coding, and RF components.

The core idea is to visualize and parametrically analyze a complex satellite communication chain. The model starts with a Bernoulli binary source, modulates it with QPSK, passes through uplink/downlink chains, and ends with demodulation. Performance metrics (e.g., BER: 0.0015) are calculated in real-time. Note: This is a simulation model; no physical hardware is required, only a MATLAB/Simulink license is sufficient.

## ✨ Key Features
- **Full Uplink/Downlink Chain**: Complete simulation from data source to demodulation, including frequency conversions and amplification. 🛰️
- **QPSK Modulation/Demodulation**: Standard QPSK with 4-bit/s/Hz spectral efficiency. 🔄
- **Channel Models**: Realistic channel impairments with AWGN noise and FSPL (for LEO). 🌌
- **Power and Noise Components**: High power amplifier (uplink), low noise amplifier (downlink), and memory polynomial distortion. 📡
- **Performance Metrics**: Real-time BER calculation (e.g., 163/105691 = 0.0015), RSSI (-77.4418 dBm), and SNR (23.5355 dB) monitoring. 📊
- **Parametric Analysis**: Easily adapt the simulation by changing SNR, modulation, or channel parameters. ⚙️
- **Visual Displays**: Simulink scopes for signal, error rate, and metric visualizations. 📈
- **Error Rate Calculation**: Bit error rate (BER) and symbol error rate (SER) analysis by comparing Tx/Rx. ❌
- **Modular Structure**: Components (modulator, channel, demodulator) as separate blocks, easily extensible.

## 📋 Requirements
To run this model, your system must meet the following requirements. The model works on Windows, Linux, and macOS, but a Simulink license is required.

### Software Dependencies:
- **MATLAB R2018b+**: Including the Simulink toolbox. Download from [mathworks.com](https://www.mathworks.com/products/matlab.html). 🧮
- **Communications Toolbox**: Required for QPSK mod/demod and error rate blocks. Typically included with MATLAB, otherwise license it.
- **DSP System Toolbox**: For filters and signal processing (optional, sufficient for basic model).
- **Others**: Standard Simulink blocks (Scope, Bernoulli Generator, AWGN, etc.) – no additional setup needed.

### Hardware Requirements:
- **Standard PC**: Minimum 8 GB RAM and an i5 processor recommended; simulation time varies by parameters.
- **License**: Valid MATLAB/Simulink license (academic or commercial).

**Platform Notes**: The model is platform-independent, provided Simulink is installed. It can be run on Linux with Wine, but a native installation is recommended.

## 🛠️ Installation
Follow these steps to set up the project on your local machine.

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yunuseemredogan/Satellite-Uplink-Downlink-Modeling.git
   cd Satellite-Uplink-Downlink-Modeling
   ```
   This downloads the Simulink model file (.slx) and README.

2. **Prepare MATLAB**:
   Open MATLAB and verify toolboxes:
   ```matlab
   ver('Communications Toolbox')
   ```
   If an error occurs, check your license.

3. **Open the Model**:
   In the folder, run in the MATLAB terminal:
   ```matlab
   open('satellite-uplink-downlink.slx')
   ```
   The model will open with scopes ready.

## ▶️ Usage
Running the model is straightforward.

1. **Start the Model**:
   After opening in Simulink, click the "Run" button or press Ctrl+R.

2. **Configure Parameters**:
   - **SNR Setting**: Adjust the SNR value in the AWGN block (e.g., 23 dB).
   - **Data Length**: Set the sample count in the Bernoulli block (e.g., 105691 bits).
   - **Frequencies**: Update fc values in the Up/Down-converters.
   - Run the simulation.

3. **Monitor and Stop Results**:
   - View signals, RSSI/SNR values, and BER in scopes.
   - Stop with the "Stop" button when the simulation ends; save data to the workspace.

4. **Analysis (Not Included in Repo)**:
   - Plot BER vs. SNR with a MATLAB script: `semilogy(EbNo, ber);`
   - Or use external tools (e.g., Python for data export).

**Pro Tip**: Use default parameters for an initial test; BER should be around 0.0015.

## 🔍 How It Works: The Inner Mechanics
The model simulates uplink and downlink chains in parallel. Here’s a detailed breakdown.

### High-Level Workflow (ASCII Diagram):
```
+-------------------+   Mod   +-------------------+   Channel   +-------------------+
| Bernoulli Binary  | ------> | QPSK Modulator    | ----------> | Up-Converter      |
| (Data Source)     |         | + HPA + Mem Poly  |             | + FSPL(LEO)       |
+-------------------+         +-------------------+             +-------------------+
  |                                         |                          |
  v                                         v                          v
Downlink: LNA + Mem Poly + Down-Conv + AWGN  |  Demod: QPSK + BER Calc (0.0015)
                                             |  
                                     Scopes: RSSI (-77.44), SNR (23.54)
```

1. **Uplink Chain**:
   - Data: Generates random bits with a Bernoulli binary generator (e.g., 105691 bits).
   - Modulation: Converts bits to symbols with QPSK.
   - RF Processing: Up-converter (fc), high power amplifier, and memory polynomial (distortion).
   - Channel: Applies FSPL (LEO path loss).

2. **Downlink Chain**:
   - Reception: Low noise amplifier (LNA) and memory polynomial.
   - Frequency Conversion: Down-converter (fc).
   - Noise: Adds AWGN channel (SNR-based).
   - Demodulation: Converts back to bits with QPSK demodulator.

3. **Metric Calculation**:
   - BER: Tx/Rx comparison (163 errors / 105691 bits = 0.0015).
   - RSSI: Received signal strength (-77.4418 dBm).
   - SNR: Calculated signal-to-noise ratio (23.5355 dB).
   - Scopes: Signal in/out, ERC (error rate) visualization.

The model operates with fixed parameters (e.g., QPSK, 30 dB SNR), but block parameters can be adjusted for customization. Simulation time is ~10-30 seconds.

## 🧱 Code Structure
The model is structured in a single .slx file with modular blocks.

- **Input Block**: Bernoulli Binary Generator (data source).
- **Modulation Subsystem**: QPSK Modulator and scopes.
- **Uplink Subsystem**: Up-Conv, HPA, Mem Poly, FSPL.
- **Downlink Subsystem**: LNA, Mem Poly, Down-Conv, AWGN.
- **Demodulation Subsystem**: QPSK Demod, BER Calculation.
- **Output Block**: Scopes (Signal, RSSI, SNR, ERC).
- **Configuration**: Solver settings in Model Properties (ode45, fixed-step).

Total block count: ~25, labeled for clarity (add more if needed).

## ⚠️ Troubleshooting
- **Simulink Not Opening**: Check license; run `license checkout Simulink`.
- **Block Errors**: Verify toolboxes; install if missing.
- **Slow Simulation**: Reduce sample count or change solver.
- **High BER**: Increase SNR or adjust channel parameters.
- **Empty Scopes**: Extend run time (Configuration Parameters > Stop Time).
- **Crashes**: Update MATLAB or use a debugger.

## 📉 Limitations
- Simulation-based; no real RF hardware.
- Fixed modulation (only QPSK); add others for expansion.
- Focused on LEO; adapt FSPL for GEO.
- No coding (ERC block is basic); add advanced error correction.
- Platform-dependent (MATLAB license).

## 🤝 Contributing
Fork the repo, make changes, and submit a PR! Suggestions: Other modulations (16QAM), Doppler effect, or Python integration.

## 📜 License
MIT License - Use, modify, and share. See [LICENSE](LICENSE) file.

*Made with ❤️ in 2025. Open an issue for questions!*
