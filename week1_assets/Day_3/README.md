# Day 3: Combinational and Sequential Optimization
Combinational and sequential optimization are distinct approaches in digital circuit design, each addressing the specific characteristics of combinational logic and sequential logic to improve a circuit's performance, area, and power consumption.

<div align="center">
  <img src="./assets/Combinational_vs_Sequential_ckt.png" alt="Combinational_vs_Sequential_ckt" width="70%">
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
  <img src="./assets/Cloning.png" alt="Cloning" width="70%">
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
  <img src="./assets/opt_check_verilogFile_optimised_by_AND_gate.png" alt="opt_check_verilogFile_optimised_by_AND_gate" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_check_optimisation.png" alt="opt_check_optimisation" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_opt_check.png" alt="yosys_opt_check" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_check_2_verilogFile_optimised_by_OR_gate.png" alt="opt_check_2_verilogFile_optimised_by_OR_gate" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_check_2_optimisation.png" alt="opt_check_2_optimisation" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_opt_check_2.png" alt="yosys_opt_check_2" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_chec_3_verilogFile.png" alt="opt_chec_3_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_check_3_optimisation.png" alt="opt_check_3_optimisation" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_opt_check_3.png" alt="yosys_opt_check_3" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_check_4_verilogFile.png" alt="opt_check_4_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./assets/opt_check_4_optimisation.jpg" alt="opt_check_4_optimisation" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_opt_check_4.png" alt="yosys_opt_check_4" width="80%">
</div>

<div align="center">
  <img src="./assets/multiple_module_opt_verilogFile.png" alt="multiple_module_opt_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_multiple_module_opt_Flatten_clean-purge.png" alt="yosys_multiple_module_opt_Flatten_clean" width="80%">
</div>

<div align="center">
  <img src="./assets/multiple_module_opt_2_verilogFile.png" alt="multiple_module_opt_2_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_multiple_module_opt_2_Flatten_clean-purge.png" alt="yosys_multiple_module_opt_2_Flatten_clean" width="80%">
</div>

<div align="center">
  <img src="./assets/gtkwave_dff_const_1.png" alt="gtkwave_dff_const_1" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_dff_const_1.png" alt="yosys_dff_const_1" width="80%">
</div>

<div align="center">
  <img src="./assets/dff_const1_2.png" alt="dff_const1_2" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_dff_const_2.png" alt="yosys_dff_const_2" width="80%">
</div>

<div align="center">
  <img src="./assets/gtkwave_dff_const_3.png" alt="gtkwave_dff_const_3" width="80%">
</div>

<div align="center">
  <img src="./assets/dff_const3.png" alt="dff_const3" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_dff_const_3.png" alt="yosys_dff_const_3" width="80%">
</div>

<div align="center">
  <img src="./assets/gtkwave_dff_const_4.png" alt="gtkwave_dff_const_4" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_dff_const_4.png" alt="yosys_dff_const_4" width="80%">
</div>

<div align="center">
  <img src="./assets/gtkwave_dff_const_5.png" alt="gtkwave_dff_const_5" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_dff_const_5.png" alt="yosys_dff_const_5" width="80%">
</div>

<div align="center">
  <img src="./assets/counter_opt_verilogFile.png" alt="counter_opt_verilogFile" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_counter_opt.png" alt="yosys_counter_opt" width="80%">
</div>

<div align="center">
  <img src="./assets/verilog_file_new_counter_opt.png" alt="verilog_file_new_counter_opt" width="80%">
</div>

<div align="center">
  <img src="./assets/yosys_new_counter_opt.png" alt="yosys_new_counter_opt" width="80%">
</div>
