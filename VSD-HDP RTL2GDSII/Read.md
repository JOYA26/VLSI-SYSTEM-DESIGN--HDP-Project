##Day 0

**Tools** **Installation**

Yosys

iverilog

gtkwave

Open STA

Magic

ngspice


**Yosys Installation**

$ git clone https://github.com/YosysHQ/yosys.git

$ cd yosys-master 

$ sudo apt install make 

$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
    
$ make 

$ sudo make install

The following images show installation & launch of Yosys

![Screenshot from 2023-09-15 17-17-08](https://github.com/JOYA26/JOYA26/assets/140269634/601d7dee-216f-4b60-a110-c0e1adeebf76)

![Screenshot from 2023-09-15 17-17-15](https://github.com/JOYA26/JOYA26/assets/140269634/1d50d3b9-019f-4914-bce6-0cc7df89f9ec)

**iVerilog**

$ sudo apt update

$sudo apt-get install iverilog

![iVerilog](https://github.com/JOYA26/JOYA26/assets/140269634/d0c0ce05-7f9a-40aa-8820-13b97e376200)

**gtkwave**

$ sudo apt update

$ sudo apt install gtkwave

![Screenshot from 2023-09-15 17-19-58](https://github.com/JOYA26/JOYA26/assets/140269634/a45ecf4d-1725-4450-8bcc-4fcc866c7243)

OpenSTA

$ sudo apt-get install cmake clang gcctcl swig bison flex

$ git clone https://github.com/The-OpenROAD-Project/OpenSTA.git

$ cd OpenSTA

$ mkdir build

$ cd build

$ cmake ..

$ make

**Got some error**

![Screenshot from 2023-09-15 17-23-21](https://github.com/JOYA26/JOYA26/assets/140269634/7e69d0d2-3a40-46ac-a3d8-e99bb869e4b3)

So performed the following instruction 

$ sudo apt update

$ sudo apt 0penSTA

![Screenshot from 2023-09-15 17-51-42](https://github.com/JOYA26/JOYA26/assets/140269634/d5590756-b604-41b3-a27a-3d326c2e8b29)

Magic

$ sudo apt-get install m4

$ sudo apt-get install tcsh

$ sudo apt-get install csh

$ sudo apt-get install libx11-dev

$ sudo apt-get install tcl-dev tk-dev

$ sudo apt-get install libcairo2-dev

$ sudo apt-get install mesa-common-dev libglu1-mesa-dev

$ sudo apt-get install libncurses-dev

![Screenshot from 2023-09-15 18-02-31](https://github.com/JOYA26/JOYA26/assets/140269634/1d8fc909-0e48-4744-b096-010e7ee52f57)

**Ngspice**

$ sudo apt update

$ sudo apt install ngspice

![Screenshot from 2023-09-15 17-48-24](https://github.com/JOYA26/JOYA26/assets/140269634/d0d15e87-e9fc-4e92-be5f-bfa3d4a15b0a)


#DAY1

##Lab using iverilog & gtkwave


**Brief**: Simulate and synthesize and verification of a design in  iverlog,gtkwave and yosys. 

Yosys is used to convert the RTL to netlist. read_verilog,read_liberty and write_verilog command is used by yosys to read the design ,read the .lib and write out the netlist respectively. 

The simulator iverilog takes the netlist and the testbench as input. It  will dump any changes in the input to the output in the form of vcd (value change dump) file. gtkwave  is used to view and verify the functionality of  the vcd output waveforms. THe output of the gtkwave is same as the RTL simulation output.

**Lab setup**

Checking the tools and library files needed for simulation. 

The standard cell library  contains all the source files and testbench files is in verilog model.

**Implementation of a 2X1 MUX in iverilog & gtkwave**

1)Load the 2X1 MUX  design  and testbench in iverilog.($ iverilog good_mux.v tb_good_mux.v)

2)a.out file is created which dumps the vcd file.($ ./a.out)

3)Loading the vcd file in gtkwave ($ gtkwave tb_good_mux.vcd)

4)Checking the functionatily of the simulated Waveform.

   ![waveform1](https://github.com/JOYA26/JOYA26/assets/140269634/97777b44-0276-4b48-8a08-49ee8db28d71)

** To see verilog code of the mux, I use this command

$ gvim tb_good_mux.v -o good_mux.v 

![Screenshot from 2023-10-25 15-23-54](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/f3fa0886-8def-4c63-82e8-44e80591d078)

**Synthesis** 

   The following commands are used for synthesis

yosys> read_liberty -lib <path to lib file>

yosys> read_verilog <path to verilog file>

yosys> synth -top <top_module_name>

yosys> abc -liberty <path to lib file>

yosys> show

Writing the verilog files and geneate netlist


yosys> write_verilog <top_module_name>_netlist.v

yosys> write_verilog -noattr <top_module_name>_netlist.v

yosys> !gvim <top_module_name>_netlist.v 

Synthesis of 2X1 Mux

![Screenshot from 2023-10-25 15-30-52](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/4cb328ca-20e7-4f07-9050-617a801ebeed)

Graphical version of the logic

![Screenshot from 2023-10-25 15-35-01](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/27cc7bbf-ed10-4087-b28e-8e69ab568d09)

Generate netlist 
![Screenshot from 2023-10-25 15-38-12](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/8c72d0ea-8eec-407c-8fc5-bb939d1397d0)





**DAY2**

Here I learn various information about the standard logic cells in the library present in ".lib".The PVT (pressure-voltage-temperature) is the operating conditon of the logic cells.Factors such as leakage power, area , technology ,cell delay, PP(Power port), pin description, transition of the pins and  all other information are formatted in liberty format. It consists are variety of versions for single cell to used in multiple scenarios each cell has it own pros and cons regarding delay , area , performance . 

Synthesize of the multiple_modules.v in different synthesis methods(Hierarachial vs Flat) and next is to synthesize in sub-module level , where bottom-up approach is used to optimize the design and the run time of the tool other thing is the Module Instantiation technique to synthesize once and instantaite multiple time in the designs.

**Top module synthesis/ Hierarical Design**

![Screenshot from 2023-10-25 16-07-47](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/efcf93a0-689d-4e42-b44c-1e0700f4bd25)

**Synthesis of flatten**
yosys> read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025C_1c80.lib

yosys> read_verilog multiple_modules.v

yosys> synth -top multiple_modules

yosys> abc -liberty ../lib/sky130_fd_sc_hd_tt_025C_1c80.lib 

yosys> flatten

yosys>show

![Screenshot from 2023-10-25 16-35-18](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/7b30fb8a-b9a4-457e-a0b4-9c04319b0076)


Netlist of the flat multiple module
yosys> write_verilog -noattr <name: multiple_modules_flat.v>
yosys> !gvim multiple_modules_flat.v

![Screenshot from 2023-10-25 16-25-15](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/fff09a3f-907d-4d29-84e1-4908f6e81056)

**Synthesis of sub_module1

yosys> read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025C_1c80.lib

yosys> read_verilog multiple_modules.v

yosys> synth -top sub_modulel

yosys> show

![Screenshot from 2023-10-25 16-58-00](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/ce311f71-f59a-49f8-9542-039968ff3dd7)


![Screenshot from 2023-10-25 16-50-27](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/5efb4328-4ad9-4f11-9d2b-afad60dd9a5d)

**Synthesis of Flops**

dff_asynchronous_reset
![dff async reset](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/3dabf844-9288-402a-88c2-1b9fc609e3b4)

dff_asynchronous_set Synthesis

![dff async set](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/e88cdc35-0c82-475e-874d-4fd07fa9282e)

dff_asynchronous_reset Synthesis

![dff sync res](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/913da9e4-5401-40c0-9d1d-05b2a80a9b63)

  mult_2.v synthesis 

![mult synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/bf1c6d29-b554-4a65-ae5f-f4a23bb72715)

mult_8.v synthesis 

![mult8 synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/4cfb1685-319f-4199-af03-faa52999b533)

**DAY3**

Combinational and Sequential Optimisation

Optimisation of a 2X1MUX Into AND Logic|opt_check.v

yosys> read_liberty -lib ../lib/sky130_fd_sc_hd_tt_025C_1c80.lib

yosys> read_verilog opt_check.v

yosys> synth -top opt_check

yosys>opt_clean -purge

yosys>abc -liberty ../lib/sky130_fd_sc_hd_tt_025C_1c80.lib

yosys> show

![opt check synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/e72d2614-50b9-4c46-a170-133e2eb5d423)

Optimisation of opt_check2.v

Here I get a 2 input OR gate after optimisation

![opt check2 synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/055d3c76-a044-40e3-83de-e40fbbe5b1c9)

Optimisation of opt_check3.v

Here I get a 3 input AND gate after optimisation

![opt check3 synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/9941bc89-c454-4dc4-beb9-d39004948d78)

Optimisation of opt_check3.v

Here I get a XNOR gate after optimisation

![opt check 4 synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/6374d143-e8e9-4de7-98db-66393d690918)

Optimisation of multiple_modules_opt.v

![multiple modules synth](https://github.com/JOYA26/VLSI-SYSTEM-DESIGN--HDP-Project/assets/140269634/29b1275f-6e1d-47d0-9bc5-1ea16b989733)













