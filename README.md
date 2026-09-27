# AAHAR-NETRA
**Inline Spectral Food Safety & Contamination Screening System**

An SIH prototype (PS2) that screens food items on a conveyor line — poultry and leafy greens — for microbial/bacterial contamination in real time, using UV-induced fluorescence and NIR absorption as a low-cost multispectral proxy for lab-grade detection, then diverts flagged items automatically.

---

## 🎯 Problem

Manual food-safety inspection on processing lines is slow, subjective, and can't catch microbial contamination (bacterial biofilm, pathogen presence) that isn't visible to the naked eye. This project builds a low-cost, real-time inline scanner that flags contaminated items before they move downstream.

## 🧪 How it works

1. An item passes under a light-sealed hood on the conveyor.
2. **365nm UV LEDs** pulse on — bacterial byproducts/biofilm fluoresce, captured by the camera and spectral sensor.
3. **850nm/940nm NIR LEDs** pulse on — checks surface moisture/tissue absorption as a corroborating signal.
4. The **AS7265X** sensor's 18 wavelength channels let the system separate the bacterial fluorescence band from surface-specific signals (e.g. chlorophyll autofluorescence on leafy greens).
5. A Raspberry Pi classifies the combined signal as **Normal** or **Contamination-Suspect**.
6. If flagged, a servo-driven diverter gate pushes the item into a reject lane.

## 🔧 Hardware

| Component | Purpose |
|---|---|
| Raspberry Pi 4 (4GB) | Main processor — runs classification, controls LEDs/actuator |
| AS7265X Triad Spectroscopy Sensor | 18-channel spectral scanner (UV–NIR) |
| Pi Camera Module 2 NoIR | Captures fluorescence glow + spatial context |
| 365nm UV LED strips | Excites bacterial fluorescence |
| 850nm/940nm NIR LED strips | Checks moisture/tissue absorption |
| Matte black hood enclosure | Blocks ambient light for clean readings |
| Relay/transistor switch | Safely drives LEDs from Pi GPIO |
| 5V 3A USB-C adapter | Power |
| Servo motor + diverter arm | Physically sorts flagged items |
| Ribbon cable / jumper wires | Wiring |

## 📁 Repo structure

```
/dashboard      → live monitoring dashboard (HTML/JS)
/pi-scripts     → sensor reading, classification, actuator control (Python)
/docs           → problem statement, PPT, research notes
README.md       → this file
```

## 🖥️ Dashboard

A real-time monitoring interface showing the live conveyor feed, per-item detection status, spectral signature chart, and contamination risk indicators.

- Live demo: *add your published link here*
- Currently runs on simulated data; see `/pi-scripts` for the plan to connect it to real Pi sensor output via a local Flask server.

## 🚧 Status / Roadmap

- [x] Dashboard UI
- [x] Component selection finalized
- [ ] Sensor calibration (clean vs. contaminated reference samples)
- [ ] Classification thresholds for poultry vs. leafy greens
- [ ] Flask backend connecting real sensor data to dashboard
- [ ] Physical diverter gate integration

## ⚠️ Scope note

This system flags *possible* microbial contamination as a rapid pre-screening filter — it does not identify exact bacterial species. Species-level confirmation still requires lab methods (culturing/PCR).

Built for Smart India Hackathon (SIH).
