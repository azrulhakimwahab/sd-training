# :book: My Respository

## Contents

[DAY 0 System/Tool Setup Check. GitHub ID creation](https://github.com/azrulhakimwahab/sd-training/blob/main/Report.md#day-0)

[DAY 1 Introduction to Verilog RTL design and Synthesis](https://github.com/azrulhakimwahab/sd-training/blob/main/Report.md#day-1)

[DAY 2 Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles](https://github.com/azrulhakimwahab/sd-training/blob/main/Readme.md#day-2--timing-libsqtmsetms-hierarchical-vs-flat-synthesis-and-efficient-flop-coding-styles)

# :book: Day 0-System/Tool Setup Check. GitHub ID creation
## Theory Recap
**IC Package**-Integrated circuits are put into protective packages to allow easy handling and assembly onto printed circuit boards and to protect the devices from damage.Exp:<br />
<img src="https://user-images.githubusercontent.com/118953938/205218471-519b2b8c-384c-4015-b869-af05d6407829.png" width=30% height=30%>
<br />
<img src="https://user-images.githubusercontent.com/118953938/205211281-f9ea98e9-eef4-45ca-a579-7de14f7eca8b.png" width=40% height=40%>

**Wire Bond**-Wire bonding is the process of creating electrical interconnections between semiconductors (or other integrated circuits) and silicon chips using bonding wires, which are fine wires made of materials such as gold and aluminium.

<img src="https://user-images.githubusercontent.com/118953938/205212706-e6191967-6885-41d5-afc3-8751144ab36f.png" width=50% height=50%>

**Die**-A die, in the context of integrated circuits, is a small block of semiconducting material on which a given functional circuit is fabricated.

**Pads**-A bonding pad serves the purpose of connecting the circuit on a die to the pin on a packaged chip

**Core**-An IP core consists of a block of logic or data that is used in a semiconductor chip. It is usually the intellectual property of a particular person or company. 

**Macros**- Also called as a custom building block

### Basic understanding of System Software interactions

1) Application softwares-*An application, also referred to as an application program or application software, is a computer software package that performs a specific function directly for an end user or, in some cases, for another application.*
2) System Software-*System software is a type of computer program that is designed to run a computer's hardware and application programs.*
    2.1) Compiler-compiler, computer software that translates (compiles) source code written in a high-level language (e.g., C++) into a set of machine-language instructions that can be understood by a digital computer's CPU. Compilers are very large programs, with error-checking and other abilities.<br />
    2.2) Assembler-A software that converts an assembly language code to machine code. It takes basic Computer commands and converts them into Binary Code that Computer's Processor can use to perform its Basic Operations.
3) Hardware-*Hardware refers to the external and internal devices and equipment that enable you to perform major functions such as input, output, storage, communication, processing, and more.* 
as shown below

<img src="https://user-images.githubusercontent.com/118953938/205213514-731d48e5-526e-4525-a472-5247fabe5ad9.png" width=50% height=50%>

Synthesis-<br />
Synthesis is a process of converting RTL (synthesizable Verilog code) into a technology specific Gate level netlist which includes nets, sequential cells, combinational cells and their connectivity. In other words, It is a process of combining pre-existing elements to form something new. It is the conversion of an idea into an implementation.<br />

### Next Review
1) Logic Synthesis
2) Static Timing Analysis

################################################################################################

## Lab Work

### Intel Unix System

<img src="https://user-images.githubusercontent.com/118953938/205214388-1e25012b-6851-47a6-9b7c-437779e538ab.png" width=50% height=50%>

Successfully executed!


# :book: Day 1-Introduction to Verilog RTL design and Synthesis

## Quick theory recap

**1) RTL (Register−Transfer Level)**- A design abstraction which models a synchronous digital circuit in terms of the flow of digital signals between hardware registers, and the logical operations performed on those signals<br />
**1.1) Benefit**: more compact since the language is more of an actual hardware modeling language. Write fewer lines of code, and it elicits a comparison to the C language.<br />

