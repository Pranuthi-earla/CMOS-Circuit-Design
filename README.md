# CMOS Circuit Design and SPICE Simulations using Sky130
## Day 1: Basics of NMOS Drain current(Id) vs Drain to source voltage(Vds)

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
### 1.Lecture 2 : Introduction to basic element in Circuit design – NMOS
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
### 2.Lecture 3: Strong Inversion

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

### 3.Lecture 4: Threshold voltage with positive substrate potential

When the substrate-to-source voltage is **VSB = 0**
- The semiconductor surface undergoes **inversion to n-type** when the gate-to-source voltage reaches the **threshold voltage VTO**.
Here, VTO is defined as the threshold voltage at which surface inversion occurs in the absence of any substrate bias.

<img width="410" height="381" alt="Screenshot 2026-02-20 095818" src="https://github.com/user-attachments/assets/2116b3a9-1274-4508-ae18-08ea257ad2fe" />

When a **positive substrate-to-source voltage (VSB > 0)** is applied, the depletion region beneath the gate **widens** as the gate-to-source voltage increases. This occurs because the reverse-biased source–substrate junction attracts **negative charge carriers toward the source**, increasing the depletion charge in the substrate.

<img width="469" height="371" alt="Screenshot 2026-02-20 100004" src="https://github.com/user-attachments/assets/37b480e7-d2a6-42b5-854e-24a168f5dcc9" />

Due to this additional depletion charge caused by the substrate bias, a **higher gate-to-source voltage** is required to achieve strong inversion. As a result, the threshold condition shifts to:

<img width="212" height="63" alt="Screenshot 2026-02-20 104659" src="https://github.com/user-attachments/assets/458401f7-8834-4dad-a829-bcb437907c32" />

where **V₁** represents the extra voltage needed to overcome the body-bias effect, as indicated in the figure.


### Threshold Voltage Expression with Body Effect

The threshold voltage in the presence of substrate bias is given by:

<img width="505" height="88" alt="Screenshot 2026-02-20 102230" src="https://github.com/user-attachments/assets/597e8221-f020-4b3b-899a-18a36fd02c24" />

- Where
   - V_to= Threshold voltage at V_sb=0, and is a function of manufacturing process
   - γ= body effect coefficient, expresses the impact of changes in body bias V_sb(Unit is V^0.5)
   - ϕ_f= Fermi Potential
   
<img width="198" height="116" alt="Screenshot 2026-02-20 102242" src="https://github.com/user-attachments/assets/ab84e277-f06c-4e10-8af4-3f205406e244" />

- Parameters
   - ε_si= relative permittivity of silicon = 11.7
   - N_A= doping concentration
   - q= charge of the electron
   - C_ox= oxide capacitance
- Fermi Potential

   <img width="286" height="125" alt="Screenshot 2026-02-20 102255" src="https://github.com/user-attachments/assets/9064d335-95bc-4ddb-aef2-962b9cbc6f0a" />

- Where
   - n<sub>i</sub>  = intrinsic doping parameter for the substrate
- All these parameters are provided to the SPICE simulation tool, which computes the effective threshold voltage. The calculated VTH accurately represents the electrical behavior of the MOS device under the given biasing conditions.
-----------------------------------------------------------------

## NMOS resistive region and saturation region of operation

### 4.Lecture 1: Resistive region of operation with small drain-source voltage

- On increasing VGS beyond Vt, the channel charge density increases
-	Down in the channel, Qi grows steady with every rise of (Vgs - Vt). That leftover push - called overdrive voltage - brings more free electrons into play. More carriers mean a stronger flow at the drain.
- Starting at 0.45 volts, that's the NMOS threshold voltage. A full volt sits between gate and source. Meanwhile, drain to source sees just 0.05 volts. These values set the operating point. Voltage levels stay fixed like this.
- Beyond the threshold, voltage switches the transistor on - then a path opens between source and drain. That connection appears because gate potential exceeds critical levels.
- A voltage difference appears across the channel when the source sits at ground while the drain holds a positive potential. From one end to the other, the electric push shifts steadily where current moves through. With grounding on one side and elevated voltage opposite, an uneven field forms within the path. Where electrons enter low, they exit higher, tracing a slope in between. This tilt in electrical level runs directly because of how each terminal connects.
- A curve begins on the left, where distance stretches from zero to L - roughly matching effective length. Charge intensity climbs at first, then shifts unevenly across the span. The vertical axis tracks how much charge fills each point along that stretch. Shape dips and rises, not straight, never flat. At every spot, strength ties directly to position. As you move right, the value changes steadily, shaped by physical limits. This picture holds steady throughout the full reach of the channel
- Without VDS, each spot in the channel experiences identical gate overdrive (VGS − Vt).
- Starting at the source, where voltage sits at zero, the channel's internal potential shifts gradually toward the drain. This shift follows the full VDS value by the time it reaches the far end. Voltage here isn't fixed - it stretches across space. At each point x along the path, the level climbs steadily. What begins as nothing ends exactly at the applied drain voltage.
- So the useful boost at spot x turns into (VGS - V(x) - Vt), showing how the charge in the channel fades a bit more from source toward drain.

Measured at fabrication, channel length stands for the set gap from source to drain drawn in layout files. Once production shifts like sideways doping occur, what truly conducts becomes shorter - this real span is effective channel length.

### 5.Lecture 2: Drift Current 

-	Down in the yellow zone, right where the channel sits, the amount of flipped charge at spot x ties closely to how much extra push the gate voltage gives locally.
-	Floating across different points, the channel's potential shifts, making the real gate push at spot x equal VGS - V(x). At each place, a unique blend of voltages shapes how things respond. Where you look changes what drives it - VGS weakened by local drop V(x). Not uniform, the pull adjusts steadily from end to end. What matters at x ties back to that momentary gap between supply and local shift.
-	So the amount of inversion charge at a spot x connects directly to how much extra voltage sits there

-	Think of Cox as how much electric charge the gate oxide can hold for each bit of area. This value shows the strength of the link between gate and channel across the slim insulating layer

-	Electricity moves in different ways. One kind flows steadily without changing direction. The other shifts back and forth many times each second
-	When an electric field is turned on, it pushes charged particles through a material. This movement forms what we call drift current. Instead of random motion, the charges follow a path shaped by voltage across the ends. The flow keeps going as long as the push stays active. Direction matters here - particles head toward the opposite pole. What counts is how strong the pull feels inside. Not every carrier moves at once, but most join when pulled hard enough.
-	Where particles spread out because they’re bunched up in one spot, flow happens. This movement shows up when charges drift toward emptier areas. A shift begins simply: too many on one side, too few on the other. Flow follows imbalance, not push from voltage. It creeps where density drops off. Motion kicks in as crowded zones thin into open space. The current appears wherever unevenness leads
Drift current (Id) = Velocity of charge carriers x Available charge (over the channel width)

### 6.Lecture 3: Drain current model for linear region of operation


-	Take kn = unCox. Here, kn stands for the process transconductance. It shows how well the transistor turns gate voltage into current at the drain. The value depends on carrier mobility and oxide capacitance together.

-	Even though the equation stays quadratic, after more steps it turns into

-	So long as VDS stays at or below (VGS - Vt), the MOSFET works like a resistor.
-	Here, the path between source and drain stays unbroken. Voltage at the gate sets how much current flows through.

### 7.Lecture 4: SPICE conclusion to resistive operation

-	A closer look at how VGS and VDS shape the drain current (ID) begins by testing separate voltage levels. Different combinations reveal shifts in current behavior. One value adjusts while the other holds steady. Changes emerge not just from magnitude, but from their interplay. Each setting alters the flow in distinct ways. What matters is how they jointly influence ID across ranges.
-	When VGS is fixed, the transistor stays in the triode zone provided that VDS stays below the difference between VGS and Vt. What matters here is how much lower VDS sits compared to that threshold gap. As voltage across drain and source drops beneath the gate-to-threshold margin, linear behavior continues uninterrupted. The condition holds only while this imbalance favors smaller VDS values. Once it narrows too far, operation shifts out of triode mode.
-	A single value of VGS is set first. Following that, VDS begins at zero and increases steadily until reaching (VGS − Vt). For each step in this range, the corresponding drain current gets recorded. This process repeats across various gate-to-source voltages. Measurements unfold point by point through incremental shifts in drain voltage.
-	Here, current behaves according to a straight-line model. Simulations help check how current changes with voltage at different gate levels. Each step matches expected patterns without deviation.

### 8.Lecture 5: Pinch Off Region Condition

-	At the drain edge, if (VGS − VDS) exceeds Vt, a conducting channel remains present. So long as that condition holds, carriers continue to form under the gate near the drain
-	Wherever inversion occurs across the channel - from x = 0 at the source to x = L at the drain - a linked conductive route forms between source and drain.
-	Here, the device works within the linear (triode) range, where rising VDS leads to a roughly proportional boost in drain current when VDS stays low. Though small, these voltage shifts clearly shape current flow across the channel.

