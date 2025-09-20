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

## 🎯 **System and Virtual Machine Configuration**

To ensure optimal performance, I configured a **Virtual Machine (VM)** with the following specifications:

| **Specification** 💻    | **Details** 📋          |
|-----------------------|-----------------------|
| **Operating System** 🐧  | Ubuntu 24.04.3         |
| **RAM** 💾               | 5GB                   |
| **Storage** 💿           | 50GB HDD              |
| **vCPUs** ⚡             | 4                     |

### **TOOL CHECK**

#### <ins>**Yosys**</ins>
```bash
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make               # If make is not installed
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
# Yosys build depends on a Git submodule called abc, which hasn't been initialized yet. You need to run the following command before running make
$ git submodule update --init --recursive
$ make 
$ sudo make install
```
<img width="835" height="231" alt="image" src="https://github.com/user-attachments/assets/096af5ca-23d0-4981-a04c-e6c16d3ad07a" />

#### <ins>**Iverilog**</ins>
```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```
<img width="777" height="657" alt="image" src="https://github.com/user-attachments/assets/ba6f89e0-f2af-4bc6-bb6a-d89a2e4ff5f5" />

#### <ins>**gtkwave**</ins>
```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```
<img width="550" height="87" alt="image" src="https://github.com/user-attachments/assets/ef041277-1659-4f1f-8bee-2b083db4b1d5" />
