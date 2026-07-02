# Synchronous-FIFO

# Synchronous FIFO (Verilog)

A parameterized **Synchronous FIFO (First-In-First-Out)** buffer designed in Verilog, supporting configurable data width and depth. This project demonstrates safe data transfer between read and write operations on a shared clock domain, with proper flag handling to prevent overflow and underflow conditions.

## 📌 Overview

A FIFO is a fundamental building block in digital systems, used to buffer data between two interfaces operating at potentially different rates but sharing a common clock. This project implements a synchronous FIFO using a pointer-based architecture with full and empty flag generation.

## ✨ Features

- Parameterized **data width** and **FIFO depth**
- Pointer-based read/write logic with wrap-around handling
- **Full** and **Empty** flag generation
- **Overflow** and **Underflow** protection
- Simultaneous read/write support
- Self-checking testbench for verification

## 🗂️ Repository Structure

```
├── src/
│   └── sync_fifo.v          # FIFO RTL design
├── tb/
│   └── sync_fifo_tb.v       # Testbench
├── sim/
│   └── waveform.vcd         # Simulation waveform (optional)
├── docs/
│   └── fifo_diagram.png     # Block diagram (optional)
└── README.md
```

## ⚙️ Design Details

| Parameter    | Description                     | Default |
|--------------|----------------------------------|---------|
| `DATA_WIDTH` | Width of data bus (bits)         | 8       |
| `FIFO_DEPTH` | Number of storage locations      | 16      |

**Ports:**

| Signal      | Direction | Description                  |
|-------------|-----------|-------------------------------|
| `clk`       | Input     | System clock                  |
| `rst_n`     | Input     | Active-low reset               |
| `wr_en`     | Input     | Write enable                   |
| `rd_en`     | Input     | Read enable                    |
| `data_in`   | Input     | Data to write                  |
| `data_out`  | Output    | Data read out                  |
| `full`      | Output    | FIFO full flag                 |
| `empty`     | Output    | FIFO empty flag                |

## 🧪 Verification

The design was verified using a self-checking testbench covering:
- Back-to-back write operations
- Back-to-back read operations
- Simultaneous read and write
- Full and empty boundary conditions
- Overflow and underflow protection checks

Simulated using Vivado & Edaplayground.

## 🚀 How to Run

```bash
# Example using Icarus Verilog
iverilog -o fifo_sim src/sync_fifo.v tb/sync_fifo_tb.v
vvp fifo_sim
gtkwave sim/waveform.vcd
```

## 📊 Results

- Verified correct functionality across all boundary and simultaneous read-write cases
- No data loss or corruption observed during simulation
- *(Add clock frequency, FPGA synthesis results, or timing details if available)*

## 🛠️ Tools Used

- Verilog HDL
- Vivado
- Edaplayground

## 📖 Future Improvements

- Add asynchronous (dual-clock) FIFO variant
- Add programmable almost-full / almost-empty flags
- FPGA synthesis and timing closure report
