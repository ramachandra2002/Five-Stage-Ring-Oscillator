# Five Stage Ring Oscillator
This is the detailed report about the design of Five Stage Ring Oscillator using CMOS technology. This is design was created in part of Cloud based Analog IC Hackathon conducted by IIT-Hyderabad and VSD Corp.

# Contents
- [Introduction](https://github.com/ramachandra2002/Five-Stage-Ring-Oscillator#introduction)
- Circuit Design
- Tools Used
- Schematics
- Waveforms

# Introduction
A Ring Oscillator is device which uses a odd number of inverters to make oscillations. This circuit has a positive feedback loop which helps to attain sustained oscillations. Here in this design we are going design a five stage ring oscillator. These ring oscillator circuits are used in Integrated Circuits which has low power applications. In this repo, we are going to design and analyse the five stage ring oscillator.

# Circuit Design
The ring oscillator is designed using odd number of inverters as a chain. Here we use CMOS inverter, which has complementary MOS transistors: pMOS on the top and nMOS on the bottom. The frequency of the oscillations produced depends upon the gate delay of the MOSFET, which is the finite time between the change of input and the corresponding change of
output. If we add inverters to the existing circuit, the total gate delay increases, thereby decreasing the frequency. The frequency of oscillations of N stage ring oscillator is given by,

![Screenshot 2022-02-26 1710251](https://user-images.githubusercontent.com/89923461/155841843-bd6016e2-d39e-48f5-8735-7e6448c12a58.png)

where t<sub>r</sub> is rise in time and t<sub>f</sub> is fall time. In this design, we include a enable circuit to control the ring oscillator. When the enable circuit is turned OFF, no oscillations are produced. There will be oscillations if you turn the enable circuit to be ON. For the enable circuit, we have to use a NAND gate asthe first stage of the ring oscillator. If one input is always high, then the NAND gate acts as the inverter of the second input.

## Reference Circuit Diagram

![circuit diagram](https://user-images.githubusercontent.com/89923461/155842061-6d56608b-3953-4db8-acda-2fbb5934dcca.jpg)
<p align="center"> Fig.1 Reference circuit diagram of a Five Stage Ring Oscillator </p>

## Reference Waveform
![waveform](https://user-images.githubusercontent.com/89923461/155842125-823f3f82-98f0-460b-96e5-9cc5524bf219.jpg)
<p align="center"> Fig.2 Reference Waveform </p>

From Fig.1, reference circuit design, we can see the enable circuit which comprises of the pMOS M1, M2 and nMOS M3, M4. The inverter in each stage consists of a pMOS and nMOS. Power supply for the circuit is given through VDD and VA acts as the enable pin. The output waveform is obtained through VOUT when VDD = 5V and VA=5V, which represented through Fig.2, Reference Output Waveform.

## Transistor Sizing
Because the standby power in a CMOS inverter is relatively low, size may be dependent on switching speed. The switching time in the pull-up mode must be the same as the switching time in the pull-down mode. The switching time is thus a function of the nMOS and pMOS transistor's current capacity. Assuming that V<sub>TN</sub> = |V<sub>TP</sub>|, equal switching times then implies that the conduction parameters of the nMOS and pMOS devices be equal and assuming that µ<sub>n</sub> ≈ 2µ<sub>p</sub> , we have (W/L)p = 2(W/L)n.

| MOS | Width | Length |
|---|---|---|
| pMOS | 0.2 µm | 0.03 µm |
| nMOS | 0.1 µm | 0.03 µm |