-	At the point where (VGS − VDS) reaches Vt, inversion at the surface is just maintained near the drain. The gate-to-channel potential closes to the minimum needed right where the channel meets the drain terminal.
-	This condition implies the surface near the drain sits exactly where inversion begins - here, the charge density inverts vanishes entirely. Though subtle, the shift marks a threshold; precisely at that location, carriers cease forming an inverted layer.
-	With the inversion layer vanishing near the drain, the channel stops short of reaching it completely. Such a state earns the name pinch-off.
-	Once pinched off, the channel vanishes near the drain yet current continues. Reaching that narrow spot, electrons move through the depleted zone into the drain, pulled by intense field forces. Consequently, further rises in VDS fail to push the drain current upward steadily

-	Once VDS goes beyond (VGS - Vt), the MOSFET shifts into saturation. Here, the channel at the drain side loses inversion capability, resulting in a pinched-off zone close to the drain terminal.
-	Where the channel's own electric influence weakens the gate effect, what remains of the driving force becomes (VGS − V(x)) at each spot. Because V(x) grows when moving from source to drain, less inverted charge appears near the drain edge.
-	With a continued rise in VDS past (VGS − Vt), the location of pinch-off shifts gradually closer to the source terminal.

### 9.Lecture 6: Drain current model for saturation region of operation
-	If (VGS - VDS) is less than or equal to Vt, the channel breaks down near the drain
-	Once saturated, the channel voltage holds steady near (VGS - Vt). Not like in the linear zone, where changes follow V(x). Here, things stay flat instead of shifting along the path
-	A steady flow sets in when voltage across source and drain stops influencing current. Instead, gate-to-source pressure - threshold level takes control. This happens if we ignore tiny shifts from shrinking paths inside the device
Id = kn/2 (Vgs-Vt)^2

-	Saturation makes the MOSFET act much like a steady current provider. When fully on, it holds current nearly unchanged. Its behavior shifts - now delivering fixed flow regardless of voltage swings. Once saturated, current stays flat even if conditions shift slightly. The device locks into a stable output under these settings.
-	Still, the flow isn’t fully untouched by VDS. When VDS goes up, the empty zone near the drain grows wider.
-	A bit shorter path inside means less resistance. When that path shrinks, more current flows even if voltage stays almost the same. People call this shift by another name - tweaking how far electrons travel changes output just a little
  
### 10.Lecture:1 Basic SPICE setup

Starting off, SPICE relies on set-in-stone models to mirror how transistors behave. Circuit pieces show up just right because of these built-in rules. Instead of guessing, it pulls from fixed templates that match real parts closely.
-	A person gives circuit details using a file called a netlist - this shows each part along with how they link together.
-	Once SPICE runs, it models the circuit behavior while creating visual outputs alongside numerical results.
-	From here, timing delays show up clearly. Cells take shape in how they respond. Because of that, tools like Static Timing Analysis gain stronger backing. Performance checks follow similar paths, shaped by what comes before

-	Starting off, values like VTO, kn′, γ, along with λ - shown in brown up there - are locked once the tech node is set. These don’t shift after that point.
-	Fabrication steps plus how a device behaves shape these values, so folks name them tech constants.
-	Packed inside the SPICE model file that powers simulations, these come straight from the foundry. They show up where the tool reads its rules, shaped by fabrication details baked in ahead of time.
-	Starting from the tech specs fed into the system, the simulation begins once the circuit layout is added alongside them. Not until both inputs are loaded does the engine start mapping how each part behaves. Only then can behavior of components be worked out by the software.
-	Starting at zero, voltage climbs slowly while current gets recorded. Each step in gate voltage paints another line on the graph. Instead of single snapshots, a full picture emerges gradually. With every run, drain current shifts under new pressure. These trails show how channels respond when pushed differently.
SPICE Netlist:

-	A correct syntax structure is needed so the SPICE engine can process the device description. What matters is matching the expected pattern without deviation. Only when formatted properly does recognition happen inside the system. Anything outside that form stays unreadable to the parser.
-	The MOSFET comes into view through how its nodes link up - Drain, Gate, Source, and Bulk shaping the setup. Its behavior leans on the width-to-length ratio of these parts. Voltage supplies set the stage by feeding steady biases. Each piece fits without flash, just function.
-	A look at how the MOSFET behaves electrically comes from its modeled version inside the simulator. Instead of physical parts, it relies on set values that shape responses during operation. What you see drawn is just a representation - what runs underneath follows precise internal rules.
-	MOSFET has four nodes Drain Gate Source Bulk
-	A power supply sets VGS and VDS across the transistor, whereas the body connection often links directly to ground in NMOS setups. The source terminal typically anchors to VSS, letting voltage inputs shape the gate and drain conditions through separate supplies. Grounding the base helps stabilize operation, since that node rarely floats during normal use.
-	A different route is taken by the simulator - it skips mapping the actual shape, relying on number patterns saved in a file to figure out how electricity moves. Instead of copying real-world thickness or width, calculations come from hidden math rules tucked inside that data file.
-	Into the gate, a resistor steps in to block sharp current jumps. Sudden surges meet resistance before reaching critical parts. This small part slows down fast electrical pushes. It stands guard where power first enters. Quick changes get smoothed by its presence. Protection comes quietly through steady opposition.
-	Even though no steady current enters the MOSFET gate, its internal capacitance allows brief surges when turning on or off. Because of this, a sudden spike might appear. That's where the resistor helps - it shields both the delicate oxide layer and whatever powers the switch. Without it, stress builds fast.

### 11-Lecture 2: Circuit description in SPICE syntax

**1. Analyze and Note All Parameter Values**

Before writing a SPICE netlist, identify and record all required parameters, such as:

- Supply voltages

- Resistance values

- Transistor dimensions (Width W and Length L)

- Device model names from the technology file

**2. Defining the Nodes**

- Each circuit component connects between two points, known as nodes.

- Components are always connected from one node to another, never fewer.

- The entire circuit network is formed by elements spanning these nodes.

- A point where multiple components connect is considered a node.

- Every node must be assigned a unique name in the SPICE description.

- Even if a junction seems insignificant, it must still be labeled.

**3. Naming the Nodes**

- Node names are usually alphanumeric (e.g., vdd, n1, in).

- Ground is always represented by node 0 in SPICE.

- Meaningful node names improve circuit readability and debugging.

**4. Defining the SPICE Netlist**

NMOS Transistor Example

The NMOS transistor M1 is connected between the supply and ground with specified channel dimensions.

M1 vdd n1 0 0 nmos W=1.8u L=1.2u
Parameter Description

- M1-MOSFET instance name

- vdd-Drain node

- n1-Gate node

- 0-Source node (ground)

- 0-Body node (ground)

- nmos-Model name (from technology file)

- W=1.8u-Channel width

- L=1.2u-Channel length

**Common MOSFET Terminal Order in SPICE**

Drain – Gate – Source – Body – Model – Dimensions

Complete SPICE Netlist Example

M1  vdd  n1  0  0  nmos  W=1.8u  L=1.2u

R1  in   n1  55

Vdd vdd  0   2.5

Vin in   0   2.5

### 12-Lecture 3: Define technology parameters

The NMOS model is defined inside a technology (tech) file, which contains key physical and electrical parameters such as:

- Threshold voltage (VTH0 / VTO)

- Transconductance parameter (kn′)

- Body effect coefficient (γ)

- Channel length modulation (λ)

- Using these parameters, SPICE predicts transistor behavior under different voltage conditions.

Impact of Technology Scaling

- As technology nodes shrink, accurate parameter extraction becomes increasingly critical.

- Short-channel effects grow stronger and can no longer be neglected.

- Effects that were once minor now significantly influence:

     - Device performance

     - Leakage currents

     - Threshold voltage behavior

- Precision in modeling is no longer optional—it is required due to scaling limits.

- Even small parameter inaccuracies can lead to noticeable deviations in simulation results.

Model Name Matching Requirement

- The model name used in the MOSFET netlist entry must exactly match the name defined in the model declaration.

- SPICE requires character-for-character equivalence:

   - Same spelling

   - Same case

   - No extra spaces or syntax variations

- There is no automatic correction for mismatches or typographical errors.

- Any inconsistency prevents proper model recognition.

Example

M1 vdd n1 0 0 nmos W=1.8u L=1.2u

.MODEL nmos NMOS ( ... )

Consequences of Model Mismatch

- Incorrect transistor type selection (NMOS vs PMOS) or parameter mismatch may:

   - Cause SPICE to reject the netlist

   - Produce incorrect or misleading simulation results

