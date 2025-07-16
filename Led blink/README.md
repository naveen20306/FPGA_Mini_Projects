```markdown
# 💡 LED Blink with Clock Divider (Verilog)

This project demonstrates a basic **LED blinking module** using Verilog. The LED toggles at a human-visible rate using an internal clock divider. Blinking is controlled by a `switch` input and can be reset anytime using `rst`.

---

## 📁 Files Included

- `ledblink.v` – Main Verilog design for blinking the LED

---

## 🔧 Functional Overview

### 📌 Description:
- **Objective**: Blink an LED at ~1Hz using a 50MHz FPGA clock
- **Clock Divider**: A 27-bit counter divides the clock by 50 million cycles
- **Control**: Blinking starts only when `switch` is `1`. Reset stops everything.

---

## ⚙️ Inputs & Outputs

| Signal   | Direction | Description                                |
|----------|-----------|--------------------------------------------|
| `clk`    | Input     | System clock (e.g., 50MHz)                 |
| `rst`    | Input     | Asynchronous reset                         |
| `switch` | Input     | Enables blinking when high                 |
| `led`    | Output    | LED toggles ON/OFF at 1Hz when enabled     |

---

## ⏱ How It Works

1. On reset, the `counter` and `led` state are cleared.
2. If `switch` is high:
   - The `counter` starts counting up every clock cycle.
   - Once it reaches 49,999,999 (i.e., `count - 1`), the LED toggles and the counter resets.
3. If `switch` is low:
   - The LED stays off, and the counter remains at 0.

---

## 🔢 Parameter

- `count = 50,000,000`  
  ➤ Assumes a 50 MHz clock input  
  ➤ Blinks LED at approximately **1 Hz** (1 toggle per second)

---

## 🛠️ Tools Used

- **Language:** Verilog HDL
- **Synthesis/Test:** Nexys A7 100T FPGA Board
- **Target Devices:** Any FPGA with 50MHz input (Basys 3 / Nexys A7 etc.)

---

## 📜 License

MIT License – Use freely with attribution.

---

## ✍️ Author

- **Naveen Kumar B**
- Date: July 2025
```
