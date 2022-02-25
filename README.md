# IMPLEMENTATION-OF-4-BIT-EVEN-PARITY-GENERATOR-USING-CMOS-28nm-PROCESS-TECHNOLOGY

# Introduction
IIT Hydrabad in collaboration with Synopsys India & VLSI Design Pvt. Ltd. has organized a 15-days “Cloud based Analog IC Design   Hackathon using Synopsys Custom Design Platform” from 15th February 2022 to 1st March 2022. This repository gives the summary about the circuit that has been designed for the fulfillement of the hackathon.

# Abstract
Parity generation is one of the most widely used error detection technique in the data transmission of digital system. This paper describes the even parity generator circuit with 4-bit input data, implemented using CMOS 28nm process technology on Synopsys Custom Compiler Design tool. 

# What is Parity Generator??
In digital systems, when binary data is transmitted and processed, data may be subjected to noise so that such noise can alter 0s (of data bits) to 1s and 1s to 0s. Hence, parity bit is added to the word containing data in order to make number of 1s either even or odd. Thus it is used to detect errors during the transmission of binary data .The message containing the data bits along with parity bit is transmitted from transmitter node to receiver node. At the receiving end, the number of 1s in the message is counted and if it doesn’t match with the transmitted one, then it means there is an error in the data.Parity generator is combinational circuit that accepts an n-1 bit stream data and generates the additional bit that is to be transmitted with the bit stream. This additional or extra bit is termed as a parity bit. There are two types of parity generation schemes namely even parity & odd parity generator. In even parity bit scheme, the parity bit is ‘0’ if there are even number of 1s in the data stream and the parity bit is ‘1’ if there are odd number of 1s in the data stream.The basic principle involved in the implementation of parity circuits is that sum of odd number of 1s is always 1 and sum of even number of 1s is always zero. Such error detecting and correction can be implemented by using EX-OR gates (since Ex-OR gate produce zero output when there are even number of inputs).

# Proposed Design
As mentioned above, the basic building block of any parity circuit is EX-OR gate, the first step is to design an EX-OR using CMOS logic. The design that has been implemented is shown below : 
![image](https://user-images.githubusercontent.com/100372947/155658987-dded4d75-4435-49a3-a817-6b57d3ff2b01.png)
Also, the inverted inputs that has been given to some of the gate terminal of transistors are produced with simple CMOS inverter circuit. Next step is to create 3 EX-OR gate instances as shown below to get final parity output :
![image](https://user-images.githubusercontent.com/100372947/155659553-bea91699-e652-43eb-8852-ce87ea48d517.png)
The truth table of generated parity bit is given as : 
![image](https://user-images.githubusercontent.com/100372947/155659698-f77c3f1f-cc93-4550-a54e-c16f5d3543db.png)

