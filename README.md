# IMPLEMENTATION-OF-4-BIT-EVEN-PARITY-GENERATOR-USING-CMOS-28nm-PROCESS-TECHNOLOGY

# Introduction
IIT Hydrabad in collaboration with Synopsys India & VLSI System Design Pvt. Ltd. has organized a 15-days “Cloud based Analog IC Design   Hackathon using Synopsys Custom Design Platform” from 15th February 2022 to 1st March 2022. This repository gives the summary about the circuit that has been designed for the fulfillement of the hackathon.

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

# Pre-Layout Schematics
Initially, the CMOS EX-OR gate implemeneted as basic building block :

![Screenshot (234)](https://user-images.githubusercontent.com/100372947/155662538-7542dc29-5f15-43b0-9ad7-7a3fd5090b26.png)

Final parity generator circuit : 

![Screenshot (235)](https://user-images.githubusercontent.com/100372947/155662632-2fac6938-576d-4271-9d8b-38d1ae368e9c.png)

# Design Specifications
28nm PDK PMOS Specifications : 

![image](https://user-images.githubusercontent.com/100372947/155662841-04401b24-c2bc-4e10-b30f-0fa487c75ee2.png)

28nm PDK NMOS Specifications : 

![image](https://user-images.githubusercontent.com/100372947/155662996-992d7941-e748-4d59-b94b-ec25d06c118d.png)

Input VDD Voltage : 1.8V

Input : (Shown for one, other 3 are with period 27ns, 11ns, 37ns)

![image](https://user-images.githubusercontent.com/100372947/155663194-4918d6af-84d0-486b-94e7-eaf500f5bdbc.png)

# PrimeWave Simulation
Analysis Type : Transient Analysis

![Screenshot (241)](https://user-images.githubusercontent.com/100372947/155663339-c4569a9f-170a-479a-b282-0f03e54fd5d0.png)

Output Waveforms :

![Screenshot (245)](https://user-images.githubusercontent.com/100372947/155663395-6dc7f2c0-c4ac-4268-8ee5-fd3a09ef1e57.png)

As we can see here, the generated parity bit is just EX-OR operation of all bits of 4-bit input. If we combine entire 5 bit data (4bit input + parity bit), we can infer that number of 1s in every combination is even i.e. even parity.

# Netlist

*  Generated for: PrimeSim
*  Design library name: parity_new
*  Design cell name: parity_4bit
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Fri Feb 25 05:54:41 2022

.global gnd!
********************************************************************************
* Library          : parity_new
* Cell             : exor
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt exor a b gnd_1 out vdd

xm11 net47 b vdd vdd p105 w=0.1u l=0.03u nf=1 m=1

xm10 net43 a vdd vdd p105 w=0.1u l=0.03u nf=1 m=1

xm3 out net47 net13 net13 p105 w=0.1u l=0.03u nf=1 m=1

xm2 out b net9 net9 p105 w=0.1u l=0.03u nf=1 m=1

xm1 net13 a vdd vdd p105 w=0.1u l=0.03u nf=1 m=1

xm0 net9 net43 vdd vdd p105 w=0.1u l=0.03u nf=1 m=1

xm9 net47 b gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1

xm8 net43 a gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1

xm7 net29 net47 gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1

xm6 net25 b gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1

xm5 out net43 net29 net29 n105 w=0.1u l=0.03u nf=1 m=1

xm4 out a net25 net25 n105 w=0.1u l=0.03u nf=1 m=1

.ends exor

********************************************************************************
* Library          : parity_new
* Cell             : parity_4bit
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi2 net14 net15 gnd! net28 net12 exor

xi1 net22 net20 gnd! net15 net12 exor

xi0 net26 net24 gnd! net14 net12 exor

v4 net12 gnd! dc=1.8

v8 net26 gnd! dc=0 pulse ( 0 1.8 0 0.1n 0.1n 8n 16n )

v7 net24 gnd! dc=0 pulse ( 0 1.8 0 0.1n 0.1n 13.5n 27n )

v6 net22 gnd! dc=0 pulse ( 0 1.8 0 0.1n 0.1n 5.5n 11n )

v5 net20 gnd! dc=0 pulse ( 0 1.8 0 0.1n 0.1n 18.5n 37n )

r10 net28 gnd! r=1k

.tran '1n' '100n' name=tran

.option primesim_remove_probe_prefix = 0

.probe v(*) i(*) level=1

.probe tran v(net20) v(net22) v(net24) v(net26) v(net28)


.temp 25

.option primesim_output=wdf

.option parhier = LOCAL

.end

# Author
•	Akash Ambekar

Final Year B.Tech. (Electronics Engineering) 

KIT's College of Engineering, Kolhapur, Maharashtra, India

# Acknowledgements
•	Mr.Kunal Ghosh (Co-Founder, VLSI System Design Corp. Pvt. Ltd.)

•	Mr.Chinmaya Panda (IIT Hydrabad)

•	Synopsys India

•	Cloud Based Analog IC Design Hackathon'

•	Sameer Durgoji, NIT Karnataka

# References
[1] Neil H. E. Weste, Kamran Eshraghian. ‘PRINCIPLES OF CMOS VLSI DESIGN A Systems Perspective’

[2] Rabaey Jan M, ‘Digital Integrated Circuits A Design Perspective (2nd Ed)

[3] R. JACOB BAKER, ‘CMOS Circuit Design, Layout, and Simulation’ 
