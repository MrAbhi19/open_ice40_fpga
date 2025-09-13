## What is a CLB?

A Configurable Logic Block (CLB) is a fundamental building unit in an FPGA architecture, combining both combinational and sequential logic elements to implement versatile digital functions. 

**A CLB typically contains:**
  - LUTs (Look-Up Tables)
  - D-Flip-Flops
  - Multiplexers
  - Carry logic
---
→**LUTs**

[we have already discussed here about LUTs](LUTS.md)

→**D-Flip-Flop**

A D Flip-Flop (DFF) is a fundamental sequential logic circuit that stores one bit of binary data. It captures the value of the input (D) on the rising or falling edge of a clock signal, and holds that value stable until the next clock event.

→**Multiplexers(MUX)**

A multiplexer (MUX) is a digital logic device that acts like a smart selector switch. It takes multiple input signals and channels only one of them to a single output line, based on control signals called select lines.

→**Carry logic**

In an FPGA carry logic is a special shortcut that helps the chip add numbers faster.


## How to design a CLB?

## 🔧 Components and Structure

### LUT1 – 2-Input Look-Up Table
- **Inputs**: `A`, `B` (binary variables)
- **Initialization Lines**: `INIT0`, `INIT1`, `INIT2`, `INIT3`  
  *(Define the truth table for all combinations of A and B)*
- **Output**: `Y` (result of the logic function based on A and B)

### DFF1 – D Flip-Flop
- **Input**: `Y` (output from LUT1)
- **Clocked Output**: `Q` (stores the value of Y on the rising edge of the clock)

### MUX – 2-to-1 Multiplexer
- **Inputs**: `Y` (combinational output from LUT1), `Q` (registered output from DFF1)
- **Select Line**: `SEL` (determines whether the output is real-time or registered)
- **Output**: `Z` (final output of the CLB)

---

## 🧬 Functional Description

- The **LUT** computes a logic function based on inputs `A` and `B`, producing output `Y`.
- The **DFF** captures and stores the value of `Y` on the clock edge, producing output `Q`.
- The **MUX** selects between the immediate combinational result (`Y`) and the stored sequential result (`Q`) based on the control signal `SEL`.
- The selected output `Z` represents the **final output of the CLB**.

## Logic Circuit 
<img src="../assets/clb_diagram.png" alt="CLB Circuit Diagram" width="500"/>

A detailed simulation of the CLB is given here [CLB](https://circuitverse.org/users/335760/projects/clb-e1e66333-e8a8-46e8-9381-f27396d5fd72). you can try the circuit with your own functions and examples.


## How to build CLB using Verilog

```verilog
module clb (
  input [1:0] addr,       // LUT address inputs
  input clk,              // Clock for DFF
  input sel,              // Select line for MUX
  output reg [3:0] z      // Final CLB output
);

  reg [3:0] y;            // Output from LUT
  reg [3:0] q;            // Output from DFF

  // LUT logic
  always @(*) begin
    case (addr)
      2'b00: y = 4'h1;
      2'b01: y = 4'h3;
      2'b10: y = 4'h5;
      2'b11: y = 4'hF;
      default: y = 4'h0;
    endcase
  end

  // D Flip-Flop logic
  always @(posedge clk) begin
    q <= y;
  end

  // MUX logic
  always @(*) begin
    z = sel ? q : y;
  end

endmodule
```
**code explanation**
```verilog
module clb (
  input [1:0] addr,       // LUT address inputs
  input clk,              // Clock for DFF
  input sel,              // Select line for MUX
  output reg [3:0] z      // Final CLB output
);
```
