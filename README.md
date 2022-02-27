# Five Stage Ring Oscillator
This is the detailed report about the design of Five Stage Ring Oscillator using CMOS technology. This is design was created in part of Cloud based Analog IC Hackathon conducted by IIT-Hyderabad and VSD Corp.

# Contents
- [Introduction](/Five-Stage-Ring-Oscillator#introduction)
- Circuit Design
- Tools Used
- Schematics
- Waveforms

# Introduction
A Ring Oscillator is device which uses a odd number of inverters to make oscillations. This circuit has a positive feedback loop which helps to attain sustained oscillations. Here in this design we are going design a five stage ring oscillator. These ring oscillator circuits are used in Integrated Circuits which has low power applications. In this repo, we are going to design and analyse the five stage ring oscillator.

# Circuit Design
The ring oscillator is designed using odd number of inverters as a chain. Here we use CMOS inverter, which has complementary MOS transistors: pMOS on the top and nMOS on the bottom. The frequency of the oscillations produced depends upon the gate delay of the MOSFET, which is the finite time between the change of input and the corresponding change ofnoutput. If we add inverters to the existing circuit, the total gate delay increases, thereby decreasing the frequency. The frequency of oscillations of N stage ring oscillator is given by,

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

# Tools Used

- **Synopsys Custom Compiler** : A design environment which is a modern solution for full-custom analog, custom digital, and mixed-signal IC design.
- **Synopsys Primewave** : for simulating the designed circuits under different conditions and time scales.
- **Synopsys 28 nm PDK** : A process design kit which has a comprehensive collection of 28nm transistor sets and libraries.

# Schematics 
The schematics of the cmos inverter, enable circuit and the final ring oscillator circuit is designed using the *Synopsys’ PrimeSim™ HSPICE®* powered schematic editor.

## CMOS Inverter
This CMOS inverter is designed as a schematic and then implemented as a symbol for later integration into the final circuit of the ring oscillator. Creating *symbols* of separate stages of circuit helps us to debug the circuit easily by implementing it through various testbench conditions. Another advantage of creating a symbol is to have it industry ready and be as a reference for creating other circuits.

![sch_Screenshot 2022-02-26 202304](https://user-images.githubusercontent.com/89923461/155868945-a0db3a46-0a49-4a4f-aeb9-ab6077f45c6d.png)
<p align="center">Fig.3 Schematic of a CMOS Inverter </p>

![symbol_Screenshot 2022-02-26 202502](https://user-images.githubusercontent.com/89923461/155868951-fa207151-69f7-43a8-bb6f-074ef63e401d.png)
<p align="center">Fig.4 CMOS inverter as a Symbol</p>

## Enable Circuit
As we saw earlier in the circuit design, the enable circuit is basically a NAND gate which acts like switching circuit for the oscillator. In the first input of the NAND gate we give a voltage pulse (*which mimics the switch ON and OFF*) and in the other input we give the feedback loop from the final stage of the oscillator. When the first input is ON, the NAND gate acts ike a inverter which is placed as the first stage of the oscillator. 

![sch_Screenshot 2022-02-26 220758](https://user-images.githubusercontent.com/89923461/155869145-6be32408-2bb3-45ed-be28-775c0e296c0c.png)
<p align="center">Fig.5 Schematic of a Enable Circuit </p>

![symbol_Screenshot 2022-02-26 221002](https://user-images.githubusercontent.com/89923461/155869157-4bd32c8e-5931-4db6-b029-e26fa8dbf72c.png)
<p align="center">Fig.6 Enable Circuit as a Symbol</p>

## Ring Oscillator
Using the symbols created for the CMOS inverter and the enable circuit, we design a schematic for the five stage ring oscillator. The enable circuit is the first stage and the CMOS inverter is used for the rest of the four stages.

![sch_Screenshot 2022-02-26 221344](https://user-images.githubusercontent.com/89923461/155869260-476efcc8-2641-47f3-802c-454d078f2619.png)
<p align="center">Fig.7 Schematic of the five stage ring oscillator </p>

![symbol_Screenshot 2022-02-26 221456](https://user-images.githubusercontent.com/89923461/155869262-f35ced3a-e6d5-4feb-a7f3-304b7f44e5d7.png)
<p align="center">Fig.8 Five stage ring oscillator as a Symbol</p>

# Simulation and Waveforms 
The final simulations of the five stage ring oscillator circuit are obtained through PrimeWave™ Design Environment using its TestSuite and Waveform viewer.

## Testbench
The five stage ring oscillator is simulated by created a schematic using the *ring_oscillator* symbol and connecting it with the vdc and vpulse, a square wave generating voltage source.

![tb_Screenshot 2022-02-26 221713](https://user-images.githubusercontent.com/89923461/155869516-e044a2b5-364d-4a36-94f5-52203143316a.png)
<p align="center">Fig.9 Testbench for the Five stage ring oscillator</p>

## Parameters for V<sub>dc</sub>
![vdc_Picture1](https://user-images.githubusercontent.com/89923461/155869669-d4f13311-e2a9-4a29-908f-0ee201bb9741.png)
<p align="center">Fig.10 Parameters for  V<sub>dc</sub> </p>

## Parameters for V<sub>pulse</sub>
![vpulse_Picture1](https://user-images.githubusercontent.com/89923461/155869710-18d426ed-7a5d-457b-a2ce-6161d1f89b11.png)
<p align="center">Fig.10 Parameters for  V<sub>pulse</sub> </p>
















