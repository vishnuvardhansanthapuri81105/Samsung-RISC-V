OBSERVING WAVEFORMS IN GTKWAVE FOR RISC-V SIMULATION:

After running the Verilog simulation, the results are saved in a VCD (Value Change Dump) file. This file contains all the signal changes that happened during the simulation. To view these signals as waveforms, we use GTKWave, a tool that helps us analyze and debug our design.

![Screenshot 2025-02-09 111738](https://github.com/user-attachments/assets/813792f2-3359-4c71-bbe4-bb48cbd30b6c)







![Screenshot 2025-02-09 111620](https://github.com/user-attachments/assets/d6b29a4e-2536-48d8-aa4f-b3867248fe90)



Steps to View Waveforms in GTKWave
1. Run the Simulation

First, make sure you have already run the simulation using:
./iiitb_rv32i

This command generates a file called iiitb_rv32i.vcd, which stores the signal changes.

2. Open GTKWave

To view the waveforms, enter:
gtkwave iiitb_rv32i.vcd

This will open GTKWave and load the saved signal data.


3. Understanding the GTKWave Window

Once GTKWave opens, you will see different sections:
Signals Panel (left side): Lists all the signals from your simulation.
Waveform Viewer (right side): Shows how signals change over time.
Time Scale (top): Represents time steps in the simulation.


4. Adding Signals to the Waveform Viewer


To observe how different signals change:
Find the signals (like pc, instr, or reg_file) in the Signals Panel.
Drag and drop them into the Waveform Viewer or right-click and select Insert into Waveform.


5. Analyzing the Waveforms


Program Counter (pc): Helps track which instruction is being executed.
Instruction Register (instr): Shows which instruction is currently running.
Registers and Data Paths: Help check if the CPU is working correctly.

6. Adjusting the View


Zoom In/Out: Use the zoom buttons to focus on specific time intervals.
Scroll Along Time: Drag left or right to see how values change at different clock cycles.


Why Use GTKWave?
GTKWave helps us visualize what’s happening inside the CPU step by step. It is useful for debugging and ensuring that the instructions are executed correctly.

