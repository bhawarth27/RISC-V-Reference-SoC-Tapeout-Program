# RISC-V-Reference-SoC-Tapeout-Program
This 20-week program guides students, educators, and professionals through end-to-end RISC-V SoC design and fabrication using Synopsys tools and the SCL180 PDK. Part of India’s Semiconductor Mission, it offers hands-on RTL-to-silicon training, with execution at IIT Gandhinagar, creating a reusable, national framework for academic chip tapeouts.

# Week 0 - Tools Installation + Environment Setup

<img width="681" height="556" alt="image" src="https://github.com/user-attachments/assets/e91242ef-69ee-4360-9917-e880f020f7ab" />

# ASIC / SoC Design Flow Overview

This flow describes the complete journey of chip design from **C modeling** to **silicon fabrication (GDSII)**.

## 1. Chip Modeling (O0 / O1)
- Write functional specifications in **C model**.  
- Use **GCC** for compilation and verification.  
- Testbenches in C validate correctness.  
- Acts as the **golden reference model** for later RTL verification.

## 2. RTL Design (O2)
- Convert the C model into **RTL (Verilog)** – the soft copy of hardware.  
- Includes **Processor, Peripherals, and IPs**.  
- Verified against the C model to ensure functional accuracy.

## 3. Synthesis & IP Integration
- RTL is synthesized into a **Gate-Level Netlist**.  
- **Macros (synthesized RTL)** and **Analog IPs** are integrated.  

## 4. SoC Integration (O3)
- All components (processor, IPs, GPIOs) are brought together.  
- Physical design steps: **Floorplanning, Placement, Clock Tree Synthesis (CTS), Routing**.  

## 5. Final Output – GDSII
- Perform **DRC/LVS checks** to ensure manufacturability and correctness.  
- Generate **GDSII**, which is sent to the foundry for fabrication.

---

📌 **In short:**  
C Model (Specs) → RTL (Verilog) → Synthesis → SoC Integration → GDSII (Fabrication).
