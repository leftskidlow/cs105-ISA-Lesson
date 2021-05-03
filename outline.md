# CS105 Instruction Set Architecture Lesson Outline

## Resources
[Instruction Set Architecture](http://www.cs.kent.edu/~durand/CS0/Notes/Chapter05/isa.html)

[Organization of Computer Systems: ISA, Machine Language, and Number Systems](https://www.cise.ufl.edu/~mssz/CompOrg/CDA-lang.html)

[Microprocessor Design](https://en.wikibooks.org/wiki/Microprocessor_Design/Instruction_Set_Architectures)

[Instruction Set Architecture](https://minnie.tuhs.org/CompArch/Lectures/week02.html)

[MIT: Instruction Set Architecture](https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-004-computation-structures-spring-2017/c9/c9s1/)

[Instruction Set Architecture](https://www.cs.swarthmore.edu/~bryce/cs31/f16/readings/Instruction_Set_Architecture.pdf)

[A Study on the Impact of Instruction Set Architectures on Processor’s Performance](https://scholarworks.wmich.edu/cgi/viewcontent.cgi?article=2517&context=masters_theses)

## Lesson Description

The purpose of this lesson is to understand the implementation of an Instruction Set Architecture and the importance that it plays in the overall heirarchy of Computer Design and Architecture. We will discuss the layers of abstraction that exist between the modern programmer, the student, and the machines we operate on.

The lesson will begin with an introduction to several common ISAs and dive into their binary structures. The first half of the lesson will focus heavily on theory and the ability to conceptualize hardware/software interface. The student will be able to visualalize the processing of information in the language of the hardware and ultimately implement a mock-up of MIPS instructions through a Python interface. This will build the foundation the student will use to understand the Assembly Language module that will draw heavily on the understanding of ISAs.

## Lesson Code Description

The goal of the lesson checkpoints is to have the learner implement a cache from scratch within an existing register/memory hierarchy. The initial program will consist of a bank of registers and blocks of main memory. A group of commands will exist that repeatedly request data from memory. The timing of the commands can be output to represent the performance of the commands. As the learner implements the cache they will see timing improve as well as the effects of different policy implementations.

## Exercise Overview

- Introduction
- Processors (CPUs & ALUs), Registers, RAM, and Data Buses
- OPCODES and Instruction Formatting
- CISC vs RISC vs MIPS (OPCODES)
- MIPS Specfic OPCODES (R & I Types)
- Writing Binary Pseudo-Code - OPCODE Reader Method
<!-- - Writing Binary Pseudo-Code - Load / Store Methods -->
- Writing Binary Pseudo-Code - Add / Subtract / Multiply / Divide Methods
- Writing Binary Pseudo-Code - Simple Calculator Summary
- Summary

## Exercises In-Depth

### Introduction
- NARRATIVE
  - Introduce analogy
    - The Computer Hamburger
      - Outer buns (Hardware, User Programs)
      - Inners (ISAs, Assembly, Compilers, High-Level Languages)
  - Introduce cache using analogy
  - Summarize lesson/exercises
- Instructions
  - Move to the next exercise
- ARTWORK: Hamburger Analogy

### Processors, Registers, RAM, and Data Buses
- NARRATIVE
  - CPUs
    - CUs
    - ALUs
  - Registers
  - RAM
  - Data Buses (Parallel / Serial)
    - Highway Analogy
- Instructions
  - Move to the next exercise
- ARTWORK: CPU

###	OPCODEs and Instruction Formatting
- NARRATIVE
  - OPCODEs are the basic instructions
  - Typical Formatting in bits
  - Example Binary Instruction
- CHECKPOINTS
  - Look at the OPCODES and the OPCODE Table -> Add print statements after each one to test
  - Do the same for multiply & divide examples

### CISC vs RISC vs MIPS Instruction Sets
- NARRATIVE
  - Each design practice has different approaches to ISA
  - CISC is instruction heavy, RISC is the opposite
  - MIPS works well on embedded devices
- CHECKPOINTS
  - Run the program
    - has three pseudo-instructions in Python (CISC/RISC/MIPS)
    - Prints to console "CISC: I load / add / store", "RISC: I do too", "MIPS: Me too!" or something similar

### MIPS Specific OPCODES
- NARRATIVE
  - We'll be building a simple MIPS-based Immediate calculator, let's look at some OPCODES
  - R-Type instructions
  - I-Type instructions
  - J-Type instructions
  - Give MIPS IV ISA Table
- CHECKPOINTS
  - Sketch a simple console calculator design (add/subtract/multiply/divide/memory) on paper
  - Create a Python Class "mipsCalculator"
  - Create `__init__` method that names the calculator, initializes userDisplayRegister, numbersRegister
  - numbersRegister = 0 thru 31 in binary -> will use for register addressing

### Writing Binary Pseudo-Code - OPCODE Reader Method
- NARRATIVE
  - The CU on the CPU is where the ISA design is stored
  - After a CU reads an instruction it can figure out what to do next
  - It is a hardware and firmware design that gives the list of instructions a CPU can process
  - If the wrong binary (x86) is given to a MIPS processor, it won't know what to do
  - Show mismatch OPCODES
- CHECKPOINTS
  - Create a `opcodeReader` method, that takes in a MIPS 32 bit instruction as a string
  - If R-Type, Parse as R-Type else return message to user
  - call `add`, `subtract`, `multiply`, or `divide` methods based on instruction
    - will throw error because methods are defined yet
  - print `userDisplay`

<!-- ### Writing Binary Pseudo-Code - Load / Store Methods
- NARRATIVE
  - After a CU reads an instruction it can figure out what to do next
  - Sometimes we are loading / store information we already have used
  - Load functions (from registers) and Store functions (into registers)
  - Why use registers? explanation
- CHECKPOINTS
  - Create a `load` method
  - Return data from specific position in registerArray
  - Create `store` method
  - Store data into a specifc position in register (overwrite) -->

### Writing Binary Pseudo-Code - Add / Subtract / Multiply / Divide Methods
- NARRATIVE
  - Explain binary addition / subtraction
  - Eplain binary multiplication / division
  - Discuss Python bin() and int()
- CHECKPOINTS
  - Create `add` method, two parameters `num1` and `num2`
  - get `num1` and `num2` from register, convert to `int`, `add`
  - update userDisplay
  - Create `subtract` method, two parameters `num1` and `num2`
  - get `num1` and `num2` from register, convert to `int`, `subtract`
  - update userDisplay
  - Create `multiply` method, two parameters `num1` and `num2`
  - get `num1` and `num2` from register, convert to `int`, `multiply`
  - update userDisplay
  - Create `divide` method, two parameters `num1` and `num2`
  - get `num1` and `num2` from register, convert to `int`, `divide`
  - update userDisplay

### Writing Binary Pseudo-Code - Simple Calculator Summary
- NARRATIVE
  - Summarize ISAs
  - Summarize Binary Instructions
  - Summarize MIPS Calculator
- CHECKPOINTS
  - Play with calculator & attempt modulus method