- Simulation integrity silently degrades if parameters drift from intended values.

Common MOSFET Model Parameters

- nmos → Model name (must match the netlist entry)

- NMOS → Device type

- TOX → Oxide thickness

- VTH0 → Zero-bias threshold voltage

- U0 → Carrier mobility

- GAMMA1 → Body effect coefficient

Technology Model Library File

- NMOS and PMOS models are defined inside a model library file, for example:

xxxx_025um_model.mod

- This file contains all technology-specific parameters under a defined library.

- The technology node is typically inferred from the filename rather than explicitly stated.

Linking the Model File to the Netlist

- The technology model file is included in the main netlist using a library reference command.

- This command specifies:

    - The file path

    - The model definitions to be used

- Once included, the circuit netlist becomes linked to the technology parameters.

Device Characterization

- After linking the model file:

   - Sweeping VGS and VDS reveals device characteristics

   - DC analysis exposes transistor behavior across operating regions

- These simulations help validate:

   - Model accuracy

   - Device performance trends

### 13-Lecture 4: First SPICE simulation


**Environment Setup**

1. **Open VirtualBox**

   * Launch the virtual machine configured for SKY130 simulations.


2. **Clone the Workshop Repository**

   ```bash
   git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
   ```
<img width="1511" height="260" alt="image" src="https://github.com/user-attachments/assets/02af6bff-0c39-4539-935c-a1e1b164e67f" />


3. **Verify Project Directory**

   * After cloning, a folder named `sky130CircuitDesignWorkshop` appears.
   * This directory contains all configuration-generated project files.
<img width="914" height="209" alt="Screenshot 2026-02-23 120523" src="https://github.com/user-attachments/assets/a4c74a4c-ae4c-4ba5-95a1-72ec4d44ceda" />


 Navigating the Design Files

4. **Move to the Design Directory**

   ```bash
   cd sky130CircuitDesignWorkshop/design/
   ```



5. **List Contents**

   ```bash
   ls
   ```

6. **Explore the SKY130 Primitive Library**

   ```bash
   cd sky130_fd_pr/
   ls
   ```

<img width="1526" height="334" alt="Screenshot 2026-02-23 120554" src="https://github.com/user-attachments/assets/a41d6a45-1b8c-4309-a2fa-d292db45d4a7" />


7. **Enter the Cells Directory**

   ```bash
   cd cells/
   ```

   Two folders appear:

   * `nfet_01v8` → NMOS devices
   * `pfet_01v8` → PMOS devices


 Understanding Process Corners

8. **Inspect NMOS Libraries**

   ```bash
   cd nfet_01v8/
   ls
   ```
<img width="1510" height="213" alt="image" src="https://github.com/user-attachments/assets/cc2732db-355d-4e40-92a6-c374cc351128" />

   You will find multiple files corresponding to different **process corners**:

   * **TT** → Typical–Typical
   * **FF** → Fast–Fast
   * **SS** → Slow–Slow

   Each file models transistor behavior under different fabrication and electrical variations.

Viewing the NMOS Model File

9. **Open the TT Corner Model**

   ```bash
   less sky130_fd_pr__nfet_01v8___tt.pm3.spice
   ```

<img width="1509" height="120" alt="image" src="https://github.com/user-attachments/assets/3c83abf3-12d8-42c6-9460-2a72c47dae59" />


   * This file contains **all NMOS parameters** for the typical process corner.
   * It defines how the device behaves under nominal conditions.

   <img width="1509" height="296" alt="image" src="https://github.com/user-attachments/assets/5e4a4468-3a75-45bc-a111-a9553aeeca03" />


   **Exit the file** by pressing:

   ```text
   q
   ```

10. **Check Allowed Dimensions**

* Open:

  ```bash
  less sky130_fd_pr__nfet_01v8___tt.corner.spice
   ```

<img width="1511" height="796" alt="image" src="https://github.com/user-attachments/assets/c0033835-7e7e-4ae9-9bb7-b4be1da7c5a6" />

  
* Only specific **W (width)** and **L (length)** values are allowed.
* Using dimensions outside this list may cause simulation failure.

<img width="1511" height="799" alt="image" src="https://github.com/user-attachments/assets/1216e337-58fd-444b-9f9c-b20a98154ed1" />


Model Library Overview

11. **Navigate to the Models Directory**

```bash
cd ../../models
```

12. **Locate the Master Library**

```bash
ls
```

* `sky130.lib.spice` contains **all NMOS and PMOS models** across corners.


<img width="1247" height="235" alt="image" src="https://github.com/user-attachments/assets/34319629-f44b-4322-8d14-42359f6a65ea" />


 Running the Simulation

<img width="1510" height="1006" alt="image" src="https://github.com/user-attachments/assets/dc382b16-aa0d-43b9-9401-7a4a5f379055" />
 

13. **Return to the Design Directory**

```bash
cd ../design
```

14. **Open the Simulation File**

```bash
vim day1_nfet_idvds_L2_W5.spice
```

* This file is preconfigured for repeated simulations.


## Library Linking and Corner Selection

* A **yellow highlighted box** confirms successful inclusion of the SKY130 model library.
* A **yellow indicator** shows the selected process corner.

### Process Corner Codes

* `tt` → Typical–Typical
* `ff` → Fast–Fast
* `ss` → Slow–Slow
* `sf` → Slow–Fast

---

## Netlist Description

```spice
XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=5 l=2
R1  n1 in 55
Vdd Vdd 0 1.8
Vin in  0 1.8
```

### Notes

* NMOS model used: `sky130_fd_pr__nfet_01v8`
* W = 5 µm, L = 2 µm are **selected directly from the corner file**
* Supply voltage = **1.8 V**, matching the device rating


## DC Simulation Command

```spice
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2
```

### Sweep Description

* **VDS**: 0 → 1.8 V in steps of 0.1 V
* **VGS**: 0 → 1.8 V in steps of 0.2 V



## Running ngspice

15. **Execute the Simulation**

```bash
ngspice day1_nfet_idvds_L2_W5.spice
```
<img width="1511" height="716" alt="image" src="https://github.com/user-attachments/assets/a08d3f48-d97d-49a7-9f17-c5b54075ed16" />


16. **Plot Drain Current**

```spice
plot -vddbranch
```


<img width="1565" height="812" alt="Screenshot 2026-02-23 121048" src="https://github.com/user-attachments/assets/4a12e6bb-39b8-4d76-bb1a-259c2549853f" />


* This produces the **Id–Vds curves** for multiple VGS values.



## Observations from the Plot

* When **VGS slightly exceeds Vt**, drain current increases roughly as:
  [
  I_D \propto (V_{GS} - V_t)^2
  ]
* At higher VGS:

  * Mobility degradation
  * Short-channel effects
  * Non-ideal behavior becomes dominant
* The response gradually shifts away from ideal square-law behavior.

<img width="1819" height="902" alt="Screenshot 2026-02-23 121120" src="https://github.com/user-attachments/assets/c5c971ba-f206-40bf-9c7a-69e0c80d309d" />


## Reading Current Values

* Click anywhere on the plot:

  * The terminal displays numerical values
  * The vertical coordinate represents **drain current (Id)** at that operating point

---

### 14-Lecture 5 :SPICE Lab with sky130 models

- Open sky130.lib.spice from the models directory.

- Parameter scaling is defined in the all.spice file.

- Device dimensions must follow the scale specified in all.spice.

Cut-Off Region

- At VGS = 0.4 V, drain current is very small.

- When VGS < Vt, the transistor operates in cut-off.

- In cut-off, the device is mostly OFF with negligible current.

## Day 2: Velocity saturation and basics of CMOS inverter VTC

 ### SPICE simulation for lower nodes and velocity saturation effect

 ### 15-Lecture 1: SPICE simulation for lower nodes

<img width="747" height="555" alt="Screenshot 2026-02-24 151924" src="https://github.com/user-attachments/assets/ffebe4b5-c847-406b-af46-f3987a402421" />


- Initial device has a fixed W/L ratio ≈ 1.5 (W=1.8u, L=1.2u) 

<img width="792" height="482" alt="image" src="https://github.com/user-attachments/assets/65f45183-3fed-4af4-baa5-859d0477058a" />

- Below the blue boundary, MOSFET operates in the linear (resistive) region where drain current increases with voltage.

- Above the blue boundary, device enters saturation; current nearly stabilizes due to channel pinch-off.

- Channel-length modulation causes a slight rise in current in saturation.

Device Dimensions Used

- Case 1: W = 0.375u, L = 0.25u

<img width="330" height="177" alt="Screenshot 2026-02-24 152814" src="https://github.com/user-attachments/assets/a232477d-e684-4365-99b3-3aa41b3fa45b" />

Plot:

