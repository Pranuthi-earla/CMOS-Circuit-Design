# CMOS Circuit Design and SPICE Simulations using Sky130
## Module 1: Basics of NMOS Drain current(Id) vs Drain to source voltage(Vds)

##  Introduction to Circuit Design and SPICE simulations
### Lecture 1 : Why do we need SPICE simulations?
 **Circuit Design** : 
All logic gates are constructed by connecting PMOS (p-channel Metal-Oxide-Semiconductor) and NMOS (n-channel Metal-Oxide-Semiconductor) transistors in specific configurations.
The transistor arrangement determines which logic function the gate performs.

#### CMOS Inverter Circuit Structure:
An INVERTER consists of:
- One PMOS transistor connected between power supply (Vdd) and the output
- One NMOS transistor connected between the output and ground (GND)
- Both transistor gates connected together to form the input
<img width="500" height="500" alt="Screenshot 2026-02-17 145251" src="https://github.com/user-attachments/assets/97f2b180-0d17-4ec6-ba49-b463a8ca4d6c" />

#### Characteristic Curves: Describing NMOS Transistor Behavior

The complete behavior of an NMOS transistor can be described by plotting characteristic curves. These curves show the relation between Drain current (Id) vs Drain-to-source voltage (Vds)
- **Multiple curves:** Each curve represents a different gate-to-source voltage (Vgs)
The curves illustrate how much current flows through the transistor under different voltage conditions. By reading the curves, we can predict transistor behavior for any combination of voltages.
<img width="500" height="500" alt="Screenshot 2026-02-17 190619" src="https://github.com/user-attachments/assets/056d2cf1-526b-4eca-9be2-f9522bce8f05" />

PMOS transistor characteristics are the inverted (or complementary) form of NMOS characteristics. 
Extracting Delay Through SPICE Simulation by simulating the transistor and gate behavior in SPICE:
- We apply input signals to the circuit
- We observe how the output responds over time
- We measure how long it takes for the output to transition from one level to another
- This transition time is called the **delay**
The **W/L ratio** is simply the width divided by the length of the transistor. This ratio is the primary parameter designers use to control transistor behavior.
The amount of current a transistor can supply is directly proportional to its W/L ratio:
#### SPICE Simulation: Understanding Device Behavior
SPICE stands for Simulation Program with Integrated Circuit Emphasis. It is a computational tool that simulates how circuits behave by using mathematical models of transistors and other components.
#### SPICE is the Foundation for Modern Chip Design
SPICE simulations are essential because they form the basis for several critical design stages:
Clock Tree Synthesis (CTS)
Physical Design
Cross-talk Analysis
Timing Verification
**Delay** Depends on two factors: input slew and output load
**Example Scenario:**
Assume that clock tree synthesis has been performed for the circuit shown below, where buffers are inserted such that each buffer drives a different capacitive load at its output.
<img width="500" height="500" alt="Screenshot 2026-02-17 223722" src="https://github.com/user-attachments/assets/9a5b58d0-ad9c-4669-8fac-6dae7cf0b593" />

- Buffer Cbuf1 receives an input with slew  of 40 ps
- The output of Cbuf1 must drive a load of 60 fF
**Finding Delay:**
1. Look at the row for 40 ps input slew
2. Look at the column for 60 fF output load
3. Find where they intersect
4. Read the delay value: **9 ps**
The delay tables are derived from circuit-level design and analysis carried out using SPICE simulations. These simulations are used to characterize the timing behavior of CMOS logic circuits under various operating conditions.
-------------------------------------------------------------------------------------------------
### Lecture 2 : Introduction to basic element in Circuit design – NMOS
#### NMOS
An N Channel metal oxide semiconductor transistor is a 4 terminal device, built on a P-Substrate.Conversely pmos transistor iis built on n-type substrate. It has two isolation regions one on the left hand and other on the right side. This isolation regions are actually used to differentiate between two different transistors.n+ diffusion region called as source terminal and drain terminal.
Gate oxide placed over the p substrate
polisilicon or metal gate is placed over the gate oxide and this forms the gate terminal .
## NMOS Transistor Structure Explanation
<img width="500" height="500" alt="image" src="https://github.com/user-attachments/assets/8ce145e7-62ce-4a3b-b694-a3b35178a820" />

This image shows the cross-sectional structure of an NMOS (n-channel Metal-Oxide-Semiconductor) transistor, which is one of the fundamental building blocks of CMOS circuits.

---
## Structure Breakdown

### Physical Components:

#### 1. P-Substrate (P-substrate)
- The base material of the transistor
- Made of p-type (positive-doped) silicon
- Provides the foundation on which the transistor is built
- Connected to terminal B (Body/Bulk)

