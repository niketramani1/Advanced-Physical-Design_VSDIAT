# Advanced-Physical-Design_VSDIAT

## **Day 1**: Inception of Open source EDA, Openlane and SKY 130 PDKs

**Day1_SK1: How to talk to computers**

Basics of package, chip, pad, core, die, IPs:

![image](https://user-images.githubusercontent.com/86380243/123850511-1cac5380-d8e8-11eb-9086-5baf7b2c8bbc.png)

![image](https://user-images.githubusercontent.com/86380243/123852034-dbb53e80-d8e9-11eb-9050-e940c4b69676.png)

![image](https://user-images.githubusercontent.com/86380243/123851516-444feb80-d8e9-11eb-89b1-b6fcc36cfb5c.png)

Basics of RISCV

![image](https://user-images.githubusercontent.com/86380243/123853254-3e5b0a00-d8eb-11eb-8af2-1a8e96597f2c.png)

Flow from sowtware applications to hardware

![image](https://user-images.githubusercontent.com/86380243/123854332-947c7d00-d8ec-11eb-85f2-8b3aa39e1a36.png)
                                                                                            Ref: www.vsdiat.com
                                                                                            
                                                                                            
**Day1_SK2: SoC Design and OpenLane**

![image](https://user-images.githubusercontent.com/86380243/123863692-e8409380-d8f7-11eb-9075-d3711c02c95b.png)

ASIC flow

![image](https://user-images.githubusercontent.com/86380243/123864814-2e4a2700-d8f9-11eb-8df5-6e430ff29b5c.png)

OpenLane ASIC flow

![image](https://user-images.githubusercontent.com/86380243/123875235-4fb20f80-d907-11eb-9d44-3461d4ad8f40.png)

![image](https://user-images.githubusercontent.com/86380243/123875463-b9cab480-d907-11eb-9b89-ec78b2bc845e.png)

DFT

![image](https://user-images.githubusercontent.com/86380243/123875662-1037f300-d908-11eb-960b-e6e78f319481.png)

EDA tools introduction

![image](https://user-images.githubusercontent.com/86380243/123877530-5b9fd080-d90b-11eb-99fa-4a7212ac283b.png)

In the pdks directory there are 2 sub directories:

libs.ref contain technology specific info

libs.tech contains tool specific info like which tools are supported by sky 130 tech

We will be working on sky130_fd_sc_hc (fd--> foundry, sc-->std cell, hc --> version)

-- Tech lef contains layer info

![image](https://user-images.githubusercontent.com/86380243/123878196-a1a96400-d90c-11eb-9a0a-e1a89b0fe64d.png)

Example of a .tlef file

![image](https://user-images.githubusercontent.com/86380243/123878517-32803f80-d90d-11eb-8831-79980195087c.png)

Example of a .lef file

![image](https://user-images.githubusercontent.com/86380243/123878351-e92ff000-d90c-11eb-885a-1a0a2bfc8d54.png)


--Lib file is as below. It contains different .lib files for different PVT corners (tt-->typical, ss--> slow slow, ff -->fast fast)

![image](https://user-images.githubusercontent.com/86380243/123878003-48413500-d90c-11eb-9ad1-154d851d5378.png)

example

![image](https://user-images.githubusercontent.com/86380243/123879429-e59d6880-d90e-11eb-8f3e-6dccf9d8094b.png)

![image](https://user-images.githubusercontent.com/86380243/123879488-fcdc5600-d90e-11eb-87ac-9706c6e4357a.png)

![image](https://user-images.githubusercontent.com/86380243/123879327-c1418c00-d90e-11eb-9f80-9eaab41863cf.png)

INVOKING openlane

In the openlane directory,

run the below commands

**docker**

**./flow.tcl -interactive**

**package require openlane 0.9**

Now, the designs are store in /openlane/designs and we are interested in picorv32

![image](https://user-images.githubusercontent.com/86380243/123881636-20a19b00-d913-11eb-886e-6c768b03825a.png)

Now lets see whats in a config.tcl file

![image](https://user-images.githubusercontent.com/86380243/123881709-4f1f7600-d913-11eb-84e6-bcf1ed86d3e0.png)

It basically sets the path for .v and SDC files and also can give a clock value which goes and overwrites the value in the design.

The design config.tcl is as below and has highest precedence:

![image](https://user-images.githubusercontent.com/86380243/123953383-27f99080-d975-11eb-9d32-5aceea1f01bf.png)

INVOKING OPENLANE

![image](https://user-images.githubusercontent.com/86380243/123953546-54151180-d975-11eb-8457-178757be56d8.png)

The rund directory is created after running the prep command as below

![image](https://user-images.githubusercontent.com/86380243/123953891-c128a700-d975-11eb-8cc9-e7bf776d6218.png)

All results and reports will be saved in the runs directory

![image](https://user-images.githubusercontent.com/86380243/123954301-3dbb8580-d976-11eb-9fbe-9cdc4a73f6d0.png)

THe config.tcl inside runs directiry shows parameters taken during the prep design steps. We can see the modifications which we made anyime and anywhere.

![image](https://user-images.githubusercontent.com/86380243/123954605-9ab73b80-d976-11eb-8a14-e49ae1630d8e.png)

The run_synthesis command will give all reports and the cell counts

![image](https://user-images.githubusercontent.com/86380243/123955831-12399a80-d978-11eb-8509-37ad0b2a6af5.png)

From above, we calculate flop ratio as NO. of DFF/ Total no. of cells

Flop ratio for the picorv32a design is 1613/14876 = 0.10 (10.84%)

The SYNTHESIS RESULTS directory:

![image](https://user-images.githubusercontent.com/86380243/123961120-06e96d80-d97e-11eb-8535-41a23402b924.png)

As we can see the netlis.v is generated

![image](https://user-images.githubusercontent.com/86380243/123961320-35ffdf00-d97e-11eb-8294-599c8a530951.png)

Synthesis report:

![image](https://user-images.githubusercontent.com/86380243/123961511-719aa900-d97e-11eb-8004-a3e36d80b763.png)

![image](https://user-images.githubusercontent.com/86380243/123961568-7d866b00-d97e-11eb-9659-d1eff2fbe4cd.png)
