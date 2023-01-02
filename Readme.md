# :book: My Respository

## Contents

[DAY 0 System/Tool Setup Check. GitHub ID creation](https://github.com/azrulhakimwahab/sd-training/blob/main/Report.md#day-0)

[DAY 1 Introduction to Verilog RTL design and Synthesis](https://github.com/azrulhakimwahab/sd-training/blob/main/Report.md#day-1)

[DAY 2 Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles](https://github.com/azrulhakimwahab/sd-training/blob/main/Readme.md#day-2--timing-libsqtmsetms-hierarchical-vs-flat-synthesis-and-efficient-flop-coding-styles)

[DAY 3 Combinational and sequential optimizations](https://github.com/azrulhakimwahab/sd-training/blob/main/Readme.md#book-day-3---combinational-and-sequential-optimizations)

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

# :book: Day 4 - GLS, Synthesis-Simulation mismatch and Blocking/Non-blocking statements

### :mag_right: Gate Level Simulation (GLS)
The term "gate level" refers to the netlist view of a circuit, usually produced by logic synthesis. 
* As a process of running the testbench with netlist under Design Under Test (DUT)
* A 'netlist' is a description of the connectivity of an electronic circuit. In its simplest form, a netlist consists of a list of the electronic components in a circuit and a list of the nodes they are connected to. 

Benefits:
* Can verify the logical correctness of the design after synthesis
* Ensuring the timing of the design follows the requirements

### :mag_right: Gate Level Simulation (GLS) using I Verilog

<img src="https://user-images.githubusercontent.com/118953938/207057743-acb93c06-6a44-46b9-8ddf-75626ab19798.png" width=70% height=70%><br />

Example:

assign y=(a&b)|c

<img src="https://user-images.githubusercontent.com/118953938/207067196-b6ac65cc-6e70-458f-b9b5-53f49deeb774.png" width=50% height=50%><br />

### :mag_right: Synthesis Simulation Mismatch

Why is it happening?

**1) Missing sensitivity list**

<img src="https://user-images.githubusercontent.com/118953938/207072609-1f0c90a8-f48c-4118-b5a8-b0aa6e767882.png" width=70% height=70%><br />

**2) Blocking vs Non-Blocking Assignments**

Blocking<br />
* Executes the statements in order it is written
* The first statement is evaluated before the second statement

Non-Blocking<br />
* Executes all the RHS when the always block is entered and assigns to LHS
* Parallel evaluation

Caveats with Blocking Statements

<img src="https://user-images.githubusercontent.com/118953938/207080124-74d5a7d7-5b5f-433a-bd28-1e46de5fec33.png" width=70% height=70%><br />

* Use nonblocking for writing sequential circuits 
* Need to use blocking carefully 

Synth Sim Mismatch

<img src="https://user-images.githubusercontent.com/118953938/207241913-e7436966-b4ad-4f46-866f-30492435b119.png" width=70% height=70%><br />

#Note that the figures were taken from the lectures and edited according to understanding

**3) Non Standard Verilog Coding**


### :test_tube:	Lab 8- Labs on GLS and Synthesis-Simulation Mismatch Part 1/2

8.1) ternary_operator_mux.v

<img src="https://user-images.githubusercontent.com/118953938/207226907-6b25ec1b-2b1c-4e2b-a72a-55489eeab931.png" width=70% height=70%><img src="https://user-images.githubusercontent.com/118953938/207227078-f8240d34-8654-4f6c-a87d-d448a4953fdd.png" width=50% height=50%><br />
<img src="https://user-images.githubusercontent.com/118953938/207225419-7f854ecb-c2ad-40da-8bff-8b1bd711b966.png" width=70% height=70%>

**Commands**<br />

        1) yosys
        2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog ternary_operator_mux.v
        4) synth -top ternary_operator_mux
        5) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        6) write_verilog -noattr ternary_operator_mux_net.v
        7) show
        
        Ternary_operator_mux wave form
        1) iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
        2) ./a.out
        3) gtkwave tb_ternary_operator_mux.vcd

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/207225951-c12dc257-ed22-423e-9258-954f39879dd0.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/207226666-96619c81-77c7-4584-8429-7ccd396d8604.png" width=70% height=70%>

8.2) bad_mux.v

<img src="https://user-images.githubusercontent.com/118953938/207227690-e7881ae1-590e-49a9-ab34-b1250efab6e9.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/207234532-95d2d27f-29b3-444f-9007-47ccab7143f2.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/207235253-6b95f4e7-64a2-4c18-bdc5-3b3cc27617ce.png" width=70% height=70%>

**Commands**<br />

        1) yosys
        2) read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog bad_mux.v
        4) synth -top bad_mux
        5) abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        6) write_verilog -noattr bad_mux_net.v
        7) show
        
        Ternary_operator_mux wave form
        1) iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
        2) ./a.out
        3) gtkwave tb_bad_mux.vcd

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/207235731-4614f121-cb5c-468b-bac9-7866ae5d24c2.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/207236874-b1470cff-bd96-4faf-b6f4-c2277a9d540d.png" width=70% height=70%>

### :test_tube:	Lab 9- Labs on Synth sim mismatch blocking statement Part 1/2

9.1) blocking_caveat.v

**Commands**<br />

        1) gvim blocking_caveat.v
        2) riverilog blocking_caveat.v tb_blocking_caveat.v
        3) ./a.out
        4) gtkwave tb_blocking_caveat.vcd
               
        Synthesize
        1) yosys
        2) read_liberty -lib ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        3) read_verilog blocking_caveat.v
        4) synth -top blocking_caveat
        5) abc -liberty ../my_lib/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
        6) write_verilog -noattr blocking_caveat_net.v
        7) show
        
        Waveform
        1) iverilog ../my_lib/verilog_model/primitives.v ../my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
        2) ./a.out
        3) gtkwave tb_blocking_caveat.vcd
        
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/207238130-1382d6bf-986b-41f5-be2e-9425db091a8f.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/207239249-ed7b9c2c-b87e-4d82-b1c9-ad9f3dbb6c18.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/207239567-088bd850-2a8e-4ab6-8945-6c6648d2ae94.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/207240419-373ed5c4-45b6-4ccb-89c8-3fe92c003b98.png" width=70% height=70%>


# :book: Day 5 - Design For Testability

### :mag_right: DFT definition

* Design For Testability (or Design for Test, or DFT) refers to design techniques that make products easier to test.
* The new features simplify the development and application of manufacturing tests to the designed hardware. 
* Manufacturing tests are performed to ensure that the product hardware is free of manufacturing defects that could interfere with the product's proper operation.

Tests are utilized at numerous stages of the hardware manufacturing process and, in some cases, for hardware maintenance in the customer's environment. Test programmes are typically used to drive the tests, which are then executed on automatic test equipment (ATE) or, in the case of system maintenance, within the constructed system itself. Tests may be able to log diagnostic information regarding the nature of the encountered test fails in addition to discovering and indicating the presence of faults (i.e., the test fails). The diagnostic data can be used to pinpoint the source of the failure.

| Advantages  | Disadvantages |
| ------------- | ------------- |
| Reduces tester complexity  | DFT increase power, area, timing   |
| Reduces tester time | DFT adds complication to the design flow. |
| Reduces the possibility of losing money due to defective products. | Design time increases  |

#### :black_nib: Example of DFT
<details><summary> Explainations </summary>
<p>
        
1) **MBIST**: is the industry-standard method of testing embedded memories. MBIST works by performing sequences of reads and writes to the memory according to a test algorithm. Many industry-standard test algorithms exist.

    ![image](https://user-images.githubusercontent.com/118953938/207633181-1b6ecec9-6a9d-40a6-a7de-60370ee604b0.png)<br>
 visit [here](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.design-reuse.com%2Farticles%2F45915%2Fmemory-testing-self-repair-mechanism.html&psig=AOvVaw0z6iyRGnzeG6m-O2mSmz19&ust=1671116083088000&source=images&cd=vfe&ved=0CBEQjhxqFwoTCMj0_pqy-fsCFQAAAAAdAAAAABAP) for more info

2) **Scan chains**: Scan chains are the elements in scan-based designs that are used to shift-in and shift-out test data

    <img src="https://user-images.githubusercontent.com/118953938/207635196-ed672c27-3e5b-44eb-9ff9-84eb3a1a955e.png" width=50% height=50%>
   
3) **Generate test patterns** for combo logics

* DFT benefit: can reduce the high cost in time and effort required to generate test vector sequences for VLSI circuits.
</p>
</details>

#### :black_nib: Levels of testing

<img src="https://user-images.githubusercontent.com/118953938/207757611-1284d021-8955-4e68-b358-97b91d6c7e69.png" width=50% height=50%>

#### :black_nib: Terminologies

1) **Controlability**- Controllability gives us a measure of how easy or difficult it is to force the logic level in a node to either 1 or 0. If we consider the simple circuit shown in figure 1, it is easy to verify that only 2 out of 8 possible input combinations enable us to force a 1 in node Y. [Source](https://www.google.com/url?sa=i&url=http%3A%2F%2Fvlsi-soc.blogspot.com%2F2013%2F04%2Ftwo-pillars-of-dft-controllability.html&psig=AOvVaw3RfyRP2JZ6lGFmfInSYEa0&ust=1671159908845000&source=images&cd=vfe&ved=0CBEQjhxqFwoTCLiY_vjR-vsCFQAAAAAdAAAAABAD)

<img src="https://user-images.githubusercontent.com/118953938/207762936-fc6d91fd-a635-47db-895f-dd1f50639fa1.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/207805782-c0d6a061-dbcf-42b9-989f-fa3522bd1c53.png" width=50% height=50%>

2) **Observability**- The observability of a node is defined precisely to give a measure of how easy or difficult it is to propagate the logic level in a node to a directly observable output.<br>

<img src="https://user-images.githubusercontent.com/118953938/207805891-ef07369c-81ce-4541-b45d-997fb151da01.png" width=50% height=50%>

4) **Fault**- It is a physical damage/defect compared to the good system, which may or may not cause system failure.<br>
5) **Error**-  An error is caused by a fault because of which system went to erroneous state.<br>
6) **Failure**-  failure is when the system is not providing the expected service. A fault causes an error which leads to the system failure.<br>
7) **Fault Coverage**- Percentage of the total number of logical faults that can be tested using a given test set T.<br>
8) **Defect Level**- Refers to the fraction of shipped parts that are defective. Or, the proportion of the faulty chip in which fault isn’t detected and has been classified as good.<br>

#### :black_nib: DFT techniques

Two main categories of DFT Techniques

<img src="https://user-images.githubusercontent.com/118953938/207784240-88112dc9-f7ee-43a1-8aa2-c038c029dde0.png" width=50% height=50%>

#### :black_nib: SCAN CHAIN TECHNIQUE

1) Scan chains are scan-based design features that are used to shift-in and shift-out test data.
2) A scan chain is made up of a series of flops connected back to back in a chain, with the output of one flop connected to the output of the next.
3) The first flop's input is connected to the chip's input pin (called scan-in), from which scan data is fed. The output of the last flop is attached to the chip's output pin (called scan-out), which is used to extract the shifted data. 

         • Lots and lots of flops/latches in a high-end chip
             * 200,000 latches on 2nd gen Itanium (static + dynamic)
          • Scan chains offer two benefits for these latches and flops
              – Observability: you can stop the chip and read out all their states
              – Controllability: you can stop the chip and set all of their states
         • Critical for debugging circuit issues too
              – They are your easiest “probe” points in the circuit
              – Can trace back errors to see where they first appear
         • Great with simulator or when a part fails in some condition
             – Even more useful with a flexible clock generator
          • Can stress certain clock cycles, and look at which bits fail

<img src="https://user-images.githubusercontent.com/118953938/207803976-6e80c450-7fc7-4eed-8aed-ca1e3bcdaf9b.png" width=80% height=80%>

There are three sorts of scan flip-flop configurations: 

**1) Multiplexed**<br>

