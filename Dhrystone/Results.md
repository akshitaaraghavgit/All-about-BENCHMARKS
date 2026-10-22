# PicoRV32 Dhrystone — Results

## 1. Benchmark Overview

- **Core:** PicoRV32
- **Benchmark:** Dhrystone 2.1
- **Execution environment:** RTL simulation using Icarus Verilog
- **Simulation runner:** `vvp`
- **Workload:** 100 Dhrystone runs
- **Validation:** Printed benchmark variables match their expected values

## 2. Configuration

| Setting | Value |
|---|---|
| Compiler | `riscv64-unknown-elf-gcc` |
| Compiler version | 14.2.0 |
| Architecture | `rv32im` |
| ABI | `ilp32` |
| Optimization | `-O3` |
| Custom library | Enabled (`USE_MYSTDLIB = 1`) |
| Freestanding build | Enabled |
| Standard library linking | Disabled (`-nostdlib`) |
| Simulator | Icarus Verilog 12.0 |

Compiler flags:

```text
-MD -O3 -mabi=ilp32 -march=rv32im -DTIME -DRISCV
-DUSE_MYSTDLIB -ffreestanding -nostdlib
```

## 3. Performance Results

| Metric | Result |
|---|---:|
| Number of runs | 100 |
| User time | 139,391 cycles |
| Instructions | 35,725 |
| Cycles per instruction (CPI) | 3.901 |
| Dhrystones per second per MHz | 717 |
| DMIPS per MHz | 0.408 |

## 4. Correctness Validation

The benchmark printed the expected values for the checked variables, including:

- `Int_Glob = 5`
- `Bool_Glob = 1`
- `Ch_1_Glob = A`
- `Ch_2_Glob = B`
- `Arr_1_Glob[8] = 7`
- `Arr_2_Glob[8][7] = 110`
- `Int_1_Loc = 5`
- `Int_2_Loc = 13`
- `Int_3_Loc = 7`

The pointer structures, enumeration values, and string variables also matched the expected output.

**Status:** Benchmark completed; visible correctness checks passed.

## 5. Reproduction

From the PicoRV32 repository:

```bash
cd ~/picorv32/dhrystone
make dhry.hex
make test
```

The build requires a compatible RISC-V toolchain, and the simulation requires Icarus Verilog and `vvp`.

The Makefile must use the toolchain prefix and custom-library configuration documented above.

## 6. Interpretation and Limitations

These results were obtained from RTL simulation, not a physical FPGA.

The reported `DMIPS/MHz` is a normalized performance metric. It should only be compared with results that use compatible benchmark versions, compiler settings, core configurations, and measurement methodologies.

The reported 139,391 cycles and 35,725 instructions are the benchmark's reported user-execution counts. They should not be assumed to represent the entire simulation's cycle and instruction totals.

The testbench prints `TRAP` after the core raises its trap signal and then terminates the simulation using `$finish`. In this testbench, that message is the termination mechanism rather than evidence of a benchmark failure.

<img width="486" height="165" alt="dhrystone1" src="https://github.com/user-attachments/assets/92afc020-6450-49f9-8b91-0578156adfae" />