#### 2. Isolation Region (SiO2)
- Silicon dioxide (SiO2) insulating layers
- Isolates this transistor from neighboring components
- Prevents unwanted current leakage between adjacent transistors
- Located on the sides of the structure

#### 3. Diffusion Regions (n+)
- Two heavily doped n-type regions labeled as n+
- Located on either side of the channel
- Left side: Source (S) - where charge carriers enter
- Right side: Drain (D) - where charge carriers exit
- These are the conducting terminals of the transistor

#### 4. Gate Oxide 
- Thin layer of insulating material between the gate and channel
- Made of silicon dioxide (SiO2)
- Controls the electric field that turns the transistor ON and OFF
- Acts as a capacitor between gate and channel

#### 5. Poly-Si or metal gate
- Polysilicon or metal material placed on top of the gate oxide
- Receives the input signal (Gate terminal - G)
- When voltage is applied here, it creates an electric field in the oxide
- This field controls whether the channel conducts or not

---

## Terminal Definition 

### **4 Terminal Device**

The NMOS transistor has four terminals:

1. **G (Gate)**
   - Voltage applied here controls transistor operation

2. **S (Source)**
   - Acts as the source of charge carriers (electrons)
   - Connected to ground (GND) or lower potential

3. **D (Drain)**
   - Acts as the destination for charge carriers
   - Connected to higher potential or intermediate voltages

4. **B (Body)**
   - Controls the substrate voltage
   - Affects the threshold voltage of the transistor
   ## Quick Summary

| Component | Purpose |
|-----------|---------|
| P-substrate | Base material |
| Gate Oxide | Insulation + control element |
| Poly-Si/Metal Gate | Input signal application |
| n+ Diffusion (Source) | Charge carrier entry point |
| n+ Diffusion (Drain) | Charge carrier exit point |
| SiO2 Isolation | Prevents leakage |
| Channel | Conducting path when gate voltage is applied |
## Threshold Voltage
#### NMOS Transistor – Physical Operation Explanation
The figures illustrate the internal structure and operation of an NMOS transistor fabricated on a p-type substrate with n+ source and drain regions and a gate separated by a thin oxide layer.
#### 1. NMOS Structure (Initial Condition)
<img width="500" height="500" alt="Screenshot 2026-02-17 234828" src="https://github.com/user-attachments/assets/89851dc6-8b04-46bc-a658-8dece1825544" />

- The NMOS is built on a p-type substrate.
- Source (S) and Drain (D) are heavily doped n+ regions.
- The gate (G) is insulated from the substrate by a thin SiO₂ layer.
- The body (B) is connected to ground (GND).
- At this stage : VGS = 0
- No conductive channel exists between source and drain.
- Source–body and drain–body junctions form reverse-biased p–n junctions.
- The transistor is in the OFF state.

#### 2. Application of Positive Gate Voltage (Charge Accumulation)
<img width="500" height="500" alt="Screenshot 2026-02-17 234057" src="https://github.com/user-attachments/assets/14d645fa-b947-4317-bde8-72e4755f7795" />

When a positive voltage is applied to the gate (VGS > 0):
- Positive charge accumulates on the gate electrode.
- An electric field is created across the gate oxide.
- This field repels holes (positive carriers) from the substrate surface.
- Electrons (negative charge carriers) are attracted toward the oxide–substrate interface.
- This results in:Formation of a depletion region below the gate.
- Accumulation of electrons near the surface, as shown in the figure.

#### 3. Channel Formation (Inversion)
<img width="500" height="500" alt="Screenshot 2026-02-17 234118" src="https://github.com/user-attachments/assets/b09fe343-af5f-43f0-9c3f-652090f8e218" />
As VGS increases beyond the threshold voltage (VTH):
- The electron concentration at the surface exceeds the hole concentration.
- The surface region of the p-substrate becomes inverted to n-type.
- A continuous n-type channel is formed between source and drain.
- At this point:
- The NMOS transistor turns ON.
- A conductive path exists between source and drain.

#### 4. Current Flow (ON State)
<img width="500" height="500" alt="Screenshot 2026-02-17 234143" src="https://github.com/user-attachments/assets/fd17d325-584c-44ae-b206-278429c35840" />

- With:VGS > VTH
- Drain at a higher potential than source
- Electrons flow:From source → channel → drain
- Conventional current flows from drain to source.
- The drain current is controlled by:
 - Gate-to-source voltage (VGS)
 - Drain-to-source voltage (VDS)
---------------------------------------------------
### lecture
by increasing the gate voltage we observe that positive charges get repelled and depletion region increases.