* Scan testing is done in order to detect any manufacturing fault in the combinatorial logic block. In order to do so, the ATPG tool try to excite each and every node within the combinatorial logic block by applying input vectors at the flops of the scan chain. All the flops are connected in form of a chain, which effectively acts as a shift register. The first flop of the scan chain is connected to the scan-in port and the last flop is connected to the scan-out port.

 <p align="center"><img src="https://user-images.githubusercontent.com/118953938/207814382-c53ac8ee-5d03-4119-83f0-0b3dc1a8d47f.png" width=70% height=70%></p>
<p align="center"><img src="https://user-images.githubusercontent.com/118953938/207812996-8c37101d-bd32-4df1-a04c-18aec8fe2c76.png" width=80% height=80%></p>

**2) Level-sensitive scan design (lssd)**

* IT uses separate system and scan clocks to distinguish between normal and test mode. Latches are used in pairs, each has a normal data input, data output and clock for system operation. For test operation, the two latches form a master/slave pair with one scan input, one scan output and non-overlapping scan clocks A and B which are held low during system operation but cause the scan data to be latched when pulsed high during scan. [Source](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.researchgate.net%2Ffigure%2FModified-Clocked-LSSD-Scan-FF-b-Additional-front-end-logic_fig1_280173334&psig=AOvVaw13SU6GfK5vMLtBUpVfNhXe&ust=1671178751339000&source=images&cd=vfe&ved=0CBEQjhxqFwoTCKCT3JGY-_sCFQAAAAAdAAAAABAP)

<p align="center"><img src="https://user-images.githubusercontent.com/118953938/207808393-9cccd9f1-33e8-45f1-89b1-5987fabb66b4.png" width=30% height=30%></p>

### :mag_right: Automatic test equipment

Automatic test equipment (ATE) is any apparatus that uses automation to swiftly make measurements and assess test findings on a device known as the device under test (DUT), equipment under test (EUT), or unit under test (UUT). An ATE can be as simple as a computer-controlled digital multimeter or as complex as a system with dozens of complex test instruments (real or simulated electronic test equipment) capable of automatically testing and diagnosing faults in sophisticated electronic packaged parts or on wafer testing, such as system on chips and integrated circuits.

1.Scan-In Phase
2.Parallel Measure 
3.Parallel Capture 
4.First Scan-Out Phase
5.Scan-Out Phase

# :book: Day 6 - Introduction to Logic Synthesis

### :mag_right: Definition and details about Logic Synthesis

**It is the process of transforming RTL to gate-level netlist. Synthesis process can be optimized for Speed(timing)/Area/Testability (DFT)/Power(DFP)/Run time. Inputs : RTL, Technology libraries, Constraints (Environment, clocks, IO delays etc.). Outputs : Netlist , SDC, Reports etc.**

:gear: Tools used in the synthesis

        1. iVerilog: for verilog compilation and simulation
        2. gtkwave: for viewing the simulation output
        3. Synopsys design compiler: for logic synthesis
        4. skywater 130nm library
        5. Pre-requisites

:gear: Digital electronics applied

        1. Boolean algebra
            - Boolean algebra is a branch of mathematics that deals with operations on logical values with binary variables. 
        2. Verilog Hardware Description Level (HDL) coding
            - Used to model electronic systems
        3. Idea of basic synthesis
            - Synthesis occurs between the RTL Design & Verification phase and the Physical Design phase
        
:gear: The aim of this course

        1. Understand various steps involved in Digital Logic Synthesis
        2. Understand and write Synopsis Design Constrants (SDC) for the given module
        3. Perform synthesis and write out netlist using design compiler
        4. Generate and analyze the synthesis reports/STA reports
        
### :mag_right: Basics of digital logic design and synthesis

:triangular_flag_on_post: **Digital logic** <br>
-*Digital logic is the **manipulation of binary values** through printed circuit board technology that uses circuits and logic gates to construct the implementation of computer operations.*

A **hardware description language (HDL)** is a specialized computer language used to describe the structure and behavior of electronics.

Example of HDLs

| Name  | Description |
| ------------- | ------------- |
| VHDL-AMS (VHDL with Analog/Mixed-Signal extension) | An IEEE standard extension (IEEE Std 1076.1) of VHDL for analog and mixed-signal simulation  |
| Verilog-AMS (Verilog for Analog and Mixed-Signal) | An Accellera standard extension of IEEE Std 1364 Verilog for analog and mixed-signal simulation  |
|SpectreHDL  | A proprietary analog HDL from Cadence Design Systems for its Spectre circuit simulator  |
| HDL-A  | A proprietary analog HDL  |

**Verilog HDL and Verilog**<br>

<img src="https://user-images.githubusercontent.com/118953938/208822921-82d7aed0-6847-4ba2-b966-b738cfb68674.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/208825551-9f5460ab-57a2-4ef1-9467-19d7a4546f5a.png" width=80% height=80%><br>
[Figure source](https://digilent.com/blog/verilog-vs-vhdl/#:~:text=VHDL%20was%20written%20as%20a,is%20often%20easier%20to%20learn.)

:red_circle: Can you mix VHDL and Verilog? :red_circle: <br>
*Yes, you can mix Verilog and VHDL in Vivado, and it is also supported in the Xilinx simulation environment. If you use another simulator like Modelsim, you may need a different license class to support mixed language simulation.*

:triangular_flag_on_post: **Logic Synthesis** <br>
*A process by which an abstract specification of desired circuit behavior, typically at **register transfer level (RTL), is turned into a design implementation in terms of logic gates, typically by a computer program called a synthesis tool**.*

3 components in synthesis are RTL, standard cell library (.lib) and netlist

<img src="https://user-images.githubusercontent.com/118953938/208852110-348047f3-0a82-4fc2-9a81-c4df57426b2e.png" width=50% height=50%>

1) Register Transfer Level (RTL)

* A smaller subset of the full range of HDL code
* The term Register Transfer refers to the **availability of hardware logic circuits that can perform a given micro-operation and transfer the result of the operation to the same or another register.** (Describes how data is transformed as it is passed from register to register)
* <img src="https://user-images.githubusercontent.com/118953938/208852007-71f2e89c-7a3e-4f27-98a6-93ae3960f261.png" width=30% height=30%>

2) standard cell library (.lib)

* A collection of low-level electronic logic functions.
* In general, a standard cell library contains the following types of cell:

        - All basic and universal gates (like AND, OR, NOT, NAND, NOR, XOR etc)
        - Complex gates (like MUX, HA, FA, Comparators, AOI, OAI etc)
        - Clock tree cells (like Clock buffers, clock inverters, ICG cells etc)
        - Flip flops and latches.
        - Delay cells.
* Have different flavours of gates
    * Why we needed that?
        * Combinational delay in logic path determines the maximum speed of operation of digital logic circuit
        
        <img src="https://user-images.githubusercontent.com/118953938/208852504-06bdb38b-4a07-429d-8dc9-6a091ac346ed.png" width=60% height=60%>
        
* Why we need slow cells?

        1) to ensure that there is no 'hold' issue at DFF_B
        2) Therefore we need a 'fast cell' to meet required performance (setup)
        3) the collection forms the .lib
     
    <img src="https://user-images.githubusercontent.com/118953938/208853858-6e27e2ae-3fca-4797-8d8f-26f7f3eea8df.png" width=40% height=40%>

* Faster Cells vs Slower Cells

| Faster Cells | Slower Cells |
| ------------- | ------------- |
| wider transistor -> low delay -> more area and power  | narrow transistor -> more delay -> less area and power  |

* Cell Selection
    * It is essential to guide the synthesiser in choosing the cell flavour that is best for using in a logic circuit.
    * More use of faster cells giving the Power and Area in a bad condition
    * More use of slower cells will result in sluggish circuit where it may not meet the performance needed

![image](https://user-images.githubusercontent.com/118953938/208860251-133dd6fb-2226-46db-83b5-72508613ed7f.png)

* What are the requirements achieve in logic synthesis?

        1) Logically correct
        2) Electrically correct
        3) Timing met

*  How do we know it i sthe correct recipie?
    * By set up constraints- Constraints are the guide to the synthesizer to pick the correct library cells which is most appropriate for the design

### :mag_right: Introduction to design compiler

**Design Compiler** <br>
A Synthesis tool targeted for ASIC design flow from Synopsys

**Benefits** [source](https://www.synopsys.com/implementation-and-signoff/rtl-synthesis-test/dc-ultra.html#:~:text=Design%20Compiler%C2%AE%20RTL%20synthesis,in%20faster%20time%20to%20results.)

        1. Concurrent optimization of timing, area, power and test
        2. Results correlate within 10% of physical implementation
        3. Removes timing bottlenecks by creating fast critical paths
        4. Gate-to-gate optimization for smaller area on new or legacy designs while maintaining timing Quality of Results (QoR)
        5. Cross-probing between RTL, schematic, and timing reports for fast debug
        6. Offers more flexibility for users to control optimization on specific areas of designs
        7. Enables higher efficiency with integrated static timing analysis, test synthesis and power synthesis
        8. Support for multi voltage and multi supply
        9. 2X faster runtime on quad-core compute servers

**Common Terminologies** associated with DC 

        1. SDC (Synopsys Design Constraints)- design constraints which are supplied to DC to enable appropriate optimization suitable for achieving the best implementation
        2. Industry standard- used across Electronic Design Automation (EDA) implementation tools
        3. .lib- Design Library which contains the standard cells
        4. DB- (same as .lib but in different format) understand libraries in .db format (convert .lib in db and then supply to DC)
        6. DDC- synopsys proprietary format for storing the design information. can write out and read in DDC
        7. Design- RTL files which has the behavioral model of the design
        
**Synopsys Design Constraints (SDC)**

* Used to specify the design intent in terms of timing, power and area constraints
* Supported by Electronic Design Automation (EDA) tools across semiconductor industry
* Using the Tool Command Language (TCL)

![image](https://user-images.githubusercontent.com/118953938/208903231-deced78d-b763-4c17-bbb7-2ce3ebbc8e18.png)

<img src="https://user-images.githubusercontent.com/118953938/208903310-66cf441e-94e2-494d-99d1-c3bce629077b.png" width=40% height=40%>

### :mag_right: Quick recap: TCL

![image](https://user-images.githubusercontent.com/118953938/208954251-3d2db13c-5b47-4562-ac92-3b516ac7540d.png)

### :test_tube:	Lab 1- Invoking dc basic setup

1.1) Invoking

**Commands**

        1) cd /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm--->open directory
        2) mkdir VLSI---> make a new directory 
        3) git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git --->file cloning (copy/paste)
        4) cd sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib
        
**Output**

<img src="https://user-images.githubusercontent.com/118953938/208927319-79aabf37-418c-488c-af0a-4ec474eefe5d.png" width=60% height=60%>

1.2) Reading '.lib'

**Commands**

        1) gvim sky130_fd_sc_hd__tt_025C_1v80.lib
        2) :syn off ---> to shut the syntax (red colour) 
        3) git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git --->file cloning (copy/paste)
        4) cd sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib
        
        Searching multiple types of cell
        1) /cell (.*and(or)(inv)
      
**Output**

Info captured <br>
<img src="https://user-images.githubusercontent.com/118953938/208929233-d31e9515-4af0-49db-92b6-d6a1d23db3a3.png" width=60% height=60%>

Searching multiple types of cell <br>
![image](https://user-images.githubusercontent.com/118953938/208930288-9ed8af1f-54d2-4a52-b4ae-cc2089a85e54.png)

1.3) Invoking DC

**Commands**

        1) /p/hdk/pu_tu/prd/sams/mig76_wlw/setup/enter_p31 -cfg ip76p31r08hp7rev03 -ov ./
        2) csh
        3) dc_shell
        
**Output**

<img src="https://user-images.githubusercontent.com/118953938/208932669-e141eb07-57f2-41f6-a6f1-f6882c097840.png" width=60% height=60%>

1.4) Read std cell/tech .lib

**Commands**

        1) echo $target_library
        2) echo $link_library
        Exit and ready to use gvim
        3) gvim DC_WORKSHOP/verilog_files/lab1_flop_with_en.v