**2) Hardware description language (HDL)**: A programming language used to describe the behavior or structure of digital circuits (ICs).

**3) iVerilog**: An implementation of the Verilog hardware description language compiler that generates netlists in the desired format.

**4) GTKWave**: A fully featured GTK+ based wave viewer for Unix, Win32, and Mac OSX which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog. 

<img src="https://user-images.githubusercontent.com/118953938/205651867-5bfd9786-fe3b-493a-8d9d-5f835ea4c9db.png" width=50% height=50%>

##########################################################################################################

## Lab Work
### Lab 1- Introduction to Lab
1.1) Copying directory from source <br />
<img src="https://user-images.githubusercontent.com/118953938/205256498-ca0e627e-924d-419e-8099-f5d832882c20.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205256649-2699c0ec-b49d-4fab-83af-a2d678915d05.png" width=50% height=50%>

### Lab 2- Introduction to iverilog and GTKWave Part 1
2.1) Launching the GTKWave <br />
<img src="https://user-images.githubusercontent.com/118953938/205260137-79f93e7a-ad6b-4879-87ce-18bccbb15ef0.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205260341-e0bfea4e-3a18-4816-aadb-fa914fd0d384.png" width=50% height=50%>
<img src="https://user-images.githubusercontent.com/118953938/205260820-9d56d72a-1eee-4f65-9969-7e56d776150f.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205261274-3b66e0cf-46b1-44d3-9f4c-251b71595e86.png" width=50% height=50%>

### Lab 2- Introduction to iverilog and GTKWave Part 2
2.2) Displaying file content (module and testbench of good_mux.v) <br />
<img src="https://user-images.githubusercontent.com/118953938/205565493-518ebbe0-bd06-49ca-95a2-b6ed521ebc9f.png" width=50% height=50%>

