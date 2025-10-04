## What is a System-on-Chip (SoC)?  

⚡ **A System-on-Chip (SoC) is essentially an entire computer integrated into a single silicon chip.**  
It brings together **CPU, memory, I/O interfaces, GPU, DSP, power management, and connectivity modules** into one highly optimized package.  

### 🎯 Why SoCs?  
- 📦 **Compactness** → Perfect for mobile & embedded devices  
- 🔋 **Energy Efficiency** → Extends battery life in wearables, IoT, smartphones  
- ⚡ **High Performance** → Reduced latency with on-chip communication  
- 💰 **Cost-Effective** → One chip instead of multiple discrete components  

---

### Key Parts of an SoC

1. **CPU (Central Processing Unit)**:
   - The brain of the SoC, handling all main instructions and decisions.
   - Manages tasks like calculations, data processing, and running applications.

2. **Memory**:
   - **RAM** (Random Access Memory) for temporarily storing data as you use the device.
   - **ROM** or **Flash Storage** for keeping information saved even when the device is off.

3. **I/O Ports (Input/Output)**:
   - Connects the SoC to other parts or devices, like a camera, USB, or even your headphones.
   - These ports let the SoC send and receive data externally.

4. **Graphics Processing Unit (GPU)**:
   - Responsible for creating visuals on your screen.
   - Used for gaming, watching videos, or any activity involving images or animations.

5. **Digital Signal Processor (DSP)**:
   - Specialized in processing audio and video signals.
   - Helps with tasks like noise reduction in phone calls or enhancing video quality.

6. **Power Management**:
   - Regulates power usage within the SoC, making sure the chip operates efficiently.
   - This is crucial for extending battery life in portable devices.

7. **Special Features**:
   - Additional features may include Wi-Fi, Bluetooth, and even security modules for safe data handling.
   - These features vary depending on the specific purpose of the SoC.

## 🔥 Types of SoCs  

-  **Microcontroller-based SoC** → Small-scale, low-power control (IoT nodes, appliances)  
-  **Microprocessor-based SoC** → Runs OS, multitasking (smartphones, tablets)  
-  **Application-Specific SoC (ASIC SoC)** → Domain-optimized (AI accelerators, automotive, networking)  

---

##  The SoC Design Flow  

<img width="960" height="720" alt="image" src="https://github.com/user-attachments/assets/a2b88b5a-dcd3-429f-8f19-fb893321fc76" />


---

## 👶⚡ VSDBabySoC – A Tiny but Powerful RISC-V SoC  

---

## 🌟 Introduction  

In the world of chip design, even the simplest SoC can teach us **how digital and analog domains come together on silicon**.  
**VSDBabySoC** is one such platform — a **compact educational SoC** that integrates three key blocks:  

- 🧠 **RVMYTH Core** – a lightweight RISC-V CPU  
- ⏱️ **8× PLL** – stable clock generation  
- 🎚 **10-bit DAC** – digital-to-analog interface  


<img width="2270" height="1260" alt="image" src="https://github.com/user-attachments/assets/a3946dc3-828e-4142-952e-5bd1408bda8c" />


---

##  What Makes Up VSDBabySoC?  

VSDBabySoC is a compact yet highly capable System on Chip (SoC) based on the RISC-V architecture. The primary objective of designing this small-scale SoC is to facilitate the simultaneous testing of three open-source intellectual property (IP) cores for the first time while also calibrating its analog components. The VSDBabySoC incorporates an RVMYTH microprocessor, an 8x phase-locked loop (PLL) for generating a stable clock signal, and a 10-bit digital-to-analog converter (DAC) that enables communication with various analog devices.

1. **Initialization and Clock Generation**: Upon receiving an initial input signal, BabySoC activates the PLL. The PLL generates a stable and synchronized clock signal, which is essential for coordinating the activities of the RVMYTH processor and DAC. By synchronizing the system, the PLL ensures that all components operate in harmony, avoiding timing mismatches and ensuring data integrity.

2. **Data Processing in RVMYTH**: Within BabySoC, RVMYTH plays a central role in processing data. Specifically, it utilizes its `r17` register to hold and cycle through values that are used by the DAC. As RVMYTH executes instructions, it sequentially updates `r17` with new data, preparing it for analog conversion. This cyclical processing allows BabySoC to generate continuous data streams that the DAC can output.

