Wang Yinfeng  
===============
Phone: 	**1865-1692-775**  
Email: **wang.batman@gmail.com**  
Objective: **E-Car Firmware Developer**  

_____________________________

##Self- appraisal
An accomplished software engineer specializing in embedded software/hardware design and develop with extensive experience; Technical background includes industry embedded system, telecommunication, and data communication; Good English communication skills and global teamwork experience; Willing to innovate, to accept challenge, and to learn new knowledge. 

___________________________

##Working Experience
- 2012.2  -   Now   [2 years 11 months] IBM CSTL System Networking/GTS SDN 
- 2009.2  -  2012.2  [3 years] Nanjing ZTE corporation
- 2008.6  -  2009.2  [8 month] Guangzhou Southern Power Group Technology Development Corporation.

______________________________

##Education
 - 2006.9 - 2008.6 Huazhong University of Science and Technology, Department of Telecommunications  
 Master of Telecommunications and Information System
 - 2002.9 - 2006.6 Huazhong University of Science and Technology, Department of Telecommunications  
 Bachelor of Telecommunications Engineering

______________________________ 

##Professional skills
- 6 years experiences in embedded system software and hardware development and testing; 
- Proficient at C programming language; and familiar with Shell and Python scripts;
- Good skills about developing on Linux platform, and using tools such as gcc, gdb, gprof, DUMA etc;
- Rich experience about ARM/MCU based border design, include schematic design, PCB layout, board bring up, bootloader and OS(uCOS/Linux) porting, device driver, Linux kernel tailoring;
- Good theoretical knowledge and implement experience of telecommunication systems, especially for SS7 protocol, Sigtran protocol suite, etc; 
- Good theoretical knowledge and implement experience about data communication, familiar with TCP/IP, routing protocols(OSPF/BGP);

_______________________________

##Working experience
####2014.2  -  now  IBM GTS CDL
Department: SDN-VE  
Position: Staff Software Engineer  
Projects:   

- Routing appliance for DOVE and OpenStack  
 - Project introduction  
IBM Dove(Distributed Overlay Virtual Ethernet) is an architecture that allows a network engineer to abstract the physical network infrastructure from hypervisor hosts and make network changes in software. Routing appliance is a plugin for IBM DOVE(Distributed Overlay Virtual Ethernet) product, it’s used to advertise routing info to internet, to provide interconnections between VMs(virtual machine) and external physical network.  
 - My works and achivement  
I was responsible for merging routing protocols (OSPF/BGP) to DOVE, which provides the ability to import and distribute the routing tables, and provides tunnel function for these protocols;  
And developed the REST APIs for the routing appliance, provide northbound interface to the SDN controller (IBM Pinnacle/OpenStack).


####2012.2  -  2014.2 IBM CSTL
Department: System Networking  
Position: Staff Software Engineer  
Projects:  

- Embedded switch Compass stacking
 - Project introduction  
Stacking is a method of connect two or more physical switch chips to build a larger system that behaves as a single logical entity, to provide high port density, centralized management, redundancy, modularity and flexible, distributed approach for data center network solution.  
 - My works and achivement  
I was responsible for porting stacking function to the new hardware platform, based on the MPC8536, BCM56840 and Linux platform, developed low level device drivers for new transceiver(via I2C), optimized port bit mapping, reduced CPU load by separating transceiver management to new thread, and fixed massive bugs about LACP/STP.  
- TOR switch Gryphon stacking  
 - Project introduction  
Gryphon is IBM's second generation all 10G standalone TOR (Top of Rack) switch.  
 - My works and achivement  
I was responsible for doing modification about the BCM SDK to adapting new hardware platform(from BCM56840 to BCM56846).   
And developed new approach to speed up image file transfer, by using the benefit of the Boardcom HiGig technology to transfer file by ATP(Acknowledge Transfer Protocol) instead of socket, image file dispatch time was reduced by 90%.  
And fixed massive bugs related with HW-specified, thread deadlock, CPU spike, CLI, SNMP etc.  
- Heterogeneous switch StockCar  
 - Project introduction   
StockCar is IBM's next generation stacking platform, which is similar to the Cisco's FabricPath solution used in it's UCS product. It provides a simple and flexible way to manage network inside data center, centralizes the management panel with the aggregation TOR switch to control massive access Embedded switch, provides virtualization function based on current hardware.  
 - My works and achivement  
