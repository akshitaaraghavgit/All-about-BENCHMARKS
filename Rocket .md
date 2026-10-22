
# Rocket Core — Benchmark Analysis

## 1. Core Overview

- **Official Repository:** https://github.com/chipsalliance/rocket-chip
- **Official Core Documentation:** https://github.com/ucb-bar/chipyard/blob/main/docs/Generators/Rocket.rst
- **Developer / Maintainer:** Originally developed at UC Berkeley and SiFive; maintained by Chips Alliance
- **Core Name:** Rocket
- **Architecture:** 64-bit RISC-V (RV64)
- **ISA Support:** RV64GC, with configurable ISA extensions
- **Implementation Language:** Chisel (hardware construction language embedded in Scala)
- **Core Type:** In-order, single-issue processor
- **Pipeline:** Commonly described as a 5-stage pipeline
- **Primary Design Goal:** A configurable, synthesizable RISC-V processor suitable for SoC integration and operating-system workloads
- **Integration Framework:** Rocket Chip Generator / Chipyard

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone | 1.72 DMIPS/MHz | Rocket core, 64-bit RISC-V, TSMC 40GPLUS comparison reported in the official lowRISC Rocket README | Found |
| CoreMark | Not verified | No normalized CoreMark/MHz result verified from the official sources checked | Not verified |
| Embench | Not verified | No Rocket-specific published result verified from the official sources checked | Not verified |
| Fmax | Above 1 GHz | Reported TSMC 40GPLUS implementation; exact maximum frequency not specified | Partial information only |

**Important:** The Dhrystone and frequency figures above come from the official Rocket README maintained by lowRISC. The reported frequency is stated as greater than 1 GHz, not as an exact Fmax measurement. Do not record it as a precise maximum-frequency result.

## 3. Published Implementation Comparison

The official Rocket README compares a 64-bit Rocket core with an ARM Cortex-A5 built using the same TSMC process.

| Parameter | ARM Cortex-A5 | Rocket Core |
|---|---:|---:|
| Register width | 32 bits | 64 bits |
| Reported frequency | >1 GHz | >1 GHz |
| Dhrystone performance | 1.57 DMIPS/MHz | 1.72 DMIPS/MHz |
| Area excluding caches | 0.27 mm² | 0.14 mm² |
| Area with 16 KB caches | 0.53 mm² | 0.39 mm² |
| Area efficiency | 2.96 DMIPS/MHz/mm² | 4.41 DMIPS/MHz/mm² |
| Dynamic power | <0.08 mW/MHz | 0.034 mW/MHz |

These are published implementation-comparison figures, not results from a new benchmark run in this project.

## 4. Benchmark Configuration Notes

- **Dhrystone:** 1.72 DMIPS/MHz, as reported in the official Rocket README.
- **Dhrystone compiler and flags:** Exact flags associated with this figure were not verified.
- **CoreMark configuration:** Not verified.
- **Embench configuration:** Not verified.
- **Fmax:** The official comparison reports frequency above 1 GHz for the specified implementation, but not an exact maximum frequency.
- **Technology:** TSMC 40GPLUS for the cited implementation comparison.
- **SoC integration:** Rocket is a processor core generator and normally requires Rocket Chip or Chipyard to generate a complete SoC.
- **Comparability:** Benchmark values depend on the core configuration, compiler, memory system and implementation technology.

## 5. Core Features Relevant to Benchmarking

- Single-issue, in-order instruction execution.
- Configurable RISC-V ISA extensions.
- Branch prediction.
- Instruction and data caches.
- Memory management unit and virtual memory support.
- Optional floating-point unit.
- Configurable cache and TLB parameters.
- Integration with Rocket Chip and Chipyard.
- Supports generation of synthesizable RTL for implementation and evaluation.

## 6. Findings

- The official lowRISC Rocket README publishes a Dhrystone score of 1.72 DMIPS/MHz.
- The same source reports a frequency above 1 GHz for a specified TSMC 40GPLUS implementation.
- The source also provides area, area-efficiency and dynamic-power comparisons with an ARM Cortex-A5.
- CoreMark and Embench results have not been verified from the official sources checked.
- The frequency figure is not an exact Fmax value and should not be compared directly with exact FPGA timing results.
- Rocket is an in-order processor, unlike out-of-order cores such as SonicBOOM.
- A fair benchmark comparison requires documenting the core configuration, compiler settings, memory system and implementation platform.

## 7. Official References

1. **Official Rocket Chip repository:**  
   https://github.com/chipsalliance/rocket-chip

2. **Official Rocket Core documentation:**  
   https://github.com/ucb-bar/chipyard/blob/main/docs/Generators/Rocket.rst

3. **Official Rocket Chip documentation:**  
   https://github.com/ucb-bar/chipyard/blob/main/docs/Generators/Rocket-Chip.rst

4. **Rocket Core README with Dhrystone and implementation comparison:**  
   https://github.com/lowRISC/rocket/blob/master/README.md

5. **Official BOOM documentation describing Rocket within Rocket Chip:**  
   https://github.com/riscv-boom/riscv-boom/blob/master/docs/sections/intro-overview/rocket-chip.rst

## 8. Research Notes

- **Analysis type:** Published benchmark and implementation-data analysis.
- **Source policy:** Official project repositories and documentation only.
- **Date accessed:** 22 October 2026.
- **Limitations:** "Not verified" means a result was not confirmed in the official sources checked; it does not prove that no result exists.
