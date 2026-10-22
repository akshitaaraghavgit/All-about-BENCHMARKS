
# CVA6 — Benchmark Analysis

## 1. Core Overview

- **Official Repository:** https://github.com/openhwfoundation/cva6
- **Developer / Maintainer:** OpenHW Foundation; originally developed at ETH Zürich and the University of Bologna
- **Core Name:** CVA6 (formerly Ariane)
- **Architecture:** Configurable RV32 or RV64
- **ISA Support:** Configurable RISC-V extensions; RV64GC is supported
- **Implementation Language:** SystemVerilog
- **Core Type:** In-order, single-issue processor in the standard configuration
- **Pipeline:** 6-stage
- **Primary Design Goal:** Application-class RISC-V processing with support for operating systems such as Linux
- **Integration Framework:** CVA6 APU / Chipyard and related SoC platforms

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone | Not verified | No measured, normalized Dhrystone result verified in the official sources checked | Not verified |
| CoreMark | Target: 3.0 CoreMark/MHz | CVA6 performance target, assuming a sufficiently fast memory hierarchy | Published target, not a verified measured result |
| CoreMark | Optional target: 4.5 CoreMark/MHz | Dual-issue feature enabled; sufficiently fast memory hierarchy assumed | Published target, not a verified measured result |
| Embench | Not verified | No CVA6-specific measured result verified in the official sources checked | Not verified |
| Fmax | Target: >150 MHz | CV32A6 IMAC SV32 configuration on Kintex-7 FPGA, commercial -2 speed grade | Published target, not a verified measured result |
| Fmax | Target: >900 MHz | CV64A6 IMACFD SV39 configuration on 28FDSOI technology, worst-case frequency corner with fastest threshold voltage | Published target, not a verified measured result |

**Important:** The official CVA6 requirements specification lists the CoreMark and frequency figures above as performance targets. They must not be presented as measured benchmark results.

## 3. Published Performance Targets

| Metric | Target | Conditions |
|---|---:|---|
| CoreMark performance | 3.0 CoreMark/MHz | Sufficiently fast memory hierarchy |
| Optional CoreMark performance | 4.5 CoreMark/MHz | Dual-issue option enabled |
| CV32A6 frequency | >150 MHz | Kintex-7 FPGA, commercial -2 speed grade |
| CV64A6 frequency | >900 MHz | 28FDSOI technology; specified frequency corner |

These figures describe requirements or design targets, not necessarily achieved performance for every implementation.

## 4. Benchmark Configuration Notes

- **Dhrystone configuration:** Not verified.
- **CoreMark:** Published targets are available; corresponding measured results and compiler settings need separate verification.
- **Embench configuration:** Not verified.
- **Fmax:** Published target values are tied to specific FPGA or ASIC technology configurations.
- **Architecture:** CVA6 can be configured as a 32-bit or 64-bit processor.
- **Memory system:** Includes caches and configurable memory-management features.
- **Integration:** The repository separates the core RTL from the CVA6 APU and FPGA emulation platform.
- **Comparability:** Performance depends on configuration, compiler, memory hierarchy, implementation technology, and timing constraints.

## 5. Core Features Relevant to Benchmarking

- Six-stage pipeline.
- In-order instruction execution.
- Configurable 32-bit and 64-bit variants.
- Branch prediction using a branch target buffer and branch history table.
- Separate instruction and data TLBs.
- Hardware page-table walker.
- Optional MMU, PMP, and floating-point unit.
- Support for application-class operating systems.
- Performance model available in the official repository.
- Synthesis and FPGA implementation flows.

## 6. Findings

- The official requirements specification publishes CoreMark and frequency targets for specified configurations.
- The 3.0 and 4.5 CoreMark/MHz figures are targets, not verified measured scores.
- The frequency targets distinguish between a Kintex-7 FPGA implementation and a 28FDSOI ASIC implementation.
- Dhrystone and Embench results have not been verified in the official sources checked.
- CVA6 is more complex than small embedded cores such as SERV and Ibex, making its configuration and implementation platform particularly important.
- A fair comparison requires measured results with documented compiler settings, memory system, configuration, and target technology.

## 7. Official References

1. **Official CVA6 repository:**  
   https://github.com/openhwfoundation/cva6

2. **Official CVA6 requirements specification:**  
   https://github.com/openhwfoundation/cva6/blob/master/docs/02_cva6_requirements/cva6_requirements_specification.rst

3. **Official CVA6 documentation:**  
   https://docs.openhwgroup.org/projects/cva6-user-manual/

4. **Official synthesis and physical-design files:**  
   https://github.com/openhwfoundation/cva6/tree/master/pd

5. **Official CVA6 performance model:**  
   https://github.com/openhwfoundation/cva6/tree/master/perf-model

## 8. Research Notes

- **Analysis type:** Published specification and performance-target analysis.
- **Source policy:** Official OpenHW Foundation sources only.
- **Date accessed:** 22 October 2026.
- **Limitations:** Published targets are not equivalent to measured results. "Not verified" means a result was not confirmed in the official sources checked; it does not prove that no result exists.
