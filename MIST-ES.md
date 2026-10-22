
# MIST-ES — Benchmark Analysis

## 1. Core Overview

- **Official Repository:** https://github.com/OR5-LABS/MIST-ES
- **Developer:** OR5-LABS
- **Core Name:** MIST-ES
- **Architecture:** 32-bit RISC-V (RV32)
- **ISA Support:** RV32IMC_Zicsr
- **Implementation Language:** SystemVerilog
- **Core Type:** Multi-cycle, non-pipelined processor
- **Microarchitecture:** Deterministic finite-state machine (FSM)
- **Privilege Modes:** Machine mode; optional User mode in SECURE configuration
- **Primary Design Goal:** Area-optimized, verified processor for embedded systems and FPGA applications
- **Target FPGA:** AMD/Xilinx Artix-7 100T
- **Reference Board:** Digilent Arty A7
- **License:** MIT

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone 2.1 | 0.388 DMIPS/MHz; 683 Dhrystones/s/MHz | 100,000 runs; cycle-accurate Verilator simulation | Found |
| CoreMark | 1.18 CoreMark/MHz | 1,000 iterations; cycle-accurate Verilator simulation | Found |
| Embench | Not verified | No Embench result reported in the official repository checked | Not verified |
| Fmax | Not verified | FPGA implementation details are provided, but no maximum-frequency value was verified in the benchmark report | Not verified |

## 3. Dhrystone Results

| Metric | Published Result |
|---|---:|
| Benchmark version | Dhrystone 2.1 |
| Number of runs | 100,000 |
| Total cycles | 146,300,070 |
| Retired instructions | 49,200,030 |
| Cycles per instruction (CPI) | 2.973 |
| Dhrystones/sec/MHz | 683 |
| DMIPS/MHz | 0.388 |
| Internal variable verification | PASS |

### Dhrystone Build Configuration

- **Compiler:** `riscv-none-elf-gcc 13.2.0`
- **Optimization:** `-O2`
- **Architecture:** `-march=rv32imc_zicsr`
- **ABI:** `-mabi=ilp32`
- **Run-count definition:** `-DNUM_RUNS=100000`
- **Simulation:** Cycle-accurate Verilator

## 4. CoreMark Results

| Metric | Published Result |
|---|---:|
| Benchmark version | EEMBC CoreMark v1.0 |
| Iterations | 1,000 |
| Total cycles in timed window | 847,547,135 |
| Cycles per iteration | 847,547.1 |
| CoreMark/MHz | 1.1799 (~1.18) |
| CRC validation | PASS |

### CoreMark Build Configuration

- **Compiler:** `riscv-none-elf-gcc` (xPack GNU RISC-V Embedded GCC 13.2.0)
- **Optimization:** `-O2`
- **Architecture:** `-march=rv32imc_zicsr`
- **ABI:** `-mabi=ilp32`
- **Memory allocation:** Static allocation
- **Linker configuration:** Harvard architecture using `bench.ld`
- **Simulation:** Cycle-accurate Verilator

## 5. FPGA Resource Utilization

The official repository reports synthesis and implementation using AMD Vivado 2023.2 for the Xilinx Artix-7 100T (`xc7a100tcsg324-1`).

| Configuration | Slice LUTs | Registers (FFs) | DSP48E1 | BRAM |
|---|---:|---:|---:|---:|
| Core — Default | 2,491 | 749 | 4 | 0 |
| Core — SECURE | 4,362 | 1,400 | 4 | 0 |
| Full SoC — Default, 128 KB BRAM | 2,816 | 1,335 | 4 | 32 |
| Full SoC — SECURE, 128 KB BRAM | 5,226 | 1,980 | 4 | 32 |

**Note:** These figures describe hardware resource utilisation. They are not Fmax results.

## 6. Benchmark Configuration Notes

- **Dhrystone:** 100,000 runs with GCC 13.2.0 and `-O2`.
- **CoreMark:** 1,000 iterations with GCC 13.2.0 and `-O2`.
- **Embench:** No published result verified in the official repository checked.
- **Fmax:** No numerical maximum-frequency result verified in the benchmark report.
- **Simulation tool:** Verilator 5.020, as reported in `benchmark.md`.
- **Implementation tool:** AMD Vivado 2023.2 for FPGA resource reporting.
- **Configuration distinction:** MIST-ES supports a default configuration and a SECURE configuration with User mode, PMP/ePMP, and register-file ECC.

## 7. Core Features Relevant to Benchmarking

- Multi-cycle FSM-based execution.
- No instruction pipeline or pipeline hazards.
- RV32IMC and Zicsr support.
- Hardware multiplication and division.
- Compressed-instruction support.
- Physical Memory Protection and enhanced PMP in SECURE mode.
- SECDED error-correcting register file in SECURE mode.
- Native memory interface and AXI4-Lite bridge.
- Cycle-accurate simulation and FPGA implementation flows.
- Automated ISA compliance and verification tests.

## 8. Findings

- The official repository publishes both CoreMark and Dhrystone results.
- CoreMark achieves 1.18 CoreMark/MHz in the reported simulation.
- Dhrystone achieves 0.388 DMIPS/MHz, with an average CPI of 2.973.
- Both benchmark results were measured using cycle-accurate Verilator simulation rather than a physical FPGA benchmark run.
- The repository reports FPGA resource utilisation for both default and SECURE configurations.
- Embench and a numerical Fmax value remain unverified in the official sources checked.
- Benchmark comparisons with other cores must account for compiler settings, simulation methodology, architecture, and memory configuration.

## 9. Official References

1. **Official MIST-ES repository:**  
   https://github.com/OR5-LABS/MIST-ES

2. **Official benchmark report:**  
   https://github.com/OR5-LABS/MIST-ES/blob/main/benchmark.md

3. **Official RTL source:**  
   https://github.com/OR5-LABS/MIST-ES/tree/main/rtl

4. **Official FPGA implementation files:**  
   https://github.com/OR5-LABS/MIST-ES/tree/main/fpga

5. **Official test report:**  
   https://github.com/OR5-LABS/MIST-ES/blob/main/tests_report.md

## 10. Research Notes

- **Analysis type:** Published benchmark, verification, and FPGA resource analysis.
- **Source policy:** Official OR5-LABS MIST-ES repository only.
- **Date accessed:** 22 October 2026.
- **Limitations:** Published simulation results are not equivalent to measurements from physical silicon or FPGA execution. "Not verified" means a result was not found in the official sources checked.
