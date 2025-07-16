# 🧮 4-Bit ALU (Arithmetic Logic Unit)

This project implements a 4-bit Arithmetic Logic Unit (ALU) using Verilog. It performs a variety of arithmetic and logical operations based on a 3-bit select line.

## 📁 Files Included

- `alu.v` – Verilog design file for the ALU.
- `Verification(x).jpg` – Photos of hardware implementation.

---

## ⚙️ ALU Operation Table

| `sel` (3-bit) | Operation         | Description             |
|---------------|-------------------|--------------------------|
| `000`         | `a + b`           | Addition with overflow  |
| `001`         | `a - b`           | Subtraction with overflow |
| `010`         | `a & b`           | Bitwise AND             |
| `011`         | `a | b`           | Bitwise OR              |
| `100`         | `a ^ b`           | Bitwise XOR             |
| `101`         | `a << b`          | Logical Left Shift      |
| `110`         | `a >> b`          | Logical Right Shift     |
| `111`         | `rotate left`     | Circular left rotation  |

> Output: `out` (4-bit), `ov` (1-bit overflow indicator)

---

## 🔍 Description

- Inputs:
  - `a`, `b`: 4-bit operands
  - `sel`: 3-bit select line to choose operation
- Outputs:
  - `out`: 4-bit result
  - `ov`: Overflow flag (for arithmetic ops)

All operations are performed combinationally using a `case` statement inside an `always @(*)` block.

---


## 📸 Demo

*Include waveform images or working hardware demo photos/videos as `Verification(x).jpg`.*

---

## 🛠️ Tools Used

- Verilog HDL
- Simulated in: *Xilinx Vivado*
- Synthesized on: *Nexys Artix-7 100T FPGA board*

---

## 📜 License

MIT License – Feel free to use and modify.

---

## ✍️ Author

- **Naveen Kumar B**
- Date: July 2025

