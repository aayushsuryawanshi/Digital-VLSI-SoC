# Digital-VLSI-SoC
RTL to GDSII Implementation of RISC-V (picorv32a) using Sky130 PDK
This repository documents an end-to-end RTL-to-GDSII physical design flow for the picorv32a RISC-V core using the Sky130 open-source PDK and industry-relevant open-source EDA tools. It covers all key stages including synthesis, floorplanning, placement, CTS, timing closure, PDN design, routing, parasitic extraction, and final GDSII generation.
The focus of this project was to understand, debug, and optimize each stage of the physical design flow, with successful integration of a custom standard cell.
#
# Toolchain & Environment
- **PDK:** Sky130 (sky130A)
- **Design:** picorv32a RISC-V Core
- **Flow Manager:** OpenLANE
- **Synthesis:** Yosys + ABC
- **STA:** OpenSTA
- **CTS:** TritonCTS
- **Routing:** TritonRoute
- **Layout & GDS:** Magic
- **Parasitic Extraction:** SPEF Extractor
- **SPICE Simulation:** Ngspice
- **OS:** Ubuntu Linux
#

## Repository Structure

The repository is organized in a **day-wise manner** to reflect a real-world physical design learning and execution flow:

- **Day 1:** Open-source VLSI flow setup and synthesis  
- **Day 2:** Floorplanning, placement, and standard cell alignment  
- **Day 3:** Custom standard cell design and library integration  
- **Day 4:** Timing analysis, ECOs, and clock tree synthesis (CTS)  
- **Day 5:** PDN design, routing, parasitic extraction, and GDSII generation  

### Each Day Includes

- Task-wise documentation  
- Tool-specific observations  
- Timing and physical design insights  
- Screenshots for verification  
## Day 1 – RTL Synthesis & Flow Initialization

On Day 1, the OpenLANE environment was initialized and the **picorv32a** RTL design was synthesized.

### Key Tasks Completed

- Loaded RTL and verified design hierarchy  
- Performed logic synthesis using **Yosys**  
- Executed technology mapping with **ABC** using Sky130 standard cells  
- Analyzed synthesis reports, including:
  - Cell utilization  
  - Area metrics  
  - Initial timing slack  

This stage converts the RTL design into a **gate-level netlist**, establishing the foundation for subsequent physical design stages.
## Day 2 – Floorplanning, Placement & Track Alignment

Day 2 focused on preparing the design for routing and power delivery.

### Key Tasks Completed

- Defined die area and core utilization targets  
- Generated standard cell rows aligned to routing tracks  
- Performed standard cell placement and legalization  
- Verified row orientation, spacing, and pin accessibility  
- Analyzed placement density and routing congestion  

This stage ensures the design is **physically feasible** and well-prepared for clock tree synthesis and signal routing.
## Day 3 – Custom Standard Cell Design & Library Integration

Day 3 focused on designing and integrating a custom inverter (**sky130_vsdinv**) into the OpenLANE flow.

### Key Tasks Completed

- Designed the inverter schematic and simulated functionality using **Ngspice**  
- Created the standard cell layout in **Magic** following Sky130 DRC rules  
- Aligned the layout to routing tracks for placement compatibility  
- Extracted **LEF** for physical abstraction  
- Verified pin placement, cell boundaries, and routing obstructions  
- Studied timing libraries (`.lib`) to understand:
  - Delay models  
  - Slew characteristics  
  - Output capacitance  
- Integrated the custom standard cell into synthesis and STA flows  

This step bridges **circuit design, layout, and timing modeling**, providing end-to-end standard cell integration experience.
## Day 4 – Timing Closure & Clock Tree Synthesis (CTS)

Day 4 focused on timing optimization and clock distribution.

### Key Tasks Completed

- Performed pre-layout static timing analysis (STA) using **OpenSTA**  
- Identified setup and hold timing violations  
- Tuned synthesis parameters to reduce negative slack  
- Applied manual timing ECOs by upsizing critical cells  
- Verified timing improvements through updated STA reports  
- Executed clock tree synthesis using **TritonCTS**  
- Evaluated clock quality metrics, including:
  - Clock skew  
  - Clock latency  
  - Hold slack  
- Analyzed the impact of larger CTS buffers on:
  - Slew  
  - Skew  
  - Area  
  - Power  

This stage transitions the design from **ideal clock assumptions to real clock behavior**, a critical milestone toward physical sign-off.
## Day 5 – PDN, Routing, Parasitics & GDSII Generation

Day 5 completed the full RTL-to-GDSII physical design flow.

### Key Tasks Completed

- Generated the Power Distribution Network (PDN), including:
  - Power rings  
  - Power straps  
  - Standard cell power rails  
- Verified power connectivity across all cells, including the custom inverter  
- Performed global and detailed routing using **TritonRoute**  
- Analyzed routing congestion and DRC behavior  
- Extracted parasitics (SPEF) to model interconnect RC effects  
- Executed post-route STA using extracted RC data  
- Verified final setup and hold timing  
- Generated the final **GDSII** using **Magic**  
- Conducted final visual inspection of the layout  

This stage delivers a **fabrication-ready GDSII**, marking completion of the end-to-end physical design flow.
## Conclusion

This repository demonstrates a **complete, industry-aligned ASIC physical design flow** using open-source EDA tools and a real production PDK. It highlights hands-on experience across the full RTL-to-GDSII pipeline, emphasizing not just tool execution but deep understanding of design analysis, debugging, and optimization.

The project reflects the ability to analyze reports, resolve timing and physical violations, make informed design trade-offs, and achieve closure across all major stages of chip implementation.