<img width="532" height="408" alt="image" src="https://github.com/user-attachments/assets/878f2e32-518e-401e-ad63-2186cc195000" />



Scaling Observation

- When W and L are scaled proportionally, ideal theory predicts similar drain current.

- In practice, drain current changes due to:

   - Mobility degradation
 
   - Channel length variation

   - Parasitic resistance

   - Short-channel effects
   
<img width="902" height="490" alt="image" src="https://github.com/user-attachments/assets/71381295-0b39-4b32-86d1-6d48b5cbb375" />


---

### 16-Lecture 2: Id–Vgs Behavior (Long vs Short Channel)

Long-Channel Device Device dimensions
-	W = 1.8 µm
-	L = 1.2 µm
-	
At VDS = 2.5 V, the drain current shows quadratic dependence on gate voltage.
Observed values

-	VGS = 0 V → ID = 0
-	VGS = 0.5 V → ID ≈ 10 µA
-	VGS = 1 V → ID ≈ 40 µA
  
This behavior follows the saturation-region equation:

- <img width="218" height="75" alt="Screenshot 2026-02-24 161749" src="https://github.com/user-attachments/assets/c3080270-49f2-45ed-8609-61a1c4fab101" />


<img width="428" height="350" alt="image" src="https://github.com/user-attachments/assets/e066881f-5576-4a8a-b40d-6d4cc96d148c" />

SPICE Simulation Results (Long Channel)

<img width="500" height="250" alt="Screenshot 2026-02-24 154535" src="https://github.com/user-attachments/assets/a094950c-ccb4-4888-a1c0-8a84a093ecc3" />


<img width="554" height="448" alt="Screenshot 2026-02-24 160129" src="https://github.com/user-attachments/assets/3ad74cfd-52e4-4675-a3a0-3ba136088934" />


Short-Channel Device
For short-channel devices, Id initially follows the same trend of quadratic but then becomes linear at higher VGS.
Observed behavior

-	VGS = 0.5 V → ID ≈ 10 µA
-	VGS = 1 V → ID ≈ 40 µA
-	Up to this point, behavior appears quadratic
-	At higher VGS, Id shifts toward linear dependence

<img width="446" height="386" alt="image" src="https://github.com/user-attachments/assets/76d2b67d-5be8-4fc3-b2b2-b84231dd5156" />


This deviation is the key difference between short- and long-channel devices due to Velocity Saturation

SPICE Simulation: Id vs Vgs (VDS Constant)
The following plots show Id vs Vgs for different gate voltages while keeping VDS constant.


<img width="500" height="250" alt="Screenshot 2026-02-24 160231" src="https://github.com/user-attachments/assets/9b9717e9-42ef-4f98-818d-c7d76e7c9f0d" />


<img width="522" height="408" alt="image" src="https://github.com/user-attachments/assets/de5c9f8b-de9f-4bc6-bdfd-48e9ef5ecccd" />


### 17-L3 Velocity saturation at lower and higher electric fields



- In short-channel MOSFETs, drain current does not increase rapidly with gate voltage. As Vgs increases, Id rises more slowly and looks almost linear. This happens because carriers cannot move faster beyond a certain limit.

<img width="1332" height="592" alt="image" src="https://github.com/user-attachments/assets/33a2d933-03fd-4680-add0-39f0b617928e" />

- At low electric fields, carrier velocity increases along with the field. When the electric field becomes strong, velocity reaches a maximum value and stops increasing. This limit is called **velocity saturation**.
  
<img width="702" height="432" alt="image" src="https://github.com/user-attachments/assets/a1391c10-15a7-4316-9a75-9cf49767fb6d" />


- As electrons move through the channel, they collide with lattice atoms. These collisions are called scattering. At low fields, scattering is less and electrons accelerate easily. At high fields, electrons gain more energy and cause more lattice vibration. This increases scattering and prevents further acceleration.

<img width="867" height="277" alt="image" src="https://github.com/user-attachments/assets/645c1e42-8e5e-439f-86d9-178fe8d0fe91" />

- Because of frequent scattering, electrons lose momentum and settle at a constant maximum speed. Even if the electric field increases, velocity does not increase much beyond this point.

- For small electric fields (E < Ec), electron velocity increases linearly with the field. When the field reaches the critical value (E ≥ Ec), velocity becomes almost constant at **vsat**. Using E = Ec keeps the velocity model continuous.

- In cutoff, no channel forms for both long- and short-channel devices. In the linear region, Id increases with Vds in both cases. In saturation, long-channel devices follow square-law behavior, while short-channel devices show nearly linear dependence due to velocity saturation.

<img width="657" height="316" alt="image" src="https://github.com/user-attachments/assets/82bb0368-33dd-4d13-86f8-e1d35bcabed4" />

### 18-L4 Velocity saturation drain current model

Gate overdrive voltage is defined as Vgt=Vgs-Vt​ and is used to express drain current under higher gate bias conditions. For small drain voltages, the effect of channel length modulation is usually neglected.

<img width="808" height="427" alt="image" src="https://github.com/user-attachments/assets/b294de6a-3405-4924-8a99-fbe474fbe488" />


As the electric field in the channel increases, carriers reach a maximum velocity. The drain voltage at which this happens is called Vdsat.

Beyond this point, increasing Vds does not significantly increase the drain current due to scattering effects.

In short-channel devices, strong electric fields develop even at lower drain voltages. Because of this, carriers reach their speed limit much earlier compared to long-channel devices.

As technology scales down, fewer carriers are able to reach the drain. This leads to a reduction in saturation current, meaning smaller technology nodes show lower saturation current than longer-channel devices.

<img width="895" height="413" alt="image" src="https://github.com/user-attachments/assets/002559c0-95d1-49a0-9ae9-5d2e28eda0c2" />

### 19-L5 Labs Sky130 Id-Vgs

 Device Setup

* Simulation is performed using the Day-2 design file focusing on the lower nodes
* Device dimensions are fixed at:

  * Channel length (L) = 0.15 µm
  * Channel width (W) = 0.39 µm
* All simulations are run using these dimensions without modification.



Id–Vds Characteristics

* The drain current Id is plotted against drain-source voltage (Vds) for multiple gate-source voltages (Vgs).
* At lower Vgs the curves exhibit a parabolic shape, indicating operation in the linear region.
* As Vgs increases the curves become more linear, showing stronger channel formation and higher conductivity.
* At Vgs = 1.8 V the maximum drain current is approximately 198 µA, obtained by cursor selection on the plot.



 Id–Vgs Characteristics

* For this analysis:

  * **Vds is held constant at 1.8 V**
  * **Vgs is swept from 0 V to 1.8 V** in **0.1 V steps**
* Device dimensions remain unchanged throughout the sweep.
* Only the **gate voltage** varies; all other parameters are fixed.
* The sweep consists of **18 uniform intervals**, ensuring consistent measurement conditions.

* At higher **Vgs**, the **Id–Vgs plot shows a near-linear trend**.
* This behavior is attributed to **short-channel effects**, where current increases proportionally with gate voltage under limited channel control.
* The constant drain voltage reinforces the observed proportionality between **Id and Vgs** at strong inversion.



### 20-L6 Labs Sky130 Vt

The threshold voltage (Vt) is extracted from the **Id–Vgs** characteristic obtained through SPICE simulation.

From the plot, Vt is identified at the point where a small increase in Vgs produces a rapid rise in drain current. A tangent line drawn along the steep region of the curve intersects the **Vgs** axis, indicating the threshold point.

Using this method, the threshold voltage is approximately 0.76 V.


-----------------------------------------------------
## CMOS voltage transfer characteristics (VTC)
### 21-L1 MOSFET as a switch

- When the gate-to-source voltage is below the threshold value, no inversion channel forms. Because there is no conducting path between source and drain, the MOSFET behaves like an open switch. Channel resistance is very high, and current does not flow.

- When the gate-to-source voltage exceeds the threshold, an inversion layer is created. This allows current to flow from source to drain. The MOSFET now behaves like a closed switch, though the resistance is finite and depends on how much ( V_{gs} ) exceeds the threshold.

<img width="584" height="343" alt="image" src="https://github.com/user-attachments/assets/3c174f7e-1664-4bed-a5c9-c6a3fc388dc1" />


 Complementary MOS Operation

Input = Vdd:
- The NMOS turns ON since its gate-to-source voltage is high, while the PMOS turns OFF. The output is pulled toward ground through the NMOS, discharging the load capacitance. As a result, the output becomes logic LOW.

Input = 0 V:
- The NMOS remains OFF, and the PMOS turns ON due to sufficient gate-to-source voltage. The output is connected to the supply through the PMOS, charging the load capacitance. This drives the output to logic HIGH.

<img width="806" height="503" alt="image" src="https://github.com/user-attachments/assets/cd5ce5f5-bf3a-49de-80bb-8e0ccf5463de" />

