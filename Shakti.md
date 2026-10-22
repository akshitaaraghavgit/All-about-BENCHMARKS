
# SHAKTI C-Class (RISECREEK) — Benchmark Analysis

## 1. Core Overview

- **Official Website:** https://shakti.org.in/
- **Official Processor Information:** https://shakti.org.in/tapeout.html
- **Developer:** Reconfigurable Intelligent Systems Engineering (RISE) group, IIT Madras
- **Core Name:** RISECREEK
- **Processor Family:** SHAKTI C-Class
- **Architecture:** RV64
- **ISA Support:** RV64IMAFD
- **Pipeline:** 5-stage, in-order
- **Cache:** 16 KB instruction cache and 16 KB data cache, 4-way set associative
- **Memory Management:** Separate instruction and data TLBs; Sv39 supervisor support
- **Branch Prediction:** Simple 2-state branch predictor
- **Floating-Point Support:** IEEE-754 compliant single- and double-precision FPUs
- **Primary Design Goal:** Controller-class processing with support for operating systems such as Linux

## 2. Published Benchmark Results

| Benchmark | Published Result | Configuration / Platform | Status |
|---|---|---|---|
| Dhrystone | 1.68 DMIPS/MHz | Official SHAKTI RISECREEK test-chip information | Found |
| CoreMark | Not verified | No published result verified from the official sources checked | Not verified |
| Embench | Not verified | No published result verified from the official sources checked | Not verified |
| Fmax | 350 MHz maximum closure frequency | RISECREEK test chip; Intel 22 nm FinFET technology | Found |

**Important:** The official website reports 1.68 DMIPS/MHz under RISECREEK performance information. The exact Dhrystone build configuration and compiler flags were not verified.

## 3. Physical Design and Frequency Details

| Parameter | Published Information |
|---|---|
| Test-chip name | RISECREEK |
| Manufacturer | Intel |
| Technology node | 22 nm FinFET |
| Die size | 4 × 4 mm |
| Core gate count | 140K |
| SoC gate count | 370K |
| Maximum closure frequency | 350 MHz |
| Physical design team | HCL Technologies |
| Core design team | IIT Madras |

The reported maximum closure frequency is a physical-design timing result for the specified test-chip implementation. It should not be assumed to represent the maximum frequency of every SHAKTI C-Class configuration.

## 4. Benchmark Configuration Notes

- **Dhrystone:** 1.68 DMIPS/MHz, as published on the official SHAKTI website.
- **Dhrystone compiler and flags:** Not verified.
- **CoreMark configuration:** Not verified.
- **Embench configuration:** Not verified.
- **Fmax technology:** Intel 22 nm FinFET.
- **Fmax result:** 350 MHz maximum closure frequency.
- **Implementation distinction:** Published silicon and physical-design results are not automatically comparable to FPGA implementation results.

## 5. Core Features Relevant to Benchmarking

- 64-bit RISC-V architecture.
- Five-stage in-order pipeline.
- Instruction and data caches.
- Branch prediction.
- Single- and double-precision floating-point support.
- Virtual memory support through Sv39.
- Linux and FreeRTOS support documented in the SHAKTI ecosystem.

## 6. Findings

- The official SHAKTI website publishes a Dhrystone performance figure of 1.68 DMIPS/MHz for RISECREEK.
- The official tapeout information reports a maximum closure frequency of 350 MHz for its Intel 22 nm test-chip implementation.
- CoreMark and Embench results have not been verified from the official sources checked.
- The reported performance figures describe a particular implementation and should not be treated as universal values for all SHAKTI cores.
- A fair comparison with other cores requires checking benchmark configuration, compiler flags, memory system, and implementation technology.

## 7. Official References

1. **SHAKTI official website:**  
   https://shakti.org.in/

2. **Official SHAKTI tapeout and test-chip information:**  
   https://shakti.org.in/tapeout.html

3. **Official SHAKTI processor families:**  
   https://shakti.org.in/processors.html

4. **Official SHAKTI publications:**  
   https://shakti.org.in/publications.html

5. **Official SHAKTI SDK:**  
   https://shakti.org.in/shaktisdk.html

