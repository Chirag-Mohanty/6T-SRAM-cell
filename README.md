# 6T-SRAM-cell
**Design and Simulation of 1k 32-bit 6T-SRAM using OpenRAM(NGspice tool)**
## Contents
- **_1. Introduction_** 
- **_2. Design of SRAM using OpenRAM_**
- **_3. Block Diagram_** 
- **_4. Blocks Description_**
  - _6T-SRAM cell_
  - _Pre-Charge circuit_
  - _Sense Amplifier_
  - _Write Driver_
- **_5. Simulation Results_**
- **_6. Upcoming Updates_**

## **1. Introduction**
Static Random-Access Memory(SRAM) uses latching circuitry (flip-flop) to store each bit. SRAM is a volatile memory i.e. data is lost when power is removed. SRAMs have become a standard component embedded in all System-on-Chip (SoC), Application Specific Integrated Circuit (ASIC) and micro processor designs.

## 2. Design of SRAM using OpenRAM
**Why OpenRAM ?**
   - Existing Process Design Kits (PDKs) frequently lack memory compilers, while expensive commercial solutions only provide memory models with immutable cells, limited configurations, and restrictive licenses.The OpenRAM project aims to provide an open-source memory compiler development framework for memories. It provides reference circuit and physical implementations in a generic 45nm technology and fabricable Scalable CMOS (SCMOS), but it has also been ported to several commercial technology nodes using a simple technology file. OpenRAM also includes a characterization methodology so that it can generate the timing and power characterization results in addition to circuits and layout while remaining independent of specific commercial tools. Most importantly, OpenRAM is completely user-modifiable since all source code is open source at:
                                                    (https://openram.soe.ucsc.edu/)

**SRAM Design**
- This project is mainly targeted for the following specifications:-
  - Memory Size = 1k 32-bit 
  - Voltage Supply = 5V
  - Technology = 0.5um SCMOS Technology

## 3. Block Diagram

![](https://user-images.githubusercontent.com/72131007/94683992-04051200-0345-11eb-988e-a979c6c6df52.PNG)
- The SRAM block consists of 8 major blocks:
  - The bit-cell array
  - Address Decoder
  - Sense Amplifier
  - Word-line driver
  - Precharge circuit
  - Write Driver
  - Control logic
  - Column MUX

## 4. Block Description
- **6T-SRAM cell**
  - ![6t_fin](https://user-images.githubusercontent.com/72131007/94717862-82c27500-036e-11eb-9d23-8239a5c9868f.PNG)
  - The netlist is in the repository named as **'sram_cell.sp'**




- **Transient Analysis of SRAM including all the parasitics**
  - ![1st_tran](https://user-images.githubusercontent.com/72131007/94721564-b227b080-0373-11eb-80a6-0b17c8c52e91.PNG)
  - The netlist for SRAM with all the parasitics in **'sram_parasitic.sp'**
  - The testbench for the above can be found in **'testbench.sp**
