3. **Analog Signal Generation via DAC**: The DAC receives the processed digital values from RVMYTH and converts them into an analog signal. This output, saved in a file named `OUT`, can be fed to external devices like TVs and mobile phones, which interpret the analog signals to produce sound or video. This functionality enables BabySoC to interface with consumer electronics, showcasing how digital data can drive multimedia outputs in real-world applications.

   ![333622249-04238eab-4d48-4d57-9061-f8b660a83d6e](https://github.com/user-attachments/assets/38253bb7-b658-496d-a043-15402219e089)


### BabySoC components

   - **RVMYTH (RISC-V CPU)**: RVMYTH is the brain of BabySoC, based on the open-source RISC-V design. It's a simple, customizable CPU that handles processing tasks and communicates with other parts of the SoC. This flexibility makes RVMYTH ideal for learning and experimenting with CPU architecture.

   - **Phase-Locked Loop (PLL)**: The PLL generates a stable clock signal to keep everything in BabySoC running in sync. It matches the SoC's clock with a reference frequency, ensuring reliable timing for RVMYTH and DAC. PLLs are widely used to keep signals aligned in communication and timing circuits.

   - **Digital-to-Analog Converter (DAC)**: The DAC turns digital signals from RVMYTH into analog output, like sound or video. This allows BabySoC to connect with external devices that use analog signals, such as speakers or displays.

## PLL

   - A Phase-Locked Loop (PLL) is a control system that generates an output signal whose phase is synchronized with an input signal. Both signals will have the same frequency and can either have no phase difference or a constant phase difference.
     
**Block Diagram**
![333810875-fd7730e9-a867-4ce3-bfc6-9453e3d8ad14](https://github.com/user-attachments/assets/217d602f-003d-4606-9bca-855a4832764c)<br>
A PLL typically consists of three main components:
   - **Phase Detector:** Compares the input signal (reference) with the output signal from the oscillator and generates an error signal based on the phase difference.
   - **Loop Filter:** Usually a low-pass filter that processes the error signal to produce a control voltage.
   - **Voltage-Controlled Oscillator (VCO):** Adjusts its frequency based on the control voltage to match the input frequency.

**Functionality:**
   - The PLL aims to lock the output frequency to the input frequency, maintaining a constant phase relationship between the two signals.
   - In some cases, a frequency divider may be used in the feedback loop to produce an output that is a multiple of the reference frequency.

**Why Can’t Off-Chip Clocks Always Be Used?**

   1. Clock Distribution Delays:
      - Using a single clock source for an entire chip can lead to delays due to long wiring distances, which can affect timing.
   2. Clock Jitter:
      - Off-chip clocks may experience variations in signal timing, known as jitter, which can disrupt synchronization.
   3. Different Frequency Requirements:
      - Various blocks within the same chip may require different clock frequencies. For example, one block might need 200 MHz while another needs 100 MHz.
   4. Crystal Frequency Deviations:
      - When quartz crystals are used as clock sources, they come with a frequency error measured in parts per million (ppm).
      - A higher ppm error means that the frequency can deviate more from the desired value, affecting timing precision.
   5. Frequency Stability:
      - The stability of a crystal’s frequency can vary with temperature. Crystals with higher ppm errors are more likely to exhibit larger frequency variations when temperature changes.
   6. Total Frequency Error:
      - The overall frequency error of a crystal includes contributions from:
         - Frequency Tolerance: The initial error in frequency.
         - Frequency Stability: Variation over temperature.
         - Aging: Changes in frequency over time.
      - Higher ppm errors in any of these factors can lead to larger total frequency errors, impacting the accuracy of timing references in electronic systems.

## DAC

   - A Digital to Analog Converter (DAC) is an electronic device that converts a digital input signal (represented in binary code) into an analog output signal.
   1. Digital Signal Representation:
      - The digital input is composed of bits, specifically 0s and 1s, which represent the digital information.
   2. Structure:
      - A DAC typically has multiple binary inputs and a single analog output.
      - The number of binary inputs is usually a power of two (e.g., 2, 4, 8, 16).
   3. Types of DACs:
      - There are primarily two common types of DACs:
         - Weighted Resistor DAC: Uses resistors with different weights to convert the digital signal into an analog voltage.
   ![binary_weighted_resistors](https://github.com/user-attachments/assets/344e4ffd-7509-41e7-ac42-21a553b3db11)

         - R-2R Ladder DAC: Uses a repeating network of resistors to achieve the same effect, allowing for simpler design and easier scaling.
   ![comb99 gif copy](https://github.com/user-attachments/assets/5c15f424-1a94-4424-b019-a76c0ca0db43)

   4. In VSDBabySoC:
      - In the VSDBabySoC design, we are utilizing a 10-bit DAC, which means it can take a digital input represented by 10 bits and convert it into an analog output.

</details>

---


## 📂 Project Structure

```txt
VSDBabySoC/
├── src/
│   ├── include/      # Header files (*.vh)
│   ├── module/       # Verilog + TLV modules
│   │   ├── vsdbabysoc.v   # Top-level module
│   │   ├── rvmyth.v       # CPU
│   │   ├── avsdpll.v      # PLL
│   │   ├── avsddac.v      # DAC
│   │   └── testbench.v    # Testbench
└── output/           # Simulation outputs
```

---

## 🛠️ Setup

### 📥 Cloning the Project

```bash
git clone https://github.com/manili/VSDBabySoC.git
cd VSDBabySoC/
```

📂 You’ll see:

* `src/` (modules)
* `images/` (visuals)
* `output/` (simulation results)

---

## 🔧 TLV → Verilog Conversion

Since **RVMYTH** is written in **TL-Verilog (.tlv)**, we need to convert it to Verilog before simulating.

```bash
# Install tools
sudo apt update
sudo apt install python3-venv python3-pip

# Create virtual env
python3 -m venv sp_env
source sp_env/bin/activate

# Install SandPiper-SaaS
pip install pyyaml click sandpiper-saas

# Convert TLV → Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```

✅ Now you’ll have `rvmyth.v` alongside your other Verilog files.

---

##  Simulation Flow

### 🔹 Pre-Synthesis Simulation

```bash
mkdir -p output/pre_synth_sim

iverilog -o output/pre_synth_sim/pre_synth_sim.out \
  -DPRE_SYNTH_SIM \
  -I src/include -I src/module \
  src/module/testbench.v

cd output/pre_synth_sim
./pre_synth_sim.out
```

📊 View in GTKWave:

```bash
gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```

### 🔍 Signals to Observe

*  **CLK** → Input clock (from PLL)
*  **reset** → Reset signal
*  **OUT (DAC)** → Output from DAC (appears digital in sim)
*  **RV_TO_DAC[9:0]** → 10-bit RVMYTH output → DAC input

---
### 🧠 The Instruction Program Driving BabySoC  

1. Increment counters,
2. Accumulate values into `r17`,
3. Oscillate them to generate analog waveforms,
4. Hold in a final loop.

| #  | Instruction         | Action                  |
| -- | ------------------- | ----------------------- |
| 0  | `ADDI r9, r0, 1`    | r9 = 1 (decrement variable) |
| 1  | `ADDI r10, r0, 43`  | r10 = 43 (looping variable)   |
| 2  | `ADDI r11, r0, 0`   | r11 = 0 (counter)       |
| 3  | `ADDI r17, r0, 0`   | r17 = 0 (DAC input)     |
| 4  | `ADD r17, r17, r11` | Accumulate into r17     |
| 5  | `ADDI r11, r11, 1`  | Increment counter       |
| 6  | `BNE r11, r10, -4`  | Repeat until r11(counter)=43     |
| 7  | `ADD r17, r17, r11` | r17 += r11              |
| 8  | `SUB r17, r17, r11` | r17 -= r11              |
| 9  | `SUB r11, r11, r9`  | r11--   (decrement counter)                |
| 10 | `BNE r11, r9, -4`   | Loop until r11=1        |
| 11 | `SUB r17, r17, r11` | Final adjust            |
| 12 | `BEQ r0, r0, ...`   | Infinite loop           |

---

##  Pre_synth_sim Waveform
<img width="1198" height="667" alt="image" src="https://github.com/user-attachments/assets/42a2750d-6f83-4faf-93ee-f518af93ee11" />

#### For the peak **r17 = 946**:
$$
V_{OUT} = \frac{946}{1023} \times 1.0 = 0.92473\ \text{V}
$$

#### 📊 Example Output Values (VREF = 1.0 V)

| r17 Value | DAC Output Voltage |
|-----------|------------------|
| 946 (peak)| 0.925 V          |


👉 Switch `OUT` format → **Analog Step** in GTKWave for DAC output visualization.


##  Resources

*  [RISC-V Core – Shivani Shah](https://github.com/shivanishah269/risc-v-core)
*  [SoC Fundamentals – Hemanth Kumar](https://github.com/hemanthkumardm/SFAL-VSD-SoC-Journey/blob/main/11.%20Fundamentals%20of%20SoC%20Design/README.md)
*  [VSDBabySoC – Manili](https://github.com/manili/VSDBabySoC)
