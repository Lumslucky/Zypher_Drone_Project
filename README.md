# Zypher Drone FCU

This repository is preserved only for the Flight Control Unit (FCU)
Other parts of the project, can be found under the following repositories:

- [Zypher-Overview](https://github.com/Lumslucky/Zypher.git)
- [Zypher-Link](https://github.com/Lumslucky/Zypher_Link.git)
- [Zypher-Connect](https://github.com/Lumslucky/Zypher_Connect.git)

## Flight Control Unit Overview

This is the Main-Deice of the system, the drone itself. In this document, the complete functioning principle of the drone is explained in detail as well as why certain decision were made, what could be potentional flaws and what can be upgraded in the project.

This document is split into 3 main subjects:

- Housing
- PCB
- Embedded Software

## Housing

The housing was 3D modelled in Fusion360.
<!-- NOT READ YET -->

## PCB

The PCB has pretty interesting mechanical constraints:

- 8 Layer -- 1.6 mm
- 52 mm x 52 mm

The reason for these constraints is the promotion at [JLCPCB](https://jlcpcb.com/), as for just 2$, you are able to get a 8 Layer board with the maximum dimensions of 52 mm x 52 mm. (`I love you JLCPCB and sorry for using this for a project like this`).

By requirements the following hardware is needed:

- ESP32-S3-Wroom-1 (Main Control Unit)
- LSM6DSO32TR (IMU)
- LIS2MDLTR (Magnetometer)
- TESEO-LIV3ER (GPS Location)
- LTC4067 (Battery Management System)
- TPS62825 (Buck Regulator)
- USB4105 (USB-C Connector)
- 2x STSPIN240 (Motor Controllers)
- FZ2812 (RGB Addr. LED)
- 4x BLDC

## Embedded Software

The system is supposed to be a safety critical system (Unfortunately without any certifications).
The requirements for this software are the following:

- Real time (FreeRTOS as it is native on the ESP32)
- Easily Testable
- Safety Critical
- Lightweight **(FAST)**
- AIO Module (All in one, I want to push to the limits of the ESP32)