### 22-Lecture 2: Introduction to standard MOS voltage current parameters

<img width="837" height="450" alt="image" src="https://github.com/user-attachments/assets/f17c02ff-3773-4c71-822e-639d350bd203" />

The CMOS inverter behaves differently depending on whether the input is HIGH or LOW.

- When Vin = Vdd, the NMOS turns ON and the PMOS turns OFF. The output connects to ground through the NMOS, forming a pull-down path.

- When Vin = 0, the NMOS turns OFF and the PMOS turns ON. The output connects to Vdd through the PMOS, forming a pull-up path.

During steady logic states, only one transistor conducts at a time.

During switching, both devices momentarily conduct. By current conservation at the output node, the drain current of PMOS equals the negative of the NMOS drain current (Idsp = −Idsn). The magnitudes are equal, but directions are opposite.

<img width="857" height="438" alt="image" src="https://github.com/user-attachments/assets/6e71e760-bad7-4737-9f4e-7a5a2599c13f" />

### 23-Lecture 3: PMOS/NMOS drain current v/s drain voltage
Obervations:

<img width="887" height="268" alt="Screenshot 2026-02-24 191917" src="https://github.com/user-attachments/assets/92af254f-41cf-4dfe-b2f1-c1755fff8da5" />

Drain current in a MOSFET is controlled by both gate voltage and drain voltage. For NMOS, the key voltages are Vgsn and Vdsn, while for PMOS they are Vgsp and Vdsp.

<img width="312" height="297" alt="image" src="https://github.com/user-attachments/assets/c5a1615d-d6af-4e39-aa1b-e1671ca12eb8" />

In the NMOS device, increasing Vgsn increases the drain current Idsn. At small Vdsn, the device behaves like a resistive switch and current rises almost linearly with voltage. Once Vdsn crosses a certain level, the channel pinches off and the NMOS enters saturation, where current becomes nearly constant.

<img width="278" height="312" alt="image" src="https://github.com/user-attachments/assets/afcd90d3-9d31-4dc2-bff6-6f6cbc54085f" />

For the PMOS, larger negative Vgsp results in higher Idsp. When |Vdsp| is small, the PMOS operates in the resistive region, similar to NMOS behavior. At higher |Vdsp|, the PMOS also enters saturation, causing the drain current to flatten.

Overall, both NMOS and PMOS show linear behavior at low drain voltages and saturation at higher drain voltages, with polarity differences based on device type.

### 24-L4 Step1 – Convert PMOS gate-source-voltage to Vin

- In a CMOS inverter, only Vin and Vout are directly accessible, so voltage transfer and delay analysis rely entirely on these two signals. Internal transistor nodes are not observed directly and are inferred from input–output behavior.

- For static analysis using long-channel devices (Vdd = 2 V), PMOS gate–source voltage is written as Vgsp = Vin − Vdd. By setting Idsp = −Idsn, PMOS and NMOS currents match in magnitude and can be plotted on the same Vin axis, simplifying comparison and analysis.

<img width="892" height="491" alt="image" src="https://github.com/user-attachments/assets/1a793cad-9452-4498-ba3e-090f32d17789" />


### 25-Lecture 5: Step 2 & Step 3 — Expressing Vds in Terms of Vout

To describe inverter behavior using only observable nodes, the internal drain–source voltages are rewritten in terms of **Vout**. Since PMOS drain–source voltage is not directly measurable, it is expressed as
**Vdsp = Vout − Vdd**, allowing all current equations to depend only on **Vin** and **Vout**.
Load curve for PMOS:

<img width="897" height="492" alt="Screenshot 2026-02-24 194332" src="https://github.com/user-attachments/assets/dd68c636-f908-4bee-b43c-01bb798be43c" />

When **Vout = Vdd (2 V)**, the PMOS sees zero drain–source voltage, so its current drops to zero and the load capacitor holds charge. This is a stable HIGH state. When **Vout = 0**, the PMOS experiences maximum |Vds|, the capacitor is fully discharged, and the output is LOW.
Load curve for NMOS:

<img width="612" height="512" alt="image" src="https://github.com/user-attachments/assets/ea84c48a-9700-41c5-b191-bc377b150d50" />
<img width="312" height="212" alt="image" src="https://github.com/user-attachments/assets/c32db7d0-4349-46fd-a25b-2ec676e1ba99" />

With both **Vgs** tied to **Vin** and **Vds** tied to **Vout**, NMOS and PMOS current equations can be rewritten fully in terms of input and output voltages. This enables direct plotting of inverter transfer behavior without referencing hidden internal nodes.

<img width="892" height="302" alt="image" src="https://github.com/user-attachments/assets/5dceea1f-f5fc-45c6-aed5-9eeb6fb8b4c2" />

### 26-Lecture 6: Step-4 —  Merge PMOS – NMOS load curves and plot VTC

The CMOS voltage transfer characteristic (VTC) is obtained by **overlaying NMOS and PMOS load curves** and finding points where their drain currents are equal in magnitude and opposite in direction. Each intersection corresponds to a valid operating point, giving **Vout for a given Vin**. As Vin is swept, these intersections trace the full VTC.

<img width="387" height="262" alt="image" src="https://github.com/user-attachments/assets/4ed5e429-42b6-407a-825d-9647a1e17aeb" />

With **Vdd = 2 V**, both Vin and Vout stay within 0–2 V

* Vin = 0 V → NMOS OFF, PMOS ON → Vout = 2 V
* Vin ≈ 0.5 V → NMOS in saturation, PMOS in linear → Vout slightly below 2 V
* Vin ≈ 1 V → both devices in saturation → Vout around mid-range
* Vin ≈ 1.5 V → NMOS linear, PMOS saturation → Vout < 0.5 V
* Vin = 2 V → NMOS ON, PMOS OFF → Vout = 0 V

By combining both load lines instead of treating devices separately, the inverter switching behavior becomes clear across cutoff, linear, and saturation regions.

<img width="907" height="502" alt="image" src="https://github.com/user-attachments/assets/7a230e14-cd30-46ea-b0c0-cba634c270b8" />

# NgspiceSky130-Day3-CMOS switching threshold and dynamic simulations
## Voltage transfer characteristics – SPICE simulations

### 27-Lecture 1: SPICE deck creation for CMOS inverter

A SPICE deck starts by defining how all components connect in the circuit, followed by specifying the input signal applied to the inverter.
- Component connectivity
<img width="248" height="305" alt="image" src="https://github.com/user-attachments/assets/e19081e7-238a-4af3-b532-61fe1da294c5" />

Next, device models are included to describe transistor behavior, and finally the nodes or signals to be observed during simulation are selected. These steps together form the complete simulation setup.
- Component values
<img width="402" height="322" alt="image" src="https://github.com/user-attachments/assets/719a029f-51d3-49b2-b17a-fb7a488880b4" />

- Identify nodes
<img width="508" height="373" alt="image" src="https://github.com/user-attachments/assets/f47d0770-1771-4d5c-8acf-3372294c6158" />

 - name the nodes 
 
   - M1 out in VDD VSS pmos w=0.375 L=0.25
   - M2 out in 0 0 nmos w=0.375 L=0.25
    
The inverter uses two transistors: **M1 as PMOS** and **M2 as NMOS**. Both devices must have their body terminals properly connected to the substrate to capture body-bias effects on threshold voltage. In this setup, both transistors use the same **W/L ratio** as a reference, even though practical CMOS designs usually size the PMOS wider to compensate for lower hole mobility.

Key parameters used are: **W = 0.375 µm**, **L = 0.25 µm** for both devices, **Cload = 10 fF**, **Vdd = 2.5 V**, and **Vin swept from 0 to 2.5 V**. The supply and dimensions reflect a long-channel process where higher operating voltages are common.

 <img width="375" height="322" alt="image" src="https://github.com/user-attachments/assets/16a1aec5-0190-43de-a505-60c365fd5668" />

### 28-Lecture-2 SPICE simulation for CMOS inverter

Simulation Setup

* The input voltage (Vin) is swept from 0 V to 2.5 V in 0.05 V increments to capture the voltage transfer characteristic (VTC).
* At each step, the corresponding output voltage (Vout) is recorded, ensuring sufficient resolution across the full input range.

* Device parameters are defined through included model files, which contain the required technology details.

* The extracted VTC shows a slight leftward shift

* This shift indicates stronger NMOS pull-down relative to PMOS pull-up, revealing a small but visible strength imbalance in the inverter.


### 29-L3 Labs Sky130 SPICE simulation for CMOS

 VTC Characteristics

* The CMOS inverter consists of one PMOS and one NMOS transistor, with the PMOS W/L ≈ 2.33× NMOS W/L

* Vin is swept from 0 V to 1.8 V in 0.01 V increments, and Vout is recorded at each step to generate the VTC.

