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

> Initially, various files in different folders come under *openlane* has been observed as shown below
> > ![image](https://github.com/user-attachments/assets/a3307be2-3606-4ca7-9b2c-84f19dd15ce8)

> Later
>   1. To open OPENLANE, docker command can be used which responds with bash-4.2


>   2. Enter into interactive mode of operation a command **<./flow.tcl -interactive>**


>   3. Further, the required version of openlane to be defined which is openlane 0.9 using command **<package require openlane 0.9>**


>   4. Select the design using command **<prep -design picorv32a>**, design folder.


>   5. Then all LEF files will be merged.

> ![image](https://github.com/user-attachments/assets/f9425128-9657-4d5a-9f78-24d1d84f154b)


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

**DAY2: Floorplan and Placement:**
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
**DAY 3: Cloning:** It is a process in layout with which a custom layout instance can be included in the existing layout with standard cells. 

> An inverter from the link https://github.com/nickson-jose/vsdstdcelldesign.git using git clone command clones it with picorv32A design. It creates vsdstdcelldesign folder in openlane directory with all the related lib files
>
> ![image](https://github.com/user-attachments/assets/21f4d886-c8db-49ca-907a-af8593c2a69a)
>
> Copying sky130A.tech technology library into vsdstdcelldesign folder
>
> ![image](https://github.com/user-attachments/assets/cb5379ca-b5f9-4ccd-9971-dbbe9b9075d1)
>
> ![image](https://github.com/user-attachments/assets/1cb1c0eb-d77a-4151-803f-cd0682127478)
> 
> Sky130A.tech file can be observed vsdstdcelldesign folder
>
> Using the magic tools, the layout of the custom inverter from vsdstdcelldesign folder can be opened as follows:
>
> ![image](https://github.com/user-attachments/assets/31396c97-2a62-43b9-b0a2-b2108c6b5d6a)
>
> Inverter's spice file can be opened to edit using vim command
>
> ![image](https://github.com/user-attachments/assets/b2431d83-0b6e-4066-a474-b0189ee64d24)
>
> Spice file opened is given below:
>
> ![image](https://github.com/user-attachments/assets/0c728565-5281-40af-b36a-4579fe32633c)
> 
> In the above file, many changes have been done and observed the error to be addressed
>
> Simulation of the custom inverter is done using ngspice tool
>
> ![image](https://github.com/user-attachments/assets/9ac2211e-d29e-4ef2-857a-eace52a61da3)
>
> From the simulation results, rise time, fall time and propagation delay is calculated
>
> ![image](https://github.com/user-attachments/assets/aee550d1-f224-4d8c-bf83-ee14215ad311)
> 
> Rise time is from 20% to 80% of the peak voltage of logic '0' to '1' of the output transition. It is observed that it's value is 2.206 - 2.163 = 0.043 ns
>
> Simularly, for fall time, it is from 80% to 20% of the peak voltage of logic '1' to '0' of the output transition. It is observed that it's value is 4.0689 - 4.0407 = 0.028 ns
> 
>![image](https://github.com/user-attachments/assets/7c800c8a-5852-4fde-86a9-10d0749fb166)
> 
> Always rise ime is larger than fall time
>
> Propagation Delay of the inverter can be obtained by findinf the values of Tplh and Tphl. Tplh is the component which defines the delay between output transition from '0' to '1' and input transition while it is vice versa for Tphl. In both the cases, 50% of the transistion is to be taken
>
> ![image](https://github.com/user-attachments/assets/77e6ba92-23ba-4525-829d-7ecb9275a13a)
>
> From the above values, Tplh is 0.03 ns and Tphl is 0.004 ns. If the difference between both of the components is small then its average is the propagation delay else, it is the maximum value. In our case it is 0.03 ns
>
> 
**DAY 4: Pre-Layout Timing Analysis after Cloning:**

>    In this lab, design flow from synthesis to pre-layout processes are done step by step which include floorplan, placement with STA analysis

> Initially, LEF file of custon std. cell is copied into picorv32a design using the <cp> command
>**LEF** file is also called **Library Exchange Format** file, has basically two parts **technology lef** and **cell lef file**.
> **Technology lef** contains information about the metal layers and vias and design rules whereas **cell lef file** contains an abstract view of the layout of standard cells.
>
> ![image](https://github.com/user-attachments/assets/9e133cf5-b366-4c26-bf1c-48d3ef74e28e)
>
> After that command, LEF file can be observed in the src folder of picorv32a as shown below
>
> ![image](https://github.com/user-attachments/assets/d7f4fdff-8df3-4a1d-8fcb-d23442015f58)
>
> Later, all the library files are copied from vsdstdcelldesign folder into picorv32a
>
> ![image](https://github.com/user-attachments/assets/d0ed5bf3-c2f7-4fb9-9165-c89aaebb25ca)
>
> ![image](https://github.com/user-attachments/assets/4972a484-2265-4797-9497-df0d93c906de)
>
> Synthesis is done by using <run_synthesis> command
>
> ![image](https://github.com/user-attachments/assets/3c437e4a-b9bb-44c5-9235-028c34cb2f35)
>
> After the synthesis, custom std. cell vsd inverter is observed in the cell description
> ![image](https://github.com/user-attachments/assets/7d51bdcf-9715-4277-a507-66dd275974de)
> 
> Then floorplan has been done using the following commands <init_floorplan> 
>                                                           <place_io>
>                                                           <tap_decap_or>
>  To do placement, <run_placement> is used which provides result as below:
> ![image](https://github.com/user-attachments/assets/739524e4-01c1-4063-a087-f18689fcf07c)
> ![image](https://github.com/user-attachments/assets/dcbd64fc-0501-40c9-a06c-c7ab3ad4ec0f)

> To check whether the custon cell i.e., vsdinv inverter is available in the layout using magic tool. The below images show the commands given, layout and clear picture of vsdinv inverter
> ![image](https://github.com/user-attachments/assets/01e1eebd-cb22-45bf-ad51-8c0d55a23939)
> ![image](https://github.com/user-attachments/assets/0e0bbdd0-0518-42f4-a5b3-dd4e00c90391)
> ![image](https://github.com/user-attachments/assets/c7c7119d-af0c-4f51-a8e4-c9fe24c64404)

> Once, the cell is selected, it can be observed that the vsdinv inverter cell is connected with power rails of adjacent std. cells
> ![image](https://github.com/user-attachments/assets/cef4d39b-c250-4f48-9bce-f1ed9cc14c64)
>
> For the Static Timing Analysis (STA), Pre-STA configuration file is to be created using <vim> command which is shown below. pre-sta.config file consists of information about the parameters to be observes like time, capacitance, resistance, also reading out the lib files
> ![image](https://github.com/user-attachments/assets/4d0777df-611b-4433-8c04-9f123f03fb84)
>
> The parameters that are not covered by .config file is mentioned in another file my_base.sdc. Latter, the base.sdc file in pre-sta.config is replaced with my_base.sdc.
> ![image](https://github.com/user-attachments/assets/b8f6c583-fc32-4a75-9a00-4ecd59149ef8)
>
> For STA analysis, need to check any negative slack is available. If it is there, thenby adjustinf the loads of the cells in the pre-sta.config file slack is to be reduced. To do this <sta pre-sta.config> command is used. The below figures show the initail slack and the optimized slack. To optimize the slack the following command need to be used
>        <replace_cell_cell-no_ _cell-name_>
         < report_checks -fields {net cap slew input_pins} -digits 4>
> ![image](https://github.com/user-attachments/assets/0466e708-f624-4592-8246-18c1cb4272be)
> ![image](https://github.com/user-attachments/assets/55f2f44c-4d14-4553-bc87-d59b3136b48c)
>
> Later, these are to be updated in the picorv32a.synthesis.v file
> ![image](https://github.com/user-attachments/assets/2791558c-c62e-448a-aeae-212533db3bf6)
>
> Later, complete floorplan and placement as shown below
>![image](https://github.com/user-attachments/assets/a0a3edfc-cc06-47bc-b3bc-b663da2cf02a)
> ![image](https://github.com/user-attachments/assets/1ec60d6e-667e-403a-920f-424924882f83)
> ![image](https://github.com/user-attachments/assets/d29858cb-e089-425c-9f07-c8501be06392)
> 


 






>
>  


 

