**Output**

<img src="https://user-images.githubusercontent.com/118953938/208933423-b5a2efce-bc2c-45d8-a2c5-18cf0e114def.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/208934994-c5e87d66-e9b8-4d67-9fd0-4ff7026e71e6.png" width=60% height=60%>

1.5) Read and write verilog

**Commands**

        1) read_verilog DC_WORKSHOP/verilog_files/lab1_flop_with_en.v
        2) write -f verilog -out lab1_net.v
        3) read_db DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
        4) write -f verilog -out lab1_net.v
        5) sh gvim lab1_net.v &

**Output**

![image](https://user-images.githubusercontent.com/118953938/208937241-3a83b6a7-c600-4d0a-9093-7e4c8e62b015.png)

1.6) loading the sky130 library

**Commands**

        1) read_db DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
        2) write -f verilog -out lab1_net.v
        3) sh gvim lab1_net.v & ---> the format is still in gtech
        look at target_library and link_library  
        
        To set target library
        4) set target_library /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db/nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
        5) set link_library {* /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db}*/nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
        6)link
        7) compile
        8) write -f verilog -out lab1_net_with_sky130.v
        9) sh gvim lab1_net_with_sky130.v &

**Output**

<img src="https://user-images.githubusercontent.com/118953938/208939357-1aa37fe5-e880-4fc4-aa96-96a056a37d83.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/208939647-cf64ecaf-1f84-424e-968f-c5fd89955fbb.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/208940378-3f622a7a-ba9a-4738-b0f7-326084266563.png" width=60% height=60%>

### :test_tube:	Lab 2- Intro to ddc gui with design_vision

**Commands**

        1) csh
        2) Design vision
        3) start_gui
        4) read_ddc lab1.ddc

**Output**

<img src="https://user-images.githubusercontent.com/118953938/208941454-9927252b-46c4-417d-b6c1-856cb5ab09ce.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/208941855-010a185c-9b80-4e94-a5da-211f7cea9f11.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/208942090-7b5f6f35-3ca0-41ea-ac8a-e287f343df7b.png" width=60% height=60%>

### :test_tube:	Lab 3- dc synopsys dc setup

**Commands**

        1) csh
        2) dc_shell
        3) echo $target_library
        4) echo $link_library
        5) set target_library DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
        6) set link_library {* $target_library}
        7) echo $target_library
        8) output: DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
        9) echo $link_library

**Output**

<img src="https://user-images.githubusercontent.com/118953938/208944525-3b823af4-d841-4c34-9d67-5a606a99d785.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/208946213-c06a9f25-2620-4ebc-ac81-9b5cc049c2da.png" width=60% height=60%>

To correct the issue

**Commands**

        1) quit dc_shell
        2) cd /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop
        3) gvim .synopsys_dc.setup
            -in gvim, paste this and save
                set target_library DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db
                set link_library {* $target_library}
        
        invoke DC shell
        4) csh
        5) dc_shell
        6) echo $target_library
        7) echo $link_library

**Output**

<img src="https://user-images.githubusercontent.com/118953938/208947484-f7acba91-4de6-4d25-a60e-16a309448c6d.png" width=60% height=60%>

**Target library and link library now is auto set**

### :test_tube:	Lab 4- TCL

4.1) For loop

            for {set i 0} {$i < 12} {incr i} {                                                             
                      echo $i
            }

<img src="https://user-images.githubusercontent.com/118953938/208956840-8b29f850-d8ec-4b9c-82ca-d9a656903e1f.png" width=40% height=40%>

4.2) while loop 

        while {$i < 11} {  
            echo $i;  
            incr i;                                                                                                              
            }

<img src="https://user-images.githubusercontent.com/118953938/208959355-91428d61-0ea6-47f8-b2e0-0c79e5e4a751.png" width=40% height=40%>

         while {$i < 11} {
            echo $i;
            set i [expr $i + 1];
            }

<img src="https://user-images.githubusercontent.com/118953938/208959691-f1284b53-206c-41fe-a931-fa1890d9eb89.png" width=40% height=40%>

4.3) List

        set mylist [list a b c d e f g];
        
<img src="https://user-images.githubusercontent.com/118953938/208960408-d0e18a64-e15f-4d24-b4c6-0f56474b1903.png" width=40% height=40%>

4.4) foreach loop

        foreach my_var $mylist {
        echo $my_var;
        }
        
<img src="https://user-images.githubusercontent.com/118953938/208961109-8aa1ae44-9a28-4ae3-ac32-35aeb72537f5.png" width=40% height=40%>

4.5) foreach_in_collection

        get_lib_cells */*and* ---> listing all the and gates
        ( bracket to bracket means collection)

<img src="https://user-images.githubusercontent.com/118953938/208961567-1fe38025-bc8e-4cd2-9215-036ec37bb365.png" width=40% height=40%>

        foreach_in_collection my_var [get_lib_cells */*and*] {
            echo $my_var;
        } ---> listing the collection of pointers
        
<img src="https://user-images.githubusercontent.com/118953938/208963792-e3669877-de91-423b-b8e6-4fb47447d969.png" width=40% height=40%>

        foreach_in_collection my_var [get_lib_cells */*and*] {
        set my_var_name [get_object_name $my_var]; echo $my_var_name;
        }

<img src="https://user-images.githubusercontent.com/118953938/208964255-aff0eb3f-ed79-43b6-9dab-9a45e0248bcf.png" width=40% height=40%>

Can also be printed in gvim

        sh gvim &

        copy and paste these in gvim

            foreach_in_collection my_var [get_lib_cells */*and*] {
	            set my_var_name [get_object_name $my_var]; echo $my_var_name;
            }

            echo "Printing Multiplication Table"

            set i 10;
            set j 1;
            while {$j < 21} {
	            echo $i*$j;
	            incr j;
            }
        
        Save it 
        :w! myscript.tcl
        Quit
        :q!
        
        Launch it
        source myscript.tcl

<img src="https://user-images.githubusercontent.com/118953938/208965624-8a07c328-2043-4c35-846a-9a9f5edaf3e7.png" width=40% height=40%>

        sh gvim myscript.tcl &

         Edit the highlighted part
           
        foreach_in_collection my_var [get_lib_cells */*and*] {
	        set my_var_name [get_object_name $my_var]; echo $my_var_name;
        }

        echo "Printing Multiplication Table"

        set i 10;
        set j 1;
        while {$j < 21} {
	        echo [expr $i*$j]; --->edited here
	        incr j;
        }

        save
        :wq!
        Launch it
        source myscript.tcl
        
<img src="https://user-images.githubusercontent.com/118953938/208967037-d9f78d2c-cf7f-4c8f-b5c9-98eb4f7a6378.png" width=40% height=40%>



        gvim myscript.tcl &

        add these codes after the last bracket

        set mylist [list a b c d e f g];

        foreach myvar $mylist {
	        echo $myvar;
        }
        echo $mylist;

        save
        :wq!
        Launch it
        source myscript.tcl
        
<img src="https://user-images.githubusercontent.com/118953938/208968503-4b9e0807-c6d4-4b7e-aac3-6e07a756d62d.png" width=40% height=40%>

 # :book: Day 7-Basic SDC constraints

### :mag_right: Introduction to Static Timing Analysis (STA)

:black_nib: What is **Static Timing Analysis (STA)**? <br>
*Static timing analysis (STA) is a technique for evaluating a design's timing performance by inspecting all conceivable paths for timing violations.*

:black_nib: How does STA work?

When performing timing analysis, STA first **breaks down the design into timing paths**. Each timing path consists of the following elements:<br>

*1) **Startpoint**. The start of a timing path where data is launched by a clock edge or where the data must be available at a specific time. Every startpoint must be either an input port or a register clock pin.*<br>
*2) **Combinational logic network**. Elements that have no memory or internal state. Combinational logic can contain AND, OR, XOR, and inverter elements, but cannot contain flip-flops, latches, registers, or RAM.*<br>
*3) **Endpoint**. The end of a timing path where data is captured by a clock edge or where the data must be available at a specific time. Every endpoint must be either a register data input pin or an output port.*<br>

* STA does a complete and exhaustive point to point analysis of the design
* To ensure that despite all possible pessimism in a design, the signals arrives either too early, nor too late and the design maintains its correct operation

<img src="https://user-images.githubusercontent.com/118953938/209026926-b93e616d-b073-44ff-af51-73571fa5a419.png" width=40% height=40%>

:black_nib: **Maximum and minimum delay constraint**

1) Maximum delay constraint<br>
*The maximum delay constraint **limits the number of consecutive gates** on the critical path of a high-speed circuit because a high clock frequency means a short clock period*

2) Minimum delay constraint<br>
*Memory element inputs must not change until a hold time after the sampling edge.*

<img src="https://user-images.githubusercontent.com/118953938/209024681-739a8a08-dd8f-48a7-9f7b-1c1cc73eeef6.png" width=60% height=60%>

:black_nib: **Why delay? look ad the analogy below**

Water bucket analogy

<img src="https://user-images.githubusercontent.com/118953938/209028810-70b8c06e-beaf-465c-a24c-3ee934974cef.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/209030369-a38c1f32-1cc3-4590-a320-77fcc63e444a.png" width=80% height=80%>

:black_nib: **Is delay of a cell constant?**

* Delay of a cell will be a function of input Transition which is the water inflow.<br>
* Delay of a cell will be a function of output load which is the size of the bucket.

<img src="https://user-images.githubusercontent.com/118953938/209033870-e2c37c41-5fcf-467c-a785-2cce313faa4f.png" width=50% height=50%>

:black_nib: **Timing Arc**

*Timing arc is an abstract notion of a timing dependence between the signals at any two related pins of a standard cell.*<br>
* usually present in the timing libraries (liberty files), which are then used by the tool to perform static timing analysis and gate level synthesis of the design

1) Combinational cell

	<img src="https://user-images.githubusercontent.com/118953938/209034242-03853cd0-a070-4528-a475-25b5b8c45c7e.png" width=70% height=70%>

2) Sequential cell<br>
	- can be DFF/D-latch<br>
	- Delay from clock to Q for D-flip flop<br>
	- Delay from clock to Q, delay from D to Q for D latch<br>
	- Setup and hold time<br>

	<img src="https://user-images.githubusercontent.com/118953938/209035848-6d5da6cb-4ba5-47c0-8420-1e2a9b96612d.png" width=70% height=70%>

### :mag_right: Constraints

Before going in details about constraints, lets look at timing path

<img src="https://user-images.githubusercontent.com/118953938/209038467-10013161-0c27-423b-99c4-056147fb2622.png" width=70% height=70%>

:black_nib: **Constraints**

* Design constraints are limitations on a design. 
* These include imposed limitations that you don't control, and limitations that are self-imposed as a way to improve a design.

Why we need constraints?

<img src="https://user-images.githubusercontent.com/118953938/209054060-ad67ab97-ac0f-4d96-ac2f-10af94b36824.png" width=70% height=70%>

:black_nib: **Timing paths**

Start point <br>
* Input ports
* Clk pins of register

End point<br>
* Output ports
* D pins of DFF/D-latch

Always the timing paths start at one of the start points and ends at one of the end points.<br>
* Clk to D (reg-to-reg timing path)
* Clk to output (IO timing path)
* Input to D (IO timing path)
* Input to output (IO timing path that ideally shouldn't be present)

<img src="https://user-images.githubusercontent.com/118953938/209059758-010ae4c4-fbe7-4cd2-be5d-5ef9048e51a0.png" width=70% height=70%>

		REG 2 REG: constrained by clock
		REG 2 OUT: constrained by output external delay and clock period
		IN 2 REG: constrained by input external delay and clock period
		Collectively the REG2OUT and IN2REG are called IO paths and the delay modelling are referred above is called IO Delay Modelling

<img src="https://user-images.githubusercontent.com/118953938/209059792-6addd325-6d68-4009-958c-36febc41ff94.png" width=70% height=70%>

### :mag_right: Input Transfer Output Load

1) Is IO modelling sufficient?

<img src="https://user-images.githubusercontent.com/118953938/209252358-e9ed87fa-4dfd-4369-91ce-57960399fd6e.png" width=70% height=70%>

2) Is IO delay and input transition modelling sufficient for IO path?

<img src="https://user-images.githubusercontent.com/118953938/209253282-8d22d4cd-94ec-45f9-af78-b2c36fce662f.png" width=70% height=70%>

		-> REG 2 REG: constrained by clock
		-> REG 2 OUT: constrained by output external delay, output load and clock period
		-> IN 2 REG: constrained by input external delay, input transition and clock period
		-> The IO paths needs to be constrained for both Max delay (setup) and Min delay (hold)

### :test_tube:	Lab 5- Timing dot Libs

5.1) opening '.lib' file

**Commands**

		1) gvim DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
		2) :syn off
		
**Output**

<img src="https://user-images.githubusercontent.com/118953938/209063373-d73a977b-e3aa-4fe7-8e9e-8e218cf32853.png" width=70% height=70%>

5.1.1) Default Max Transition

<img src="https://user-images.githubusercontent.com/118953938/209065715-31248283-53a6-4d63-88ce-71655f6d71f7.png" width=70% height=70%>

5.1.2) Delay Model Lookup Table

<img src="https://user-images.githubusercontent.com/118953938/209065459-12b9791b-6e71-4b2c-bf2d-758fb60cf722.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/209066723-f5c139df-c947-452a-b438-0775b7e4fd8d.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209070161-c48c941f-6595-408d-aa67-80333aa18573.png" width=60% height=60%>

5.1.2.1) Internal power delay

<img src="https://user-images.githubusercontent.com/118953938/209070265-d3b54dee-d0ea-4236-b7b8-498c4bad2cac.png" width=60% height=60%>

5.1.2.2) Timing delay

<img src="https://user-images.githubusercontent.com/118953938/209071330-2abda278-f49b-4ddd-a425-1900362c0160.png" width=60% height=60%>

5.1.2.3) Combinational timing arc

<img src="https://user-images.githubusercontent.com/118953938/209073440-af95cf54-4b5c-4907-8c6a-7353ccb1bcde.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209073228-4cf3105f-3245-4ed9-9c0a-164fea855f44.png" width=60% height=60%>

### :test_tube:	Lab 6- Exploring dot Lib

6.1) Pin details

<img src="https://user-images.githubusercontent.com/118953938/209078286-64322721-f05a-4f5a-a06f-41f20c9e0349.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209077822-3c281ab2-fc97-4705-a021-be0c12abfc87.png" width=80% height=80%>

6.2) Rising/falling edge of the pins

<img src="https://user-images.githubusercontent.com/118953938/209079520-2e5a361a-e524-4ff0-8974-4a536c9d110c.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209080532-a9032da6-e911-4e11-af1d-b1fa63b5029c.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209084351-6a1ede75-d66e-412d-b37f-ccc305a404c7.png" width=60% height=60%>

6.3) To find DFF and D-latch

**Commands**

		csh
		dc_shell
		echo $target_library
		get_lib_cells */* -filter "is_sequential==true"

<img src="https://user-images.githubusercontent.com/118953938/209085758-e54797b7-21e9-4e48-9445-5c820b4d8fd7.png" width=60% height=60%>

### :test_tube:	Lab 7- Exploring dot Lib part 2

7.1) Loading library

