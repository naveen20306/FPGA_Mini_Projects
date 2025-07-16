```markdown
# 🔄 4-Bit Barrel Shifter (Verilog)

This project implements a 4-bit **barrel shifter** in Verilog HDL. A barrel shifter allows shifting or rotating a data word by a specific number of positions in a single clock cycle. It is useful in ALUs, DSP blocks, and other fast data manipulation circuits.

---

## 📁 Files Included

- `barrel.v` – Design file for the 4-bit barrel shifter.
- `barrel_tb.v` – Testbench to simulate and verify functionality.
- `docs/` – (Optional) Waveform screenshots or hardware demo media.

---

## 🔧 Description

- **Inputs:**
  - `in [3:0]` – 4-bit input data
  - `sel [2:0]` – 3-bit selection input to control the shift/rotate operation

- **Output:**
  - `out [3:0]` – Result of the shift/rotate operation

---

## ⚙️ Operation Table

The `sel` input determines the rotation/shift operation as shown below:

| `sel` | Operation                          | Output Description                   |
|--------|------------------------------------|----------------------------------------|
| `000`  | No shift (Pass-through)            | `out = in`                             |
| `001`  | Rotate Left by 1 bit               | `out = {in[2:0], in[3]}`               |
| `010`  | Rotate Left by 2 bits              | `out = {in[1:0], in[3], in[2]}`        |
| `011`  | Rotate Left by 3 bits              | `out = {in[0], in[3:1]}`               |
| `100`  | Duplicate Pass-through             | `out = in`                             |
| `101`  | Rotate Right by 1 bit (same as 011)| `out = {in[0], in[3:1]}`               |
| `110`  | Rotate Right by 2 bits             | `out = {in[1:0], in[3:2]}`             |
| `111`  | Rotate Right by 3 bit              | `out = {in[2:0], in[3]}`               |

> ⚠️ Note: This design appears to be experimenting with various rotation patterns — some custom, some repeating.

---

## 🧪 Testbench Summary

The testbench (`barrel_tb.v`) performs:

- Static input: `in = 4'hA` (i.e., `1010`)
- Iterates through all 8 `sel` values (0–7)
- Outputs observed via waveform or console

### Example Simulation Snippet:
```verilog
in = 4'ha; sel = 3'h0; // out = 1010
sel = 3'h1;            // out = 0101
sel = 3'h2;            // out = 0101
sel = 3'h3;            // out = 0101
...
```

> Use tools like **Vivado**, **ModelSim**, or **GTKWave** to simulate and view waveform output.

---

## 🛠️ Tools Used

- **HDL:** Verilog
- **Tested On:** Nexys Artix-7 100T FPGA board.
- **Simulated Using:** Vivado Simulator 

---

## 📜 License

MIT License – Free to use, modify, and share with attribution.

---

## ✍️ Author

- **Naveen Kumar B**
- Date: July 2025
```
