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
