# 🚁 Nano Drone DGCA Safety Failsafes 

Welcome to the concept repository for an autonomous, lightweight safety system designed specifically for sub-250-gram (Nano) drones in India. 

Under the Indian DGCA Drone Rules, Nano drones do not require a Remote Pilot Certificate (RPC) or a Unique Identification Number (UIN) for non-commercial flights in Green Zones. However, they are strictly limited to a **15-meter (50 feet) maximum altitude**. This project aims to build open-source, hardware-level failsafes into custom drones so they automatically obey these laws without relying on the pilot's manual reflexes.

## 📌 About This Project
When building experimental Nano drones from scratch, high-powered brushless motors can easily shoot the drone past the 15-meter legal limit in a split second. Furthermore, a lost radio connection can result in dangerous flyaways. 

This project solves these issues by creating a "digital ceiling" and automated recovery systems using a custom Arduino-based flight controller, paired with a future Raspberry Pi AI companion computer for smart obstacle avoidance.

## ✨ Proposed Features

*   **🔒 The 15-Meter Digital Ceiling:** Fuses data from a barometer (air pressure) and a downward-facing Laser Time-of-Flight (ToF) sensor. If the drone reaches 14.8 meters, the software actively locks the throttle, making it physically impossible to breach the 15-meter DGCA limit.
*   **📡 Smart Return-to-Home (RTH):** A radio-frequency watchdog constantly monitors the controller connection. If the signal drops for more than 1 second, the drone automatically stabilizes at a legal 10-meter altitude and uses GPS to slowly fly back to its launch coordinates.
*   **🛬 Laser Auto-Landing:** Upon reaching the home coordinates, the laser ToF sensor tracks the exact distance to the ground. When the drone is just a few inches from the floor, it instantly cuts motor power for a perfectly smooth touchdown.
*   **🪂 Emergency Micro-Parachute:** An independent, spring-loaded parachute system with its own coin-cell battery and accelerometer. If a motor fails and the drone goes into free-fall, the parachute deploys to prevent kinetic impact on the ground.
*   **🧠 Raspberry Pi AI (Future Scope):** A lightweight Raspberry Pi Zero 2 W running a local AI vision model to analyze telemetry and downward camera feeds in real-time, sending obstacle-avoidance override commands to the Arduino.

## 🛠️ Planned Tech Stack

### Hardware
*   **Flight Controller:** Custom Arduino-compatible microcontroller
*   **Sensors:** 6-axis IMU (Gyro/Accelerometer), Barometer, Laser ToF (Time-of-Flight), and GPS module
*   **Companion Computer:** Raspberry Pi Zero 2 W (for AI processing)

### Software
*   **Control Loop:** C++ (Arduino) for 250Hz PID stabilization and sensor fusion
*   **AI Model:** Local quantized Qwen model running via edge inference for real-time hazard detection

## 🚀 Current Status: Proposal Phase
**Note:** This project is currently in the conceptual and design phase. The hardware has not been assembled, and the codebase is actively being planned. The HTML proposal and documentation can be viewed on the [GitHub Pages site](https://mepython313.github.io).

## 📄 Licensing

Because this project consists of ideas, software, and physical hardware, it uses a split licensing model:

*   **Documentation & Proposals:** Published under **[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)**. You may share and adapt this proposal, provided you give credit and share alike.
*   **Future Software (Code):** Will be licensed under **GNU GPLv3**. Any improvements to the code must remain open-source.
*   **Future Hardware (PCB & 3D Files):** Will be licensed under **CERN-OHL-S**. Modified hardware designs must be shared with the community.

---
*Developed by Prakshit Gupta [@MePython313](https://github.com/MePython313) | Hyderabad, India*
