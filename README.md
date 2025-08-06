# NAND-Based-Computer

This project describes how a working computer was built.  
Both its Central Processing Unit (CPU) and Random Access Memory (RAM) were constructed entirely from NAND logic gates. 

### Project Background and Development  
The entire computer system was developed using the LogicCircuit application, a digital logic simulator available at https://www.logiccircuit.org/index.html.  
This was the final project for a computer architecture course, demonstrating practical skills in digital design.  
This project took 3 days to compelete, even though we had been given 2 months to complete.  

The computer's design is based on the NandToTetris curriculum.  
This approach involves building a computer in layers.  
It starts with creating basic logic gates and then gradually building more complex parts like an Arithmetic Logic Unit (ALU), registers, and memory units, eventually leading to a complete, programmable computer.  

### How the System Works  
The CPU in this system is a custom design that can run a specific set of instructions. Its main part, the ALU, performs all the necessary math and logic operations, and it's built completely from NAND gates.  
Data is handled and programs are controlled using registers and a program counter, which are themselves made from D flip-flops.  

The memory system uses Static Random Access Memory (SRAM).  
Different sizes of memory (like RAM8, RAM64, up to RAM16K) are built by combining smaller memory units.  
This layered design helps the computer store and retrieve data efficiently, which is vital for its operation.  

## Instruction Set Architecture
The computer operates on a 16-bit word length, with each instruction occupying two bytes. The instruction set is divided into two primary modes, determined by the Most Significant Bit (MSB) of the instruction word.

### A-Instruction (Address/Constant Loading)
When the MSB of a 16-bit instruction is 0, the instruction is interpreted as an A-instruction. This mode is designed to load a 15-bit constant value directly into the A register. This functionality is crucial for operations requiring immediate values, such as addressing memory locations, selecting specific registers, or providing operands for arithmetic and logical operations.

### C-Instruction (Computation/Control)
When the MSB of a 16-bit instruction is 1, the instruction is interpreted as a C-instruction, signaling a computational or control operation rather than a constant load. For all C-instructions, the three most significant bits (bits 15, 14, 13) are set to 1. The remaining bits are structured as follows:

### Computation (comp) Bits (7 bits)
The subsequent seven bits define the computation to be performed by the Arithmetic Logic Unit (ALU). The most significant bit of this 7-bit segment (bit 12 of the original 16-bit instruction, often denoted as a) determines the source of one of the ALU's operands:

If a is 1, the ALU utilizes the value stored at the memory location addressed by the A register (M), serving as an input.

If a is 0, the ALU utilizes the value from the A register (A).

The remaining six bits (c1-c6) specify the exact ALU operation. Below is a table of common comp values and their corresponding operations:

 ----------------------------------
  When a = 0 |   bits   | when a=1 
 ----------------------------------
       0     |  101010  | 
	   1     |  111111  |
	  -1     |  111010  |
	   D     |  001100  |
	   A     |  110000  |     M
	  !D     |  001101  |
	  !A     |  110001  |    !M 
	  -D     |  001111  |
	  -A     |  110011  |    -M 
	  D+1    |  011111  |
	  A+1    |  110111  |    M+1
	  D-1    |  001110  |
	  A-1    |  110010  |    M-1
	  D+A    |  000010  |    D+M
	  D-A    |  010011  |    D-M
	  A-D    |  000111  |    M-D
	  D&A    |  000000  |    D&M
	  D|A    |  010101  |    D|M
	   