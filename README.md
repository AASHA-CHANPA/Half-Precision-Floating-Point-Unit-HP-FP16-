IEEE-754 FP16 Floating-Point Adder & Multiplier on FPGA
Overview
This project implements an IEEE-754 Half-Precision (FP16) Floating-Point Arithmetic Unit using Verilog HDL and deploys it on an FPGA development board. The design supports both floating-point addition and multiplication while handling IEEE-754 special cases such as NaN, Infinity, Zero, Subnormal, and Normal numbers.
The system allows users to enter operands using hardware switches, select arithmetic operations through push buttons, and display the computed FP16 result on an 8-digit seven-segment display. Button presses are synchronized using hardware debouncing and one-pulse generation to ensure reliable operation.

Features
IEEE-754 Half-Precision (FP16) floating-point arithmetic
Floating-point Addition
Floating-point Multiplication
Complete FP16 number classification
Zero
Subnormal
Normal
Infinity
NaN
IEEE-754 compliant normalization and exponent bias handling
Overflow and underflow detection
Real-time hardware input using FPGA switches
Debounced push-button interface
Seven-segment hexadecimal output display
Modular Verilog implementation

IEEE-754 FP16 Format
Field
Bits
Sign
1
Exponent
5
Fraction (Mantissa)
10

The represented value is
(-1)^Sign × 1.Fraction × 2^(Exponent − 15)

The implementation correctly supports:
Normal numbers
Subnormal numbers
Positive and Negative Zero
Positive and Negative Infinity
Quiet and Signaling NaN


Project Modules
top_fp_display
Top-level integration module
Handles operand loading
Controls operation selection (ADD/MUL)
Stores computation results
Interfaces with display hardware

hp_class
FP16 classifier responsible for
Extracting sign, exponent, and mantissa
Detecting
Zero
Subnormal
Normal
Infinity
NaN
Adding the hidden leading bit for normalized numbers
Providing classification information to arithmetic units

hp_add
Implements IEEE-754 FP16 addition.
Features include:
Exponent comparison
Mantissa alignment
Signed addition/subtraction
Result normalization
Exponent rebiasing
Overflow and underflow handling
IEEE-754 compliant result packing

hp_mul
Implements IEEE-754 FP16 multiplication.
Features include:
11 × 11-bit significand multiplication
Exponent addition with bias correction
Product normalization
Overflow/underflow detection
IEEE-754 compliant FP16 result generation

debounce
Eliminates mechanical switch bouncing to ensure stable button inputs.

one_pulse
Generates a single clock-cycle pulse for every button press, preventing multiple unintended operations.

display32_hex
Drives the 8-digit seven-segment display
Time-multiplexed display control
Displays the lower 16 bits as the FP16 result in hexadecimal format

Design Highlights
Fully modular Verilog HDL implementation
IEEE-754 compliant arithmetic
Robust exception handling
Hardware-friendly architecture
Real-time operation on FPGA
Reliable user interface using debounced controls
Clean separation between datapath and control logic

Technologies Used
Verilog HDL
FPGA Development Board
IEEE-754 Floating-Point Standard
Digital Logic Design
Seven-Segment Display Interface

Repository Structure

├── top_fp_display.v

├── hp_add.v

├── hp_mul.v

├── hp_class.v

├── debounce.v

├── one_pulse.v

├── display32_hex.v

├── constraints/

├── simulation/

├── images/

└── README.md

Future Improvements
Support for FP32 arithmetic
Floating-point subtraction module
Fused Multiply-Add (FMA)
IEEE-754 rounding modes
Division and square-root operations
Pipelined architecture for higher throughput
Comprehensive verification testbench with corner-case coverage

Learning Outcomes
This project provided practical experience in:
IEEE-754 floating-point arithmetic
Hardware implementation of arithmetic units
Verilog HDL design methodology
FPGA prototyping
Modular digital system design
Exception handling in floating-point computation
Hardware debugging and verification

Authors
Aasha Chanpa
B.Tech Electronics Engineering
Astha Patel
B.Tech Electronics Engineering