* The switching threshold (Vm) is identified where Vin = Vout on the ngspice plot.

* This intersection point clearly marks the inverter’s operating midpoint.

* At a W/L ratio ≈ 2.3 the measured switching voltage is approximately 0.876 V.

* Fine cursor movement on the plot is achieved by pressing and holding the right mouse button


Transient Analysis

* Transient behavior is analyzed using the Day-3 transient SPICE file

* Input is a pulse signal transitioning between 0 V and 1 V with:

  * Rise time = 0.1 ns
  * Fall time = 0.1 ns
  * Pulse width = 2 ns
  * Period = 4 ns

* The reference point for delay measurement is 50% of output voltage (≈ 0.9 V)

* Delay is measured as the time difference between the input transition and the output reaching the mid-level.
  
 Delay Results

* Rise delay =  2.482 - 2.15 = 0.333ns

* Fall delay =  4.334 - 4.050 = 0.285ns

-------------------------------------------------------------------------------

## Static behavior evaluation – CMOS inverter robustness – Switching Threshold

### 30-L1 Switching Threshold, Vm

-	Changing PMOS and NMOS W/L ratios does not alter the overall voltage transfer curve shape; only the switching point shifts due to drive-strength imbalance between the transistors.
-	Despite sizing variations, the CMOS inverter preserves full output swing, sharp transition, and stable saturation regions, showing strong robustness to design changes.
-	Initially, both Wn/Ln and Wp/Lp are set to 1.5, then uniformly scaled by a factor of 1.5 to reach a value of 3.75 for both transistors.
-	In the next sizing step, widths are adjusted independently: Wn becomes 0.375 µm and Wp becomes 0.9375 µm, while both channel lengths remain fixed at 0.25 µm.
-	The switching threshold voltage (Vm) occurs when the input voltage equals the output voltage, defining the exact point where the inverter changes logic state.
-	Vm is identified graphically at the intersection of the voltage transfer curve with the 45° line (Vin = Vout), marking the midpoint of the transition region.
-	At Vm, both NMOS and PMOS operate in saturation, conducting simultaneously and creating a temporary direct path between VDD and GND.
-	From the plots, Vm is approximately 0.9 V when Wn/Ln equals Wp/Lp, and shifts toward 1.2 V when the PMOS is made wider, confirming sizing-dependent threshold movement.

### 31-Lecture 2: Analytical expression of Vm as a function of (W/L)n and (W/L)p

-	Vm depends directly on the ratio ((Wp/Lp)/(Wn/Ln)), which sets the relative drive strength of PMOS and NMOS.
-	Increasing PMOS width shifts Vm upward, moving it closer to VDD.
-	Increasing NMOS width shifts Vm downward, moving it closer to GND.
-	When PMOS and NMOS strengths are balanced, Vm settles near (VDD/2).


### 32-Lecture 3: Analytical expression of (W/L)n and (W/L)p as a function of Vm
-	In the switching-point equation, all parameters except Vm are fixed by the technology model (k′n, k′p, Vtn, |Vtp|, VDD), making Vm the only variable that changes with sizing.
-	Once Vm is obtained from the VTC plot, the required ratio ((W/L)_p / (W/L)_n) can be directly calculated from the equation.
-	The switching point represents the balance of drive strengths between PMOS and NMOS; the transition occurs when one device begins to dominate the other.
-	This tipping point is fully determined by the relative strength ratio, clearly marking where control shifts from one transistor to the other.
-	When Vm is close to (VDD/2), PMOS and NMOS have equal strength.
-	When Vm shifts toward 0 V, NMOS drive strength dominates.
-	When Vm shifts toward VDD, PMOS drive strength dominates.

### 33-Lecture 4: Static and dynamic simulation of CMOS inverter

-	The behavior of a CMOS inverter varies with different PMOS-to-NMOS size ratios ((Wp/Lp):(Wn/Ln)).
-	Multiple sizing cases are analyzed by progressively changing the (Wp/Lp) to (Wn/Ln) ratio to observe inverter performance trends.
Case 1: (Wp/Lp = Wn/Ln = 0.7,\mu m / 1.5,\mu m)
DC Analysis
-	The switching threshold voltage is approximately 0.83 V, indicating balanced PMOS and NMOS strengths.
Transient Analysis
-	For the rising edge, the delay difference is 0.381 ns, calculated from (2.533,ns - 2.152,ns), showing a later output transition.
-	For the falling edge, the delay is 0.1597 ns, obtained from (4.2104,ns - 4.0507,ns), indicating a faster discharge path.


### 34-L5 Static and dynamic simulation of CMOS inverter with increased PMOS width

Case 2: (Wp/Lp = 2 \times (Wn/Ln))
Parameters
-	(Wn/Ln = 0.7,\mu m / 0.15,\mu m)
-	(Wp/Lp = 1.4,\mu m / 0.15,\mu m)
DC Analysis
-	Switching threshold voltage ≈ 0.87 V
Transient Analysis
-	Rising edge delay increases by 0.2 ns (2.35 ns − 2.15 ns).
-	Falling edge delay increases by 0.1602 ns (4.2127 ns − 4.0525 ns).

Case 3: (Wp/Lp = 3 \times (Wn/Ln))
Parameters
-	(Wn/Ln = 0.7,\mu m / 0.15,\mu m)-
-	(Wp/Lp = 1.4,\mu m / 0.15,\mu m)
DC Analysis
-	Switching threshold voltage ≈ 0.89 V
Transient Analysis
-	Rising edge delay is 0.16 ns (2.30 ns − 2.14 ns).
-	Falling edge delay increases slightly by 0.169 ns (4.22 ns − 4.051 ns).
-	Increasing PMOS width shifts the switching point Vm upward due to stronger pull-up action relative to NMOS.
-	A stronger PMOS requires higher input voltage to balance NMOS current, moving Vm closer to VDD.
-	Larger PMOS width reduces rise delay by supplying more charging current, allowing the load capacitance to reach high voltage faster.


### 35-L6 Applications of CMOS inverter in clock network and STA

-	During fabrication, small variations in transistor W/L ratios occur, but CMOS inverters tolerate these well, keeping the switching point largely stable.
-	Vm remains consistent under minor variations and shifts noticeably only when there is a strong imbalance between PMOS and NMOS strengths.
-	When PMOS width is set to about twice NMOS width, rise and fall times closely match, compensating for lower hole mobility in PMOS devices.
-	Matching rise and fall delays improves timing consistency, reduces duty-cycle distortion, and ensures symmetric signal transitions across loads.
-	This balanced behavior highlights the inherent symmetry of CMOS inverters, which supports their reliability and scalability in large designs.
-	Clock inverters and buffers are primarily designed to achieve balanced propagation delays, where (tpHL \approx tpLH).
-	Timing mismatches cause asymmetric clock waveforms, leading to uneven pulse widths and reduced timing margins at storage elements.
-	In buffer chains, small rise/fall mismatches accumulate stage by stage, increasing clock skew and complicating timing closure.
-	If rise delay (tpLH) becomes the critical timing limiter, optimization focuses specifically on improving the rising transition.
-	Increasing PMOS width selectively reduces rise delay, ensuring the clock edge arrives early enough to meet setup timing without unnecessary redesign.

---
## Day4- CMOS Noise Margin robustness evaluation

## Static behaviour evaluation-CMOS inverter robustness-Noise Margin

### 36-L1 Introduction to noise margin

-	As supply voltages scale down and interconnects pack closer, signals interfere more easily due to reduced spacing and stronger coupling. Noise margins quantify how much disturbance a circuit can tolerate before failing.
-	A digital circuit can tolerate a certain amount of noise added to a valid signal without malfunctioning. This tolerance limit defines the noise margin and separates correct operation from erroneous switching.
-	In an ideal inverter, the transition between logic levels is perfectly sharp, switching instantaneously at a single threshold with no gradual transition region.
-	In real CMOS circuits, parasitic resistance and capacitance slow voltage transitions, producing a gradual slope in the voltage transfer curve near the switching point.
-	Around the switching voltage (Vm), limited gain makes the inverter highly sensitive to input noise, where small voltage variations can cause large output changes.

Voltage Margin Definitions
-	VIL (Input Low Voltage):
Any input voltage between 0 and VIL is interpreted as logic 0. Voltages below this limit are reliably recognized as low.
-	VIH (Input High Voltage):
Any input voltage between VIH and VDD is interpreted as logic 1, defining the minimum voltage required for a valid high input.
-	VOL (Output Low Voltage):
Output voltages between 0 and VOL represent logic 0, ensuring a clear low-level output range for reliable signal interpretation.

### 37-Lecture 2: Noise Margin voltage parameters

