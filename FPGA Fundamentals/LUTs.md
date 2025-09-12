# 🔍 What is a LUT (Look-Up Table)?

A **Look-Up Table (LUT)** is a fundamental component in digital electronics. It functions as a versatile combinational circuit by storing the output values for every possible input combination, effectively replicating the behavior of a dedicated logic circuit.

Instead of manually designing a circuit using logic gates like AND, OR, or XOR based on a truth table, a LUT simplifies the process by directly storing the truth table itself. When an input is provided, the LUT retrieves and outputs the corresponding pre-computed value.

This approach eliminates the need for complex circuit design and expression derivation, making LUTs especially valuable in programmable logic devices such as FPGAs.

# How to build one?

A LUT can be viewed as a multiplexer where the selector lines represent the input variables of a function, and the data inputs correspond to the function’s predefined output values. The multiplexer’s output then serves as the final output of the function.

## 🔄 XOR Function Using a 4×1 Multiplexer

The XOR function can be implemented using a 4×1 multiplexer by assigning the correct logic levels to the data inputs based on the truth table.

### 🧮 XOR Truth Table

| A | B | Select (AB) | Output |
|---|---|--------------|--------|
| 0 | 0 | 00           |   0    |
| 0 | 1 | 01           |   1    |
| 1 | 0 | 10           |   1    |
| 1 | 1 | 11           |   0    |

### 🧩 MUX Configuration

To replicate this behavior using a 4×1 MUX:
- **Select lines**: A and B
- **Data inputs**:
  - I₀ = 0
  - I₁ = 1
  - I₂ = 1
  - I₃ = 0

<p align="center">
  <img src="assets/xor_mux.png" alt="XOR using 4x1 Multiplexer" width="400"/>
</p>

This demonstrates how a LUT can be realized using multiplexers, where the select lines are the input variables and the data inputs represent the function's output values.

---

## ✅ Summary

- LUTs simplify logic design by storing output values directly.
- They are often implemented using multiplexers in hardware.
- The XOR function is a classic example of how a LUT can replicate logic using a 4×1 MUX.
