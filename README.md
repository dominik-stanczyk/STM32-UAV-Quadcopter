# Custom UAV Flight Controller Project (STM32)

A professional, from-scratch engineering project aimed at developing a manual quadcopter flight controller using STM32, focused on real-time systems, signal processing, and low-level hardware integration.

---

## Project Architecture & Tech Stack

The mindmap below outlines the core engineering domains, communication protocols, and algorithms utilized in this project.
```mermaid
mindmap
    root(UAV Drone)
        Hardware & Power Systems
            STM32 Nucleo + IMU
            EMI Shielding
            Power Conditioning
            Assembly
            4-Layer PCB 
        Firmware
            Low-Level Protocols
                I2C
                SPI
            Sensor Fusion
                Complementary Filter
                Kalman Filter
            Real-time Loop
            Data Offloading
                DMA usage for I2C/SPI
            Flight Controler
            PID Algorithm
        RF Communication & Safety
            UART connection to RF Receiver
            Digital packet decoding
                CRSF/SBUS protocol
            Signal Processing
            Signal Calibration
            Input mapping
            Critical Safety
        Telemetry & 3D Diagnostics
            Data Pipeline
                UART-to-USB
            Data Framing
            Python multi-threaded backend
            3D Real-time orientation visualizer
                Python
                OpenGL
            ESC Diagnostics
                Real-time motor thrust & PID error tracking
            
```
---

## Project Timeline & Stage Roadmap

```mermaid
%%{init: {
  'theme': 'base',
  'themeVariables': {
    'primaryColor': '#1e1e2e',
    'primaryTextColor': '#cdd6f4',
    'primaryBorderColor': '#b4befe',
    'lineColor': '#a6adc8',
    'cScaleColor0': '#89b4fa',
    'cScaleColor1': '#a6e3a1',
    'cScaleColor2': '#f9e2af',
    'cScaleColor3': '#fab387',
    'cScaleColor4': '#f38ba8'
  }
}}%%
timeline
    title UAV Drone Project Development Timeline
    Stage 1 : STM32 Nucleo + IMU : IMU Register Reading via I2C : Python/OpenGL 3D Visualization
    Stage 2 : Sensor Fusion Algorithms : RF Protocol Decoding : Initial PID Loop Development
    Stage 4 : F450 Frame Assembly : Manual Hover Tests
    Stage 5 : 4-Layer Flight Controller PCB Design : Advanced PID Tuning : Field Flight Testing
    Stage 6 : Implementing RaspberryPI With AI Face Recognition : Final Engineering Thesis Documentation
```
---

## Detailed Engineering Task Checklist

*Status: Tracking Stage 1 objectives.*

### 1. Hardware & Power Systems
- [x] Select and verify IMU sensors (BMI270/LSM6DSOX)
- [ ] **Assemble a solderless desktop prototyping rig (Nucleo + IMU)** `<- IN PROGRESS`
- [ ] Design the flight controller schematic diagrams (KiCad/Altium)
- [ ] Route the 4-layer PCB layout with dedicated GND shielding planes
- [ ] Solder components and perform Low-ESR power delivery validation

### 2. Firmware (STM32 / Embedded C)
- [ ] Configure low-level I2C/SPI peripheral drivers for IMU data streaming
- [ ] Implement a non-blocking DMA pipeline for sensor acquisition
- [ ] Develop the Kalman Filter algorithm for precise angle estimation
- [ ] Set up a hardware timer ISR for a deterministic 400Hz control loop
- [ ] Code the Motor Mixer and configure stable hardware PWM outputs for ESCs
- [ ] Implement and tune the triple-loop PID orientation controller

### 3. RF Communications & Safety
- [ ] Interface the RF Receiver with the STM32 via Hardware UART
- [ ] Implement a fast packet parser for CRSF/SBUS digital protocols
- [ ] Design stick input mapping, deadbands, and calibration routines
- [ ] Develop a 2-stage Failsafe state machine (Self-leveling -> Throttle ramp-down -> Hard cutoff)

### 4. Telemetry & PC Diagnostics
- [ ] Establish high-speed UART-to-USB telemetry data streaming
- [ ] Design a robust binary data framing protocol with CRC checksums
- [ ] Build a multi-threaded Python backend for non-blocking serial acquisition
- [ ] Implement the real-time 3D OpenGL orientation visualizer
- [ ] Create GUI diagnostic graphs for PID tracking and real-time ESC output monitoring
