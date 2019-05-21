# Case Study for 32-bit Pipelined CPU design with New ALU Architecture
Introduction:

The objective of the final project for ECE429 is to understand 32-bit Pipelined Central Processing Unit (CPU). Pipelined means that the circuit can handle more than one 32-bit word at a time. We will use the techniques from the past 9 labs and the introduced software to implement the circuit design. This requires revisiting past labs. 

The lab is broken into two Case Studies. In Case Study-1 we investigate different types of adders in our CPU and examine the path delay associated with each adder over a variety of operations. In Case Study-2 we redesign the Arithmetic Logic unit (ALU) as a 32-bit 

Pre-Lab/Theory:

Our designed CPU consists of a 32x32 Memory File, Arithmetic Logic Unit (ALU) and several 2-1 MUXs along with the inputs and various encoders. The below block diagram from the lab manual shows the relationships between the signals and components in the lab.

Implementation:
Case Study 1 32-bit CPU design with Different Adders:

In the first case study we follow the standard cell based flow for different adders implemented in our CPU. We explore the Carry Ripple Adder, Carry Look-ahead Adder, Carry Skip Adder, and the Carry Select Adder. The source code for each of the adders along with the test bench is provided and we simply need to perform an RTL simulation, Logic synthesis and Post Synthesis Simulation and Place and Route and Post P&R Simulation for each of the different possible CPU configurations. 

First we need to detect any bugs in the adder design by running the test bench. Each of the adders is already integrated into the CPU design in the Verilog source file. The generated warning is the result of missing “.over(over)” placeholders as predefined by the function but these are unnecessary. The test bench file validates the store, read, addition and subtraction functionality of each of the CPU configurations. 

After validation we follow IIT-ECE429 ASIC flow for the logical and physical synthesis. For the logical synthesis we use Synopsis DC with a desired clock frequency of 30 MHZ.

Finally for case study 1 we perform a Place & Route and Post-P&R Simulation using Cadence SOC Encounter. The layout is automatically generated and we can check the timing report. We modify the test bench to build in some custom operations detailed 
in the chart above and in the code snippets below.

The Path delay measurements, if correct, make sense. As the operations get more intensive the delay time grows. For example adding numbers requires less than adding letters. The reason for which the adders rank in terms of delay is unclear but they are all relatively close.

Case Study-2: 32-bit CPU design with New ALU Architecture:

In the second case study we are designing the structure of an alternative ALU. Similar to the first case study we are provided with the template source file. First we must write the Verilog code structure for 32 one_bit_comp, 16 mux_4to2, 8 mux_4to2, 4 mux_4to2, 2 mux_4to2, and 1 mux_4to2. After completing the Verilog file we need to write a test bench for the specified operations.

Again similar to Case Study-1 we run the RTL simulation and validate the output. Next we follow the steps of logical and physical synthesis. Again we run a post-synthesis simulation and explore the timing delays

Conclusion:

The final project walked through two different experiments modifying the computer architecture of a 32-bit CPU. First we modified the type of adder used in the CPU switching between four different adders. Next we changed the ALU Verilog file to support a 32-bit design. The project was the culmination of semesters worth of training in VLSI simulation tools and provided a challenging final task.
