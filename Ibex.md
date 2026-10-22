
# Ibex — Benchmark Analysis

## 1. Core Overview

- **Official Repository:** https://github.com/lowRISC/ibex
- **Developer / Maintainer:** lowRISC
- **Core Name:** Ibex
- **Architecture:** 32-bit RISC-V (RV32)
- **Implementation Language:** SystemVerilog
- **ISA Support:** RV32I or RV32E, with configurable M, C, and B extensions
- **Core Type:** In-order processor designed for embedded control applications
- **Pipeline:** Configurable pipeline; performance configurations can include a writeback stage
- **Primary Design Goal:** Small, configurable, production-quality RISC-V CPU with extensive verification

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone | Not verified | No normalized Dhrystone result recorded from the official sources checked | Not verified |
| CoreMark | 0.904 CoreMark/MHz | micro configuration; RV32EC | Found |
| CoreMark | 2.47 CoreMark/MHz | small configuration; RV32IMC, 3-cycle multiplier | Found |
| CoreMark | 3.13 CoreMark/MHz | maxperf configuration; RV32IMC, 1-cycle multiplier, branch-target ALU and writeback stage | Found |
| CoreMark | 3.13 CoreMark/MHz | maxperf-pmp-bmfull configuration; RV32IMCB, 1-cycle multiplier, branch-target ALU, writeback stage and 16 PMP regions | Found |
| Embench | Not verified | No Ibex-specific result verified from the official sources checked | Not verified |
| Fmax | Not verified | No specific maximum-frequency result recorded from the official sources checked | Not verified |

**Important:** The CoreMark/MHz values are published in the official Ibex README. They are based on CoreMark running on the Ibex Simple System platform.

## 3. Published Hardware Area Information

The official README also reports synthesis-area estimates for selected configurations.

| Configuration | Yosys Area (kGE) | Estimated Commercial Area (kGE) |
|---|---:|---:|
| micro | 16.85 | ~15 |
| small | 26.60 | ~24 |
| maxperf | 32.48 | ~30 |
| maxperf-pmp-bmfull | 66.02 | ~61 |

- **Synthesis flow:** Yosys basic synthesis flow.
- **Register file:** Latch-based register file.
- **Commercial area:** Rough estimate, not a measured result from a specified commercial implementation.

These are area results, not Fmax results.

## 4. Benchmark Configuration Notes

- **Benchmark platform:** Ibex Simple System.
- **CoreMark source:** Vendored under `vendor/eembc_coremark` in the official repository.
- **Build instructions:** `examples/sw/benchmarks/README.md`.
- **CoreMark build directory:** `examples/sw/benchmarks/coremark`.
- **CoreMark configuration:** The reported score depends on the selected Ibex configuration, ISA extensions, compiler and memory system.
- **Dhrystone compiler and flags:** Not verified.
- **Embench configuration:** Not verified.
- **Fmax device, timing constraints and implementation tool:** Not verified.

## 5. Core Features Relevant to Benchmarking

- Configurable RISC-V ISA extensions.
- Different multiplier architectures and performance configurations.
- Optional branch-target ALU and writeback stage.
- Configurable security and physical memory protection features.
- Simple System platform for running software in simulation.
- Official build and run instructions for CoreMark.
- Synthesis flow for estimating hardware area.

## 6. Findings

- The official repository publishes CoreMark/MHz results for four named configurations.
- The maxperf configuration reports 3.13 CoreMark/MHz.
- The micro configuration reports 0.904 CoreMark/MHz, illustrating the performance differences between configurations.
- The official repository provides synthesis-area figures alongside benchmark performance.
- Dhrystone and Embench results have not been verified in the official sources checked for this entry.
- Fmax requires a separate implementation-specific timing result; CoreMark/MHz cannot be used to infer it.
- Results should be compared with other cores only after considering configuration, compiler flags, memory system and implementation technology.

## 7. Official References

1. **Official Ibex repository and benchmark summary:**  
   https://github.com/lowRISC/ibex

2. **Official benchmark documentation:**  
   https://github.com/lowRISC/ibex/blob/master/examples/sw/benchmarks/README.md

3. **CoreMark build instructions:**  
   https://github.com/lowRISC/ibex/tree/master/examples/sw/benchmarks/coremark

4. **Ibex configuration definitions:**  
   https://github.com/lowRISC/ibex/blob/master/ibex_configs.yaml

5. **Official synthesis documentation:**  
   https://github.com/lowRISC/ibex/blob/master/syn/README.md

## 8. Research Notes

- **Analysis type:** Published benchmark and hardware-area analysis.
- **Source policy:** Official lowRISC Ibex repository only.
- **Date accessed:** 22 October 2026.
- **Limitations:** "Not verified" means a result was not confirmed in the official sources checked; it does not establish that no result exists.