**Commands**

		In dc_shell
		1) list_lib
		2) get_lib_cells */*and* --->collection form (fetch all the 'and' gate in the lib)
		3) foreach_in_collection my_lib_cell [get_lib_cells */*and*] {
			set my_lib_cell_name [get_object_name $my_lib_cell]; echo $my_lib_cell_name;
			} ---> in list form
			
		Wrong way to print out the pointer
		1) foreach_in_collection my_lib_cell [get_lib_cells */*and*] {
			echo $my_lib_cell;
			}

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209160395-a58da666-e029-4d6f-9395-274c23973e19.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209160826-90298c18-91ed-464c-a3eb-6a22da94cf49.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/209161779-2fc27ec6-2f5f-4616-9760-c0ec0d896326.png" width=50% height=50%>

7.2) Pins for specific gate and functionality

**Commands**

		In dc_shell
		1) get_lib_pins sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/*
		2) get_lib_cells */*and* --->collection form (fetch all the 'and' gate in the lib)

		Fetch with pin direction
		1) foreach_in_collection my_pins [get_lib_pins sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/*] {                  
			set my_pin_name [get_object_name $my_pins];                                                                               
			set pin_dir [get_lib_attribute $my_pin_name direction];                                                                   
			echo $my_pin_name $pin_dir;                                                                                               
			}                               
		2) get_lib_attribute sky130_fd_sc_hd__tt_025C_1v80/sky130_fd_sc_hd__and2_0/X function

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209164199-e5af0d0e-3ad7-4262-a4b3-809be06c41eb.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/209164670-88f447da-e8ed-4e7b-9a91-9ca1b8bd9561.png" width=70% height=70%>

7.3) Writing script for displaying needed output

**Commands**

		In dc_shell
		1)  sh gvim my_script.tcl

		In my_script.tcl, paste the below command
		1)  set my_list [list *paste the gates copied]

			#For each cell in the list, find the output pin name and its functionality

			foreach my_cell $my_list {
				foreach_in_collection my_lib_pin [get_lib_pins ${my_cell}/*] {
					set my_lib_pin_name [get_object_name $my_lib_pin];
					set a [get_lib_attribute $my_lib_pin_name direction];
					if {a > 1} {
						set fn [get_lib_attribute $my_lib_pin_name function];
						echo $my_lib_pin_name $a $fn];
					}
				}
			}
		
		2) Save and exit
		3) In dc_shell---> source my_script.tcl

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209167573-c6b5c44e-5b7b-4c96-9f1f-87b0f9a7071c.png" width=80% height=80%>

Getting selected attributes such as clock, area and capacitance value

<img src="https://user-images.githubusercontent.com/118953938/209169698-e428c47d-4dfb-4b13-9424-09ea755ae072.png" width=80% height=80%>

7.4) all attribute list

**Commands**

		In dc_shell
		1) list_attributes -app
		2) list_attributes -app > a
		3) sh gvim a &

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209170520-8fb33463-6f33-4a9f-97fe-7b8adc60dfa1.png" width=80% height=80%>

# :book: Day 8 - Advanced SDC Constraints

### :mag_right: Clock - Clock Tree Modelling - Uncertainty

:black_nib: **Clock Tree**---> **clock distribution network** within a system or hardware design.

* *It includes the clocking circuitry and devices from clock source to destination.* <br>
* *The complexity of the clock tree and the number of clocking components used depends on the hardware design.* <br>
* *Since systems can have several ICs with different clock performance requirements and frequencies, a “clock tree” refers to the various clocks feeding those ICs.*<br>
* *Clock trees can be both very complex with many timing components and very simple with a single reference and a few copies.*

:black_nib: Clock Tree Latency Skew **Uncertainty**

There are two phases in the design of a clock signal.

1) 1st the clock is in “ideal mode” (e.g.: during RTL design, during synthesis and during placement). An “ideal” clock has no physical distribution tree, it just shows up magically on time at all the clock pins.

2) 2nd phase comes when clock tree synthesis (CTS) inserts an actual tree of buffers into the design that carries the clock signal from the clock source pin to the (thousands/millions) of flip-flops that need to get it. CTS is done after placement and before routing. After CTS is finished, the clock is said to be in “propagated mode”.

What actually is clock uncertainty?

Clock uncertainty is **the deviation of the actual arrival time of the clock edge with respect to the ideal arrival time**. In ideal mode the clock signal can arrive at all clock pins simultaneously. 

<img src="https://user-images.githubusercontent.com/118953938/209493056-30f37af3-f1d4-47e5-8818-d35ac909365d.png" width=40% height=40%>

What needs to be constrained by a clock?

		1. Reg to Reg path---> clock period [Tclk >= Tcq + Tcombi + Ts]
		2. Input to Reg path---> clock, input delay and input transition
		3. Output to Reg path---> clock, output delay and load

Let's look at the implementation of ASICS first

<img src="https://user-images.githubusercontent.com/118953938/209494196-ce992bf0-9422-4096-92ec-c9a7f2584b8e.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209495051-ebab629f-ba15-40d9-8c41-e49a993c7ba5.png" width=60% height=60%>

Ideal network- The clock will meet the registers at he same time.
Practical network- There will be a delay routing the clock

:black_nib: CLock generation

Oscillator<br>
* PLL
* External clock source
* All of those clocks generation have inherit generations in the clock priod due to stochastic effect

**Stochastic effects**<br>
* *Stochastic effects of ionising radiation are chance events, with the probability of the effect increasing with dose, but the severity of the effect is independent of the dose received. Stochastic effects are assumed to have no threshold.*

<img src="https://user-images.githubusercontent.com/118953938/209512680-814e8e80-3c5f-49df-847b-e4a659f037f0.png" width=60% height=60%>

:black_nib: CLock distribution

<img src="https://user-images.githubusercontent.com/118953938/209523712-e2e29f09-e02c-49ed-8f02-87d9a107cbf5.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209523840-23fa3dc2-b80f-4c7c-a8f3-cbb241221084.png" width=60% height=60%>

:black_nib: CLock skew

*The difference in the arrival time of a clock signal at two distinct registers, which can be generated by variances in path length between two clock paths or by employing gated or rippled clocks.*

		clock tree built during CTS: practical Clock Tree
		Logic optimization happens during in synthesis: Ideal Clock Tree
		Timing Clean paths in Synthesis may fail after STA

:black_nib: CLock modelling 

Model the clock for following

		1) Period
		2) Source latency: time taken by the clock source to generate clock
		3) Clock network latency: time taken by clock distribution network
		4) Clock skew: clock path delay mismatches which causes difference in the arrival of clock
			4.1) CTS will balance clocks but still skew cannot be reduced to 0
		5) Jitter: stochastic variation in the arrival of clock edge
			5.1) Duty cycle jitter
			5.2) Period jitter
		6) clock skew & jitter is called clock uncertainty
		
**IMPORTANT NOTE** 'post CTS, the clock network is real and hence these modelled clock skew and clock network latency must be removed' 

<img src="https://user-images.githubusercontent.com/118953938/209528365-aa9fae0d-21bb-4f29-ba5d-8cc434806ace.png" width=60% height=60%>

| Stage  | Clock Uncertainty |
| ------------- | ------------- |
| Synthesis | Jitter + Skew  |
| Post CTS | Only Jitter  |

### :mag_right: IO Delays

How to constraint the design in DC?

<img src="https://user-images.githubusercontent.com/118953938/209533442-1afda2a2-27db-435c-85e3-908067310200.png" width=60% height=60%>

:black_nib:Getting Ports in DC (get_ports) ---> Query the ports in the design         

		get_ports clk;
		get_ports *clk*;                         --> a collecting ports
		get_ports *;                             --> all ports of the design
		get_ports * -filter "direction==in";     --> 'filter' -filtering based in the conditions (all input ports)
		get_ports * -filter "direction==out";    --> (all input ports)
		
:black_nib:Getting the clocks in DC

		get_clocks *                                        --> the clocks in the design
		get_clocks *clk*                                    --> clocks which has the name clk in it
		get_clocks * - filter "period>10"                   --> this query which get the attribute of period
		get_attribute [get_clocks my_clk] is_generated
		report_clocks my_clk                                

<img src="https://user-images.githubusercontent.com/118953938/209536004-f5b45951-32bc-4233-a2b7-9f3aaf828cab.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/209537087-d1c85fd2-53ba-4938-a74d-dcb9fcd7ace1.png" width=80% height=80%>

**Bringing the practicalities of the clock network**

<img src="https://user-images.githubusercontent.com/118953938/209537837-f2ca99c2-546a-4dde-84b8-aeb7bb4ec435.png" width=80% height=80%>

**Clocks waveform**

<img src="https://user-images.githubusercontent.com/118953938/209540170-0e1b9356-f894-497f-a665-5a0594e16bb9.png" width=80% height=80%>

**Constraining the IO Paths Constraint the Input/Output**

Input<br>
<img src="https://user-images.githubusercontent.com/118953938/209540453-7f5001ea-6aab-43a5-aeab-c11488c70343.png" width=80% height=80%>

		set_input_delay -max 3 -clock [get_clocks MY_CLK][get_ports IN_*];
		set_input_delay -min 1.5 -clock [get_clocks MY_CLK][get_ports IN_*];
		set_input_transition -max 1.5 [get_ports IN_*];
		set_input_transition -min .75 [get_ports IN_*];
		Note: Both inputs IN_A, IN_B are coming wrt clock MY_CLK created on port CLK

Output<br>
<img src="https://user-images.githubusercontent.com/118953938/209540685-5df98d2e-a746-40a1-8369-626452b3fb00.png" width=60% height=60%>

		set_output_delay -max 3 -clock [get_clocks MY_CLK][get_ports Out_y];
		set_output_delay -min 0.5 -clock [get_clocks MY_CLK][get_ports Out_y];
		set_output_load -max 80 [get_ports Out_y];
		set_output_load -min 20 [get_ports Out_y];

### :test_tube:	Lab 8- Exploring dot Lib

8.1) Opening lab_8 circuit

**Command**

		1) gvim lab8_circuit.v
		
		In dc_shell
		1) echo $target_library
		2) echo $link_library
		3) read_verilog lab8_circuit.v
		4) link
		5) compile_ultra

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209551710-a9687437-c4ff-4c57-a957-2ecb59d7bd53.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209551814-096696b8-9ae2-4100-952f-e4e3f076ecb7.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209551954-cc04b2ee-4a71-49c7-8827-00149bb70a70.png" width=60% height=60%>

8.2) Finding ports and the direction

**Command**

		In dc_shell
		1) get_ports
		2) foreach_in_collection my_port [get_ports *] {
			set my_port_name [get_object_name $my_port]; echo $my_port_name; }---> port list
			
		1) get_ports rst
		2) get_attribute [get_ports rst] direction ---> know direction of only 1 port
		3) foreach_in_collection my_port [get_ports *] {
			set my_port_name [get_object_name $my_port];
			set dir [get_attribute [get_ports $my_port_name] direction];
			echo $my_port_name $dir;
			} --->multiple ports
		
		Fetching cells
		1) get_cells *
		2) get_attribute [get_cells U9] is_hierarchical
		3) get_attribute [get_cells U12] is_hierarchical
		4) get_attribute [get_cells REGA_reg] is_hierarchical
		5) get_cells * -filter "is_hierarchical == false"
		
**Output**

<img src="https://user-images.githubusercontent.com/118953938/209552429-96a6fe49-2dc3-426b-a97d-144fcd4cda37.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/209552703-100412de-c7b8-4bc7-bf6b-7dd4b40eee54.png" width=40% height=40%>

8.3) Getting the ref name

**Command**

		In dc_shell
		1) get_attribute [get_cells REGA_reg] ref_name
		2) foreach_in_collection my_cell [get_cells * -hier] {                                                        
			set my_cell_name [get_object_name $my_cell];                                                                 
			set rname [get_attribute [get_cells $my_cell_name] ref_name];                                                
			echo $my_cell_name $rname;                                                                                   
			}

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209553521-c037d21a-03dd-486f-a235-5020140181a6.png" width=40% height=40%>

8.4) DDC design_vision

**Command**

		In dc_shell
		1) write -f ddc -out lab8_circuit.ddc
		
		In design_vision
		1) read_ddc lab8_circuit.ddc
		2) all_connected N1
		3) all_connected N5
		4) foreach_in_collection my_pin [all_connected n5] {
			set pin_name [get_object_name $my_pin];
			set dir [get_attribute [get_pins $pin_name] direction];
			echo $pin_name $dir;
			}

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209553984-190ac7f6-029e-41ea-8c2d-acfdebd97c2d.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209554229-4b107903-3b53-4ff4-b50b-aab0bf715230.png" width=60% height=60%>

### :test_tube:	Lab 9- get_pins, get_clocks, querying_clocks

9.1) Knowing the pins

**Commands**

		1) get_pins *
		2) foreach_in_collection my_pin [get_pins *] {
			set pin_name [get_object_name $my_pin];
			echo $pin_name;
				}---> listing the pins name
		3) get_attribute [get_pins REGC_reg/RESET_B] direction
		4) get_attribute [get_pins REGC_reg/RESET_B] clock
		5) get_attribute [get_pins REGC_reg/CLK] clock
		6) foreach_in_collection my_pin [get_pins *] {
			set pin_name [get_object_name $my_pin];
			set dir [get_attribute [get_pins $pin_name] direction];
			echo $pin_name $dir;
			}

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209557435-6fbe799a-8dc1-4106-8f46-cfa8d229e792.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209557480-9538d112-55c6-496a-8c49-e9e79be466db.png" width=60% height=60%>

9.2) regexp

**Commands**

		In dc_shell
		1) regexp abcd efgh
		2) regexp abcd abcd
		3) set a in
		4) regexp $a in
		5) regexp $a out
		6) foreach_in_collection my_pin [get_pins *] {
			set pin_name [get_object_name $my_pin];                                                                                      
			set dir [get_attribute [get_pins $pin_name] direction];                                                      
			if { [regexp $dir in] } {                                                                                    
			if { [get_attribute [get_pins $pin_name] clock] } {                                          
			echo $pin_name;                                                                                              
			}                  }        }

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209557787-bddb25e5-1bc3-4b18-8562-7338f643809e.png" width=60% height=60%>

9.3) query_clock_pin.tcl script writing

**Commands**

		In dc_shell
		1) sh gvim query_clock_pin.tcl &
		Paste the bellow command
		foreach_in_collection my_pin [get_pins *] {
			set my_pin_name [get_object_name $my_pin];
       			 set dir [get_attribute [get_pins $my_pin_name] direction];                                                                                              
			if { [regexp $dir in] } {
				if { [get_attribute [get_pins $my_pin_name] clock ] } { 
					echo $my_pin_name $clk_name;

					}
				}
			}	
		4)  source query_clock_pin.tcl
	
**Output**

<img src="https://user-images.githubusercontent.com/118953938/209558228-927808fa-aec8-4577-b864-c4929d669019.png" width=60% height=60%>

9.4) Clock coming in and checking the clock

**Commands**

		In dc_shell
		1) get_attribute [get_pins REGA_reg/CLK] clock
		2) get_attribute [get_pins REGA_reg/CLK] clocks
		3) get_clocks * 
		
**Output**

<img src="https://user-images.githubusercontent.com/118953938/209558805-092847d3-517f-43e6-99ba-351c455011e7.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209558940-2a441c2a-6ed4-465a-a549-b5dbb012de37.png" width=60% height=60%>

**No clock created that is why there is no clock**

### :test_tube:	Lab 10- create_clock waveform

10.1) Get ports, Create Clock, and Know Attribute Reporting clocks

**Commands**

		In dc_shell
		1) current_design --->to know the top module
		2) get_ports *
		3) create_clock -name MYCLK -per 10 [get_ports clk]
		4) get_clocks *
		5) get_attribute [get_clocks MYCLK] period
		6) get_attribute [get_clocks MYCLK] is_generated
		7) get_attribute [get_pins REGA_reg/CLK] clocks
		
		report clock
		8) report_clocks *
		
**Outputs**]

<img src="https://user-images.githubusercontent.com/118953938/209559712-b5c3d1c6-e0bc-4090-8574-0f03ac2bbe3f.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209559762-7d6526f2-c720-40ce-81d0-869e4276c01d.png" width=60% height=60%>

10.2) get the attributes and query_clock_pin.tcl script writing

**Commands**

		In dc_shell
		1) get_attribute [get_pins REGA_reg/CLK] clocks
		2) get_attribute [get_ports out_clk] clocks
		3) sh gvim query_clock_pin.tcl
		Paste bellow command
		foreach_in_collection my_pin [get_pins *] {
			set my_pin_name [get_object_name $my_pin];
        		set dir [get_attribute [get_pins $my_pin_name] direction];                                                                                              
			if { [regexp $dir in] } {
				if { [get_attribute [get_pins $my_pin_name] clock ] } { 
					set clk [get_attribute [get_pins $my_pin_name] clocks]; 
					set clk_name [get_object_name $clk];
 					echo $my_pin_name $clk_name;

				}
			}
			}	
		4) source query_clock_pin.tcl 


**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209560349-058bed52-12e7-4b9e-a0e0-8163754e2aa7.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/209560265-3e2557d0-1e0d-4271-bd03-e15a0e4b485e.png" width=60% height=60%>

10.3) Creating clock

**Commands**

		In dc_shell
		1) create_clock -name BAD_CLK -per 10 [get_pins U14/Y]
		2)  get_clocks *
		3)  report_clocks *
		4) all_connected U14/Y
		5) all_connected n3
		
		Removing clock
		1) remove_clock BAD_CLK

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209560658-53ca3d77-f181-483c-8803-70c72fd1a075.png" width=60% height=60%>

Removing clock

<img src="https://user-images.githubusercontent.com/118953938/209560802-66804087-ae88-4701-b6fd-aaeba523d752.png" width=60% height=60%>

10.4) Waveform adjustment

**Commands**
		
		In dc_shell
		1) remove_clock MYCLK
		2) create_clock -name MYCLK -per 10 [get_ports clk] -wave {5 10} --> rise edge at 5   fall edge at 10
		3) report_clocks *
		
		4) remove_clock MYCLK
		5) create_clock -name MYCLK -per 10 [get_ports clk] -wave {0 2.5}  
		---> first rising edge = 0, fall edge = 2.5,  next rising edge = 10, fall edge =12.5
		6) report_clocks *
		
		7) remove_clock MYCLK
		8) create_clock -name MYCLK -per 10 [get_ports clk] -wave {15 20}
		9) report_clocks *

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209561373-1f63c440-4ede-44ab-964a-62b98b386aeb.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209561453-43c8468a-a0bb-4109-ab9a-bf565ac435c7.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209561532-13208412-245f-419b-97ce-f9df88c059a1.png" width=60% height=60%>

### :test_tube:	Lab 11- Clock Network Modelling - Uncertainty, report_timing

11.1) Model the clock tree attribute

**Commands**
		
		In dc_shell
		1) report_clocks *
			set_clock_latency -source 1 [get_clocks MYCLK] --> modelling source latency
			set_clock_latency 1 [get_clocks MYCLK] --> modelling network latency
			set_clock_uncertainty 0.5 [get_clocks MYCLK] --> max delay time/setup time (default)
			set_clock_uncertainty -hold 0.1 [get_clocks MYCLK] --> min delay time/hold time

		2) remove_clock *
		3) get_clocks *
		4) report_timing
		5) report_timing -to REGC_reg/D

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209562153-5e2c07df-a2c5-46b1-9e13-9f779df9a7ce.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209562165-0d809667-f50c-448b-80cd-b51bfc942474.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209562300-5634b60f-fe94-486a-a03a-2cc70884f063.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209562324-36f5c292-07b0-46be-b3cb-8866900300dd.png" width=60% height=60%>

11.2) Creating clock and report timing

**Commands**
		
		In dc_shell
		1) create_clock -name MYCLK -per 10 [get_ports clk]
		2) report_timing -to REGC_reg/D
			
**Output**

<img src="https://user-images.githubusercontent.com/118953938/209562153-5e2c07df-a2c5-46b1-9e13-9f779df9a7ce.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209562613-8f45f54b-7b1b-4e0e-b8d9-49aa110d9091.png" width=60% height=60%>

11.3) Model clock behaviour and Report Timing

**Commands**
		
		In dc_shell
		1) set_clock_latency -source 2 [get_clocks MYCLK]
		2) set_clock_latency 1 [get_clocks MYCLK]
		3) set_clock_uncertainty -setup  0.5 [get_clocks MYCLK]
		4) set_clock_uncertainty -hold  0.1 [get_clocks MYCLK]
		5)  report_timing -to REGC_reg/D
		6) report_timing -to REGC_reg/D -delay min

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209562945-7a02ae9d-003d-42fc-9f33-97a5f8e190fd.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209563036-198a1db4-80e1-4a52-85e5-257d66b14ff3.png" width=60% height=60%>

11.4) All Port Report

**Commands**
		
		In dc_shell
		1) report_port -verbose

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209563125-10db9212-1089-4e72-87a6-17dc40976822.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209563165-da3c7be1-3838-4776-a437-5a42afef7674.png" width=60% height=60%>

### :test_tube:	Lab 12- Clock Network Modelling - IO Delays

12.1) IO Constraints

**Commands**
		
		In dc_shell
		1) report_timing -from IN_A
		2) report_timing
		3) report_timing -to OUT_Y

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209563366-61941d35-054c-4962-9bf2-f9c01917fb23.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209563393-178123d9-9959-4f6b-908c-421ae16708fe.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209563405-86b3dd6a-4598-4969-9cdb-d43dcc6a6350.png" width=60% height=60%>

12.2) Listing all ports

**Commands**
		
		In dc_shell
		1) report_port -verbose

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209563487-cb948002-78aa-4222-b43e-4c0f0b154164.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209563504-52ae1b06-769e-4dc0-805f-42c0533aecb0.png" width=60% height=60%>

12.3) Modelling

12.3.1) input delay

**Commands**		
		
		In dc_shell ---> delay setup
		1) set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A]				
		2) set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_B]
		3) report_port -verbose
		4) report_timing -from IN_A
		5) report_timing -from IN_A -trans -net -cap
		6) report_timing -from IN_A -trans -net -cap -nosplit > a
		7) sh gvim a

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209564491-812c1581-5925-430f-9070-70b2589e8d05.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209564517-27a117ce-0fe7-440f-b300-965f442af38e.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209564552-f38575c1-1606-4c26-bafd-6c2a1554c4a9.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209564582-5feceb57-ea7f-43cf-901c-27ecb95b1fc7.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209564614-a9f62450-02d5-4512-96f9-5587ce3c62fc.png" width=60% height=60%>

12.4) hold timing 

**Commands**		
		
		In dc_shell 
		report_timing -from IN_A -trans -net -cap -nosplit -delay_type min

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209564846-1537d857-f59c-42e5-a106-a9cb1c9f4bf4.png" width=60% height=60%>

12.5) hold time modelling

**Commands**		
		
		In dc_shell 
		1) set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_A]
		2) set_input_delay -min 1 -clock [get_clocks MYCLK] [get_ports IN_B]
		3) report_timing -from IN_A -trans -net -cap -nosplit -delay_type min

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209564965-898e3619-55a5-454d-b30d-02bcf602a60e.png" width=60% height=60%>

12.6) Setting new maximum value, input transition and output transition

**Commands**		
		
		In dc_shell 
		1) set_input_delay -max 5 -clock [get_clocks MYCLK] [get_ports IN_A]
		2) sh gvim a
		
		1) set_input_transition -max 0.3 [get_ports IN_A]
		2) set_input_transition -max 0.3 [get_ports IN_B]
		3) set_input_transition -min 0.1 [get_ports IN_B]
		4) set_input_transition -min 0.1 [get_ports IN_A]
		5) report_timing -from IN_A -trans  -cap -nosplit > a_trans
		
		1)set_output_delay -max 5 -clock [get_clocks MYCLK] [get_ports OUT_Y]
		2) set_output_delay -min 1 -clock [get_clocks MYCLK] [get_ports OUT_Y]
		3) report_timing -to OUT_Y
		4) report_timing -to OUT_Y -cap -trans

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209565305-e0afd1fc-434e-46e6-bd2f-00c603990766.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209565747-f0b78f89-0d57-4c10-add2-5f5f680702f2.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209565833-f1b66102-8d8f-4e4b-9ac0-3bb102fd2783.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209565857-4fee4d59-530a-468b-bf51-be874dcc4102.png" width=60% height=60%>

12.7) Setting for load minimum delay

**Commands**		
		
		In dc_shell 
		1) set_load -max 0.4 [get_ports OUT_Y]
		2) report_timing -to OUT_Y -cap -trans
		3) report_timing -to OUT_Y -cap -trans -delay min
		4) report_timing -to OUT_Y -cap -trans -delay min

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209566061-67c76b97-3650-4b3f-9bbd-c4afe2efb87a.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209566084-c9f6b00a-872a-498d-a0ac-fb205646bcf3.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209566116-96d1f64b-0b0a-4f11-9f44-c4f82123105f.png" width=60% height=60%>

### :mag_right: SDC Part3: Generated clock

<img src="https://user-images.githubusercontent.com/118953938/209567100-19bcd9e1-c54d-478f-b37a-c6ca4241240f.png" width=60% height=60%>

**Generated clocks**

*A **generated clock** is a **clock derived from a master clock**. A master clock is a clock defined using the create_clock specification. When a new clock is generated in a design that is based on a master clock, the new clock can be defined as a generated clock.*

<img src="https://user-images.githubusercontent.com/118953938/209567246-10d61f3d-00d7-48cb-a0ad-e94748150596.png" width=60% height=60%>

[source](https://www.google.com/url?sa=i&url=https%3A%2F%2Fblogs.cuit.columbia.edu%2Fzp2130%2Fconfigure_sta_environment%2F&psig=AOvVaw3Hnz4-mID2J94Z08fhnWOg&ust=1672158081665000&source=images&cd=vfe&ved=0CA0QjhxqFwoTCPDsnbrYl_wCFQAAAAAdAAAAABAD)

Generation of clock are always created with respect to master clocks (clocks at clock source or primary IO pin)

		create_generated_clock -name MY_GEN_CLK -master [get clocks MY_CLK] -source [get_ports CLK] -div 1 [get_ports OUT_CLK]
		
		->[get clocks MY_CLK] -source [get_ports CLK]
			wrt what the generated clock is created
		->div
			Refers to the division value of generated clock (useful for clock dividers)
		->[get_ports OUT_CLK]
			Generated definition point where the generated clock is created
		->Out_Y need to be constrained wrt the generated clock

**Constraining the Design**

<img src="https://user-images.githubusercontent.com/118953938/209568289-69e25ca2-42a9-4523-9b5a-463e9ac841f8.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209568265-a7c9074d-8abb-4d98-8702-cf7410ac824e.png" width=60% height=60%>

### :test_tube:	Lab 13- Generated clock

13.1) creating a generated clock

**Commands**		
		
		In dc_shell 
		1) report_timing -to OUT_Y
		
		creating a generated clock
		1) create_generated_clock -name MYGEN_CLK -master MYCLK -source [get_ports clk] -div 1 [get_ports out_clk]
		2) report_clocks
		3) get_attribute [get_clocks MYGEN_CLK] is_generated-->True if it is generated clk
		4) get_attribute [get_clocks MYCLK] is_generated-->False if it is generated clk - master clk

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209568760-c69818be-424b-49a8-8244-9188a9383812.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209568881-41576a78-4459-4c32-92f9-051645123c5c.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209568899-29218e96-2d1d-4dc9-9dc5-41275e50d09b.png" width=40% height=40%>

13.2) modification of lab8_circuit.v

**Commands**	

		sh gvim lab8_circuit.v
		:vsp lab8_circuit_modified.v 

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209569238-a6e10ae7-2d12-45f0-951f-f9749b59bce6.png" width=60% height=60%>

13.3) Reset the design

**Commands**		
		
		In dc_shell 
		1) reset_design
		2) read_verilog DC_WORKSHOP/verilog_files/lab8_circuit_modified.v
		3) sh gvim DC_WORKSHOP/verilog_files/lab8_cons.tcl
		4) link
		5) source DC_WORKSHOP/verilog_files/lab8_cons.tcl
		6) report_clocks
		7) get_generated_clocks
		
		reporting the ports
		1) report_port -verbose
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209569445-ebf21f07-8efb-4b79-b324-000a9f1682a4.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209569490-1434dae4-b501-4a8e-838f-d9142279d8e1.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209569655-7e4bd9ef-557b-4649-a543-57b2082a3a8e.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209569752-e977a4e9-3a46-4547-90ba-b14b2a3dfac5.png" width=60% height=60%>
<img src="https://user-images.githubusercontent.com/118953938/209569767-4e56156e-6f76-41f1-8ae2-a5d95516baa7.png" width=60% height=60%>

DESIGN SUCCESSFULLY CONSTRAINED!!

### :mag_right: SDC Part4: vclk, max_latency, rise_fall IO Delays

Input Delay

<img src="https://user-images.githubusercontent.com/118953938/209597754-08fd4e3b-ac31-4c2b-ab58-7888eadb21ee.png" width=60% height=60%>

Output Delay

<img src="https://user-images.githubusercontent.com/118953938/209598149-bbba4d6e-a652-45ec-875d-e051f0521101.png" width=60% height=60%>

IO Constrains Re-Visited

<img src="https://user-images.githubusercontent.com/118953938/209598556-890ba205-a86d-4744-a8cc-da142d0653e9.png" width=60% height=60%>

Can be overcome by a **Virtual CLock**

		create_clock -name MY_VCLK -period 5 #no clock definition point (automatically inferred as virtual clock)
		
input and output delay for virtual clock

<img src="https://user-images.githubusercontent.com/118953938/209599010-d1f04693-291d-4f15-b828-bc72f0633dc1.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209599369-4176673e-15ff-4316-9872-ed1b65255a73.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209599437-32ebd66f-7b40-44a0-9d47-a9ac76162072.png" width=60% height=60%>

Taken from the slides and trainer for reffrencing

<img src="https://user-images.githubusercontent.com/118953938/209600040-cdcfc954-d437-47e5-8b46-2051d7f0ae51.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209600057-f86d0a1d-2e7c-4c49-a5bd-cab96033e137.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209600186-f569761b-7ea2-4e32-9903-58d445a33795.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209599832-8ab51312-2cb2-47de-83c2-8e46ea65e213.png" width=60% height=60%>



### :test_tube:	Lab 14- Set_Max_delay

Recall on previous design

<img src="https://user-images.githubusercontent.com/118953938/209570597-a74d65ad-6b2f-4907-a0c7-6d17fb213c14.png" width=60% height=60%>

14.1) lab14_circuit.v

**Commands**		
		
		In dc_shell 
		1) reset_design
		2) sh gvim DC_WORKSHOP/verilog_files/lab14_circuit.v
		3) read_verilog DC_WORKSHOP/verilog_files/lab14_circuit.v
		4) source DC_WORKSHOP/verilog_files/lab8_cons.tcl 
		5) report_timing
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209570917-5c8bc6c7-bf73-44a1-8868-6258bc34b726.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209570951-b016799b-caad-49df-b9dd-ac83ce5db4fe.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209570988-cde1997a-41e7-4062-ba80-0d6c90d13353.png" width=60% height=60%>

UNLINKED DESIGN!!

14.2) Linking the design

**Commands**		
		
		In dc_shell 
		1) link
		2) compile_ultra
		3) report_timing
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209571150-0c4d282c-b441-495c-b1b0-79badc036cb2.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209571187-9f454186-27de-43e5-b661-30fcc7c71c0c.png" width=60% height=60%>
<img src="https://user-images.githubusercontent.com/118953938/209571207-2a9f579c-d0f2-46d1-9c4a-f56ae33ca33d.png" width=60% height=60%>

14.3) Checking path (wheather it is constraint or not)

**Commands**		
		
		In dc_shell 
		1) get_ports *
		2) report_timing -to OUT_Z
		3) report_timing -from IN_C
		
		helpful commands to try on
		all_inputs--->Listing all inputs
		all_outputs--->Listing all outputs
		all_clocks --->Listing all clocks
		all_registers --->Listing all registers
		all_registers -clock MYCLK --->Listing registers clocked by MYCLK
		all_fanout -from IN_A 	--->Listing all fanouts of desired input
		all_fanout -flat -endpoints_only -from IN_A
		all_fanin -to REGA_reg/D
		all_fanin -flat -startpoints_only -to REGA_reg/D
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209571478-e6b66d69-4a9e-473b-b8d5-6af109d6c440.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209571503-2aa5fe4e-a5af-49ab-8150-1fe6d8a99741.png" width=60% height=60%>

Note that the ENDPOINTS of a timing path = D pin or out pin

14.4) Constraining path to Z

There is mo path to OUT_Z yet

**Commands**		
		
		In dc_shell 
		1) set_max_delay 0.1 -from [all_inputs] -to [get_port OUT_Z]
		2) report_timing -to OUT_Z -sig 4
		
		OPtimizing
		1) compile_ultra
		2) report_timing -to OUT_Z -sig 4
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/209571725-e0f8b8b3-6109-4ded-b5b4-5696fcd9324e.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209571784-c22ffb2d-004e-451a-b738-f6c6bccc1414.png" width=60% height=60%>

14.5) Invoking design_vision

**Commands**		
		
		In dc_shell 
		1) write -f ddc -out lab14.ddc
		2) reset_design
		3) read_ddc lab14.ddc
		4) start_gui

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209571984-3f6ac2a3-688f-4e48-8a88-d0c31f49d1a6.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/209572141-81365330-1f57-438f-8001-d416dc63bb7e.png" width=80% height=80%>

### :test_tube:	Lab 15 - part2 - VCLK

**virtual clock** is a clock that has been defined, but has not been associated with any pin/port.

	While using VCLK

		1st method--> set_max_delay
		2nd method--> use virtual clock where a clock is created without a definition point

15.1) VCLK

**Commands**		
		
		In dc_shell 
		1) reset_design
		2) read_verilog lab14_circuit.v
		3) link
		4) source lab8_cons.tcl
		5) compile_ultra
		6) report_clocks
		7) report_timing -to OUT_Z
		8) create_clock -name MYVCLK -per 10
		9) report_clocks

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209572529-a2757e0e-67b1-4659-bf08-21d3c2f0d52c.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572572-0a1610f8-d8bc-41da-910b-234116193d92.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572615-e32cbca4-3bc9-421a-a691-16100df7239a.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572727-77a6e0d6-30e3-4ec8-8038-7a3df2c3789d.png" width=60% height=60%>

15.1) IO delays

**Commands**		
		
		In dc_shell 
		1) set_input_delay -max 5 [get_ports IN_C] -clock [get_clocks MYVCLK]
		2) set_input_delay -max 5 [get_ports IN_D] -clock [get_clocks MYVCLK]
		3) set_output_delay -max 4.9 [get_ports OUT_Z] -clock [get_clocks MYVCLK]
		4) report_timing
		5) compile_ultra
		6) report_timing -to OUT_Z -sig 4
		7) report_port -verbose

**Output**

<img src="https://user-images.githubusercontent.com/118953938/209572837-8e9fbae4-3426-4705-9a5d-5a441ae99770.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572862-a92b1f27-79ce-414d-9274-92e982c628a4.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572875-91bc134a-afdb-4c83-8ebc-140a72400616.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572973-42333f33-2353-49d9-b926-d1975a7609e1.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209572997-0e7b9147-2475-4976-8276-6a49d7802d48.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/209573013-44b69fb7-a171-4419-80ee-17390ef520f9.png" width=60% height=60%>

# :book: Day 9- Optimization in synthesi

### :mag_right: Optimizations Combinational Opt

:black_nib:  **Optimization goals**

* Cost function based optimizations
	* Optimization until the cost is met 
	* Over optimization of one goal will harm other goals
	* Goals for synthesis
		* Meet Timing
		* Meet Area 
		* Meet Power

<img src="https://user-images.githubusercontent.com/118953938/209962353-e044703d-e199-41c7-8fcf-ffc640dfe2aa.png" width=30% height=30%>

:black_nib:  **Combinational logic optimization**

:pushpin: Function: Squeezing the logic to get most optimised design.<br>
	
	* Area and Power savings
	
:pushpin: Constant Propagation<br>
	
	* Direct Optimization
	
<img src="https://user-images.githubusercontent.com/118953938/209964812-ece165a5-7324-4379-a38c-dbd4989e934d.png" width=80% height=80%>


:pushpin: Boolean Logic Optimization<br>
	
	* K-Map
	* Quine McKluskey

<img src="https://user-images.githubusercontent.com/118953938/209969225-07b887fb-28e0-437d-8ebd-bd522be2a976.png" width=80% height=80%>

**Resource sharing**

<img src="https://user-images.githubusercontent.com/118953938/210024216-8814241c-0451-41ce-a96d-03b04cd5608b.png" width=80% height=80%>

**Logic sharing**

<img src="https://user-images.githubusercontent.com/118953938/210025816-adb82cc0-f074-40b0-adb4-ac478efea91d.png" width=80% height=80%>

**Balanced vs Preferential Implementation**

<img src="https://user-images.githubusercontent.com/118953938/210027705-82324d62-c3b5-400c-90ac-a7d6a1b9d74f.png" width=80% height=80%>

Constraint is very important in a design. It is dependable on the output of the timing to arrange the constraint needed.

### :mag_right: Sequential Optimizations

:black_nib: **Basic**

	1) Sequential Constant Propagation
	2) Retiming
	3) Unused Flop removal
	4) Clock gating

:black_nib: **Advanced**

	1) State optimization
	2) Sequential logic cloning
	
:black_nib: **Sequential constant**

Q is grounded

<img src="https://user-images.githubusercontent.com/118953938/210282865-3e46d4c3-1ac2-439d-8565-333c136ad328.png" width=80% height=80%>

Q is sourced/optimized

<img src="https://user-images.githubusercontent.com/118953938/210283451-04e309de-f323-4c44-81b1-e423d56ab7f4.png" width=80% height=80>

:black_nib: **Constant Propagation**

Sequential constant

<img src="https://user-images.githubusercontent.com/118953938/210283920-8cc7e91e-3684-488a-8f0a-61a10d94b5b3.png" width=80% height=80>

:black_nib: **Optimization of Unloaded output**

<img src="https://user-images.githubusercontent.com/118953938/210284215-110cb5ac-339f-4716-9c47-ce8c116d0e95.png" width=80% height=80>

:black_nib: **Controlling sequential optimizations in DC**

	1) compile_seqmap_propagate_constants 
		For propagation sequential constant (The cct remain the same)

	2) compile_delete_unloaded_sequential_cells 
		For sequential optimization


	3) compile_register_replication 
		Cloning registers

### :test_tube:	Lab 16 - part 1 Combinational_optimizations

16.1) Optimization of opt_check.v

**Commands**

		1) sh gvim opt_check*.v -o
		2) read_verilog opt_check.v
		3) report_timing
		4) get_cells *
		5) report_timing -to y2
		6) report_timing -to y1
		7) write -f ddc -out opt_check.ddc
		
		In design_vision
		1) read_ddc opt_check.ddc

**Outputs**

Gvim<br>
<img src="https://user-images.githubusercontent.com/118953938/210042828-f9e1ff77-98d5-4705-8207-1ce065003ee3.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210043041-6056efa7-c42e-4c1e-b851-b7c6e70eb2e2.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210043723-7f893813-aab1-45f9-8e12-10f15d4a7ec0.png" width=80% height=80%>

16.2) Optimization of opt_check2.v

**Commands**

		1) read_verilog opt_check2.v
		2) link
		3) compile
		4) write -f ddc -out opt_check2.ddc
		
		In design_vision
		1) read_ddc opt_check2.ddc

**Outputs**

Expected

<img src="https://user-images.githubusercontent.com/118953938/210055409-ae906791-b603-485a-ba5d-1257701c6379.png" width=80% height=80%>

Real

<img src="https://user-images.githubusercontent.com/118953938/210055498-e8052e9f-018b-4e3b-8289-0e93227315b4.png" width=80% height=80%>

16.3) Optimization of opt_check3.v

**Commands**

		1) read_verilog opt_check3.v
		2) link
		3) compile
		4) write -f ddc -out opt_check3.ddc
		
		In design_vision
		1) read_ddc opt_check3.ddc

**Outputs**

Expected

<img src="https://user-images.githubusercontent.com/118953938/210055605-3d63ab43-968d-4a21-95fc-318a0c619397.png" width=80% height=80%>

Real

<img src="https://user-images.githubusercontent.com/118953938/210055682-f33262f6-07ee-4133-9f1b-c23967f0cb27.png" width=80% height=80%>

16.4) Optimization of opt_check4.v

**Commands**

		1) read_verilog opt_check4.v
		2) link
		3) compile
		4) write -f ddc -out opt_check4.ddc
		
		In design_vision
		1) read_ddc opt_check4.ddc

**Outputs**

Expected

<img src="https://user-images.githubusercontent.com/118953938/210055891-10aead77-5279-4c65-a452-f65d0a9d382c.png" width=80% height=80%>

Real

<img src="https://user-images.githubusercontent.com/118953938/210055972-2132ed8e-1d4c-49e0-bcdc-ca27a3e8cf57.png" width=80% height=80%>

### :test_tube:	Lab 16 - part 2 Resource Sharing Optimizations

16.5) Optimization of resource_sharing_mult_check.ddc

**Commands**

		1) sh gvim DC_WORKSHOP/verilog_files/resource_sharing_mult_check.v
		2) read_verilog DC_WORKSHOP/verilog_files/resource_sharing_mult_check.v
		3) link
		4) compile_ultra
		5) write -f ddc -out DC_WORKSHOP/verilog_files/resource_sharing_mult_check.ddc
	
		1) reset_design
		2) read_ddc DC_WORKSHOP/verilog_files/resource_sharing_mult_check.ddc

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210242491-982418a9-1b75-4ad3-8024-e0e139084922.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/210243763-c0d38a7c-986c-48fe-9374-9aac5ce3d821.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/210244460-3f5d137d-7af9-450a-b7a6-8581e530ea26.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/210244842-37a875f8-1868-4565-8ed4-016153ad5b30.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/210247193-7e8b1c53-e18c-4d43-be6b-9276cf87afce.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210284637-478931f4-e2ed-4176-846d-0d599cc253ea.png" width=80% height=80%>

16.6) Constraint area

**Commands**

		1) set_max_area 800
		2) compile_ultra
		3) report_timing -sig 4
		4) report_area

<img src="https://user-images.githubusercontent.com/118953938/210284691-ae644fe8-4db6-4a53-b0cc-110a3a9177f9.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210284700-5430c83b-d642-4dcd-98cf-aa2664e17b21.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210284416-79e6945f-add4-44b1-986c-8516381001c7.png" width=80% height=80%>


### :test_tube:	Lab 17 - Seq Optimizations

17.1) Display (sh gvim dff_cons* -o)

<img src="https://user-images.githubusercontent.com/118953938/210255623-04c7ac8c-1479-46ed-a2c2-036bf30f77c0.png" width=50% height=50%>

17.2) Optimizations

Theoritical Expectations 

17.2.1(2)) dff_const.v and dff_const2.v

<img src="https://user-images.githubusercontent.com/118953938/210252655-57e28dca-16c1-4935-a08a-ba278869e36c.png" width=80% height=80%>

17.2.3) dff_const3.v

<img src="https://user-images.githubusercontent.com/118953938/210255334-c0a6085f-74ce-4c18-be64-5497a690f976.png" width=80% height=80%>

17.2.4) dff_const4.v

<img src="https://user-images.githubusercontent.com/118953938/210256965-e2ff6076-7ae1-4693-9c14-dac477227609.png" width=80% height=80%>

17.2.5) dff_const5.v

<img src="https://user-images.githubusercontent.com/118953938/210257599-3b377c8e-0e7c-4eab-820b-8fcc192f58e3.png" width=80% height=80%>

**Commands**

		1) reset_design
		2) read_verilog dff_const1.v
		3) link
		4) compile
		
		Getting the cells
		5) get_cells
		6) foreach_in_collection my_cell [get_cells *] {
			set cell_name [get_object_name $my_cell];
			echo $cell_name; 
			}
		7) foreach_in_collection my_cell [get_cells *] {
			set cell_name [get_object_name $my_cell];
			set rn [get_attribute [get_cells $cell_name] ref_name];  
			echo $cell_name $rn; 
			}
			
		In design_vision
		1) read_verilog dff_const1.v
		2) link
		3) compile

**Outputs**

17.2.1) dff_const.v

<img src="https://user-images.githubusercontent.com/118953938/210259048-73e535cb-b9d2-4085-86eb-452df0032683.png" width=80% height=80%>

17.2.2) dff_const2.v

<img src="https://user-images.githubusercontent.com/118953938/210259766-f46500cf-36b1-4ee1-a17f-70e252cf082d.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210260262-5ff65b9c-4312-4414-acbf-03a0dce69ebb.png" width=80% height=80%>

17.2.3) dff_const3.v

<img src="https://user-images.githubusercontent.com/118953938/210260917-34e5c323-a31b-47ff-8629-473c79c489ad.png" width=80% height=80%>

17.2.4) dff_const4.v

<img src="https://user-images.githubusercontent.com/118953938/210261155-420cb6d6-900c-4c5d-8441-2d40193741c1.png" width=80% height=80%>

17.2.5) dff_const5.v

<img src="https://user-images.githubusercontent.com/118953938/210261347-d2c36766-4d60-40b8-89d4-3b86ebe41484.png" width=80% height=80%>

### :mag_right: Special Optimizations

Register Retiming

* Register retiming is a circuit optimization technique that moves registers forward or backward across combinational elements in a circuit. 
* The aim of this procedure is to shorten the clock cycle or reduce circuit area. There are two basic types of register retiming: Forward retiming and backward retiming.

<img src="https://user-images.githubusercontent.com/118953938/210262288-9e6fff5c-2531-4a51-b37b-e0d5f053e5ae.png" width=70% height=70%>

:black_nib: **Retiming part**

<img src="https://user-images.githubusercontent.com/118953938/210263386-2312f5a9-66a1-461c-af8f-f687d91684f7.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/210263820-69bb4cc0-26e9-49bf-884d-ddb418147a45.png" width=70% height=70%>

:black_nib: **Boundary Optimization**

<img src="https://user-images.githubusercontent.com/118953938/210264695-0b83356d-e863-48de-9079-6f17a5766f74.png" width=100% height=100%>

Applying boundary optimization

Negative: May have problem with the functional design verification<br> 
Positive: bring most optimal logic<br> 

Commands
		
		1) set_boundary_optimization <design><true|false>
		2) set_boundary_optimization module_sub false
		
:black_nib: **Multicycle Path**

<img src="https://user-images.githubusercontent.com/118953938/210266758-d18c392b-e000-4b25-8ea2-b62066cde001.png" width=70% height=70%>

Need to understand the design thoroughly before using it!!!

Command

	set multicycle_path -setup 2 -to prod_reg[*]/D -through [all_inputs]

:black_nib: **False path**

<img src="https://user-images.githubusercontent.com/118953938/210268326-0a837bba-487f-4b0a-8314-c2c25fd7de5d.png" width=70% height=70%>

:black_nib: **External Load vs Internal Load**

<img src="https://user-images.githubusercontent.com/118953938/210269633-c7c4434c-a3c2-459d-955d-afd50a0f1389.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/210269868-58dc3997-f96d-4087-9786-566acaa8a61e.png" width=75% height=75%>

### :mag_right: How Paths are timed MCP?

:black_nib: **Single cycle path**

Single Cycle Datapaths : Single Datapaths is equivalent to the original single-cycle datapath The data memory has only one Address input. The actual memory operation can be determined from the MemRead and MemWrite control signals. There are separate memories for instructions and data.

<img src="https://user-images.githubusercontent.com/118953938/210273809-639be681-9476-4f65-8260-7888f13f5292.png" width=75% height=75%>

:black_nib: **Half cycle path**

A half cycle timing path is one in which launch and capture happen on different clock edges. A half cycle path can be in terms of both setup and hold.

<img src="https://user-images.githubusercontent.com/118953938/210274090-5cbd7f91-5319-40a9-872e-785527946bad.png" width=75% height=75%>

:black_nib: **Multi cycle path**

Multicycle paths are data paths between two registers that operate at a sample rate slower than the FPGA clock rate and therefore take multiple clock cycles to complete their execution. Multi-cycle data path break up instructions into separate steps. It reduces average instruction time. Each step takes a single clock cycle Each functional unit can be used more than once in an instruction, as long as it is used in different clock cycles. It reduces the amount of hardware needed.

<img src="https://user-images.githubusercontent.com/118953938/210275040-b7d7f0d0-b9e9-46aa-892b-8631070d0204.png" width=75% height=75%>

Command

	set multicycle_path -setup 2 -from [all_inputs] -to prod_reg[*]/D 
	set multicycle_path -hold 1 -from [all_inputs] -to prod_reg[*]/D 

### :test_tube:	Lab 18 - Boundary Optimization

18.1) open (sh gvim check_boundary.v)

<img src="https://user-images.githubusercontent.com/118953938/210275830-31e449b7-f78a-494d-9cdb-df9580ecf238.png" width=75% height=75%>

**Commands**

		1) reset_design
		2) read_verilog check_boundary.v
		3) link
		4) compile_ultra
		5) write -f ddc -out boundary.ddc
		6) get_cells
		
		In design_vision
		1) read_ddc boundary.ddc

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210276737-efeef769-840d-47c6-a342-ee57d4ad5adc.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210277098-cee67691-2e1e-40da-8c69-29a8d5ffc8ac.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210276963-f83785be-18fa-4493-9340-ec78eb218df9.png" width=75% height=75%>

**Commands**
 		
		In design_vision
		1) reset_design
		2) read_verilog check_boundary.v
		3) link
		4) get_cells
		5) get_pins u_im/*
		6) set_boundary_optimization u_im false
		7) compile_ultra

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210277369-bed9ab69-b32e-4334-a687-8381ab1c0886.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210277557-7d12fdb0-4b17-4090-9c0f-b51ba3641095.png" width=75% height=75%>

### :test_tube:	Lab 19 - Register Retiming

19.1) Open (sh gvim DC_WORKSHOP/verilog_files/check_reg_retime.v)

<img src="https://user-images.githubusercontent.com/118953938/210278373-d8c95f9d-57b5-49ef-ae3c-bab0d0c1f229.png" width=75% height=75%>

**Commands**
 		
		In design_vision
		1) read_verilog check_reg_retime.v
		2) link
		3) compile

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210278600-a80035e4-7ae7-4726-910a-92f3dd8305ac.png" width=75% height=75%>

**Commands**

		1) report_timing
		2) sh gvim reg_retime_cons.tcl-->Setting up constraints
		3) source reg_retime_cons.tcl
		4) report_clocks
		5) report_timing
		6) compile_ultra -retime
		7) start_gui
		
		1) report_timing
		2) compile_ultra
		3) report_timing -from [all_inputs]
		4) report_timing -from [all_inputs] -trans -cap -nosplit -sig 4

**Outputs**

![image](https://user-images.githubusercontent.com/118953938/210278917-29227d8b-8589-47bf-b06f-dc04208e8b5d.png)

<img src="https://user-images.githubusercontent.com/118953938/210279107-8ef50c92-b837-4ff7-b9d2-760f32cbf119.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210279257-17b0b846-2ca2-4492-bdf8-04512d1ff926.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210279313-0a47bf75-7476-4840-ae7d-6e59b8bafdf0.png" width=55% height=55%>

### :test_tube:	Lab 20 - Isolating output ports

<img src="https://user-images.githubusercontent.com/118953938/210279699-588cf67c-ab1c-46c9-a96a-2c6d8c3c1a18.png" width=80% height=80%>

20.1) Open (sh gvim check_boundary.v)

<img src="https://user-images.githubusercontent.com/118953938/210275830-31e449b7-f78a-494d-9cdb-df9580ecf238.png" width=75% height=75%>

**Commands**

		1) reset_design
		2) read_verilog check_boundary.v
		3) link
		4) compile_ultra
		5) start_gui
		
		1) set_isolate_ports -type buffer [all_outputs]
		2) compile_ultra
		3)start_gui

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210280494-1bbee116-3619-4638-afc6-3f498ad246fe.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210280793-d68f1828-95b5-44e5-a1d5-c6e7db824a52.png" width=75% height=75%>

**Commands**

		reset_design
		read_verilog check_boundary.v
		link
		compile_ultra
		create_clock -per 5 -name myclk [get_ports clk]
		set_input_delay -max 2 [all_inputs] -clock myclk
		set_output_delay -max 2 [all_outputs] -clock myclk
		set_load -max 0.3 [all_outputs]
		report_timing -nosplit -inp -cap -trans -sig 4
		report_timing -to val_out_reg[0]/D -inp -trans -nosplit -cap -sig 4	

**Outputs**

![image](https://user-images.githubusercontent.com/118953938/210281008-bdc7ee5e-cff6-4008-a934-81188664126b.png)


20.2) Ports isolation

**Commands**

		set_isolate_ports -type buffer [all_outputs]
		compile_ultra
		report_timing -nosplit -inp -cap -trans -sig 4
		report_timing -from val_out_reg[0]/CLK -to val_out_reg[0]/D -nosplit -inp -cap -trans -sig 4	

**Outputs**

![image](https://user-images.githubusercontent.com/118953938/210281283-a109ce5a-6ab0-400b-bb7d-2835d71b006a.png)

### :test_tube:	Lab 21 - MultiCycle path

21.1) Open (sh gvim mcp_check.v)

<img src="https://user-images.githubusercontent.com/118953938/210281417-9a41937a-6cab-4eaf-9a65-c3c65df63dc0.png" width=75% height=75%>

**Commands**

		1) read_verilog mcp_check.v
		2) link
		3) compile_ultra
		4) sh gvim mcp_check_cons.tcl
		5) source mcp_check_cons.tcl
		6) report_timing
		7) compile_ultra
		8) report_timing
		9) set_multicycle_path -setup 2 -to prod_reg[*]/D -from [all_inputs] 	
		10) report_timing -to prod_reg[*]/D -from valid_reg/CLK
		11) report_clock *

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210281806-4587ebd6-25ec-4507-9f81-79ca072f8e85.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210281891-f6ddd6f9-6556-4c69-acb1-0092d01b915f.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210281950-34845061-42c4-470c-988e-e264887a207c.png" width=65% height=65%>

21.2) Applying MCP

**Commands**

		Hold time
		1) report_timing -delay min
		
		1) set_multicycle_path -hold 1 -from [all_inputs] -to prod_reg[*]/D
		2) report_timing -delay min -to prod_reg[*]/D -from [all_inputs]
		3) report_timing -nosplit -inp -cap -trans -sig 4

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210282215-5663ad20-8431-4050-ba31-bf8b46d6516b.png" width=65% height=65%>

<img src="https://user-images.githubusercontent.com/118953938/210282233-fab93a48-1296-43ca-aec6-88e6f43f73c6.png" width=65% height=65%>

# :book: Day 10- Quality Checks - Quality of Results (QOR)

### :mag_right: Report Timing

:black_nib:  **List of commands**

	1) report_timing -from DDF_A/clk
	2) report_timing -from DDF_A/clk -to DDF_A/d
	3) report_timing -fall_from DDF_A/clk
	4) report_timing -rise_from DDF_b/clk
	5) report_timing -delay_type min -to DDF_C/d
	6) report_timing -delay_type min -through INV/a
	7) report_timing -delay_type max -through AND/b
	8) report_timing -rise_from DDF_b/clk -delay_type max -nets -cap -trans -sig 4    
	
	Default
	delay_type max (not for specified delay type)
	
:black_nib:  **Propagation Delay**
	












