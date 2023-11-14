# x86 Architecture 
![plot](./Architecture.png)
## CPU Archi
- (I/O Devices) <=> (CPU: Registers <=> Arithmetic Logic Unit <=> Control Unit) <=> (Main Memory RAM)
- Control Unit => takes instructions from RAM, EIP (Instruction Pointer)
- Arithmetic Logic Unit => Executes instructions and stores results in Registers or RAM
- Registers => CPU Storage
- RAM => contains code and data for a program to run, CPU access it one instruction at time
- I/O

- En bref: When a program has to be executed, it is loaded into the memor, from there, the Control Unit fetches one instruction at a time, using the Instruction Pointer Register, and the Arithmetic Logic Unit executes it,the results are either stored in the Registers or the RAM.

## Registers
- **Instruction Pointer**: pointer to the next instruction to be executed by the CPU.(EIP for 32bit, RIP for 64bit)

- **General-Purpose Registers**: (32bits/64bits)
![plot](./General_purpose_registers.png)
- used during the general execution of instruction by the CPU.
- for 64bits (extended registers):
    - **EAX or RAX(Accumulator Register)** : 
        - stores results of Arithmetic Operations.
        - last 16 bits of this register can be accessed by addressing **AX**. Similarly, it can also be addressed in 8 bits by using **AL** for the lower 8 bits and **AH** for the higher 8 bits

        ```assembly
        ; Example of adding two values and storing the result in EAX
        mov eax, 5       ; Move the value 5 into EAX
        add eax, 7       ; Add 7 to the value in EAX
        ; Result (12) is now in EAX
        ```

    - **EBX or RBX(Base Register)** :
        - In the context of memory addressing, it can serve as a base address for data structures or arrays.
        - The base register is often used in combination with an offset to calculate memory addresses. This is known as effective address computation.
        - For example, if you have an array in memory, the base register might hold the starting address of the array, and an offset can be added to it to access a specific element.

        ```assembly
        ; Example of using EBX as a base register for memory addressing
        mov ebx, offset myArray   ; Set EBX to the base address of myArray
        mov eax, [ebx + 4]        ; Load the value at the address (EBX + 4) into EAX
        ```

    - **ECX or RCX(Counter Register)**:
        - The counter register is commonly used as a general-purpose register for various operations.
        - Historically, it has been frequently used as a loop counter in assembly language and low-level programming, though its use is not limited to this purpose.

        ```assembly
        ; Example of using ECX as a loop counter
        mov ecx, 5         ; Set ECX to the loop count (e.g., 5 iterations)
        loop_start:
            ; Code inside the loop
            ; ...

            ; Decrement ECX and check if it's zero
            loop loop_start
        ```