-	Due to real-world non-idealities in CMOS inverters, the voltage transfer curve is not vertical; therefore, logic levels occupy voltage ranges rather than single points.
-	A low input voltage produces a high output voltage, while an input between VIH and VDD results in an output between 0 and VOL.
-	The region between VIL and VIH is the transition zone, where both NMOS and PMOS conduct simultaneously, making the output unstable and unsuitable for logic interpretation.
-	In this transition region, overlapping conduction prevents the signal from being classified as a valid logic high or low.
-	The voltage hierarchy follows: VOL < VIL < VIH < VOH < VDD, defining safe operating limits for digital signals.
-	VIL and VIH are identified at points where the slope of the voltage transfer curve equals –1, marking the onset of noise vulnerability.
-	In the transition region, the curve’s slope magnitude exceeds unity, amplifying signal changes and enabling switching.
-	Outside this region, the slope drops below unity, stabilizing output levels and preventing noise-induced state changes.


### 38-Lecture 3: Noise Margin Equation and Summary

- **Noise Margin Low (NML):**
  Voltages within this range are interpreted as logic 0. Even low-amplitude signals remain meaningful and are correctly recognized despite nearby noise.

- **Noise Margin High (NMH):**
  Voltages within this range are interpreted as logic 1. Signals above this threshold are reliably identified as high and remain immune to noise interference.

- When voltages move above **VIL** or below **VIH**, they enter an undefined transition region where signals are neither clearly low nor high, resulting in uncertain behavior.

- Voltages outside the defined **NML** and **NMH** limits fall beyond safe operating bounds, increasing the risk of incorrect switching and malfunction.
<img width="675" height="498" alt="image" src="https://github.com/user-attachments/assets/f8f737a1-7c94-435c-8438-e55106772094" />


Noise Impact Scenarios

- Small voltage glitches, often caused by crosstalk or capacitive coupling from nearby wires, introduce brief disturbances on signal lines.

- If a glitch occurs while the signal is at logic 0 but remains within the **NML** range, the signal is still correctly interpreted as LOW and operation continues normally.

- If noise pushes the voltage into the undefined region between **VIL** and **VIH**, the inverter may behave unpredictably, leading to unreliable output.

- If a noise spike drives the voltage into the **NMH** region, false triggering can occur, causing unintended logic transitions and timing failures.
<img width="592" height="317" alt="image" src="https://github.com/user-attachments/assets/f270891c-73a8-4d6c-ad5e-929348df011d" />


### 39-Lecture 4: Noise margin variation with respect to PMOS width

-	Changing the PMOS-to-NMOS width ratio shifts the voltage transfer curve, revealing how noise tolerance depends on transistor sizing balance.
-	Key voltage points (VIL, VIH, VOL, VOH) are identified where the slope of the VTC equals –1, indicating the limits of reliable logic recognition.
-	From these slope = –1 points, noise margins are calculated as
NMH = VOH − VIH and NML = VIL − VOL.

Case 1: (Wp/Lp = Wn/Ln)
<img width="868" height="376" alt="image" src="https://github.com/user-attachments/assets/bfaa4a03-0244-4a4e-9709-3fd210b43703" />

-	Higher noise margins improve inverter reliability by keeping logic levels stable despite interference and glitches.

Case 2: (Wp/Lp = 2(Wn/Ln))
<img width="862" height="362" alt="image" src="https://github.com/user-attachments/assets/5164a5b4-278a-4ae7-9b0c-ecc6a8f9666c" />

-	A wider PMOS lowers pull-up resistance, strengthening the connection to VDD and improving the ability to restore logic HIGH.
-	Reduced resistance allows faster recovery from leakage or noise, keeping the output node closer to its intended level.
-	As a result, VOH remains closer to VDD, increasing NMH and improving high-level noise immunity.

Case 3: (Wp/Lp = 3(Wn/Ln))
<img width="857" height="377" alt="image" src="https://github.com/user-attachments/assets/04450d31-96a7-4254-9ab3-e84a11975a54" />

   -	Increasing PMOS width further strengthens the pull-up path, slightly raising VOH and NMH.
   -	NMOS dimensions remain unchanged, so VOL and NML show minimal variation.
   -	Noise tolerance improves mainly for logic HIGH, while logic LOW stability remains nearly constant.

Case 4: (Wp/Lp = 4(Wn/Ln))
<img width="865" height="362" alt="image" src="https://github.com/user-attachments/assets/090a7be8-412b-4325-b641-93a09dcb5c7f" />

   -	Beyond a certain width, PMOS scaling faces physical limits such as increased area, capacitance, and power consumption.
   -	NMH begins to saturate because VOH approaches VDD, reducing the benefit of additional width.

Case 5: (Wp/Lp = 5(Wn/Ln))
<img width="856" height="351" alt="image" src="https://github.com/user-attachments/assets/a5f2a760-fd46-434c-8735-a861a2355dca" />

   -	Noise margins show little difference compared to the 4× case.
   -	Once the PMOS exceeds a threshold size, further widening yields diminishing returns while increasing parasitic effects.

Impact of Process Variations

<img width="522" height="187" alt="image" src="https://github.com/user-attachments/assets/9759073f-b786-480d-b1f8-f86117626926" />

   -	Small fabrication-induced variations in transistor dimensions cause minimal change in NMH, NML, and Vm.
   -	Despite imperfect manufacturing, inverter switching behavior and noise tolerance remain stable.
   -	CMOS inverters therefore exhibit strong robustness to real-world process variations.

Design Perspective
Digital Design

<img width="497" height="412" alt="image" src="https://github.com/user-attachments/assets/c2690f6d-592a-496c-afcb-adbdff093f3c" />

   -	Stable operation occurs when inputs remain near 0 V or VDD, avoiding the transition region.
	Noise margins ensure reliable logic levels and prevent unintended switching.
Analog Design

<img width="501" height="413" alt="image" src="https://github.com/user-attachments/assets/377228f5-f545-477e-9e06-c17428bc1633" />

   -	Operation occurs in the steep central region of the VTC, where gain is highest.
   -	Small input changes produce amplified output variations.
   -	Outputs follow continuous values along the transfer curve rather than discrete logic states.


### 40-Lecture 5: Sky130 Noise margin labs

 Noise Margin Plotting

* The PMOS-to-NMOS width-to-length ratio is set to **2.77**, while Vin is swept from 0 V to 1.8 V in 0.01 V increments.

* VIL and VIH are identified at points where the slope of the VTC equals -1 using the horizontal axis.


   
```bash   
Spice deck to find the noise margin of a cmos inverter circuit for (wp/lp=1/0.15) and (wn/ln=0.36/0.15)

*Model description
.param temp = 27

*Netlist description

XM1 out in Vdd Vdd sky130_fd_pr__pfet_01v8 W =1 L = 0.15
XM1 out in 0 0 sky130_fd_pr__nfet_01v8 W =0.36 L = 0.15 
cload out 0 50fF

Vdd Vdd 0 1.8V
Vin in 0 1.8V

*include model file
.lib "../sky130_fd_pr/models/sky130.lib.spice" tt

*simulation commands
.op
.dc Vin 0 1.8V 0.01

*interactive interpretor commandw
.control
run
display
setplot dc1
plot out vs in
.endc
.end
```
   


* Corresponding VOH and VOL values are obtained from the vertical axis at these crossover points.
  
  <img width="802" height="455" alt="image" src="https://github.com/user-attachments/assets/8a57d988-69e5-4bcd-8b6d-a6eefba0ff9c" />


 Noise Margin Calculation

* Noise Margin High (NMH)
  NMH= VOH - VIH = 0.72

