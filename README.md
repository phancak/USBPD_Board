# ⚡ Modular Power Distribution & USB-PD System
### Intelligent Multi-Source Power Management for Mixed-Signal Platforms

## 📑 Quick Access
* [**📂 View Project Schematics (PDF)**](./Schematics/USBPD_Board_Schematics.pdf)

## 📖 Overview
This project is a high-efficiency, multi-input **Power Distribution Board** designed to provide stable, low-noise rails for interchangeable high-performance modules. It serves as the primary power hub for my **24-bit Precision ADC** and **STM32H7S3 System-on-Module** projects.

The system is engineered for maximum field flexibility, allowing a single instrumentation stack to be powered via laboratory bench supplies, USB-C PD sources, or mobile battery packs.

---

## 🛠 Technical Architecture

### 1. Power Entry & Negotiation
The board features a triple-redundant input strategy to support diverse operating environments:
* **USB Power Delivery:** Utilizes an **MCP2221A-I/ST** USB-to-I2C bridge to communicate with PD controllers and negotiate specific voltage profiles.
* **DC Input:** A standard barrel jack for **12V DC** wall converters, ideal for stationary bench-top development.
* **Battery Port:** A dedicated high-current connector for **Lithium-Ion/Polymer battery packs**, enabling untethered mobile data acquisition.

### 2. Digitally Enhanced Conversion
At the core is the **MCP19061-E/RTB**, a Digitally Enhanced Power Analog (DEPA) controller. 
* **Integrated MCU Control:** Combines the performance of an analog peak current mode controller with the flexibility of a microcontroller.
* **Dynamic Regulation:** Enables real-time telemetry and adjustment of output levels to match the requirements of the downstream load.
* **Protection Circuitry:** Hardware-level Under-Voltage Lockout (UVLO), Over-Voltage Protection (OVP), and thermal shutdown.

### 3. Distribution & Filtering
* **4-Way Power Bus:** Features four precision power connectors to distribute clean rails to a stack of interchangeable boards.
* **Noise Mitigation:** Designed with localized LC filtering and optimized PCB return paths to ensure switching noise from the DC-DC stage does not compromise the 120dB SNR performance of connected ADC modules.

---

## 📐 Hardware Specifications

| Feature | Component / Specification |
| :--- | :--- |
| **Main Controller** | Microchip MCP19061 (Integrated MCU + PWM) |
| **USB Interface** | MCP2221A-I/ST (USB-to-I2C/UART Bridge) |
| **Input Range** | Negotiated USB-PD / 12V DC / Battery |
| **Topology** | Synchronous Buck-Boost Converter |
| **Output Ports** | 4x Interconnect Headers |

---

## 🏗 System Integration Philosophy
This board was developed to solve the "Power Bottleneck" in modular hardware design. By decoupling the power stage from the logic and sensing stages, the system achieves:

1.  **High Modularity:** The "Interchangeable Device" architecture allows for swapping analog front-ends or digital processing units without redesigning the power delivery network.
2.  **Field Readiness:** The seamless transition to battery power makes the entire instrumentation stack viable for real-world environmental and oceanographic data collection.
3.  **Stability:** Centralized regulation reduces ground loops and phase coherency issues common in multi-board "nest" wiring.

---