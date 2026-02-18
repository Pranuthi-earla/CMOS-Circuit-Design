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
An NMOS (n-channel metal-oxide-semiconductor) transistor is a key active device in CMOS design. Its main features include:
A p-type substrate that forms the base material.
Two heavily doped n⁺ regions which act as the Source and Drain terminals.
A thin insulating oxide layer between the semiconductor and a gate terminal.
The Gate terminal controls the flow of current between the source and drain when voltage is applied.
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

1. **G (Gate)**- Voltage applied here controls transistor operation

2. **S (Source)** - Acts as the source of charge carriers (electrons), connected to ground (GND) or lower potential

3. **D (Drain)** - Acts as the destination for charge carriers - connected to higher potential or intermediate voltages

4. **B (Body)** - Controls the substrate voltage - affects the threshold voltage of the transistor
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

### Physical Explanation of Operation
#### 1. NMOS Structure (Initial Condition)
When the gate–source voltage (VGS) is 0 V:

- No channel exists between source and drain.

- The NMOS acts like an open switch — no current flows.

- The body (substrate), source, and drain are at the same potential.

<img width="500" height="500" alt="Screenshot 2026-02-17 234828" src="https://github.com/user-attachments/assets/89851dc6-8b04-46bc-a658-8dece1825544" />

#### 2. Application of Positive Gate Voltage (Charge Accumulation)
As Vgs increases positively:

- Negative charges (electrons) accumulate near the channel region under the gate.

- A depletion region forms under the gate as majority carriers are repelled.

<img width="500" height="500" alt="Screenshot 2026-02-17 234118" src="https://github.com/user-attachments/assets/b09fe343-af5f-43f0-9c3f-652090f8e218" />

- When **VGS reaches the threshold voltage (VTH)**, electrons are attracted to the oxide–semiconductor interface, increasing their concentration at the surface.

- The surface region inverts from p-type to n-type (strong inversion), forming a continuous n-type channel between source and drain.

- This channel formation turns the **NMOS transistor ON**, and the threshold voltage (Vt) is the minimum gate voltage required for conduction to begin.

<img width="500" height="500" alt="Screenshot 2026-02-17 234143" src="https://github.com/user-attachments/assets/ce4c5b0e-990d-4969-b40d-d8d9866a12af" />

---------------------------------------------------
### Lecture 3: Strong Inversion

- As the gate voltage increases, holes in the p-substrate are repelled, widening the depletion region beneath the gate.

- At a certain voltage, the surface region inverts from p-type to n-type — this condition is called **strong inversion**, and the corresponding voltage is the **threshold voltage (Vt)**.

- Beyond this point, electrons from the n+ source accumulate to form and widen the conducting channel between source and drain, allowing current flow.

<img width="574" height="287" alt="Screenshot 2026-02-18 164946" src="https://github.com/user-attachments/assets/78ba210f-ef39-4873-941d-912489662a35" />

- When VGS is low, the surface of the p-type substrate has mostly positive carriers (holes), so there is no path for electrons between the source and drain — the transistor remains OFF.

- As VGS increases, the electric field from the gate repels holes away from the surface and creates a depletion region. More gate voltage strengthens this field.

- At a certain VGS, enough electrons are pulled toward the surface so that they outnumber the holes. This flips the surface from p-type to n-type — a condition called strong inversion.

**Forming the Conductive Channel**

<img width="869" height="412" alt="Screenshot 2026-02-18 165322" src="https://github.com/user-attachments/assets/08db6aa6-23b8-4888-bbc7-f2b8a27b5161" />

Once strong inversion occurs:

- A continuous layer of electrons forms under the gate between the source and drain.

- This n-type region acts as a low-resistance path.

- The transistor switches ON and can conduct current when a drain voltage is applied.

**Threshold Voltage (Vt)**

The threshold voltage is defined as the value of VGS at which strong inversion first occurs and a conducting channel starts to form. Below Vt, the transistor remains off; above Vt, the channel begins to support current flow.


