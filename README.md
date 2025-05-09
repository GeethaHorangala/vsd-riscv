# vsd-riscv
# VSDSquadron Mini Research Internship
This internship program focuses on RISCV-V based architecture.

# Participant Information
Name : Geetha H

E-mail : geethahorangala@gmail.com

# Task 1 : Virtual Machine Setup & RISC-V Code Execution
# Overview
This task contains a simple C program for calculating the sum of n integers, along with its compiled output and the equivalent RISC-V assembly code. The entire setup was performed on an Ubuntu-based Virtual Machine (VM) created using VirtualBox.

# RISC-V
RISC-V is an open-source, modular, and scalable Instruction Set Architecture (ISA) based on the RISC (Reduced Instruction Set Computing) principles. It is free from licensing restrictions, making it widely used in embedded systems, AI, IoT, and high-performance computing. With a simple yet extensible design, RISC-V supports multiple instruction extensions, enabling flexibility for various applications, from microcontrollers to data centers. Its growing ecosystem and industry adoption make it a strong competitor to proprietary ISAs like ARM and x86.

# O1 and Ofast Optimization
O1 and -Ofast are optimization levels used in compilers like GCC to optimize code performance. They control how the compiler transforms and optimizes the generated machine code.

# -O1 (Optimization Level 1)
* Enables basic optimizations while keeping compilation time low.
* Focuses on reducing code size and improving execution speed without aggressive transformations.
* May disable some debugging features but keeps code relatively easy to analyze.

# -Ofast (Aggressive Optimization)
* Similar to -O3 but removes strict standard compliance for more aggressive optimizations.
* Enables all -O3 optimizations plus additional speed-focused optimizations like:
  * Ignoring strict floating-point rules (e.g., allowing unsafe math optimizations).
  * Removing some safety checks.
  * Using architecture-specific features for maximum performance.
* May cause unexpected behavior in some programs due to floating-point approximations and removed safety constraints.

