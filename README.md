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

# 1.The RISC-V assembly instruction : lui a0, 0x2b
![Screenshot from 2025-04-02 19-16-04](https://github.com/user-attachments/assets/1c72468a-783f-48e0-9a37-0fd3e9ea6174)
* Instruction Type : lui (Load Upper Immediate) is an U-type (Upper Immediate) instruction in the RISC-V ISA.
* lui (Load Upper Immediate): Loads a 20-bit immediate value into the upper 20 bits of a register, setting the lower 12 bits to zero.
* a0: Register x10, commonly used for function return values in the RISC-V calling convention.
* 0x2b (Hexadecimal 0x2B = Decimal 43): This value is shifted left by 12 bits.
* 32-bit Instruction Representation : 00000000000000000000 01010 0110111
![Screenshot 2025-04-02 220433](https://github.com/user-attachments/assets/085fced6-d648-42fc-8a1e-1964fb1ba9e8)
 
# 2.The RISC-V Assembly Instruction : addi sp, sp, -32
![Screenshot from 2025-04-02 19-16-15](https://github.com/user-attachments/assets/726c1906-9b59-4b6d-961b-a6189a8f3e20)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011
![Screenshot 2025-04-02 205939](https://github.com/user-attachments/assets/8494c6da-343e-47cc-a8df-34964ce75108)

# 3.The RISC-V Assembly Instruction : sd ra, 24(sp)
![Screenshot from 2025-04-02 19-16-36](https://github.com/user-attachments/assets/358e8e11-bdac-44b3-83c7-9db75b9dedf0)
* Instruction Type : sd (Store Double Word) is an S-type (Store) instruction in the RISC-V ISA.
* sd (Store Double Word) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

# 4.The RISC-V Assembly Instruction : jal ra,10468 <printf>
![Screenshot from 2025-04-02 19-17-00](https://github.com/user-attachments/assets/f3790890-a899-4492-884d-3c419ae840a7)
* Instruction Type : jal (Jump And Link) is an J-type (Jump) instruction in the RISC-V ISA.
* jal (Jump And Link) is used for function calls and jumps in RISC-V. It performs two actions:
  1. Saves the return address (PC + 4) into a register (rd).
  2. Jumps to a target address (PC + immediate).
* ra (Return Address Register): Register x1 stores the address where the program should return after printf executes. 
* 10468 <printf>: 10468 is the memory address of printf in this specific compiled program. The <printf> label shows that this jump is calling the standard C printf function.
* Here, it saves the return address (PC + 4) into the register ra (x1) and jumps to the address 10468 (0x28E4 in hex), which corresponds to printf.
* 32-bit Instruction Representation : 0 0001110010 1 00000010  00001 1101111

# 5.The RISC-V Assembly Instruction : lw a2, 12(sp)
![Screenshot from 2025-04-02 19-17-26](https://github.com/user-attachments/assets/c2ce4284-75f3-4735-9523-d4020a1031dc)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

# 6.The RISC-V Assembly Instruction : mv a2,a5
![Screenshot from 2025-04-02 19-17-39](https://github.com/user-attachments/assets/5d92d130-ec7c-4cb1-884a-12888729f175)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

# 7.The RISC-V Assembly Instruction : sw a4, 8(sp)
![Screenshot from 2025-04-02 19-17-51](https://github.com/user-attachments/assets/e075e2db-d4f8-43a0-8467-ebd0dc7e5d04)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

# 8.The RISC-V Assembly Instruction : ld ra, 24(sp)
![Screenshot from 2025-04-02 19-18-10](https://github.com/user-attachments/assets/369a25d3-2f84-4b9e-8ea9-be8c8f3111dc)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

# 9.The RISC-V Assembly Instruction : li a0,0
![Screenshot from 2025-04-02 19-18-21](https://github.com/user-attachments/assets/f51d83f4-0a5a-4575-b0c9-c0479af3aece)
* Instruction Type : addi (Add Immediate) is an I-type (Immediate) instruction in the RISC-V ISA.
* addi (Add Immediate) is used to add an immediate value (a constant) to a register.
* sp: Register x2, commonly used as stack pointer.
* -32 : Immediate value to add with sp. 
* 32-bit Instruction Representation : 111111100000 00010 000 00010 0010011

 
  