**Testbench** <br />

    `timescale 1ns / 1ps 
    module tb_good_mux;
        // Inputs
        reg i0,i1,sel;
        // Outputs
        wire y;

        // Instantiate the Unit Under Test (UUT)
        good_mux uut (
                .sel(sel),
                .i0(i0),
                .i1(i1),
                .y(y)
        );

        initial begin
        $dumpfile("tb_good_mux.vcd");
        $dumpvars(0,tb_good_mux);
    // Initialize Inputs
        sel = 0;
        i0 = 0;
        i1 = 0;
        #300 $finish;
    always #75 sel = ~sel;
    always #10 i0 = ~i0;
    always #55 i1 = ~i1;
    endmodule

####################################################################################
    
    module good_mux (input i0 , input i1 , input sel , output reg y);
    always @ (*)
    begin
        if(sel)
                y <= i1;
        else
                 y <= i0;

### Lab 3- Labs using yosys and SKY130 PDKs Good_mux Part 1

#### 3.1) Invoking YOSYS <br />

<img src="https://user-images.githubusercontent.com/118953938/205570129-9ab774c1-bfc1-4f56-8608-f22952e646a7.png" width=50% height=50%>

**3.2) read_liberty -lib ../my_lib/lib/sky*.lib and read_verilog good_mux.v <br />**
<img src="https://user-images.githubusercontent.com/118953938/205580276-cca4faf2-9989-4b41-96ca-b1cb20596dda.png" width=50% height=50%>

**3.3) synth -top good_mux <br />**
<img src="https://user-images.githubusercontent.com/118953938/205580716-c39e49e1-07ab-414b-8772-8416c03dce3b.png" width=50% height=50%>

**3.4) abc -liberty ../lib/sky*.lib <br />**
<img src="https://user-images.githubusercontent.com/118953938/205584426-033b3a65-620f-4750-9798-6a9e5d12dbb0.png" width=80% height=80%>

**3.5) show (display) <br />**
<img src="https://user-images.githubusercontent.com/118953938/205584955-2c0c5989-8753-462a-96fc-b7ff1de5228e.png" width=50% height=50%>

### Lab 3- Labs using yosys and SKY130 PDKs Good_mux Part 2

**3.6) Considering 2 input mux <br />**
<img src="https://user-images.githubusercontent.com/118953938/205657687-70840dca-3b7b-4bab-a0fb-0e9d1c118578.png" width=50% height=50%><br />

Conversion from the synthesis to logic circuit can be done by reading the diagram above. Can be also checked by using Boolean equation to confirm the logic design.<br />
<img src="https://user-images.githubusercontent.com/118953938/205657433-e21f64a5-8057-4d76-92c5-863563ec6526.png" width=50% height=50%><br />

### Lab 3- Labs using yosys and SKY130 PDKs Good_mux Part 3

**3.7) write_verilog good_mux_netlist.v and !vim good_mux_netlist.v <br />**
<img src="https://user-images.githubusercontent.com/118953938/205591107-be8cc6f1-d76f-4b1e-89dd-c2b4efa6d097.png" width=50% height=50%>

**3.8) (simplified) write_verilog -noattr good_mux_netlist.v and !vim good_mux_netlist.v <br />**
<img src="https://user-images.githubusercontent.com/118953938/205591648-9d3c6e7b-114c-45bb-843b-4a0a11c3d41b.png" width=50% height=50%>


# :book: Day 2- Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles

**Note/: Theory was put between the labs**

### Lab Work
### Lab 4 -Introduction to timing .libs Part 1
‌
4.1) Open .lib 

<img src="https://user-images.githubusercontent.com/118953938/206061310-8eddbd07-20ed-44f6-8173-53fce86fa270.png" width=50% height=50%>

**tt**- typical <br />
**025C**- temperature

### PVT
PVT is the Process, Voltage, and Temperature. In order to make our chip to work after fabrication in all the possible conditions, we simulate it at different corners of process, voltage, and temperature. These conditions are called corners. All these three parameters directly affect the delay of the cell.

1) Process (variations due to fabrication)- Process variation is the naturally occurring variation in the attributes of transistors (length, widths, oxide thickness) when integrated circuits are fabricated.<br />
2) Voltage - Variation of voltage contributes to the variation of behaviour in the circuit. <br />
3) Temperature - The transistor density is not uniform throughout the chip. Some regions of the chip have higher density and higher switching, resulting in higher power dissipation and Some regions of the chip have lower density and lower switching, resulting in lower power dissipation Hence the junction temperature at these regions may be higher or lower depending upon the density of transistors.<br />

### Lab 4 -Introduction to timing .libs Part 2

4.2) Information extraction from .lib

<img src="https://user-images.githubusercontent.com/118953938/206067245-4bf69a56-199b-439a-8a05-b92c82456042.png" width=50% height=50%>

**Commands**

        :se nu - enabling the line numbers

<img src="https://user-images.githubusercontent.com/118953938/206264279-a27561bb-4b26-411f-9f9d-1897b3ed42b3.png" width=50% height=50%>

Information on "a2111o"<br />
1) 'a'- and gate
2) 'o' or gate
3) '2'- 2 input and gate
4) '2111'- 4 input or gate

<img src="https://user-images.githubusercontent.com/118953938/206265818-8fcf1d0f-5a57-4637-9006-cc2e6dae5da6.png" width=50% height=50%>

### Lab 4 -Introduction to timing .libs Part 3

<img src="https://user-images.githubusercontent.com/118953938/206268527-c8eeee1f-c2a6-481f-abeb-13302da10a3a.png" width=50% height=50%>

**Commands**

        :vsp-split the screen
        -to review more information
        
![image](https://user-images.githubusercontent.com/118953938/206269265-850d17bb-50d2-4a6f-9ca0-92e8abbf5e02.png)

### Lab 5 -Hier synthesis flat synthesis Part 1

<img src="https://user-images.githubusercontent.com/118953938/206068994-b43a7b0c-73c8-4c5c-9de9-2bf54770bf58.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/206074036-bc277834-94f1-4488-9dfb-e99ca16b6057.png" width=50% height=50%><img src="https://user-images.githubusercontent.com/118953938/206188884-53852bc3-a1de-471c-8b1f-29f385c6af3e.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/206080600-e4eeb0a5-ecee-4093-80ae-74841c46ac46.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/206081584-e6e455af-952c-4511-85bf-e05a689df147.png" width=100% height=100%>

‌ **Printing statistics**

    === multiple_modules ===

     Number of wires:                  5
     Number of wire bits:              5
     Number of public wires:           5
     Number of public wire bits:       5
     Number of memories:               0
     Number of memory bits:            0
     Number of processes:              0
     Number of cells:                  2
      sub_module1                     1
      sub_module2                     1

    === sub_module1 ===

     Number of wires:                  3
     Number of wire bits:              3
     Number of public wires:           3
     Number of public wire bits:       3
     Number of memories:               0
     Number of memory bits:            0
     Number of processes:              0
     Number of cells:                  1
      $_AND_                          1

    === sub_module2 ===

     Number of wires:                  3
     Number of wire bits:              3
     Number of public wires:           3
     Number of public wire bits:       3
     Number of memories:               0
     Number of memory bits:            0
     Number of processes:              0
     Number of cells:                  1
       $_OR_                           1

    === design hierarchy ===

     multiple_modules                  1
      sub_module1                     1
      sub_module2                     1

     Number of wires:                 11
     Number of wire bits:             11
     Number of public wires:          11
     Number of public wire bits:      11
     Number of memories:               0
     Number of memory bits:            0
     Number of processes:              0
     Number of cells:                  2
       $_AND_                          1
       $_OR_                           1
       
<img src="https://user-images.githubusercontent.com/118953938/206106057-0d1a10da-3db8-471d-8a9b-71cbcc1ada30.png" width=50% height=50%>

Preservation of hierarchy in Hierarchical synthesized netlist

<img src="https://user-images.githubusercontent.com/118953938/206108747-286e8099-8c28-45cd-bdc4-a447d1da3213.png" width=50% height=50%>

  /* Generated by Yosys 0.9+4081 (git sha1 862e84eb, gcc 7.5.0-3ubuntu1~18.04 -fPIC -Os) */

    module multiple_modules(a, b, c, y);
         input a;
          input b;
          input c;
          wire net1;
          output y;
          sub_module1 u1 (
               .a(a),
               .b(b),
                .y(net1)
          );
          sub_module2 u2 (
            .a(net1),
           .b(c),
           .y(y)
          );
        endmodule

        module sub_module1(a, b, y);
         input a;
          input b;
         output y;
         assign y = b | a;
        endmodule

**We can observe the modules are being preserved (no changes) and seperated one by one**<br />
**Quick recap on CMOS off all the gates:**<br />
<img src="https://user-images.githubusercontent.com/118953938/206195903-6a3383a8-f508-4267-9b1c-4140927190f7.png" width=80% height=80%>

### Lab 5 -Hier synthesis flat synthesis Part 2

<img src="https://user-images.githubusercontent.com/118953938/206127215-610d5999-61ba-442a-8059-44c3a8bae6f8.png" width=50% height=50%>

![image](https://user-images.githubusercontent.com/118953938/206123996-e1a4a6b0-f2a1-41c3-b911-75774550b0e1.png)

We can observe that on the multiple_modules_flat.v depict no hierarchical modules showed in the flat synthesis.

Show the design
![image](https://user-images.githubusercontent.com/118953938/206207412-61eaa796-97d1-48e0-adb5-139acc40ad92.png)
We cannot see the "U1" and "U2" because it was flatten

Open only one module

<img src="https://user-images.githubusercontent.com/118953938/206213054-febc2c66-2b9e-479a-ac07-5f15c240dcbf.png" width=50% height=50%>

synth -top sub_module1 and abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib then show

<img src="https://user-images.githubusercontent.com/118953938/206213552-5ea2f314-b345-41b5-bd37-f8aea19ee093.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/206214978-4d5337ea-8a93-4afa-b924-371e3cc003d9.png" width=50% height=50%>
From the lecture, why we nees a sub module level synth is because<br />
1) When we have multiple module of the same instance<br />
2) Divide and conquer (the design is to take a dispute on a huge input, break the input into minor pieces, decide the problem on each of the small pieces, and then merge the piecewise solutions into a global solution)

## Various Flop Coding Styles and optimization
### Theory Recap
### Why Flops and Flop coding styles Part 1

Flop coding

1) **Flip-flop**-flip-flop or latch is a circuit that has two stable states and can be used to store state information – a bistable multivibrator. The circuit can be made to change state by signals applied to one or more control inputs and will have one or two outputs. Exp:<br />

<img src="https://user-images.githubusercontent.com/118953938/206220131-9ca370a9-d75c-4e52-afa4-c07fcbf27f71.png" width=50% height=50%>

2) **Signal propagation delay**- Propagation delay is the time duration taken for a signal to reach its destination.<br />

<img src="https://user-images.githubusercontent.com/118953938/206221486-7dff5515-57fc-4f8e-b93b-d33fc381008f.png" width=50% height=50%>

4) **Glitch**-result when an input signal changes state, provided the signal takes two or more paths through a circuit and one path has a longer delay than the other.

### Why Flops and Flop coding styles Part 2

1) **Asynchronous**- asynchronous inputs on a flip-flop have control over the outputs (Q and not-Q) regardless of clock input status. These inputs are called the preset (PRE) and clear (CLR). The preset input drives the flip-flop to a set state while the clear input drives it to a reset state.<br />
Example: 4-bit asynchronous counter<br />
<img src="https://user-images.githubusercontent.com/118953938/206224057-c0824575-327d-42f5-a690-8ff17b7c11df.png" width=50% height=50%>

2) **Synchronous**- synchronous counter is a type of counter in which the clock signal is simultaneously provided to each flip-flop present in the counter circuit. More specifically, we can say that each flip-flop is triggered in synchronism with the clock input.
Example: 4-bit synchronous counter<br />
<img src="https://user-images.githubusercontent.com/118953938/206225805-32bee99c-e553-4301-a52d-b9e6e6c398b3.png" width=50% height=50%>

### Lab 5.1- Lab flop synthesis simulations Part 1
5.1.1) Asynchronous Reset

<img src="https://user-images.githubusercontent.com/118953938/206227275-8ea9a958-ffce-4ef6-aef6-2dd2b0707a52.png" width=100% height=100%>

![image](https://user-images.githubusercontent.com/118953938/206231314-a61d83c1-65b9-426a-b206-e344d651a905.png)

![image](https://user-images.githubusercontent.com/118953938/206232667-dfdce230-4d87-4f34-aea6-d02ea7410232.png)

![image](https://user-images.githubusercontent.com/118953938/206237085-2d7df92f-06f0-4e73-9666-d18efa98d723.png)

5.1.2) Synchronous Reset

![image](https://user-images.githubusercontent.com/118953938/206240447-70dbfc55-4b5e-45d9-80c2-a6644a97f594.png)

![image](https://user-images.githubusercontent.com/118953938/206240322-385d4541-22db-4d68-8224-6f99693f63a9.png)

### Lab 5.1- Lab flop synthesis simulations Part 2

5.1.3) Asynchronous 

**Commands**<br />

    1) yosys
    2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    3) read_verilog dff_asyncres.v
    4) synth -top dff_asyncres
    5) dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib 
    6) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    7) show

**Output**

<img src="https://user-images.githubusercontent.com/118953938/206243461-c023cafc-83bf-45b0-8f7c-4f3a46e98510.png" width=80% height=80%>

**Commands**<br />

    1) read_verilog dff_async_set.v
    2) synth -top dff_async_set
    3) dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    4) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    5) show

**Output**

![image](https://user-images.githubusercontent.com/118953938/206245194-1e54e233-722b-4fa4-b3db-5339e2251bc5.png)

5.1.4) Synchronous

**Commands**<br />

    1) read_verilog dff_syncres.v
    2) synth -top dff_syncres
    3) dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    4) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    5) show

**Output**

<img src="https://user-images.githubusercontent.com/118953938/206247803-d8403775-33c5-4491-9c91-169a20aeabca.png" width=80% height=80%>

### Lab 5.2- Interesting optimisations Part 1

**Multiplexer**- The multiplexer, shortened to “MUX” or “MPX”, is a combinational logic circuit designed to switch one of several input lines through to a single common output

5.2.1) mult_2.v

**Commands**<br />

    1) yosys
    2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    3) read_verilog mult_2.v
    4) synth -top mul2
    5) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    6) show

**Output**

![image](https://user-images.githubusercontent.com/118953938/206253674-f0319c90-9665-4e36-a62a-c45e36de7f7e.png)

### Lab 6- Interesting optimisations Part 2

5.2.2) mult_8.v

**Commands**<br />

    1) yosys
    2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    3) read_verilog mult_8.v
    4) synth -top mult8
    5) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
    6) show

**Output**

![image](https://user-images.githubusercontent.com/118953938/206256679-97b653f8-26b0-4d4b-8bde-2963a52edce9.png)

# :book: Day 3 - Combinational and sequential optimizations

### :mag_right: Combinational Logic Optimization
is a process of finding an equivalent representation of the specified logic circuit under one or more specified constraints. This process is a part of a logic synthesis applied in digital electronics and integrated circuit design.<br />

<img src="https://user-images.githubusercontent.com/118953938/206629033-0516bc19-de72-4f97-9cc2-2d5cefc2d643.png" width=40% height=40%>

How to optimize the design?<br />
1) Squeezing the logics (area and power)<br />
2) Constant propagation <br />
    * It can be defined as the process of replacing the constant value of variables in the expression. In simpler words, we can say that if  some value is assigned a known constant, than we can simply replace the that value by constant. Constants assigned to a variable can be propagated through the flow graph and can be replaced when the variable is used. 
3) Boolean logic optimization <br />
    * In terms of Boolean algebra, the optimization of a complex boolean expression is a process of finding a simpler one, which would upon evaluation ultimately produce the same results as the original one.Exp:<br />
    
    !<img src="https://user-images.githubusercontent.com/118953938/206629248-7d2f5b3f-981a-4324-bb92-ba4c7681fd64.png" width=60% height=60%>

### :mag_right: Sequential Logic Optimization
optimization on a type of logic circuit whose output depends on the present value of its input signals and on the sequence of past inputs, the input history.<br />

<img src="https://user-images.githubusercontent.com/118953938/206628188-21135ec8-0828-4f87-b360-c46d7cd094a0.png" width=40% height=40%>

1) Basic
    * Sequential Constant propagation 
        * Constant propagation is the use of control-flow and data-flow information to determine that a variable must have a particular constant value at a specific point in the program.
2) Advanced
    * State optimization
         
         :heavy_check_mark: Retiming
         * Retiming is a technique for optimizing sequential circuits. It repositions the registers in a circuit leaving the combinational portion of circuitry untouched. The central objective of retiming is to find a circuit with the minimum number of registers for a specified clock period.
         * It cann help to reduce the delay and improve frequency efficiency of the sequential design.
          
             <img src="https://user-images.githubusercontent.com/118953938/206641971-ffa7441b-9c4f-4b91-88c9-216a44b3ce1b.png" width=20% height=10%>
         
         :heavy_check_mark: Sequential Logic cloning (physical aware)
           
         * In Physical aware synthesis, it will provide floor plan DEF as one of the input to the synthesis tool. Floor plan DEF will contains the physical information like placement of macros, placement of input & output ports, die area & placement blockages. Also, RC co-efficient file can be given as input to synthesis tool for better calculation of wire resistance & capacitance compared to wire load model method.

                Advantages of Physical aware synthesis:

                     * Gives better PPA (power, performance, area)
                     * Will give better timing correlation between synthesis and PnR results
                     * Improvement in Power
                     * PnR run time also reduces because of lesser violations


        * Sequential logic cloning will help to reduce the large routing delay from the design

### :test_tube:	Lab 6- Combinational Logic Optimisations Part 1/2

**:mag_right: Multiplexer**- A multiplexer is a circuit used to select and route any one of the several input signals to a single output. A simple example of an non-electronic circuit of a multiplexer is a single pole multi-position switch. Multi-position switches are widely used in many electronics circuits. <br />
* Multiplexers are part of computer systems to select data from a specific source, be it a memory chip or a hardware peripheral. A computer uses multiplexers to control the data and address buses, allowing the processor to select data from multiple data sources.  <br />

![image](https://user-images.githubusercontent.com/118953938/206646645-f7f541c2-8d71-48c0-a4f5-ea90d6fbad17.png)

Files that used in the lab:<br />
<img src="https://user-images.githubusercontent.com/118953938/206646837-2f43f589-8ad4-4fc9-b79a-deb8be479831.png" width=70% height=70%>

Expectation from: <br />
**opt_check**<br />
y=a! y=o<br />
y=a!.o+ab<br />
y= a.b (and gate)<br />

**opt_check2**<br />
y=a!b+a<br />
y=a+b<br />

**opt_check3**<br />
y=a!o+a(c!o+cb)<br />
y=o+abc<br />
y=abc<br />

**opt_check4**<br />
y=a!c!+a(b!c+b(ac))<br />
y=a!c!+ab!c+abc<br />
y=a!c!+ac<br />

**Commands**<br />
        
        opt_check.v
        1) yosys
        2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog opt_check.v (opt_check2.v/opt_check3.v/opt_check4.v)
        4) synth -top opt_check (opt_check2/opt_check3/opt_check4)
        5) opt_clean -purge
        6) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        7) show
        multiple_module_opt.v
        1) yosys
        2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog multiple_module_opt.v
        4) synth -top multiple_module_opt
        5) opt_clean -purge
        6) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        7) flatten
        8) show
        
**Outputs**

**opt_check.v**

6.1) opt_check.v

<img src="https://user-images.githubusercontent.com/118953938/206650258-4d8c5816-7466-4b6f-a78b-fbc72bce0e84.png" width=70% height=70%>

6.2) opt_check2.v

<img src="https://user-images.githubusercontent.com/118953938/206655855-bcff2bfb-8129-4c15-be49-db75f6cc6621.png" width=70% height=70%>

6.3) opt_check3.v

<img src="https://user-images.githubusercontent.com/118953938/206656766-ef63d951-a494-489e-babc-215dd312f5c7.png" width=70% height=70%>

6.4) opt_check4.v

<img src="https://user-images.githubusercontent.com/118953938/206658501-17ef67e6-576e-4ab1-ac3a-b151593986fd.png" width=70% height=70%>

**multiple_module_opt.v**

6.5) multiple_module_opt.v

<img src="https://user-images.githubusercontent.com/118953938/206825112-61f0e771-44d9-4ec3-b25e-7a853d53a628.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/206825248-ca41eed4-0eed-42fb-9df4-6fc1cfea263b.png" width=70% height=70%>

6.5) multiple_module_opt.v

<img src="https://user-images.githubusercontent.com/118953938/206826258-20e59c46-62bf-49a6-8422-02b42c55b6cc.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/206825783-832a4072-2f84-4106-bf4a-e2759e4dc865.png" width=70% height=70%>


### :test_tube:	Lab 7- Sequential Logic Optimisations Part 1/2/3

:grey_exclamation: Files that used in the lab:<br />

![image](https://user-images.githubusercontent.com/118953938/206661166-35ce7f5d-b7a2-406a-8b06-895679f9f685.png)

Open files (gvim dff_const1.v -o dff_const2.v)<br />

![image](https://user-images.githubusercontent.com/118953938/206829396-01d1fea2-fa27-4fe0-93e9-ee1761f545e3.png)

![image](https://user-images.githubusercontent.com/118953938/206829428-ba0d5072-037d-4a7d-b9c4-416199b342f5.png)

**Commands**<br />

        1)iverilog dff_const1(2).v tb_dff_const1(2).v       
        2)./a.out
        3)gtkwave tb_dff_const1(2).vcd
        
        1) yosys
        2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog dff_const1(2,3,4).v
        4) synth -top dff_const1(2,3,4)
        5) dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        6) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        7) show
 
 **Outputs**
 
 **7.1) dff_const1.v**
 
 <img src="https://user-images.githubusercontent.com/118953938/206716305-0503e144-1ae3-4108-894c-a5fabed0a83f.png" width=70% height=70%><br />
:grey_exclamation: We can observe that the 'q' will be high when the positive clock edge <br />

 <img src="https://user-images.githubusercontent.com/118953938/206722429-a7380f65-0879-4285-ada8-92b585924bff.png" width=70% height=70%><br />


 **7.2) dff_const2.v**
 
 <img src="https://user-images.githubusercontent.com/118953938/206718806-5d643402-3291-4f1c-aa25-9f0ba6ffd12b.png" width=70% height=70%><br />
 
<img src="https://user-images.githubusercontent.com/118953938/206724438-2a6d0e25-efae-4472-ab49-d5036cafa944.png" width=70% height=70%><br />

**7.3) dff_const3.v**

<img src="https://user-images.githubusercontent.com/118953938/206731500-2616f009-641e-47fc-9477-26501739bcc7.png" width=70% height=70%><br />

 <img src="https://user-images.githubusercontent.com/118953938/206734381-f472352d-0780-4c6e-97e6-7d166bf387e5.png" width=70% height=70%><br />
       

### :mag_right: Seq optimisation unused outputs 

**Counter**-counter is a device which stores (and sometimes displays) the number of times a particular event or process has occurred, often in relationship to a clock. The most common type is a sequential digital logic circuit with an input line called the clock and multiple output lines.

### :test_tube:	Lab- Seq optimisation unused outputs Part 1/2

**Commands**<br />

        1) yosys
        2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog counter_opt.v
        4) synth -top counter_opt
        5) dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        6) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        7) show

**Outputs**

**counter_opt.v**

<img src="https://user-images.githubusercontent.com/118953938/206827397-b2bdcba6-d41c-4422-bcaa-e2bea0dc2fd6.png" width=70% height=70%><br />

<img src="https://user-images.githubusercontent.com/118953938/206827736-73ce0d9a-e73d-4b89-9c2b-a170454e421d.png" width=30% height=30%><br />

<img src="https://user-images.githubusercontent.com/118953938/206827717-2b585628-17e5-4019-a3b5-bae205012510.png" width=100% height=100%><br />

**counter_opt2.v**

<img src="https://user-images.githubusercontent.com/118953938/206828145-1f000601-c665-4779-b047-ccd6cae48792.png" width=70% height=70%><br />

<img src="https://user-images.githubusercontent.com/118953938/206828220-c98e737b-e9e3-42d9-9182-052a43be7e67.png" width=30% height=30%><br />

![image](https://user-images.githubusercontent.com/118953938/206829257-34beedea-58a5-493b-987c-42449a48a15b.png)


