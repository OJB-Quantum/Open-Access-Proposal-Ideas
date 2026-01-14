Table I  
A Compact View of the Two-SRAM-Macro pattern in Cryogenic Readout Controller ICs 

| Macro | Primary Data | Nearest Blocks | Placement Rationale  |
| :---- | :---- | :---- | :---- |
| Capture SRAM | Raw ADC samples (I/Q words, high-rate bursts) | ADC core, decimator, clocking | Minimizes interconnect length and skew from ADC to memory, reduces dynamic power, and simplifies timing closure in a high-throughput domain \[5\], \[25\]. |
| Decision SRAM | State decisions ( $1-3$ bits), confidence, time-tags, syndrome metadata | DSP chain, matched filter, classifier, finitestate machine | Keeps the discrimination pipeline one clock deep while isolating narrow-bus traffic from wide ADC buses, and supports deterministic feedforward/feedback scheduling \[5\], \[6\]. |

Table II   
Real Quantum Gate Control Pulse Characteristics and Memory Usage Per Control Pulse

| Vendor | Sampling Rate( $f\_s$ ) | Sample Size $\\left(N\_S\\right)$ | Gate Set | Gate Latencies $(\\tau)$ | Connectivity | Memory  (per qubit) |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| IBM | 4.54 GS/s | 32-bits | X, SX, CX | 1Q:30 ns;  2Q:300 ns;  Readout:300 ns | Heavy hexagonal | 18 KB |
| Google | 1 GS/s | 28-bits | fsim, iSWAP, phased XZ | 1Q:25 ns;  2Q:30 ns;  Readout:500 ns | Grid | 3 KB |

Table III  
Experimental Temperature Comparisons of SRAM-based In-memory Computing

| Operation | Stored Bits | Latency (ps) |  |  |
| :---- | :---- | :---- | :---- | :---- |
|  |  | $\\mathrm{T}=300 \\mathrm{\~K}$ | $\\mathrm{T}=10 \\mathrm{\~K}$ | $\\mathrm{T}=300 \\mathrm{\~K}\[16\]$ |
| IMC-based OR | 00 | 39.75 | 26.75 | 1000.0 |
|  | 01 | 24.05 | 30.15 | 1000.0 |
|  | 10 | 24.05 | 30.15 | 1000.0 |
|  | 11 | 22.14 | 24.43 | 1000.0 |
| IMC-based NOR | 00 | 42.66 | 28.53 | 1000.0 |
|  | 01 | 23.67 | 29.29 | 1000.0 |
|  | 10 | 23.67 | 29.29 | 1000.0 |
|  | 11 | 21.93 | 23.03 | 1000.0 |
| IMC-based AND | 00 | 21.89 | 20.30 | 1000.0 |
|  | 01 | 27.28 | 35.69 | 1000.0 |
|  | 10 | 27.28 | 35.69 | 1000.0 |
|  | 11 | 27.10 | 29.12 | 1000.0 |
| IMC-based NAND | 00 | 20.55 | 24.44 | 1000.0 |
|  | 01 | 27.40 | 36.39 | 1000.0 |
|  | 10 | 27.40 | 36.39 | 1000.0 |
|  | 11 | 26.45 | 27.96 | 1000.0 |

Table IV   
Cryogenic CMOS State-of-Art Random-Access Memory 

| Metric | Ref  \[Joshi et al.\] | Ref  \[Joshi et al.\] | Ref  \[Saligram et al.\] | Ref  \[Kulkarni et al.\] |
| :---- | :---- | :---- | :---- | :---- |
| Topology | SRAM | SRAM | e-DRAM | SRAM |
| Technology | 14 nm FinFET Bulk | 14 nm FinFET SOI  (high performance) | 28 nm bulk | 22 nm Trigate |
| Vmin (V) | 0.23 (VCS), 0.31 (VDD) (300 K) | 0.3 | 0.75 | N/A |
| Type | 6 T | 8 T | 2 T | 8 T |
| Compileable | Yes | No | No | No |
| Speed (GHz) | 0.5 @ 0.45 V | N/A | N/A | 1.6 |
| Minimum power (mW) | 0.022 @ 1.5 MHz | 0.03 | 0.56 | N/A |
| Size | 11 Kb | 36 Kb | 12 Kb | 12 KB |
| Cryo demonstration | Yes, 6 K | No | Yes, 4 K | No |
| Implementation | Configurable two separate voltage-plane boosting (with and w/o) \- VCS and VDD | Only VDD-plane boosting \- capacitive and inductive coupling (full macro) | Single supply | Capacitive coupling word-line boosting only |