I was the technical leader of China stacking project team, focused on communicate with global team, assisted project manager to do development progress trace and bug fix schedule.  
Was mainly responsible for the FoD(Feature on Demand) feature development, which provide the solution to support dynamic port resource requirement according to the software license installed.  
Was mainly responsible for the image binding development. Heterogeneous hardware platform required different image files for different switches. I worked with global team to bind multiple types of images into single one and decompose the specified image for specified switch member.  
And was mainly responsible for the hitless image upgrade feature development, co-work with global team members to achieve upgrade software without traffic loss.  
And delivered quick response to customer issues, worked with global team to provide solution to hot-site issues. And provide technology training to sales.  


####2009.2  -  2012.2     Nanjing ZTE Co., Ltd.
Department: Cloud computing and IT Research Institute  
Position: Embedded Software Engineer  
Projects:  

- SIU-V3 SMS signaling platform  
 - Project introduction   
SIU(Signaling Interface Unit) is a SMS(Short Message Service) signaling platform, based on ZTE's MSG9000 hardware and VxWorks OS.  
 - My works and achivement  
I was mainly responsible for GSM SMS signaling developing, involving MAP/TCAP/SCCP signaling protocols. Developed the signaling trace module to trace signaling message flow bi-directional, provided method to do signaling analysis without extra signaling equipment.  
Developed signaling gateway which provide signaling transfer between GSM and CDMA protocols.  
And on-site support work, customer issues fix.  
- SSIU SMS signaling platform  
 - Project introduction  
SSIU(Server Signaling Interface Unit) is a new low-cost signaling platform, which is based on x86 blade server and Linux OS.  
 - My works and achivement  
I was mainly responsible for the signaling protocols porting (from SIU-V3 platform to SSIU platform). Involving Sigtran related protocols, including the SCTP (RFC2960), M3UA (RFC3332/RFC4666) protocol.  
Worked on performance improvement, user interface design and optimize.  
Developed signaling emulation based on PC to provide function and performance test without extra expensive hardware emulation.  
And overseas technical support. July 2010 to December 2010, assignment overseas (France) supporting work, responsible for signaling IOT testing, network testing and other support work.  
- SIU-V4 SMS signaling platform  
 - Project introduction  
SIU-V4 is based on ZTE's next generation USAP1000 hardware and Linux OS.  
 - My works and achivement  
I was mainly responsible for the signaling protocol porting (from SIU-V3 platform to SIU-V4 platform), involving MAP/TCAP/SCCP signaling protocol.  
And on-site support work.  

####2008.7  -  2009.2 Guangzhou Southern Power Group Technology Development Co., Ltd  
Department: FTU Products Research Institute  
Position: Embedded Software Engineer  
Projects:  

- FTU embedded controller  
 - Project introduction  
FTU (Feeder Automation terminal) is used for the grid status detection, provides monitoring for power line operating parameters (short circuit protection, overcurrent protection), etc. The FTU embedded controller is a general control platform, provide various interface such as AD/DA, GPIO, IrDA, RS232, RS485, I2C, SPI, Ethernet, video etc.  
 - My works and achivement  
I was responsible for development and testing the core control device. Designed the controller board based on ARM(S3C2440) and Linux platform, main work include schematic design, PCB layout, board bring up, bootloader (U-Boot) porting, Linux (2.4.18/2.6.14) tailoring and device driver(AD/DA, relay, I2C, SPI) developing.  
And responsible for the EMC/ESD testing for the embedded controller, passed the verification from China electric power research institute after version 4.  

####2007.2  -  2008.6 Guangzhou Southern Power Group Technology Development Co., Ltd  
Department: FTU Products Research Institute  
Position: Embedded Software Engineer(Intern)  
Projects:  

- Industry Embedded Ethernet switch  
 - Project introduction  
The Ethernet switch is used in FTU production, is designed for industry requires high availability, be able to work under harsh duty locations.  
 - My works and achivement  
I was responsible for developing a 24 ports Ethernet switch based on ARM(S3C2410) and Boardcom BCM5324 chip. Main work include schematic design, PCB layout and bootloader (U-Boot) porting, Linux OS(2.4.18/2.6.14) tailoring.   
And assist to do EMC/ESD test.  

____________________________________

##Rewards Events
- First prize of the 7th National undergraduate Electronic Design Contest 2007
- Patent: A method to enhance the reliability of industrial wireless sensor networks 2008
- Patent: A message processing method and device 2011

________________________________________

##Language skill
English: Fluent
