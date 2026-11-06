# LED POV Holographic Display Fan

This repository contains the source code, hardware Bill of Materials (BOM), and assembly information for building an **LED POV (Persistence of Vision) Holographic Display Fan**. 

The device uses a high-speed brushless motor to spin a lightweight, rigid carbon fiber blade carrying a strip of individually addressable RGB LEDs. By rapidly updating the LED colors in synchronization with the motor's precise angular position, it creates the optical illusion of a floating, 3D holographic image or animation suspended in mid-air.

---

## Hardware Bill of Materials (BOM)

The hardware components listed below are sourced from the project's tracking cart. All listed prices are in **Canadian Dollars (C$)**.

| # | Component Description | Undiscounted Price | Discounted Price |
|---|---|:---:|:---:|
| 1 | **A2212 Brushless Motor (930KV/1000KV)** <br> Provides the high RPM required to achieve the POV illusion. | C$ 8.41 | C$ 7.82 |
| 2 | **30-125A XXD HW ESC Brushless Speed Controller** <br> Controls motor velocity safely via PWM signals. | C$ 7.37 | C$ 6.35 |
| 3 | **GHPYQKC Hall Sensor Module** <br> Detects a passing magnet on each rotation to calculate exact RPM and index timing. | C$ 1.75 | C$ 1.71 |
| 4 | **DC5V WS2812B LED Strip (1m / 144 LEDs, IP30)** <br> The dense light source array mounted to the fan blade. | C$ 10.38 | C$ 8.97 |
| 5 | **Carbon Fiber Strip (1mm-18mm Dia. / 1x500mm)** <br> Serves as the ultra-lightweight, zero-flex structural spinning arm for the LEDs. | C$ 5.85 | C$ 2.85 |
| 6 | **5x2mm N35 Strong Disc Neodymium Magnets** <br> Fixed to the spinning arm to trigger the Hall sensor once per full revolution. | C$ 12.05 | C$ 2.78 |
| - | **Total Component Cost** | **C$ 45.81** | **C$ 30.48** |

---

## How It Works

1. **The Spin:** The **A2212 Brushless Motor** spins a rigid, lightweight **Carbon Fiber Strip** acting as the blade assembly. This arm carries the high-density **WS2812B LED strip** at an optimized constant rate (typically >1000 RPM so the human eye perceives continuous motion).
2. **Synchronization:** Every time the blade completes a full 360-degree rotation, an **N35 Neodymium Magnet** embedded on the carbon fiber arm passes the stationary **Hall Sensor Module**, firing a hardware interrupt signal to an onboard microcontroller.
3. **The Projection:** The microcontroller uses this timing window to slice the rotation into hundreds of tiny angular segments, updating the color data frame of the entire LED strip slice-by-slice. Because of **Persistence of Vision (POV)**, your brain blends these instantaneous radial lines into a singular, seamless circular display canvas.
