
# 🔃 Integrated Up & Down Counter on 7-Segment Display

This project implements a **4-bit up/down counter** with 7-segment display control in **Verilog HDL**. The direction (up or down) is determined dynamically based on input signal edges. Both modes are seamlessly integrated into a **single hardware module**, avoiding the need for separate designs.

---

## 📁 Files Included

- `counter.v` – Main Verilog design for the integrated up/down counter.
- `counter_tb.v` – Testbench to simulate the behavior.

---

## 🔧 Functional Overview

### 🔄 Behavior:
- Rising edge of `in` → **Start Counting Up**
- Falling edge of `in` → **Start Counting Down**
- Counter rolls over after `9` and underflows after `0`
- Each time the counter wraps around (up or down), the `loops` register increments

### 🕹 Control Signals:
| Signal  | Direction | Description                                 |
|---------|-----------|---------------------------------------------|
| `clk`   | Input     | System clock                                |
| `rst`   | Input     | Reset signal (synchronous)                  |
| `start`| Input     | Enable counting                              |
| `in`    | Input     | Direction controller (edge-sensitive)       |
| `seg_out` | Output | 7-bit output to the 7-segment display        |
| `loops`  | Output | 4-bit register tracking counter rollovers     |
| `an`     | Output | 8-bit active-low anode control (static `11111110`) |

---

## 🧠 Key Features

- ⏱ Clock divider for slow counting using `clk_div[25]`
- 🔁 Up/down detection via previous state tracking (`prev_in`)
- 🔢 BCD counter from `0` to `9`
- 🔄 Integrated wrap-around handling (reset to `0` or `9`)
- 🧮 BCD to 7-segment conversion using a `case` statement
- 🟢 Single module handles both up & down logic efficiently

---

## 🧪 Testbench Summary (`counter_tb.v`)

### Simulation Procedure:

1. Apply reset
2. Simulate falling edge of `in` to trigger down count
3. Simulate rising edge of `in` to switch to up count
4. Monitor values of `loops` via console

### Snippet:
```verilog
rst=1; in=0; start=1; #5
rst=0; in=0; start=1; #5000  // Falling edge → Count Down
rst=0; in=1; start=1; #5000  // Rising edge → Count Up
```

### Monitor Output:
```text
Time=XXXX || loop=1
```

---

## 🛠️ Tools Used

- **HDL:** Verilog
- **Simulation:** Vivado Simulator
- **Synthesis:**  Nexys A7 100t FPGA

---

## 📜 License

MIT License – Free to use, modify, and distribute with credit.

---

## ✍️ Author

- **Naveen Kumar B**
- Date: July 2025
```
