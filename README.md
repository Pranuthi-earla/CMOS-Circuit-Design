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
