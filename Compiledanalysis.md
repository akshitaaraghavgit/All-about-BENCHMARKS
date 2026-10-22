# RISC-V Core Benchmark Comparison

## Cores Included

1. PicoRV32
2. SHAKTI C-Class
3. Ibex
4. SonicBOOM
5. Rocket
6. CVA6
7. MIST-ES
8. 3-SIPP-ESR

**Note:** SERV and Vex are excluded. `Not verified` means a result was not verified in the official sources checked; it does not prove that no result exists.

---

## 1. CoreMark Comparison

CoreMark measures embedded processor performance using integer workloads. Higher CoreMark/MHz generally indicates better performance per clock, provided the benchmark configurations are comparable.

| No. | Core | CoreMark Result | Result Type / Configuration |
|---:|---|---|---|
| 1 | PicoRV32 | Not verified | No result recorded in the official source checked |
| 2 | SHAKTI C-Class | Not verified | No result recorded in the official source checked |
| 3 | Ibex | 0.904–3.13 CoreMark/MHz | Published results across micro, small, maxperf, and maxperf-pmp-bmfull configurations |
| 4 | SonicBOOM | 6.2 CoreMark/MHz | Previously identified published result; exact configuration requires rechecking |
| 5 | Rocket | Not verified | No result recorded in the official source checked |
| 6 | CVA6 | 3.0 CoreMark/MHz; optional 4.5 target | Published targets, not verified measured results |
| 7 | MIST-ES | 1.18 CoreMark/MHz | Verilator simulation; 1,000 iterations; GCC `-O2` |
| 8 | 3-SIPP-ESR | 2.92 CoreMark/MHz | Verilator simulation; 100 iterations; GCC `-O2` |

### CoreMark Analysis

- SonicBOOM has the highest numerical result currently recorded, but the exact configuration needs verification before drawing a firm comparison.
- Ibex results vary by configuration.
- MIST-ES and 3-SIPP-ESR have simulation-based results.
- CVA6 figures are targets, not confirmed measurements.
- Missing results should be verified before ranking all eight cores.

---

## 2. Dhrystone Comparison

Dhrystone evaluates general-purpose integer workloads. DMIPS/MHz is a normalized metric; higher values generally indicate better performance per clock when measurement conditions match.

| No. | Core | Dhrystone Result | Result Type / Configuration |
|---:|---|---|---|
| 1 | PicoRV32 | 0.516 DMIPS/MHz | Published result with specified multiplier, divider, and barrel-shifter options |
| 2 | SHAKTI C-Class | 1.68 DMIPS/MHz | Published on the official SHAKTI tapeout page |
| 3 | Ibex | Not verified | No result recorded in the official source checked |
| 4 | SonicBOOM | Not verified | No result recorded in the official source checked |
| 5 | Rocket | 1.72 DMIPS/MHz | Previously identified published comparison result; implementation configuration matters |
| 6 | CVA6 | Not verified | No measured result recorded here |
| 7 | MIST-ES | 0.388 DMIPS/MHz | Verilator simulation; 100,000 runs; self-check passed |
| 8 | 3-SIPP-ESR | 1.26 DMIPS/MHz | Verilator simulation; 2,000,000 runs |

