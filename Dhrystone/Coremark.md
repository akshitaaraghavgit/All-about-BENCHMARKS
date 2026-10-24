# CoreMark Benchmark — PicoRV32

## 1. Objective

To execute the CoreMark 1.0 benchmark on the PicoRV32 RISC-V processor using simulation and evaluate its functional correctness and performance.

## 2. Experimental Environment

| Parameter | Details |
|---|---|
| Processor Core | PicoRV32 |
| ISA Configuration | RV32IM with Zicsr |
| Benchmark | CoreMark 1.0 |
| Compiler | GCC 14.2.0 |
| Compiler Optimization | `-O3` |
| Simulation Tool | Icarus Verilog 12.0 |
| Execution Environment | Ubuntu Linux |
| Output Method | Memory-mapped character output |

## 3. Benchmark Results

| Metric | Result |
|---|---:|
| CoreMark Size | 666 |
| Iterations Completed | 10 |
| Total Reported Ticks | 11,266,309 |
| Average Ticks per Iteration | 1,126,630.9 |
| Final CRC | `0xfcaf` |
| Correctness Validation | Passed |
| Program Termination | Successful |

## 4. Correctness Verification

The simulation completed successfully and produced the following validation messages:

- `Correct operation validated.`
- `CoreMark 1.0`
- `DONE`
- `TRAP`

The benchmark reported the following CRC values:

| Check | CRC |
|---|---:|
| Seed CRC | `0xe9f5` |
| List CRC | `0xe714` |
| Matrix CRC | `0x1fd7` |
| State CRC | `0x8e3a` |
| Final CRC | `0xfcaf` |

These results indicate that the benchmark completed its functional validation for this run.

## 5. Timing and Performance Analysis

The custom port reads the RISC-V `cycle` CSR at the beginning and end of the timed region.

The reported average is:

**Average reported ticks per iteration = Total reported ticks / Iterations**

= 11,266,309 / 10

= **1,126,630.9 ticks per iteration**

The counter's behavior and the relationship between reported ticks and processor cycles must be verified before treating this value as a definitive cycle count.

CoreMark/MHz is not reported as a final metric in this experiment because the timing method and processor-frequency assumptions have not yet been independently verified.

## 6. Limitations

- The benchmark was executed in simulation rather than on a physical FPGA board.
- The run used 10 iterations; longer runs are required for more robust performance measurements.
- Floating-point summary formatting was disabled in the custom output implementation.
- The custom port, compiler flags, and benchmark configuration should be documented when comparing results with other implementations.
- Results should not be compared directly with published CoreMark scores unless the measurement methodology and benchmark configuration are compatible.

## 7. Conclusion

CoreMark 1.0 was successfully compiled, linked, and executed on the PicoRV32 simulation environment. The run completed its correctness checks and reported 11,266,309 ticks over 10 iterations.

This establishes a successful functional benchmark run. Further timing verification and repeatability testing are required before publishing a definitive performance score.

## 8. Future Work

- Verify the behavior of the RISC-V cycle counter.
- Increase the number of benchmark iterations.
- Repeat the benchmark to assess consistency.
- Record the exact source changes and build configuration.
- Investigate a reliable timing method for reporting performance metrics.
- Compare results with other processor implementations using consistent conditions.

  <img width="1848" height="724" alt="coremark1" src="https://github.com/user-attachments/assets/51862456-148f-4ce3-85cb-6463cbedf499" />