Table V  
Representative Read/ Write Access Times for Cryogenic Memory Candidates

| Technology | Read Access | Write Access | Note |
| :---- | :---- | :---- | :---- |
| 6T cryo-SRAM (survey baseline) | sub-ns class | sub-ns class | Baseline values synthesized in an embeddedmemories survey for cryogenic operation; SRAM remains the latency reference \[35\]. |
| Gain-cell eDRAM macro (CryoMem) | $\\sim 0.77 \\mathrm{\~ns}$ | $\\sim 0.77 \\mathrm{\~ns}$ | Macro cycle time inferred from 1.3 GHz maximum frequency, measured down to 4 K \[36\]. |
| Cryogenic quasi-static eDRAM | ns-class | ns-class | Quasi-static embedded DRAM concepts targeting energy-efficient near-memory compute at cryogenic temperature \[10\]. |
| FBRAM (1T SiGe floatingbody) | few-ns class | $\<5 \\mathrm{\~ns}$ | Cache-motivated 1T floating-body memory with multi-bit per cell behavior in cryogenic FDSOI \[38\]. |
| Capacitorless 1T DRAM (pseudo-static) | $\\sim 0.8 \\mathrm{\~ns}$ to 0.9 ns | $\\sim 0.8 \\mathrm{\~ns}$ to 0.9 ns | Pseudo-static 1T cell in 22 nm FDSOI, demonstrated down to cryogenic temperature \[39\]. |
| MRAM-class MTJ switching (SOT/VCMA) | ns-class readout (MTJ) | sub-ns-ns switching | Sub-nanosecond switching demonstrations and field-free write schemes (note: switching time is not identical to array write latency) \[42\]-\[44\]. |

Table VI   
Suitable Temperature Stages for Selected Technologies in a Dilution Refrigerator

| Technology | Room temperature  (300 K) | 4 K plate | Millikelvin stage (20 mK class) |
| :---- | :---- | :---- | :---- |
| SOT/VCMA MRAM | Yes (development and characterization) | Yes; recommended for nonvolatile caches and calibration memories when writes can be scheduled and shielded \[7\], \[44\], \[49\] | Conditional; feasible only with aggressive stray-field management and write-duty-cycle control, likely limited to niche functions |
| CMOS SRAM | Yes (conventional electronics) | Yes, with cryo-qualified design and verified models \[14\], \[15\], \[24\] | Rare for sizeable arrays, given the few- $\\mu \\mathrm{W}$ base-stage power budget and the difficulty of thermalizing dynamic switching |
| Qubit chip and resonators | No (coherence requires cryogenic operation) | Possibly for select intermediate resonators or couplers (modality dependent) | Yes; required for high-coherence operation in superconducting platforms \[37\] |

Table VII   
Mapping Memories and Logic to Representative Quantum-Control Tasks

| Control task | Best-fit technology | Rationale |
| :---- | :---- | :---- |
| Waveform buffer (AWG) | Cryo-SRAM or compressed waveform memory with SRAM front-end; MRAM as deeper dictionary | SRAM provides deterministic, sub-ns access; compression reduces stored samples; MRAM enables persistent dictionaries and calibration LUTs \[11\], \[48\], \[58\]. |
| State latch/ syndrome bit | SRAM or FPGA block RAM; possible superconducting latch long-term | Requires fast capture and deterministic timing; syndrome engines can run in FPGA fabrics or ASIC DSP blocks \[5\], \[12\], \[59\]. |
| Fast feed-forward (\<100 ns) | Local DSP \+ SRAM and/or FPGA acceleration | Latency is dominated by capture buffering, filtering, and decision logic; minimizing wire round-trip is the primary system benefit \[5\], \[6\]. |
| Long-term calibration store | MRAM (STT/SOT/VCMA) | Zero standby power and persistence across thermal cycles; updates can be scheduled between experiments \[48\], \[49\]. |
| Cryo-boot firmware/ configuration | MRAM \+ cryo-CMOS loader | Retains configuration between power cycles and reduces cold-to-warm state transfer \[14\], \[48\]. |