# C Code for Calculating the Sum of N Integers
![sum1ton c](https://github.com/user-attachments/assets/29293baa-6189-4e22-9767-3428506526de)
The above program is then executed and converted into RISC-V object code with O1 and Ofast optimization.

# RISC-V O1 Optimization
![riscv_based_lab 2](https://github.com/user-attachments/assets/a1c82169-6007-4c62-88b2-ae767ed878e2)

# RISC-V Ofast Optimization
![riscv_based_lab 4](https://github.com/user-attachments/assets/42531f01-4ea9-440c-9433-e499adb23859)

# Task 2 : RISC-V O1 and Ofast Optimization Analysis
# Overview
This task involves a simple C program for swapping two numbers, along with its compiled output and the corresponding RISC-V assembly code. Additionally, the program is executed using the GCC compiler with O1 and Ofast optimization levels. Furthermore, a register-level analysis is conducted using Spike, providing insights into the impact of these optimizations on execution performance.

# Spike : RISC-V ISA Simulator
Spike is the official RISC-V ISA simulator, designed for testing and running RISC-V programs without actual hardware. It supports different RISC-V instruction sets (RV32, RV64) and extensions, making it useful for software development, debugging, and performance analysis. Spike is widely used in research and industry to validate RISC-V software before deploying it on real hardware.

# C Code for Swap Two Numbers
![swap_code](https://github.com/user-attachments/assets/a3eea8b9-0350-452f-ae1c-ea1d1e57b41a)

# RISC-V O1 Optimization
![RISC-V _O1](https://github.com/user-attachments/assets/fdf9c784-e1cb-464c-9ab9-77c9a06f066a)

# RISC-V Ofast Optimization
![RISC-V_Ofast](https://github.com/user-attachments/assets/f5acb58e-2191-4749-ae1a-ad9f9c30b63c)

# Analysis Using Spike Simulator
![RISC-V_spike](https://github.com/user-attachments/assets/acead6bb-5bf3-4e7f-93f5-acf611382a67)

# Task 3 : RISC-V Instruction Formats
# Overview

# 1. The RISC-V Assembly Instruction : lui a0, 0x2b
![Screenshot from 2025-04-02 19-16-04](https://github.com/user-attachments/assets/1c72468a-783f-48e0-9a37-0fd3e9ea6174)
* Instruction Type : lui (Load Upper Immediate) is an U-type (Upper Immediate) instruction in the RISC-V ISA.
* lui (Load Upper Immediate): Loads a 20-bit immediate value into the upper 20 bits of a register, setting the lower 12 bits to zero.
* a0: Register x10, commonly used for function return values in the RISC-V calling convention.
* 0x2b (Hexadecimal 0x2B = Decimal 43): This value is shifted left by 12 bits.
* 32-bit Instruction Representation : 00000000000000000000 01010 0110111
![Screenshot 2025-04-02 220433](https://github.com/user-attachments/assets/085fced6-d648-42fc-8a1e-1964fb1ba9e8)
 
# 2. The RISC-V Assembly Instruction : addi sp, sp, -32
![Screenshot from 2025-04-02 19-16-15](https://github.com/user-attachments/assets/726c1906-9b59-4b6d-961b-a6189a8f3e20)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011
![Screenshot 2025-04-02 205939](https://github.com/user-attachments/assets/8494c6da-343e-47cc-a8df-34964ce75108)

# 3. The RISC-V Assembly Instruction : sd ra, 24(sp)
![Screenshot from 2025-04-02 19-16-36](https://github.com/user-attachments/assets/358e8e11-bdac-44b3-83c7-9db75b9dedf0)
* Instruction Type : sd (Store DoubleWord) is a S-type (Store) instruction in the RISC-V ISA.
* sd (Store DoubleWord) is used to store a 64-bit (doubleword) value from a register into memory. It is part of the RV64I instruction set (only available in 64-bit RISC-V).
* sp : Register x2, commonly used as stack pointer.
* ra (Return Address Register): Register x1 stores the data.
* 24 : Immediate value to add with sp.
* Here, the instruction sd ra, 24(sp) stores the 64-bit value in ra (x1) into memory at sp + 24.
* 32-bit Instruction Representation : 0000000 00001 00010 011 11000 0100011
![Screenshot 2025-04-02 232454](https://github.com/user-attachments/assets/35ee32e8-f0a3-4eb8-b801-b5a7ef339150)

# 4. The RISC-V Assembly Instruction : jal ra,10468 <printf>
![Screenshot from 2025-04-02 19-17-00](https://github.com/user-attachments/assets/f3790890-a899-4492-884d-3c419ae840a7)
* Instruction Type : jal (Jump And Link) is a J-type (Jump) instruction in the RISC-V ISA.
* jal (Jump And Link) is used for function calls and jumps in RISC-V. It performs two actions:
  1. Saves the return address (PC + 4) into a register (rd).
  2. Jumps to a target address (PC + immediate).
* ra (Return Address Register): Register x1 stores the address where the program should return after printf executes. 
* 10468 <printf>: 10468 is the memory address of printf in this specific compiled program. The <printf> label shows that this jump is calling the standard C printf function.
* Here, it saves the return address (PC + 4) into the register ra (x1) and jumps to the address 10468 (0x28E4 in hex), which corresponds to printf.
* 32-bit Instruction Representation : 0 0001110010 1 00000010  00001 1101111
![Screenshot 2025-04-02 222830](https://github.com/user-attachments/assets/551a48ef-28ed-499f-8bf8-fc6773a909e9)

# 5. The RISC-V Assembly Instruction : lw a2, 12(sp)
![Screenshot from 2025-04-02 19-17-26](https://github.com/user-attachments/assets/c2ce4284-75f3-4735-9523-d4020a1031dc)
* Instruction Type : lw (Load Word) is an I-type (Immediate) instruction in the RISC-V ISA.
* lw (Load Word) is used to load a 32-bit word (4 bytes) from memory into a register in the RV32I and RV64I instruction sets. It is typically used for loading data from memory into registers.
* sp : Register x2, commonly used as stack pointer.
* a2 : Register x12.
* 12 : Immediate value to add with sp.
* The instruction lw a2, 12(sp) loads a 32-bit word (4 bytes) from memory at sp + 12 into the register a2. 
* 32-bit Instruction Representation : 000000001100 00010 010 01100 0000011
![Screenshot 2025-04-03 003038](https://github.com/user-attachments/assets/633714bb-5cac-4a6d-8991-f1a424dfd32b)

# 6. The RISC-V Assembly Instruction : mv a2,a5
![Screenshot from 2025-04-02 19-17-39](https://github.com/user-attachments/assets/5d92d130-ec7c-4cb1-884a-12888729f175)
* Instruction Type : The mv instruction is a pseudo-instruction in RISC-V that performs a register-to-register copy.
* a5 : source register (Register x15)
* a2 : destination register (Register x12)
* This instruction copies the value in register a5 into a2.
* mv a2, a5 is a pseudo-instruction, which the assembler translates to: addi a2, a5, 0
* addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* 32-bit Instruction Representation :000000000000 01111 000 01100 0010011

# 7. The RISC-V Assembly Instruction : sw a4, 8(sp)
![Screenshot from 2025-04-02 19-17-51](https://github.com/user-attachments/assets/e075e2db-d4f8-43a0-8467-ebd0dc7e5d04)
* Instruction Type : sw (Store Word) is a S-type (Store) instruction in the RISC-V ISA.
* sw (Store Word) is used to store a 32-bit (word) value from a register into memory.
* sp : Register x2, commonly used as stack pointer.
* a4 : Register x14, that holds the data to be stored.
* 8 : Immediate value to add with sp.
* The instruction sw a4, 8(sp) stores a 32-bit word (4 bytes) from a4 into memory at sp + 8.
* 32-bit Instruction Representation : 0000000 01110 00010 010 01000 0100011
![Screenshot 2025-04-03 001414](https://github.com/user-attachments/assets/387232a0-00b2-452e-9fb6-94fb137c8444)

# 8. The RISC-V Assembly Instruction : ld ra, 24(sp)
![Screenshot from 2025-04-02 19-18-10](https://github.com/user-attachments/assets/369a25d3-2f84-4b9e-8ea9-be8c8f3111dc)
* Instruction Type : ld (Load Word) is an I-type (Immediate) instruction in the RISC-V ISA.
* ld (Load Word) is used to load a 64-bit (8-byte) value from memory into a register in the RV64I instruction set. It is commonly used to retrieve data stored in memory or on the stack.
* sp : Register x2, commonly used as stack pointer.
* ra (Return Address Register): Register x1 is the destination.
* 24 : Immediate value to add with sp.
* The instruction ld ra, 24(sp) is used to load a 64-bit (doubleword) value from memory at sp + 24 into the ra (return address) register.
* 32-bit Instruction Representation : 000000011000 00010 011 00001 0000011

# 9. The RISC-V Assembly Instruction : li a0,0
![Screenshot from 2025-04-02 19-18-21](https://github.com/user-attachments/assets/f51d83f4-0a5a-4575-b0c9-c0479af3aece)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

# Task 4 : Functional Simulation of RISC-V Core
# Overview
This task involved performing functional simulation of the given RISC-V Core Verilog netlist and testbench and checking the functional correctness of the core by observing the output signals.

# 1. Introduction to Verilog
Verilog is a hardware description language (HDL) used to model and design digital systems such as processors, memory modules, and logic circuits. It allows designers to describe hardware behavior and structure, making it a key tool in digital electronics and embedded systems.

# 2. Verilog Netlist
A netlist in Verilog is a detailed representation of a digital circuit in terms of its components and the connections (nets) between them. It specifies how elements such as logic gates and modules are interconnected. Netlists are either manually written using structural Verilog or automatically generated using synthesis tools. They serve as the foundation for simulation and verification before deploying a design on actual hardware.

# 3. Verilog Testbench
A testbench is a non-synthesizable Verilog module used to verify and test the functionality of a design. It simulates the environment in which the actual hardware will operate by applying various input combinations and observing the outputs. The testbench doesn't represent real hardware; instead, it automates testing by using simulation tools. It typically includes initial blocks for defining signal behavior over time and uses system tasks like $display and $dumpfile to monitor and record simulation results.

# 4. Icarus Verilog
Icarus Verilog is an open-source Verilog compiler and simulator. It compiles Verilog source files and testbenches into an intermediate simulation format and then runs the simulation to check the logic and timing of the design. It is widely used for educational purposes due to its simplicity, efficiency, and compatibility with all major operating systems. Icarus Verilog supports simulation of both behavioral and structural Verilog code.

# 5. GTKWave
GTKWave is a waveform viewer that is used to analyze the simulation results visually. It displays changes in signals over time in the form of waveforms. GTKWave reads data from .vcd (Value Change Dump) files generated during simulation and helps designers debug, analyze, and validate the logic by examining how input and output signals behave over a simulated time period.

# 6. Complete Design Flow Summary
The typical digital design flow using Verilog starts with writing the Verilog module (design), followed by creating a testbench for simulation. The design and testbench are compiled using Icarus Verilog, and the simulation output is stored in a .vcd file. Finally, this file is opened with GTKWave to analyze signal waveforms and verify that the design behaves as expected. This flow is crucial in ensuring that digital circuits are functionally correct before hardware implementation.

# Reference Verilog Code
![Screenshot 2025-04-08 211839](https://github.com/user-attachments/assets/5c2dd6dd-1ad4-434b-99ac-a6ba40f7195e)

# Commands to get GTKWave
![cmd](https://github.com/user-attachments/assets/b53b6a8e-f85d-46a1-8c80-0470d7d32ded)

# GTKWave Output Waveform
# Instruction 1 : add r6,r1,r2
![Screenshot (34)](https://github.com/user-attachments/assets/1d010921-8064-4802-b35a-bc42366fad04)

# Instruction 2 : sub r7,r1,r2
![Screenshot (36)](https://github.com/user-attachments/assets/54c1c569-af67-4581-bf4b-6fbd7e52febf)

# Instruction 3 : and r8,r1,r3
![Screenshot (38)](https://github.com/user-attachments/assets/97582ebc-66da-4c08-be87-55b5a86fa83c)

# Instruction 4 : or r9,r2,r5
![Screenshot (39)](https://github.com/user-attachments/assets/a8069532-d02d-46fc-8107-c0d8994033a4)

# Instruction 5 : xor r10,r1,r4
![Screenshot (40)](https://github.com/user-attachments/assets/04fbcf19-8475-402e-ab3f-3019524d044c)

# Instruction 6 : slt r11,r2,r4
![Screenshot (41)](https://github.com/user-attachments/assets/30ba3149-8388-45f9-a87f-f536959e5a21)

# Instruction 7 : addi r12,r4,5
![Screenshot (49)](https://github.com/user-attachments/assets/457dba96-c9d5-449b-9e22-d5887169f74c)

# Instruction 8 : sw r3,r1,2
![Screenshot (48)](https://github.com/user-attachments/assets/79ec09c6-200c-469d-bee1-07c012166f2a)

# Instruction 9 : lw r13,r1,2
![Screenshot (47)](https://github.com/user-attachments/assets/e065fdef-c94c-40fa-b92b-2ff4910ec52e)

# Instruction 10 : beq r0,r0,15
![Screenshot (50)](https://github.com/user-attachments/assets/ae9216b0-69e0-4390-8bd6-b0ee16af8ce8)

# Instruction 11 : add r14,r2,r2
![Screenshot (46)](https://github.com/user-attachments/assets/387f8623-f50c-47d8-b3d0-40a708f9347d)

# Task 5 : Obstacle Detection and Visual-Audio Alert System using VSDSquadron Mini 
# Overview
This project uses an ultrasonic sensor (HC-SR04) interfaced with the VSD Squadron Mini board to detect obstacles. If an object is detected within a threshold distance, the system triggers a buzzer and red LED to alert the driver, signaling the vehicle must stop. If the path is clear, a green LED lights up indicating it's safe to move. This system is ideal for smart vehicle safety or autonomous robots.

# Hardware Components:
![Screenshot 2025-04-11 173448](https://github.com/user-attachments/assets/534877ba-9c4a-4f99-8dad-f967129310ee)

# Hardware Description:
# 1.VSD Squadron Mini (RISC-V Board):
![IMG-20250410-WA0067](https://github.com/user-attachments/assets/7e8f2e38-ec55-4ba0-a48f-bf1b75f8c378)

The VSD Squadron Mini is a compact development board based on the RISC-V open-source architecture. It is used for learning embedded systems and digital design. The board includes GPIO pins to connect sensors, LEDs, buzzers, and more. It is ideal for hands-on projects and experimentation with the RISC-V toolchain.

# 2.Ultrasonic Sensor (HC-SR04):
![hc-sr04-ultrasonic-sensor](https://github.com/user-attachments/assets/03a90d25-114b-492c-8a40-87fec9acb11b)

The HC-SR04 is a popular ultrasonic distance sensor used to measure the distance between the sensor and an object using sound waves. It has four pins (VCC, GND, Trig, Echo) and can measure distances from 2 cm to 400 cm with good accuracy. Commonly used in obstacle detection and robot navigation.

# 3.Buzzer:
![buzzer](https://github.com/user-attachments/assets/55411ae9-ae2a-4d82-be4b-095e9bc7bcc3)

A buzzer is an electronic component that produces sound when voltage is applied. It is used for audio alerts or notifications in systems. In this project, the buzzer is activated when an obstacle is detected nearby.

# 4.LED (Light Emitting Diode):
![led](https://github.com/user-attachments/assets/c6139f77-1ef6-40db-99c4-a15bdd65f9af)

An LED is a light-emitting device used to indicate status or output. A Red LED is used to indicate danger or obstacle detection, while a Green LED indicates safety or no obstacles. A 220-ohm resistor is usually connected in series to limit current.

# Pin Diagram:
![Screenshot 2025-04-11 171700](https://github.com/user-attachments/assets/1ab542d2-2d7b-44c3-9008-3d51b91bae69)

# Circuit Diagram:
![Screenshot 2025-04-11 164238](https://github.com/user-attachments/assets/a66d53ca-d772-42aa-9843-fd3aef92fa95)

# Pin Connections:
![Screenshot 2025-04-11 174141](https://github.com/user-attachments/assets/52706ee6-aeb8-42fc-a691-dbc0b26953bf)

# Task 6 : Project Video
https://drive.google.com/file/d/1aMHbqK383fPR0MHRuOrs2yzE0XmoX5ZT/view?usp=drivesdk



    
