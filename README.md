# VLSI-SYSTEM-DESIGN--HDP-Project

Day 0

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


##DAY1

**Lab using iverilog & gtkwave**


**Brief**: Simulate and synthesize and verification of a design in  iverlog,gtkwave and yosys.

Yosys is used to convert the RTL to netlist. read_verilog,read_liberty and write_verilog command is used by yosys to read the design ,read the .lib and write out the netlist respectively. 

 The simulator iverilog takes the netlist and the testbench as input. It  will dump any changes in the input to the output in the form of vcd (value change dump) file. gtkwave  is used to view and verify the functionality of  the vcd output waveforms. THe output of the gtkwave is same as the RTL simulation output.

**Lab setup**

Checking the tools and library files needed for simulation. 

The standard cell library  contains all the source files and testbench files is in verilog model.

**Implementation of a 2X1 MUX in iverilog & gtkwave**

1)Load the 2X1 MUX  design  and testbench in iverilog.

2)a.out file is created which dumps the vcd file.

3)Loading the vcd file in gtkwave

4)Checking the functionatily of the simulated Waveform.

   ![waveform1](https://github.com/JOYA26/JOYA26/assets/140269634/97777b44-0276-4b48-8a08-49ee8db28d71)

   


**DAY2**
