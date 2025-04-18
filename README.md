# Moore Machine Sequence Detector (001) in Verilog

This project implements a Moore Machine in Verilog that detects the sequence "001" in a serial input stream. The machine sets the output `det` to 1 when the sequence "001" is detected (i.e., when the machine reaches state `s3`). A testbench is included to verify the machine’s functionality across various input sequences, including correct detections, incorrect sequences, and overlapping patterns.

## Project Overview

The Moore Machine is a finite state machine (FSM) where the output depends only on the current state (unlike a Mealy Machine, where the output depends on both the state and input). This design uses four states to detect the sequence "001":
- `s0`: Initial state (no zeros seen).
- `s1`: One zero seen.
- `s2`: Two zeros seen (waiting for a 1).
- `s3`: Sequence "001" detected (output `det=1`).

The machine sets `det` to 1 when in state `s3`, which is reached after seeing "001". It supports overlapping sequences by transitioning from `s3` to `s1` on `inp=0` (allowing a new sequence to start) or `s0` on `inp=1`. The machine is synchronous, with state transitions occurring on the rising edge of the clock, and includes a synchronous reset to return to `s0`.

### Files in the Project

- **`seq_moore_001.sv`**: The main Verilog module implementing the Moore Machine. It defines the state machine logic for detecting the sequence "001".

- **`seq_moore_001_tb.sv`**: The testbench for the Moore Machine. It tests various input sequences to verify correct detection, non-detection, overlapping sequences, and reset behavior.

- **`README.md`**: This file, providing documentation and instructions for the project.
