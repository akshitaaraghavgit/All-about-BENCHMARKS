
# SonicBOOM (BOOMv3) — Benchmark Analysis

## 1. Core Overview

- **Official Repository:** https://github.com/riscv-boom/riscv-boom
- **Developer:** Berkeley Architecture Research, University of California, Berkeley
- **Core Name:** SonicBOOM (BOOMv3)
- **Architecture:** 64-bit RISC-V (RV64)
- **ISA Support:** RV64GC; additional extensions depend on configuration
- **Implementation Language:** Chisel (hardware construction language)
- **Core Type:** Superscalar, out-of-order processor
- **Pipeline:** Out-of-order execution pipeline
- **Primary Design Goal:** High-performance, synthesizable RISC-V processor for computer architecture research
- **Integration Framework:** Chipyard
- **License:** BSD-3-Clause (check individual files for any additional licensing terms)

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone | Not verified | No normalized DMIPS/MHz result verified in the official sources checked | Not verified |
| CoreMark | 6.2 CoreMarks/MHz | SonicBOOM / BOOMv3; exact benchmark build configuration requires further verification | Found |
| Embench | Not verified | No SonicBOOM-specific result verified in the official sources checked | Not verified |
| Fmax | Not verified | No specific maximum-frequency result recorded from the official sources checked | Not verified |

**Important:** The official SonicBOOM repository reports 6.2 CoreMarks/MHz. This is a published performance figure, not a result independently reproduced as part of this analysis.

## 3. Published Hardware and Architecture Information

| Parameter | Published Information |
|---|---|
| ISA | RISC-V RV64GC |
| Execution model | Out-of-order |
| Issue capability | Superscalar |
| Synthesizable | Yes |
| FPGA support | Yes |
| Floating-point support | IEEE 754 floating point |
| Atomic instructions | Supported |
| Caches | Supported |
| Virtual memory | Supported |
| Operating system support | Can boot Linux |
| SPEC benchmark support | Listed in the official repository |

These are architectural capabilities, not benchmark scores or timing results.

## 4. Benchmark Configuration Notes

- **CoreMark:** 6.2 CoreMarks/MHz, as published in the official repository.
- **CoreMark compiler and flags:** Exact settings associated with the published figure were not verified.
- **Dhrystone configuration:** Not verified.
- **Embench configuration:** Not verified.
- **Fmax device and timing constraints:** Not verified.
- **Integration:** BOOM is not a self-running repository; the official documentation recommends using Chipyard to instantiate the core within an SoC.
- **Comparability:** The reported CoreMark/MHz result should not be directly compared with results from other cores without checking benchmark settings, compiler options, memory system, and configuration.

## 5. Core Features Relevant to Benchmarking

- Out-of-order instruction execution.
- Superscalar execution.
- Branch prediction.
- Instruction and data caches.
- Virtual memory support.
- Floating-point and atomic instruction support.
- Configurable processor implementation.
- Integration with Chipyard for SoC generation.
- Support for simulation and FPGA implementation.

## 6. Findings

- The official repository publishes a CoreMark result of 6.2 CoreMarks/MHz for SonicBOOM / BOOMv3.
- SonicBOOM is designed for high performance and uses out-of-order execution, unlike small in-order cores such as SERV and Ibex.
- The repository documents synthesizable RTL and integration through Chipyard.
- Dhrystone and Embench results have not been verified in the official sources checked.
- An implementation-specific Fmax result remains to be verified from an official timing report.
- CoreMark/MHz alone is insufficient to compare overall processor performance, area, power, or maximum clock frequency.

## 7. Official References

1. **Official SonicBOOM repository:**  
   https://github.com/riscv-boom/riscv-boom

2. **Official BOOM documentation:**  
   https://github.com/riscv-boom/riscv-boom/tree/master/docs

3. **Official SonicBOOM v3 release notes:**  
   https://github.com/riscv-boom/riscv-boom/releases

4. **Official CoreMark wrapper for RISC-V:**  
   https://github.com/riscv-boom/riscv-coremark

5. **Official Chipyard framework:**  
   https://github.com/ucb-bar/chipyard

## 8. Research Notes

- **Analysis type:** Published benchmark and architecture analysis.
- **Source policy:** Official BOOM / Berkeley project sources only.
- **Date accessed:** 22 October 2026.
- **Limitations:** "Not verified" means a result was not confirmed in the official sources checked; it does not prove that no result exists.
