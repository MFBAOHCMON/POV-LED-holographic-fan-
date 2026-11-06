# 🔌 Hardware Wiring & Pin Mapping Specifications

This document outlines the electrical connections, signal routing, and power distribution paths required to safely interface the system components.

## 📌 Wiring Table

| Component | Pin / Cable | Target Connection | Connection Type | Technical Notes |
| :--- | :--- | :--- | :--- | :--- |
| **XXD 30A ESC** | Power Leads (Red/Black) | Main Battery / Power Source | High-Current DC | Observe polarity. Handles raw input voltage. |
| | 3x Motor Phase Wires | A2212 Brushless Motor Wires | 3-Phase AC | Swap any two wires to reverse motor direction. |
| | BEC Red (+5V) | Microcontroller 5V Rail | Power Output | Provides regulated 5V power to the logic rail. |
| | BEC Black (GND) | Microcontroller GND Rail | Ground | Common system ground baseline. |
| | BEC White/Yellow | Microcontroller PWM Pin | Signal Input | Receives servo PWM signals to regulate motor speed. |
| **Hall Sensor Module** | VCC | Microcontroller 5V or 3.3V Rail | Power Input | Refer to specific board variation for voltage tolerance. |
| | GND | Microcontroller GND Rail | Ground | Common system ground baseline. |
| | DO (Digital Output) | Microcontroller GPIO Pin | Signal Output | Triggers a HIGH/LOW state change upon magnetic threshold. |
| | AO (Analog Output) | Microcontroller ADC Pin | Signal Output | *Optional:* Outputs variable voltage based on magnetic proximity. |
| **WS2812B LED Strip** | +5V | Dedicated 5V Power Supply | Power Input | Do not power a high-density strip directly from an MCU pin. |
| | GND | Dedicated 5V PSU & MCU GND | Ground | Essential to tie the LED ground and MCU ground together. |
| | DIN (Data Input) | Microcontroller GPIO Pin | Signal Input | Needs a 330–470 Ω resistor inline to prevent data corruption. |

## 🛠 Schematic Layout

<!-- Place your custom wiring diagram or schematic image below -->
![System Wiring Diagram](path/to/your/wiring-diagram-image.png)

## ⚠ Electrical Isolation & Power Handling Guidelines

* **Common Ground Baseline:** Ensure all negative terminals (GND) from the main battery, speed controller, microcontroller, and LED external power supply are directly tied together to establish a unified reference voltage.
* **LED Power Constraints:** The high-density WS2812B addressable strip requires significant power. Isolate its +5V injection point from the microcontroller's onboard regulator to protect your logic components from severe voltage drops or thermal overloading.
* **Data Line Protection:** Place a resistor inline on the LED data connection near the first pixel to suppress voltage spikes traveling along the signal line.
