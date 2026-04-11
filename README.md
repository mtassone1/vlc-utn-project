# 💡 VLC-UTN — IEEE 802.15.13 Visible Light Communication System

Final degree project developed at **UTN Facultad Regional Buenos Aires**, implementing a
complete **Visible Light Communication (VLC / Li-Fi)** system from the ground up, based on the
**IEEE 802.15.13-2023 standard (HB-PHY physical layer)**.

The project spans the full engineering stack: standard specification, optical channel modeling,
digital baseband processing (DC-OFDM) implemented on FPGA, analog front-end hardware design,
network-layer protocol simulation, and end-to-end system validation.

> 📅 Submitted February 2025 · 10 repositories · UTN FRBA

---

## System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                      VLC System Overview                            │
│                                                                     │
│   ┌──────────────┐    optical     ┌──────────────┐                  │
│   │  TX Hardware │───────────────▶│  RX Hardware │                  │
│   │  LED driver  │   visible      │  Photodiode  │                  │
│   └──────┬───────┘    light       └──────┬───────┘                  │
│          │                               │                          │
│   ┌──────▼──────────────────────────────▼───────┐                  │
│   │           FPGA  (PYNQ-Z2 / Red Pitaya)      │                  │
│   │   ┌────────────┐         ┌────────────────┐  │                  │
│   │   │  DC-OFDM   │         │   DC-OFDM      │  │                  │
│   │   │  TX        │         │   RX           │  │                  │
│   │   │  LDPC enc  │         │   LDPC dec     │  │                  │
│   │   │  IFFT      │         │   FFT + EQ     │  │                  │
│   │   └────────────┘         └────────────────┘  │                  │
│   │       ↑  VHDL generated via MATLAB HDL Coder  │                  │
│   └──────────────────────────────────────────────┘                  │
│                                                                     │
│   ┌──────────────────────────────────────────────┐                  │
│   │       MATLAB Simulation Layer                │                  │
│   │  channel_simulation · digital_signals        │                  │
│   │  BER/SNR · delay spread · Monte Carlo        │                  │
│   └──────────────────────────────────────────────┘                  │
│                                                                     │
│   ┌──────────────────────────────────────────────┐                  │
│   │       Network Simulation (OMNeT++)           │                  │
│   │  ieee8021513 · ieee802157                    │                  │
│   └──────────────────────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Repositories

| Repository | Description | Stack |
|---|---|---|
| [**dc-ofdm**](https://github.com/vlc-utn/dc-ofdm) | DC-OFDM TX/RX physical layer with LDPC coding. MATLAB/Simulink model auto-synthesized to VHDL via HDL Coder and deployed on Xilinx FPGA | MATLAB · Simulink · VHDL · Vivado |
| [**channel_simulation**](https://github.com/vlc-utn/channel_simulation) | Optical channel model: SNR and BER characterization, delay spread, illuminance distribution, Monte Carlo analysis | MATLAB |
| [**digital_signals**](https://github.com/vlc-utn/digital_signals) | DSP library covering OFDM, PAM/QAM/PSK, pulse shaping, zero-forcing equalizer, fading channel models, receiver impairments | MATLAB |
| [**ieee8021513**](https://github.com/vlc-utn/ieee8021513) | Network-level simulation of the IEEE 802.15.13-2023 MAC/PHY stack | OMNeT++ · C++ |
| [**ieee802157**](https://github.com/vlc-utn/ieee802157) | Reference simulation for the earlier IEEE 802.15.7 standard | OMNeT++ · C++ |
| [**vlc_hardware**](https://github.com/vlc-utn/vlc_hardware) | Analog front-end PCB design: LED transmitter, photodiode receiver, VNA measurements | KiCad |
| [**ethernet**](https://github.com/vlc-utn/ethernet) | Red Pitaya FPGA platform integration: Python socket control, AXI register maps, bitstream loading, Vivado IP cores | Python · Vivado |
| [**video_processing**](https://github.com/vlc-utn/video_processing) | Python pipeline for video and image data transmission over the VLC link | Python |
| [**vivado_tutorial**](https://github.com/vlc-utn/vivado_tutorial) | 12-chapter FPGA development guide: pure VHDL → AXI4 IP integration → HDL Coder → HLS → debugging, targeting PYNQ-Z2 | VHDL · Verilog · Vivado |
| [**matlab_hdl_tutorial**](https://github.com/vlc-utn/matlab_hdl_tutorial) | 5-chapter MATLAB-to-FPGA tutorial: combinational logic, cosimulation, FPGA-in-the-loop, IP core generation, fixed-point arithmetic | MATLAB · HDL Coder |

---

## Key Technical Highlights

- **DC-OFDM modulation** compliant with IEEE 802.15.13 HB-PHY, designed in MATLAB/Simulink and synthesized to production-ready VHDL via HDL Coder (MATLAB R2024a · Vivado 2024.1)
- **LDPC forward error correction** with custom dual-diagonal parity matrix adaptation for hardware compatibility with the MathWorks Wireless HDL Toolbox
- **Optical channel model** with Monte Carlo simulation: SNR, BER, delay spread, and illuminance characterization for indoor VLC environments
- **Full DSP library** implementing modulation schemes (PAM, QAM, PSK, OFDM), zero-forcing equalization, pulse shaping, and receiver impairment compensation
- **Network-layer simulation** of both IEEE 802.15.13-2023 and IEEE 802.15.7 in OMNeT++, covering MAC/PHY interaction
- **Analog hardware** — custom PCB design for LED driving and photodetection with VNA-characterized frequency response
- **FPGA platform integration** on Red Pitaya via Python socket interface, with documented AXI memory map and bitstream loading pipeline
- **End-to-end validation** from optical channel simulation through FPGA synthesis to physical hardware measurement

---

## Tools & Stack

`MATLAB R2024a` `Simulink` `HDL Coder` `VHDL` `Verilog` `Vivado 2024.1` `PYNQ-Z2` `Red Pitaya` `OMNeT++` `C++` `Python` `KiCad` `AXI4` `Git`

---

## Authors

Developed as a Final Degree Project (*Proyecto Final de Carrera / Tesina*) at **UTN Facultad Regional Buenos Aires**, 2024–2025.

→ Organization: [github.com/vlc-utn](https://github.com/vlc-utn)
