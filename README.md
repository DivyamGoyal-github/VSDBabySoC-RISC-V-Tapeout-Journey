# 🖥️ RISC-V Reference SoC Tapeout Program VSD

<div align="center">

![RISC-V](https://img.shields.io/badge/RISC--V-SoC%20Tapeout-blue?style=for-the-badge&logo=riscv)
![VSD](https://img.shields.io/badge/VSD-Program-orange?style=for-the-badge)
![Participants](https://img.shields.io/badge/Participants-3500+-success?style=for-the-badge)
![India](https://img.shields.io/badge/Made%20in-India-saffron?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAyNCAyNCIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj4KPHJlY3Qgd2lkdGg9IjI0IiBoZWlnaHQ9IjgiIGZpbGw9IiNGRjk5MzMiLz4KPHJlY3QgeT0iOCIgd2lkdGg9IjI0IiBoZWlnaHQ9IjgiIGZpbGw9IiNGRkZGRkYiLz4KPHJlY3QgeT0iMTYiIHdpZHRoPSIyNCIgaGVpZ2h0PSI4IiBmaWxsPSIjMTM4ODA4Ii8+Cjwvc3ZnPgo=)

</div>

Welcome to my journey through the **SoC Tapeout Program VSD**!

This repository documents my **week-by-week progress** with tasks inside each week.

<div align="center">

> *"In this program, we learn to design a System-on-Chip (SoC) from basic RTL to GDSII using open-source tools. Part of India's largest collaborative RISC-V tapeout initiative, empowering 3500+ participants to build silicon and advance the nation's semiconductor ecosystem."*

</div>

<div align="center">

```
📝 RTL Design → 🔄 Synthesis → 🏗️ Physical Design → 🎯 Tapeout Ready
```

</div>

<details>
    <summary><span style="color:#3FA9F5;">Week 0 - Setup and Tools Installation</span></summary>

    
    
# Task 1
## RTL to GDSII SoC Design Flow

This covers the complete journey of designing a **System-on-Chip (SoC)**, starting from high-level specifications and ending at a verified GDSII layout.

---

## 🔹 Design Flow Steps

### 1. **Chip Modelling (O1)**

* Begin with **specifications** using a **C model**.
* Create a **C testbench** to validate functionality at this level.

---

### 2. **RTL Design (O2)**

* Write the **soft copy of hardware** using **RTL (Verilog)**.
* Model different blocks:
  * **Processor**
  * **Peripherals / IPs**
* Verify functionality through RTL testbenching.

---

### 3. **Synthesis & Netlist Generation**

* Convert RTL into a **Gate-Level Netlist**.
* Include supporting elements:

  * **Macros (synthesized RTL)**
  * **Analog IPs (functional RTL)**
* Netlist represents the circuit structure in terms of logic gates.

---

### 4. **SoC Integration (O3)**

* Integrate **Processor, Macros, Analog IPs, GPIOs, and Peripherals** into a single SoC.
* Validate correctness of the overall system.

---

### 5. **Physical Design (RTL2GDS)**

* Perform the following steps:

  * **Floorplanning**
  * **Placement**
  * **Clock Tree Synthesis (CTS)**
  * **Routing**
* Place **hardened macros and analog IP libraries** in layout.
* Generate the **GDSII file** (final chip layout).

---

### 6. **Verification & Signoff**

* Run **DRC (Design Rule Check)** to ensure layout follows manufacturing rules.
* Run **LVS (Layout vs. Schematic)** to confirm layout matches logical design.
* A clean DRC/LVS means the design is ready for fabrication (tape-out).

<img width="575" alt="yosys" src="week0_assets/Task1_RTLtoGDS_Flow.png">

---

## ✅ Final Validation

The SoC design is declared successful when:

**O1 = O2 = O3 = O4**

* **O1** → C Model (Specs)
* **O2** → RTL Design
* **O3** → SoC Integration
* **O4** → Final SoC with Peripherals

This equivalence ensures the chip behaves **consistently** across specification, RTL, integration, and physical implementation.

<img width="575" alt="yosys" src="week0_assets/Task1goal.png">

# Task 2

## Yosys
```
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys 
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make 
$ sudo make install
```
<img width="575" alt="yosys" src="week0_assets/yosys.png">

## Iverilog
```
$ sudo apt-get install iverilog
```
<img width="702" alt="iverilog" src="week0_assets/iverilog.png">

## GTKWave
```
$ sudo apt update
$ sudo apt install gtkwave
```
<img width="1008" alt="gtkwave" src="week0_assets/gtkwave.png">

### 🌟 Key Learnings from Week 0
- Installed and verified **open-source EDA tools** successfully.  
- Learned about **basic environment setup** for RTL design and synthesis.  
- Prepared the system for upcoming **RTL → GDSII flow experiments**.

#### **Core RTL Design & Synthesis Tools**

| Tool | Purpose | Verification |
|------|---------|--------------|
| 🧠 **Yosys** | RTL Synthesis & Logic Optimization | ✅ Verified |
| 📟 **Iverilog** | Verilog Simulation & Compilation | ✅ Verified |
| 📊 **GTKWave** | Waveform Viewer & Analysis | ✅ Verified |
| ⚡ **Ngspice** | Analog & Mixed-Signal Simulation | ✅ Verified |
| 🎨 **Magic VLSI** | Layout Design & DRC Verification | ✅ Verified |

#### **Advanced Flow Tools**

| Tool | Purpose | Verification |
|------|---------|--------------|
| 🐳 **Docker** | Containerization Platform | ✅ Verified |
| 🌊 **OpenLane** | Complete RTL-to-GDSII Flow | ✅ Verified |

</div>

---

</details>

Installed and verified **open-source EDA tools** successfullya and Learned about **basic environment setup** for RTL design and synthesis.  

<details>
    <summary><span style="color:#3FA9F5;">Week 1 - RTL Design </span></summary>

# RTL Design And Synthesis Using Sky130


This repository is a structured record of my **intensive 5-day learning journey** in RTL Design and Synthesis using open-source tools like **Icarus Verilog, GTKWave, Yosys**, and **Sky130 PDKs**.  

The bootcamp focused on bridging **RTL coding, simulation, synthesis, optimization, and gate-level verification**, covering both theoretical concepts and practical labs.

Welcome to my notes from Week 1 of the RTL Design and Synthesis by VLSI System Design (VSD). This week focused on building a solid foundation in Verilog RTL design, simulation, and the basics of digital circuit synthesis using Sky130 PDK. I’ve compiled my key learnings and insights below to reinforce the concepts and guide my ongoing practice.

---
## Prerequisites

- Basic understanding of digital logic (gates, flip-flops, multiplexers, etc.)
- Familiarity with Linux shell commands
- A Linux environment (or WSL on Windows/macOS)
- Tools: `git`, `iverilog`, `gtkwave`, `yosys`, and a text editor

---
## Structure
The repository is organized by day, each with a dedicated folder and README:

- [Day 1: Introduction to Verilog RTL Design & Synthesis](week1_assets/Day_1/README.md)
- [Day 2: Timing Libraries, Synthesis Approaches, and Efficient Flip-Flop Coding](week1_assets/Day_2/README.md)
- [Day 3: Combinational and Sequential Optimization](week1_assets/Day_3/README.md)
- [Day 4: Gate-Level Simulation (GLS), Blocking vs. Non-Blocking in Verilog, and Synthesis-Simulation Mismatch ](week1_assets/Day_4/README.md)
- [Day 5: Optimization in Synthesis ](week1_assets/Day_5/README.md)

Each day’s README includes:
- Clear explanations of the day’s concepts
- Step-by-step practical labs with code and screenshots
---

## Key Takeaways from Week 1

### **Day 1 – RTL Foundations, Simulation & Synthesis Tools**

<details>
    <summary>Day 1</summary>

#  Day 1: Introduction to Verilog RTL Design & Synthesis

I'm diving into digital design and exploring Verilog, a hardware description language. This day's focus is on understanding the basics of Verilog, simulation with  **Icarus Verilog (iverilog)**, and logic synthesis using **Yosys**.
---

##  Table of Contents

1. [What is a Simulator, Design, and Testbench?](#1-what-is-a-simulator-design-and-testbench)
2. [iverilog Simulation Flow](#2-iverilog-Simulation-Flow)
3. [What is a VCD File](#3-what-is-a-vcd-file)
4. [Lab: Simulating a 2-to-1 Multiplexer](#4-lab-simulating-a-2-to-1-multiplexer)
5. [Verilog Code Analysis](#4-verilog-code-analysis)
6. [Yosys & Gate Libraries](#6-introduction-to-yosys--gate-libraries)
7. [Synthesis Lab with Yosys](#7-synthesis-lab-with-yosys)
8. [Summary](#8-summary)

---

## 1. What is a Simulator, Design, and Testbench?

###  Simulator

A **simulator** is a software tool that runs our digital circuit virtually. It takes our Verilog design and a testbench as input to check if the circuit works correctly before it's ever built. This saves significant time and cost by helping you find bugs early in the design process.

###  Design

The **design** is the core of our project. It's the Verilog code that describes the actual logic of the circuit you want to create. This could be anything from a simple counter to a complex processor. It’s what you're ultimately building and what the testbench is meant to verify.

###  Testbench

A **testbench** is the verification environment for our design. It's a separate Verilog file that doesn't get turned into hardware. Its purpose is to feed specific inputs to our design and check if the outputs are correct, acting like a lab where we can test our circuit and ensure it behaves as expected.

<div align="center">
  <img src="./week1_assets/Day_1/assets/testbench.png" alt="Design & Testbench Overview" width="70%">
</div>

---

## 2. iverilog Simulation Flow

**iverilog** is an open-source simulator for Verilog. Here’s the typical simulation flow:

<div align="center">
  <img src="./week1_assets/Day_1/assets/iverilog_simulation_flow.png" alt="iverilog Simulation Flow" width="70%">
</div>

- Inputs: The process starts with two Verilog files: the **Design** and the **Test Bench**.

The Design is the Verilog code for the digital circuit you want to test.

The Test Bench is a separate Verilog file that applies specific input signals to your design and checks for correct outputs. It acts as the testing environment.

- The simulator produces a `.vcd` file for waveform viewing in GTKWave.

---
## 3. What is a VCD File

A **VCD (Value Change Dump)** file is a text-based file that records the activity of a digital circuit during a simulation. It is essentially a log of every time a signal's value changes, along with the specific timestamp of that change.

This file format is widely used in the field of digital design because it provides a compact and standardized way to capture all the necessary information for a waveform viewer (like **GTKWave**) to display the simulation results graphically for analysis and debugging.

---
## 4. Lab: Simulating a 2-to-1 Multiplexer

Simulating a simple **2-to-1 multiplexer** using iverilog!

###  Step 1: Clone the Workshop Repository

```shell
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
```
<div align="center">
  <img src="./week1_assets/Day_1/assets/Clone_repo.png" alt="clone_repo" width="70%">
</div>

### Step 2: Install Required Tools

```shell
sudo apt install iverilog
sudo apt install gtkwave
```

###  Step 3: Simulate the Design

Compile the design and testbench:

```shell
iverilog good_mux.v tb_good_mux.v
```
<div align="center">
  <img src="./week1_assets/Day_1/assets/a.out_file_creation.png" alt="a.out file creation" width="70%">
</div>
Run the simulation:

```shell
./a.out
```
<div align="center">
  <img src="./week1_assets/Day_1/assets/vcd_file_dumped.png" alt="vcd dumped file creation" width="70%">
</div>
This creates a VCD File 

View the waveform:

```shell
gtkwave tb_good_mux.vcd
```

<div align="center">
  <img src="./week1_assets/Day_1/assets/mux_output_gtkwave.png" alt="GTKWave waveform" width="70%">
</div>

---

## 5. Verilog Code Analysis

2:1 Multiplexer in Verilog
This project contains the Verilog code for a simple 2:1 multiplexer (mux) and its corresponding testbench for functional verification.

Project Files
good_mux.v: This is the design file. It contains the Verilog module for the 2:1 mux.

tb_good_mux.v: This is the testbench file. It simulates the design by providing various inputs and generating a waveform file for analysis.

<div align="center">
  <img src="./week1_assets/Day_1/assets/vim_editor.png" alt="vim_editor" width="70%">
</div>

**The code for the multiplexer (`good_mux.v`):**

```verilog
module good_mux (input i0, input i1, input sel, output reg y);
always @ (*)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule
```

###  **Working**

The good_mux module is a combinational circuit. It has two data inputs, i0 and i1, and a single select line, sel. The output y is determined by the sel signal:

If sel is 0, the output y will be equal to i0.

If sel is 1, the output y will be equal to i1

The Testbench (tb_good_mux.v)
```verilog timescale 1ns / 1ps
module tb_good_mux;

    // Inputs
    reg i0, i1, sel;
    // Outputs
    wire y;

    // Instantiate the Unit Under Test (UUT)
    good_mux good_mux_inst (
        .i0(i0),
        .i1(i1),
        .sel(sel),
        .y(y)
    );

    initial begin
        $dumpfile("tb_good_mux.vcd");
        $dumpvars(0, tb_good_mux);
        // Initialize Inputs
        sel = 0;
        i0 = 0;
        i1 = 0;
        #388 $finish;
    end
    
    always #75 sel = ~sel;
    always #10 i0 = ~i0;
    always #10 i1 = ~i1;

endmodule
```
This file is the verification environment for the multiplexer design. It doesn't get turned into a physical circuit. Instead, its job is to:

Instantiate the Design: It includes the good_mux module and connects its inputs and outputs to testbench signals.

Generate Stimulus: It uses initial and always blocks to provide a sequence of input values (i0, i1, sel) to the multiplexer over time.

Dump Waveforms: It uses the system tasks $dumpfile and $dumpvars to record the changes in all signals during the simulation, which creates the .vcd file for viewing.

---
## 6. Introduction to Yosys & Gate Libraries

###  What is Yosys?

**Yosys** is a powerful open-source synthesis tool for digital hardware. It takes the Verilog code and converts it into a gate-level netlist—a hardware blueprint.

<div align="center">
  <img src="./week1_assets/Day_1/assets/yosys_setup.png" alt="yosys_setup" width="70%">
</div>

#### Yosys Features

- **Synthesis:** Converts HDL to a logic circuit
- **Optimization:** Improves speed or area
- **Technology Mapping:** Matches logic to actual hardware cells
- **Verification:** Checks correctness
- **Extensibility:** Supports custom flows

###  Why Do Libraries Have Different Gate "Flavors"?

A `.lib` file contains many versions of each gate (like AND, OR, NOT) with different properties:

- **Performance:** Faster gates for critical paths, slower for power savings
- **Power:** Some gates use less energy
- **Area:** Smaller gates for compact chips
- **Drive Strength:** Stronger gates to drive more load
- **Signal Integrity:** Specialized gates for noise/performance
- **Mapping:** Synthesis tools pick the best flavor for your needs

<div align="center">
  <img src="./week1_assets/Day_1/assets/about_.lib.png" alt="about_.lib" width="70%">
</div>

#### Cell Selection
<div align="center">
  <img src="./week1_assets/Day_1/assets/Cell_Selection.png" alt="cell-selection" width="70%">
</div>
<div align="center">
  <img src="./week1_assets/Day_1/assets/Fast_Slow_Cells.png" alt="Fast_Slow_Cells" width="70%">
</div>

---

## 7. Synthesis Lab with Yosys

Let’s synthesize the `good_mux` design using Yosys!

###  Step-by-Step Yosys Flow

1. **Start Yosys**
    ```shell
    yosys
    ```

2. **Read the liberty library**
    ```shell
    read_liberty -lib ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

3. **Read the Verilog code**
    ```shell
    read_verilog good_mux.v
    ```

<div align="center">
  <img src="./week1_assets/Day_1/assets/read_verilog_yosys.png" alt="read_verilog_yosys" width="70%">
</div>

4. **Synthesize the design**
    ```shell
    synth -top good_mux
    ```

5. **Technology mapping**
    ```shell
    abc -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

6. **Visualize the gate-level netlist**
    ```shell
    show good_mux
    ```

<div align="center">
  <img src="./week1_assets/Day_1/assets/yosys_show.png" alt="Yosys show" width="70%">
</div>

7. **gate-level netlist**
    ```shell
    write_verilog good_mux_netlist.v
    !vim good_mux_netlist.v
    ```
<div align="center">
  <img src="./week1_assets/Day_1/assets/netlist.png" alt="Gate-level netlist" width="70%">
</div>

---
## 8. Summary

- Learned about simulators, designs, and testbenches.
- Ran my first Verilog simulation with iverilog and visualized waveforms.
- Analyzed the 2-to-1 mux code.
- Explored Yosys and learned why gate libraries have various flavors.

---


</details>

- **Concepts Covered:**
  - Introduction to RTL design with Verilog.
  - Setup and usage of **Icarus Verilog** for simulation.
  - Waveform analysis with **GTKWave**.
  - Introduction to **Yosys** and logic synthesis flow.
  - Familiarization with **Sky130 PDKs** for real silicon mapping.
- **Labs Completed:**
  - Simulated basic combinational circuits (AND, OR, MUX) using Icarus Verilog.
  - Waveform analysis in GTKWave.
  - Synthesized a simple adder circuit using Yosys.
  - Observed technology-mapped gates with Sky130 libraries.
- **Outcome:**  
  Gained hands-on comfort with Verilog simulation and basic synthesis flows.

---

### **Day 2 – Timing Libraries & Robust RTL Coding**


<details>
    <summary>Day 2</summary>

# Day 2: Timing libs, Hierarchical vs Flat Synthesis and Efficient Flop Coding Styles
---
## Introduction to timing .libs

**Libraries are characterized based on PVT (process, voltage, temperature) \
Process -> Variations due to fabrication \
Voltage -> Variations due to voltage \
Temperature -> Variations due to temperature**

when we open the sky_lib library file then all the information about the library is visible like - \
**tt stands for typical in the .lib name \
025C stands for temperature of 25 C in the .lib name \
1v80 stands for voltage of 1.8V in the .lib name**
<div align="center">
  <img src="./week1_assets/Day_2/assets/sky_lib.png" alt="sky_lib" width="70%">
</div>

-cell defines the beginning of the cell. Other information of cells mentioned are:
- Leakage power based on the combination of inputs
- Area
- Power ports
- Input capacitance
- Power associated with the pin
- Transition
- Delay

---
## Hierarchical vs Flat Synthesis

###  Synthesis Procedure

1. **Start Yosys**
    ```shell
    yosys
    ```

2. **Read the liberty library**
    ```shell
    read_liberty -lib ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

3. **Read the Verilog code**
    ```shell
    read_verilog <filename.v>
    ```

4. **Synthesize the design**
    ```shell
    synth -top <module>
    ```

5. **Technology mapping**
    ```shell
    abc -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

6. **Visualize the gate-level netlist**
    ```shell
    show <module>
    ```

7. **gate-level netlist**
    ```shell
    write_verilog <filename_netlist.v>
    !vim <filename_netlist.v>
    ```
8. **For Flatten Synthesis**
    ```shell
    flatten <module>
    abc -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

---
### Hierarchical Synthesis
Lets take an example of a module containing submodules like -
```verilog 
module sub_module2 (input a, input b, output y);
    assign y = a | b;
endmodule

module sub_module1 (input a, input b, output y);
    assign y = a&b;
endmodule

module multiple_modules (input a, input b, input c , output y);
    wire net1;
    sub_module1 u1(.a(a),.b(b),.y(net1));  //net1 = a&b
    sub_module2 u2(.a(net1),.b(c),.y(y));  //y = net1|c ,ie y = a&b + c;
endmodule
```
<div align="center">
  <img src="./week1_assets/Day_2/assets/multiple_modules.png" alt="multiple_modules" width="70%">
</div>

Report after synthesizing multiple_modules.v. As shown below the sub_modules statistics are printed. For example, sub-module1 has 1 AND gate and sub-module2 has 1 OR gate. This is an example of Hierarchical Synthesis.
<div align="center">
  <img src="./week1_assets/Day_2/assets/synth_multiple_modules.png" alt="synth_multiple_modules" width="70%">
</div>

Hierarchy is preserved. sub_module1 and sub_module2 are instantiated separately in the synthesized Verilog netlist. Rather than seeing AND or OR gate, we see sub_modules when we run the command 'show' as shown in the screenshot.

<div align="center">
  <img src="./week1_assets/Day_2/assets/hierarchical_schematic.png" alt="hierarchical_schematic" width="70%">
</div>

For **gate-level netlist** 
```shell
write_verilog hier_netlist.v
!vim hier_netlist.v
```
    
<div align="center">
  <img src="./week1_assets/Day_2/assets/hier_netlist_1.png" alt="hier_netlist_1" width="70%">
</div>
<div align="center">
  <img src="./week1_assets/Day_2/assets/hier_netlist_2.png" alt="hier_netlist_2" width="70%">
</div>

**Advantages:**
-Faster synthesis time for large designs.
-Improved debugging and analysis due to maintained module boundaries.
-Modular approach, aiding integration with other tools.

**Disadvantages:**
-Cross-module optimizations are limited.
Reporting can require additional configuration.

---
### Flat Synthesis
The design can be flattened by using the command `flatten`.
The gate level implementation after synthesis is shown as below -
<div align="center">
  <img src="./week1_assets/Day_2/assets/Flat_schematic.png" alt="Flat_schematic" width="70%">
</div>

Hierarchy is not preserved. sub_module1 and sub_module2 are now seen as AND or OR gate which is different from the earlier `hierarchical_schematic`.
Flatten netlist -
<div align="center">
  <img src="./week1_assets/Day_2/assets/flat_netlist_1.png" alt="flat_netlist_1" width="70%">
</div>
<div align="center">
  <img src="./week1_assets/Day_2/assets/flat_netlist_2.png" alt="flat_netlist_2" width="70%">
</div>

**Advantages:**
-Enables aggressive, cross-module optimizations.
-Results in a unified netlist, sometimes simplifying downstream processes.

**Disadvantages:**
-Longer runtime for large designs.
-Loss of hierarchy complicates debugging and reporting.
-Can increase memory usage and netlist complexity.

Following image shows the comparsion of hierarchical_netlist vs flat_netlist
<div align="center">
  <img src="./week1_assets/Day_2/assets/Compare_hier_and_flat.png" alt="Compare_hier_and_flat" width="70%">
</div>

### Key Differences

| Aspect                | Hierarchical Synthesis             | Flattened Synthesis           |
|-----------------------|------------------------------------|------------------------------|
| Hierarchy             | Preserved                          | Collapsed                    |
| Optimization Scope    | Module-level only                  | Whole-design                 |
| Runtime               | Faster for large designs           | Slower for large designs     |
| Debugging             | Easier (traces to RTL)             | Harder                       |
| Output Complexity     | Modular structure                  | Single, complex netlist      |
| Use Case              | Modularity, analysis, reporting    | Maximum optimization         |

---
### Sub-module Level Synthesis
RTL (Register Transfer Level) designs are often modular, with various functional blocks or sub-modules. Sub-module level synthesis allows each of these sub-modules to be synthesized independently.

Why is the sub-module level synthesis necessary?
- Optimization and Area Reduction: By synthesizing sub-modules separately, the synthesis tool can optimize each one individually. It performs logic optimization, technology mapping, and area minimization for each sub-module. This leads to more efficient use of resources and reduced overall chip area.
- Resuability: Each submodule can be designed, verified, and optimized independently. They can be reused in a large design multiple times saving time and enhancing efficiency. 
- Parallel Processing: Different sub-modules can be synthesized concurrently, improving efficiency. For large designs, parallel synthesis significantly reduces turnaround time.

The commands to run sub-module synthesis
```
read_liberty -lib ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog multiple_modules.v
synth -top sub_module1
abc -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
show sub_module1
```

## Various Flop Coding Styles and Optimization

### Why do we need flops and how do they prevent glitches in the circuit?

Glitches can occur in digital circuits due to various reasons such as signal delays, noise, or timing issues. Flops prevent glitches during the operation in the following ways:
- Synchronization: Flops are edge-triggered devices, meaning they respond only to transitions of the input signal (e.g., rising edge, falling edge). This synchronization ensures that the output changes only at specific points, reducing the likelihood of glitches caused by transient signal variations.
- Timing Control: Flops are typically controlled by a clock signal, ensuring that all circuit operations occur synchronously. This eliminates timing issues that could lead to glitches due to data arriving at different times.

### Different types of flops
Flip-flops are fundamental sequential elements in digital design, used to store binary data. Below are efficient coding styles for different reset/set behaviors.
To initialize flops, we need to `set` and `reset` which can be synchronous or asynchronous.

### Asynchronous Reset D Flip-Flop

```verilog
module dff_asyncres (input clk, input async_reset, input d, output reg q);
  always @ (posedge clk, posedge async_reset)
    if (async_reset)
      q <= 1'b0;
    else
      q <= d;
endmodule
```
- **Asynchronous reset**: Overrides clock, setting q to 0 immediately.
- **Edge-triggered**: Captures d on rising clock edge if reset is low.

### Asynchronous Set D Flip-Flop

```verilog
module dff_async_set (input clk, input async_set, input d, output reg q);
  always @ (posedge clk, posedge async_set)
    if (async_set)
      q <= 1'b1;
    else
      q <= d;
endmodule
```
- **Asynchronous set**: Overrides clock, setting q to 1 immediately.

### Synchronous Reset D Flip-Flop

```verilog
module dff_syncres (input clk, input async_reset, input sync_reset, input d, output reg q);
  always @ (posedge clk)
    if (sync_reset)
      q <= 1'b0;
    else
      q <= d;
endmodule
```
- **Synchronous reset**: Takes effect only on the clock edge.

### Simulation and Synthesizing flops

### Icarus Verilog Simulation

1. **Compile:**
   ```shell
   iverilog dff_asyncres.v tb_dff_asyncres.v
   ```
2. **Run:**
   ```shell
   ./a.out
   ```
3. **View Waveform:**
   ```shell
   gtkwave tb_dff_asyncres.vcd
   ```
The screenshot below shows DFF with asynchronous reset HDL simulation in Iverilog and waveform display in GTKwave. Irrespective of the clock and d, as soon as async_reset=1, q=0.

<div align="center">
  <img src="./week1_assets/Day_2/assets/gtkwave_dff_async_reset.png" alt="gtkwave_dff_async_reset" width="70%">
</div>

Similarly we can simulate other flipflops - \
`dff_async_set`
<div align="center">
  <img src="./week1_assets/Day_2/assets/gtkwave_dff_async_set.png" alt="gtkwave_dff_async_set" width="70%">
</div>

`dff_sync_reset`
<div align="center">
  <img src="./week1_assets/Day_2/assets/gtkwave_dff_sync_reset.png" alt="gtkwave_dff_sync_reset" width="70%">
</div>

### Synthesis with Yosys
The command to synthesize ***DFF with asynchronous reset*** as an example -
1. Start Yosys:
   ```shell
   yosys
   ```
2. Read Liberty library:
   ```shell
   read_liberty -lib ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
   ```
3. Read Verilog code:
   ```shell
   read_verilog dff_asyncres.v
   ```
4. Synthesize:
   ```shell
   synth -top dff_asyncres
   ```
5. Map flip-flops:
   ```shell
   dfflibmap -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
   ```
6. Technology mapping:
   ```shell
   abc -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
   ```
7. Visualize the gate-level netlist:
   ```shell
   show dff_asyncres
   ```

On synthesizing ***DFF with synchronous reset*** we get NOR gate with inverted `d` as shown in the screenshot below. However,on evaluating the boolean expression, we reached the same logic realization. 
<div align="center">
  <img src="./week1_assets/Day_2/assets/yosys_dff_async_reset.png" alt="yosys_dff_async_reset" width="70%">
</div>
Similarly we get the synthesis for -

`dff_async_set`
<div align="center">
  <img src="./week1_assets/Day_2/assets/yosys_dff_async_set.png" alt="yosys_dff_async_set" width="70%">
</div>

`dff_sync_reset`
<div align="center">
  <img src="./week1_assets/Day_2/assets/yosys_dff_sync_reset.png" alt="yosys_dff_sync_reset" width="70%">
</div>

### Synthesizing mult2 (multiply by 2)

To implement `y[3:0] = 2*a[2:0]`, we append a `1'b0 `to the `a[2:0]` i.e, `y[3:0] = {a[2:0],0}`. This is also equal to left shift the input bits by 1.
This can be realized by just wiring.
So we expect no hardware which is also seen in the screenshot below, analysis after synthesis and show. The command 'abc' is not required for mapping when there are no cells.

<div align="center">
  <img src="./week1_assets/Day_2/assets/yosys_mul2.png" alt="yosys_mul2" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_2/assets/mul2_netlist.png" alt="mul2_netlist" width="70%">
</div>

### Synthesizing mult9 (multiply by 9 or 8+1)

`y=9*a` can be considered `8*a+1*a`
To implement `y[5:0] = 9*a[2:0]`, we append `000` to `a[2:0]` and then add `a` i.e, `y[5:0] = {a[2:0],000} + a[2:0]`.
This can be realized just by wiring.
So we expect no hardware which is also seen in the screenshot below, analysis after synthesis and show. The command 'abc' is not required for mapping when there are no cells.

<div align="center">
  <img src="./week1_assets/Day_2/assets/yosys_mult8.png" alt="yosys_mult8" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_2/assets/mult8_netlist.png" alt="mult8_netlist" width="70%">
</div>

</details>

- **Concepts Covered:**
  - What are timing libraries (`*.lib`) and why they matter.
  - Hierarchical vs Flat synthesis – optimization trade-offs.
  - Efficient flop coding styles to ensure timing-friendly RTL.
- **Labs Completed:**
  - Compared hierarchical vs flat synthesis results.
  - Coded different DFF styles and analyzed their impact on synthesis.
- **Outcome:**  
  Learned how coding style directly affects timing, area, and synthesis efficiency.

---

### **Day 3 – Combinational & Sequential Optimizations**

<details>
    <summary>Day 3</summary>

# Day 3: Combinational and Sequential Optimization
Combinational and sequential optimization are distinct approaches in digital circuit design, each addressing the specific characteristics of combinational logic and sequential logic to improve a circuit's performance, area, and power consumption.

<div align="center">
  <img src="./week1_assets/Day_3/assets/Combinational_vs_Sequential_ckt.png" alt="Combinational_vs_Sequential_ckt" width="70%">
</div>

---
## Table of Contents
1. [Combinational logic optimization](#combinational-logic-optimization)
2. [Sequential logic optimization](#sequential-logic-optimization)
3. [Constant propagation](#constant-propagation)
4. [State Optimization](#state-optimization)
5. [Cloning](#cloning)
6. [Retiming](#retiming)
7. [Labs on Optimization](#labs-on-optimization)

---
## Combinational logic optimization
Combinational logic circuits produce outputs based solely on their present inputs, with no memory of past states. Optimization focuses on minimizing the number of logic gates, transistors, and the circuit's depth to achieve a smaller size, lower power, and higher speed. 

### Objectives
- Area minimization: Reducing the number of logic gates and transistors used.
- Speed improvement: Reducing the circuit's critical path delay (the longest delay from an input to an output).
- Power reduction: Decreasing the switching activity of the circuit. 

---
## Sequential logic optimization
Sequential logic circuits have memory elements (e.g., flip-flops) and their outputs depend on both the current inputs and the previous state. This adds an extra dimension to optimization, allowing for techniques that consider the circuit's behavior over time. 

### Objectives
- State minimization: Reducing the number of states in a finite state machine (FSM) representation, which in turn reduces the number of flip-flops required.

- Retiming: Moving flip-flops within a circuit to balance delays, reduce the overall clock period, and improve performance without changing the circuit's functionality.

- State encoding: Assigning binary codes to the states of an FSM to minimize the complexity of the combinational logic needed for state transitions.

- Low-power design: Using techniques like precomputation to disable parts of the circuit when not needed, reducing power consumption. 

---
## Constant propagation
Constant propagation is an optimization technique that simplifies logic by identifying and replacing gates with known, constant input values. If the output of a gate can be determined solely by its constant inputs, the gate can be removed and its output replaced by the constant value.

### Benefits:
- Reduced Complexity: Simpler logic, smaller circuit.
- Performance Improvement: Faster execution and reduced delays.
- Resource Optimization: Fewer gates or flip-flops required.

## State optimization
State optimization, specifically for finite state machines (FSMs), aims to reduce the number of states while preserving the machine's behavior. A simpler FSM requires fewer registers, which reduces area and power. 

### Core techniques
- State minimization: This process involves identifying and merging redundant or equivalent states. Two states are considered equivalent if they produce the same output and transition to equivalent next states for every possible input.
- State encoding (or state assignment): Once the number of states is minimized, a binary code is assigned to each unique state. The encoding strategy significantly impacts the complexity of the FSM's combinational logic. Common encoding methods include:
    - Binary encoding: The most compact encoding, but can lead to complex combinational logic.
    - One-hot encoding: Assigns one flip-flop per state. While it uses more registers, it can simplify the decoding logic, often leading to faster operation.
    - Gray encoding: Ensures that only one bit changes between adjacent state codes, which can help minimize power consumption by reducing switching activity. 

---
## Cloning
Cloning duplicates a logic cell or module to optimize performance, reduce power, or improve timing by balancing load or reducing wire length.
### How it works
- Problem: A single gate, P, drives multiple downstream gates (sinks), S1, S2, S3, etc. This creates a large capacitive load on gate P, increasing its delay.
- Solution: A copy (P') of gate P is created. The sinks are partitioned, with some driven by P and the others by P'. This reduces the fanout of both P and P', lowering the capacitance and therefore the signal propagation delay.
- Result: The technique improves the overall timing of the design, particularly on critical paths. It is often combined with other physical synthesis techniques, such as buffer insertion and placement optimization, to achieve the best results.

<div align="center">
  <img src="./week1_assets/Day_3/assets/Cloning.png" alt="Cloning" width="70%">
</div>

## Retiming
Retiming is a sequential optimization technique that repositions registers (flip-flops) in a circuit to balance delays, improve clock frequency, or minimize the number of registers. It moves registers across combinational logic blocks without changing the circuit's overall function. 
### How it works
- Minimizing clock period: Retiming can move registers away from long combinational paths (the critical path) and place them closer to shorter paths. This breaks up long delays and allows the circuit to operate at a higher clock frequency.
- Minimizing registers: In cases where timing is not the limiting factor, retiming can be used to merge registers, reducing the total register count and thus lowering the circuit's area and power consumption.
- Backward and forward retiming: Registers can be moved either backward (upstream) toward the inputs or forward (downstream) toward the outputs. Moving a register backward across a gate requires adding a register to every input of that gate. Conversely, moving registers forward from the inputs of a gate to its output can reduce the register count if the gate has multiple inputs. 

**Example-**

Consider a path with three combinational logic blocks, C1, C2, and C3, separated by registers R1 and R2. If C2 has a significantly longer delay than C1 and C3, it becomes the critical path.

`IN -> R1 -> C1 -> C2 -> R2 -> C3 -> OUT`\
A retiming tool could move R2 forward across C3.\
`IN -> R1 -> C1 -> C2 -> C3 -> R2 -> OUT`\
It could then move R1 forward across C1.\
`IN -> C1 -> R1 -> C2 -> C3 -> R2 -> OUT`\
This balances the logic delay between the registers, potentially allowing a faster clock speed. 

---
## Labs on Optimization

Follow the steps from [Day 1 Synthesis Lab](https://github.com/DivyamGoyal-github/RTL_Design/tree/main/Day_1#7-synthesis-lab-with-yosys) and add the following between `abc -liberty` and `synth -top`:
```shell
opt_clean -purge
```

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_verilogFile_optimised_by_AND_gate.png" alt="opt_check_verilogFile_optimised_by_AND_gate" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_optimisation.png" alt="opt_check_optimisation" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_opt_check.png" alt="yosys_opt_check" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_2_verilogFile_optimised_by_OR_gate.png" alt="opt_check_2_verilogFile_optimised_by_OR_gate" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_2_optimisation.png" alt="opt_check_2_optimisation" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_opt_check_2.png" alt="yosys_opt_check_2" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_chec_3_verilogFile.png" alt="opt_chec_3_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_3_optimisation.png" alt="opt_check_3_optimisation" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_opt_check_3.png" alt="yosys_opt_check_3" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_4_verilogFile.png" alt="opt_check_4_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/opt_check_4_optimisation.jpg" alt="opt_check_4_optimisation" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_opt_check_4.png" alt="yosys_opt_check_4" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/multiple_module_opt_verilogFile.png" alt="multiple_module_opt_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_multiple_module_opt_Flatten_clean-purge.png" alt="yosys_multiple_module_opt_Flatten_clean" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/multiple_module_opt_2_verilogFile.png" alt="multiple_module_opt_2_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_multiple_module_opt_2_Flatten_clean-purge.png" alt="yosys_multiple_module_opt_2_Flatten_clean" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/gtkwave_dff_const_1.png" alt="gtkwave_dff_const_1" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_dff_const_1.png" alt="yosys_dff_const_1" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/dff_const1_2.png" alt="dff_const1_2" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_dff_const_2.png" alt="yosys_dff_const_2" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/gtkwave_dff_const_3.png" alt="gtkwave_dff_const_3" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/dff_const3.png" alt="dff_const3" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_dff_const_3.png" alt="yosys_dff_const_3" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/gtkwave_dff_const_4.png" alt="gtkwave_dff_const_4" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_dff_const_4.png" alt="yosys_dff_const_4" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/gtkwave_dff_const_5.png" alt="gtkwave_dff_const_5" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_dff_const_5.png" alt="yosys_dff_const_5" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/counter_opt_verilogFile.png" alt="counter_opt_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_counter_opt.png" alt="yosys_counter_opt" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/verilog_file_new_counter_opt.png" alt="verilog_file_new_counter_opt" width="80%">
</div>

<div align="center">
  <img src="./week1_assets/Day_3/assets/yosys_new_counter_opt.png" alt="yosys_new_counter_opt" width="80%">
</div>


</details>

- **Concepts Covered:**
  - Synthesis optimizations: how tools simplify logic.
  - **Combinational optimizations:** constant folding, redundant gate removal.
  - **Sequential optimizations:** FSM simplification, unused register elimination.
  - Proper handling of unused outputs.
- **Labs Completed:**
  - Verified Boolean simplification automatically performed during synthesis.
  - Observed state machine reduction in synthesized designs.
  - Experimented with unused output signals and their effect on synthesis.
- **Outcome:**  
  Developed understanding of how synthesis tools "clean up" designs for efficiency.

---

### **Day 4 – Gate-Level Simulation & RTL/Synthesis Mismatches**

<details>
    <summary>Day 4</summary>

# Day 4: GLS, blocking vs non-blocking and Synthesis-Simulation mismatch

## Table of Contents
- [Gate Level Simulation](#gate-level-simulation-gls)  
- [Synthesis - Simulation mismatch](#synthesis---simulation-mismatch)
- [Synthesis of Ternary Operator MUX](#synthesis-of-ternary-operator-mux)  
- [GLS of Ternary Operator MUX](#gls-of-ternary-operator-mux)  
- [Synthesis of Bad MUX design](#synthesis-of-bad-mux-design)  
- [GLS of Bad MUX design](#gls-of-bad-mux-design)  
- [Synthesis of blocking_caveat design](#synthesis-of-blocking_caveat-design)  
- [GLS of blocking_caveat design](#gls-of-blocking_caveat-design)  

---
## Gate Level Simulation (GLS)
  * _Gate Level_ refers to the netlist view of a design after the synthesis has been performed.
  * RTL simulations are pre-synthesis, while GLS is post-synthesis - i.e., in RTL simulations, the Device Under Test (DUT) is the RTL design itself while in GLS, the DUT is the netlist generated after synthesis.
  * The RTL code and the generated netlist are logically equivalent (well, supposed to be!)  and hence the same testbenches can be used to verify both.
  * Although it is expected that the generated netlist has the same logical correctness as the RTL design, there can sometimes be mismatches between the RTL-level simulation and the sythesized design (Synthesis - Simulation mismatch) and thus arises the need to run GLS to help identify such scenarios and fix them to ensure the logical correctness post-synthesis as well.

To run GLS, we need to provide the Gate level netlist, the testbench and the Gate Level verilog models to the simulator.  
GLS can be run in different delay modes:
   1. Functional validation (zero delay similar to RTL sim): if the Gate Level verilog models do not have the timing information for various corners, we can only verify the functional correctness of the design by running GLS.
   2. Full Timing validation: if the Gate level verilog models have the necessary timing information, both the functional correctness and the timing behaviour can be verified by GLS.
   
<div align="center">
  <img src="./week1_assets/Day_4/assets/GLS_using_iverilog.png" alt="GLS_using_iverilog" width="70%">
</div>

### Why Perform GLS?

- **Synthesis Validation**: Ensures that synthesis tools faithfully translate RTL into gates.
- **Timing Verification**: Simulates with realistic delays (from SDF files), allowing you to check for timing violations (e.g., setup/hold errors).
- **Testability**: Confirms that scan chains and other test features work post-synthesis.

### When is GLS Performed?

- **After synthesis**: Once the RTL is converted into a gate-level netlist.
- **Before physical design**: To catch issues early, before layout.

### Types of GLS

- **Functional GLS**: Logic-only simulation, often with zero or unit delays.
- **Timing GLS**: Uses annotated timing data to check real-world timing behavior.

---
## Synthesis - Simulation mismatch

A **synthesis-simulation mismatch** occurs when the simulation results of RTL (pre-synthesis) do not match simulation results of the gate-level netlist (post-synthesis) or hardware. Reasons include:

- **Non-synthesizable constructs**: Use of delays, initial blocks, or other code not supported by synthesis.
- **Incomplete or ambiguous coding**: E.g., missing `else` clauses, improper sensitivity lists.
- **Tool interpretation differences**: Simulation and synthesis tools may interpret ambiguous RTL differently.

**Key Point:** Always write synthesizable, unambiguous RTL and follow good coding practices to minimize mismatches.

Some of the common reasons for Synthesis - Simulation mismatch (mismatch between pre- and post-synthesis simulations) :  
  * Incomplete sensitivity list
  * Use of blocking assignments inside always block vs. non-blocking assignments
    * Blocking assignments ("=") inside always block are executed sequentially by the simulator.
    * The RHS of non-blocking assignments ("<=") are evaluated first and then assigned to the LHS at the same simulation clock tick by the simulator. 
    * Synthesis will yield the same circuit with blocking and non-blocking assignments, with the synthesis output being that of the non-blocking case for both.
    * Hence, if the RTL was written assuming one functionality using blocking assignments, a simulation mismatch can occur in GLS.
  * Non-standard verilog coding
    
<div align="center">
  <img src="./week1_assets/Day_4/assets/Reasons_of_Synthesis_Simulation_mismatch.png" alt="Reasons_of_Synthesis_Simulation_mismatch" width="70%">
</div>

---

For ex: As seen in the screenshot below, in the left column,always block is evaluated only when sel is changing. So output y is not reflecting changes in input i1 and i0 when sel is not changing. Rather it acts like a latch. 

The code on the right side represents the correct design coding for mux. In this case always is evaluated for any signal changes.

<div align="center">
  <img src="./week1_assets/Day_4/assets/Missing_sensitivity_list.png" alt="Missing_sensitivity_list" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_4/assets/Blocking_NonBlocking_statements.png" alt="Blocking_NonBlocking_statements" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_4/assets/Blocking_NonBlocking_statements_ex2.png" alt="Blocking_NonBlocking_statements_ex2" width="70%">
</div>

---
## Synthesis of Ternary Operator MUX

``ternary_operator_mux.v ``
```verilog
module ternary_operator_mux (input i0 , input i1 , input sel , output y);
    assign y = sel?i1:i0;
    endmodule
```
Testbench ``tb_ternary_operator_mux.v``

```verilog 

`timescale 1ns / 1ps
module tb_ternary_operator_mux;
    // Inputs
    reg i0,i1,sel;
    // Outputs
    wire y;

        // Instantiate the Unit Under Test (UUT)
    ternary_operator_mux uut (
        .sel(sel),
        .i0(i0),
        .i1(i1),
        .y(y)
    );

    initial begin
    $dumpfile("tb_ternary_operator_mux.vcd");
    $dumpvars(0,tb_ternary_operator_mux);
    // Initialize Inputs
    sel = 0;
    i0 = 0;
    i1 = 0;
    #300 $finish;
    end

always #75 sel = ~sel;
always #10 i0 = ~i0;
always #55 i1 = ~i1;
endmodule
```

### `RTL simulation`

```shell
iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
./a.out
gtkwave tb_ternary_operator_mux.vcd
```

<div align="center">
  <img src="./week1_assets/Day_4/assets/rtl_ternary_operator_mux.png" alt="rtl_ternary_operator_mux" width="70%">
</div>

Steps for Netlist Generation
1. **Start Yosys**
    ```shell
    yosys
    ```

2. **Read the liberty library**
    ```shell
    read_liberty -lib ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

3. **Read the Verilog code**
    ```shell
    read_verilog ternary_operator_mux.v
    ```

4. **Synthesize the design**
    ```shell
    synth -top ternary_operator_mux
    ```

5. **Technology mapping**
    ```shell
    abc -liberty ../my_lib/verilog_models/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

6. **Visualize the gate-level netlist**
    ```shell
    show ternary_operator_mux
    ```

7. **gate-level netlist**
    ```shell
    write_verilog -noattr ternary_operator_mux_netlist.v
    !vim ternary_operator_mux_netlist.v
    ```

---
## GLS of Ternary Operator MUX

Gate-Level Simulation is performed using the synthesized netlist (ternary_operator_mux_netlist.v) instead of RTL. This helps verify the functional correctness of the design after synthesis, using the actual standard cells and any delays (if modeled)

```bash
# Compile the gate-level netlist and testbench
iverilog ../my_lib/verilog_model/primitives.v  ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v

# Run the simulation binary
./a.out

# View the waveform
gtkwave tb_ternary_operator_mux.vcd
```

<div align="center">
  <img src="./week1_assets/Day_4/assets/gls_ternary_operator_mux.png" alt="gls_ternary_operator_mux" width="70%">
</div>

## Synthesis of Bad MUX design
``bad_mux.v``
```verilog
module bad_mux (input i0 , input i1 , input sel , output reg y);
always @ (sel)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule
```
This bad_mux uses a blocking sensitivity list (@ (sel)) without including data inputs (i0, i1), leading to a simulation-synthesis mismatch due to incomplete sensitivity.


Testbench ``tb_bad_mux.v``
```verilog
`timescale 1ns / 1ps
module tb_bad_mux;
    // Inputs
    reg i0,i1,sel;
    // Outputs
    wire y;

        // Instantiate the Unit Under Test (UUT)
    bad_mux uut (
        .sel(sel),
        .i0(i0),
        .i1(i1),
        .y(y)
    );

    initial begin
    $dumpfile("tb_bad_mux.vcd");
    $dumpvars(0,tb_bad_mux);
    // Initialize Inputs
    sel = 1'b0;
    i0 = 1'b0;
    i1 = 1'b0;
    #300 $finish;
    end

always #75 sel = ~sel;
always #10 i0 = ~i0;
always #55 i1 = ~i1;
endmodule
```

### `RTL simulation`

```bash
iverilog bad_mux.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
<div align="center">
  <img src="./week1_assets/Day_4/assets/rtl_bad_mux.png" alt="rtl_bad_mux" width="70%">
</div>

After this synthesise the netlist using yosys 

---
## GLS of Bad MUX design

```bash
iverilog ../my_lib/verilog_model/primitives.v  ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_netlist.v tb_bad_mux.v
./a.out
gtkwave tb_bad_mux.vcd
```
<div align="center">
  <img src="./week1_assets/Day_4/assets/gls_bad_mux_sensitivity_simulation_mismatch.png" alt="gls_bad_mux_sensitivity_simulation_mismatch" width="70%">
</div>

So clearly their is a Synthesis-Simulation Mismatch of Bad MUX design
The waveform illustrates a `synthesis vs. simulation mismatch` caused by the RTL not including i0 and i1 in the sensitivity list.

---
## Synthesis of blocking_caveat design

``blocking_caveat.v``
```verilog
module blocking_caveat (input a , input b , input  c, output reg d); 
reg x;
always @ (*)
begin
    d = x & c;
    x = a | b;
end
endmodule
```

Testbench ``tb_blocking_caveat.v``
```verilog
`timescale 1ns / 1ps
module tb_blocking_caveat;
    // Inputs
    reg a,b,c   ;
    // Output
    wire d;

        // Instantiate the Unit Under Test (UUT)
    blocking_caveat uut (
        .a(a),
        .b(b),
        .c(c),
        .d(d)
    );

    initial begin
    $dumpfile("tb_blocking_caveat.vcd");
    $dumpvars(0,tb_blocking_caveat);
    // Initialize Inputs
    a = 0;
    b = 0;
    c = 0;
    #3000 $finish;
    end

always #10 a = ~a;
always #100 c =~c;
always #50 b = ~b;
endmodule
```

### RTL simulation

```bash
iverilog blocking_caveat.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
<div align="center">
  <img src="./week1_assets/Day_4/assets/rtl_blocking_caveat.png" alt="rtl_blocking_caveat" width="70%">
</div>

After this synthesise the netlist using yosys 

---
## GLS of blocking_caveat design

```bash
iverilog ../my_lib/verilog_model/primitives.v  ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_netlist.v tb_blocking_caveat.v
./a.out
gtkwave tb_blocking_caveat.vcd
```
<div align="center">
  <img src="./week1_assets/Day_4/assets/gls_blocking_caveat_blockingStatement_mismatch.png" alt="gls_blocking_caveat_blockingStatement_mismatch" width="70%">
</div>

In this case, there is a mismatch in the simulation results between pre and post-synthesis due to the use of blocking assignments.

</details>

- **Concepts Covered:**
  - Running **Gate-Level Simulation (GLS)** with netlists.
  - Identifying **simulation vs synthesis mismatches**.
  - Blocking (`=`) vs Non-blocking (`<=`) assignments in procedural code.
- **Labs Completed:**
  - Compared RTL simulation vs GLS waveforms.
  - Created intentional mismatches using blocking assignments.
  - Debugged sequence failures in GLS.
- **Outcome:**  
  Ability to write synthesis-safe RTL and debug synthesis-simulation mismatches.

---

### **Day 5 – Control Structures, Loops & Advanced Coding**

<details>
    <summary>Day 5</summary>

# Day 5: Optimization in Synthesis

 Optimization in Verilog synthesis, focusing on `if-else` statements, `for` loops, generate blocks, and explore how improper coding can lead to inferred latches. 

---
## Table of Contents
- [1. If-Else Statements in Verilog](#1-if-else-statements-in-verilog)
- [2. Inferred Latches in Verilog](#2-inferred-latches-in-verilog)
- [3. Labs for If-Else and Case Statements](#3-labs-for-if-else-and-case-statements)
  - [Lab 1: Incomplete If Statement](#lab-1-incomplete-if-statement)
  - [Lab 2: Synthesis Result of Lab 1](#lab-2-synthesis-result-of-lab-1)
  - [Lab 3: Nested If-Else](#lab-3-nested-if-else)
  - [Lab 4: Synthesis Result of Lab 3](#lab-4-synthesis-result-of-lab-3)
  - [Lab 5: Incomplete Case Statement](#lab-5-incomplete-case-statement)
  - [Lab 5: Complete Case Statement](#lab-5-complete-case-statement)
  - [Lab 6: Synthesis Result of Lab 5](#lab-6-synthesis-result-of-lab-5)
  - [Lab 7: Complete Case Statement](#lab-7-complete-case-statement)
  - [Lab 8: Synthesis Result of Lab 7](#lab-8-synthesis-result-of-lab-7)
  - [Lab 9: Bad Case Handling](#lab-9-bad-case-handling)
  - [Lab 10: Synthesis Result of Lab 9](#lab-10-synthesis-result-of-lab-9)
  - [Lab 11: Partial Assignments in Case](#lab-11-partial-assignments-in-case)
- [4. For Loops in Verilog](#4-for-loops-in-verilog)
- [5. Generate Blocks in Verilog](#5-generate-blocks-in-verilog)
- [6. What is an RCA (Ripple Carry Adder)?](#6-what-is-an-rca-ripple-carry-adder)
- [7. For vs For Generate](#7-for-vs-for-generate)
- [8. Labs on Loops and Generate Blocks](#8-labs-on-loops-and-generate-blocks)
  - [Lab 12: 4-to-1 MUX Using For Loop](#lab-12-4-to-1-mux-using-for-loop)
  - [Lab 13: 8-to-1 Demux Using Case](#lab-13-8-to-1-demux-using-case)
  - [Lab 14: 8-to-1 Demux Using For Loop](#lab-14-8-to-1-demux-using-for-loop)
  - [Lab 15: 8-bit Ripple Carry Adder with Generate Block](#lab-15-8-bit-ripple-carry-adder-with-generate-block)
- [Summary](#summary)

---

## 1. If-Else Statements in Verilog

**If-else statements** are used for conditional execution in behavioral modeling, typically within procedural blocks (`always`, `initial`, tasks, or functions).

### Syntax

```verilog
if (condition) begin
    // Code block executed if condition is true
end else begin
    // Code block executed if condition is false
end
```

- **condition**: An expression evaluating to true (non-zero) or false (zero).
- **begin ... end**: Used to group multiple statements. Omit if only one statement is present.
- The `else` part is optional.


#### Nested If-Else

```verilog
if (condition1) begin
    // Code for condition1 true
end else if (condition2) begin
    // Code for condition2 true
end else begin
    // Code if no conditions are true
end
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/if_statement.png" alt="if_statement" width="70%">
</div>

#### Case Statment

<div align="center">
  <img src="./week1_assets/Day_5/assets/Case_statement.png" alt="Case_statement" width="70%">
</div>

---
## 2. Inferred Latches in Verilog

**Inferred latches** occur when a combinational logic block does not assign a value to a variable in all possible execution paths. This causes the synthesis tool to infer a latch, which may not be the designer’s intention.

### Example of Latch Inference

```verilog
module ex (
    input wire a, b, sel,
    output reg y
);
    always @(a, b, sel) begin
        if (sel == 1'b1)
            y = a; // No 'else' - y is not assigned when sel == 0
    end
endmodule
```

**Problem**: When `sel` is 0, `y` is not assigned, so a latch is inferred.

<div align="center">
  <img src="./week1_assets/Day_5/assets/inferred_latch_problem_with_incomplete_if_statement.png" alt="inferred_latch_problem_with_incomplete_if_statement" width="70%">
</div>


#### Solution: Add Else or Default Case

```verilog
module ex (
    input wire a, b, sel,
    output reg y
);
    always @(a, b, sel) begin
        case(sel)
            1'b1 : y = a;
            default : y = 1'b0; // Default assignment
        endcase
    end
endmodule
```

We generally add an Else/default statement to mitigate this problem but sometimes if statement could be usefull without else based on application. For example, in a counter if no enable is their then it latches to the previous value

<div align="center">
  <img src="./week1_assets/Day_5/assets/incomplete_if_Counter_application.png" alt="incomplete_if_Counter_application" width="70%">
</div>

---
## 3. Labs for If-Else and Case Statements

### Lab 1: Incomplete If Statement

```verilog
module incomp_if (input i0, input i1, input i2, output reg y);
always @(*) begin
    if (i0)
        y <= i1;
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_incom_if.png" alt="gtkwave_incom_if" width="70%">
</div>

---

### Lab 2: Synthesis Result of Lab 1

<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_incom_if.png" alt="yosys_incom_if" width="70%">
</div>

---

### Lab 3: Nested If-Else

```verilog
module incomp_if2 (input i0, input i1, input i2, input i3, output reg y);
always @(*) begin
    if (i0)
        y <= i1;
    else if (i2)
        y <= i3;
end
endmodule
```
<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_incom_if2.png" alt="gtkwave_incom_if2" width="70%">
</div>

---

### Lab 4: Synthesis Result of Lab 3

<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_incom_if2.png" alt="yosys_incom_if2" width="70%">
</div>

---
### Lab 5: Incomplete Case Statement

```verilog
module incomp_case (input i0 , input i1 , input i2 , input [1:0] sel, output reg y);
always @ (*)
begin
    case(sel)
        2'b00 : y = i0;
        2'b01 : y = i1;
    endcase
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/inferred_latch_problem_with_incomplete_case_statement.png" alt="inferred_latch_problem_with_incomplete_case_statement" width="70%">
</div>


<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_incom_case.png" alt="gtkwave_incom_case" width="70%">
</div>
---

### Lab 6: Synthesis Result of Lab 5

<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_incom_case.png" alt="yosys_incom_case" width="70%">
</div>

---
### Lab 7: Complete Case Statement

```verilog
module comp_case (input i0, input i1, input i2, input [1:0] sel, output reg y);
always @(*) begin
    case(sel)
        2'b00 : y = i0;
        2'b01 : y = i1;
        default : y = i2;
    endcase
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_comp_case.png" alt="gtkwave_comp_case" width="70%">
</div>
---

### Lab 8: Synthesis Result of Lab 7

<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_comp_case.png" alt="yosys_comp_case" width="70%">
</div>

---

### Lab 9: Bad Case Handling

```verilog
module bad_case (
    input i0, input i1, input i2, input i3,
    input [1:0] sel,
    output reg y
);
always @(*) begin
    case(sel)
        2'b00: y = i0;
        2'b01: y = i1;
        2'b10: y = i2;
        2'b1?: y = i3; // '?' is a wildcard; be careful with incomplete cases!
    endcase
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/overlapping_problem_case_statement.png" alt="overlapping_problem_case_statement" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_bad_case.png" alt="gtkwave_bad_case" width="70%">
</div>

---

### Lab 10: Synthesis Result of Lab 9

<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_bad_case.png" alt="yosys_bad_case" width="70%">
</div>

Let's check the GLS of the bad case also
<div align="center">
  <img src="./week1_assets/Day_5/assets/gls_bad_case.png" alt="gls_bad_case" width="70%">
</div>

---
### Lab 11: Partial Assignments in Case

```verilog
module partial_case_assign (
    input i0, input i1, input i2,
    input [1:0] sel,
    output reg y, output reg x
);
always @(*) begin
    case(sel)
        2'b00: begin
            y = i0;
            x = i2;
        end
        2'b01: y = i1;
        default: begin
            x = i1;
            y = i2;
        end
    endcase
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/partial_assignments_case_statement.png" alt="partial_assignments_case_statement" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_partial_case.png" alt="yosys_partial_case" width="70%">
</div>

---
## 4. For Loops in Verilog

A **for loop** is used within procedural blocks (`initial`, `always`, tasks/functions) to execute statements multiple times based on a loop counter.

<div align="center">
  <img src="./week1_assets/Day_5/assets/Loop_constructs.png" alt="Loop_constructs" width="70%">
</div>

### Why Loops?
Loops helps in better readibility and more easy to write the code for more complex hardwares. An example is shown below that how code becomes so big if we go from 2:1 MUX to 32:1 MUX

<div align="center">
  <img src="./week1_assets/Day_5/assets/why_loops.png" alt="why_loops" width="70%">
</div>

Loop Benefits -
Example of a MUX

<div align="center">
  <img src="./week1_assets/Day_5/assets/loop_benefits_mux.png" alt="loop_benefits_mux" width="70%">
</div>

Example of a DEMUX

<div align="center">
  <img src="./week1_assets/Day_5/assets/loop_benefits_demux.png" alt="loop_benefits_demux" width="70%">
</div>

### Syntax

```verilog
for (initialization; condition; increment) begin
    // Statements to execute
end
```

- Must be inside procedural blocks.
- Synthesizable only if the number of iterations is fixed at compile time.

#### Example: 4-to-1 MUX Using a For Loop

```verilog
module mux_4to1_for_loop (
    input wire [3:0] data, // 4 input lines
    input wire [1:0] sel,  // 2-bit select
    output reg y           // Output
);
    integer i;
    always @(data, sel) begin
        y = 1'b0; // Default output
        for (i = 0; i < 4; i = i + 1) begin
            if (i == sel)
                y = data[i];
        end
    end
endmodule
```

---
## 5. Generate Blocks in Verilog

A **generate block** is used to create hardware structures such as module instances or logic at compile time. Typically used with `for` loops and the `genvar` keyword.

#### Example

```verilog
genvar i;
generate
    for (i = 0; i < 4; i = i + 1) begin : gen_loop
        and_gate and_inst (.a(in[i]), .b(in[i+1]), .y(out[i]));
    end
endgenerate
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/For_generate.png" alt="For_generate" width="70%">
</div>

---

## 6. What is an RCA (Ripple Carry Adder)?

An RCA adds binary numbers using a chain of full adders. To add `n` bits, you need `n` full adders. Each carry-out connects to the carry-in of the next stage.

<div align="center">
  <img src="./week1_assets/Day_5/assets/RCA.png" alt="RCA(Ripple Carry Adder)" width="70%">
</div>

<div align="center">
  <img src="./week1_assets/Day_5/assets/For_generate_application_ripple_carry_adder.png" alt="For_generate_application_ripple_carry_adder" width="70%">
</div>

---
## 7. For vs For Generate

<div align="center">
  <img src="./week1_assets/Day_5/assets/For_vs_ForGenerate.png" alt="For_vs_ForGenerate" width="70%">
</div>

---

## 8. Labs on Loops and Generate Blocks

### Lab 12: 4-to-1 MUX Using For Loop

```verilog
module mux_generate (
    input i0, input i1, input i2, input i3,
    input [1:0] sel,
    output reg y
);
wire [3:0] i_int;
assign i_int = {i3, i2, i1, i0};
integer k;
always @(*) begin
    for (k = 0; k < 4; k = k + 1) begin
        if (k == sel)
            y = i_int[k];
    end
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_mux_using_for_loop.png" alt="gtkwave_mux_using_for_loop" width="70%">
</div>

---

### Lab 13: 8-to-1 Demux Using Case

```verilog
module demux_case (
    output o0, output o1, output o2, output o3,
    output o4, output o5, output o6, output o7,
    input [2:0] sel,
    input i
);
reg [7:0] y_int;
assign {o7, o6, o5, o4, o3, o2, o1, o0} = y_int;
always @(*) begin
    y_int = 8'b0;
    case(sel)
        3'b000 : y_int[0] = i;
        3'b001 : y_int[1] = i;
        3'b010 : y_int[2] = i;
        3'b011 : y_int[3] = i;
        3'b100 : y_int[4] = i;
        3'b101 : y_int[5] = i;
        3'b110 : y_int[6] = i;
        3'b111 : y_int[7] = i;
    endcase
end
endmodule
```

---

### Lab 14: 8-to-1 Demux Using For Loop

```verilog
module demux_generate (
    output o0, output o1, output o2, output o3,
    output o4, output o5, output o6, output o7,
    input [2:0] sel,
    input i
);
reg [7:0] y_int;
assign {o7, o6, o5, o4, o3, o2, o1, o0} = y_int;
integer k;
always @(*) begin
    y_int = 8'b0;
    for (k = 0; k < 8; k = k + 1) begin
        if (k == sel)
            y_int[k] = i;
    end
end
endmodule
```

<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_demux_for_loop.png" alt="gtkwave_demux_for_loop" width="70%">
</div>

---

### Lab 15: 8-bit Ripple Carry Adder with Generate Block

```verilog
module rca (
    input [7:0] num1,
    input [7:0] num2,
    output [8:0] sum
);
wire [7:0] int_sum;
wire [7:0] int_co;

genvar i;
generate
    for (i = 1; i < 8; i = i + 1) begin
        fa u_fa_1 (.a(num1[i]), .b(num2[i]), .c(int_co[i-1]), .co(int_co[i]), .sum(int_sum[i]));
    end
endgenerate

fa u_fa_0 (.a(num1[0]), .b(num2[0]), .c(1'b0), .co(int_co[0]), .sum(int_sum[0]));

assign sum[7:0] = int_sum;
assign sum[8] = int_co[7];
endmodule
```
**Full Adder Module:**
```verilog
module fa (input a, input b, input c, output co, output sum);
    assign {co, sum} = a + b + c;
endmodule
```

Simulating in GTKwave
<div align="center">
  <img src="./week1_assets/Day_5/assets/gtkwave_rca.png" alt="gtkwave_rca" width="70%">
</div>

Yosys Synthesis 
<div align="center">
  <img src="./week1_assets/Day_5/assets/yosys_rca.png" alt="yosys_rca" width="70%">
</div>

GLS Of Ripple carry Adder using the testbench and generated netlist
<div align="center">
  <img src="./week1_assets/Day_5/assets/gls_rca.png" alt="gls_rca" width="70%">
</div>

---
## Summary
- Use complete if-else and case statements to avoid unintended latch inference.
- For loops and generate blocks are powerful for writing scalable, synthesizable code.
- Always ensure every signal is assigned in every possible execution path for combinational logic.
- Use labs to reinforce concepts with practical Verilog code and synthesis results.

---

</details>

- **Concepts Covered:**
  - Correct handling of **if-case constructs** to avoid latch inference.
  - Understanding **overlapping vs parallel case statements**.
  - Using **for loops** and **for-generate** for scalable RTL.
- **Labs Completed:**
  - Wrote incomplete if/case RTL and observed unintended latch generation.
  - Explored overlapping case behavior.
  - Designed scalable structures (barrel shifter/register replications) using loops and generate.
- **Outcome:**  
  Mastery of advanced RTL coding constructs ensuring correctness and scalability.

---

## ⚡ Tools & Technologies Used
- **Verilog HDL**
- **Icarus Verilog** (simulation)
- **GTKWave** (waveform visualization)
- **Yosys** (logic synthesis)
- **Sky130 PDKs** (real silicon standard cell libraries)

---

## 🏆 Week 1 Achivements
- Write Verilog RTL that is **simulation-correct and synthesis-friendly**.  
- Perform simulation with Icarus Verilog and debug waveforms in GTKWave.  
- Run synthesis flows in Yosys and map to Sky130 gates.  
- Understand timing libraries and design trade-offs.  
- Optimize designs at both combinational and sequential levels.  
- Confidently perform **Gate-Level Simulation (GLS)** to verify post-synthesis behavior.  
- Avoid RTL pitfalls like incomplete case statements, blocking assignments, and unintended latches.  

---

## My Notes and Insights

- **Design Workflow:** The typical flow I’m learning involves writing RTL → simulating with testbenches → synthesizing with Yosys → analyzing waveforms and debugging.
- **Importance of Clear Coding Practices:** Proper naming conventions and modular code make debugging and future modifications much easier.
- **Open-Source Ecosystem:** Sky130 and Yosys are powerful tools that democratize hardware design, making it accessible for students and hobbyists.

---

## 🌟 Reflection
This 5-day week on RTL Design has given me **end-to-end confidence** in the digital design flow: from coding RTL, simulating it, synthesizing with real libraries, to debugging mismatches at gate-level simulation. I now approach RTL **not just as code, but as real hardware blueprints**.


This initial week has laid a strong foundation for my RTL design journey. I look forward to applying these concepts in more complex designs and exploring optimization techniques in the upcoming weeks!

</details>

---

Hands-on introduction to Verilog RTL, including combinational and sequential logic modeling, simulation using Icarus Verilog, and waveform analysis with GTKWave.
Also covers RTL coding styles, writing testbenches, and synthesizing basic designs using Yosys and Sky130 libraries.

<details>
    <summary><span style="color:#3FA9F5;">Week 2 - SOC Fundamentals </span></summary>

# System on Chip (SoC) Fundamentals

<div>
  <img src="./week2_assets/System-On-Chip.jpg" alt="System-on-chip" width="70%">
</div>


This repository provides a deep dive into the **fundamentals of System on Chip (SoC) design**, covering its definition, architecture, benefits, challenges, and the role of VLSI in modern electronics. Whether you're a student, hobbyist, or professional, this guide will help you understand the core concepts and latest trends in SoC and VLSI design.

---

## Table of Contents
- [What is a System on Chip (SoC)?](#what-is-a-system-on-chip-soc)
- [Why Do We Need SoC?](#why-do-we-need-soc)
- [Key Benefits of SoC](#key-benefits-of-soc)
- [SoC Architecture](#soc-architecture)
- [Current Challenges in SoC Design](#current-challenges-in-soc-design)
- [Role of VLSI in SoC Design](#role-of-vlsi-in-soc-design)
- [Latest Trends in SoC and VLSI (2025)](#latest-trends-in-soc-and-vlsi-2025)
- [Applications of SoC](#applications-of-soc)
- [VSDBabySoC](#vsdbabysoc-a-compact-risc-v-soc-for-learning-and-experimentation)

---

## What is a System on Chip (SoC)?

A **System on Chip (SoC)** is an integrated circuit (IC) that integrates all components of a computer or electronic system into a single chip. This includes:
- Central Processing Unit (CPU)
- Memory (RAM, ROM)
- Input/Output (I/O) interfaces
- Graphics Processing Unit (GPU)
- Wireless connectivity (Wi-Fi, Bluetooth)
- Power management units
- Specialized accelerators (AI, DSP, etc.)

SoCs are the backbone of modern smart devices, enabling compact, efficient, and high-performance electronics.

---

## Why Do We Need SoC?

| Reason                | Explanation                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| Miniaturization       | Combines multiple functions into a single chip, reducing device size       |
| Power Efficiency       | Optimized for low power consumption, ideal for battery-operated devices    |
| Performance           | Faster data processing due to reduced communication latency                |
| Cost-Effectiveness    | Lower manufacturing and assembly costs compared to multi-chip systems      |
| Reliability           | Fewer interconnections mean higher reliability and fewer points of failure 

---

## Key Benefits of SoC

| Benefit               | Impact                                                                     |
|-----------------------|---------------------------------------------------------------------------|
| Reduced Size          | Enables smaller, portable devices (smartphones, wearables)                |
| Lower Power           | Extends battery life for IoT and mobile devices                           |
| Improved Performance  | Faster processing and real-time data handling                            |
| Cost Savings          | Lower production and assembly costs                                      |
| Integration           | Simplifies system design and reduces PCB complexity                      |
| Security              | Centralized security features and hardware-based protection               

---

## SoC Architecture

A typical SoC architecture includes:

| Component             | Function                                                                   |
|-----------------------|----------------------------------------------------------------------------|
| CPU Cores             | Execute instructions and manage system operations                        |
| Memory Units          | Store data and instructions (RAM, ROM, Flash)                            |
| I/O Interfaces        | Connect to external devices (USB, HDMI, Ethernet)                        |
| GPU                   | Handles graphics rendering and display output                            |
| DSP                   | Digital signal processing for audio, video, and communications            |
| Connectivity          | Wireless modules (Wi-Fi, Bluetooth, 5G)                                  |
| Power Management      | Regulates power consumption and battery life                              |
| Security Modules      | Hardware-based security (encryption, secure boot)                       

<div>
  <img src="./week2_assets/SOC_Architecture.png" alt="SOC Architecture" width="80%">
</div>


---

## Current Challenges in SoC Design

| Challenge                     | Explanation                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| Design Complexity             | Integrating billions of transistors and diverse IP blocks                  |
| Power Management              | Balancing performance with power consumption                              |
| Heat Dissipation              | Managing thermal issues in high-performance chips                         |
| Security Vulnerabilities      | Protecting against hardware-level attacks                                  |
| Verification & Testing        | Ensuring correctness and reliability of complex designs                   |
| Cost of Development           | High NRE (Non-Recurring Engineering) costs for advanced nodes              |
| Scalability                   | Supporting future upgrades and new features                             

---

## Role of VLSI in SoC Design

**VLSI (Very Large Scale Integration)** is the technology that enables the creation of SoCs by integrating thousands to billions of transistors on a single chip. VLSI is crucial for:
- Achieving high levels of integration and miniaturization
- Reducing power consumption and improving performance
- Enabling the development of complex digital and analog circuits
- Supporting advanced fabrication processes (7nm, 5nm, and below)

---
## SOC Design Flow

<div>
  <img src="./week2_assets/SOC_Design_Flow.png" alt="SOC Design Flow" width="80%">
</div>

The above image illustrates the comprehensive System on Chip (SoC) Design Flow, a multi-stage process for developing integrated circuits that combine various components of a computer system onto a single chip. The flow can be broadly categorized into Front-End Design, Software Development, and Physical Design (Back-End), culminating in manufacturing and post-silicon validation. 
SoC Design Flow Stages:

1. SoC Specification
  - The process begins by defining the intended functionality, performance goals, power constraints, and physical dimensions of the chip based on the target application. 

2. Architecture Design (Hardware/Software Partitioning)
  - A high-level architecture of the chip is developed, outlining the key functional blocks, their interconnections, and the partitioning of functions between hardware and software components. 

3. Software Development (Parallel Track)
  - High-Level Modeling: Abstract algorithmic descriptions of hardware components are created, often in languages like C or SystemC.
  - Software Development: The software components are developed in parallel with hardware design, including drivers, firmware, and application software.
  - HW/SW Co-simulation: Hardware and software components are simulated together to ensure they function correctly and verify the hardware/software interfaces.
  - Software Testing and Refinement: Rigorous testing and debugging of the software on virtual prototypes or emulation platforms ensure its correctness and compatibility with the hardware.
  - Final Code: The optimized and validated software code is prepared for integration with the hardware. 

4. Front-End Design
  - RTL Design: The architecture is translated into a Register Transfer Level (RTL) representation using Hardware Description Languages (HDLs) like Verilog or VHDL, describing the data flow and control logic.
  - Functional Simulation and Verification: Extensive simulations and verifications are performed on the RTL code to ensure functional correctness and identify design flaws.
  - RTL Synthesis and DFT: The RTL design is converted into a gate-level netlist, which is a description of the circuit in terms of logic gates and their interconnections. Design For Testability (DFT) logic is also inserted to facilitate post-fabrication testing.
  - Gate Level Netlist: The output of synthesis, a detailed description of the circuit using standard logic cells. 

5. Physical Design (Back-End)
  - Place and Route: Standard cells (logic gates) are placed on the chip, and interconnections (routing) between them are created to meet timing, power, and area constraints.
  - Timing Verification and Signoff: Static Timing Analysis (STA) is performed to verify that the design meets all timing requirements and constraints.
  - Physical Verification: Checks like Design Rule Check (DRC) and Layout Versus Schematic (LVS) are performed to ensure the physical layout adheres to manufacturing rules and matches the logical design.
  - Design GDSII: The final layout data in Graphic Data System II (GDSII) format, which is sent to the semiconductor foundry for fabrication. 

6. Manufacturing
  - The GDSII data is used to fabricate the physical chip on silicon wafers in a semiconductor foundry. 

7. Post-Silicon Validation and Integration
  - After manufacturing, the fabricated chips are tested and validated in a real-world environment to ensure they meet all functional and performance specifications. 

8. Mass Production
  - Once validated, the chips proceed to mass production to be integrated into target devices.

---
## Latest Trends in SoC and VLSI (2025)

| Trend                        | Impact                                                                     |
|------------------------------|---------------------------------------------------------------------------|
| AI & ML Integration          | On-chip AI accelerators for real-time processing                          |
| 3D Stacked Integration       | Higher density and performance using 3D IC stacking                       |
| Advanced Materials           | Use of graphene, carbon nanotubes for better electrical/thermal properties |
| Edge Computing                | SoCs optimized for real-time, low-latency processing at the edge         |
| Security-First Design         | Hardware-based security for IoT and connected devices                    |
| Open-Source RISC-V           | Customizable, royalty-free CPU cores for diverse applications            

---

## Applications of SoC

| Industry          | Example Applications                                              |
|-------------------|-------------------------------------------------------------------|
| Mobile            | Smartphones, tablets, smartwatches                                |
| Automotive        | Advanced Driver Assistance Systems (ADAS), infotainment         |
| Healthcare        | Portable medical devices, wearables                              |
| IoT              | Smart home devices, industrial sensors                           |
| Consumer Electronics | Smart TVs, gaming consoles, digital cameras                     |
| Telecommunications | 5G modems, network routers                                      

---
# VSDBabySoC: A Compact RISC-V SoC for Learning and Experimentation

**VSDBabySoC** is a small-scale, open-source **System on Chip (SoC)** built around the **RISC-V** architecture. Designed for educational and experimental purposes, it enables simultaneous testing of three open-source IP cores and calibration of analog components.

---

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [SoC Architecture](#soc-architecture)
- [Components](#components)
  - [RVMYTH: The RISC-V CPU](#rvmyth-the-risc-v-cpu)
  - [PLL: Phase-Locked Loop](#pll-phase-locked-loop)
  - [DAC: Digital-to-Analog Converter](#dac-digital-to-analog-converter)
- [How It Works](#how-vsd-baby-soc-works)
  - [Initialization and Clock Generation](#initialization-and-clock-generation)
  - [Data Processing in RVMYTH](#data-processing-in-rvmyth)
  - [Analog Signal Generation via DAC](#analog-signal-generation-via-dac)
- [Why Use a PLL?](#why-use-a-pll)
- [DAC: Digital to Analog Conversion](#dac-digital-to-analog-conversion)
- [Applications](#applications)
- [Getting Started](#getting-started)

---

# VSDBabySoC
VSDBabySoC is designed to bridge the gap between digital and analog domains, making it an ideal platform for learning about SoC design, CPU architecture, clock synchronization, and analog signal generation. It integrates a RISC-V CPU, a PLL for clock generation, and a DAC for analog output, all on a single chip.

---

## Key Features

| Feature                | Description                                                                 |
|------------------------|-----------------------------------------------------------------------------|
| **RISC-V CPU (RVMYTH)**| Open-source, customizable CPU core for processing tasks.                   |
| **8x PLL**             | Generates stable, synchronized clock signals for the SoC.                  |
| **10-bit DAC**         | Converts digital data to analog signals for real-world applications.       |
| **Open-Source**        | All components and designs are open for modification and experimentation.  |
| **Educational Focus**  | Ideal for learning SoC design, CPU architecture, and analog/digital conversion. |

---

## SoC Architecture
The VSDBabySoC architecture is modular, with each component playing a specific role:

<div>
  <img src="./week2_assets/VSDbabySOC.png" alt="VSDbabySOC" width="80%">
</div>

## Components

### RVMYTH: The RISC-V CPU
- **Role:** Acts as the brain of the SoC, executing instructions and managing data flow.
- **Features:**
  - Open-source RISC-V ISA implementation.
  - Customizable and extensible for educational purposes.
  - Communicates with the DAC via the `r17` register.
- **Use Case:** Ideal for learning CPU architecture, assembly programming, and SoC integration.

### PLL: Phase-Locked Loop
- **Role:** Generates a stable, synchronized clock signal for the SoC.
- **Features:**
  - Locks onto a reference frequency and minimizes jitter.
  - Ensures all components operate in harmony.
  - Can multiply or divide frequencies as needed.
- **Block Diagram:**

<div align="center" >
  <img src="./week2_assets/PLL_Diagram.png" alt="PLL_Diagram" width="70%">
</div>

- **Components:**
  - **Phase Detector:** Compares input and output signals, generating an error signal.
  - **Loop Filter:** Processes the error signal to produce a control voltage.
  - **VCO (Voltage-Controlled Oscillator):** Adjusts frequency based on the control voltage.

### DAC: Digital-to-Analog Converter
- **Role:** Converts digital data from the CPU into analog signals.
- **Features:**
  - 10-bit resolution for high-quality output.
  - Outputs analog signals to external devices (e.g., speakers, displays).
  - Supports real-world applications like audio/video generation.
- **Types of DACs:**
  - **Weighted Resistor DAC:** Uses resistors of different values for each bit.
  - **R-2R Ladder DAC:** Uses a network of resistors for simpler design and scaling.

### **1. Binary Weighted Resistor DAC**

#### **Overview**
The **Binary Weighted Resistor DAC** converts a digital input (binary code) into an analog voltage output using resistors whose values are weighted in powers of two. Each bit of the digital input controls a switch that connects the corresponding resistor to a reference voltage or ground.

#### **Circuit Diagram**

<div align="center" >
  <img src="./week2_assets/BinaryWeightedDAC.png" alt="BinaryWeightedDAC" width="70%">
</div>

#### **Working Principle**
- Each bit of the digital input is connected to a resistor whose value is twice that of the next lower bit.
- The most significant bit (MSB) uses the smallest resistor, and the least significant bit (LSB) uses the largest.
- The output voltage is the sum of the voltages contributed by each bit, weighted by the resistor values.

#### **Advantages**
- Simple and easy to understand.
- Fast conversion due to direct resistor network.

#### **Disadvantages**
- Requires a wide range of resistor values, which can be impractical for high-resolution DACs.
- More expensive and less scalable for higher bit counts.

---

### **2. R-2R Ladder DAC**

#### **Overview**
The **R-2R Ladder DAC** is a popular type of DAC that uses only two resistor values (R and 2R) arranged in a ladder network. This design simplifies the circuit and makes it easier to scale for higher resolutions.

#### **Circuit Diagram**

<div align="center" >
  <img src="./week2_assets/R2RLadderDAC.png" alt="R2RLadderDAC" width="70%">
</div>

#### **Working Principle**
- The ladder network is constructed using resistors of values R and 2R.
- Each bit of the digital input controls a switch that connects the corresponding node to either the reference voltage or ground.
- The equivalent resistance seen by each node is always 2R, regardless of the number of bits, due to the ladder’s recursive structure.
- The output voltage is the sum of the voltages contributed by each bit, weighted by the ladder network.

#### **Advantages**
- Uses only two resistor values, making it easier and cheaper to manufacture.
- Highly scalable for higher bit counts.
- More practical for integrated circuit implementation.

#### **Disadvantages**
- Slightly more complex to analyze and design compared to the binary weighted DAC.
- Requires precise resistor matching for accurate conversion.

#### **Formula**
The output voltage `V_out` is given by:

`V_out = -V_ref * (b0/2^1 + b1/2^2 + b2/2^3 + ... + b(n-1)/2^n)`

where:
- `V_ref` is the reference voltage,
- `b0, b1, ..., b(n-1)` are the bits of the digital input (0 or 1),
- `n` is the number of bits.

---

### **Comparison Table**

| Feature                     | Binary Weighted Resistor DAC       | R-2R Ladder DAC                     |
|-----------------------------|------------------------------------|-------------------------------------|
| **Resistor Values**         | Many different values (2^0R, 2^1R, ...) | Only two values (R and 2R)         |
| **Scalability**             | Poor for high bit counts           | Excellent for high bit counts       |
| **Cost**                    | Higher (more resistor types)       | Lower (only two resistor types)     |
| **Complexity**              | Simple                             | Moderate                            |
| **Speed**                   | Fast                               | Fast                                |
| **Practicality for ICs**    | Less practical                     | Highly practical                    |

---

### **Why R-2R Ladder DAC is Used in VSDBabySoC**
- **Simplicity:** Only two resistor values are needed, simplifying the design and reducing cost.
- **Scalability:** Easily extended to higher resolutions (e.g., 10-bit DAC in VSDBabySoC).
- **Integration:** Well-suited for implementation in integrated circuits and FPGAs.

---
## How VSD Baby SOC Works

### Initialization and Clock Generation
1. On power-up, the PLL is activated.
2. The PLL locks onto the reference clock and generates a stable, synchronized clock signal.
3. This clock signal is distributed to the RVMYTH CPU and DAC, ensuring all components operate in sync.

### Data Processing in RVMYTH
1. The RVMYTH CPU executes instructions and processes data.
2. The `r17` register is used to hold and cycle through values destined for the DAC.
3. As the CPU runs, it updates `r17` with new data, preparing it for analog conversion.

### Analog Signal Generation via DAC
1. The DAC receives digital values from the RVMYTH CPU.
2. It converts these values into an analog signal.
3. The analog output is saved to a file (`OUT`) and can be sent to external devices (e.g., TVs, mobile phones) for further processing or display.

---

## Why Use a PLL?

| Issue                     | Impact                                                                 |
|---------------------------|------------------------------------------------------------------------|
| **Clock Distribution Delays** | Long wiring can introduce delays, affecting timing.                   |
| **Clock Jitter**          | Variations in signal timing can disrupt synchronization.               |
| **Different Frequency Needs** | Different SoC blocks may require different clock frequencies.       |
| **Crystal Frequency Errors** | Crystals can drift with temperature and age, affecting accuracy.      |
| **Frequency Stability**   | Higher ppm errors mean more frequency variation with temperature.     |

**Solution:** The PLL provides a stable, adjustable clock signal, ensuring reliable operation across the SoC.

---

## DAC: Digital to Analog Conversion
- **Digital Signal Representation:** Input is a binary code (1s and 0s).
- **Structure:** Multiple binary inputs, single analog output.
- **In VSDBabySoC:** 10-bit DAC allows for 1024 possible output values, enabling smooth analog signals.

---

## Applications
- **Education:** Learn SoC design, CPU architecture, and analog/digital conversion.
- **Prototyping:** Test and calibrate open-source IP cores.
- **Multimedia:** Generate analog signals for audio/video applications.
- **Embedded Systems:** Interface with analog sensors and actuators.

---

## Getting Started
1. **Installation**

Before running the simulation, install the required packages and tools:

```bash
sudo apt update
sudo apt install make python3 python3-pip git iverilog gtkwave docker.io
sudo chmod 666 /var/run/docker.sock
sudo apt install python3-venv
python3 -m venv venv
source venv/bin/activate
pip install pyyaml click sandpiper-saas

# Convert rvmyth.tlv to Verilog
sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
```
### Explanation:
- make: Build automation tool
- python3, pip3: Python and package manager for additional tooling
- git: Version control system
- iverilog: Verilog simulator
- gtkwave: Waveform viewer
- docker.io: Containerization platform (used for some EDA tools)
- pyyaml, click, sandpiper-saas: Python packages for YAML parsing, CLI, and RTL processing

2. **Clone the Repository:**
   ```bash
   git clone git clone https://github.com/manili/VSDBabySoC.git
   ```

3. **Running the Simulation**
  Navigate to the project directory and run the pre-synthesis simulation:
    ```bash
    cd VSDBabySoC
    make pre_synth_sim
    ```

- The make command executes the simulation script defined in the Makefile.
- iverilog compiles the Verilog source files and runs the simulation.
- The output is saved as a Value Change Dump (VCD) file: pre_synth_sim.vcd in the output/pre_synth_sim directory.

<div align="center" >
  <img src="./week2_assets/Simulation_logs.png" alt="Simulation_logs" width="70%">
</div>

4. **Visualizing Waveforms**

  To view the simulation results, use `gtkwave`:
  ```bash
  gtkwave output/pre_synth_sim/pre_synth_sim.vcd
  ```

<div align="center" >
  <img src="./week2_assets/gtkwave_Output_Pre_Synth_Sim.png" alt="gtkwave_Output_Pre_Synth_Sim" width="70%">
</div>

| Signal Name | Description | Notes |
|-------------|-------------|--------------|
| CLK | Input clock signal for the RVMYTH core, generated by the PLL. | Drives all synchronous logic in the SoC. |
| reset | Input reset signal for the RVMYTH core, sourced externally. | Asynchronously resets the core and peripherals. |
| OUT | Output signal of the VSDBabySoC module, representing the DAC output (simulated as digital). | In simulation, this is a digital approximation of the analog output. |
| RV_TO_DAC[9:0] | 10-bit output port from the RVMYTH core (register #17), feeding the DAC. | Data bus for DAC input, representing digital values to be converted. |
| OUT (real) | Analog output of the DAC module, simulated as a analog interpolated datatype. | True analog output, only visible in simulation. |

---


</details>

---

Covers the building blocks of a System-on-Chip: processor, peripherals, memory, interconnect, and top-level integration.
You learn how SoC architecture is defined and how different subsystems communicate inside a VSDBabySoC-style RISC-V system.

<details>
    <summary><span style="color:#3FA9F5;">Week 3 - STA Fundamentals </span></summary>

# Static Timing Analysis Fundamentals

## 1. Introduction

Static Timing Analysis validates whether a synchronous digital design meets timing without applying input vectors. Instead, the STA tool breaks the design into timing paths, computes delays across cells and interconnect, and checks setup/hold and related constraints on all possible paths. Compared to simulation, STA is faster and more exhaustive for timing coverage, but it does not verify functional correctness.

**Key ideas:**
- Paths are classified by startpoint and endpoint types (ports, register pins).
- STA checks max-time constraints (setup) and min-time constraints (hold) using longest/shortest path delays respectively.
- Timing closure means zero or positive slack across all relevant paths and corners.

---

<details>
  <summary>STA Fundas</summary>

## 2. Introduction to Timing Path and Arrival Time

A timing path is the connection from a startpoint to an endpoint through a cloud of combinational logic. Startpoints include input ports or register clock pins; endpoints include register data pins or output ports.


<div align="center" >
  <img src="./week3_assets/Timing_Path.png" alt="timingpath" width="80%">
</div>

Arrival time is when data actually reaches the endpoint, computed by summing source launch timing, clk→Q, cell and net delays along the data path.

<div align="center" >
  <img src="./week3_assets/Arrival_Time.png" alt="Arrival_Time" width="80%">
</div>

Required time is when data must be present at the endpoint to meet a timing check. 

**Slack quantifies margin:**
- **Setup slack = Required Time − Arrival Time (positive is good).**
- **Hold slack = Arrival Time − Required Time (positive is good).**

<div align="center" >
  <img src="./week3_assets/Slack_calc.png" alt="Slack_calc" width="80%">
</div>


The foundational data-path types:
- reg2reg (register-to-register)
- in2reg (input-to-register)
- reg2out (register-to-output)
- in2out (input-to-output)

Each category has its own clocking/IO assumptions and checks for both setup (max) and hold (min).

- reg2reg

<div align="center" >
  <img src="./week3_assets/reg2reg.png" alt="reg2reg" width="80%">
</div>

- in2reg

<div align="center" >
  <img src="./week3_assets/in2reg.png" alt="in2reg" width="80%">
</div>

- reg2out

<div align="center" >
  <img src="./week3_assets/reg2out.png" alt="reg2out" width="80%">
</div>

- in2out

<div align="center" >
  <img src="./week3_assets/in2out.png" alt="in2out" width="80%">
</div>


Beyond setup/hold for flops, STA verifies:
- Data-to-data checks: relationships between data signals (e.g., pulse width, inter-signal skew windows) and custom min/max constraints.
- Recovery/removal checks: asynchronous set/reset must be deasserted (recovery) or asserted (removal) with proper timing relative to clock edges.

Latches introduce time borrowing (open-phase transparency), changing required-time accounting across half cycles. Correct modeling of latch transparency windows and “time given/borrowed” is essential for accurate slack computation in latch-based designs.


- Data-to-data

<div align="center" >
  <img src="./week3_assets/data2data.png" alt="data2data" width="80%">
</div>

- clock gating

<div align="center" >
  <img src="./week3_assets/clock_gating.png" alt="clock_gating" width="80%">
</div>

- recovery/removal 

<div align="center" >
  <img src="./week3_assets/recovery:removal.png" alt="recovery" width="80%">
</div>

- latch (time borrow/time given)

<div align="center" >
  <img src="./week3_assets/latch(timeborrow:timegiven).png" alt="latch" width="80%">
</div>

- Input slew and output load directly influence cell delay per timing library tables; STA propagates slews and loads to compute realistic arc delays.

- Clock checks include duty-cycle, uncertainty, and skew; uncertainty captures jitter and modeling margins and is subtracted/added in setup/hold slack equations.

- Excessive clock skew tightens setup or hold margins depending on skew polarity.

- Clock_Analysis(skew)

<div align="center" >
  <img src="./week3_assets/Clock_Analysis(skew).png" alt="Clock_Analysis(skew)" width="80%">
</div>
- Clock_Analysis(Pulse_Width)
<div align="center" >
  <img src="./week3_assets/Clock_Analysis(Pulse_Width).png" alt="Clock_Analysis(Pulse_Width)" width="80%">
</div>

---

## 3. Convert Logic Gates into Nodes

STA engines build a timing graph where pins/arcs become nodes/edges. Each gate input-to-output arc is a directed edge with delay as a function of input slew and output load. Graph-based traversal accumulates arrival times and required times across these nodes to compute slack for endpoints.

- DAG Timing Graph

<div align="center" >
  <img src="./week3_assets/DAG_Timing_Graph.png" alt="DAG_Timing_Graph" width="80%">
</div>

---

## 4. Compute Actual Arrival Time (AAT)

AAT is the latest (for setup) or earliest (for hold) time the signal arrives at a node. For setup (max-time), traverse with max-delay models; for hold (min-time), traverse with min-delay models.

Practical notes:
- Include clk→Q at the launch element, combinational delays, and net RCs.
- Consider derates for variation if OCV/AOCV/POCV is enabled.

***

## 5. Compute Required Arrival Time (RAT)

RAT flows backward from endpoints:
- For setup: from capture edge, subtract setup time and propagate back through the clock network to the startpoint edge, considering skew/uncertainty; then backward through the data graph to intermediate nodes.
- For hold: required relationship is relative to the same clock edge; the tool computes the earliest time data is allowed to change without violating hold at the capture flop.

<div align="center" >
  <img src="./week3_assets/RAT,AAT_calc.png" alt="RAT,AAT_calc" width="80%">
</div>


---

## 6. Compute Slack and Introduction to GBA-PBA Analysis

Slack = RAT − AAT (setup) or AAT − RAT (hold). Two engine styles:
- GBA (Graph-Based Analysis): fast, pessimistic; uses bounding models across reconvergent paths.
- PBA (Path-Based Analysis): re-evaluates a single critical path with tighter correlation, removing some pessimism—often used to validate the worst violators before signoff.

<div align="center" >
  <img src="./week3_assets/GBA_PBA.png" alt="GBA_PBA" width="80%">
</div>

---

## 7. Convert Pins to Nodes and Compute AAT, RAT, and Slack

Pin-level timing graph:
- Node types: input ports, register pins (CLK/D/Q/ASYNC), combinational pins, output ports.
- Edge types: timing arcs with conditional sense and tables.
Compute AAT forward from startpoints; compute RAT backward from endpoints; slack at each endpoint pin reflects design margin.

- Detailed DAG with Pin Node Conventions

<div align="center" >
  <img src="./week3_assets/Detailed_DAG_with_Pin_Node_conventions.png" alt="Detailed_DAG_with_Pin_Node_conventions" width="80%">
</div>

---

## 8. Introduction to Transistor-Level Circuit for Flops

Real flops have non-ideal setup/hold and clk→Q behaviors arising from transistor-level latching and regeneration. Internals (master–slave, sense-amplifier-based) influence library timing arcs characterized across PVT and slew/load spaces.

<div align="center" >
  <img src="./week3_assets/Setup_Analysis.png" alt="Setup_Analysis" width="80%">
</div>


---

## 9. Negative and Positive Latch Transistor-Level Operation

- Positive latch: transparent when clock is high; negative latch: transparent when clock is low.
- Transparency enables time borrowing within the open phase, but requires careful phase-aware required-time modeling and accounting for latch propagation characteristics and hold windows during transparency.

<div align="center" >
  <img src="./week3_assets/Negative_vs_Postitive_Latch.png" alt="Negative_vs_Postitive_Latch" width="80%">
</div>


---

## 10. Library Setup Time Calculation

Setup time in libraries is defined as the minimum interval data must be stable before the active clock edge to guarantee correct capture. Characterization sweeps the data/clock alignment and records the boundary beyond which capture fails, producing setup tables indexed by slew and load.

<div align="center" >
  <img src="./week3_assets/Setup_time_d_ff.png" alt="Setup_time_d_ff" width="80%">
</div>

---

## 11. Clk→Q Delay Calculation

Clk→Q is the propagation delay from active clock edge to stable Q transition. It varies with input slew, output load, and sometimes data value history. Characterization captures clk→Q tables used by STA as the starting term in arrival time computations at launch points.

<div align="center" >
  <img src="./week3_assets/Clk-q_delay.png" alt="Clk-q_delay" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/Hold_Time.png" alt="Hold_Time" width="80%">
</div>

---

## 12. Steps to Create Eye Diagram for Jitter Analysis

Conceptual workflow:
- Measure zero-crossings or sample edges over time across multiple cycles to build a composite “eye” at a receiver sampling instant.
- Extract random and deterministic jitter components to derive total jitter and map to clock uncertainty budgets that feed STA setup/hold checks.

<div align="center" >
  <img src="./week3_assets/Clk_with_VoltageDroop_Power_Variations.png" alt="Clk_with_VoltageDroop_Power_Variations" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/Eye_diagram.png" alt="Eye_diagram" width="80%">
</div>

- magnified version of the above eye diagram

 <div align="center" >
  <img src="./week3_assets/EyeDiagram_magnified.png" alt="EyeDiagram_magnified" width="80%">
</div>

---

## 13. Jitter Extraction and Accounting in Setup Timing Analysis

- Convert measured/specified jitter (cycle-to-cycle, period, random, deterministic) into clock uncertainty values.
- For setup: uncertainty reduces the effective time budget; for hold: uncertainty tightens the same-edge margin. Include PLL/DLL and distribution-induced jitter and model per-domain constraints.

<div align="center" >
  <img src="./week3_assets/Jitter&NoiseMargin.png" alt="Jitter&NoiseMargin" width="80%">
</div>

---

## 14. Setup Analysis — Graphical to Textual Representation

Graphical paths (like the attached diagrams) map to textual timing reports listing:
- Startpoint, endpoint, path group and clocks
- AAT components: clk→Q, cell, and net delays
- RAT components: period, capture clock path, setup time, uncertainty, skew
- Slack summary with WNS/TNS
Interpret the table to identify dominant contributors (logic delay, skew, uncertainty) and prioritize fixes.

- SetupAnalysis including Setuptime and uncertainity

<div align="center" >
  <img src="./week3_assets/SetupAnalysis_including_Setuptime_uncertainity.png" alt="SetupAnalysis_including_Setuptime_uncertainity" width="80%">
</div>

- Textual representation

<div align="center" >
  <img src="./week3_assets/SETUP_Graphical_to_textual_representation.png" alt="SETUP_Graphical_to_textual_representation" width="80%">
</div>

---

## 15. Hold Analysis with Real Clocks

With real clocks (non-ideal skew and latency), hold checks consider:
- Fast data path (min delay), early launch clock, late capture clock as worst case
- Negative skew can exacerbate hold failures
Fixes typically add data-path delay (buffers), rebalance clock tree, or tighten uncertainty budgets safely.

<div align="center" >
  <img src="./week3_assets/Hold_Analysis_d_ff.png" alt="Hold_Analysis_d_ff" width="80%">
</div>


---

## 16. Hold Analysis — Graphical to Textual Representation

Textual reports detail:
- Required time = Thold (+ removal for async) at capture
- Arrival = clk→Q(min) + data(min)
- Skew and uncertainty impact signs differ from setup
Read the sequence to confirm whether violations are due to overly short data paths, skew polarity, or modeling margins; then apply targeted ECOs (insert delay cells, resize drivers, route elongation) consistent with signoff corners.

<div align="center" >
  <img src="./asweek3_assetssets/HOLD_Graphical_to_textual_representation.png" alt="HOLD_Graphical_to_textual_representation" width="80%">
</div>

---

## 17. Sources of Variation — Etching

Local process variations (e.g., etch bias, line-edge roughness) alter effective transistor/channel/interconnect dimensions, shifting delay and slew. STA incorporates margins via derates (OCV) or statistical models (AOCV/POCV) to cover these local deviations across the chip.

<div align="center" >
  <img src="./week3_assets/Etching_Process_Variation.png" alt="Etching_Process_Variation" width="80%">
</div>

---

## 18. Sources of Variation — Oxide Thickness

Gate oxide thickness variation changes threshold voltage and drive current, impacting cell delay. These device-level variations are reflected in library corners and variation models used by STA, tightening max/min analyses accordingly.

<div align="center" >
  <img src="./week3_assets/Oxide_thickness_Variation.png" alt="Oxide_thickness_Variation" width="80%">
</div>

---

## 19. Relationship Between Resistance, Drain Current, and Delay

Cell and net delays depend on channel resistance and drain current; wiring resistance and capacitance set RC time constants. Increased resistance or reduced current increases propagation delay, degrading setup margins; unusually low RC can create hold hazards by making paths too fast.

- CMOS Inverter RC Circuit
<div align="center" >
  <img src="./week3_assets/CMOS_inverter_as_RC_Ckt.png" alt="CMOS_inverter_as_RC_Ckt" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/Output_CMOS_inverter_depends_on_charging_dischargin_of_capacitor.png" alt="Output_CMOS_inverter_depends_on_charging_dischargin_of_capacitor" width="80%">
</div>

- Propagation Delay as a function of Drain Current

<div align="center" >
  <img src="./week3_assets/Propagation_delay_fn_of_Id.png" alt="Propagation_delay_fn_of_Id" width="80%">
</div>
 
- OCV Derates

<div align="center" >
  <img src="./week3_assets/OCV_Derates.png" alt="OCV_Derates" width="80%">
</div>

---

## 20. OCV-Based Setup Timing Analysis

OCV applies fixed derate factors to model local variations:
- Setup worst-case: late data path and launch clock; early capture clock
- Derates enlarge pessimism for robustness; captured in STA as early/late derate tables for rise/fall on data/clock paths.

---

## 21. Setup Timing Analysis After Pessimism Removal

Pessimism Removal (e.g., CPPR—Common Path Pessimism Removal) reduces double-counting on shared clock segments between launch and capture.

---

## 22. OCV-Based Hold Timing Analysis

Hold worst-case: early launch clock and data path; late capture clock. Apply early derates to launch/data and late derates to capture clock to stress the min-time check. 

---

## 23. Hold Timing Analysis After Pessimism Removal

As with setup, remove common-path pessimism on the clock network for min checks, but confirm that early/late selections remain worst-case after CPPR. Ensure that any recovered slack is still robust over jitter/uncertainty budgets and across all MMMC corners.

---

## Fixing Violations 
- Setup paths:
  - Reduce data-path delay (logic restructuring, upsizing, Vt swap), reduce net RC (buffering/re-route), leverage useful skew, review uncertainty.
- Hold paths:
  - Increase data-path delay (insert buffers/detours), avoid introducing new setup failures, check skew/uncertainty consistency across corners.
- Clock gating and async checks:
  - Verify enable arrival relative to clock gating cell requirements; validate async reset release windows for recovery/removal with uncertainty included.

</details>

<details>
  <summary>GLS VSD Baby SOC</summary>

# VSD BabySoC: RTL to Post-Synthesis Verification

This document provides a comprehensive walkthrough of the synthesis and post-synthesis verification flow for the `vsdbabysoc` System-on-Chip. The project integrates the `rvmyth` RISC-V core with two analog IPs, `avsddac` (a DAC) and `avsdpll` (a PLL), using an open-source toolchain featuring Yosys for synthesis and Icarus Verilog for simulation.

The primary goal is to convert the high-level RTL design into a gate-level netlist based on the SkyWater 130nm technology library and to verify that the resulting netlist is functionally equivalent to the original design.

## Pre-requisites:

- Install Yosys, Icarus Verilog, and GTKWave. Refer to their respective documentation for installation instructions in WEEK_0.
- Install Sandpiper for Verilog generation from TL-Verilog: rvmyth is in TL-Verilog.

  - **Command**:

    ```bash
    pip3 install pyyaml click sandpiper-saas
    sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/
    ```

  - **Note**: The `rvmyth.v` file is generated from `rvmyth.tlv` using Sandpiper. This file is included in the synthesis and simulation processes.

  - **Files**:
    ```bash
    path/to/VSDBabySoC$ tree -a
    .
    ├── assets
    │   ├── chip_stats.png
    │   ├── comp_pre_vs_post_synth_sim_2.png
    │   ├── comp_pre_vs_post_synth_sim.png
    │   ├── vsdbabysoc.yosys_show.png
    │   ├── waveform_post_synth_sim.png
    │   ├── waveform_pre_synth_sim_2.png
    │   └── waveform_pre_synth_sim.png
    ├── reports
    │   ├── logs
    │   │   └── synthesis_yosis.log
    │   └── vsdbabysoc_netlist.v
    ├── simulation
    │   ├── dump.vcd
    │   ├── post_synth_sim.out
    │   ├── pre_synth_sim.out
    │   └── pre_synth_sim.vcd
    └── src
        ├── gds
        │   ├── avsddac.gds
        │   └── avsdpll.gds
        ├── gls_model
        │   ├── primitives.v
        │   └── sky130_fd_sc_hd.v
        ├── include
        │   ├── sandpiper_gen.vh
        │   ├── sandpiper.vh
        │   ├── sp_default.vh
        │   └── sp_verilog.vh
        ├── layout_conf
        │   ├── rvmyth
        │   │   ├── config.tcl
        │   │   └── pin_order.cfg
        │   └── vsdbabysoc
        │       ├── config.tcl
        │       ├── macro.cfg
        │       └── pin_order.cfg
        ├── lef
        │   ├── avsddac.lef
        │   └── avsdpll.lef
        ├── lib
        │   ├── avsddac.lib
        │   ├── avsdpll.lib
        │   └── sky130_fd_sc_hd__tt_025C_1v80.lib
        ├── module
        │   ├── avsddac_stub.v
        │   ├── avsddac.v
        │   ├── avsdpll_stub.v
        │   ├── avsdpll.v
        │   ├── clk_gate.v
        │   ├── pseudo_rand_gen.sv
        │   ├── pseudo_rand.sv
        │   ├── rvmyth_gen.v
        │   ├── rvmyth.tlv
        │   ├── rvmyth.v
        │   ├── testbench.rvmyth.post-routing.v
        │   ├── testbench.v
        │   └── vsdbabysoc.v
        ├── script
        │   ├── sta.conf
        │   ├── verilog_to_lib.pl
        │   ├── yosys_wo_lc_shell.ys
        │   └── yosys.ys
        └── sdc
            ├── vsdbabysoc_layout.sdc
            └── vsdbabysoc_synthesis.sdc
    ``` 

## 1. Pre-Synthesis Verification (RTL)

Before synthesis, the RTL design was verified using a testbench (`testbench.v`) that instantiates the `vsdbabysoc` module and applies a series of stimulus to validate its functionality. The simulation was run using Icarus Verilog, and the waveform was inspected in GTKWave to ensure correct operation.

  - **Command**:

    ```bash
    iverilog -o simulation/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module
    ```

  - **Execution**:

    ```bash
    cd simulation
    ./pre_synth_sim.out
    gtkwave pre_synth_sim.vcd
    ```

  - **Results**: The RTL simulation waveform confirmed that the CPU could successfully write to the DAC and that the PLL locked correctly, indicating that the design was functionally sound before synthesis.

  <div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/gtkwave_Output_Pre_Synth_Sim.png" alt="gtkwave_Output_Pre_Synth_Sim" width="80%">
</div>


## 2. Synthesis Flow Overview

The synthesis process converts the abstract RTL (Verilog) code into a physical implementation composed of standard logic gates from a specific technology library (PDK).

  - **Inputs**:
      - RTL Verilog files (`vsdbabysoc.v`, `rvmyth.v`)
      - Analog IP stubs (`avsddac_stub.v`, `avsdpll_stub.v`)
      - Technology timing libraries (`.lib` files)
  - **Tool**: `Yosys` Open SYnthesis Suite
  - **Output**: A gate-level netlist (`vsdbabysoc_netlist.v`)

## 3. Key Concept: Black-Boxing Analog IPs

A critical step in a mixed-signal SoC flow is handling the analog macros (`avsddac`, `avsdpll`). The synthesis tool cannot create these blocks from digital gates. Therefore, we treat them as **"black boxes"**.

  - **For Simulation**: We use the full behavioral Verilog models to verify functionality.
  - **For Synthesis**: We provide **stub files**. These are empty Verilog modules that only declare the module's name and its input/output ports. This tells Yosys what the IP's interface looks like without trying to synthesize its internal (and non-synthesizable) logic.

#### `src/module/avsddac_stub.v`

```verilog
// Stub module for the avsddac analog IP.
// This is a black box for synthesis. Do not add logic here.

module avsddac (
   output OUT,
   input [9:0] D,
   input VREFH,
   input VREFL
);

// Intentionally empty

endmodule
```

#### `src/module/avsdpll_stub.v`

```verilog
// Stub module for the avsdpll analog IP.
// This is a black box for synthesis. Do not add logic here.

module avsdpll (
   output reg  CLK,
   input  wire VCO_IN,
   input  wire ENb_CP,
   input  wire ENb_VCO,
   input  wire REF
);

// Intentionally empty

endmodule
```

## The step-by-step execution plan for running the commands manually:
---
### **Step 1: Load the Top-Level Design and Supporting Modules**
```bash
yosys
```

Inside the Yosys shell, run:
```yosys
read_verilog /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/vsdbabysoc.v
read_verilog -I /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/include /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/rvmyth.v
read_verilog -I /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/include /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/clk_gate.v

```

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/reading_modules.png" alt="reading_modules" width="80%">
</div>

---

### **Step 2: Load the Liberty Files for Synthesis**

Inside the same Yosys shell, run:

```yosys
read_liberty -lib /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/lib/avsddac.lib
read_liberty - lib /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/lib/avsdpll.lib
read_liberty -lib /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/lib/sky130_fd_sc_hd_tt_025C_1v80.lib
```

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/reading_lib.png" alt="reading_lib" width="80%">
</div>

---

### **Step 3: Run Synthesis Targeting `vsdbabysoc`**
```yosys
synth -top vsdbabysoc
```
<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/synth-top.png" alt="synth-top" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/stats.png" alt="synth-top-stats" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/stats2.png" alt="synth-top-stats2" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/stats3.png" alt="synth-top-stats3" width="80%">
</div>


---

### **Step 4: Map D Flip-Flops to Standard Cells**
```yosys
dfflibmap -liberty /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/dff_libmap.png" alt="dff_libmap" width="80%">
</div>

---

### **Step 5: Perform Optimization and Technology Mapping**
```yosys
opt
abc -liberty /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib -script +strash;scorr;ifraig;retime;{D};strash;dch,-f;map,-M,1,{D}
```

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/abc_liberty.png" alt="abc_liberty" width="80%">
</div>


---

### **Step 6: Perform Final Clean-Up and Renaming**
```yosys
flatten
setundef -zero
clean -purge
rename -enumerate
```

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/flatten_clean.png" alt="flatten_clean" width="80%">
</div>

---

### **Step 7: Check Statistics**
```yosys
stat
```

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/statistics_after_flat.png" alt="statistics_after_flat" width="80%">
</div>

---

### **Step 8: Write the Synthesized Netlist**
```yosys
write_verilog -noattr /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v
```

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/write_verilog.png" alt="write_verilog" width="80%">
</div>

---


### **Step 1: Compile the Testbench**

Run the following `iverilog` command to compile the testbench:

```bash
iverilog -DFUNCTIONAL -DUNIT_DELAY=#1 -o /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/output/post_synth_sim/post_synth_sim.out /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/gls_model/primitives.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/gls_model/sky130_fd_sc_hd.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/avsdpll.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/avsddac.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/testbench.v
```
---

### **Step 2: Navigate to the Post-Synthesis Simulation Output Directory**
```bash
cd output/post_synth_sim/
```
---
### **Step 3: Run the Simulation**

```bash
./post_synth_sim.out
```
---
### **Step 4: View the Waveforms in GTKWave**

```bash
gtkwave dump.vcd
```
---

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/gtkwave_gls.png" alt="gtkwave_gls" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/gtkwave_Output_Pre_Synth_Sim.png" alt="gtkwave_Output_Pre_Synth_Sim" width="80%">
</div>

So the GLS Simulation for Pre and Post synthesis of VSD Baby SOC matches and so the design is complete and ready.

## 4. The Debugging Journey: Errors & Resolutions

The path to a successful synthesis involved solving several key issues.

### Error 1: Missing Include File

  - **Symptom**: Yosys failed during RTL parsing with the error:
    ```
    ERROR: Can't open include file 'sp_verilog.vh /*_\SV */'!
    ```
  - **Root Cause**: The `rvmyth` core uses `include` directives to import Verilog header files (`.vh`). Yosys was not aware of the `src/include/` directory where these files are located.
  - **Resolution**: Add the `-I src/include` flag to required `read_verilog` commands in the Yosys script. This tells Yosys to add that directory to its search path for header files.

### Error 2: Architectural & Port Mismatches

  - **Symptom**: After fixing the include path, synthesis failed during the hierarchy check with port mismatch errors, such as:
    ```
    ERROR: Module 'avsddac' ... does not have a port named 'VREFH'.
    ```
  - **Root Cause**: The initial version of `avsddac_stub.v` and `avsdpll_stub.v` had fundamental architectural flaws. The instantiations of, `avsddac`, and `avsdpll` were using entirely incorrect port names and connections that did not match the actual module definitions. For example, `avsddac` was instantiated with ports that did not exist in its definition.This was due to use of placeholder names and stub modules for the analog IPs.
  - **Resolution**: The corrected version instantiates all IPs with their proper port names and adds the necessary glue logic for the CPU to control the DAC via a simple memory-mapped scheme. This aligned the top-level design with the actual IP interfaces.

## 5. Post-Synthesis Verification (GLS)

To ensure the synthesis process did not alter the design's logic, we perform a **Gate-Level Simulation (GLS)**. This involves simulating the generated netlist with the same testbench used for the original RTL.

  - **Command**: The `iverilog` command for GLS is more complex, as it requires the Verilog models for the Sky130 standard cells.

    ```bash
     iverilog -DFUNCTIONAL -DUNIT_DELAY=#1 -o /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/output/post_synth_sim/post_synth_sim.out /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/gls_model/primitives.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/gls_model/sky130_fd_sc_hd.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/avsdpll.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/avsddac.v /home/divyam_goyal/Documents/week_2_BabySoc/VSDBabySoC/src/module/testbench.v
    ```

  - **Execution**:

    ```bash
    cd simulation
    ./post_synth_sim.out
    gtkwave dump.vcd
    ```

  - **Results**: The GLS waveform was compared against the pre-synthesis (RTL) waveform. They were found to be identical, confirming that the synthesized netlist is functionally correct.

  <div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/gtkwave_gls.png" alt="gtkwave_gls" width="80%">
</div>

<div align="center" >
  <img src="./week3_assets/gls_VSDBabySOC/gtkwave_Output_Pre_Synth_Sim.png" alt="gtkwave_Output_Pre_Synth_Sim" width="80%">
</div>

## 6. Conclusion

This process successfully transformed the `vsdbabysoc` RTL design into a verified, synthesizable gate-level netlist. The debugging journey highlighted the importance of correctly handling IP integration, from Verilog header paths to precise port-matching in hierarchical designs. The identical pre- and post-synthesis simulation results provide high confidence in the netlist, which is now ready for the Physical Design (Place and Route) stage.

</details>


</details>

---

Introduces Static Timing Analysis (STA), including setup/hold timing, timing arcs, slack calculation, and path analysis.
You also learn how STA ensures timing closure of real designs and how timing reports are interpreted.

<details>
    <summary><span style="color:#3FA9F5;">Week 4 - Spice Simulations </span></summary>

# SPICE Simulations

# NgspiceSky130 – CMOS Inverter Design and Simulation

A comprehensive guide for **CMOS inverter design, simulation, and analysis** using **Ngspice with the SkyWater 130nm PDK (sky130)**.  
This repository covers theoretical foundations and practical SPICE implementations — including NMOS, PMOS, and CMOS inverter behavior across resistive, saturation, and velocity saturation regions.

---

### Basics of NMOS Drain Current (Id) vs. Drain-to-Source Voltage (Vds)

#### 1. Introduction to Circuit Design and SPICE Simulations
SPICE (Simulation Program with Integrated Circuit Emphasis) is an industry-standard circuit simulator that models transistor-level and system-level behavior.  
It allows circuit designers to verify functionality, noise margins, power, and timing before fabrication.

<div align="center" >
  <img src="./week4_assets/CMOS_inverter.png" alt="CMOS_inverter" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/Spice_sim.png" alt="Spice_sim" width="80%">
</div>

**Why Do We Need SPICE Simulations?**
- Enables transistor-level verification of non-linear and parasitic effects.
- Reduces fabrication iterations by simulating circuits virtually.
- Helps measure design metrics such as noise margin, power, and delay.
- Power Aware CTS and Delay Table

<div align="center" >
  <img src="./week4_assets/DelayTable.png" alt="DelayTable" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/QuesWeShouldAns.png" alt="QuesWeShouldAns" width="80%">
</div>

**NMOS as Basic Element in Circuit Design** \
An NMOS transistor acts as a switch controlled by gate voltage $(V_g)$. When $(V_{gs} > V_t)$, a conduction channel is formed between source and drain.

**Key Components:**

- P-Substrate: Base material (p-type silicon)
- N⁺ Source/Drain: Heavily doped n-type regions for current conduction
- Gate Oxide (SiO₂): Thin insulating layer for capacitive control
- Gate Electrode: Poly-Si or metal; controls inversion layer formation
- Isolation Oxide: Prevents electrical cross-talk between devices
- Body Terminal (B): Connected to substrate, usually tied to ground

**Operation Principle:**

Applying gate-to-source voltage Vgs > Vt forms a conductive channel between source and drain
Channel acts as voltage-controlled resistor in linear region
Current saturates when channel pinches off near drain

<div align="center" >
  <img src="./week4_assets/NMOS.png" alt="NMOS" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/Threshold_Voltage.png" alt="Threshold_Voltage" width="80%">
</div>

**Strong Inversion and Threshold Voltage** \
Strong inversion starts when $(V_{gs})$ exceeds threshold voltage $(V_t)$.  
$(V_t)$ is affected by:
- Substrate doping concentration
- Oxide thickness
- Source-body bias

<div align="center" >
  <img src="./week4_assets/Body_gnd.png" alt="Body_gnd" width="80%">
</div>

**Threshold with Substrate Potential**
Increasing substrate potential raises $(V_t)$:
$$ V_t = V_{t0} + \gamma (\sqrt{|-2\phi_f + V_{sb}|} - \sqrt{|-2\phi_f|}) $$

<div align="center" >
  <img src="./week4_assets/Vsb_applied.png" alt="Vsb_applied" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/Threshold_Voltage_equation.png" alt="Threshold_Voltage_equation" width="80%">
</div>

---

#### NMOS Resistive and Saturation Region of Operation

**Resistive (Linear) Region**  
For small $(V_{ds})$:
$$ I_d = \mu_n C_{ox} \frac{W}{L}((V_{gs}-V_t)V_{ds} - \frac{V_{ds}^2}{2}) $$

<div align="center" >
  <img src="./week4_assets/Resistive_Operation.png" alt="Resistive_Operation" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/firstOrderAnalysis.png" alt="firstOrderAnalysis" width="80%">
</div>


**Drift Current Theory**  

<div align="center" >
  <img src="./week4_assets/DriftCurrent.png" alt="DriftCurrent" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/velocity.png" alt="velocity" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/DrainCurrent_Eqn.png" alt="DrainCurrent_Eqn" width="80%">
</div>

**Linear Region Model**  

<div align="center" >
  <img src="./week4_assets/ConditionforVds_in_linear_region.png" alt="ConditionforVds_in_linear_region" width="80%">
</div>


**Pinch-Off and Saturation**  

<div align="center" >
  <img src="./week4_assets/PinchOffCondition.png" alt="PinchOffCondition" width="80%">
</div>

**Channel length Modulation**  

<div align="center" >
  <img src="./week4_assets/ChannelLength_modulation.png" alt="ChannelLength_modulation" width="80%">
</div>


**Spice Set Up**  
Spice Model Parameters + Spice Netlist = Spice Software which generates the required waveforms for the analysis

<div align="center" >
  <img src="./week4_assets/spice_software.png" alt="spice_software" width="80%">
</div>

### SPICE NETLIST
- Creating SPICE NETLIST \
A SPICE netlist provides a text description of a circuit.
<div align="center" >
  <img src="./week4_assets/nmos_symbol.png" alt="nmos_symbol" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/Netlist_syntax.png" alt="Netlist_syntax" width="80%">
</div>

**1. Element Declarations (Circuit Components)** \
The first letter of the element name defines its type. Node 0 represents ground.

| Type                | Syntax Format                                             | Example                                     | Description                                                                                                                                     |
| ------------------- | --------------------------------------------------------- | ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Resistor            | `Rname N+ N- Value`                                       | `R1 1 2 1k`                                 | Defines a resistor between Node 1 and Node 2 with a value of 1 kOhm.                                                                            |
| Capacitor           | `Cname N+ N- Value`                                       | `Cload 3 0 100pF`                           | Defines a capacitor between Node 3 and Ground with a value of 100 pF.                                                                           |
| Inductor            | `Lname N+ N- Value`                                       | `Lmatch 4 5 10nH`                           | Defines an inductor between Node 4 and Node 5 with a value of 10 nH.                                                                            |
| Voltage Source      | `Vname N+ N- [Type]`                                      | `Vdd 10 0 DC 3.3V`                          | Defines a DC voltage source (Vdd) of 3.3V between Node 10 and Ground.                                                                           |
| Current Source      | `Iname N+ N- [Type]`                                      | `Ib bias 0 DC 1mA`                          | Defines a DC current source (Ib) flowing from `bias` to Ground.                                                                                 |
| Diode               | `Dname N_anode N_cathode ModelName`                       | `D1 2 3 D_generic`                          | Defines a diode using a specific `.MODEL` called `D_generic`.                                                                                   |
| N-Channel MOS       | `Mname N_drain N_gate N_source N_bulk ModelName [params]` | `M1 out in 0 0 NMOS_mod W=10u L=0.5u`       | Defines an NMOS transistor (M1) with drain, gate, source, and bulk connected to specific nodes, using parameters like width (W) and length (L). |
| P-Channel MOS       | `Mname N_drain N_gate N_source N_bulk ModelName [params]` | `M2 vout vin vdd vdd PMOS_mod W=20u L=0.5u` | Defines a PMOS transistor (M2) using a PMOS model name. Note that bulk is typically tied to VDD.                                                |
| Subcircuit Instance | `Xname Node1 Node2 ... SubName`                           | `Xamp 1 2 3 0 OPAMP_VFB`                    | Instantiates a complex subcircuit block named `OPAMP_VFB` into the main schematic.                                                              |

**2. Control Statements (Directives)** \
These lines always start with a period (.) and control how the simulation runs.

| Directive          | Syntax Format                            | Description                                                                                                                          |
| ------------------ | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Transient Analysis | `.TRAN Tstep Tstop [Tstart [Tmax]]`      | Performs time-domain simulation for a specified duration (Tstop), saving data points every Tstep.                                    |
| AC Analysis        | `.AC [LIN/DEC/OCT] Npoints Fstart Fstop` | Performs frequency-domain simulation (e.g., for finding gain and phase margin) using linear, decade, or octave sweep types.          |
| DC Analysis        | `.DC Source Start Stop Step`             | Performs a DC sweep, varying an input source (voltage or current) through a range of values.                                         |
| Model Definition   | `.MODEL ModelName Type (params)`         | Defines specific electrical characteristics for diodes (`D`), NMOS (`NMOS`), PMOS (`PMOS`), etc., using foundry-provided parameters. |
| Subcircuit Def     | `.SUBCKT SubName Node1 Node2 ...`        | Starts the definition of a hierarchical block (like an operational amplifier).                                                       |
| End Subcircuit     | `.ENDS [SubName]`                        | Ends the subcircuit definition block.                                                                                                |
| End Netlist        | `.END`                                   | The final line in every SPICE netlist file, indicating the end of the description.                                                   |

**3. Syntax Modifiers and Units** \
SPICE accepts standard engineering multipliers for convenience.

| Unit/Modifier | Value                                  |
|---------------|----------------------------------------|
| `p`           | Pico $(10^{−12})$                      |
| `n`           | Nano $(10^{−9})$                       |
| `u`           | Micro $(10^{−6})$                      |
| `m`           | Milli $(10^{−3})$                      |
| `k`           | Kilo $(10^{3})$                        |
| `Meg` or `M`  | Mega $(10^{6})$ (Note:  `m`  is milli) |
| `G`           | Giga $(10^{9})$                        |

<div align="center" >
  <img src="./week4_assets/Technology_File.png" alt="Technology_File" width="80%">
</div>

## Regions of Operation

| Region | Condition | Drain Current | Application |
|--------|-----------|---------------|-------------|
| **Cutoff** | Vgs < Vt | Id ≈ 0 | OFF state, logic '0' |
| **Linear** | Vgs > Vt, Vds < Vgs-Vt | Id ∝ Vds | Resistive switches, transmission gates |
| **Saturation** | Vgs > Vt, Vds ≥ Vgs-Vt | Id ∝ (Vgs-Vt)² | Amplifiers, current sources |


### Lab1

**Objective:** Observe linear and saturation regions for a long-channel NMOS device.

Steps 1. Clone the repository 
```bash 
git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
```
Steps 2. Open the file `day1_nfet_idvds_L2_W5.spice` in design folder

```bash 
vim ./design/day1_nfet_idvds_L2_W5.spice
```

```
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description



XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=5 l=2

R1 n1 in 55

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run
display
setplot dc1
.endc

.end
```
Steps 3. Use ngspice for simulating `day1_nfet_idvds_L2_W5.spice` 
``` 
ngspice day1_nfet_idvds_L2_W5.spice
```
``` 
gnuplot plot -vdd#branch
```
<div align="center" >
  <img src="./week4_assets/day1_nfet_gnuplot.png" alt="day1_nfet_gnuplot" width="80%">
</div>


**Observations:**
- **Linear Region**: Current increases linearly with Vds for low Vds
- **Saturation Region**: Current plateaus at higher Vds
- **Family of Curves**: Different Vgs values produce different saturation currents
- **Peak Current**: ≈ 410 μA at Vgs = 1.8V, Vds = 1.8V

## Analysis 

Linear Region and Saturation regions can be clearly observed.
<div align="center" >
  <img src="./week4_assets/analysis_w1.8u_L1.2u.png" alt="analysis_w1.8u_L1.2u" width="80%">
</div>

### Effect of Velocity Saturation
Velocity saturation is a short-channel effect in MOS transistors where the velocity of charge carriers (electrons or holes) in the channel stops increasing linearly with the electric field and instead reaches a maximum, constant value, known as the saturation velocity
<div align="center" >
  <img src="./week4_assets/ShortChannelMos.png" alt="ShortChannelMos" width="80%">
</div>

### Id Vgs Comparison with short channel MOS

<div align="center" >
  <img src="./week4_assets/idvgs_Comparison.png" alt="idvgs_Comparison" width="80%">
</div>

Slope becomes linear on higher Vgs in Short Channel MOS due to Velocity Saturation Effects.

<div align="center" >
  <img src="./week4_assets/velocity_sat_effect.png" alt="velocity_sat_effect" width="80%">
</div>

### Drain Current Expression including Velocity Saturation Effect

<div align="center" >
  <img src="./week4_assets/derivingDrainCurrent_including_velocity_sat_effect.png" alt="derivingDrainCurrent_including_velocity_sat_effect" width="80%">
</div>

### Generalised Drain Current Expression for all operating modes

<div align="center" >
  <img src="./week4_assets/operation_modes.png" alt="operation_modes" width="80%">
</div>

### Peak Current reduces due to Velocity Saturation Effect

<div align="center" >
  <img src="./week4_assets/PeakCurrent_reduces_dueto_vel_sat_effect.png" alt="PeakCurrent_reduces_dueto_vel_sat_effect" width="80%">
</div>


## Lab2

**Objective:** Extract threshold voltage from transfer characteristics.

Steps 1. Clone the repository 
```bash 
git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
```
Steps 2. Open the file `day2_nfet_idvds_L015_W039.spice` in design folder

```bash 
vim ./design/day2_nfet_idvds_L015_W039.spice
```

```
*Model Description
.param temp=27


*Including sky130 library files
.lib "sky130_fd_pr/models/sky130.lib.spice" tt


*Netlist Description



XM1 Vdd n1 0 0 sky130_fd_pr__nfet_01v8 w=0.39 l=0.15

R1 n1 in 55

Vdd vdd 0 1.8V
Vin in 0 1.8V

*simulation commands

.op
.dc Vdd 0 1.8 0.1 Vin 0 1.8 0.2

.control

run
display
setplot dc1
.endc

.end
```
Steps 3. Use ngspice for simulating `day2_nfet_idvds_L015_W039.spice` 
``` 
ngspice day2_nfet_idvds_L015_W039.spice
```
``` 
gnuplot plot -vdd#branch
```

<div align="center" >
  <img src="./week4_assets/day2_nfet_idvds_gnuplot.png" alt="day2_nfet_idvds_gnuplot" width="80%">
</div>

Similarly we do it for `day2_nfet_idvgs_L015_W039.spice`

<div align="center" >
  <img src="./week4_assets/day2_nfet_idvgs_gnuplot.png" alt="day2_nfet_idvgs_gnuplot" width="80%">
</div>

The results from above simulation show the effect of velocity saturation as discussed above. Forming of Linear slope and Peak Current Reduction when we compare it with `day1_nfet_idvds_L2_W5.spice`.


**Threshold Voltage Extraction:**
1. Plot Id vs Vgs on linear scale
2. Find maximum slope (gm,max) point
3. Extrapolate linear portion to Id = 0 axis
4. Intersection gives Vt ≈ 0.4-0.5V for SKY130 typical corner

**Observations:**
- **Subthreshold Region**: Exponential Id increase below Vt
- **Strong Inversion**: Quadratic Id dependence above Vt
- **Body Effect**: Vt increases with positive Vsb

**Comparative Analysis:**

| Parameter | Long Channel (W=5µm, L=2µm) | Short Channel (W=0.39µm, L=0.15µm) |
|-----------|----------------------------|-------------------------------------|
| W/L Ratio | 2.5 | 2.6 |
| Peak Id | ≈ 410 μA | ≈ 210 μA |
| Saturation Mode | Classical pinch-off | Velocity saturated |
| Vds,sat | ≈ Vgs - Vt | << Vgs - Vt |
| Transconductance | Higher | Degraded (~50%) |

**Key Observations:**
- Despite similar W/L ratio, short-channel device has **~50% lower current**
- Saturation occurs at **lower Vds**
- Curves show **less pronounced saturation** region
- **Velocity saturation** is the dominant current-limiting mechanism


### MOS Characteristics

<div align="center" >
  <img src="./week4_assets/MOS_Characteristics.png" alt="MOS_Characteristics" width="80%">
</div>

### CMOS Inverter

A CMOS inverter uses complementary PMOS and NMOS transistors:

**Structure:**
- PMOS source → VDD, drain → Vout
- NMOS source → GND, drain → Vout
- Gates tied together → Vin
- Drains tied together → Vout

**Logic Operation:**

| Vin | PMOS | NMOS | Vout |
|-----|------|------|------|
| 0V (Low) | ON | OFF | VDD (High) |
| VDD (High) | OFF | ON | 0V (Low) |

<div align="center" >
  <img src="./week4_assets/Cmos_inverter_ckt.png" alt="Cmos_inverter_ckt" width="80%">
</div>

**PMOS and NMOS Ids vs Vds Curves**

<div align="center" >
  <img src="./week4_assets/pmos_nmos.png" alt="pmos_nmos" width="80%">
</div>

**Changing_vgsP_in_terms_of_Vin**

<div align="center" >
  <img src="./week4_assets/changing_vgsP_in_terms_of_Vin.png" alt="changing_vgsP_in_terms_of_Vin" width="80%">
</div>

**Creating Load Curves**

<div align="center" >
  <img src="./week4_assets/LoadCurve_Pmos.png" alt="LoadCurve_Pmos" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/LoadCurve_Nmos.png" alt="LoadCurve_Nmos" width="80%">
</div>

### CMOS_VTC(VoltageTransferCharacteristics)

<div align="center" >
  <img src="./week4_assets/CMOS_VTC(VoltageTransferCharacteristics).png" alt="VoltageTransferCharacteristics" width="80%">
</div>

### SPICE Deck

<div align="center" >
  <img src="./week4_assets/Spice_deck.png" alt="Spice_deck" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/spice_netlist_cmos_inverter.png" alt="spice_netlist_cmos_inverter" width="80%">
</div>

### Analysis

<div align="center" >
  <img src="./week4_assets/spice_sim_analysis_diff_wL_pmos_in_cmos_inverter.png" alt="spice_sim_analysis_diff_wL_pmos_in_cmos_inverter" width="80%">
</div>


### Lab 3

Use ngspice for simulating `day3_inv_vtc_Wp084_Wn036.spice` 
``` 
ngspice day3_inv_vtc_Wp084_Wn036.spice
```
``` 
gnuplot plot -vdd#branch
```

<div align="center" >
  <img src="./week4_assets/day3_cmos_vtc_gnuplot.png" alt="day3_inv_vtc_Wp084_Wn036.spice" width="80%">
</div>

**Switching Threshold Extraction:**

Method 1: Graphical
- Plot Vout vs Vin
- Plot line y = x
- Intersection gives Vm

Method 2: SPICE Measurement
```spice
.measure dc vm when out=in
```

**Expected Vm ≈ 0.89-0.90V** (close to VDD/2 = 0.9V)

Similarly we do it for `day3_inv_tran_Wp084_Wn036.spice`

<div align="center" >
  <img src="./week4_assets/day3_cmos_tran_gnuplot.png" alt="day3_cmos_tran_gnuplot" width="80%">
</div>


## **Delay Measurements:**

## **Transient Delay Extraction — Detailed Calculation**

**Context:** values from ngspice output (screenshot):
- First rising-crossing point: `x0 = 2.15167e-09` s, `y0 = 0.902174`
- Second rising-crossing point: `x0 = 2.485e-09` s, `y0 = 0.901087`
- First falling-crossing candidate: `x0 = 4.05e-09` s, `y0 = 0.9`
- Second falling-crossing candidate: `x0 = 4.33488e-09` s, `y0 = 0.898913`


---

## **Definitions**
- **Rise propagation delay (tpLH)** ≈ time difference between the two specified rising crossing points:
tp_rise = t2_rise − t1_rise


- **Fall propagation delay (tpHL)** ≈ time difference between the two specified falling crossing points:
tp_fall = t2_fall − t1_fall



---

## **Numeric calculation (SI units)**

### Rise delay
t1_rise = 2.15167e-09 s
t2_rise = 2.48500e-09 s

tp_rise = t2_rise - t1_rise
= 2.48500e-09 - 2.15167e-09
= 3.3333000000000013e-10 s



Convert to convenient units:
tp_rise = 3.3333e-10 s = 333.33 ps = 0.33333 ns


### Fall delay
t1_fall = 4.05000e-09 s
t2_fall = 4.33488e-09 s

tp_fall = t2_fall - t1_fall
= 4.33488e-09 - 4.05000e-09
= 2.8488000000000036e-10 s



Convert to convenient units:
tp_fall = 2.8488e-10 s = 284.88 ps = 0.28488 ns



---

## **Summary (final values)**
- Rise propagation delay (tp_rise) = 3.3333e-10 s = 333.33 ps

- Fall propagation delay (tp_fall) = 2.8488e-10 s = 284.88 ps


### **Threshold Voltage Shift**

<div align="center" >
  <img src="./week4_assets/Switching_Threshold.png" alt="Switching_Threshold" width="80%">
</div>

**Deriving Threshold Voltage**

<div align="center" >
  <img src="./week4_assets/Deriving_Vm.png" alt="Deriving_Vm" width="80%">
</div>

**Varying_wL_pmos_for_setting_Vm**

<div align="center" >
  <img src="./week4_assets/Varying_wL_pmos_for_setting_Vm.png" alt="Varying_wL_pmos_for_setting_Vm" width="80%">
</div>

**Variation_in_Rise,Fall_delay_for_diff_wL**

<div align="center" >
  <img src="./week4_assets/Variation_in_Rise,Fall_delay_for_diff_wL.png" alt="Variation_in_Rise,Fall_delay_for_diff_wL" width="80%">
</div>

**Understanding Clock Tree Buffer**

<div align="center" >
  <img src="./week4_assets/ClockBuffer.png" alt="ClockBuffer" width="80%">
</div>

**Input Output Characteristics**

<div align="center" >
  <img src="./week4_assets/IO_char_with_finiteSlope.png" alt="IO_char_with_finiteSlope" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/Actual_IO_Char_inverter.png" alt="Actual_IO_Char_inverter" width="80%">
</div>

## Noise Margin Fundamentals

**Definition:** Noise margin quantifies the maximum noise voltage that can be tolerated at the input while maintaining valid logic levels at the output.

**Why Noise Margins Matter:**
- Real circuits experience noise from:
  - Crosstalk between wires
  - Power supply variations
  - Electromagnetic interference (EMI)
  - Substrate coupling
- Adequate noise margins ensure reliable operation
- Critical for yield and reliability in production

## Noise Margin Voltage Parameters

**Four Critical Voltages:**

1. **VOH (Output High Voltage):**
   - Maximum output voltage when output is logic '1'
   - Ideally VOH = VDD

2. **VOL (Output Low Voltage):**
   - Minimum output voltage when output is logic '0'
   - Ideally VOL = 0V

3. **VIH (Input High Voltage):**
   - Minimum input voltage recognized as logic '1'
   - Defined where dVout/dVin = -1 (unity gain point) on falling edge

4. **VIL (Input Low Voltage):**
   - Maximum input voltage recognized as logic '0'
   - Defined where dVout/dVin = -1 (unity gain point) on rising edge

<div align="center" >
  <img src="./week4_assets/NMH_NML.png" alt="NMH_NML" width="80%">
</div>

## Noise Margin Definitions

**High-Level Noise Margin (NMH):**
```
NMH = VOH - VIH
```
- Maximum noise voltage that can be added to a high input
- Ensures output remains valid high

**Low-Level Noise Margin (NML):**
```
NML = VIL - VOL
```
- Maximum noise voltage that can be subtracted from a low input
- Ensures output remains valid low

**Ideal Values:**
- For VDD = 1.8V: NMH = NML ≈ 0.6-0.7V
- Larger noise margins → better noise immunity
- Both margins should be roughly equal for symmetric behavior



<div align="center" >
  <img src="./week4_assets/Noise_Margin_summary.png" alt="Noise_Margin_summary" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/effectOf_wL_on_noiseMargin.png" alt="effectOf_wL_on_noiseMargin" width="80%">
</div>

## Graphical Extraction Method

**Step-by-Step Procedure:**

1. Plot VTC (Vout vs Vin)
2. Calculate slope: dVout/dVin at each point
3. Find points where slope = -1:
   - Left unity-gain point → VIL
   - Right unity-gain point → VIH
4. Read VOL and VOH from VTC extremes
5. Calculate NML = VIL - VOL
6. Calculate NMH = VOH - VIH

### Lab 4

**Objective:** Extract complete noise margin parameters for standard inverter.

**Device Sizing:**
- Wn = 0.36 μm, Ln = 0.15 μm
- Wp = 1.00 μm, Lp = 0.15 μm
- Wp/Wn = 2.78

Use ngspice for simulating `day4_inv_noisemargin_wp1_wn036.spice` 
``` 
ngspice day4_inv_noisemargin_wp1_wn036.spice
```
``` 
gnuplot plot -vdd#branch
```

<div align="center" >
  <img src="./week4_assets/day4_cmos_noiseM_gnuplot.png" alt="day4_cmos_noiseM_gnuplot" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/NoiseMargin_calc.png" alt="NoiseMargin_calc" width="80%">
</div>

## Power Supply Variation

<div align="center" >
  <img src="./week4_assets/PowerSupplyVariation.png" alt="PowerSupplyVariation" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/spice_sim_powerSupply_scaling.png" alt="spice_sim_powerSupply_scaling" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/advantage_disadvantages_powerSupplyScaling.png" alt="advantage_disadvantages_powerSupplyScaling" width="80%">
</div>

### Lab 5 Part 1

Use ngspice for simulating `day5_inv_supplyvariation_Wp1_Wn036.spice` 
``` 
ngspice day5_inv_supplyvariation_Wp1_Wn036.spice
```
``` 
gnuplot plot -vdd#branch
```

<div align="center" >
  <img src="./week4_assets/characteristics_for_diff_supply_voltages.png" alt="characteristics_for_diff_supply_voltages" width="80%">
</div>

## Variation due to Etching Process

<div align="center" >
  <img src="./week4_assets/Variation_due_to_etching_process.png" alt="Variation_due_to_etching_process" width="80%">
</div>

## Variation due to Oxide Thickness

<div align="center" >
  <img src="./week4_assets/Variation_due_to_oxide_thickness.png" alt="Variation_due_to_oxide_thickness" width="80%">
</div>

## Device Variations

<div align="center" >
  <img src="./week4_assets/spice_sim_device_variations.png" alt="spice_sim_device_variations" width="80%">
</div>

<div align="center" >
  <img src="./week4_assets/static_behavior_analysis_spice_sim.png" alt="static_behavior_analysis_spice_sim" width="80%">
</div>

### Lab 5 Part 2

Use ngspice for simulating `day5_inv_devicevariation_wp7_wn042.spice` 
``` 
ngspice day5_inv_devicevariation_wp7_wn042.spice
```
``` 
gnuplot plot -vdd#branch
```

<div align="center" >
  <img src="./week4_assets/day5_cmos_device_variation_gnuplot.png" alt="day5_cmos_device_variation_gnuplot" width="80%">
</div>


</details>

---

Covers analog/digital circuit behavior using SPICE simulations with ngspice.
You simulate basic circuits, understand transient/AC/DC analysis, and learn how device characteristics impact real silicon behavior.

<details>
    <summary><span style="color:#3FA9F5;">Week 5 - OpenROAD Flow-Setup Floorplan Placement </span></summary>

# OpenROAD installation guide

**OpenROAD** is an open-source, fully automated RTL-to-GDSII flow for digital integrated circuit (IC) design. It supports synthesis, floorplanning, placement, clock tree synthesis, routing, and final layout generation. OpenROAD enables rapid design iterations, making it ideal for academic research and industry prototyping.
---

### 📚 Contents

  - [Steps to Install OpenROAD and Run GUI](#steps-to-install-openroad-and-run-gui)
    - [1. Clone the OpenROAD Repository](#1-clone-the-openroad-repository)
    - [2. Run the Setup Script](#2-run-the-setup-script)
    - [3. Build OpenROAD](#3-build-openroad)
    - [4. Verify Installation](#4-verify-installation)
    - [5. Run the OpenROAD Flow](#5-run-the-openroad-flow)
    - [6. Launch the GUI](#6-launch-the-graphical-user-interface-gui-to-visualize-the-final-layout)
- [ORFS Directory Structure and File Formats](#orfs-directory-structure-and-file-formats)


### `Steps to Install OpenROAD and Run GUI`

### 1. Clone the OpenROAD Repository

```bash
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
```

<div align="center" >
  <img src="./week5_assets/git_clone.png" alt="git_clone" width="80%">
</div>

### 2. Run the Setup Script

```bash
sudo ./setup.sh
```

<div align="center" >
  <img src="./week5_assets/sudo_setup.png" alt="sudo_setup" width="80%">
</div>

### 3. Build OpenROAD

```bash
./build_openroad.sh --local --openroad-args "-DENABLE_TESTS=OFF" 
```

<div align="center" >
  <img src="./week5_assets/build.png" alt="build" width="80%">
</div>


### 4. Verify Installation

```bash
source ./env.sh
yosys -help  
openroad -help
```

<div align="center" >
  <img src="./week5_assets/verify_install_1.png" alt="verify_install_1" width="80%">
</div>


<div align="center" >
  <img src="./week5_assets/verify_install_2.png" alt="verify_install_2" width="80%">
</div>

### 5. Run the OpenROAD Flow

```bash
cd flow
make
```

<div align="center" >
  <img src="./week5_assets/cd_flow.png" alt="cd_flow" width="80%">
</div>

<div align="center" >
  <img src="./week5_assets/make.png" alt="make" width="80%">
</div>

### 6. Launch the graphical user interface (GUI) to visualize the final layout

```bash
 make gui_final
```

<div align="center" >
  <img src="./week5_assets/make_gui.png" alt="make_gui" width="80%">
</div>

✅ Installation Complete! We can now explore the full RTL-to-GDSII flow using OpenROAD.

### `ORFS Directory Structure and File formats`

OpenROAD-flow-scripts/

```plaintext
├── OpenROAD-flow-scripts             
│   ├── docker           -> It has Docker based installation, run scripts and all saved here
│   ├── docs             -> Documentation for OpenROAD or its flow scripts.  
│   ├── flow             -> Files related to run RTL to GDS flow  
|   ├── jenkins          -> It contains the regression test designed for each build update
│   ├── tools            -> It contains all the required tools to run RTL to GDS flow
│   ├── etc              -> Has the dependency installer script and other things
│   ├── setup_env.sh     -> Its the source file to source all our OpenROAD rules to run the RTL to GDS flow
```
Inside the `flow/` Directory

```plaintext
├── flow           
│   ├── design           -> It has built-in examples from RTL to GDS flow across different technology nodes
│   ├── makefile         -> The automated flow runs through makefile setup
│   ├── platform         -> It has different technology note libraries, lef files, GDS etc 
|   ├── tutorials        
│   ├── util            
│   ├── scripts                 
```

<div align="center" >
  <img src="./week5_assets/final.png" alt="final" width="80%">
</div>

</details>

---

Walkthrough of OpenROAD setup and its early physical design stages: reading netlists, technology files, and initializing the floorplan.
You work with IO placement, tapcell insertion, PDN generation, and standard-cell placement using automated OpenROAD optimization.

<details>
    <summary><span style="color:#3FA9F5;"> Week 6 - Physical Design using OpenLANE </span></summary>

## 🚀 Introduction

### Why Open-Source EDA Matters

EDA tools are critical for the design, simulation, and verification of integrated circuits. Open-source EDA democratizes chip design, removing licensing barriers and fostering collaborative innovation. Sky130 and OpenLANE are two of the most accessible platforms for learning and building digital ICs from scratch.

***

## 🛠️ How to Talk to Computers

### Abstraction in Digital Design

Computers operate on instructions at varying abstraction levels—software (high-level languages, OS), hardware (logic gates, flip-flops), and everything between. The pathway from code to silicon involves translation steps, each handled by specialized tools and flows.

- **Software Applications → Hardware:** Higher-level programs are converted by compilers and synthesis tools into logic that can be etched onto silicon.

***

## 🧩 Introduction to RISC-V

RISC-V is an open, royalty-free instruction set architecture (ISA) designed for flexibility and extensibility.

- **Modular ISA:** Core instructions (base integer set) plus optional extensions for multiplication, atomicity, floating-point, etc.
- **Open Ecosystem:** Enables customization for research, education, embedded systems, or high-performance applications.
- **Support for Multiple Privilege Modes:** From lightweight embedded cores to feature-rich platforms supporting operating systems.

***

## 🏗️ SoC Design and OpenLANE

### Components of Digital ASIC Design

Open-source digital ASIC design typically involves:

- **RTL (Register Transfer Level):** The hardware description code, generally written in Verilog or VHDL.
- **Synthesis:** Converts RTL to gate-level netlist using logic libraries.
- **Floorplanning and Placement:** Organizes logic elements physically on the die.
- **Routing:** Connects standard cells with metal interconnects.

### RTL2GDS Flow (Simplified)

- **RTL (Verilog) → Synthesis → Floorplan → Placement → Routing → GDSII (final tapeout layout).**
- OpenLANE automates this flow specifically for Sky130 PDK, handling each step and offering hooks for manual intervention or advanced configuration.

***

## ⚙️ OpenLANE and Sky130 PDK

### OpenLANE Overview

OpenLANE is an open-source digital ASIC flow built around the Sky130 PDK.

- Automated digital design flow (RTL → GDSII).
- Integrates multiple tools (yosys for synthesis, Magic for layout viewing, OpenROAD utilities for placement/routing).

### Key Features

- Scriptable and repeatable design flow.
- Detailed directory structure for managing design, scripts, reports, and resulting layout files.

***

## 📂 Exploring OpenLANE Directory Structure

OpenLANE organizes projects into directories for:

- **Designs:** User circuits and configurations.
- **Runs:** Per-design execution logs, results, and intermediate files.
- **PDK:** Standard cell libraries, LEF/DEF files, rules, etc.
- **Reports:** Timing, area, and metrics for each design step.

***

## 🏞️ Floorplanning and Placement

### Good Floorplan vs. Bad Floorplan

A well-thought-out floorplan improves routability, performance, and power integrity:

- **Utilization Factor:** Balances logic density.
- **Aspect Ratio:** Ensures die fits target packaging.
- **Pre-placed Cells & Decoupling Capacitors:** Ensures robust power delivery.
- **Pin Placement:** Affects timing, congestion, and ease of testing.

### Running Floorplan in OpenLANE

- OpenLANE scripts automate much of the setup; designers review output for errors and optimization opportunities.

***

## 🧪 Cell Design and Characterization

### From Schematic to Spice

- **CMOS Inverter as a Reference:** Begin with basic gates (inverter), create layout in Magic, simulate in ngspice.
- **Characterization:** Extract delay, power, threshold characteristics from SPICE simulations.

### Key Timing Parameters

- **Propagation Delay:** Time required for signal to propagate through a gate.
- **Transition Time:** Slope of the output signal, critical for performance.
- **Timing Thresholds:** Voltage levels at which logic state transitions occur.

***

## 🖥️ Sky130 Tech and Layout Labs

- **Magic Tool Use:** Layout editing and view, DRC checks, LEF/DEF generation from Magic-extracted layouts.
- **PDK Files:** Provide standardized models and DRC rules for process-correct design.
- **Troubleshooting Labs:** Real-world exercises like fixing DRC errors, adjusting poly/metal spacing, and interpreting Magic errors.

***

## 🕑 Timing Analysis and Clock Tree

### OpenSTA for Timing

- **Clock Setup/Hold Analysis:** Ensures that clocked elements (FFs/latches) receive valid signals at the correct time.
- **Post-synthesis/CTS Analysis:** Includes routing details and real clock network delays.

### TritonCTS for Clock Synthesis

- **H-Tree Algorithm:** Balances clock signal distribution across chip.
- **Signal Integrity:** Crosstalk and shielding methods to prevent spurious behavior.

***

## 🛣️ Routing, DRC, and Final Tapeout

### TritonRoute

- Handles detailed interconnect routing, respects routing guides, and honors DRC constraints.
- Outputs DRC-clean GDSII files for fabrication.

### Power Distribution Network (PDN)

- **Generation of Power Straps**
- Robust connection between standard cells and chip-level supply rails.

***

## 📝 Useful References

- RISC-V ISA official site
- OpenLANE: https://github.com/The-OpenROAD-Project/OpenLane
- SkyWater Sky130: https://github.com/google/skywater-pdk
- Magic VLSI: http://opencircuitdesign.com/magic/

***

</details>

---

Full RTL-to-GDS flow using OpenLANE: synthesis, floorplanning, placement, CTS, routing, DRC, and GDS export.
You explore the OpenLANE directory structure, configuration files, and understand how PnR automation produces manufacturable layouts on Sky130.

<details>
    <summary><span style="color:#3FA9F5;"> Week 7 - OpenRoad VSDBabySOC Physical Design </span></summary>

# VSDBabySoC Physical Design – Using OpenROAD

This README documents the complete, step‑by‑step flow I followed to complete **Task 13** of the VSD Physical Design workshop using **OpenROAD Flow Scripts (ORFS)**.

It includes **all explanations**, **all fixes**, and **all commands** needed to successfully run the VSDBabySoC design from RTL → GDS.


---

# 📘 Overview

The goal of this task is to take the **VSDBabySoC RTL**, integrate it inside **OpenROAD Flow Scripts**, and then run through:

* Synthesis (Yosys)
* Floorplan
* Placement
* Clock Tree Synthesis
* Global Routing
* Detailed Routing
* GDS Export

Because VSDBabySoC contains **custom analog blocks** (DAC, PLL), the `.lib` files are provided. However, they need **modifications** to be compatible with OpenROAD.

This README explains everything cleanly.

---

# 🗂 Repository Structure


```
OpenRoad-VSDBabySOC-Physical-Design/
│
├── designs/
│   └── sky130hd/
│       └── vsdbabysoc/
│           ├── config.mk
│           ├── src/
│           │   └── vsdbabysoc.v
│           └── lib/
│               ├── avsddac.lib
│               └── avsdpll.lib     ← (fixed version)
│
├── assets/      
└── README.md
```

---

# 🚀 Step 1 – Clone OpenROAD Flow Scripts

```bash
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
cd OpenROAD-flow-scripts
```

Install dependencies:

```bash
sudo ./etc/DependencyInstaller.sh
```

Build ORFS tools:

```bash
./build_openroad.sh --local
```

This builds:

* Yosys
* OpenROAD
* TritonRoute
* KLayout export

---

# 🧩 Step 2 – Add VSDBabySoC to ORFS

Inside:

```
flow/designs/sky130hd/
```

create a folder:

```
vsdbabysoc/
```

### Add Files:

```
vsdbabysoc/
│── config.mk
│── src/
│   └── vsdbabysoc.v
└── lib/
    ├── avsddac.lib
    └── avsdpll.lib
```

### ⚠ IMPORTANT: Fixing the Liberty Files

The PLL library (`avsdpll.lib`) originally had **invalid `//` comments**, which Liberty format does NOT support.

Liberty supports only:

```c
/* comment */
```

So I fixed the file by converting all `//` lines to proper block comments.
This prevents the `STA-0164` syntax error during floorplan.

---

### Config file 
Now, create a config.mk file whose contents are shown below:

```shell
export DESIGN_NICKNAME = vsdbabysoc
export DESIGN_NAME = vsdbabysoc
export PLATFORM    = sky130hd

# export VERILOG_FILES_BLACKBOX = $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/IPs/*.v
# export VERILOG_FILES = $(sort $(wildcard $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/*.v))
# Explicitly list the Verilog files for synthesis
export VERILOG_FILES = $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/vsdbabysoc.v \
                       $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/rvmyth.v \
                       $(DESIGN_HOME)/src/$(DESIGN_NICKNAME)/clk_gate.v

export SDC_FILE      = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)/vsdbabysoc_synthesis.sdc

export vsdbabysoc_DIR = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)

export VERILOG_INCLUDE_DIRS = $(wildcard $(vsdbabysoc_DIR)/include/)
# export SDC_FILE      = $(wildcard $(vsdbabysoc_DIR)/sdc/*.sdc)
export ADDITIONAL_GDS  = $(wildcard $(vsdbabysoc_DIR)/gds/*.gds.gz)
export ADDITIONAL_LEFS  = $(wildcard $(vsdbabysoc_DIR)/lef/*.lef)
export ADDITIONAL_LIBS = $(wildcard $(vsdbabysoc_DIR)/lib/*.lib)
# export PDN_TCL = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)/pdn.tcl

# Clock Configuration (vsdbabysoc specific)
# export CLOCK_PERIOD = 20.0
export CLOCK_PORT = CLK
export CLOCK_NET = $(CLOCK_PORT)

# Floorplanning Configuration (vsdbabysoc specific)
export FP_PIN_ORDER_CFG = $(wildcard $(DESIGN_DIR)/pin_order.cfg)
# export FP_SIZING = absolute

export DIE_AREA   = 0 0 1600 1600
export CORE_AREA  = 20 20 1590 1590

# Placement Configuration (vsdbabysoc specific)
export MACRO_PLACEMENT_CFG = $(wildcard $(DESIGN_DIR)/macro.cfg)
export PLACE_PINS_ARGS = -exclude left:0-600 -exclude left:1000-1600: -exclude right:* -exclude top:* -exclude bottom:*
# export MACRO_PLACEMENT = $(DESIGN_HOME)/$(PLATFORM)/$(DESIGN_NICKNAME)/macro_placement.cfg

export TNS_END_PERCENT = 100
export REMOVE_ABC_BUFFERS = 1

# Magic Tool Configuration
export MAGIC_ZEROIZE_ORIGIN = 0
export MAGIC_EXT_USE_GDS = 1

# CTS tuning
export CTS_BUF_DISTANCE = 600
export SKIP_GATE_CLONING = 1

# export CORE_UTILIZATION=0.1  # Reduce this value to allow more whitespace for routing.
```

# 🔨 Step 3 – Run Synthesis

```bash
cd flow
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk synth
```

### Common Error I Faced

```
No rule to make target '.../vsdbabysoc.v'
```

This means the design RTL wasn’t in the correct path.

✔ FIX:
Place the RTL at:

```
flow/designs/src/vsdbabysoc/vsdbabysoc.v
```

<div align="center" >
  <img src="./week7_assets/make_synth_1.png" alt="make_synth_1" width="80%">
</div>


<div align="center" >
  <img src="./week7_assets/make_synth_2.png" alt="make_synth_2" width="80%">
</div>

### Synth check txt 

<div align="center" >
  <img src="./week7_assets/synth_check_txt.png" alt="synth_check_txt" width="80%">
</div>

### Synth statistics

<div align="center" >
  <img src="./week7_assets/synth_stats.png" alt="synth_stats" width="80%">
</div>

---

# 📐 Step 4 – Floorplan

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk floorplan
```

### Error I Encountered

```
[ERROR STA-0164] syntax error in avsdpll.lib
```

✔ FIX: Replace all `//` with `/* ... */` in `avsdpll.lib`.

<div align="center" >
  <img src="./week7_assets/make_floorplan_1.png" alt="make_floorplan_1" width="80%">
</div>


<div align="center" >
  <img src="./week7_assets/make_floorplan_2.png" alt="make_floorplan_2" width="80%">
</div>


---

# 🖥 Step 5 – Floorplan GUI

Launch GUI mode:

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_floorplan
```

<div align="center" >
  <img src="./week7_assets/make_gui_floorplan_1.png" alt="make_gui_floorplan_1" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_gui_floorplan_2.png" alt="make_gui_floorplan_2" width="80%">
</div>

---

# 🧱 Step 6 – Placement

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk place
```

<div align="center" >
  <img src="./week7_assets/make_place_1.png" alt="make_place_1" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_place_2.png" alt="make_place_2" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_place_3.png" alt="make_place_3" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_place_4.png" alt="make_place_4" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_place_5.png" alt="make_place_5" width="80%">
</div>

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk gui_place
```

<div align="center" >
  <img src="./week7_assets/make_gui_place.png" alt="make_gui_place" width="80%">
</div>

### Heat Map

<div align="center" >
  <img src="./week7_assets/heatmap_1.png" alt="heatmap_1" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/heatmap_2.png" alt="heatmap_2" width="80%">
</div>


---

# ⏱ Step 7 – Clock Tree Synthesis (CTS)

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk cts
```

<div align="center" >
  <img src="./week7_assets/make_cts_1.png" alt="make_cts_1" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_cts_2.png" alt="make_cts_2" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/cts_final_report.png" alt="cts_final_report" width="80%">
</div>

---

# 🚦 Step 8 – Global Routing 

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk route
```

<div align="center" >
  <img src="./week7_assets/make_route_1.png" alt="make_route_1" width="80%">
</div>

<div align="center" >
  <img src="./week7_assets/make_route_2.png" alt="make_route_2" width="80%">
</div>

### Error I Encountered

```
[ERROR GRT-0116] Global routing finished with congestion.
```

This means routing resources were insufficient.

### ✔ FIX 1 — Inspect Congestion

Open GUI:

```
make ... gui_floorplan
```

Enable congestion map:

```
Route → Congestion Map
```

### ✔ FIX 2 — Reduce Core Utilization

In `config.mk`, set:

```makefile
CORE_UTILIZATION = 0.60
```

This spreads cells further apart → lowers routing congestion.

### Re-run Routing

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk route
```

---

# ✨ Step 9 – Detailed Routing

Once congestion is solved, TritonRoute completes successfully.


---

# 🏁 Step 10 – GDSII Export

```bash
make DESIGN_CONFIG=./designs/sky130hd/vsdbabysoc/config.mk finish
```

Output GDS is located at:

```
results/sky130hd/vsdbabysoc/base/vsdbabysoc.gds
```


---

# 📦 Summary of All Fixes

| Error                 | Cause                           | Fix                                 |
| --------------------- | ------------------------------- | ----------------------------------- |
| RTL not found         | Wrong path                      | Place RTL in `flow/designs/src/...` |
| `STA-0164`            | Liberty file used `//` comments | Convert to `/* ... */`              |
| GUI heatmap issues    | Old OpenROAD version            | Use GUI menus, not Tcl              |
| `GRT-0116` congestion | High core utilization           | Lower to 0.60 and inspect heatmap   |
| GUI warnings          | Missing Wayland plugin          | Safe to ignore                      |

---

# 📚 References

* OpenROAD Project: [https://github.com/The-OpenROAD-Project](https://github.com/The-OpenROAD-Project)
* Sky130 PDK Documentation
* VSD Physical Design Course

---

# 🎯 Final Note

This walkthrough documents a **complete, real-world Physical Design flow** using the VSDBabySoC design. It includes every debugging step I faced so others can easily reproduce the setup.

Feel free to fork this repo or adapt the steps for your own custom designs.


</details>

---

Apply the complete OpenROAD PD flow specifically to the VSDBabySoC RISC-V SoC.
You run macro placement, congestion analysis, CTS tuning, routing, and generate the final layout for the BabySoC top module.

<details>
    <summary><span style="color:#3FA9F5;"> Week 8 - RISC-V core multi corner STA analysis </span></summary>

# RISC-V_core_multi_corner_sta_analysis
---

### Week-3 (Post-Synthesis) vs Week-8 (Post-Route) Timing Comparison  
### Using OpenLANE, OpenROAD & OpenSTA

---

## 1. Overview

This repository documents the complete **Static Timing Analysis (STA)** of the **riscv_core** design across multiple **PVT corners** using:

- **OpenLANE** for synthesis, placement and routing  
- **OpenROAD** for loading post-route ODB and extracting SPEF  
- **OpenSTA** for multi-corner timing analysis  

The objective is to compare:

- **Week-3:** Post-Synthesis STA (ideal interconnect, no parasitics)  
- **Week-8:** Post-Route STA (real parasitics from SPEF, routed design)  

This report includes:  
✔ Timing tables  
✔ All PVT corner results  
✔ Graphs (WNS, TNS, Setup, Hold)  
✔ Detailed explanation of timing behavior after routing  

---

## 2. Environment & Inputs

### Software
- OpenLANE  
- OpenROAD  
- OpenSTA (v2.7.0)  
- Sky130 HD PDK (Liberty timing models)

### Required Files
- `riscv_core.odb` — Post-route OpenROAD database  
- `riscv_core.nom.spef` — Extracted parasitics  
- `riscv_base_post_cts.sdc` — Timing constraints  
- 16 × Liberty files across TT, FF, SS corners  

---

## 3. Post-Route STA TCL Script (Week-8)

This script loads the post-route design, SPEF parasitics, all 16 PVT Liberty files, runs setup/hold analysis for each corner, and writes WNS/TNS/Worst-Slack results.

```tcl
set list_of_lib_files(1)  "sky130_fd_sc_hd__tt_025C_1v80.lib"
set list_of_lib_files(2)  "sky130_fd_sc_hd__tt_100C_1v80.lib"
set list_of_lib_files(3)  "sky130_fd_sc_hd__ff_100C_1v65.lib"
set list_of_lib_files(4)  "sky130_fd_sc_hd__ff_100C_1v95.lib"
set list_of_lib_files(5)  "sky130_fd_sc_hd__ff_n40C_1v56.lib"
set list_of_lib_files(6)  "sky130_fd_sc_hd__ff_n40C_1v65.lib"
set list_of_lib_files(7)  "sky130_fd_sc_hd__ff_n40C_1v76.lib"
set list_of_lib_files(8)  "sky130_fd_sc_hd__ff_n40C_1v95.lib"
set list_of_lib_files(9)  "sky130_fd_sc_hd__ss_100C_1v40.lib"
set list_of_lib_files(10) "sky130_fd_sc_hd__ss_100C_1v60.lib"
set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
set list_of_lib_files(14) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
set list_of_lib_files(15) "sky130_fd_sc_hd__ss_n40C_1v60.lib"
set list_of_lib_files(16) "sky130_fd_sc_hd__ss_n40C_1v76.lib"

set run_tag $::env(RUN_TAG)

set_cmd_units -time ns -capacitance pF -current mA -voltage V -resistance kOhm -distance um
set_units -time ns -capacitance pF -current mA -voltage V -resistance kOhm -distance um

read_db /openlane/designs/riscv_core/runs/$run_tag/results/routing/riscv_core.odb
read_spef /openlane/designs/riscv_core/runs/$run_tag/results/final/spef/multicorner/riscv_core.nom.spef
current_design

if {![file exists ./sta_output]} {
    file mkdir ./sta_output
}

for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {

    read_liberty $::env(PDK_ROOT)/sky130A/libs.ref/sky130_fd_sc_hd/lib/$list_of_lib_files($i)
    read_sdc /openlane/designs/riscv_core/src/riscv_base_post_cts.sdc

    if {$i == 1} {
        exec echo -n > ./sta_output/sta_wns.txt
        exec echo -n > ./sta_output/sta_tns.txt
        exec echo -n > ./sta_output/sta_worst_max_slack.txt
        exec echo -n > ./sta_output/sta_worst_min_slack.txt
    }

    exec echo -ne "$list_of_lib_files($i)    " >> ./sta_output/sta_worst_max_slack.txt
    report_worst_slack -max >> ./sta_output/sta_worst_max_slack.txt

    exec echo -ne "$list_of_lib_files($i)    " >> ./sta_output/sta_worst_min_slack.txt
    report_worst_slack -min >> ./sta_output/sta_worst_min_slack.txt

    exec echo -ne "$list_of_lib_files($i)    " >> ./sta_output/sta_tns.txt
    report_tns >> ./sta_output/sta_tns.txt

    exec echo -ne "$list_of_lib_files($i)    " >> ./sta_output/sta_wns.txt
    report_wns >> ./sta_output/sta_wns.txt
}

exit
````

---

## 4. Week-3 Timing Results (Post-Synthesis)

### Week 3 Summary Table

<div align="center" >
  <img src="./week8_assets/week_3/week3_sta_data.png" alt="week3_sta_data" width="80%">
</div>

### Worst Hold Slack

<div align="center" >
  <img src="./week8_assets/week_3/WHS.jpg" alt="Worst_Hold_Stack" width="80%">
</div>

### Worst Setup Slack

<div align="center" >
  <img src="./week8_assets/week_3/WSS.jpg" alt="Worst_Setup_Stack" width="80%">
</div>

### WNS

<div align="center" >
  <img src="./week8_assets/week_3/WNS.jpg" alt="WNS" width="80%">
</div>

### TNS

<div align="center" >
  <img src="./week8_assets/week_3/TNS.jpg" alt="TNS" width="80%">
</div>

---

## 5. Week-8 Timing Results (Post-Route)

### Week-8 Summary Table

<div align="center" >
  <img src="./week8_assets/week_8/riscv_core_sta_across_pvt.png" alt="riscv_core_sta_across_pvt" width="80%">
</div>


### Worst Setup Slack

<div align="center" >
  <img src="./week8_assets/week_8/worst_setup_slack.png" alt="worst_setup_slack" width="80%">
</div>

### Worst Hold Slack

<div align="center" >
  <img src="./week8_assets/week_8/worst_hold_slack.png" alt="worst_hold_slack" width="80%">
</div>

### WNS

<div align="center" >
  <img src="./week8_assets/week_8/wns.png" alt="wns" width="80%">
</div>


### TNS

<div align="center" >
  <img src="./week8_assets/week_8/tns.png" alt="tns" width="80%">
</div>

---

## 6. Week-3 vs Week-8 Comparison Table

| PVT Corner   | WNS (W3) | WNS (W8) | TNS (W3) | TNS (W8)   | WHS (W3) | WHS (W8) | Setup (W3) | Setup (W8) |
| ------------ | -------- | -------- | -------- | ---------- | -------- | -------- | ---------- | ---------- |
| tt_025C_1v80 | 0        | -7.4403  | 0        | -7477.7690 | 0.3096   | -2.8904  | 1.106      | -7.4403    |
| ff_100C_1v65 | 0        | -6.4158  | 0        | -6048.2212 | 0.2491   | -2.9509  | 2.4466     | -6.4158    |
| ff_100C_1v95 | 0        | -4.7488  | 0        | -4155.6294 | 0.196    | -3.0040  | 3.8366     | -4.7488    |
| ff_n40C_1v56 | 0        | -6.2602  | 0        | -6312.1372 | 0.2915   | -2.9085  | 1.127      | -6.2602    |
| ff_n40C_1v65 | 0        | -5.1682  | 0        | -5053.1134 | 0.2551   | -2.9449  | 2.1219     | -5.1682    |
| ff_n40C_1v76 | 0        | -4.2362  | 0        | -4004.4890 | 0.2243   | -2.9757  | 2.9919     | -4.2362    |
| ss_100C_1v40 | -13.0402 | -27.9272 | -7518    | -32115     | 0.9053   | -2.2947  | -13.0402   | -27.9272   |
| ss_100C_1v60 | -6.2777  | -18.2358 | -2911    | -20155     | 0.6420   | -2.5580  | -6.2777    | -18.2358   |
| ss_n40C_1v28 | -52.9031 | -51.4456 | -36775   | -72154     | 1.8296   | -1.8463  | -52.9031   | -51.4456   |
| ss_n40C_1v35 | -33.1984 | -37.8016 | -23279   | -51688     | 1.3475   | -1.9116  | -33.1984   | -37.8016   |
| ss_n40C_1v40 | -24.6564 | -31.4799 | -17173   | -42060     | 1.1249   | -2.0751  | -24.6564   | -31.4799   |
| ss_n40C_1v44 | -19.961  | -27.4636 | -13603   | -36005     | 0.9909   | -2.2091  | -19.961    | -27.4636   |
| ss_n40C_1v76 | -3.9606  | -12.3806 | -1905    | -14293     | 0.5038   | -2.6962  | -3.9606    | -12.3806   |

---

## 7. Interpretation of Results

### Post-Route Timing Is Worse

Because Week-8 includes **actual interconnect parasitics** from SPEF:

* Wire capacitance
* Wire resistance
* Via parasitics
* Coupling between adjacent nets

These increase the delay of long critical paths.

### Setup Slack Degradation

Worst corners (SS) show large setup violations:

* Slow silicon
* Low voltage
* High wire RC
* Long routes

### Hold Slack Degradation

Fast corners show worst hold slack:

* Fast silicon
* Higher supply voltage
* Shorter delays → races between FF stages

### SS_n40C_x corners dominate setup

As expected: slow + low voltage = maximum delay.

### FF_n40C_x corners dominate hold

Fast + low temperature = shortest delays.

---

## 8. Final Summary

* Week-3 timing is optimistic because it ignores routed RC parasitics.
* Week-8 timing is realistic and shows significant degradation in both setup and hold slack.
* SS corners show severe setup violations due to large wire delays.
* FF corners produce hold-time violations due to short propagation delays.
* Post-route timing highlights the need for buffering, cell upsizing, and net restructuring before sign-off.

---

</details>

---

Perform multi-corner STA (TT, SS, FF) for the RISC-V core to evaluate timing robustness across Process-Voltage-Temperature variations.
You analyze worst-case slack, path failures, and verify timing closure for tapeout readiness.


## 🙏 **Acknowledgment**
I am thankful to [**Kunal Ghosh**](https://github.com/kunalg123) and Team **[VLSI System Design (VSD)](https://vsdiat.vlsisystemdesign.com/)** for the opportunity to participate in the ongoing **RISC-V SoC Tapeout Program**.  

I also acknowledge the support of **RISC-V International**, **India Semiconductor Mission (ISM)**, **VLSI Society of India (VSI)**, and [**Efabless**](https://github.com/efabless) for making this initiative possible.  
<div align="center">

