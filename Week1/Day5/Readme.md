# Day 5: Optimization in Synthesis

Welcome to Day 5 of the RTL workshop! Today, we will cover optimization in Verilog synthesis, focusing on `if-else` statements, `for` loops, generate blocks, and explore how improper coding can lead to inferred latches. Labs are included for hands-on experience.

---

# 📌 Task 1 – MUX Using `for-generate`
## 📊 Results

* ✅ **RTL and GLS waveforms match** → proves correctness of design.
* ⚡ **`for-generate` loop instantiates MUXes cleanly**, avoiding repetitive manual code.

📷 Simulation:
<img width="1417" height="534" alt="image" src="https://github.com/user-attachments/assets/b716b2cd-f024-4317-98cc-cf34368e2d23" />




📷 Synthesized Netlist:
<img width="1509" height="935" alt="image" src="https://github.com/user-attachments/assets/4b666152-2d5c-4a85-a0eb-b7014f2475e1" />


---

# 📌 Task 2 – DEMUX Using `for-generate`
## 📊 Results

* ✅ **RTL and GLS waveforms match** → proves correctness of design.
* ⚡ **`for-generate` loop instantiates DEMUXes cleanly**, avoiding repetitive manual code.

📷 Simulation:
<img width="1513" height="784" alt="image" src="https://github.com/user-attachments/assets/79e4cc70-19ff-49d4-a8f8-eb734befd516" />

📷 Synthesized Netlist:
<img width="1220" height="653" alt="image" src="https://github.com/user-attachments/assets/3b81411a-93cf-4ada-b127-e5271f54736c" />
<img width="1215" height="762" alt="image" src="https://github.com/user-attachments/assets/beef8337-dfa5-44c4-8476-8cb133f12178" />

# 📌 Task 3 – RIPPLE CARRY ADDER
📷 Simulation:
<img width="1519" height="615" alt="image" src="https://github.com/user-attachments/assets/fdaa7a03-1926-4f8c-8509-c320dc4ea161" />

📷 Synthesized Netlist:
<img width="1222" height="508" alt="image" src="https://github.com/user-attachments/assets/fc138385-b703-439b-8788-a06a044efb80" />
<img width="1220" height="595" alt="image" src="https://github.com/user-attachments/assets/9babc896-bb91-47c3-a98b-ee0f64097d2d" />




