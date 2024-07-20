  **This SoC Design Program is organised by VLSI System Design with Hands-on Practice over open-source platform OPENLANE. It has 5 days of hands-on practice from RTL to GDSII generation.**

**Openlane** is an innovative silicon implementation platform which supports open-source tools such as Yosys, OpenROAD, Magic, KLayout. OpenLane integrates and abstracts the various steps of silicon implementation, allowing users to harden their projects using simple configuration files
Currently, there are two versions of OpenLane, each tailored to its own use case.
**OpenLane 1:** Tried-and-True Open-Source Silicon Implementation Flow
**OpenLane 2:** Next-Generation Silicon Implementation Platform for Highly-Custom Chips  [Reference:https://efabless.com/openlane]

**Helpful Links:**
Check it out on GitHub! https://github.com/efabless/openlane2
Reference Manual: https://openlane2.readthedocs.io/en/latest/reference/index.html
Additional Material: https://openlane2.readthedocs.io/en/latest/additional_material.html


**Day 1: Introduction to Openlane and Synthesizing the Picorv32A**

Initially, various files in different folders come under *openlane* has been observed as shown below

![image](https://github.com/user-attachments/assets/a3307be2-3606-4ca7-9b2c-84f19dd15ce8)

Later
1. To open OPENLANE, docker command can be used which responds with bash-4.2


2. Enter into interactive mode of operation a command **<./flow.tcl -interactive>**


3. Further, the required version of openlane to be defined which is openlane 0.9 using command **<package require openlane 0.9>**


4. Select the design using command **<prep -design picorv32a>**, design folder.


5. Then all LEF files will be merged.

![image](https://github.com/user-attachments/assets/f9425128-9657-4d5a-9f78-24d1d84f154b)


> **Once the design is selected for synthesis**
> 
> **runs** folder is created in the design directory in which after the synthesis the reports, results and other design parameters will be loaded.
>
> ![image](https://github.com/user-attachments/assets/19bcccb9-b049-44bf-8730-8f3873991987)
>
> ![image](https://github.com/user-attachments/assets/7f340c06-6d20-44f7-8034-4fe55a35ad25)
>
> In bash prompt, give the command **<run_synthesis>**, then synthesis will be done on the design if errors are not observed.
>
> ![image](https://github.com/user-attachments/assets/87281901-efc6-47e7-9a3c-3908510061e2)
>
> The number of D-flip flops observed in the synthesis report is shown below which conveys that there is 10.48% of flops available in the total number of cells.
>
> ![image](https://github.com/user-attachments/assets/b2ba4ff2-333d-4fd9-84af-76b86b87d90c)
>
> Synthesis process also provides reports over timing, no. of cells etc, on among which is shown below:
>
> ![image](https://github.com/user-attachments/assets/032c8a18-4ac2-4bef-a08f-a38dedea63d6)
>
> Netlist is generated upon the command given
> ![image](https://github.com/user-attachments/assets/a9576002-e4ff-44e4-8212-7d592ae4216a)
>
> Report over the STA analysis is generated upon the respective commands:
>
>![image](https://github.com/user-attachments/assets/75b94631-74c7-432d-9469-ae0e0c21eccb)
>
> ![image](https://github.com/user-attachments/assets/6b650d74-2cf0-4b58-beb9-b7a78ab3c4cd)
> 

> **DAY2: Floorplan and Placement:**
> 
> **Chip Floorplanning** partitions the chip die between different system building blocks and place I/O pads. Dimensions of every cell, pin location and row locations are defined by **Macro Floor Planning.**
> To perform Floorplan, you need to make sure that synthesis is over. Then, by using the command <run_synthesis>, one can perform it. The floorplan process is shown below:
>
> ![VirtualBox_VSD Workshop_16_07_2024_21_43_04_Floorpaln1](https://github.com/user-attachments/assets/5a739050-1f38-4454-a07f-d019b80a5580)
>
> ![VirtualBox_VSD Workshop_16_07_2024_20_06_26_floorplan 2](https://github.com/user-attachments/assets/261f7184-6f75-4630-99d7-d385b607dada)
>
> This floorplan provides the information about the components, pins, commections and also the standard cells in the layout by opening the ioplacer.log file which is generated as a par of the floorplan process as shown below: To open it <less ioplacer.log>  command
>
> ![VirtualBox_VSD Workshop_16_07_2024_21_42_36](https://github.com/user-attachments/assets/543bd5c1-4722-4396-8a40-0538921238aa)
>
> ![VirtualBox_VSD Workshop_16_07_2024_21_43_25](https://github.com/user-attachments/assets/f8f0c449-6553-4c56-afd1-6191d767b792)
>
> To open the DEF file which gives the physical information of design in ASCII form magic tool is used:
>
> ![image](https://github.com/user-attachments/assets/71ff6026-cd83-44e5-936c-e30544e6bb72)
>
> ![image](https://github.com/user-attachments/assets/1504aa74-ec65-41c0-bb1d-359013c36d0a)
>
> **Placement:** Placement is the process of placing of all standard cells that are present in netlist by the tool into the core area. Thsi process basicaaly follows floorplan which gives information of netlist. Command <run_placement is used. This placement process gives the information on total instances, nets and all
>
> ![image](https://github.com/user-attachments/assets/17c42abe-02bd-4665-aec8-c8778eb7d258)
>
> To get the layout, magic tool is used and standard cells can be observes in the layout also. These standard cells are placed diagonally in the layout to form connectivity with power lines
>
> ![image](https://github.com/user-attachments/assets/9da783ad-251a-4336-b537-acce0b921f2e)
>
> ![image](https://github.com/user-attachments/assets/a6f7a9c2-3d6c-4ff9-b27a-e89e442a7bda)
>
> Sub-cells inside layout can be observed here with their type and so on
>
> ![image](https://github.com/user-attachments/assets/0a836514-6d80-47b5-a74a-9c57880283ba)
>
> ![image](https://github.com/user-attachments/assets/7a909afb-58d8-482c-801e-172517cf6dbe)
>
> ![image](https://github.com/user-attachments/assets/d74a6c42-fe4f-4895-bccd-10c2a2ae8b66)
>
> ![image](https://github.com/user-attachments/assets/dd1c57e9-320b-4aa8-94eb-dd0db0829b02)
> 









