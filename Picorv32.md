
# PicoRV32 — Benchmark Analysis

## 1. Core Overview

- **Official Repository:** https://github.com/YosysHQ/picorv32
- **Developer:** YosysHQ
- **Core Type:** Size-optimized RISC-V CPU
- **Architecture:** RV32
- **ISA Support:** Configurable RV32E, RV32I, RV32IC, RV32IM, and RV32IMC
- **Implementation Language:** Verilog
- **Interfaces:** Native memory interface, AXI4-Lite, and Wishbone variants
- **License:** ISC
- **Primary Design Goal:** Small hardware footprint and high maximum clock frequency

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone | 0.516 DMIPS/MHz; 908 Dhrystones/s/MHz | ENABLE_FAST_MUL, ENABLE_DIV, and BARREL_SHIFTER enabled | Found |
| Dhrystone CPI | Average CPI: 4.100 | Configuration stated in the official README | Found |
| CoreMark | Not verified | No result recorded from the official source checked | Not verified |
| Embench | Not verified | No result recorded from the official source checked | Not verified |
| Fmax | 416–769 MHz across listed FPGA devices and speed grades | PicoRV32 AXI variant with TWO_CYCLE_ALU enabled; Vivado 2017.3 | Found |

**Official benchmark source:**  
https://github.com/YosysHQ/picorv32

## 3. Fmax Results — Published FPGA Timing

The official repository reports place-and-route timing results for the `picorv32_axi` module with `TWO_CYCLE_ALU` enabled.

| FPGA Device | Speed Grade | Clock Period | Frequency |
|---|---|---:|---:|
| Kintex-7T | -2 | 2.4 ns | 416 MHz |
| Kintex-7T | -3 | 2.2 ns | 454 MHz |
| Virtex-7T | -2 | 2.3 ns | 434 MHz |
| Virtex-7T | -3 | 2.2 ns | 454 MHz |
| Kintex UltraScale | -2 | 2.0 ns | 500 MHz |
| Kintex UltraScale | -3 | 1.8 ns | 555 MHz |
| Virtex UltraScale | -2 | 2.1 ns | 476 MHz |
| Virtex UltraScale | -3 | 2.0 ns | 500 MHz |
| Kintex UltraScale+ | -2 | 1.4 ns | 714 MHz |
| Kintex UltraScale+ | -3 | 1.3 ns | 769 MHz |
| Virtex UltraScale+ | -2 | 1.5 ns | 666 MHz |
| Virtex UltraScale+ | -3 | 1.4 ns | 714 MHz |

**Timing tool:** Vivado 2017.3  
**Method:** Place-and-route timing evaluation using a binary search for the shortest clock period meeting timing.

These results apply to the listed hardware configurations and should not be treated as a universal Fmax for every PicoRV32 implementation.

## 4. Benchmark Configuration Notes

- **Dhrystone configuration:** ENABLE_FAST_MUL, ENABLE_DIV, and BARREL_SHIFTER enabled.
- **Reported Dhrystone score without look-ahead memory interface:** 0.305 DMIPS/MHz.
- **Reported CPI without look-ahead memory interface:** 5.232.
- **Dhrystone compiler flags:** The exact flags associated with the published score were not verified.
- **CoreMark configuration:** Not verified.
- **Embench configuration:** Not verified.
- **Fmax tool and version:** Vivado 2017.3.
- **Fmax configuration:** `picorv32_axi` with `TWO_CYCLE_ALU` enabled.

## 5. Core Features Relevant to Benchmarking

- Configurable ISA and optional instruction extensions.
- Optional multiplier, divider, barrel shifter, and interrupt support.
- Native memory interface with optional look-ahead signals.
- AXI4-Lite and Wishbone interface variants.
- Different configuration choices can affect performance, area, and achievable clock frequency.

## 6. Findings

- The official README provides a published Dhrystone score and average CPI.
- The repository also provides FPGA timing results for multiple device families and speed grades.
- The published Fmax values are implementation-specific and depend on the FPGA and core configuration.
- CoreMark and Embench results have not been verified from the official source checked.
- The available figures do not establish a controlled head-to-head comparison with other RISC-V cores.


