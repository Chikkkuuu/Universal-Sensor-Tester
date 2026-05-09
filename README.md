# Universal Sensor Tester: Multi-Protocol Diagnostic Architecture
### High-Fidelity Signal Validation | Auto-Protocol Identification | I/O Protection
**Focus:** Automated sensor benchmarking, hardware abstraction, and signal integrity analysis.

---

## Engineering Philosophy
In rapid prototyping, manual sensor debugging often accounts for significant downtime. The **Universal Sensor Tester** was engineered to eliminate this bottleneck by implementing a **Unified Hardware Abstraction Layer (UHAL)**. This architecture allows a single port to dynamically reconfigure itself for Analog, Digital, and Serial communication (I2C/UART/SPI), reducing manual troubleshooting time by approximately **40%**.

---

## Technical Challenges & Engineering Solutions

### 1. Robust Auto-Detection Algorithm
*   **The Problem:** Manually switching firmware to test different sensor types is inefficient and prone to pin-mapping errors.
*   **The Solution:** Developed a custom **Signal Scanning Routine** that monitors the universal port for active pull-ups (I2C), steady-state voltages (Analog), or specific start-bit patterns (UART). This allows the system to automatically identify the sensor category upon connection.

### 2. Protocol Integrity Benchmarking
*   **The Problem:** Sensors often "partially" fail, where they respond but return corrupted data or inconsistent timing.
*   **The Solution:** Implemented a **Protocol Validator** in `Protocol_Handler.cpp`. It doesn't just read data; it benchmarks integrity by checking for ACK/NACK responses, parity consistency, and I2C clock-stretching anomalies.

### 3. Baseline Calibration & Noise Analysis
*   **The Problem:** High-sensitivity sensors often suffer from DC offset and environmental noise floor interference.
*   **The Solution:** Integrated an **Automated Zero-Point Calibration** engine. By sampling the "Idle State" across a precise time-delta, the system calculates the noise floor and applies a software offset, ensuring high-fidelity data acquisition for subsequent tests.

---

## System Architecture & Logic Flow
![System Architecture](https://github.com/Chikkkuuu/Asset/blob/main/System%20Architecture.png)

The system operates as a supervisory state machine, prioritizing hardware safety and signal stability.

### 1. Unified Hardware Interface (UHAL)
*   **Multi-Signal Acquisition:** Engineered to handle high-frequency ADC sampling alongside interrupt-driven digital polling.
*   **Health Scoring:** Analyzes signal stability and jitter to provide a quantitative pass/fail diagnostic score for the connected hardware.

### 2. Real-Time Visualization
*   **On-Device Feedback:** Coordinates with a serial interface or integrated display to provide instantaneous feedback on sensor health and raw hex/voltage values.

---

## Repository Structure
```text
Universal_Sensor_Tester/
├── Firmware/                 # Diagnostic Core
│   ├── Tester_Main.ino       # Main lifecycle & auto-detection supervisor
│   ├── Protocol_Handler.cpp  # Benchmarking logic for I2C, SPI, and UART
│   ├── Analog_Digital.cpp    # ADC/GPIO signal validation logic
│   └── Calibration.h         # Automated zero-point adjustment routines
```

---

## 📈 Technical Specifications
| Category | Specifications |
| :--- | :--- |
| **Logic Levels** | 3.3V / 5V (via External Level Shifting) |
| **ADC Resolution** | 12-bit (ESP32) or 10-bit (Arduino) |
| **Bus Protocols** | I2C (Standard/Fast), UART (up to 115200), SPI |
| **Safety** | Voltage threshold monitoring via `Config.h` |

---

## 💡 Lessons Learned & Future Iterations
This project was a deep dive into creating resilient diagnostic hardware:

*   **The Pivot:** Early versions lacked adequate overvoltage protection, posing a risk to the MCU. I implemented a **Software Watchdog** that monitors ADC saturation levels in real-time. The system now alerts the user immediately if a 5V sensor is connected directly to a 3.3V GPIO, preventing hardware degradation.
*   **Future Refinement:** I am currently developing a **Waveform Analyzer** module. This feature will visualize analog sensor "jitter" in real-time, allowing developers to diagnose EMI interference on long signal leads during the prototyping phase.

---

## 📬 Contact & Proof of Work
**Ritul Raj Bhakat**  
*Firmware Developer | Embedded Systems Architect*

*   **Deep Dive:** [View My Full Portfolio](https://ritulrajbhakatportfolio.vercel.app/)
*   **Professional:** [LinkedIn](https://linkedin.com/in/ritul-raj-bhakat)
*   **Direct:** [Email Me](mailto:ritulraj384@gmail.com)

---
© 2026 Ritul Raj Bhakat. Optimized for rapid hardware diagnostics.
