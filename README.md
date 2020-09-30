# 6T-SRAM-cell
Design and Simulation of 1k 32-bit 6T-SRAM using OpenRAM(NGspice tool)
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
An SRAM cell has three different operating states: standby (the circuit is idle), reading (the data has been requested) or writing (updating the contents). The three different states work as follows:

1.**Standby**
  - If the word line is not asserted, the access transistors M5 and M6 disconnect the cell from the bit lines. The two cross-coupled inverters formed by M1 – M4 will continue to     reinforce each other as long as they are connected to the supply.

2.**Reading**
In theory, reading only requires asserting the word line WL and reading the SRAM cell state by a single access transistor and bit line, e.g. M6, BL. However, bit lines are relatively long and have large parasitic capacitance. To speed up reading, a more complex process is used in practice: The read cycle is started by precharging both bit lines BL and BL, to high (logic 1) voltage. Then asserting the word line WL enables both the access transistors M5 and M6, which causes one bit line BL voltage to slightly drop. Then the BL and BL lines will have a small voltage difference between them. A sense amplifier will sense which line has the higher voltage and thus determine whether there was 1 or 0 stored. The higher the sensitivity of the sense amplifier, the faster the read operation. As the NMOS is more powerful, the pull-down is easier. Therefore, bit lines are traditionally precharged to high voltage. Many researchers are also trying to precharge at a slightly low voltage to reduce the power consumption.

3.**Writing**
The write cycle begins by applying the value to be written to the bit lines. If we wish to write a 0, we would apply a 0 to the bit lines, i.e. setting BL to 1 and BL to 0. This is similar to applying a reset pulse to an SR-latch, which causes the flip flop to change state. A 1 is written by inverting the values of the bit lines. WL is then asserted and the value that is to be stored is latched in. This works because the bit line input-drivers are designed to be much stronger than the relatively weak transistors in the cell itself so they can easily override the previous state of the cross-coupled inverters. In practice, access NMOS transistors M5 and M6 have to be stronger than either bottom NMOS (M1, M3) or top PMOS (M2, M4) transistors. This is easily obtained as PMOS transistors are much weaker than NMOS when same sized. Consequently, when one transistor pair (e.g. M3 and M4) is only slightly overridden by the write process, the opposite transistors pair (M1 and M2) gate voltage is also changed. This means that the M1 and M2 transistors can be easier overridden, and so on. Thus, cross-coupled inverters magnify the writing process.
## 2.Design of SRAM using OpenRAM
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
  - Column MUX.

## 4. Block Description
- **6T-SRAM cell**
  

























