#NAND-Based-Computer
This project describes how a working computer was built. 
Both its Central Processing Unit (CPU) and Random Access Memory (RAM) were constructed entirely from NAND logic gates. 

Project Background and Development
The entire computer system was developed using the LogicCircuit application, a digital logic simulator available at https://www.logiccircuit.org/index.html.

This was the final project for a computer architecture course, demonstrating practical skills in digital design.
This project took 3 days to compelete, even though we had been given 2 months to complete.

The computer's design is based on the NandToTetris curriculum. 
This approach involves building a computer in layers. 
It starts with creating basic logic gates and then gradually building more complex parts like an Arithmetic Logic Unit (ALU), registers, and memory units, eventually leading to a complete, programmable computer.

How the System Works
The CPU in this system is a custom design that can run a specific set of instructions. Its main part, the ALU, performs all the necessary math and logic operations, and it's built completely from NAND gates. Data is handled and programs are controlled using registers and a program counter, which are themselves made from D flip-flops.

The memory system uses Static Random Access Memory (SRAM). Different sizes of memory (like RAM8, RAM64, up to RAM16K) are built by combining smaller memory units.
This layered design helps the computer store and retrieve data efficiently, which is vital for its operation. 
