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

- **docker**

- **./flow.tcl -interactive**

- **package require openlane 0.9**

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


## **Day 2**: Good floorplan vs Bad floorpan and introduction to library cells

**Day2_SK1: Chip floorplanning considerations**

- Defining height and Width of core and die
  -  Utilization factor: Area occupied by netlist/Total area of the core
  -  Aspect ratio is ratio of Height by width of the core. If aspect ratio is 1, it is a square.

![image](https://user-images.githubusercontent.com/86380243/123998447-80de1e80-d99f-11eb-872a-065787441199.png)

In reality, the utilization factor should be generally around 0.5 or 0.6 and the remaining area can be used for optimization like buffers etc.

- Defining locations of pre placed cells:
  - Preplaced cells are nothing but macros of which the locations have to be decided optimally.
  - If the macros are large in size, they can be broken down to small blocks depending on the routing resources etc. These instances can be accesed multiple time in the netlist.
  
  ![image](https://user-images.githubusercontent.com/86380243/124000481-9d7b5600-d9a1-11eb-990d-b734320ba048.png)
  
  - Also there are multiple IPs which are available like the Clockgating circuit, memory etc. which we can integrate with our design and the arrangement of these IPs is nothing but floorplanning.
  
  ![image](https://user-images.githubusercontent.com/86380243/124000650-cdc2f480-d9a1-11eb-8c77-7f5ca7ab3990.png)
  
  - Once the macros are placed, the APR tool will automatically detect the macros and will not touch.
  
  ![image](https://user-images.githubusercontent.com/86380243/124001387-9143c880-d9a2-11eb-96cd-e28ae7419ad1.png)

- Decoupling capacitors: Suround pre placed cells with decouplinng capacitors as they are mostly power hungry and need power intantaneuously. Due to IR drops on the power rails, the current might not be within noise margin at the input of the macro and this can lead to the entire chip to go for a toss.

![image](https://user-images.githubusercontent.com/86380243/124002190-702fa780-d9a3-11eb-9f20-09cf3c6d1ae4.png)

  a) The voltage should not be in the undefined range as it can either go to logic 0 or logic 1.
  
  b) The decoupling capacitors act as battery to provide power to the circuits directly. During switching activity, the capacitor discharges and when not switching, it charges through the power supply.
 
 ![image](https://user-images.githubusercontent.com/86380243/124002465-c56bb900-d9a3-11eb-84c9-c0012ea0c833.png)
 
 ![image](https://user-images.githubusercontent.com/86380243/124002626-f9df7500-d9a3-11eb-97b2-c1586de0ab8f.png)
 
- Power Planning
  - The chip should get uniform power i.e. VDD and GND throughout the chip in order to maintain signal integrity. If there is a long bus from a driver to load, there can be voltage droop or ground bounce issues.
  - Hence a mesh structure is built with many VDD and GND rails so that the chip gets enough power. The power rails are generally designed using higher metal layers as they have least resistance.
  

![image](https://user-images.githubusercontent.com/86380243/124004472-0bc21780-d9a6-11eb-99a6-82949601e857.png)

![image](https://user-images.githubusercontent.com/86380243/124004652-3a3ff280-d9a6-11eb-8db7-9ebd8ff9c40c.png)

 - Summarizing steps till this point, the mesh structure is as below:
 
 ![image](https://user-images.githubusercontent.com/86380243/124005062-a884b500-d9a6-11eb-9c92-e681187d0f87.png)


 - Pin placement and logical cell blockage 

   - Lets consider the below circuit
  ![image](https://user-images.githubusercontent.com/86380243/124008267-3e6e0f00-d9aa-11eb-98b4-a28ad892b233.png)
   
   - Place the pin as per the design requirements also based on minimum routing connectivity
   ![image](https://user-images.githubusercontent.com/86380243/124008867-e7b50500-d9aa-11eb-9b1b-365e16146cf6.png)
   
   - The clock pins should have least resistance and should be more in size and least resistance.
   ![image](https://user-images.githubusercontent.com/86380243/124008986-0e733b80-d9ab-11eb-85e0-77084f393035.png)
   
 - Logical cell blockage: No cells to be placed in the region between the core and die.
 ![image](https://user-images.githubusercontent.com/86380243/124009188-4c705f80-d9ab-11eb-89a1-68672705315a.png)


LABS on floorplanning:

- Lets see what all switches can be configured:
![image](https://user-images.githubusercontent.com/86380243/124010440-d10fad80-d9ac-11eb-9cc1-dc2968ba112d.png)

![image](https://user-images.githubusercontent.com/86380243/124010532-ebe22200-d9ac-11eb-958a-fb3b8e80be66.png)

- After run_synthesis, we do run_floorplan after configuring the swithces

![image](https://user-images.githubusercontent.com/86380243/124013812-c5be8100-d9b0-11eb-874e-78f7185ba2da.png)

![image](https://user-images.githubusercontent.com/86380243/124014158-2bab0880-d9b1-11eb-9f6f-87cd5108f418.png)

![image](https://user-images.githubusercontent.com/86380243/124014195-36659d80-d9b1-11eb-970c-1da68cc03846.png)

  - A DEF file is created in the runs directory
  
  ![image](https://user-images.githubusercontent.com/86380243/124014720-df13fd00-d9b1-11eb-9d85-c28f5d67e765.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124014781-efc47300-d9b1-11eb-8311-5bd36ab05f3d.png)

  The die coordinates are (0 0) lower left x and y (660685 671405) upper left corner x and y.
  
  Dividing these values, we get value in micro meter.
  
  - To view the floorplan layout, we need to be inside the floorplan directory and run the command:
  
  ![image](https://user-images.githubusercontent.com/86380243/124016119-48e0d680-d9b3-11eb-859e-e1073a8c4068.png)
  
  The command is:
  
  magic -T path of tech file(image below) lef read ../../tmp/merged.lef def read picrv32a.floorplan.def
  
  ![image](https://user-images.githubusercontent.com/86380243/124016748-fb189e00-d9b3-11eb-8df2-8fb3b57f03b4.png)
  
![image](https://user-images.githubusercontent.com/86380243/124017249-8134e480-d9b4-11eb-825c-c39f8fa91bd5.png)

![image](https://user-images.githubusercontent.com/86380243/124017571-de309a80-d9b4-11eb-9800-19f728fed7db.png)

  Note: Press s and then v to align the layout at the center in magic tool.
        To zoom in, left click the mouse then form a box by right clicking in whicehver part you want to zoon into. Press z to zoom in how much ever. Use arrow keys to move left right top and bottom
        To check what metal layer an input/output pin is, take cursor on that pin (DO NOT CLICK) and press s. We get to see the name of the pin. Next, fo to the tkcon window and type 'what', this will five the metal layer info.
        
 ![image](https://user-images.githubusercontent.com/86380243/124018891-5b104400-d9b6-11eb-82d8-3290b111c91b.png)
 
 Horizontal metal is layer 3 and vertical is layer 2.
 
 ![image](https://user-images.githubusercontent.com/86380243/124019076-990d6800-d9b6-11eb-97ad-fe7eeb68dc73.png)
 
   - Tap cells used to avoid latchup. They connect nwell to VDD and substrate to ground.
 
The standard cells are not placed in the floorplan but are present on the lower bottom corner of the layout.

![image](https://user-images.githubusercontent.com/86380243/124019640-4aac9900-d9b7-11eb-975c-54538eafb2d8.png)

        
**Day2_SK2: Library binding and placement **

- Binding netlist with physical cells
  - Take each and every component of the netlist is given proper width and height
  - All the info of width and height etc. along with timing info is present in library file (.lib). It will also have required conditions. 
  - The cells of different drive strengths of a same cell. Bigger the size, smaller the resistance.
  - Based on timing the cells are selected.
  ![image](https://user-images.githubusercontent.com/86380243/124024569-61ee8500-d9bd-11eb-8e27-d9b4b9e5d82d.png)
  
- Placement
  - Now we have floorplan, the netlist and the library of cells. 
  - We need to place the netlist on the floorplan
  
  ![image](https://user-images.githubusercontent.com/86380243/124024744-9f531280-d9bd-11eb-9160-6a56d52ad1d6.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124025837-eee60e00-d9be-11eb-98de-fd3deea73069.png)

- Optimized placement
  - This is needed if distance between two cells is large. Also to maintain signal integrity. 
  - We can place buffers based on wire length estimation and also the wire capacitance.
  - This is a tradeoff bween perforamnce and area as the buffers will help to improve performance but will compromise on area
  - The signal transition decides if we have to place a buffer. There is a range for the slew and transition should be within the given range.
  - If there is a criss cross connection, we use different metal layers
 
![image](https://user-images.githubusercontent.com/86380243/124027657-205fd900-d9c1-11eb-8ad7-98e678e095ee.png)

- Need for chRcterization
  - The library characterization is basically modelling the cells with respect to timing and functionality 
  ![image](https://user-images.githubusercontent.com/86380243/124028558-21453a80-d9c2-11eb-9654-f16ddf0c4d9f.png)

- Placement on open lane
  - Congestion driven placement and not timing driven
    - Global placement: Coarse placement with no legalization (placement of std cells inside rows abutted and no overlap). The main objective is to reduce wire length. In open lane, we use Half Parameter Wire Length (HPWM). The HPWM is reducing wirelength and the OvFL should decrease (design will converge). 
    - Detailed placement

  The command **run_placement** will do both the above placement 
  
  As we can see the DEF file is created in the placement directory:
  
  ![image](https://user-images.githubusercontent.com/86380243/124030987-c2cd8b80-d9c4-11eb-942b-ee18fb22c224.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124031129-edb7df80-d9c4-11eb-81c8-fcd120c9d3fd.png)
  
  As we can see that the standard cells are placed inside the std cell rows:
  
  ![image](https://user-images.githubusercontent.com/86380243/124031401-44251e00-d9c5-11eb-843e-2510988c01e3.png)


NOTE: In openlane the power generation is done AFTER CTS and not during floorplan


**Day2_SK3: Cell Design and Characterization**

- Cell Design Flow
![image](https://user-images.githubusercontent.com/86380243/124034047-bb0fe600-d9c8-11eb-8c6b-f785887fa9f7.png)
  
  - The library has cells with different functionalities and different drive strengths
  - It also has cells with different Vt i.e. threshold voltage
 
 ![image](https://user-images.githubusercontent.com/86380243/124034285-00ccae80-d9c9-11eb-9274-d331fe96ac95.png)

 ![image](https://user-images.githubusercontent.com/86380243/124034622-75075200-d9c9-11eb-9c24-48427e9df258.png)

  - Input rules: 
  ![image](https://user-images.githubusercontent.com/86380243/124034965-e2b37e00-d9c9-11eb-9fab-4b01c2717e84.png)
  
   SPICE models:
  ![image](https://user-images.githubusercontent.com/86380243/124035087-0d9dd200-d9ca-11eb-94b1-0bf804708bf1.png)
  
   Library and user defined specs: Cell height, supply voltage, metal layers, pin location, drawn gate length
   
  - Design steps:
    - Circuit Design: Implement function, model PMOS and NMOS wrt W/L 
    
    ![image](https://user-images.githubusercontent.com/86380243/124036226-aed95800-d9cb-11eb-9a59-947fc27b3f94.png)
    
    - Layout Design: Get the dual Euler's trail for PMOS and NMOS and output is GDSII, LEF, extracted SPICE netlist. 
    
    ![image](https://user-images.githubusercontent.com/86380243/124037423-8a7e7b00-d9cd-11eb-923b-c8b98f92fa0b.png)
    
    - Characterization: Timing, noise and power (.libs) and also functionality
    a) Read model file
    
    b) Extracted spice netlist
    
    c) Recognize behaviour of buffer
    
    d) Read the subckt of the design
    
    e) Attach necessary power sources
    
    f) Apply stimulus
    
    g) Output capacitance 
    
    h) Provide necessary simulation command (.tran for transient and .dc for dc simulation)
    
    ![image](https://user-images.githubusercontent.com/86380243/124038625-6d4aac00-d9cf-11eb-856f-70bd97c9be88.png)
 
    ![image](https://user-images.githubusercontent.com/86380243/124038476-307eb500-d9cf-11eb-9583-55e239324f51.png)
    
    All this is given to GUNA and outpts are timing, noise and power characterizations.

    
    **Day2_SK4: Timing Characterizations**
    
    - Different voltage levels required to calculate slew and propagation delay
    
    ![image](https://user-images.githubusercontent.com/86380243/124042219-5b203c00-d9d6-11eb-9915-79e2bcb4a506.png)
    
    - Propagation Delay:

    ![image](https://user-images.githubusercontent.com/86380243/124042348-a5a1b880-d9d6-11eb-9c48-737cd6c8227c.png)
    
      - Issues with setting a threshold point

        Now, if the threshold of 50% shifts above, then we get a negative delay and is not acceptable. This means we are geiing ouput before input. This is poor choice of threshold point.
        
        ![image](https://user-images.githubusercontent.com/86380243/124042541-0d580380-d9d7-11eb-981c-163a8c2194e5.png)
        
        At times even when 50 %, we get negative delay. IF there is a huge net between two inverters( buffer with 2 back to back as seen in above figures). Basically huge slew
        
        ![image](https://user-images.githubusercontent.com/86380243/124042694-63c54200-d9d7-11eb-8638-0970d5fe3629.png)
        
        ![image](https://user-images.githubusercontent.com/86380243/124042726-78a1d580-d9d7-11eb-8fb5-1701397a5fe8.png)

    - Transition Delay (Slew): Difference between high and low rise/fall (20-80% of VDD)

        ![image](https://user-images.githubusercontent.com/86380243/124042888-d6ceb880-d9d7-11eb-8dba-4d421dd4aaf8.png)
  
      
    
  ## **Day 3**: Design library cell using magic layout and ngspice characterization

**Day3_SK1: Labs for CMOS inverter ngspice simulations**

- Changing the FP_IO_MODE switch to 2, we get a different IO pin placement, which was equidistant initially

![image](https://user-images.githubusercontent.com/86380243/124188637-82861000-da8d-11eb-8c75-73ee305fa73e.png)


- Defining a SPICE Deck

![image](https://user-images.githubusercontent.com/86380243/124189692-19070100-da8f-11eb-9bad-1ac21a0f89b5.png)

Drain gate source substrate is the order in which a MOS transistor nodes are defines in SPICE

![image](https://user-images.githubusercontent.com/86380243/124189881-64211400-da8f-11eb-881c-430e8519f13a.png)

Complete SPICE deck

![image](https://user-images.githubusercontent.com/86380243/124190549-75b6eb80-da90-11eb-8704-b384fc0f877f.png)

The tech file contains all tech parameters of NMOS and PMOS

The mod file looks like this

![image](https://user-images.githubusercontent.com/86380243/124190783-d514fb80-da90-11eb-84d7-3a5aa7b23c5e.png)

![image](https://user-images.githubusercontent.com/86380243/124190867-f7a71480-da90-11eb-8a54-60e35e7814d4.png)

- Running SPICE simulations with same W/L for both PMOS and NMOS vs running it for PMOS 2.5 times, we see the VTC for PMOS is shifted to L and R respectively

![image](https://user-images.githubusercontent.com/86380243/124192753-ca0f9a80-da93-11eb-96eb-905d87ac8b2b.png)

- Switching threshold: Point at which device switches and both PMOS and NMOS are in sat region

![image](https://user-images.githubusercontent.com/86380243/124195019-95054700-da97-11eb-96fa-e81e6e1aa224.png)

![image](https://user-images.githubusercontent.com/86380243/124195263-13fa7f80-da98-11eb-8fb3-6c2ccb24ca64.png)

![image](https://user-images.githubusercontent.com/86380243/124195390-5f149280-da98-11eb-95fe-0387592d89e7.png)

Dynamic Simulation of Inverter: We give a pulse in this case and a tran instead of dc. We are doing this for PMOS and NMOS of equal sizes

![image](https://user-images.githubusercontent.com/86380243/124195664-e3ffac00-da98-11eb-9ed5-7ee7caad4177.png)

![image](https://user-images.githubusercontent.com/86380243/124195838-317c1900-da99-11eb-859d-4e9c9367d05d.png)

![image](https://user-images.githubusercontent.com/86380243/124196189-e44c7700-da99-11eb-9448-92c78084b062.png)

Labs on characterization:

Git clone from https://github.com/nickson-jose/vsdstdcelldesign.git

Copy tech files from magic into this cloned repository

![image](https://user-images.githubusercontent.com/86380243/124198256-4909d080-da9e-11eb-8073-ae1f4a59a230.png)

![image](https://user-images.githubusercontent.com/86380243/124198285-56bf5600-da9e-11eb-9c67-c557fa4be57c.png)

![image](https://user-images.githubusercontent.com/86380243/124198433-a736b380-da9e-11eb-9800-a4b68abbcb05.png)



**Day3_SK2: Inception of Layout CMOS fabrication process**

- 16 mask CMOS process

![image](https://user-images.githubusercontent.com/86380243/124198743-51aed680-da9f-11eb-821a-fa8339ce1588.png)

![image](https://user-images.githubusercontent.com/86380243/124199094-28db1100-daa0-11eb-8e59-b49ce7768c21.png)

![image](https://user-images.githubusercontent.com/86380243/124199141-490ad000-daa0-11eb-8bdf-6cdfeceebef4.png)

![image](https://user-images.githubusercontent.com/86380243/124199218-72c3f700-daa0-11eb-889c-10e4f054d053.png)

![image](https://user-images.githubusercontent.com/86380243/124199255-81aaa980-daa0-11eb-95c5-5da2dbe42c76.png)

![image](https://user-images.githubusercontent.com/86380243/124199356-b3237500-daa0-11eb-8fc9-84b0d7e25471.png)

In above figure, field oxide is grown. This process is called LOCOS - Local Oxidation of Silicon

![image](https://user-images.githubusercontent.com/86380243/124199472-f8e03d80-daa0-11eb-885f-e4d7fe14b485.png)

![image](https://user-images.githubusercontent.com/86380243/124199495-05fd2c80-daa1-11eb-801d-bda6f4d5f769.png)

  - Nwell and pwell
  
  ![image](https://user-images.githubusercontent.com/86380243/124199798-c7b43d00-daa1-11eb-8c57-ba6085b4306a.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124199831-ddc1fd80-daa1-11eb-8a59-2b476ce7a706.png)

  Creating p well by Boron ion implantation
  
  ![image](https://user-images.githubusercontent.com/86380243/124199924-1b268b00-daa2-11eb-87a7-6220f444059c.png)
  
  Creating n well
  
  ![image](https://user-images.githubusercontent.com/86380243/124200007-46a97580-daa2-11eb-858b-39de74c6959e.png)

  ![image](https://user-images.githubusercontent.com/86380243/124200060-6b9de880-daa2-11eb-9e52-039a8b9feda6.png)

  Increasing depth of well: Twin tub process
  
  ![image](https://user-images.githubusercontent.com/86380243/124200190-b15ab100-daa2-11eb-9851-d4b1afe5858f.png)
  
  
  Creating gate terminal
  
  Vt dependent on below factors
  
  ![image](https://user-images.githubusercontent.com/86380243/124200538-9c325200-daa3-11eb-846e-da2e0e08a8e7.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124200640-d996df80-daa3-11eb-904c-29bd74a1b420.png)
  
  Introduce boron again with a low energy than before as we want it only on the surface. This is how we modify the doping concentration and also the Vt
  
  ![image](https://user-images.githubusercontent.com/86380243/124200728-0f3bc880-daa4-11eb-9b64-01e2177d062b.png)
  
  While boron penetrates, the oxide layer damages
  
  Similarly do for Pmos - Mask5
  
  ![image](https://user-images.githubusercontent.com/86380243/124200808-38f4ef80-daa4-11eb-83e3-064a2d5a0754.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124200849-5b870880-daa4-11eb-8d34-c28a3578df2a.png)
  
  Can use phosphorus or arsenic as both are n type impurities
  
  Next is fix damages to oxide region. Also the newly formed oxide region will have dimensions with respect to the Vt which we want.
  
  ![image](https://user-images.githubusercontent.com/86380243/124200997-c9cbcb00-daa4-11eb-85bf-be00b3c5685c.png)
  
  Next we need to make the gate. Fist put poly throughout (red) and dope it with n type impurity as gate has to be low resistance (sheet)
  
  ![image](https://user-images.githubusercontent.com/86380243/124201057-fd0e5a00-daa4-11eb-95db-0a60ff75a949.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124201110-26c78100-daa5-11eb-9cb8-74fd7bf06abd.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124201135-3c3cab00-daa5-11eb-9595-b5ad17631b62.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124201183-570f1f80-daa5-11eb-904d-15dd3b554ae8.png)
  
  - Lightly doped drain formation (LDD)

  ![image](https://user-images.githubusercontent.com/86380243/124201341-cbe25980-daa5-11eb-9eb2-74924b502c28.png)
  
  Here P+ and N+ are used for source and drain for PMOS and NMOS respectively. P- and N- are for the LDD to take care of the short channel effect and the hot electron effect.
  
  ![image](https://user-images.githubusercontent.com/86380243/124201807-f41e8800-daa6-11eb-87e9-d51dcb44d30b.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124201873-25975380-daa7-11eb-9c7c-7185600f03f9.png)

  ![image](https://user-images.githubusercontent.com/86380243/124201905-38aa2380-daa7-11eb-9b70-516d65a65fa4.png)

  ![image](https://user-images.githubusercontent.com/86380243/124201946-54adc500-daa7-11eb-8939-3ef4690a4e30.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124201990-6abb8580-daa7-11eb-927c-7400a4326ba3.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124202022-82930980-daa7-11eb-9445-ae09c38fa8e5.png)

  These are side wall spacers. They help to retain the N- and P- implants just below them when we do the N+ and P+ implant later.
  
 - Source and drain formation
 
  First add a thin layer of oxide above the source and drain terminals. This is done to avoid channeling. Chaneelling is when we doa lot of ion imolanting and when vector vel of ion matches p substrate and the ion penetates into the p substrate.
  
  ![image](https://user-images.githubusercontent.com/86380243/124202512-7eb3b700-daa8-11eb-82f2-24e9c076e83c.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124202533-8a06e280-daa8-11eb-9326-7ffbc5c42aad.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124202560-9723d180-daa8-11eb-9ffb-602f37abefb5.png)
  
  the LDD remaines intact due to the side wall spacers.
  
  ![image](https://user-images.githubusercontent.com/86380243/124202678-db16d680-daa8-11eb-824b-8960f9b01399.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124202692-ea961f80-daa8-11eb-8418-8a4d72cccd0b.png)

  Similarly do for Pmos. Use boron here
  
  ![image](https://user-images.githubusercontent.com/86380243/124202723-ff72b300-daa8-11eb-8b81-2c4732e0a193.png)
  
  ![image](https://user-images.githubusercontent.com/86380243/124202778-25985300-daa9-11eb-97c9-17512dda491a.png)
  
  Next put it to high furnace annealing, this will penetrate p+ and n+ more deep similar to the twin tub
  
  ![image](https://user-images.githubusercontent.com/86380243/124202862-61cbb380-daa9-11eb-8bba-60f2fc9e7268.png)

- Steps to form contacts and interconnect

Here we remove the thin oxide which we had done in previous steps using hydrofloric soln

![image](https://user-images.githubusercontent.com/86380243/124202962-a1929b00-daa9-11eb-8f5b-3fed29c09665.png)

Sputtering: Hitting argon gas on the Titanium metal and it emits on the substrate 

![image](https://user-images.githubusercontent.com/86380243/124203023-c5ee7780-daa9-11eb-875b-b2b5bcb8609e.png)

![image](https://user-images.githubusercontent.com/86380243/124203120-ffbf7e00-daa9-11eb-9256-a2439674ca94.png)

Next we need to make contacts. The white layer is TiN used for local communication 

![image](https://user-images.githubusercontent.com/86380243/124203208-2ed5ef80-daaa-11eb-8079-37dc5b10c49e.png)

Now we can do some local internal connection for an inverter like the D of NMOS and PMOS are connected to the output 

![image](https://user-images.githubusercontent.com/86380243/124203396-a0ae3900-daaa-11eb-8a4e-f51a8c2bed9d.png)

![image](https://user-images.githubusercontent.com/86380243/124203452-c4717f00-daaa-11eb-9a78-852a3367d285.png)

![image](https://user-images.githubusercontent.com/86380243/124203554-fbe02b80-daaa-11eb-9639-1b0336642f7e.png)

- Higher level metal formation: We add a thick oxide layer because of the surface is non linear

![image](https://user-images.githubusercontent.com/86380243/124203722-5c6f6880-daab-11eb-88ed-ef55a2e84e18.png)

Planarization

![image](https://user-images.githubusercontent.com/86380243/124203784-790ba080-daab-11eb-95c4-e36f73163153.png)

Contact holes

![image](https://user-images.githubusercontent.com/86380243/124203892-b96b1e80-daab-11eb-852b-d7db0127f060.png)

![image](https://user-images.githubusercontent.com/86380243/124203936-d7388380-daab-11eb-9ed3-b0ff4916c509.png)

![image](https://user-images.githubusercontent.com/86380243/124203951-e0295500-daab-11eb-92c6-e1c6c1577c83.png)

![image](https://user-images.githubusercontent.com/86380243/124203963-e7506300-daab-11eb-8248-3ad3788d3a5a.png)

![image](https://user-images.githubusercontent.com/86380243/124203988-fa633300-daab-11eb-8ff4-37c187b76015.png)

![image](https://user-images.githubusercontent.com/86380243/124204012-0e0e9980-daac-11eb-8fb6-34cc16ff1ea8.png)

![image](https://user-images.githubusercontent.com/86380243/124204051-2a123b00-daac-11eb-8880-bce9b21ef351.png)

![image](https://user-images.githubusercontent.com/86380243/124204092-40b89200-daac-11eb-9a42-8a9c1e6dac38.png)

![image](https://user-images.githubusercontent.com/86380243/124204219-98ef9400-daac-11eb-895e-1ad84ef16129.png)


Labs for characterizing:

Considering the layout of an inverter, if a poly crosses n-diff its and nmos and if it crosses a p diffusion its a pmos

![image](https://user-images.githubusercontent.com/86380243/124204583-58dce100-daad-11eb-9cb0-76f4882b4dc7.png)

![image](https://user-images.githubusercontent.com/86380243/124204643-77db7300-daad-11eb-97d5-30a4a769d23f.png)

Checking connectivity of output and drain terminals of both MOS. (take cursor at y and press 's' thrice).

![image](https://user-images.githubusercontent.com/86380243/124204951-2b446780-daae-11eb-8fb9-00160f38e4b8.png)

Checking connectivity of source of pmos (take cursor and press 's' thrice)

![image](https://user-images.githubusercontent.com/86380243/124204998-4dd68080-daae-11eb-835a-b00a645f5955.png)

There should be contact between nwell and locali (n subs contact) & contact between locali(licol) and m1. Similarly for nmos - contact between locali and pusbs & locali and m1

Nwell and above that is locali and aboce that is m1


- Extracting spice and do simulation on ngspice

![image](https://user-images.githubusercontent.com/86380243/124209477-9e9ea700-dab7-11eb-8af4-c01fabcd1501.png)

The **extract all** command creates the sky130_inv.ext file and the second **ext2spice** command creates sky130_inv.spice file

The spice file contains the below parameters

![image](https://user-images.githubusercontent.com/86380243/124209699-081eb580-dab8-11eb-9b3a-5c7fec38b592.png)

NOTE: We need to edit the scale value in the spice file with respect to the grid value in the layout.

![image](https://user-images.githubusercontent.com/86380243/124211125-9c8a1780-daba-11eb-8dbe-9cbeea862aed.png)

Since its 0.01, we make changes int he spice file.

![image](https://user-images.githubusercontent.com/86380243/124211276-d78c4b00-daba-11eb-8688-925c0554c603.png)

Also, we need to include pmos and nmos lib files. pshort.lib and nshort.lib

![image](https://user-images.githubusercontent.com/86380243/124211578-55505680-dabb-11eb-8920-862c2b54c8f0.png)

Modifying the soice file like below:

![image](https://user-images.githubusercontent.com/86380243/124216227-c0059000-dac3-11eb-9429-612f39e0a67b.png)

Run the command **ngspice sky130_inv.spice**

![image](https://user-images.githubusercontent.com/86380243/124216321-ff33e100-dac3-11eb-9be2-60846af93c97.png)













  
  


 
  
    

 



  


  
  


        







  

