# VLC-UTN — IEEE 802.15.13 Optical Communication System

Final degree project developed at **UTN Facultad Regional Buenos Aires**, implementing a 
complete Visible Light Communication (VLC) system based on the **IEEE 802.15.13-2023 
standard (HB-PHY physical layer)**.

The project covers the full stack: from standard specification and channel modeling, 
through digital baseband processing (DC-OFDM) implemented on FPGA, to analog front-end 
hardware and end-to-end system validation.

---

## System Architecture

The system is organized into the following subsystems, each with its own repository:

| Repository | Description | Stack |
|---|---|---|
| [dc-ofdm](https://github.com/vlc-utn/dc-ofdm) | DC-OFDM baseband TX/RX implementation with LDPC coding, for FPGA via HDL Coder | MATLAB/Simulink → VHDL |
| [channel_simulation](https://github.com/vlc-utn/channel_simulation) | Optical channel modeling and SNR/BER performance analysis | MATLAB |
| [digital_signals](https://github.com/vlc-utn/digital_signals) | Digital signal processing utilities and analysis scripts | MATLAB |
| [ieee8021513](https://github.com/vlc-utn/ieee8021513) | Network-level simulation of the IEEE 802.15.13 standard | OMNeT++ / C++ |
| [ieee802157](https://github.com/vlc-utn/ieee802157) | IEEE 802.15.7 reference simulation | C++ |
| [vlc_hardware](https://github.com/vlc-utn/vlc_hardware) | Analog front-end hardware design (schematics, BOM) | KiCad / HTML |
| [video_processing](https://github.com/vlc-utn/video_processing) | Video data pipeline for transmission over the VLC link | Python |
| [ethernet](https://github.com/vlc-utn/ethernet) | Ethernet interface integration for data I/O | Python |
| [vivado_tutorial](https://github.com/vlc-utn/vivado_tutorial) | Guide to the Vivado/Vitis FPGA development workflow | VHDL |
| [matlab_hdl_tutorial](https://github.com/vlc-utn/matlab_hdl_tutorial) | Guide to MATLAB HDL Coder workflow for FPGA generation | MATLAB |

---

## Key Technical Highlights

- **DC-OFDM modulation** compliant with IEEE 802.15.13 HB-PHY, implemented in 
  MATLAB/Simulink and synthesized to VHDL via HDL Coder for deployment on Xilinx FPGA 
  (Vivado 2024.1, MATLAB R2024a)
- **LDPC error correction** adapted from the standard's parity matrices to dual-diagonal 
  form for hardware compatibility
- **Optical channel simulation** including noise modeling and BER/SNR characterization
- **Full system validation** from simulation through hardware implementation

---

## Tools & Stack

`MATLAB R2024a` `Simulink` `HDL Coder` `VHDL` `Vivado 2024.1` `OMNeT++` `Python` `C++` `KiCad` `Git`

---

## Authors

Developed as a Final Degree Project at UTN FRBA, 2024–2025.
