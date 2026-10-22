# dhry_1.c — Main Benchmark Program

## Purpose
`dhry_1.c` contains the main Dhrystone benchmark program. It initialises the benchmark data, executes the main loop, and reports performance measurements.

## Key Components

| Component | Role |
|---|---|
| Global variables | Store benchmark data used by the program. |
| Arrays and structures | Provide data for memory access and manipulation. |
| Initialisation | Sets up variables and data structures before measurement. |
| Main loop | Repeatedly executes the benchmark workload. |
| Function calls | Invokes procedures and functions from the Dhrystone source files. |
| Measurement | Records execution information, including cycles and instructions in this RISC-V configuration. |
| Validation | Prints final variable values so the results can be checked. |

## Execution Flow

1. Initialise variables, arrays, and structures.
2. Set up the measurement mechanism.
3. Execute the benchmark loop.
4. Call the required Dhrystone procedures and functions.
5. Record and display execution measurements.
6. Print final values for validation.

## Role in This Project

The file is compiled with `dhry_2.c` and `dhry.h` as part of the Dhrystone build for PicoRV32.

The resulting program is converted into a HEX image and executed in the processor simulation.

## Source

Original source: [PicoRV32 — Dhrystone](https://github.com/YosysHQ/picorv32/tree/main/dhrystone)
