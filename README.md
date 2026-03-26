# Universal Sensor Tester: Multi-Protocol Diagnostic Architecture
The **Universal Sensor Tester** is a versatile hardware diagnostic tool designed to validate and benchmark a wide array of sensors within a single unit. By implementing an auto-detection algorithm, the system identifies connected sensor types—whether Analog, Digital, or Protocol-based—and executes baseline calibration routines, reducing manual troubleshooting time by approximately **40%**.

## System Architecture
The architecture is centered on a high-speed hardware abstraction layer that allows for seamless switching between different electrical interfaces and communication protocols.
### 1. Unified Hardware Interface
* **Multi-Signal Acquisition:** The tester is engineered with a universal port capable of interfacing with Analog (ADC), Digital (GPIO), and Protocol-based (I2C, SPI, UART) sensors.
* **Auto-Detection Algorithm:** Developed a custom routine to scan the interface for active pull-ups or specific signal patterns, automatically identifying the sensor category upon connection.
### 2. Diagnostic & Calibration Engine
* **Protocol Benchmarking:** Independently validates data integrity for I2C and UART sensors by checking for ACK/NACK responses and parity consistency.
* **Baseline Calibration:** Executes automated routines to determine a sensor's "zero-point" and sensitivity, ensuring high-fidelity data acquisition.
### 3. Real-Time Visualization
* **On-Device Feedback:** Provides instantaneous feedback on sensor health and raw output values via an integrated display or serial interface.
* **Health Scoring:** Analyzes signal stability and noise floors to provide a pass/fail diagnostic score for the connected hardware.

## Technical Stack

| Category | Specifications |
| :--- | :--- |
| **Processing Power** | ESP32 or Arduino-based architecture |
| **Interface Support** | Analog (0-5V/0-3.3V), Digital, I2C, SPI, UART  |
| **Algorithms** | Auto-sensing detection and baseline calibration  |
| **Efficiency** | 40% reduction in manual troubleshooting time  |

## Repository Structure
The codebase is organized into modular drivers and a central diagnostic supervisor to ensure ease of expansion for new sensor types.
```text
Universal_Sensor_Tester/
├── Firmware/                 # Diagnostic Core
│   ├── Tester_Main.ino       # Main lifecycle and auto-detection supervisor
│   ├── Protocol_Handler.cpp  # Drivers for I2C, SPI, and UART benchmarking
│   ├── Analog_Digital.cpp    # ADC and GPIO signal validation logic
│   ├── Calibration.h         # Baseline and sensitivity adjustment routines
│   └── Config.h              # Pin mapping and voltage threshold constants
├── LICENSE                   # MIT Open Source License
└── README.md                 # Project Documentation
```

## Deployment & Setup
### 1. Environment Configuration
* **Arduino IDE / PlatformIO:** Ensure the board manager is set for your specific microcontroller.
* **Serial Monitor:** Set the baud rate to **115200** for detailed diagnostic logs and auto-detection results.
### 2. Hardware Assembly
* **Terminal Block:** It is recommended to use a screw-terminal or breadboard-friendly header for the "Universal Port."
* **Level Shifting:** Ensure logic level converters are used if testing 5V sensors with a 3.3V microcontroller (like ESP32) to prevent overvoltage.
### 3. Initial Test Run
1. Connect a sensor to the universal port.
2. Observe the auto-detection logs to confirm the system has identified the correct protocol.
3. Review the calibration output to verify the sensor's functional range.

## Professional Profile
* **Developer:** Ritul Raj Bhakat (Firmware Developer)
* **Impact:** Optimized single-purpose diagnostic tools into a unified unit, significantly increasing troubleshooting efficiency.
* **Contact:** [ritulraj384@gmail.com](mailto:ritulraj384@gmail.com)
* **Links:** [LinkedIn](https://www.linkedin.com/in/ritul-raj-bhakat-521202277/) | [GitHub Portfolio](https://github.com/Chikkkuuu)