* Noise Margin Low (NML
  NML = VIL - VOL = 0.67807



# Day 5 - CMOS power supply and device variation robustness evaluation
## Static behavior evaluation – CMOS inverter robustness – Power supply variation

### 41-L1 Smart SPICE simulation for power supply variations


- As technology scales, reliability analysis increasingly depends on supply voltage scaling, where reducing **VDD** lowers energy consumption and electric-field stress.

- Lower supply voltage reduces noise margins and increases sensitivity in switching behavior, making inverter operation more vulnerable during transitions due to limited voltage headroom.

- Even under reduced **VDD**, CMOS inverters must preserve correct logic operation, stable switching points, and sufficient gain to maintain functional reliability.

<img width="811" height="472" alt="image" src="https://github.com/user-attachments/assets/26292472-ff24-4acb-8122-c71eac7bcb87" />

- A DC analysis is performed on the CMOS inverter while progressively reducing the supply voltage.

- VDD starts at 2.5 V and is decreased in 0.5 V steps repeated over five iterations.

- For each supply voltage, Vin is swept from 0 V to 2.5 V in 0.01 V increments, generating a complete voltage transfer characteristic (VTC).

- Supply voltage changes are applied using the `.alter VDD` command, allowing reuse of the same circuit without redesign.

- Each sweep records operating points across the transition region, updating measurements at every voltage level.

<img width="505" height="486" alt="image" src="https://github.com/user-attachments/assets/4ab1a802-50e5-4888-811f-f448d675ca0f" />



### 42-L2:Advantages and disadvantages using low supply voltage


-	A CMOS inverter can operate at low supply voltages (down to 0.5 V) while still showing a valid voltage transfer curve, though the output swing reduces and switching becomes less sharp.
-	Inverter performance under changing supply voltage is commonly evaluated using gain, which reflects how strongly the output responds to input variations.
-	As VDD decreases, maximum gain trends downward overall, leading to reduced signal amplification and smaller noise margins.
<p align="center">
  <img src="https://github.com/user-attachments/assets/ac4d51f2-5901-47cc-949e-d66ef75d6bb6" width="48%" />
  <img src="https://github.com/user-attachments/assets/8ed4c794-bb83-4bf5-97b2-640ddcefa372" width="48%" />
</p>


<p align="center">
  <img src="https://github.com/user-attachments/assets/d53826d7-a4bd-4c81-ac42-b6fbfff48ccd" width="48%" />
  <img src="https://github.com/user-attachments/assets/50596c87-8755-487a-a444-1dc6c5ef2efc" width="48%" />
</p>


Advantages of Lower Supply Voltage
-	Gain increases by roughly 50%.
-	Energy consumption reduces significantly (≈ 90% reduction).

Disadvantages of Lower Supply Voltage
- Performance impact



### 43-L3: SKY130 Supply Variation Testing

- The supply voltage variation is defined starting from 1.8 V, decreasing in steps of 0.2 V.

- A total of six iterations are performed, allowing a gradual and controlled reduction in VDD.
<img width="1500" height="633" alt="Screenshot 2026-02-26 163729" src="https://github.com/user-attachments/assets/f1729dd6-4b16-4e21-960b-cd3bfd00f9f4" />

<img width="1386" height="791" alt="image" src="https://github.com/user-attachments/assets/a323df26-d118-4541-ad87-6255343a12bc" />

Gain Calculation

- At VDD = 1.8 V
  |Gain| = 7.6229

- At VDD = 0.8 V
  |Gain| = 9.3844


- The increase in gain magnitude with reduced supply voltage highlights the impact of **VDD scaling** on inverter amplification behavior.

## Static behaviour evaluation-CMOS inverter robustness- Device variation

### 44-L1 Sources of variation – Etching process

<img width="872" height="282" alt="image" src="https://github.com/user-attachments/assets/0fa6821e-79f6-47d7-a3dd-1ccdc26a2518" />

* In a CMOS inverter, the channel length (L is defined by the polysilicon gate length, while the channel width (W is set by the overlap of polysilicon over the diffusion region.
<img width="902" height="466" alt="image" src="https://github.com/user-attachments/assets/17331ef1-5e27-4204-979f-6c4c03888271" />

* During fabrication, small variations arise due to lithography and etching imperfections, since manufacturing processes are not perfectly repeatable.
<img width="891" height="472" alt="image" src="https://github.com/user-attachments/assets/b88b1f59-7749-48d0-bbf2-4b797c2e8ba6" />

* These variations cause slight changes in effective W and L for PMOS and NMOS devices, leading to minor performance differences.

* Changes in device dimensions affect threshold voltage drive strength and propagation delay making robustness to process variation a key design requirement.
<img width="902" height="466" alt="image" src="https://github.com/user-attachments/assets/17331ef1-5e27-4204-979f-6c4c03888271" />


* Gate length measured through the polysilicon feature defines the technology node (e.g., 180 nm, 65 nm) and serves as the primary scaling metric.

* As technology nodes shrink, minimum gate length reduces, enabling higher device density and faster switching speeds.


<img width="583" height="325" alt="image" src="https://github.com/user-attachments/assets/526ab5e4-8e21-4a20-88a1-fef1f39c2b17" />


* Even with identical layouts, small process variations in length, width, and threshold voltage appear across inverters in a chain.

* Local fabrication differences such as edge roughness or impurity fluctuations cause each inverter to behave slightly differently.

* These variations lead to small changes in delay, switching point, and drain current at each stage.

* Across an inverter chain, such differences accumulate, impacting overall timing behavior and performance predictability.



## 45-Lecture 2: Sources of Variation – Oxide Thickness

* Oxide thickness (tox) is a major source of process variation in CMOS devices.
<img width="885" height="392" alt="image" src="https://github.com/user-attachments/assets/07a374a5-b867-45cd-ae92-2731b2ed6fab" />

* A thinner oxide increases Cox, reducing effective channel resistance and increasing drive current.

* A thicker oxide decreases Cox, increasing effective resistance and weakening the drive current.

* In a CMOS inverter cross-section, the gate oxide lies directly beneath the polysilicon (or metal) gate.

* In practice, oxide thickness is not perfectly uniform, leading to device-to-device variation.

 Impact on Inverter Chains
<img width="823" height="461" alt="image" src="https://github.com/user-attachments/assets/09edc3eb-0ca1-4768-950e-8e7669872107" />

* Across an inverter chain, small variations in oxide thickness cause incremental shifts in delay and threshold behavior.

* These small variations accumulate stage by stage, resulting in noticeable timing differences further down the chain.

* Inverters located in the middle of a chain experience more uniform surroundings, allowing some variations to average out.

* Edge inverters face more diverse layout conditions and neighboring structures, leading to higher variability.

* Despite these effects, CMOS inverters maintain correct logic operation, demonstrating strong resilience to oxide-thickness variation.

* Changes in tox directly affect the drain current, influencing overall switching performance.

<img width="721" height="393" alt="image" src="https://github.com/user-attachments/assets/5e4f7722-3bd4-4456-9652-453ca607016e" />

## 46-L3 Smart SPICE simulation for device variations

<img width="855" height="500" alt="image" src="https://github.com/user-attachments/assets/54dd9c16-c67b-43e1-9c2e-d21d0f499e8f" />


SPICE Simulation: Device Behavior Under Variation

* SPICE simulations are used to study inverter behavior under extreme parameter variations.

* Even with large, deliberate shifts in device parameters, inverter performance remains stable, demonstrating strong resilience.

* Despite harsh operating conditions and drifting values, functional behavior stays consistent and predictable.



 Effect of Transistor Width Variation

<img width="530" height="415" alt="image" src="https://github.com/user-attachments/assets/cd97b9ff-5e94-4e1b-8746-2e7d3da29501" />

* Increasing PMOS width lowers its resistance, strengthening pull-up behavior and improving conduction.

* When PMOS becomes weaker, a wider NMOS dominates due to its lower resistance, shifting current flow to the pull-down path.

* In both cases, increasing channel width reduces resistance, regardless of transistor type.

* Overall performance depends not just on size, but on how width influences conductivity and current flow.


## 47-L4 Conclusion

* Clear trends emerge when inverter behavior is examined across parameter variations, revealing consistent and predictable patterns.
<img width="711" height="490" alt="image" src="https://github.com/user-attachments/assets/b0a8cb20-51b5-4279-9ee3-858bc2018d8d" />

* The switching threshold Vm shifts rightward when PMOS strength increases and leftward when NMOS strength dominates.

* The direction of Vm movement directly indicates which transistor controls the inverter: PMOS dominance raises Vm, while NMOS dominance lowers it.
<img width="733" height="496" alt="image" src="https://github.com/user-attachments/assets/59e4d758-10f7-420d-b530-3d939c2ec22b" />

* Despite extreme variations, noise margins change very little indicating stable inverter operation.
<img width="547" height="472" alt="image" src="https://github.com/user-attachments/assets/84112fbd-41ae-4fff-abe4-f00f361db5a8" />

* Overall output behavior remains consistent across scenarios, demonstrating strong robustness to device strength imbalance.


## 48-L5 Sky130 Device Variation Labs

* SPICE simulations are performed individually for each device variation, with one configuration tested at a time under modified conditions.
<img width="466" height="602" alt="image" src="https://github.com/user-attachments/assets/fd6363b3-1bcd-477c-bad5-a900e0401d31" />

* Results from each run are compared to identify trends and relate behavior directly to the corresponding parameter changes.

* Simulations are repeated only when required, keeping the analysis efficient and controlled.
<img width="586" height="606" alt="image" src="https://github.com/user-attachments/assets/cb764210-0ab4-494f-8f57-485a812ff538" />

* Observations show a significantly wider PMOS compared to NMOS, indicating PMOS dominance.
 
<img width="1547" height="786" alt="image" src="https://github.com/user-attachments/assets/5a6fdbda-61a4-40f6-af52-8de950bc54b1" />

* This strength imbalance shifts the switching threshold Vm toward higher voltages (rightward), consistent with a stronger pull-up device.



