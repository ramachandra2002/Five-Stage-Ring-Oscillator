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
part1 about the circuit+reference+waveform

The ring oscillator is designed using odd number of inverters as a chain. Here we use CMOS inverter, which has complementary MOS transistors: pMOS on the top and nMOS on the bottom. The frequency of the oscillations produced depends upon the gate delay of the MOSFET, which is the finite time between the change of input and the corresponding change of
output. If we add inverters to the existing circuit, the total gate delay increases, thereby decreasing the frequency. The frequency of oscillations of N stage ring oscillator is given by,
![1_formula_Screenshot 2022-02-26 165413](https://user-images.githubusercontent.com/89923461/155841367-5aead861-b9d9-4fed-8d9f-fb1dd203d5c7.png)

where tr is rise in time and tf is fall time. 


part2 ref ckt image + about it

part3 ref ckt waveform
