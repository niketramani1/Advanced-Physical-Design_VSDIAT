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

        
**Day1_SK2: Library binding and placement **

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

    

    



    


  


  
  


        







  

