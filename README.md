# Real-Time FIR & IIR Filter Implementation on ZedBoard FPGA

This project implements real-time **FIR** and **IIR** filters on a **ZedBoard (Zynq-7000)** FPGA. The system reads audio input from a **PMOD MIC**, processes it using digital filters with **configurable coefficients**, and outputs the filtered signal through a **PMOD DA2** DAC interface. Designed in Verilog and synthesized using Vivado, this project demonstrates practical signal processing on hardware.

---

##  Features

- **Real-time FIR and IIR digital filtering**
- Audio input via **PMOD MIC**
- Audio output via **PMOD DA2**
- **Dynamic coefficient configuration** (runtime adjustable)
- **Comparison with software-based filtering** (for validation)
- Designed for **ZedBoard (xc7z020clg484-1)**

---

##  Hardware Architecture

- **PMOD MIC** → ADC (onboard) → FPGA
- **FPGA**:
  - FIR / IIR Filter Modules
  - Coefficient Loader
  - Synchronization Logic
- **PMOD DA2** → DAC interface (SPI-like protocol)
- **Clock divider** to match sampling frequency


##  How It Works

1. **Input**: PMOD MIC samples are digitized and fed into the filter module.
2. **Filtering**: Either FIR or IIR filter is selected. Coefficients can be preloaded or changed dynamically.
3. **Output**: The filtered output is serialized and sent to PMOD DA2 using a clocked interface (`SYNC`, `SCLK`, `SDATA`).
4. **Timing**: A clock divider ensures correct timing for DAC communication.

---

##  Filter Comparison

Filter output was validated against MATLAB/NumPy implementations for accuracy. The hardware output closely follows software-generated signals, ensuring correctness and stability.

---

##  Synthesis & Testing

- **Tool Used**: Vivado 2021.2
- **Target Device**: `xc7z020clg484-1`
- **Simulation**: Testbenches for both FIR and IIR filters validate functional correctness.
- **Synthesis**: Successfully synthesized and deployed on ZedBoard

---



##  Author

Prathamesh Pise  
B.E. (Hons.) Electronics and Instrumentation  
BITS Pilani, Goa Campus

---

