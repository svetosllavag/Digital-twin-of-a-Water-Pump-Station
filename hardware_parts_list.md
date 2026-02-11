# Mini Pump Station Hardware (Arduino Prototype)

## Purpose
Build a small, safe, low-voltage (5V) physical model of a pump station to generate telemetry signals that can be used in the digital twin.

The prototype is designed for demonstration, not for full hydraulic simulation.

---

## Hardware Overview
The mini station will include:
- 1–3 identical 5V DC water pumps (Pump A, Pump B, Pump C)
- a small reservoir (container)
- tubing for water circulation
- sensors for level, current, and optional water quality
- Arduino-based control and data logging

Power is provided by a USB power bank for safety.

---

## Parts List

### Pumps & Plumbing
- **5V mini submersible water pump ×3**
- **Silicone tubing** (6–8 mm inner diameter)
- **Plastic container / reservoir**


### Electronics & Control
- **Arduino Uno 
- **Logic-level MOSFET module ×3** 
  *(Alternative: 3-channel relay module)*
- **INA219 current sensor module** (pump current + power estimate)
- Jumper wires
- Breadboard 

### Sensors
- **Ultrasonic sensor** 
  - HC-SR04 
  - JSN-SR04T
- **Turbidity sensor module (optional)**
  - SEN0189-style turbidity sensor

### Power
- **USB power bank** (5V output)
- USB cable for Arduino
