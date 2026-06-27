IEEE-754 FP16 Floating-Point Adder & Multiplier on FPGA

This project implements an IEEE-754 Half-Precision (FP16) Floating-Point Arithmetic Unit using Verilog HDL and deploys it on an FPGA development board. The design supports both floating-point addition and multiplication while handling IEEE-754 special cases such as NaN, Infinity, Zero, Subnormal, and Normal numbers.

The system allows users to enter operands using hardware switches, select arithmetic operations through push buttons, and display the computed FP16 result on an 8-digit seven-segment display. Button presses are synchronized using hardware debouncing and one-pulse generation to ensure reliable operation.


A. Features:-

1) IEEE-754 Half-Precision (FP16) floating-point arithmetic
2) Floating-point Addition
3) Floating-point Multiplication
4) Complete FP16 number classification
5) IEEE-754 compliant normalization and exponent bias handling
6) Overflow and underflow detection
7) Real-time hardware input using FPGA switches
8) Debounced push-button interface
9) Seven-segment hexadecimal output display
10) Modular Verilog implementation

B. IEEE-754 FP16 Format:-

The represented value is
(-1)^Sign × 1.Fraction(Mantissa) × 2^(Exponent − 15)

C. Project Modules
1) top_fp_display
- Top-level integration module
- Handles operand loading
- Controls operation selection (ADD/MUL)
- Stores computation results
- Interfaces with display hardware

2) hp_class
- FP16 classifier responsible for extracting sign, exponent, and mantissa
- Detecting whether its Zero , Subnormal , Normal , Infinity or NaN
- Adding the hidden leading bit for normalized numbers
- Providing classification information to arithmetic units

3) hp_add
- Implements IEEE-754 FP16 addition
- Exponent comparison
- Mantissa alignment
- Signed addition/subtraction
- Result normalization
- Exponent rebiasing
- Overflow and underflow handling
- IEEE-754 compliant result packing

4) hp_mul
- Implements IEEE-754 FP16 multiplication
- 11 × 11-bit significand multiplication
- Exponent addition with bias correction
- Product normalization
- Overflow/underflow detection
- IEEE-754 compliant FP16 result generation

5) debounce
- Eliminates mechanical switch bouncing to ensure stable button inputs.

6) one_pulse
- Generates a single clock-cycle pulse for every button press, preventing multiple unintended operations.

7) display32_hex
- Drives the 8-digit seven-segment display
- Time-multiplexed display control
- Displays the FP16 result in hexadecimal format

D. Technologies Used
1) Verilog HDL
2) FPGA Development Board
3) IEEE-754 Floating-Point Standard
4) Digital Logic Design
5) Seven-Segment Display Interface

E. Future Improvements
- Support for FP32 arithmetic
- Floating-point subtraction module
- Fused Multiply-Add (FMA)
- IEEE-754 rounding modes
- Division and square-root operations
- Pipelined architecture for higher throughput
- Comprehensive verification testbench with corner-case coverage


