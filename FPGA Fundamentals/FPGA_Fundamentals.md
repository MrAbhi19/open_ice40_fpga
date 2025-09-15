## 📚 Table of Contents
- [FPGA](#fpga)
- [ICE40 LP384](#ice40-lp384)
- [Architecture Overview](#architecture-overview)


# FPGA

**FPGA** or (*Field Programmable Gate Array*), is a type of integrated circuit that can be **programmed and reprogrammed** after manufacturing to perform specific digital logic tasks. Think of *blank canvas* for digital circuits—you design how it behaves using code, typically written in hardware description languages like **VHDL** or **Verilog**. In this module we are going to learn about ICE40 LP384.

# ICE40 LP384

The **iCE40** is a family of **low-power, compact FPGAs** (Field-Programmable Gate Arrays) developed by *Lattice Semiconductor*. They're especially popular in hobbyist, open-source, and embedded systems communities thanks to their affordability and support for open-source toolchains.

The **iCE40 LP384** is one of the smallest and most power-efficient members of the iCE40 LP family of FPGAs from Lattice Semiconductor. It's designed for **ultra-low-power applications** where space and energy are at a premium—think wearables, small IoT devices, and embedded systems.
> 💡 *The “384” refers to its 384 logic cells (LookUp Table + D-Flip-Flop).*
---
# Architecture Overview

A single **ICE40 LP384** contains:

- 🔷 Programmable Logic Blocks (PLB)
- 🧠 4 kbit RAM
- 🔁 Phase-Locked Loop (PLL)
- 🔌 SPI Bank
- 💾 Non-Volatile Configuration Memory (NVCM)
- 🔗 I/O Bank
---

### Diving deeper into logic 

- 🔷 Programmable Logic Blocks (PLB)

core of FPGA consists of Programmable Logic Blocks (PLB) which can be programmed to perform 
logic and arithmetic functions.
> Each PLB consists of eight interconnected Logic Cells (LC)

#### Logic cells

Each Logic cell contains 3 logic elemnets 

1. A 4-input LUT (Look-Up Table) which builds any combinational logic function, of any complexity, requiring up to four inputs. Similarly, the LUT4 element behaves as a 16 x 1 Read-Only Memory (ROM).
2. A D Flip-Flop (DFF), with an optional clock-enable and reset control input, builds sequential logic functions.
3. Carry Logic boosts the logic efficiency and performance of arithmetic functions, including adders, subtracters, 
comparators, binary counters and some wide, cascaded logic functions.

***(Refer data sheet for Logic cell signal discription, Clock/Control Distribution Network,  Global Buffer (GBUF) Connections to Programmable Logic Blocks, )***

#### sysCLOCK Phase Locked Loops (PLLs) 

In the iCE40 FPGA, the PLL (Phase-Locked Loop) is a specialized circuit used to generate and manage clock signals. It plays a crucial role in synchronizing operations and optimizing performance across different parts of the chip.
-In the iCE40 FPGA, the PLL (Phase-Locked Loop) is a specialized circuit used to generate and manage clock signals. It plays a crucial role in synchronizing operations and optimizing performance across different parts of the chip.
-It aligns the phase of the output clock with the input clock, ensuring synchronized timing across components.

***(Refer data sheet for PLL Signal Descriptions,sysMEM Block Configurations, EBR Signal Descriptions )***

