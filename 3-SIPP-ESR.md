# 3-SIPP-ESR

## Core Overview

| Property | Details |
|---|---|
| Core | 3-SIPP-ESR |
| Developer | OR5-LABS |
| Architecture | RISC-V, 32-bit |
| ISA | `RV32IMACB_Zicsr_Zcb_Zbc_Zifencei` |
| Pipeline | 3-stage, in-order |
| Branch Prediction | 256-entry gshare, 64-entry BTB, and RAS |
| RTL Language | SystemVerilog |
| Target FPGA | AMD/Xilinx Artix-7 100T |
| Evaluation Board | Digilent Arty A7 |
| RTOS Support | FreeRTOS |
| Simulation Tool | Verilator |
| FPGA Implementation Tool | AMD Vivado 2023.2 |

3-SIPP-ESR is a compact, pipelined RISC-V processor core with branch prediction, hardware multiply/divide support, debugging capabilities, and optional security features.

Official repository: https://github.com/OR5-LABS/3-SIPP-ESR

## Published Benchmark Results

The official repository reports CoreMark and Dhrystone 2.1 results measured using cycle-accurate Verilator simulation at a 100 MHz equivalent clock.

| Benchmark | Published Result | Execution Configuration |
|---|---:|---|
| CoreMark | 2.92 CoreMark/MHz | 100 iterations |
| Dhrystone 2.1 | 1.26 DMIPS/MHz | 2,000,000 runs |
| Embench-IoT | Not verified in official sources checked | — |
| Fmax | Not verified as a maximum achieved frequency in the benchmark report | — |

**Important:** The benchmark results are simulation-based. The 100 MHz equivalent simulation clock is not evidence that the FPGA implementation achieved a 100 MHz maximum clock frequency.

## Dhrystone Results

Dhrystone is a synthetic benchmark that evaluates general-purpose integer workloads, including operations involving strings, variables, and control flow.

| Metric | Published Result |
|---|---:|
| Benchmark | Dhrystone 2.1 |
| Number of Runs | 2,000,000 |
| Cycles per Iteration | 450 |
| Dhrystones per Second at 100 MHz | 222,222 |
| DMIPS at 100 MHz | 126.48 |
| DMIPS/MHz | 1.26 |
| Compiler Optimization | `-O2` |
| ISA Flag | `-march=rv32imc` |
| ABI | `-mabi=ilp32` |

### Compiler Flags

```text
-O2 -march=rv32imc -mabi=ilp32 -nostdlib -fno-pic -Wl,--no-relax
```

The official report states that the benchmark uses synchronous, single-cycle instruction and data memories without instruction or data caches. The reported score therefore reflects this simulated memory configuration.

## CoreMark Results

CoreMark evaluates integer processing through workloads such as linked-list processing, matrix operations, state-machine operations, and CRC calculations.

| Metric | Published Result |
|---|---:|
| Benchmark | CoreMark |
| Iterations | 100 |
| Cycles per Iteration | 341,599 |
| Iterations per Second at 100 MHz | 292 |
| CoreMark/MHz | 2.92 |
| Compiler Optimization | `-O2` |
| ISA Flag | `-march=rv32im` |
| ABI | `-mabi=ilp32` |

### Compiler Flags

```text
-O2 -march=rv32im -mabi=ilp32 -nostdlib -fno-pic -Wl,--no-relax -fno-builtin
```

The benchmark uses a bare-metal `barebones` configuration and the `riscv-none-elf-gcc` toolchain.

## Embench-IoT Results

**Status: Not verified in official sources checked.**

The repository's published benchmark report documents CoreMark and Dhrystone 2.1. An official Embench-IoT result was not identified in those sources.

This does not establish that Embench has never been run on the core; it means a published result could not be verified from the sources checked.

## Fmax Results

**Status: Not verified as a numerical maximum frequency in the official benchmark report.**

The repository identifies the Artix-7 100T and Digilent Arty A7 as the target FPGA platform. However, the benchmark report's 100 MHz equivalent simulation clock is not an Fmax result.

Fmax should be documented separately using an FPGA implementation's timing reports, including the target device, timing constraints, and achieved timing result.

## FPGA Resource Utilization

The official README reports synthesis and implementation results using AMD Vivado 2023.2 for the Xilinx Artix-7 100T (`xc7a100tcsg324-1`).

| Configuration | Slice LUTs | Registers (FF) | DSP48E1 | BRAM (36 Kb) |
|---|---:|---:|---:|---:|
| Core Only — M-mode | 7,418 (11.7%) | 2,092 (1.6%) | 12 (5.0%) | 0 |
| Core Only — Secure M+U mode | 8,647 | 2,993 | 12 | 0 |
| Full Evaluation SoC | 6,646 (10.5%) | 2,147 (1.7%) | 12 (5.0%) | 8 (5.9%) |

The Full Evaluation SoC includes the processor core, CLINT timer, UART, GPIO, and 32 KB of dedicated true dual-port block RAM.

**Note:** Resource utilization measures hardware area, not maximum clock frequency. These figures should not be used as substitutes for Fmax.

## Benchmark Configuration Notes

- **Simulation environment:** Verilator 5.0 or later.
- **Equivalent clock:** 100 MHz.
- **Compiler:** `riscv-none-elf-gcc` or a compatible RISC-V GCC toolchain.
- **CoreMark:** 100 iterations, `-O2`, bare-metal `barebones` port.
- **Dhrystone:** 2,000,000 runs, `-O2`.
- **Memory configuration:** No instruction or data caches; accesses use synchronous single-cycle instruction and data memories in the SoC model.
- **FPGA implementation:** AMD Vivado 2023.2, Xilinx Artix-7 100T.

## Reproducing the Benchmarks

Build the simulator from the repository root:

```bash
make
```

Run CoreMark:

```bash
cd coremark
./run_coremark.sh
```

Run Dhrystone:

```bash
cd dhrystone
./run_dhrystone.sh
```

Refer to the official benchmark report for the detailed methodology and published configuration.

## Core Features

- Three-stage in-order pipeline.
- Branch prediction using gshare, a branch target buffer, and a return address stack.
- RV32IMACB instruction support with additional extensions.
- Hardware multiply and divide.
- Optional machine and user privilege modes with physical memory protection.
- JTAG-based RISC-V external debugging.
- Verified FreeRTOS support.
- SystemVerilog RTL compatible with standard FPGA implementation workflows.

## Findings

1. The official repository publishes both CoreMark and Dhrystone results.
2. The reported results are based on Verilator simulation rather than measurements from a physical FPGA board.
3. Both published benchmark configurations use `-O2`, but their ISA flags differ; this should be considered when reproducing results.
4. The report explicitly identifies the absence of instruction and data caches in the simulated SoC configuration.
5. Embench-IoT and a numerical achieved Fmax were not verified in the official sources checked.
6. FPGA resource utilization is documented separately and must not be confused with Fmax.

## Official References

- **Main Repository:** https://github.com/OR5-LABS/3-SIPP-ESR
- **Official README:** https://github.com/OR5-LABS/3-SIPP-ESR/blob/main/README.md
- **Detailed Benchmark Report:** https://github.com/OR5-LABS/3-SIPP-ESR/blob/main/benchmarks.md
- **Tests and Verification:** https://github.com/OR5-LABS/3-SIPP-ESR/blob/main/tests.md

## Research Notes

This file records results and configurations published in the official project repository. Unverified metrics are deliberately left unspecified rather than estimated or inferred from other cores. Benchmark comparisons should account for compiler versions, optimization flags, ISA extensions, memory configuration, simulation versus hardware execution, and clock-frequency measurement methodology.
