# :book: My Respository

## :book: Day 0-System/Tool Setup Check. GitHub ID creation

<details><summary> :mag_right: Theories </summary>
<p>
	
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
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
## Lab Work

### Intel Unix System

<img src="https://user-images.githubusercontent.com/118953938/205214388-1e25012b-6851-47a6-9b7c-437779e538ab.png" width=50% height=50%>

Successfully executed!
</p>
</details>

## :book: Day 1-Introduction to Verilog RTL design and Synthesis

<details><summary> :mag_right: Theories </summary>
<p>
	
## Quick theory recap

**1) RTL (Register−Transfer Level)**- A design abstraction which models a synchronous digital circuit in terms of the flow of digital signals between hardware registers, and the logical operations performed on those signals<br />
**1.1) Benefit**: more compact since the language is more of an actual hardware modeling language. Write fewer lines of code, and it elicits a comparison to the C language.<br />

**2) Hardware description language (HDL)**: A programming language used to describe the behavior or structure of digital circuits (ICs).

**3) iVerilog**: An implementation of the Verilog hardware description language compiler that generates netlists in the desired format.

**4) GTKWave**: A fully featured GTK+ based wave viewer for Unix, Win32, and Mac OSX which reads LXT, LXT2, VZT, FST, and GHW files as well as standard Verilog. 

<img src="https://user-images.githubusercontent.com/118953938/205651867-5bfd9786-fe3b-493a-8d9d-5f835ea4c9db.png" width=50% height=50%>

</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
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
</p>
</details>

## :book: Day 2- Timing libs(QTMs/ETMs), hierarchical vs flat synthesis and efficient flop coding styles

**Note/: Theory was put between the labs**

<details><summary> :test_tube: Labs </summary>
<p>
	
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

</p>
</details>

## :book: Day 3 - Combinational and sequential optimizations

<details><summary> :mag_right: Theories </summary>
<p>
	
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
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
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
</p>
</details>


## :book: Day 4 - GLS, Synthesis-Simulation mismatch and Blocking/Non-blocking statements

<details><summary> :mag_right: Theories </summary>
<p>
	
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

</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
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

</p>
</details>

## :book: Day 5 - Design For Testability

<details><summary> :mag_right: Theories </summary>
<p>
	
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
</p>
</details>

## :book: Day 6 - Introduction to Logic Synthesis

<details><summary> :mag_right: Theories </summary>
<p>
	
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

</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
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
</p>
</details>

 ## :book: Day 7-Basic SDC constraints

<details><summary> :mag_right: Theories </summary>
<p>
	
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

</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
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
</p>
</details>


## :book: Day 8 - Advanced SDC Constraints

<details><summary> :mag_right: Theories </summary>
<p>
	
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
</p>
</details>

<details><summary> :test_tube:	Labs </summary>
<p>
	
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

</p>
</details>


## :book: Day 9- Optimization in synthesi

<details><summary> :mag_right: Theories </summary>
<p>
	
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

</p>
</details>

<details><summary> :test_tube:	Lab </summary>
<p>
	
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
</p>
</details>


## :book: Day 10- Quality Checks - Quality of Results (QOR)
	
<details><summary> :mag_right: Theories </summary>
<p>

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
	
*Propagation delay is the **time required for the input to be propagated to the output.***

<img src="https://user-images.githubusercontent.com/118953938/210297676-5d6cfc2e-23f3-4098-a01b-ea87e66239d3.png" width=85% height=85%>

For the NAND gate<br>
* The current sinking path (to GND) and current sourcing path (to Y) are different
* This results to different mobility of electrons and hole
* Delay also will be different
* Load on A and load on B will be different too

:black_nib:  **Timing Paths**

<img src="https://user-images.githubusercontent.com/118953938/210304992-8df9943d-e8e7-4f66-adbc-b203dae7822c.png" width=85% height=85%>

<img src="https://user-images.githubusercontent.com/118953938/210306109-df0d73a1-400e-49dc-93a6-de95432e31a4.png" width=85% height=85%>

:black_nib:  **Max_Paths and Nworst**

<img src="https://user-images.githubusercontent.com/118953938/210307900-676c441c-26ae-4ae0-95eb-106822a8a82d.png" width=85% height=85%>
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
### :test_tube:	Lab 1 - Lab Report timing

1.1) Open (sh gvim lab8_circuit_modified.v)

**Commands**

		1) sh gvim lab8_circuit_modified.v
		2) :sp lab8_cons_modified.tcl (in vim)
		3) read_verilog lab8_circuit_modified.v 
		4) link
		5) source lab8_cons_modified.tcl
		6) compile_ultra
		7) report_timing -sig 4 -nosplit -trans -cap -input_pins -from IN_A > t1.rpt
		8) sh gvim t1.rpt

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210310738-5e7192ac-f009-40e6-8451-212e2bad2a51.png" width=55% height=55%>

<img src="https://user-images.githubusercontent.com/118953938/210313508-a220d862-73da-47ba-a7c7-8a80bffcb6f1.png" width=65% height=65%>

<img src="https://user-images.githubusercontent.com/118953938/210313378-fb6c3afe-1c41-4fdb-adc9-55dde9478549.png" width=65% height=65%>

1.2) Worst Delay

**Commands**

		1) report_timing -rise_from IN_A -sig 4 -transition_time -capacitance -input_pins > t2.rpt
		2) sh gvim t2.rpt
		3) :vsp DC_WORKSHOP/verilog_files/t1.rpt   
		
		1) report_timing -rise_from IN_A -sig 4 -transition_time -capacitance -input_pins > t2.rpt
		2) report_timing -rise_from IN_A -sig 4 -transition_time -capacitance -input_pins -to REGA_reg/D > t3.rpt
		3) sh gvim t1.rpt -O t3.rpt & 
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210318628-c7b38518-e4af-4842-901f-c2d6f4460bd9.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210318750-b11e3b59-4f23-4c3d-ba2d-7202c1b08358.png" width=75% height=75%>

1.3) Hold and Setup

**Commands**

		1) report_timing -delay min -from  IN_A
				
		Report timing through U15/Y
		1) report_timing -through U15/Y
		2) report_timing -delay min -through U15/Y

Report timing through U15/Y

![image](https://user-images.githubusercontent.com/118953938/210321903-d419f682-04b1-49ca-bfd0-727c94636968.png)

### :test_tube:	Lab 2 - Lab Check_timing, Check_design, Set_max_capacitance, HFN

2.1) Sourcing Constraints lab8_circuit_modified.v

**Commands**

		1) read_verilog lab8_circuit_modified.v
		2) link
		3) check_design
				
		PRE-sourcing Constraints
		1) compile_ultra
		2) check_timing 
		3) report_constraints
		
		Sourcing Constraints
		1) source lab8_cons_modified.tcl 
		2) check_timing
		3) report_constraints
		
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210373767-07ddc3f8-6710-476d-b6fc-545243704028.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/210375745-878503e2-be53-45f7-b777-746aa7b80d39.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210376589-903cbe45-eb0b-4974-83ea-0b9459ed5ad4.png" width=75% height=75%>

<img src="https://user-images.githubusercontent.com/118953938/210377171-ae285928-8b92-457b-b117-f270354a9cfc.png" width=75% height=75%>

2.2) New Design

**Commands**

		1) reset_design
		2) sh gvim mux_generate.v
		3) :sp mux_generate_128_1.v (in vim)
		4) read_verilog mux_generate_128_1.v
		5) link
		6) compile_ultra
		7) write -f verilog -out mux_generate_128_1_net.v
		8) sh gvim mux_generate_128_1_net.v &
		
		-> get_cells * -hier -filter "is_sequential == true"
		-> get_cells * -hier -filter "is_sequential == false"
		
		9) report_timing -net -cap -sig 4
		10) check_timing
		
		11) set_max_delay -from [all_inputs] -to [all_outputs] 3.5
		12) report_timing

**Output**

<img src="https://user-images.githubusercontent.com/118953938/210384244-b7368087-f605-437f-bc18-aacd6a74dccb.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/210384730-56c608f9-d68a-478e-a510-d0c10e82e8da.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210385574-1c04db92-4da9-452d-b968-d0d79fd59609.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210386121-55e80930-532f-4f9f-a3eb-2498099942c4.png" width=60% height=60%>

2.3) Max Capacitance

**Commands**

		1) set_max_capacitance 0.025 [current_design]
		2) report_constraint -all_violators
		3) compile_ultra
		4) check_timing 
		5) report_constraints
		6) report_timing
		7) report_timing -net -cap -sig 4

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210388352-634f419b-f09d-42a6-b886-6d214e62ca87.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210388554-35bb2676-c0a3-4563-8ee7-545b8e47f8f8.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/210389195-23865c12-2739-46ed-a3ef-c8b19caf4dd2.png" width=60% height=60%>

* The fanouts capacitance was limited and undergoes optimization 
* The max capacitance of 25ff, the fanouts will be splitted and buffered
* Everytime doing synthesis, the capacitance need to be limitedto avoid high fanout and nets can be buffered properly
* HFN = high fanout net

2.3) New design

**Commands**

		1) sh gvim en_128.v
		2) reset_design 
		3) read_verilog en_128.v
		4) link
		5) compile_ultra
		6) report_timing -from en -inp -nets -cap
		7) set_max_capacitance 0.03 [current_design] -->Breaking/buffering HFN
		8) report_constraints
		9) compile_ultra 
		10) report_timing -from en -inp -nets -cap -sig 4
		11) write -f ddc -out en_128.ddc
		
		Invoking design Vision
		1) design_vision
		2) read_ddc en_128.ddc
		3) start_gui

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210393040-065faada-06b4-4c69-8f3d-234ae60c1ebd.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210393498-68089354-8bb5-458e-89a8-9f8a5dadebdd.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210394454-2c4c0f04-2ccb-4764-ae02-b825d150e947.png" width=80% height=80%>

2.4) Setting the max transition

**Commands**

		1) report_timing -from en -nets -cap -sig 4 -trans
		2) set_max_transition 0.150 [current_design]
		3) report_constraints
		4) report_constraint -all_violators
		5) compile_ultra
		6) report_constraint -all_violators
		7) report_timing -inp -nets -cap -trans -sig 4 -nosplit
		8) report_timing -inp -nets -cap -trans -sig 4 -nosplit -from en -to y[116]
	
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210396058-00d07b61-b667-4004-99c0-35b5fd9aa435.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210396249-720e4d74-ba31-4da0-aca6-5f40fe990d8e.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/210396932-f14f7350-5d63-4146-b202-c2cbd36ad0ad.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210397385-3a414338-84df-4440-9388-8057a06e4594.png" width=50% height=50%>

</p>
</details>

<details><summary> :black_nib: Summary </summary>
<p>
	
### :mag_right: SUMMARY!!
		
:black_nib: **check_design**<br>
* *To ensure the quality of the design is proper, to check if the design is proper/not, or if there are any missing things in the design.*

:black_nib: **check_timing**<br>
* *To ensure all the proper constraints are in place.*

:black_nib: **report_constraints**<br>
* *To check what are the constraints we are checking. If there is any violation, it will report it.*

:black_nib: **set_max_capacitance & set_max_transition**<br>
* *To check if there is any high fanout net (HFN) or broken or is the design is buffered properly, so that there are no transition issues.*	
		
![image](https://user-images.githubusercontent.com/118953938/210400702-ea1ac6b5-7dc1-4938-b106-a8eebbe72597.png)

### :mag_right: Timing Model: ETM and QTM
		
* *Timing models are used to **provide accurate timing for various instances of the cells present in the design**.* 
* *The timing model normally obtained from detailed circuit simulation of the cell to model the actual scenario of the cell operation.*		
		
There are 2 types of timing model
	
	1) Extracted Timing Model (ETM)
	2) Quick Timing Model (QTM)
		
:black_nib: **Extracted Timing Model (ETM)**

	Block based model (.lib)
	Contents of block are hidden
	Original netlist replaced by model containing timing arcs for block interfaces
	These arcs are a function of input transition and output load
	Multiple modes per model
	Single PVT per model
	Used for implementation (not sign-off) of IP models
	
<img src="https://user-images.githubusercontent.com/118953938/210402744-31c07eac-27d7-46e8-b87c-5da1529a08b6.png" width=80% height=80%>

[The Source of the picture and info](http://www.pythonclub.org/vlsi/models/etm)
		
:black_nib: **Quick Timing Model (QTM)**		
		
If a block does not yet have a netlist throughout the design cycle, we may use a QTM to describe its initial time. To get more precise timing later in the cycle, we can swap out each QTM for a netlist block.		
		
[The Source info](http://www.pythonclub.org/vlsi/models/etm](http://mantravlsi.blogspot.com/2014/06/timing-models-etm-qtm-ilm.html)		

</p>
</details>

## :book: Day 11- Introduction to the VSDBabySoC
<details><summary> :mag_right: Theories </summary>
<p>
	
* It is a RISCV-based SoC (very small SoC)

	***RISC-V** is an open-source standard instruction set architecture (ISA) that is managed by the non-profit RISC-V Foundation.* 
	
* The primary goal --> to calibrate the analogue portion of it and test three open-source IP cores together for the first time.

### :mag_right: What is SoC and Why is SoC?

:black_nib: **System on chip (SoC)**	

A system on a chip, also known as an SoC, is essentially an integrated circuit or an IC that takes a single platform and integrates an entire electronic or computer system onto it.

* **The components** :  *SoC generally looks to incorporate within itself include a central processing unit, input and output ports, internal memory, as well as analog input and output blocks*
* Depending on the kind of system that has been reduced to the size of a chip, it can perform a variety of functions including signal processing, wireless communication, artificial intelligence and more.

:black_nib: **Why System on chip (SoC)?**

* SoC with equivalent functionality will have increased performance and reduced power consumption as well as a smaller semiconductor die area.
* SoC can reduce energy waste, save up on spending costs, as well as reduce the space occupied by large systems.
* Depending upon the requirement, it can also consists of a digital/analog signal processing system or a floating-point unit.

Example

<img src="https://user-images.githubusercontent.com/118953938/210487914-9f04193f-f1b6-4cda-ac30-c254ef8d5eb5.png" width=80% height=80%>

Qualcomm Snapdragon 600 APQ8064T
* A high-end SoC for mostly Android based smartphones and tablets
* The chip includes four ARMv7 compatible Krait-300 cores that offer a slightly improved architecture compared to the Krait cores in the S4 processors (according to Anandtech)

:black_nib: **Types of System on chip (SoC)**

In general, there are three distinguishable types of SoCs:

	1) SoCs built around a microcontroller,
	2) SoCs built around a microprocessor, often found in mobile phones;
	3) Specialized application-specific integrated circuit SoCs designed for specific applications that do not fit into the above two categories.

:black_nib: **System on chip (SoC) Structure**

* SoC consists of hardware functional units, including microprocessors that run software code, as well as communication subsystems to connect, control, direct and interface between these functional modules.
* Functional components: processor cores, memory, interfaces, digital signal processor (DSP), others.
* Intermodule communication**: bus-based communication, network on a chip.

:black_nib: **System on chip (SoC) Design Flow**

<img src="https://user-images.githubusercontent.com/118953938/210489732-fc8aebdd-192f-4066-ae01-ed5b0f0a2792.png" width=40% height=40%>

### :mag_right: What is BabySoc?

* BabySoc is a small yet powerful RISCV-based SoC.
* The main purpose of designing such a small SoC is to test three open-source IP cores together for the first time and calibrate the analog part of it.
* BabySoC contains one RVMYTH microprocessor, an 8x-PLL to generate a stable clock, and a 10-bit DAC to communicate with other analog devices.

<img src="https://user-images.githubusercontent.com/118953938/210490739-2b7664d7-bee4-488e-9657-5fdda309cfca.png" width=60% height=60%>

:black_nib: **How this chip were made?**

A Closer Look at How Microchips Are Produced

:black_nib: It Starts With Sand <br>
The starting point for silicon wafers is a special kind of sand that’s specifically mined before it’s heated and purified to produce a perfect cylinder of silicon. Once these cylinders are formed, they’re slicked into thin wafers and are polished.

:black_nib: Patterns Are Created<br>
The desired patterns on silicon wafers are created by applying a photosensitive chemical and shining UV light through a stencil. The patterns are required to construct the transistor layout’s structure that was designed by engineers for an integrated circuit (IC).Since wafers are large in size, photolithography or the process of shining UV light through the stencil must be performed multiple times.

:black_nib: Ions Bombard the Patterns<br>
Next, a special solvent is used to dissolve the photosensitive chemical’s exposed areas in the wafers. To change the patterns’ physical or electrical properties, they’re left exposed on the silicon before being bombarded by charged atoms or ions through the process of implantation.

[Source](https://www.waferworld.com/post/how-are-microchips-made)

:black_nib: **Baby SoC components**

**1) RVMYTH**
* RISC stands for Reduced instruction set computer
* RISC-V(pronounced “risk-five”) ISA is defined as a base integer ISA, which must be present in any implementation, plus optional extensions to the base ISA. 
	* Each base integer instruction set is characterized by the width of the integer registers and the corresponding size of the address space and by the number of integer registers. 
	* There are two primary base integer variants, RV32I and RV64I.
* RVMYTH: RVMYTH core is a simple RISCV-based CPU, introduced in a workshop by RedwoodEDA and VSD.
	* Reduced instruction set computer (RISC) - In computer engineering, a reduced instruction set computer is a computer designed to simplify the individual instructions given to the computer to accomplish tasks.
* As we mentioned in What is RVMYTH section, RVMYTH is designed and created by the TL-Verilog language. 
* So we need a way for compile and trasform it to the Verilog language and use the result in our SoC. Here the sandpiper-saas could help us do the job.

**2) Phase-locked loop (PLL)**
* Phase-locked loop (PLL): a control system that generates an output signal whose phase is related to the phase of an input signal. PLLs are widely used for synchronization purposes, including clock generation and distribution.

* Clock generation
	* The clocks supplied to these processors come from clock generator PLLs, which multiply a lower-frequency reference clock up to the operating frequency of the processor.

* Clock distribution
	* The reference clock enters the chip and drives a phase locked loop (PLL), which then drives the system's clock distribution. 
	* The clock distribution is usually balanced so that the clock arrives at every endpoint simultaneously.
	* One of those endpoints is the PLL's feedback input. 

**3) Digital-to-analog converter (DAC)**
* Digital-to-analog converter (DAC): a system that converts a digital signal into an analog signal. DACs are widely used in modern communication systems enabling the generation of digitally-defined transmission signals.

<img src="https://user-images.githubusercontent.com/118953938/210492646-fad99e55-9927-413c-99af-ac3fbd836da0.png" width=60% height=60%>

* A Digital to Analog Converter (DAC) consists of a number of binary inputs and a single output. 
* In general, the number of binary inputs of a DAC will be a power of two.

* Types of DACs
	* There are two types of DACs

		1) Weighted Resistor DAC
		2) R-2R Ladder DAC

</p>
</details>

## :book: Day 12 - BabySoC Modelling

<details><summary> :mag_right: Theories </summary>
<p>
	
### :mag_right: What does modelling mean?(electronics terminology)

<details><summary> Explainations </summary>
<p>
	
* Modeling and simulation is the use of aphysical or logicalrepresentation of a given system to generatedata and help determine decisions or make predictions about the system.
* Models are representations that can aid in defining, analyzing, and communicating a set of concepts.M&S is widely used in the VLSI domain.
* Purpose of modelling :
	* 1.System models are specifically developed to
		* support analysis, specification
		* design
		* verification
		* validation of a system,e.as well as to communicate certain information.
</p>
</details>

### :mag_right: What are we modelling?

<details><summary> Explainations </summary>
<p>
	
:black_nib: **VSDBabySoC modelling**

* Some initial input signals will be fed into vsdbabysoc module
* That will get the pll start generating the proper CLK for the circuit
* The clock signal will make the rvmyth to execute instructions and some values are generated, these values are used by DAC core to provide the final output signal named OUT
* So we have 3 main elements (IP cores) and a wrapper as an SoC and of-course there would be also a testbench module out there.

### :mag_right: IP cores

There will be 3 IP cores that will be modelled:<br>

	1. RVMYTH modelling
	2. PLL modelling
	3. DAC modelling 
	
:black_nib: **RVMYTH - Risc-V based MYTH**

* RISC stands for Reduced instruction set computer RISC-V(pronounced “risk-five”) 
* ISA is defined as a base integer ISA, which must be present in any implementation, plus optional extensions to the base ISA. Each base integer instruction set is characterized by the width of the integer registers and the corresponding size of the address space and by the number of integer registers. 
* There are two primary base integer variants, RV32I and RV64I

<img src="https://user-images.githubusercontent.com/118953938/211184620-52e4bcf7-5a86-4fb4-8e9d-e353a0c5220a.png" width=60% height=60%>

[SOURCE](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.chegg.com%2Fhomework-help%2Fquestions-and-answers%2Fsingle-cycle-risc-v-cpu-pc31-20-instr-31-12-shift-left-1-aluop-branch-memread-control-unit-q41204815&psig=AOvVaw3jn7tf0Pnd4BnER6_OVKmY&ust=1673247973997000&source=images&cd=vfe&ved=0CA4QjhxqFwoTCJjmqc20t_wCFQAAAAAdAAAAABAD)

RISC-V waterfall diagram and hazards

<img src="https://user-images.githubusercontent.com/118953938/211184726-68a643c7-e29c-4d28-92aa-50d882781ea8.png" width=60% height=60%>

[SOURCE](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.vlsisystemdesign.com%2Frisc-v-waterfall-diagram-and-hazards%2F&psig=AOvVaw3b-JtMyP5AvinUpu9CC1Az&ust=1673248099652000&source=images&cd=vfe&ved=0CA4QjhxqFwoTCPiEiIm1t_wCFQAAAAAdAAAAABAg)

:black_nib: **Phase Locked Loop**

* A phase-locked loop (PLL) is an electronic circuit with a voltage or voltage-driven oscillator that constantlyadjusts to match the frequency of an input signal.
* PLLs are used to generate, stabilize, modulate, demodulate etc

Why off-chip clocks can’t be used all the time?
* The clock will be a supplyfor a lot of blocks on the chip, it will have delays due to long wires(if used onlyone clock source) also reasons like clock jitter
* Some blocks might need 200Mhzs and some might need 100Mhz point is differentfrequencies just onone small chip
* A concept of ppm(clock accuracy) comes in, when ever quartz is acquired, it comes with a x ppm error

How is a clock generated?<br>
Ans: Quartz crystal oscillator

Components
* Phase detector
* Loop filte
* Voltage controlled oscillator
* Frequency divider 

<img src="https://user-images.githubusercontent.com/118953938/211184913-9d280749-2beb-4707-bbb1-9fb54bb08fe3.png" width=60% height=60%>

[SOURCE](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.analog.com%2Fen%2Fanalog-dialogue%2Farticles%2Fphase-locked-loop-pll-fundamentals.html&psig=AOvVaw2gRnFtO_9BzuuhZayqGYBT&ust=1673248611662000&source=images&cd=vfe&ved=0CA4QjhxqFwoTCMCKuv22t_wCFQAAAAAdAAAAABAD)

Many FPGAs use a phase-locked loop (PLL) to increase the internal clock speed. The iCE40 on the IceStick allows you to run up to 275 MHz by setting the internal PLL with the onboard 12 MHz reference clock. However, you will often find the higher clock speed increases the chances of glitches in your design.

:black_nib: **Digital-to-Analog Converter**

* A Digital to Analog Converter (DAC) converts a digital input signal into an analog output signal
* The digital signal is represented with a binary code, which is a combination of bits 0 and 1. A Digital to Analog Converter (DAC) consists of a number of binary inputs and a single output.

**Principle**<br>
Digital to analog conversions can be performed using resistor networks and the conversion to an analog signal is usually in the order of nanoseconds. Since the digital information is a step approximation of the input signal, the resulting output from a D to A converter reflects this step nature of the signal.

There are two types of DACs :
* Weighted Resistor DAC

	* A weighted resistor DAC produces an analog output, which is almost equal to the digital (binary) input by using binary weighted resistors in the inverting adder circuit. 
	* In short, a binary weighted resistor DAC is called as weighted resistor DAC.

	<img src="https://user-images.githubusercontent.com/118953938/211185227-29cc8d22-2c0c-4b58-ba20-19272759abdc.png" width=60% height=60%>

[SOURCE](https://www.google.com/url?sa=i&url=https%3A%2F%2Fmicrocontrollerslab.com%2Fbinary-weighted-resistor-dac-working-example-circuits-advantages%2F&psig=AOvVaw3FRSuZxttJipvh1U5KQNmT&ust=1673249168009000&source=images&cd=vfe&ved=0CA4QjhxqFwoTCMiSxIW5t_wCFQAAAAAdAAAAABAD)

* R-2R Ladder DAC

	* The ladder arrangement consists of two resistors i.e. a base resistor R and a 2R resistor which is twice the value of the base resistor. 
	* This feature helps to maintain a precise output analog signal without using a wide range of resistor values. 
	* A pair of R and 2R is used for one input bit.
	* The chief benefit of the R-2R DAC is that the number of resistors required to realize the design is much fewer than the string DAC.

	<img src="https://user-images.githubusercontent.com/118953938/211185317-56ec7063-983d-47ff-98f2-90addc593f57.png" width=60% height=60%>
	
[SOURCE](https://www.google.com/url?sa=i&url=https%3A%2F%2Fmicrocontrollerslab.com%2Fr-2r-ladder-dac-digital-to-analog-converter-working-examples-circuits%2F&psig=AOvVaw3Qqtev3EooD_m6qRj2f0Fm&ust=1673249337134000&source=images&cd=vfe&ved=0CA4QjhxqFwoTCMCzs9a5t_wCFQAAAAAdAAAAABAI)
</p>
</details>
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
### :test_tube:	Lab 1 - Modelling RVMYTH(RISC-V)

<details><summary> Reports </summary>
<p>
	
**Commands**

		Copy directory from git hub
		1) git clone https://github.com/kunalg123/rvmyth/
		
		2) cd rvmyth
		3) csh
		4) vcs mythcore_test.v tb_mythcore_test.v
		5) ./simv
		6) dve -full64 & 
		
		To edit the file (fixing errors)
		gvim mythcore_test.v -o tb_mythcore_test.v

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210913833-32ac7b24-3b7b-403d-b72c-7aaf1dacdbaf.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/210914540-3a2155f6-1fd8-4904-aa76-d21dcf7a7272.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/210915068-107f89c3-c833-41d7-a5fe-58ce70e6a6c3.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/210915304-5b2e7b4d-7fd8-49d5-ac09-bed75ea72f92.png" width=80% height=80%>

</p>
</details>

### :test_tube:	Lab 2 - Modelling DAC

<details><summary> Reports </summary>
<p>
	
**Commands**

		1) csh
		4) vcs avsddac.v avsddac_tb_test.v -sverilog
		5) ./simv
		6) dve -full64 & 
		
		To edit the file (fixing errors)
		gvim avsddac.v -o avsddac_tb_test.v

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210916319-1e3989b5-649c-4c4f-8b3f-f0a2db47478a.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210918080-c95a7c24-02f7-45d3-8498-0436c7e97dd4.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/210918552-0eb8a4e5-3dc2-4e03-9ae6-904c62792875.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/210919427-64e52d40-c3ef-4710-98cc-b967317cde4b.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/210944285-fa4b0ba3-24b0-4658-945b-6604fbc470e7.png" width=80% height=80%>

</p>
</details>

### :test_tube:	Lab 3 - Simulating in interactive mode(debug mode)

<details><summary> Reports </summary>
<p>
	
**Commands**

		1) csh
		2) vcs -lca -debug_access+all mythcore_test.v tb_mythcore_test.v -sverilog
		3) ../simv -gui &
				
		To edit the file (fixing errors)
		gvim mythcore_test.v -o tb_mythcore_test.v

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210945190-a34252e9-5e64-4b64-928b-d2dd89551883.png" width=80% height=80%>

![image](https://user-images.githubusercontent.com/118953938/210944922-110513a7-4add-49e6-872c-7c24d85b1cd3.png)

</p>
</details>

### :test_tube:	Lab 4 - Interface blocks together

<details><summary> Reports </summary>
<p>
	
4.1) PLL

**Commands**

		1) csh
		2) vcs rvmyth_pll.v rvmyth_pll_tb.v  -sverilog
		3) ./simv
		4) dve -full64 & 
				
		To edit the file (fixing errors)
		gvim rvmyth_pll.v -o rvmyth_pll_tb.v 

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210946583-d1360c0d-3e38-4e09-b96f-2909350bb9d0.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/210947037-3e02f45d-daef-41e9-9ef9-3c9d6258920b.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/210947345-79a3847f-60ad-42ea-a77c-f727d82d7f2d.png" width=80% height=80%>

4.2) DAC and RVMYTH

**Commands**

		1) csh
		2) vcs rvmyth_avsddac.v rvmyth_avsddac_TB.v -sverilog
		3) ./simv
		4) dve -full64 & 
				
		To edit the file (fixing errors)
		gvim rvmyth_avsddac.v -o rvmyth_avsddac_TB.v  

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/210948952-2baa76a5-9201-465c-95e8-1d8e4cc09e1d.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/211185424-82b1bb38-ad67-401f-9774-64d1a6684269.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/211185449-3e1d4fb4-d2ba-45d9-b9dc-1c06298650f0.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/211185482-bf60afb9-a3b9-44a8-9b3b-7c39b8968ae7.png" width=70% height=70%>

</p>
</details>

### :test_tube:	Lab 5 - babySoC

<details><summary> Reports </summary>
<p>
	
**Commands**
	
		1) csh
		2) vcs -sverilog vsdbabysoc.v testbench.v 
		3) ./simv
		4) dve  -full64 &
	
		Open file
		1) gvim vsdbabysoc.v -o testbench.v 
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/211261877-ddbd630a-8d6b-44ec-9819-8412ac9cecf8.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/211261990-f07e9f38-3d3e-40a1-8c1b-79331a496078.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/211262186-d182453a-e37b-4259-86eb-b66313d9e609.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/211262413-8ec3fb74-95dd-44e2-8995-74f10062c006.png" width=80% height=80%>

	
</p>
</details>

### :test_tube:	Lab 6 - TASK: 

<details><summary> Reports </summary>
<p>
	
6.1) Modes in interactive mode

<img src="https://user-images.githubusercontent.com/118953938/211207103-aa522ca9-ac61-42fb-8259-9ee9fed9731a.png" width=90% height=90%>

[SOURCE](https://picture.iczhiku.com/resource/eetop/WhKDeOKWsJfQibVv.pdf)

6.2) 4-1 mux

<img src="https://user-images.githubusercontent.com/118953938/211206226-9041ec2e-f8a1-411e-8407-55dbbf093a6e.png" width=80% height=80%>

**Commands**

		1) csh
		2) vcs 4-1mux.v tb_4-1mux.v_TB.v -sverilog
		3) ./simv
		4) dve -full64 & 
				
		To edit the file (fixing errors)
		gvim 4-1mux.v -o tb_4-1mux.v

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/211206374-0394aff7-24fb-4f0a-8359-a93282a998d9.png" width=70% height=70%>
Move both files to a new directory
	
<img src="https://user-images.githubusercontent.com/118953938/211229590-880de289-9bdc-48bb-8c17-321d01e99928.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/211229689-ed4623db-4b74-4bae-aa3b-b8b5fdbac564.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/211229779-5fceade5-3f7d-449c-8c54-7d6ad9508845.png" width=70% height=70%>
	


</p>
</details>
</p>
</details>

## :book: Day 13 - Post-synthesis simulation

<details><summary> :mag_right: Theories </summary>
<p>
	
### :mag_right: synthesizable and non- synthesizable constructs

<details><summary> Explainations </summary>
<p>

:black_nib: **Meaning**

Synthesizable statements- The statement which directly can be used to generate the Hardware called Synthesizable statements. Ex- A 3-input AND gate, A 32-bit output bus. Non-Synthesizable statements- The statements which can't make any hardware is known as Non-synthesizable.

:black_nib: **List of synthesizable and non-synthesizable Verilog constructs**

| Verilog Constructs  | Used for | Synthesizable construct | Non-synthesizable construct |
| ------------- | ------------- | ------------- | ------------- |
| module  | The code inside the module and the endmodule consists of the declarations and functionality of the design  | Yes  |  No  |
| Instantiation  |  If the module is synthesizable then the instantiation is also synthesizable  | Yes  |  No  |
| initial  | Used in the test benches  | No  |  Yes  |
| always  | Procedural block with the reg type assignment on LHS side. The block is sensitive to the events  | Yes  |  No  |
| assign  |  Continuous assignment with wire data type for modeling the combinational logic  | Yes  |  No  |
| primitives  | UDP’s are non-synthesizable whereas other Verilog primitives are synthesizable  | Yes  |  No  |
| force and release |These are used in test benches and non-synthesizable  |  No  |  Yes  |
| delays  | Used in the test benches and synthesis tool ignores the delays  | No  |  Yes  |
| fork and join  | Used during simulation  | No  |  Yes  |
| ports  | Used to indicate the direction, input, output and inout. The input is used at the top module  | Yes  |  No  |
| parameter  | Used to make the design more generic  | Yes  |  No  |
| time  | Not supported for the synthesis | No  |  Yes  |

[SOURCE](https://link.springer.com/content/pdf/bbm:978-81-322-2791-5/1.pdf)

</p>
</details>

### :mag_right: Why do pre-synthesis? Why not just do post-synthesis?
<details><summary> Explainations </summary>
<p>
	
:black_nib: ***Pre-synthesis simulation*** is done according to the logic you have designed for and written -> only functionality.

* The main purpose of pre-synthesis simulation is to verify the logical functionality of your design, without worrying about the specific timing details of a particular implementation.
* This saves a lot of time in the functional debugging cycle, since you don't need to wait for the synthesis process to complete before simulating again after making a change.
* Once you have the design working correctly with "nominal" or "unit" delays, you can then run the synthesis tools and verify that it continues to work with actual timing delays.
* Fixing the issues at this stage and dealing with long critical paths usually takes fewer iterations, which is good since each iteration takes longer.


:black_nib: ***Post synthesis simulation*** / ‘gate level simulation’ is done after synthesisconsidering each and every gate delays into account. reports the violations in both functionality and timing. 

* Designers perform functional simulation prior to synthesis. After synthesis, gate level simulation is performed on the netlist generated by synthesis.
* You can simulate a synthesized netlist to verify that the synthesized design meets the functional requirements and behaves as expected.
</p>
</details>

### :mag_right: Gate Level Simulation (GLS) (Post synthesis simulation)
<details><summary> Explainations </summary>
<p>
	
:black_nib: **Introduction**

* The term "gate level" refers to the netlist view of a circuit, usually produced by logic synthesis. 
* So while RTL simulation is pre-synthesis, GLS is post-synthesis. 
* The netlist view is a complete connection list consisting of gates and IP models with full functional and timing behavior. 
* RTL simulation is a zero delay environment and events generally occur on the active clock edge. 
* GLS can be zero delay also, but is more often used in unit delay or full timing mode. 

:black_nib: **Why is GLS simulation required?**

* Gate level simulation is used to boost the confidence regarding implementation of a design and can help verify dynamic circuit behaviour, which cannot be verified accurately by static methods.

</p>
</details>
	
### :mag_right: Timing Terminologies
<details><summary> Explainations </summary>
<p>
	
:black_nib: **Worst Negative Slack (WNS)**
* 
	
</p>
</details>
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>
	
### :test_tube:	Lab 1 - File conversion (convert .lib to .dc)	

<details><summary> Reports </summary>
<p>

1.1) Invoking lc_shell
	
**Commands**
	
		Cheetah environment
		1) mkdir /nfs/site/disks/zsc11_mip_xmphy_0021/users/wahabm
		2) Git clone https://github.com/manili/VSDBabySoC/tree/main/src/lib
		3)  set block = ddrphy
		4) setenv block ddrphy
		5) source /nfs/site/disks/zsc11_mip_xmphy_0002/proj_root_ulc/setup/setup_pv.csh $block
		6) /p/hdk/bin/cth_psetup -proj ip/2209sp3 -cfg IP78P3H180O12_22WW47 -cfg_ov /nfs/site/disks/ipg_da_00001/da/cth_overrides/sde_2209sp3_converged.cth -ward $PWD -verbose -x '$SETUP_R2G -force'
	
		Invoking lc_shell
		1) lc_shell

**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/211344568-1731b876-b948-4354-bc70-ec89aa8860aa.png" width=90% height=90%>

1.2) File conversion
	
**Commands**
	
		in lc_shell
		1) read_lib avsddac.lib
		2) write_lib avsddac -format db -output avsddac.db
	
		Edit file .db
		1) sh gvim avsddac.lib
			
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/211437182-b683d640-f826-4770-9456-237e376b709d.png" width=90% height=90%>

<img src="https://user-images.githubusercontent.com/118953938/211437416-8aa44056-cb8c-4147-a500-c119307daaeb.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/211437651-038792f4-78a8-4ec1-90b6-dbd7320e0d9b.png" width=90% height=90%>

</p>
</details>

### :test_tube:	Lab 2 - Pre-synthesis using DC	

2.1) Synthesize of rvmyth_avsddac.v

<details><summary> Reports </summary>
<p>
	
**Commands**
	
		in dc_shell
		Set the target library
		1) set target_library {/nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsddac.db}
     		2) set link_library {* /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsddac.db}
     		3) read_verilog rvmyth_avsddac.v
		4) write -f verilog -out avsddac_net.v 
	
		Edit the file
     		1) sh gvim rvmyth_avsddac.v
	
		Set as top module
		read_file {rvmyth_avsddac.v avsddac.v mythcore_test.v clk_gate.v} -autoread -format verilog -top rvmyth_avsddac
			
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/211440311-c78f7a13-0e2b-4ab7-95d6-33722e887651.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/211440704-4e3a08e1-46e4-423d-a5f8-b89e432edbb4.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/211866015-f13b065d-1091-4a1a-a386-faf040319870.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/211867466-0c1f0936-5578-47e9-878f-176702a12511.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/211867877-1331522f-1d5e-4074-b45d-c74569b4e2b1.png" width=50% height=50%>

2.1.1) Info check rvmyth_avsddac.v
	
**Commands**
	
		in dc_shell
		1) report_constraint
		2) check_design
		3) report_timing
		
**Outputs**
	
![image](https://user-images.githubusercontent.com/118953938/211869935-2443b353-ccd6-4171-b45c-cf8d46ce3cc0.png)

</p>
</details>
	
2.2) Synthesize of rvmyth_pll.v

<details><summary> Reports </summary>
<p>
	
**Commands**
	
		in dc_shell
		Set the target library
		1) set target_library {/nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsdpll.db}
     		2) set link_library {* /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsdpll.db}
     		3) read_verilog avsd_pll_1v8.v
		4) write -f verilog -out rvmyth_avsdpll_net.v 
	
		Edit the file
     		1) sh gvim avsd_pll_1v8.v
	
		Set as top module
		read_file {avsd_pll_1v8.v mythcore_test.v clk_gate.v rvmyth_pll.v} -autoread -format verilog -top rvmyth_pll_interface
			
**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/211877215-b9138944-0c25-4c49-927a-9fae5a7396f6.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/211877660-3e9691cf-44d4-4ee9-958d-f14dc5230ca0.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/211877962-51fe2b26-bfb8-4432-b696-93bf79e248a1.png" width=80% height=80%>
	
2.1.1) Info check rvmyth_avsdpll.v
	
**Commands**
	
		in dc_shell
		1) report_constraint
		2) check_design
		3) report_timing
		
**Outputs**
	
![image](https://user-images.githubusercontent.com/118953938/211878249-73e242b2-4407-4230-9f6c-b424a93935c6.png)
	
</p>
</details>
</p>
</details>

## :book: Day 14 - Synopsys DC and timing analysis

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Process,Voltage andTemperature (PVT)
<details><summary> Explainations </summary>
<p>

* Process variations are caused by changes in manufacturing conditions such as temperature, pressure, and dopant concentrations. Deviations in the semiconductor fabrication process are accounted for by this variance.
* Integrated circuits are designed in such away that they can function in a wide variety of temperatures and voltages,rather than a single temperature and voltage.

:triangular_flag_on_post: Fun facts

How is PVT data measured?<br>
*Gammadot measures PvT behaviour using a high pressure indirect dilatometry system developed by Rapra Technology Ltd. The technique employs a stainless steel bellows test cell with Mercury as the containing fluid. Volume changes related to changes in temperature & pressure are monitored via a displacement transducer.*
		
:black_nib: **Process**
	
* Variations in the process parameters can be impurity concentration densities, oxide thicknesses and diffusion depths. 
* These are caused bye non uniform conditions during depositions and/or during diffusions of the impurities. 
* This introduces variations in the sheet resistance and transistor parameters such as threshold voltage. 
* Variations are in the dimensions of the devices, mainly resulting from the limited resolution of the photolithographic process. This causes (W/L) variations in MOS transistors.

<img src="https://user-images.githubusercontent.com/118953938/211741306-84024c07-c479-4e2b-893b-756bd0d6de36.png" width=30% height=30%>

:black_nib: **Voltage**	
	
* As we are going to the lower nodes the supply voltage for a chip is also going to less. 
* Let’s say the chip is operating at 1.2V. So, there are chances that at certain instances of time this voltage may vary. It can go to 1.5V or 0.8V. To take care of this scenario, we consider voltage variation.

	* There are multiple reasons for voltage variation.
		* IR drop is caused by the current flow over the power grid network. 
		* Supply noise caused by parasitic inductance in combination with resistance and capacitance. when the current is flowing through parasitic inductance (L) it will causes the voltage bounce.
	
<img src="https://user-images.githubusercontent.com/118953938/211746572-dbc141d8-75e1-4399-a80d-4dcf54402000.png" width=30% height=30%>
	
:black_nib: **Temperature**
	
* Effects on performance caused by temperature fluctuations are most often handled as linear scaling effects, but some submicron silicon processes require nonlinear calculations.
* This is due to the power dissipation in the MOS-transistors. 
* The power consumption is mainly due to switching, short-circuit and leakage power consumption.
	
<img src="https://user-images.githubusercontent.com/118953938/211745176-3c4ee097-8f92-4ced-9e20-93457da5d717.png" width=30% height=30%><br>

<img src="https://user-images.githubusercontent.com/118953938/211747176-47c8d9d6-3407-4b7d-8d50-22b340abf1e6.png" width=30% height=30%>
	
[SOURCE](https://www.idc-online.com/technical_references/pdfs/electrical_engineering/Process_Voltage_Temperature_PVT_Variations_and_Static_Timing_Analysis.pdf)	

</p>
</details>
	
### :mag_right: Timing Terminologies
<details><summary> Explainations </summary>
<p>

:black_nib: **Worst Negative Slack (WNS)**
* Negative slack means the design has not achieved the specified timings at the specified frequency. 
* WNS is the worst timing violations that happened in the timing reports
* Slack has to be positive always and negative slack indicates a violation in timing.
	
:black_nib: **Worst Negative Slack (WNS)**
	
	
</p>
</details>	
</p>
</details>

<details><summary> :test_tube:	Labs </summary>
<p>

### :test_tube:	Task 1 - Converting .lib to .db	

<details><summary> Reports </summary>
<p>	

<img src="https://user-images.githubusercontent.com/118953938/220514256-f2333db0-ac2c-4bdc-ac2a-7e7a1f084c17.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/220513032-55b4fda7-9c82-4ece-af26-1fea96ab023d.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/220513547-b518146d-a182-43c4-9bd0-165c1fa3faab.png" width=70% height=70%>

**'.db' files were created**

<img src="https://user-images.githubusercontent.com/118953938/220515060-4cc4787f-1527-4877-afd8-f7705a53d7f2.png" width=70% height=70%>

</p>
</details>

### :test_tube:	Task 2 - Timing libs for different PVT corners	

<details><summary> Reports </summary>
<p>

**Commands**

		In dc_shell
		-read_file {mythcore_test.v avsd_pll_1v8.v avsddac.v clk_gate.v vsdbabysoc.v} -autoread -format verilog -top vsdbabysoc
		-set target_library {/nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/timing_libs/sky130_fd_sc_hd__ff_100C_1v65.db /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db}
	
		Changing target and link library
		-set link_library {* /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/timing_libs/sky130_fd_sc_hd__ff_100C_1v65.db /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsddac.db /nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/VLSI/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/rvmyth/avsdpll.db}

		To check if clock exist
		-get_clocks 
		
		Constraints
		-source cons.tcl 

		Checking clock reports
		-report_clocks 

		-link

		-compile

		Slack report
		-report_timing 

		To retrieve the WNS WHS THS
		-report_qor 

**Outputs**

<img src="https://user-images.githubusercontent.com/118953938/220521705-9d7a66ec-edbb-4aab-83df-454a8cd9fcc7.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/220522211-1f182cac-9102-4467-93d8-dd0ee1d6dc51.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/220522399-0c7cab74-85f3-4fdc-ac01-d5f6a23cb3d8.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/220522619-245ff7d6-79a1-4929-9399-47ed947b09b8.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/220523141-01d7d7a9-04c3-4b22-a4be-ef6b8467dc1e.png" width=70% height=70%>

**Generated Table**

<img src="https://user-images.githubusercontent.com/118953938/220524313-04c246d7-13d8-455c-8d2a-e7f928455340.png" width=50% height=50%>





</p>
</details>
</p>
</details>

## :book: Day 15 - Inception of open-source EDA, OpenLANE and Sky130 PDK

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: SKY130_D1_SK1 - How to talk to computers

:black_nib: **Introduction to QFN-48 Package, chip, pads, core, die and IPs**

<details><summary> Explainations </summary>
<p>

Understanding chips and terminilogies
	
<img src="https://user-images.githubusercontent.com/118953938/212225635-92f919b2-a523-4288-815a-e58f1d837fba.png" width=80% height=80%>

A microcontroller board based on the ATmega32U4 and comes with 23 digital input/output pins. It is developed by Arduino.cc, aiming to provide easy to use interface with the ability to perform a number of functions on a single chip. 

<img src="https://user-images.githubusercontent.com/118953938/212234321-d3aabbb6-8983-4ac7-bba4-cfaf53b3ef22.png" width=80% height=80%>
	
For more infomation, can go through REPO day-0. Link as below:
	
https://github.com/azrulhakimwahab/sd-training/edit/main/Readme.md#book-day-0-systemtool-setup-check-github-id-creation


</p>
</details>

:black_nib: **Introduction to RISC-V**

<details><summary> Explainations </summary>
<p>

What is RISC-V(Five)?
	
* RISC-V (“risk-five”) is an instruction set architecture (ISA) rooted in reduced instruction set computer (RISC) principles. 
* RISC-V is unique, even revolutionary, because it is a common, free, open-source ISA to which software can be ported, hardware can be developed, and processors can be built to support it.
* Open-source nature of RISC-V is crucial because it allows smaller developers and manufacturers to design and build hardware without the cost of licensing proprietary ISAs and paying royalties. As a result, companies of all sizes can innovate and create, putting the best products on the market for the advancement of the industry and benefit of the consumer.
	
<img src="https://user-images.githubusercontent.com/118953938/212253748-bd16166f-8524-4f03-8ec1-d6723e501cbd.png" width=80% height=80%>	
	
</p>
</details>

:black_nib: **From Software Applications to Hardware**

<details><summary> Explainations </summary>
<p>

![image](https://user-images.githubusercontent.com/118953938/212256478-3aeaa2a3-c237-46a7-bb77-c2d6686e7692.png)

![image](https://user-images.githubusercontent.com/118953938/212259976-4b80a87e-95ae-47b4-8e0a-1e43916a6430.png)

:green_circle: **Operating system (OS)** is system software that manages computer hardware, software resources, and provides common services for computer programs.	

:green_circle: **Instruction Set Architecture (ISA)** is part of the abstract model of a computer that defines how the CPU is controlled by the software. The ISA acts as an interface between the hardware and the software, specifying both what the processor is capable of doing as well as how it gets done.
	
Fun fact<br>
:green_circle: How does software get into hardware?<br>
*Software is stored in the hardware as magnetic domains on the hard drive or floppy disc, or as low and high voltages in computer chips. When you type on a keyboard, each character is converted into an electrical series of 0's and 1's which are then stored as low and high voltages in the computer chips called RAM.*

There are 3 parts of the design 
	
	Part 1 : RISC-V Instruction Set Architecture
	Part 2 : RTL and Synthesis of RISC-V based CPU core -pcorv32
	Part 3 : Physical Design Implimentation of pcorv32
</p>
</details>

### :mag_right: SKY130_D1_SK2 - SoC design and OpenLANE

:black_nib: **Introduction to all components of open-source digital asic design**

<details><summary> Explainations </summary>
<p>

Open Source Digital ASIC Design

![image](https://user-images.githubusercontent.com/118953938/212275017-ede9f6f3-ac2d-416e-8e8c-12c06f34fc60.png)
	
OpenLane 
* is an automated RTL to GDSII flow based on several components including OpenROAD, Yosys, Magic, Netgen, CVC, SPEF-Extractor, KLayout and a number of custom scripts for design exploration and optimization. The flow performs all ASIC implementation steps from RTL all the way down to GDSII.	
	
</p>
</details>

:black_nib: **Simplified RTL2GDS flow**

<details><summary> Explainations </summary>
<p>

<img src="https://user-images.githubusercontent.com/118953938/212336302-7a97e14c-4bc6-4193-b364-211b827cce06.png" width=80% height=80%>
	
:green_circle: Synthesis: 
* Converts RTL design to a circuit out of the components from standard cell library(SCL).
* Standard cells have regular layout. each cell has different views/models. For eg: Liberty View-This include power and delay models

:green_circle: Floor and Power Planning: 
* Plan the silicon area and robust power distribution to power the circuits. 
* Chip Floor Planning: Partition the chip die between different system building blocks and place the I\O Pads. 
* Macro-Floor Planning:Dimensions, pin-locations,rows and routing tracks are defined. 
* Power network is constucted where chip is power by multiple Vdd and Groung Pins.
* These pins ar connected to components through vertical and horizontal metal straps.These use upper metal layers which are wider and have lower resistance

:green_circle: Placement: 
* Place the cells on the floor plan rows, aligned with the sites.
* Closer cells should be placed adjacent to reduce interconnect delay 
	* There are 2 types of placement: 
		* Global Placement- Find optimal posiiton for all cellsand these are not legal so cells may overlap. 
		* Detailed Placement-The detials obtained from Global Placement are minimally altered

:green_circle: Clock Tree Synthesis: 
* Clock Tree Synthesis (CTS) is the technique of balancing the clock delay to all clock inputs by inserting buffers/inverters along the clock routes of an ASIC design
* To deliver clock to all sequential circuis (eg;FFs) -With minimum skew-Can be ensured by H-Tree or X-tree

:green_circle: Routing:
* Implement interconnect using metal layers.
* This requires to enquire a valid horizontal and vertical patterns to implement the nets. 
* PDK defies the thickess, pitch, width of the metal layer and also the vias required to connect different metal layers.
	
:green_circle: Sign Off:
* Sign off is a process of logical and physical verification of the chip.
* Physical Verifications
	* Design Rules Checking (DRC)
	* Layout vs. Schematic
* Timing Verification
	* Static Timing Analysis

</p>
</details>
	
	
:black_nib: **Introduction to OpenLANE and Strive chipsets**

<details><summary> Explainations </summary>
<p>

**OpenLANE**<br>
*OpenLane is an open-source VLSI flow built around open-source tools. That is, it's a collection of scripts that run these tools, in the right order, transforming their inputs and outputs as appropriate, and organising the results (like Berkeley's own HAMMER.)*
* Started as an Open-Source Flow for a True Open Source Tape-out Experiment 
* A family of SOCs called striVe (Open PDK, Open EDA, Open RTL)

<img src="https://user-images.githubusercontent.com/118953938/212344661-3b7097eb-97be-48a6-8300-af8fb3271f3a.png" width=50% height=50%>

The Main Goal of the OpenLANE are:
* Produce a clean GDSII with no human intervention (no-human-in-the-loop)
	* What does 'Clean' means:
		* no LVS violations
		* no DRC violations
		* no Timing Violations

Other Informations:
* Tuned/Used for SkyWater130nm Open PDK and also, supports XFAB180 and GF130G
* Containerized
	* Means functional out of the box
	* Instructions to build and run natively will follow
* Can be used to harden (generate GDSII on the final layout) Macros and Chips
	* 2 modes of operations:
		* Autonomous = push button flow (figure the flow, time based on the design side and back to the GDS tool)
		* Interactive = run commands and steps one by one (can do experimentation and check results)
* Design Space Exploration:
	* Find the best set of flow configurations
* Large number of design examples
	* 43 designs with their best configurations
	* More designs will be added soon	
		
</p>
</details>	
	
:black_nib: **Introduction to OpenLANE detailed ASIC design flow**

<details><summary> Explainations </summary>
<p>	

The flow, depicted below, consists of several highly customizable stages. In the initial stage the RTL source files written in an HDL (Hardware Description Language) are synthesized, technology mapped and analyzed in terms of timing. In the following step the floorplan and power distribution network are prepared for the design placement. Once finished, the design and clock placement is performed followed by global routing. With the physical layout ready in the form of a DEF (Design Exchange Format) file, it’s possible to perform several DRC checks, including Antenna Net or LVS (Layout vs. Schematic), to eventually generate the final GDSII layout file which contains a complete layout description that is now ready to be sent to the foundry.
	
<img src="https://user-images.githubusercontent.com/118953938/212360183-528e067e-69fd-42c0-a279-361b679da3fa.png" width=80% height=80%>
	
1) Synthesis exploration
* Synthesis exploration utility is used to generate report that shows the design delay and area.

2) DFT 
DFT will do these synthesis
* Scan Insertion-to increase the overall testability of a circuit.
* Automatic Test Pattern Generation (ATPG)-Scan facilitates the pattern-generating process for detecting the previously described defects.
* Fault Coverage-percentage of some type of fault that can be detected during the test of any engineered system. 
* Fault Simulation-evaluates how a digital circuit will behave in the presence of manufacturing defects.

<img src="https://user-images.githubusercontent.com/118953938/212448524-0cdf4f21-b976-4166-b26f-b252a4fd4c34.png" width=50% height=50%>

3) Physical implementation (Place and Route)

Using OpenRoad open source to perform the implementation. It will involves these steps:

	1) Floor/Power Planning
	2) End Decoupling Capacitors and Tap cells insertion
	3) Placement: Global and Detailed
	4) Post placement optimization
	5) Clock Tree Synthesis (CTS)- > Post Placement optimization modifies the netlist
	6) Routing: Global and Detailed
	

4) Logic Equivalent Check (LEC) 

* Logic equivalence checking (LEC) looks at the combinatorial structure of the design to determine if the structure of two alternative implementations will exhibit the same behavior. 
* If operations such as retiming are applied to a design, the structure of the design will no long map between the two representations.
* is used to formally confirm that the function did not change after modifying the netlist.
* Yosys is used as the Open source application.

5) Dealing with Antenna Rules Violations

* Antenna Diodes Insertion is the name of a particular action used during physical implementation. 
* This step is required for antenna worst violations. 
* When a long enough length of metal wire is created, it can function as an antenna.

	* **Diode Insertion**: *Diode helps dissipate charges accumulated on metal. Diode should be placed as near as possible to the gate of device on low level of metal.*
	
Reactive ion etching causes charge to accumulate on the wire
Transistor gates can be damaged during fabrication
Solutions

Bridging attaches a higher layer intermediary (Requires router awareness)
Add antenna diode cell to leak away charges (Antenna diodes are provided by SCL)
	
How do you fix antenna violations in physical design?
* Techniques to fix the antenna violations as follows:
	* Routing on Higher Metal Layer: Long metal can be taken to higher metal routing layer. This is known as metal jumping. ...
	* Reduce the via-area: Large via area also results in process antenna violation. ...
	* Diode Insertion: Diode helps dissipate charges accumulated on metal.
</p>
</details>	
</p>
</details>	

<details><summary> :test_tube: Labs </summary>
<p>
	
### :test_tube:	Lab 1 - Pre-synthesis using DC	

1.1) Opening directories and checking files

<details><summary> Reports </summary>
<p>

**Commands**
	
		1) cd <filename>
		2) ls <filename> or
		3) ls -ltr
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/212522889-1b527474-30dc-4d16-a9b1-3f61c2ec4dee.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212523400-871bfd04-4439-430d-860c-4e18a7f290a0.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/212523487-6b6d263a-ba48-431f-b4f9-3f0ca572e49f.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212523529-14f2dda2-aed8-46a8-89f2-583b61213cff.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/212523567-023e1038-2048-46ed-ad4a-e9dc71dc3fb9.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212523785-d23c4494-0d65-44c6-9c08-68b16556605d.png" width=70% height=70%>

	
</p>
</details>		
	
### :test_tube:	Lab 2 - Design Preparation Step	

2.1) Invoking openlane

<details><summary> Reports </summary>
<p>
	
**Commands**

<img src="https://user-images.githubusercontent.com/118953938/212528648-9b0c0c6b-2cd4-436f-b039-ffb192657d8b.png" width=70% height=70%>

SOURCE- https://github.com/nickson-jose/openlane_build_script

		1) cd work/tools/openlane_working_dir/openlane
		2) make mount
		3) pwd
		4) ls -ltr
		5) ./flow.tcl -interactive
		6) package require openlane 0.9
		7) prep -design picorv32a
	
**Outputs**
	
![image](https://user-images.githubusercontent.com/118953938/212528209-96c943aa-4e44-451d-b455-ccf3d8172b4a.png)

<img src="https://user-images.githubusercontent.com/118953938/212528225-8583418e-a2ab-410b-bb21-d4b74149ae70.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212528238-2ca7fe9b-5eaf-4438-90f4-07cba09eb2e7.png" width=70% height=70%>

</p>
</details>
	
2.2) Priority files

<details><summary> Reports </summary>
<p>

**Commands**
	
		1) cd /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
		2) ls
		3) vim <filename>
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/212528388-d26786db-52e3-44f3-b0e7-717bdecbd792.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212528417-c6e8ab31-c681-4082-b84f-d000a48b0ace.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212528756-73bee193-31be-4f2d-81e8-e6f2b2192cf0.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212528809-7126104a-a5bb-4985-bae4-4eaaf28a647e.png" width=70% height=70%>

</p>
</details>
	
### :test_tube:	Lab 3 - Review files after design prep and run synthesis
	
3.1) Rev files

<details><summary> Reports </summary>
<p>

**Commands**
	
		1) cd /Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-01_14-09
		2) ls
		3) vim <filename>
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/212529419-84d800fb-9507-4e43-8cd9-b5b27149ad70.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/212529585-957db0f8-994f-4e9d-9303-27b1d127487d.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212529609-0b36a1ae-346a-4db8-bdd5-45118ee143dd.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/212529627-4967709a-2f82-462d-ba3e-29d48ac711d2.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/212530047-e41d1005-7dcc-4479-a0ce-588ab1362407.png" width=70% height=70%>
	
</p>
</details>	

### :test_tube:	Lab 4 - OpenLANE Project Git Link Description
	
<details><summary> Reports </summary>
<p>	
	
For more information, can refer the following link:
https://github.com/efabless/OpenLane
	
**Content**
	
Command line arguments<br>
https://github.com/efabless/OpenLane#command-line-arguments
	
OpenLane Architecture<br>
https://github.com/efabless/OpenLane#openlane-architecture
	
<img src="https://user-images.githubusercontent.com/118953938/212541315-da4d3937-c7cb-4069-899c-44496210abb8.png" width=70% height=70%>
<img src="https://user-images.githubusercontent.com/118953938/212541342-e65dff1b-a6d4-4da1-bba9-f9a4f45461f8.png" width=70% height=70%>
<img src="https://user-images.githubusercontent.com/118953938/212541359-fd5930dc-1746-4dac-99d7-f2a3846c85b4.png" width=70% height=70%>

Key opensource
	
<img src="https://user-images.githubusercontent.com/118953938/212541460-a6096b6b-b59a-4a50-a92b-b0d27811b7a8.png" width=70% height=70%>

</p>
</details>	

### :test_tube:	Lab 5 - OpenLANE Project Git Link Description

5.1) Finding flop ratio
	
<details><summary> Reports </summary>
<p>	

From already ran synthesis
	
<img src="https://user-images.githubusercontent.com/118953938/212531597-745d05d8-4ffe-4b7e-b2f4-244112372a32.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/212541013-1900cad9-b295-4d3d-b18e-385852347989.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/212541102-bd8ae998-edb2-4e30-8669-f44b6d160ed2.png" width=80% height=80%>

</p>
</details>	
</p>
</details>	
		
## :book: Day 16 - Good floorplan vs bad floorplan and introduction to library cells

<details><summary> :mag_right: Theories </summary>
<p>

Floorplanning involves determining the locations, shape, size of modules in a chip and as such it estimates the chip area, delay and the wiring congestion, thereby providing a ground work for layout.
	
### :mag_right: Chip Floor planning considerations	

:black_nib: **Utilization factor and aspect ratio**
	
<details><summary> Explainations </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/213098271-0d02f281-1b92-4045-81d8-e17f467ceac0.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213188526-b0f12ce3-af5f-450c-88bb-ea4ad5f2ecaa.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213191891-abfbe533-803d-4f47-a497-1e331cda737f.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213192156-34dcefaf-bf84-4d6a-8f15-4f6ceda19181.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213194524-108256e2-957b-4afb-8529-74789cd17d87.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213201947-7b3dc6ad-2bb8-404e-a2c3-80f7f32fa915.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213201348-58d57b6d-e734-48f2-a1a0-fafaba804f50.png" width=80% height=80%>


</p>
</details>	

:black_nib: **Concept of pre-placed cells**	

<details><summary> Explainations </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/213205957-ae1d54a4-c0d3-4143-9424-22f4ed70d035.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213210356-a5fc6d0b-8289-431f-86d1-d999a44c6375.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213212402-f9a103f8-194c-41df-b09c-26578b64365b.png" width=80% height=80%>

* Need to cut the block accordingly
* Extend those IO pins of the two blocks and detached those blocks with the black boxes
* The side viewing from the top/main netlist will thus be unable to see those two blocks. We will now divide the black boxes into two distinct IP addresses or modules since those portions of the boxes are no longer accessible to the top netlist that we have built.
* Separating such blocks has the benefit of making it easier to utilise them repeatedly when necessary with other users, where they will be constructed individually based on their functionality. 
* Additionally, those blocks can each be utilised independently numerous times as needed.
	
<img src="https://user-images.githubusercontent.com/118953938/213330315-b01bafd0-312c-49c5-ba6c-b4ca49f0390d.png" width=80% height=80%>

Reusing existing implementations eliminates the requirement for new ones (instantiated multiple times onto the netlist)	
	
<img src="https://user-images.githubusercontent.com/118953938/213336552-d3fb457a-b6c3-406f-b58a-25280771ec9b.png" width=80% height=80%>

* The arrangement of these IP's in a chip is referred as Floorplanning
* These IP's/blocks have user-defined locations, and hence are placed in chip before automated placement-and-routing and are called as pre-placed cells
* Automated placement and routing tools places the remaining logical cells in the design onto chip

<img src="https://user-images.githubusercontent.com/118953938/213337624-78d79f14-4f8c-4cc8-993c-0c2315e44685.png" width=80% height=80%>

</p>
</details>
	
:black_nib: **De-coupling capacitors**	

<details><summary> Explainations </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/213339124-e61c2458-e020-478d-868d-bee3aa9b4530.png" width=80% height=80%>
	
	1) Consider capacitance to be zero for the discussion. Rdd, Rss, Ldd and Lss are well defined values.
	2) During switching operation, the circuit demands switching current i.e. peak current (Ipeak).
	3) Now, due to the presence of Rdd and Ldd, there will be a voltage drop across them and the voltage at Node 'A' would be Vdd' instead of Vdd.
	
<img src="https://user-images.githubusercontent.com/118953938/213339622-38356baa-36d9-4838-9fc8-b6f3c0177875.png" width=80% height=80%>

If Vdd' goes below the noise margin, due to Rdd and Ldd, the logic '1' at the output of circuit won't be detected as logic '1' at the input of the circuit following this circuit.	
	
**Noise Margin Summary**
	
<img src="https://user-images.githubusercontent.com/118953938/213342153-e6d07688-e03a-4eee-a29c-f9d0faa331fc.png" width=80% height=80%>

* The noise margin is the amount by which the signal exceeds the threshold for a proper '0' or '1'. 
* For example, a digital circuit might be designed to swing between 0.0 and 1.2 volts, with anything below 0.2 volts considered a '0', and anything above 1.0 volts considered a '1'. 
* Then the noise margin for a '0' would be the amount that a signal is below 0.2 volts, and the noise margin for a '1' would be the amount by which a signal exceeds 1.0 volt. In this case noise margins are measured as an absolute voltage, not a ratio. Noise margins for CMOS chips are usually much greater than those for TTL because the VOH min is closer to the power supply voltage and VOL max is closer to zero.
* Everything in between Vol and Vll is regarded as logic 0. Any voltage between Vll and Vih will be regarded as being in the undefined range.
* Logic can be shifted from logic 1 to logic 0 or from the interception point of (b) to logic 0 in the region that is not specified. Undefined area is dangerous in this instance.
* When a voltage is between two points, Vih and Voh, it is always regarded as 1V, or logic 1.
* Since it is impossible to tell if a voltage is in logic 1 or not, we must make sure that it didn't reach an undefined zone.
* That is the issue when there is a significant physical distance between the circuit and the primary power supply.
	
<img src="https://user-images.githubusercontent.com/118953938/213343521-5cbae7b3-3f3e-4740-aa98-5f322143fa9b.png" width=80% height=80%>

* Decoupling capacitors must be added to address this problem.
* Consider that the decoupling capacitor is a large capacitor that is fully charged, and that the equivalent voltage across it is similar to that of the power supply. Circuit add the decoupling capacitor in parallel.
* The circuit would be uncoupled from the main supply via a decoupling capacitor. The circuit pulls electricity from Cd each time it changes. While the RL network is utilised to recharge the Cd
	
<img src="https://user-images.githubusercontent.com/118953938/213344217-41ce7b87-f617-4b02-8cc5-85e0b48372af.png" width=80% height=80%>
		
</p>
</details>
	
:black_nib: **Power planning**	

<details><summary> Explainations </summary>
<p>	

Power planning means to provide power to the every macros, standard cells, and all other cells are present in the design. Power and Ground nets are usually laid out on the metal layers. In this create power and ground structure for both IO pads and core logic.
	
<img src="https://user-images.githubusercontent.com/118953938/213348226-5d22c57c-1281-477b-962d-4ea92f280fa8.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213352535-b44a85b3-70e2-47b5-ab23-500327cb2073.png" width=80% height=80%>
	
* Imagine there are four distinct macros or blocks that typically come with varied functionality in a whole chip and contain drivers, loads, and other components.
* For four blocks, the power source was available. As a result, it will be difficult to instal all of the decoupling capacitors since the supply from the source will not be steady.
* Consider if the orange line was a 16-bit bus. Logic 0 will discharge to Ground while logic 1 signals that the capacitor is being charged to Vdd.
* The inverter is linked to this 16-bit bus, causing the output to be the opposite of the input. Logic 1 will be turned off, and logic 0 will be charged in its place.	

<img src="https://user-images.githubusercontent.com/118953938/213354219-6faa5e42-56d0-447d-9a0e-2fd02489ed89.png" width=80% height=80%>

* Through a single Ground tap point, all capacitors that were charged to volts will be discharged to 0 volts. Ground tap point will bounce as a result of this.
* The voltage may shift from logic 1 to logic 0 at that time, which is unexpected, if this bounce surpasses the noise margin threshold and reaches an undefinable state.
* Through a single Vdd tap point, all capacitors that were at "0" volts must be charged to "V" volts. This will result in a decrease in voltage at the Vdd tap point.
* Due to the simultaneous operation of several tap sites, the degree of Ground Bounce and Voltage Droop will rise.	
	
<img src="https://user-images.githubusercontent.com/118953938/213354603-eb7a8eac-0578-4151-81cf-b0039585b8b5.png" width=80% height=80%>

It may reach the undefined state if the magnitude of the ground boundary or voltage droop exceeds the noise margin level. The issue is that there is only one point of supply (single source).
	
<img src="https://user-images.githubusercontent.com/118953938/213354967-3b97a5c6-857a-41db-9b01-991c07172859.png" width=80% height=80%>

Instead of using only one power supply, we must **employ several power supplies (i.e., multiple Vdd and Vss) to resolve this problem**. The closest block will get many power sources, ensuring that it receives the power supply in time. As a result, every logic will use the closest power source. The load and the driver can also be brought near to one another in the "L" sense.
	
</p>
</details>	
	
:black_nib: **Pin placement and logical cell placement blockage**	

<details><summary> Explainations </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/213367410-316a1f81-9a31-45a9-97c8-dcb00d2180aa.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213367876-02b695bf-68c8-4414-907c-a40b8c12269a.png" width=80% height=80%>

**Pin placement**
	
<img src="https://user-images.githubusercontent.com/118953938/213368400-4efe942e-83c5-444c-ac82-e6efd2ea896a.png" width=80% height=80%>
	
* The input port is configured to be on the LHS of the design plan, while the output port is set to be on the RHS.
* The placement of input and output ports is unpredictable since it depends on our design strategy. Depending on the blocks, the pins are put. Blocks A, B, and C cannot have any cells or flip flips placed there.
* Since the clock is the port that is controlling all the cells and transmitting the signals to all flip flops, the clock ports, which are CLK1, CLK2, and Clkout, are larger than data ports.
* The less resistance, the larger the size.
	
<img src="https://user-images.githubusercontent.com/118953938/213368828-75afd081-f522-4b36-8e34-ae8f53930ae6.png" width=80% height=80%>

</p>
</details>	
	
### :mag_right: Library Binding and Placement	

:black_nib: **Netlist binding and initial place design**
	
<details><summary> Explainations </summary>
<p>	

<img src="https://user-images.githubusercontent.com/118953938/213372616-2943d14f-acc3-4c90-b1dc-70905ba76f05.png" width=80% height=80%>

The AND gate, inverter, and other conventional shapes will be used for combinational logic gates. However, the combinational logic gate will actually be modified into a box. The physical dimension will replace the physical gate. As a result, all of the gates will be altered as shown in the image.
	
<img src="https://user-images.githubusercontent.com/118953938/213377755-38b4151d-9a6b-4818-97ae-a5906fe48907.png" width=80% height=80%>
	
* The library can also be divided into sub-libraries, with the first library simply including delay information in the second library while the first contains shape and size.
* Depending on the time circumstances and the spaces that are available in the layout, the library offers a variety of possibilities inside the same cell. 
* The resistance decreases as cell size increases.	
	
<img src="https://user-images.githubusercontent.com/118953938/213383920-d7232fa8-ebbd-4164-b687-52cc23939aff.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213384199-38790394-9a32-400a-9ed4-b23f3de4730e.png" width=80% height=80%>

* The floorplan's arrangements are chosen by taking the connections between the physical cells—that is, the positions that are closest to inputs and outputs—into account.
* Make sure that no cells are introduced during the placement step that might cause the black boxes and decap cells to overlap. To avoid making the routing too lengthy, placement must also take timing into consideration.
	
</p>
</details>	
		
:black_nib: **Optimize placement using estimated wire-length and capacitance**
	
<details><summary> Explainations </summary>
<p>		

**What is Placement Optimization?**<br>
*Optimization is the process of iterating through a design such that it meets timing, area and power specifications. The design must satisfy these multiple design objectives.*

Goals of Placement:
* Timing, Power and Area optimizations.
* Minimum congestion.
* Minimal cell density, pin density and congestion hot-spots.
* Minimal timing DRVs.
	
<img src="https://user-images.githubusercontent.com/118953938/213386348-781cc34f-d5b4-41a1-9980-e28302cbbbec.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213388172-0cc2c74e-d954-42ae-b8df-58f8c6a08706.png" width=80% height=80%>
	
* Let's use Din2 to FF1 in the figure as an example to illustrate how various estimations are used to optimise.
* As we can see, the path from Din2 to FF1 would result in the worst possible data slew (long distance), as larger capacitance causes the amount needed to charge the capacitance to increase (transition).
	
<img src="https://user-images.githubusercontent.com/118953938/213387861-df9dc91a-34d6-42ce-befa-dd8a7450872a.png" width=80% height=80%>

* The repeaters are installed based on the wire length and capacitance that are estimated prior to routing.
* In this situation, a buffer is inserted (to reduce capacitance) and serves as repeaters, reconditioning the signals and creating new signals or duplicating the signal distortion-free. More repeaters would result in some data loss.	
	
</p>
</details>	
	
:black_nib: **Final placement optimization**
	
<details><summary> Explainations </summary>
<p>	
	
<img src="https://user-images.githubusercontent.com/118953938/213390106-642ec500-fcfe-4283-bd4b-98d9d64313cd.png" width=80% height=80%>

* Due to the duration of the signal transmission, buffers are introduced. For instance, because of the excessive distance between FF1 and Din4, we require repeaters to recondition the signal and deliver it to FF1.
* The length from FF1 to 1 is enough, but since we will be crossing other FF and a buffer, we must create it on a distinct layer.
* There is a significant distance between 1 and 2. So, we think about adding the buffer. The lesser the delay, the closer the gate and FF are near one another.
* Additionally, we must examine the timing setup to see whether or not our placement is suitable and to determine whether or not the parameters have been satisfied.

<img src="https://user-images.githubusercontent.com/118953938/213390581-0da3c6a7-8971-462c-a43c-2de624d033bb.png" width=80% height=80%>

</p>
</details>	
	
:black_nib: **Need for libraries and characterization**
	
<details><summary> Explainations </summary>
<p>	
		
**Library characterization and modelling**
	
<img src="https://user-images.githubusercontent.com/118953938/213393481-c6a4c6b3-0abc-46aa-8329-cbf6afced796.png" width=80% height=80%>

One thing in common to all of the stages
	
**Gates or Cells**<br>
Library	<br>
* AND Gate
* Or Gate
* Buffer
* Inverter
* DFF
* Latch
* ICG
* etc
	
</p>
</details>		

### :mag_right: Cell design and characterization flows	

:black_nib: **Inputs for cell design flow**
	
<details><summary> Explainations </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/213402326-4ab2ff29-b689-45d8-aa03-83d70889150d.png" width=80% height=80%>

* All of our standard cells and other collateral are kept in the library. 
* A library has many features in various shapes and sizes. Additionally, it has standard cells with various threshold voltages.
	
<img src="https://user-images.githubusercontent.com/118953938/213403189-40af80e4-8b64-4b98-9784-1cd9bbc0f429.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213404351-77355b27-b7ec-4d0d-b3fd-86b9509b1ed8.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213405109-e518b833-b99a-4af8-a439-f6ce0b010a6b.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213405643-737b694c-6456-4298-ac2d-3c91ba276c8e.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213477335-247180b2-01da-4a65-a7c3-07e1997c745c.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213477398-f4a28fab-c9d5-4770-9a5c-0ab4b19257c2.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213477466-50835244-5e73-4446-a254-8085d17e67c8.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213477540-01f5c2ca-a9a1-406c-8569-23942a54e6c7.png" width=80% height=80%>

</p>
</details>	

:black_nib: **Circuit Design Step**
	
<details><summary> Explainations </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/213473528-9c49d17c-3273-451d-ab2b-1bfaecf2a830.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213479466-d93b1726-4eac-44cf-a89f-83b93b105f6f.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213479681-b3e1dd0a-f832-409c-8def-29da4389a1f2.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213481005-f1e34d25-9e14-41b9-933a-ab85337cf0d0.png" width=30% height=30%>

</p>
</details>	
	
:black_nib: **Layout design step**
	
<details><summary> Explainations </summary>
<p>	
	
<img src="https://user-images.githubusercontent.com/118953938/213482433-b1e48319-2a3c-4026-81f2-a060f22ba2a4.png" width=80% height=80%>
	
* Identify Euler's path when it is a single-trace path where the function carried by by a mos transistor (pmos and nmos)
* Then draw a stick diagram. The generated stick diagram must next be transformed into an appropriate layout in accordance with the guidelines in the pdks and design characterization from earlier phases.
* The tool, such as magic open source tool, will then be used to insert the finished layout design.
* The design's output would be in the form of an extracted spice netlist, GDSII, and LEF. The last stage is characterising the design to determine its purpose, power.libs, and timing noise.
	
<img src="https://user-images.githubusercontent.com/118953938/213486209-e19634a8-5df5-48d8-8f5a-0ba76be58b0f.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213486513-de4b3f5a-2fc2-4615-8d73-5a8fd403353b.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213487664-5b224249-231d-42c0-86ac-0e62554846ea.png" width=80% height=80%>

	
</p>
</details>	
	
:black_nib: **Typical characterization flow**
	
<details><summary> Explainations </summary>
<p>	
	
<img src="https://user-images.githubusercontent.com/118953938/213491413-f6f521f3-1ad5-43b1-a38f-7b59358d21c2.png" width=80% height=80%>
	
1) Review the models and the tech file from the layout
2) Review the extracted spice netlist
3) Define or recognize the behaviour of the buffer
4) Review the subcircuit of the inverter
5) Attach the necessary power sources
6) Apply the stimulus
7) Provide the necessary the output load capacitance
8) Provide the necessary simulation command	
	
<img src="https://user-images.githubusercontent.com/118953938/213492000-b95d1760-aa37-48b6-8eaa-46503f144d44.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213492431-7f87930b-cb54-4292-89e9-53e5f278f9d9.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213492951-e88b64ed-1e01-417d-8a17-5cd66a142743.png" width=80% height=80%>
		
</p>
</details>		
	
### :mag_right: General timing characterization parameters	

:black_nib: **Timing threshold definitions**
	
<details><summary> Explainations </summary>
<p>
	
**Timing Treshold**

:pushpin: Slew Treshold
	
<img src="https://user-images.githubusercontent.com/118953938/213496343-e48ead8f-0381-478a-b914-24d804f10c01.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213496958-c1e9c13c-8786-4fa7-b115-f3ecb7fafdd9.png" width=80% height=80%>

:paperclip: **Slew Low rise**: <br>
* Describes the power supply's lowest condition (0V), which is nearer to zero. Usually, 20% of the bottom power supply is used. To compute the slew, however, we also need to know the slew high increase threshold.
	
:paperclip: **Slew High rise**: <br>
* The normal figure is 20% or so from the top of the power supply. Take the temporal difference between the two variables to get the degree of slew.
	
:pushpin: In and Out Treshold	
	
<img src="https://user-images.githubusercontent.com/118953938/213499383-e30ede90-c7ea-47ae-acd4-53a3e444f693.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213499962-5c4032e9-e605-45ba-961f-3ee66d69ae9f.png" width=80% height=80%>

:paperclip: **In rise threshold**: <br>
* A point in the output waveform where the delay can be determined, and a threshold for the delay up to 50% of the slew waveform on the ideal waveform.
	
:paperclip: **Out rise threshold**: <br>
* The output rising waveform, at which 50% of the delay can be calculated.	

</p>
</details>	
	
:black_nib: **Propagation delay and transition time**
	
<details><summary> Explainations </summary>
<p>
	
The propagation delay times are defined as the time delay between the 50% crossing of the input and the corresponding 50% crossing of the output. The rise time and the fall time of the output signal are defined as the time required for the voltage to change from its 10% level to its 90% level (or vice versa).
	
What causes propagation delay?<br>
*Propagation delay typically refers to the rise time or fall time in logic gates. This is the time it takes for a logic gate to change its output state based on a change in the input state. It occurs due to inherent capacitance in the logic gate.*
	
It is preferable for the propagation delay to be positive rather than negative. Hence, the threshold point must be carefully adjusted.
	
<img src="https://user-images.githubusercontent.com/118953938/213504315-c88dc567-def0-4aae-b7bc-12aadf4de68f.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/213505167-5191add2-c939-4309-876d-63c049ba8150.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213505982-051378f2-769a-470b-8f49-ee96c387de0b.png" width=80% height=80%>

* The input appears to have a significant wire delay, producing a massive slew (red line). 
* This might be as a result of the two inverters being situated far away from one another. 
* The design of the circuit is particularly crucial since it might result in a negative delay even when the threshold points have been chosen correctly.
	
<img src="https://user-images.githubusercontent.com/118953938/213507709-dac68748-018f-41d9-88b5-d35999c35461.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/213509653-2eb11927-9b77-4a6e-9ead-9a888aff4cdd.png" width=80% height=80%>


</p>
</details>	
	
</p>
</details>		
	
<details><summary> :test_tube: Labs </summary>
<p>
	
### :test_tube:	Lab 1 - Chip Floor planning considerations	

1.1) Steps to run floorplan using OpenLANE

<details><summary> Reports </summary>
<p>

**Commands**
	
		1) cd Desktop/work/tools/openlane_working_dir/openlane/configuration
		2) vim README.md
		3) cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a
		4) vim config.tcl
	
		in the openlane
		1) run_floorplan
	
**Outputs**	

<img src="https://user-images.githubusercontent.com/118953938/213515933-aab8a0f9-c5fc-42e2-8ab2-efb493d91ca5.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213516759-01843866-e179-48aa-a057-ac8a1ae71513.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213517090-6bf0501b-0445-4842-89c5-fcc48b978d4e.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213517560-0b7037ad-eda1-43b2-9112-e1433ba92440.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213518190-5b798793-e7fa-4cf7-b52f-a13d97905b9d.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213518440-bdc6a8c7-a57c-411f-9098-649ec2c49df8.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213518948-b4cf411f-d2df-4382-aeaf-70d59ed9be54.png" width=80% height=80%>
		
</p>
</details>		

1.2) Review floorplan files and steps to view floorplan

<details><summary> Reports </summary>
<p>

**Commands**
	
		1) cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-01_08-16/logs/floorplan
		2) vim 4-ioPlacer.log
		3) cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-01_08-16
		4) vim config.tcl
		5) cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-01_08-16/results/floorplan
		6) vim picorv32a.floorplan.def
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/213522322-6b4b69d9-5480-4026-90a1-480ef0e1cf86.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213522586-b6d597ff-2969-4c79-b1ea-fd275f598e16.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213522691-23729a21-6843-4458-ae49-694855b9c580.png" width=80% height=80%>
	
</p>
</details>		
	
1.3) Review floorplan layout in Magic

<details><summary> Reports </summary>
<p>	

**Commands**
	
		1) magic -T ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
		2) 'S' key = Select
		3) 'V' key = Zoom to fit
		4) %what = Knowing the cell's information 
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/213529432-3233bc0d-0afd-41b9-8d70-5d12cb0a1233.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213530052-3e34baa7-e942-4760-9f4f-31b9e8179cc8.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213530155-f9ac8a8e-4e6b-4848-aaea-2e654558a1f0.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213530232-222efdcd-c1de-4903-b64e-8498d76ec57d.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213530325-31d9359a-10dd-435b-9bbb-4d28f46fa75f.png" width=80% height=80%>

</p>
</details>	
	
### :test_tube:	Lab 2 - Library Binding and Placement	

2.1) Congestion aware placement using RePlAce

<details><summary> Reports </summary>
<p>

:pushpin: Global Placement

* No legalisation is taking place
	* Reducing wire length

:pushpin: Detail Placement

* There is legalisation (more on timing point of view)
	* Standard cells are placed inside the rows and no overlaps
	
	
**Commands**
	
		In openlane
		1) run_placement
	
		in Terminal
		1) cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/15-01_08-16/results/placement
		2) magic -T ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &

			
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/213534358-e4098b94-b814-416b-8e08-fe64521e0d08.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213534546-edfdb6c2-7647-4b76-a65d-16c9aa94a8e5.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/213534653-29c31efe-7ef5-4d78-b29a-0504ee8a2803.png" width=80% height=80%>
	
	
	
	
</p>
</details>	
</p>
</details>	

[BACK TO DAY 16](https://github.com/azrulhakimwahab/sd-training/blob/main/Readme.md#book-day-16---good-floorplan-vs-bad-floorplan-and-introduction-to-library-cells)<br>
[BACK TO TOP](https://github.com/azrulhakimwahab/sd-training/blob/main/Readme.md#book-my-respository)
	
## :book: Day 17 - Design library cell using Magic Layout and ngspice characterization

<details><summary> :mag_right: Theories </summary>
<p>
	
### :mag_right: CMOS inverter ngspice simulations	

:black_nib: **SPICE deck creation for CMOS inverter**
	
<details><summary> Explainations </summary>
<p>

**SPICE deck**
* A SPICE input file is known as a “spice deck” or simply “deck” because, at one time, several such files would be printed on cards and the whole 'deck' of cards would then be fed into the computer *
	
1) Component Conectivity	
* Having the conectivity information of the netlist 
* It also has a tap points 
	
1.1) Create a SPICE DECK
* Create a SPICE DECK on a compleated netlist containg P-MOS and N-MOS
	* Why? - need to define the connectivity of substrate 
	
<img src="https://user-images.githubusercontent.com/118953938/214565347-ceed9977-2678-485f-b115-878de8befe74.png" width=40% height=40%>
	
2) Component Value	
* Setting up the channel/components values
	
2.1) Need to define the value of channel length and load capacitance
* Ideally, the P-mos shoud be twice or trice bigger than the N-mos	

<img src="https://user-images.githubusercontent.com/118953938/214566998-d5eae0eb-4355-4ce9-8019-d33002dde133.png" width=40% height=40%>
	
2.2) Defining the value of input and supply voltage	
	
<img src="https://user-images.githubusercontent.com/118953938/214567662-47ddb2fc-3e10-4f2b-94b5-3c051f4fcc1f.png" width=40% height=40%>
	
3) Identify 'nodes'
* NODES = a node is any region on a circuit between two circuit elements
	
<img src="https://user-images.githubusercontent.com/118953938/214569573-799ad35b-dcf3-4083-86ee-86c725008f4f.png" width=40% height=40%>
	
4) Naming the 'nodes'
* naming the nodes to make it easier to identify
	
<img src="https://user-images.githubusercontent.com/118953938/214570298-d1ac61ad-4908-44e9-b3ab-052c5afd47ed.png" width=40% height=40%>

**Writing a SPICE deck**	

**P-MOS Transistor**
	
<img src="https://user-images.githubusercontent.com/118953938/214571898-71af92f0-f857-4d5c-9179-8c628e5cfac3.png" width=80% height=80%>

**N-MOS Transistor**
	
<img src="https://user-images.githubusercontent.com/118953938/214573776-bcb0fb15-97e1-4285-babf-cc8ef3fb04e4.png" width=80% height=80%>

**Simulation Commands**

<img src="https://user-images.githubusercontent.com/118953938/214574860-97215913-5bdd-4824-9958-f7df2a254017.png" width=80% height=80%>

</p>
</details>

:black_nib: **SPICE simulation lab for CMOS inverter**
	
<details><summary> Explainations </summary>
<p>	

<img src="https://user-images.githubusercontent.com/118953938/214584062-057aad98-b48d-4191-83a2-55292331b2d5.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214584104-e08a1fdd-a887-4cc7-8b1f-966570f7ff4d.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/214585412-14012cca-1719-4f37-a106-9fb7d7698046.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/214586620-af7abd68-0c81-4745-8273-d99d813f2f62.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/214587656-e8fa0454-14c0-4518-b6bb-7ff8e1b679e1.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214588925-085c2d4c-a3f3-452f-a2e4-375f8fcc3972.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214590462-c60a8d06-a1b8-4a46-a9bf-e39014117684.png" width=80% height=80%>

</p>
</details>

:black_nib: **Switching Threshold Vm**
	
<details><summary> Explainations </summary>
<p>		
	
The switching threshold of VM can be obtained from the VTC graph where Vin=Vout. At this point, both transistors are in the saturation region. By ignoring channel modulation, we can equate the transistor currents.
	
<img src="https://user-images.githubusercontent.com/118953938/214592145-9903b596-5597-4330-a5c8-3c5e6f610db2.png" width=80% height=80%>

At the interception
* Pmos and Nmos are in the sturation region where it will 'On' 
* Leads to a probability of having leakage current from power to ground
	
<img src="https://user-images.githubusercontent.com/118953938/214593700-483fb82d-dfe5-448f-8e48-64280cf2ba27.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214594632-147f187f-6588-4dac-911e-b0d7cec8f922.png" width=80% height=80%>

</p>
</details>	

:black_nib: **Static and dynamic simulation of CMOS inverter**
	
<details><summary> Explainations </summary>
<p>		
	
<img src="https://user-images.githubusercontent.com/118953938/214597480-9a01856d-dda2-4678-b7ef-1300a4f514e6.png" width=80% height=80%>
	
* Going to supply the pulse into the CMOS and see what is the output

<img src="https://user-images.githubusercontent.com/118953938/214601913-018e9635-78aa-411a-aa4f-1267bbf3d20d.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214601775-daae415e-bbc6-4085-930d-b1707a8b07e3.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214602794-78320959-0660-4bfb-9c2d-d4f116f352a6.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214604164-7ab189cf-f04b-4e80-b978-f9bf0f6d4530.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214606250-0d9bda34-c16f-4450-80f9-34976d8b601b.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214605570-ce5b2052-7017-4859-b0e1-3d6f87ce22d9.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214605982-a70288e3-a2ed-49b9-8bcc-c5246fe96349.png" width=80% height=80%>


</p>
</details>	
	
### :mag_right:  Inception of Layout CMOS fabrication process

:black_nib: **Create Active regions**
	
<details><summary> Explainations </summary>
<p>	
	
**16-MASK CMOS Process**
	
1) Selecting a substrate
* Doping process: the process of adding impurities to intrinsic semiconductors to alter their properties
	
<img src="https://user-images.githubusercontent.com/118953938/214608133-d5f8b343-e200-40b3-9d39-7d3f0d83c537.png" width=50% height=50%>
	
2) Creating active region for transistors
* Will be having pockets as the active region 
	
Steps<br>
2.1) Create isolation between the pockets by adding a layer of silicon dioxide<br>
	
2.2) Addition of nitrate active elements<br>
	
2.3) Defining the pocket region by depositing a layer of photoresist<br>

<img src="https://user-images.githubusercontent.com/118953938/214725183-91658ba3-e59b-4432-9d4b-33abe4c2bdee.png" width=50% height=50%>

2.4) Masking = When fabrication and masking processes are carried out, photoresist will generate a mask and shield the layout from chemical reactions if UV light is used.<br>	
	
<img src="https://user-images.githubusercontent.com/118953938/214727729-3b31d46a-0d31-4432-a92c-3def038219c5.png" width=50% height=50%>
<img src="https://user-images.githubusercontent.com/118953938/214728571-79f054fd-2808-4f0e-9ce5-7fad91a43734.png" width=70% height=70%>
	
2.5) Removing the mask. Only the exposed area will be affected by any chemical reactions or deposition/etching processes.<br>
	
2.6) Only the region behind the protective layer will be protected during the silicon nitrate etch, with the rest area being removed.<br>

<img src="https://user-images.githubusercontent.com/118953938/214732706-c9a6735e-c20f-4b36-ae41-2b7eb4391060.png" width=80% height=80%>

2.7) Remove the Silicon nitrate using phosphoric acid	
	
<img src="https://user-images.githubusercontent.com/118953938/214733252-46ef6ca4-b9e0-4256-a4fb-28671d0c9d4e.png" width=70% height=70%>
	
</p>
</details>	
	
:black_nib: **Formation of N-well and P-well**
	
<details><summary> Explainations </summary>
<p>		

3) Formation of N-well and P-well

N-well = P-MOS application <br>
P-well = N-MOS application<br>
	
Steps<br>
3.1) Deposit a layer of photoresist and define which layer that would be protected
	
<img src="https://user-images.githubusercontent.com/118953938/214736338-886055c0-7949-47de-b863-524dfb07cd94.png" width=70% height=70%>
	
3.2) The UV light will expose the photoresist, and only the exposed portion of the photoresist will respond to the UV light while the shielded area remains unchanged and does not.	
	
<img src="https://user-images.githubusercontent.com/118953938/214737542-af3a79d6-c21c-404b-84e1-a6c9e7781bb4.png" width=70% height=70%>

3.3)The mask is taken off, and a p-well is created by introducing Boron (a p-type material), which diffuses into the substrate via the oxide layer.<br>
	
3.4) The procedure for creating an N-well is the same as that for creating a P-well, except that an N-well employs phosphorus (a substance of the n-type) to implant or diffuse into the substrate at a 400 keV energy level.<br>
	
<img src="https://user-images.githubusercontent.com/118953938/214747816-5e8885a5-73c5-4e7b-9cb8-21dccc504b44.png" width=80% height=80%>
	
3.5) After the N- and P-wells have developed completely, we must disperse the well to ensure that it takes up at least half of the substrate area. As a result, we can fabricate pmos and nmos in a room that is clear. Place the entire substrate, including the N- and P-wells, in a driving furnace set to a high temperature of roughly 100°C for 4-6 hours. <br>
	
3.6) As a result, a clear well will be formed by driving in and diffusing boron and phosphorus into the substrate. While P-well produces nmos transistors, N-well produces pmos transistors.	<br>
	
3.7) Add the substrate into a high temperature furnace
	
<img src="https://user-images.githubusercontent.com/118953938/214748920-1b73b309-7aa5-440e-84ae-97f00f51e1f7.png" width=80% height=80%>
	
</p>
</details>		
	
:black_nib: **Formation of gate terminal**
	
<details><summary> Explainations </summary>
<p>			
	
4) Formation of gate
	
The most important part of the N-MOS and P-MOS transistor
	
**Refreshment on Circuit design and SPICE simulation**
	
![image](https://user-images.githubusercontent.com/118953938/214750781-5d07cf3d-a9f6-4f76-9e6e-05a7bc4d89ef.png)
	
Steps

4.1) Mask 4 is used to regulate and maintain the substrate's doping concentrations.
	
4.2) The remaining steps remain the same as previously mentioned. Therefore, the remaining phases of the procedure will be repeated.

4.3) Then add Mask 5 to the P-well and proceed similarly for the pmos. The rest of the pmos procedure must be carried out, as well as controlling the threshold voltage of pmos. Arsenic and phosphorus can be employed to keep the substrate's energy level low while diffusing into it.
	
![image](https://user-images.githubusercontent.com/118953938/214751785-41cba0d2-bf05-4c1e-a06e-0ab83ae7fd04.png)
	
4.4) As a result of the implantation operation, the oxide has to be fixed. Hydrofluoric (HF) acid can be used to remove the oxide as part of the fixing procedure. 
	
4.5) When a polysilicon layer is deposited using the deposition process, a thick polysilicon layer will develop where the gate area is intended to have a low resistance.
	
![image](https://user-images.githubusercontent.com/118953938/214752386-bfe0781c-31ae-4b33-815b-b9e156b818ec.png)

4.6) Since the gate has a low resistance, we must dope it with additional impurities, such as phosphorus and arsenic, and spread them across the entire polysilicon layer in order to have low sheet resistance in addition to low gate resistance. Use Mask6 as a polysilicon gate mask.
	
<img src="https://user-images.githubusercontent.com/118953938/214752880-830b226b-34c4-42c1-aa45-8ac3286072b0.png" width=80% height=80%>
	
**TOP VIEW OF THE DESIGN**
	
<img src="https://user-images.githubusercontent.com/118953938/214753122-a24601c5-2864-4572-846e-39c8cda3582d.png" width=60% height=60%>

4.7) Mask 6 may now be removed, and the remaining polysilicon that is outside of the photoresist can be etched out of it to make the polysilicon gate.
	
![image](https://user-images.githubusercontent.com/118953938/214753737-445f8092-53bd-4c1a-9032-6fd67a86ea1d.png)

</p>
</details>	
	
:black_nib: **Lightly doped drain (LDD) formation**
	
<details><summary> Explainations </summary>
<p>	
	
A Lightly Doped Drain (LDD) structure is known to be very effective in preventing hot electrons in modern NMOS transistors. 
	
Modern MOSFETs often incorporate a lightly-doped drain (LDD) region. Due to the presence of the LDD region, these so called LDD MOSFETs have a smaller electric field near the drain region and therefore a reduced hot-carrier effect over the conventional MOSFET
	
5) Lightly doped drain (LDD) formation	
	
**Two dopping profiles**
	
* Hot electron effect
	1) Electric field E=V/d
	2) High energy carriers break Si-Si bonds
	3) 3.2eV barrier b/w Si conduction band
	4) SiO2 conduction band

* short channel efect
	1) For short channels, drain field penetrates channel	
	
<img src="https://user-images.githubusercontent.com/118953938/214754739-4d127d07-cfb8-4fbc-b9c5-d92ff5d571a7.png" width=70% height=70%>
	
Steps
	
5.1) The process began by adding Mask 7 to protect the appropriate region based on the gate generated in the previous session, and the other photolithography stages are the same.
	
5.2) However, we must execute the ion implantation operation by doping it with phosphorus in order to build the nmos at P-well (N-type material)
	
![image](https://user-images.githubusercontent.com/118953938/214755325-8b2c520e-21ca-4b43-9f30-f4afca07dc38.png)

5.3) Create Mask 8, then proceed with the other stages. Next, ion implantation is achieved by doping with Boron to prevent the emergence of additional sources and drains, create some space around the gate.
	
![image](https://user-images.githubusercontent.com/118953938/214759944-b2438065-94c2-4335-92b8-59aa091eb663.png)

5.4) Etching using anisotropic plasma. The side-wall spacers will be produced by the etching.	
	
![image](https://user-images.githubusercontent.com/118953938/214760297-17fb0ab5-5fed-4f2b-b56b-17390489a1d3.png)
	
</p>
</details>	
	
:black_nib: **Source and drain formation**
	
<details><summary> Explainations </summary>
<p>	
	
* Source: Source is the terminal through which the majority charge carriers are entered in the FET. 
* Drain: Drain is the terminal through which the majority charge carriers exit from the FET. 
* Gate: The gate terminal is formed by diffusion of an N-type semiconductor with a P-type semiconductor.	

6) Source and drain formation	
	
Steps
	
6.1) In order to prevent channel link from accessing the substrate, add a thin coating of screen oxide.

6.2) Add Mask 9, then resume the photolithography process as beforeand expose the structure to arsenic using energy of 75 keV.
	
![image](https://user-images.githubusercontent.com/118953938/214761759-a0c2dcd7-d159-4dfe-a65a-b8e10464a691.png)

6.3) Photolithography is performed once Mask10 is added.

6.4) Use Boron and ion implantation with 50 oeV of energy. The result will be P+ P- N.
	
6.5) Place into a high-temperature furnace to anneal at a high temperature and further penetrate the N- and P-wells.
	
![image](https://user-images.githubusercontent.com/118953938/214762086-ee6acf13-625d-4ddc-bd86-2912bc81c184.png)
	
</p>
</details>	
	
:black_nib: **Local interconnect formation**
	
<details><summary> Explainations </summary>
<p>	
	
7) Local interconnect formation
	
STeps
	
7.1) To make room for the drain, source, and gate area for constructing contact, remove the thin screen oxide.

7.2) In a solution of hydrofluoric acid, etch the thin oxide.

7.3) Titanium/wafer surface may be deposited using sputtering.
	
<img src="https://user-images.githubusercontent.com/118953938/214762963-91c38f65-c2bf-4784-885b-0a59960dab08.png" width=60% height=60%>
	
7.4) By heating the wafer in a nitrogen environment, you may make contact with the Titanium that has been deposited.
	
7.5) Titanium nitrate is utilised for local communication, whereas the heating procedure created low resistance titanium silicon dioxide that may be used for local connection.	
	
<img src="https://user-images.githubusercontent.com/118953938/214763787-dbc2ecf0-f609-4457-bc28-90d60f2b2ec7.png" width=90% height=90%>
	
7.6) Repeat the lithography procedure, adding Mask 11. In order to clean the RCA, then remove Mask 11 and etch any excess Titanium nitrate.

7.7) Interconnects made of local Titanium Nitrate were applied to link locally and raise to the top.	

![image](https://user-images.githubusercontent.com/118953938/214764634-0e8dd11b-ac66-4092-a71e-403c5983bf04.png)

</p>
</details>	
	
:black_nib: **Higher level metal formation**
	
<details><summary> Explainations </summary>
<p>		

8) Higher level metal formation

8.1) The non-linear surface topography makes it unsuitable for metal interaction.
	
8.2) A thick layer of silicon dioxide doped with boron and phosphorus will be placed to correct it. When it comes to protecting against mobile sodium ions, phosphorus will operate as a barrier, while boron will lower the surface's temperature, polish it, and create a flat surface.

<img src="https://user-images.githubusercontent.com/118953938/214765369-339ab9c0-98c3-4b14-9129-df8d17adf571.png" width=80% height=80%>
	
8.3) Repeat the lithography procedure, adding Mask12.
	
<img src="https://user-images.githubusercontent.com/118953938/214765575-4fbe52db-df3d-4179-b373-8618fac758a4.png" width=80% height=80%>
	
8.4) Eliminate the mask, then etch the silicon dioxide away. Titanium nitrate should then be applied once the photoresist has been removed. Titanium nitrate is an excellent layer for silicon dioxide as well as for bottom and top connection.

8.5)Deposit a blanket tungsten layer.
	
![image](https://user-images.githubusercontent.com/118953938/214766381-a81a51cf-c4f0-442c-b9e7-2988b08c3df1.png)

8.6) Repolish and add aluminium to the contact hole to allow it to make touch with higher metal layer.

8.7) Mask13 should be added, the lithography process repeated, the mask should be removed, and the metal should be plasma-etched.
	
![image](https://user-images.githubusercontent.com/118953938/214767701-a7ff7cb1-22f6-4dcd-8f51-424cf2bd83d3.png)

8.8) Completely remove the photoresist. Put silicon dioxide on it and polish it one more.
	
8.9) Repeat Steps 1 through 3 adding Mask 14 and depositing tungsten to create the contacts and titanium nitrate to serve as a barrier.
	
![image](https://user-images.githubusercontent.com/118953938/214768202-6eb5cb26-3ef9-48f3-8785-b40f131d09d7.png)

8.10) Make Mask15 thicker than it currently is and add it as the third level connector using aluminium. Next, add a chip protective layer.

8.11) The fabrication of 16-mask C-mos is completed when adding Mask16 to the chip's contact outside.

![image](https://user-images.githubusercontent.com/118953938/214768780-84ff5f4c-4436-46bc-be50-fb8ec75eedf8.png)
	
</p>
</details>	
</p>
</details>		
	
<details><summary> :test_tube: Labs </summary>
<p>

### :microscope: Labs for CMOS inverter ngspice simulations
	
#### :test_tube: Lab 0 - IO placer revision	

<details><summary> Reports </summary>
<p>
	

**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/214769111-0f82d679-0af6-41ac-bd5c-40214664e515.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/214769256-2046d822-1df3-4b0e-9f80-17a26f548348.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/214892637-5defd58e-5397-4c29-9e6c-6423de2fb8e6.png" width=40% height=40%>

</p>
</details>
	
#### :test_tube: Lab 1 - Lab steps to git clone vsdstdcelldesign	

<details><summary> Reports </summary>
<p>
	
**Commands**
	
		cd ~/Desktop/work/tools/openlane_working_dir/openlane
		git clone https://github.com/nickson-jose/vsdstdcelldesign.git
		cd vsdstdcelldesign
	
		cd ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic
		cp sky130A.tech ~/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
		magic -T sky130A.tech sky130_inv.mag
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/214774940-55218b67-5bf7-4620-ae83-0c46b5760e0f.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/214775113-4b1a26da-6c93-47c1-a3e5-f7391250c1ae.png" width=70% height=70%>

</p>
</details>

	
### :microscope: Inception of Layout & CMOS fabrication process
	
#### :test_tube: Lab 1 - Lab introduction to Sky130 basic layers layout and LEF using inverter	

<details><summary> Reports </summary>
<p>

	
<img src="https://user-images.githubusercontent.com/118953938/214777274-49e2ead9-815a-4036-90c4-c4c081f35a8f.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/214782728-3b4964a5-1e9e-486e-822c-e8af4ab30ce2.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/214783612-6f3acd81-87c0-4587-b4f1-0f83465db496.png" width=40% height=40%>

<img src="https://user-images.githubusercontent.com/118953938/214784973-44fda085-66de-4177-a268-406789102d0c.png" width=80% height=80%>

More information can be reffered here: https://github.com/nickson-jose/vsdstdcelldesign	
		
</p>
</details>

#### :test_tube: Lab 2 - Lab steps to create std cell layout and extract spice netlist	

<details><summary> Reports </summary>
<p>	
	
<img src="https://user-images.githubusercontent.com/118953938/214790548-e673938c-3c6d-4102-a68f-ae213454f0ad.png" width=50% height=50%>
	
**Commands**
		
		
		In tk_con
		pwd
		extract all                       
		ext2spice cthresh 0 rthresh 0     
		ext2spice
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/214790973-4574959f-103b-474f-a89f-8c7db003668a.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/214791124-59b73a84-e5af-486c-84e3-4febbf7d97cf.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/214791276-6af0eab1-309f-46be-88b6-ae5a71de8bdf.png" width=50% height=50%>

	
	
</p>
</details>

### :microscope: Sky130 Tech File Labs
	
#### :test_tube: Lab 1 - Lab steps to create final SPICE deck using Sky130 tech	

<details><summary> Reports </summary>
<p>	
	
<img src="https://user-images.githubusercontent.com/118953938/214809254-f0b27b28-7627-41a1-b2e8-aad73895d975.png" width=50% height=50%>
	
<img src="https://user-images.githubusercontent.com/118953938/214813295-97f1a5ee-b9c0-452f-80ad-d0408a020a1f.png" width=80% height=80%>
	
* Change the scale so that it reflects the magic tool's value. 
* Comprise the PMOS and NMOS library files. To add the transient analysis controls, comment out the subckt and.end lines. Establish supply voltages. 
* Defines the transient analysis's specifications as well as the input pulse. 
* Rename the nmos and pmos models as specified in the model lib file. 
* Run the spice simulation by typing "ngspice sky130A inv.spice".	
</p>
</details>		
	
#### :test_tube: Lab 2 - Lab steps to characterize inverter using sky130 model files	

<details><summary> Reports </summary>
<p>	

**Commands**
		
		ngspice sky130_inv.spice
	
		in ngspice
		plot y vs time a
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/214820147-bc4b701d-4775-4bdb-b585-7252eae3ad2d.png" width=50% height=50%>
	
<img src="https://user-images.githubusercontent.com/118953938/214820881-3d2c9219-49a4-4526-9fb9-7f67bf62388b.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214820931-644d5b0a-83eb-4b43-a3c0-881fea53dd15.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214822456-57254c48-7736-4c2c-9e2a-3b604e9fbb7a.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214831165-3252b4aa-937f-4e94-88cf-cc8b26b3fc75.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214831837-e44a9c2e-06e9-485c-8cc7-88fc217d5957.png" width=80% height=80%>

	
</p>
</details>	

#### :test_tube: Lab 3 - Lab introduction to Magic tool options and DRC rules	

<details><summary> Reports </summary>
<p>	

<img src="https://user-images.githubusercontent.com/118953938/214833473-5afe4011-be49-4484-84b1-28c65cdfe13e.png" width=80% height=80%>

**Introduction to DRC**

Design Rule Checking (DRC) verifies as to whether a specific design meets the constraints imposed by the process technology to be used for its manufacturing. DRC checking is an essential part of the physical design flow and ensures the design meets manufacturing requirements and will not result in a chip failure. The process technology rules are provided by process engineers and/or fabrication facility.
	
Example of DRCs:
	
		1) Minimum width and spacing for metal
		2) Minimum area
		3) Different net spacing
		4) Short violation
		5) Less than min edge length
	
**Introduction to Magic tool**
	
Magic is a venerable VLSI layout tool, written in the 1980's at Berkeley by John Ousterhout, now famous primarily for writing the scripting interpreter language Tcl. Due largely in part to its liberal Berkeley open-source license, magic has remained popular with universities and small companies.	
	
For more information. Can visit these links
	
Link for Open Circuit Design: http://opencircuitdesign.com/

Link for Magic tool: http://opencircuitdesign.com/magic/index.html
	
</p>
</details>		
	
#### :test_tube: Lab 4 - Lab introduction to Sky130 pdk's and steps to download labs	

<details><summary> Reports </summary>
<p>	
	
**Commands**
	
		wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz   --> import magic layout into the tool
		tar xfz drc_tests.tgz                                               --> extracting the file
		cd  drc_tests
		ls
		cat .magicrc                                                        --> finding the tech file
	
		magic -d XR  
		
		in tkcon
		drc why --> to know the error
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/214844891-18592b3c-48e2-4325-bea1-c914d6210b96.png" width=60% height=60%>
	
<img src="https://user-images.githubusercontent.com/118953938/214845184-773fd800-4600-4a96-8083-1454bbfebc63.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214845380-7f4686ca-7775-46f9-a665-22da55c61d3b.png" width=50% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214845521-1a3a0060-0b9e-47af-adfa-06f731d8e3c9.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214849090-a260760f-c17e-4422-8639-c67e93aaa2af.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214845881-f13f3f74-ffb3-4ad0-a8bc-b03c1bd26c7d.png" width=40% height=40%>
	
<img src="https://user-images.githubusercontent.com/118953938/214846143-fdf57243-e46a-42bc-983d-ff62e9c0d359.png" width=80% height=80%>

	
</p>
</details>	
	
#### :test_tube: Lab 5 - Lab introduction to Magic and steps to load Sky130 tech-rules	

<details><summary> Reports </summary>
<p>		

**Commands**
	
		cif see VIA2 --> making the squares
		feed clear --> clear up the box area
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/214845521-1a3a0060-0b9e-47af-adfa-06f731d8e3c9.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214849090-a260760f-c17e-4422-8639-c67e93aaa2af.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214854061-701cff3d-0f66-4f81-8243-8142eb7e1f86.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214854520-a21e6351-6292-4774-beb1-fce6554d58ce.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214854962-15bf02f2-67dd-4ae5-81f9-fea4ea174061.png" width=80% height=80%>

	
</p>
</details>		
	
#### :test_tube: Lab 6 - Lab exercise to fix poly.9 error in Sky130 tech-file	

<details><summary> Reports </summary>
<p>		

**Commands**	
	
		load poly
		cd ~/Desktop/work/tools/drc_tests
		vim sky130A.tech
		tech load sky130A.tech              --> reloading the tech file
		drc check                           
		drc why            

**Ooutputs**
	
<img src="https://user-images.githubusercontent.com/118953938/214864443-7d34bce9-a343-42c9-b379-3614127992a0.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214864637-1647f458-4b4b-44da-ae2a-4d75bb930ed9.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214864771-340985a6-1c41-4aff-a35e-960423594f76.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214864951-df603b58-3ac2-4d5a-9acd-9df5e2fc700f.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214865327-e59795ba-107d-430d-97ba-49d776e59e1e.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214865776-df2b0402-ba06-448e-9ad7-506d2e1d6b69.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214865918-611b4fbd-4bf7-4815-94bb-2ec045e9b8ad.png" width=60% height=60%>

</p>
</details>	
	
	
#### :test_tube: Lab 7 - Lab exercise to implement poly resistor spacing to diff and tap

<details><summary> Reports </summary>
<p>		
	
<img src="https://user-images.githubusercontent.com/118953938/214970938-a52aaca9-509e-47b2-8514-8048b0e37e44.png" width=80% height=80%>

**Modify the sky130A.tech file**	

<img src="https://user-images.githubusercontent.com/118953938/214971183-5d38f500-ef23-4311-957d-e2e9797b75d2.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214971685-4bc8e38a-27f4-4351-942d-fab66cdff7ff.png" width=60% height=60%>

	
</p>
</details>	
	
#### :test_tube: Lab 8 - Lab challenge exercise to describe DRC error as geometrical construct
	
<details><summary> Reports </summary>
<p>		

**COmmands**
	
		load nwell.mag
		cif ostyle drc
		cif see dnwell_shrink
		cif see nwell_missing 
		
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/214875331-9d2f5c2e-caef-4d9f-8825-5f14b1a7f687.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214875484-158e596d-8ac8-43bd-b91f-5abaefc0d6ec.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214875634-ce97eb04-39ff-45f3-a20c-b61cde5fe130.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214875764-640a5778-4d85-405d-ab69-0d79a34e83c9.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214875870-eca0b48e-a62d-49d9-b2bd-72c7220c2aee.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/214876024-5ff4f490-ca5f-497c-9a3b-7395ffe4db1c.png" width=80% height=80%>

	
	
</p>
</details>		
	
	
#### :test_tube: Lab 9 - Lab challenge exercise to describe DRC error as geometrical construct
	
<details><summary> Reports </summary>
<p>		

**COmmands**
	
		vim sky130A.tech
		tech load sky130A.tech             
		drc check                          
		drc style drc(full)
		drc check 
		
**Outputs**	

<img src="https://user-images.githubusercontent.com/118953938/214883329-6f0926e5-6e12-469e-ab91-74e47cc7de0a.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214883416-0b2c5d44-c81a-4ef2-a703-d1f57f4bd4b3.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214883752-518865e0-9db5-4aa8-933e-b05098bb1ac5.png" width=60% height=60%>

**Modifying the tech file**

<img src="https://user-images.githubusercontent.com/118953938/214884285-7c1153bc-9765-400b-b8d1-e09833eb0ec3.png" width=60% height=60%>
	
<img src="https://user-images.githubusercontent.com/118953938/214884122-560b2c50-da64-4f4b-9598-61256340e921.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/214884442-0b39b2ff-9456-4901-91a9-5fdbf0112e52.png" width=60% height=60%>


</p>
</details>		

</p>
</details>	
	
	
	
	
## :book: Day 18 - Pre-layout timing analysis and importance of good clock tree

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Timing modelling using delay tables
	
:black_nib: **Introduction to delay tables**
	
<details><summary> Explainations </summary>
<p>		
	
<img src="https://user-images.githubusercontent.com/118953938/214972198-6c4d7858-3c94-48db-b2f9-e7afaccc6221.png" width=50% height=50%>
	
**AND Gate**
* The enable of an AND gate is high active. That is, when the enable is high the input signal will appear on the output. 
* When the AND gate enable input is low, the output will remain a constant low signal. 
* A two input OR gate can also be used with one input the desired signal and the other input is the enable.	

**OR Gate**
* The enable input of an OR gate is low active. 
* This means that the output will be a copy of the input signal when the enable is low. 
* When the enable input of an OR gate is high, the output of the gate will be a constant high signal.
	
<img src="https://user-images.githubusercontent.com/118953938/214972316-eec1533e-b76f-4fb8-8ae8-e16183a25c1f.png" width=70% height=70%>

* The input transition and output load of a cell are varied against the cell's delay to characterise the delay table.
* For various sizes and threshold tables, each cell will have its own delay table.

<img src="https://user-images.githubusercontent.com/118953938/214973293-2b9c9f12-d62c-44e2-9f8c-edfe8f9b38de.png" width=70% height=70%>

**Example of the delay table**
	
<img src="https://user-images.githubusercontent.com/118953938/214973515-434f7cb3-4ff8-4033-8d23-c659eaee57c1.png" width=50% height=50%>

**Clock Gating**
* Clock gating is a power-saving feature in semiconductor microelectronics that enables switching off circuits. 
* Many electronic devices use clock gating to turn off buses, controllers, bridges and parts of processors, to reduce dynamic power consumption.	
	
Why is clock gating used?<br>
* The technique of clock gating is used to reduce the clock power consumption by cutting off the idle clock cycles.	

What are types of clock gating?<br>
* There are two types of clock gating styles available. 
* They are: 
	1) Latch-based clock gating 
	2) Latch-free clock gating.
* The latch-free clock gating style uses a simple AND or OR gate (depending on the edge on which flip-flops are triggered).

</p>
</details>	
	
:black_nib: **Delay table usage Part 1 and Part 2**
	
<details><summary> Explainations </summary>
<p>		
	
**Example of the delay table**
	
<img src="https://user-images.githubusercontent.com/118953938/214975473-b33f6353-9b20-413f-bd93-8bb7552e14d7.png" width=50% height=50%>
	
* Delay table = representation of the delays for one of the cells 
* Similar delay table will be created for each and every kind of gates
* Table on the top shows the table buffer of '1'
* The buffer was taken out of the circuit and characterized based on different range of input slew with different output capacitance
	
<img src="https://user-images.githubusercontent.com/118953938/214975825-74cfa5b3-181b-41c2-8f4c-3dab4aa40804.png" width=80% height=80%>
	
* A characterisation table for input transition will be similar to how a delay table is to how a delay table is.
* The total of the delays experienced by each individual cell along that path will represent the latency at the endpoints.
* It is preferable to have the nodes at each level driving the same load because if the output load driven for a cell is altered, the total skew value between two endpoints will not be zero, resulting in various delay values being visible between endpoints.	
	
<img src="https://user-images.githubusercontent.com/118953938/214984885-598604a8-2d1f-40bf-821b-2f5e45a1b61f.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/214987007-f4c634cd-9240-4479-9621-3fe3c796f442.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/214987509-eaff2540-8eef-4a78-8601-99d8cdcda2d2.png" width=80% height=80%>
	
* By employing a different buffer size at the same level that can accomplish the same amount of delay as the other buffer at the same level based on its delay table, we can also maintain the skew to be zero in the presence of variable load.
* Early on in the clock tree design stage, these are the kinds of issues that should be taken into consideration.
* Now that CTS is power aware, it is necessary to take into account endpoints that are only active sometimes.
* We do not need to transmit the clock into those cells in this instance while they are dormant.	
	
<img src="https://user-images.githubusercontent.com/118953938/214987955-8aab2d1e-eb1d-40fb-9059-4563eaac714a.png" width=80% height=80%>

</p>
</details>	

### :mag_right: Timing analysis with ideal clocks using openSTA
	
:black_nib: **Setup timing analysis and introduction to flip-flop setup time**
	
<details><summary> Explainations </summary>
<p>		
	
**Setup Timing Analysis**

* Static timing analysis (STA) is a method of validating the timing performance of a design by checking all possible paths for timing violations.
* Setup time is the minimum amount of time the data signal should be held steady before the clock event so that the data are reliably sampled by the clock. 
* Hold time is the minimum amount of time the data signal should be held steady after the clock event so that the data are reliably sampled.

**How it works?**

<img src="https://user-images.githubusercontent.com/118953938/215364823-acebfc01-e334-4ce1-9fc7-83ab013bc416.png" width=80% height=80%>
	
* One clock edge hits the launch flop at the zero time stamp.
* The second rising edge reaches the capture flop at time stamp T. Between 0 and T, any necessary analysis must be performed. 
* The combinational delay must be shorter than the period, T, for the combinational circuit to function.

In more real-world situations, the internal flop circuitry will experience a delay between mux 1 and mux 2, according on how the flop operates.
	
<img src="https://user-images.githubusercontent.com/118953938/215365403-830a8e60-23f9-4b94-9fd9-a123dd8d9343.png" width=80% height=80%>
	
* The combinational delay needs will be constrained by these internal delays.
* The setup time is the name for this internal delay, and it must be deducted from the whole clock period T.
* In order to ensure that the data is prepared at Q by the time the second rise edge of the clock reaches, the capture flop now has enough time to calculate the data within the flop.	
	
<img src="https://user-images.githubusercontent.com/118953938/215365640-b507f12f-a7aa-4a68-8bb6-0d7ac996b639.png" width=80% height=80%>
	
In order to guarantee that the data system operates within the allotted time, the capture flop now has adequate time to bring the data to the flop.	
	
</p>
</details>	

:black_nib: **Introduction to clock jitter and uncertainty**
	
<details><summary> Explainations </summary>
<p>	

**JITTER**

Clock jitter is typically caused by clock generator circuitry, noise, power supply variations, interference from nearby circuitry etc. <br>
Jitter is a contributing factor to the design margin specified for timing closure.
	
* Period jitter
	* Period jitter is the deviation in cycle time of a clock signal with respect to the ideal period over a number of randomly selected cycles(say 10K cycles). 
	* It can be specified an average value of of clock period deviation over the selected cycles(RMS value) or can be the difference between maximum deviation & minimum deviation within the selected group(peak-to-peak period jitter).

* Cycle to cycle jitter
	* C2C is the deviation in cycle of of two adjacent clock cycles over a random number of clock cycles. (say 10K). 
	* This is typically reported as a peak value within the random group.This is used to determine the high frequency jitter.

* Phase jitter
	* In frequency domain, the effect being measured is phase noise. 
	* It is the frequency domain representation of rapid, short-term, random fluctuations in the phase of a waveform. 
	* This can be translated to jitter values for use in digital design.
	
To put it a simple word:
	
Clock jitter = On the same Flip-Flop, the position of the clock edge moves from edge to edge due to the oscillator noise/stability. Clock uncertainty = I'm not sure. The fact that an edge is neve perfect and that you can't say precisely when it was taken into account by the Flip-Flop?
	
<img src="https://user-images.githubusercontent.com/118953938/215366450-822d67b8-28d1-4954-9151-7ef92faf1cad.png" width=80% height=80%>

* In ideal circumstances, the clock signal should be able to reach the clock pin at exactly 0 or Ts, but in practise, this may not be possible because each clock source generation may have its own inherent fluctuation.
* This is referred to as jitter, which is a brief change in the clock's period.
* As a consequence, the combinational delay will be tightened up. As a result, we modify our combinational delay to account for the jitter's uncertainty component.
	
<img src="https://user-images.githubusercontent.com/118953938/215366576-a2766aa2-55f2-4f24-94a0-d409348b3be1.png" width=80% height=80%>
	
**Setup Uncertainty**	

_Uncertainty: It specifies a window within which a clock edge can occur._ 
* Clock uncertainty is the deviation of the actual arrival time of the clock edge with respect to the ideal arrival time. 
* In ideal mode the clock signal can arrive at all clock pins simultaneously.	
* In physical design uncertainty will be used to model several factors like jitter (the deviation of clock edge from its ideal position), additional margins and skew (at pre-cts) There will be different uncertainty values specified for setup and hold.

<img src="https://user-images.githubusercontent.com/118953938/215367146-336744da-3f48-4561-892b-ed44616508d1.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215367295-e1cb162f-5052-4c93-9ba6-465082411a13.png" width=80% height=80%>

</p>
</details>	

### :mag_right:  Clock tree synthesis TritonCTS and signal integrity
	
:black_nib: **Clock tree routing and buffering using H-Tree algorithm**
	
<details><summary> Explainations </summary>
<p>	

**Clock tree synthesis**
	
Clock Tree Synthesis (CTS) is the technique of balancing the clock delay to all clock inputs by inserting buffers/inverters along the clock routes of an ASIC design. As a result, CTS is used to balance the skew and reduce insertion latency.	
	
<img src="https://user-images.githubusercontent.com/118953938/215368085-96c9402f-fc62-4b10-8014-0a8fa823e780.png" width=80% height=80%>
	
* The skew between the clock pins brought on by lengthy routing must be taken into consideration when designing a proper clock tree.
* By using an H-tree, a more intelligent implementation of a clock tree design that is created based on the spacings between the clock pins in the clock port design.
* By having the clock signals arrive at each cell at the same time, this will provide a skew value that is as near to 0 as feasible.	
	
<img src="https://user-images.githubusercontent.com/118953938/215368394-bf7d1d7f-05f2-428b-ac49-e2ac98185bbe.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/215368535-01a139dc-06d9-40c8-a5c2-ed62931aa74e.png" width=80% height=80%>
	
**Buffering**

Why buffers are used in clock tree?<br>
In addition, we use both minimum-size clock buffers and cascaded clock buffers to minimize the maximum clock delay in the clock distribution tree. We show that the proposed buffer insertion scheme can significantly reduce the clock delay and at the same time reduce the clock skew.

<img src="https://user-images.githubusercontent.com/118953938/215368745-536cc9df-05c9-4c9d-8533-49223f5a9663.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/215368867-b7943450-47d2-4c06-84ce-a165e6851ceb.png" width=80% height=80%>

</p>
</details>	

:black_nib: **Crosstalk and clock net shielding**
	
<details><summary> Explainations </summary>
<p>	
	
**Crosstalk** 
	
Crosstalk in VLSI is any phenomenon in electronics that occurs when a signal carried on one circuit or channel of a transmission system causes an undesirable effect in another circuit or channel. Crosstalk is typically generated by unwanted capacitive, inductive, or conductive coupling between circuits or channels.

What are two types of crosstalk?
In fact, there are two types of crosstalk and there are two possible causes of crosstalk in any system. The two types of crosstalk are near-end and far-end crosstalk, both of which create unwanted interference between signals on different interconnects.
	
* The clock nets are the most important ones in the design; we construct the clock tree to guarantee a minimal skew.
* Cross talk, on the other hand, might negatively impact the clock signals and have a significant impact on the design.	
	
<img src="https://user-images.githubusercontent.com/118953938/215369708-db51a84f-cb1b-4a70-80f9-c87cbf7a740d.png" width=80% height=80%>
	
* We isolate the clock networks from the outside world, preventing errors and delta delays.
* Incorrect data in the memory will result in faulty functionality for the design if a bug in the clock net arises.	
	
<img src="https://user-images.githubusercontent.com/118953938/215370126-536d8817-4bb6-4f7b-93c5-d3f083eacc67.png" width=80% height=80%>
	
* If there is no switching action going on, the shield can be attached to either ground or Vdd.
* Nets carrying crucial data must also be protected.	

<img src="https://user-images.githubusercontent.com/118953938/215370247-ca4a3b7f-b5a3-4566-9db9-23a42db1f94a.png" width=80% height=80%>

</p>
</details>	

### :mag_right:  Timing analysis with real clocks using openSTA
	
:black_nib: **Setup timing analysis using real clocks**
	
<details><summary> Explainations </summary>
<p>	

**Setup Timing**
	
<img src="https://user-images.githubusercontent.com/118953938/215370768-406419dd-89d0-46eb-a902-058dbcbe728d.png" width=80% height=80%>
	
* More clock network delay has been imposed with the addition of the buffer, and all delays will be combined.
* In order to maintain the integrity of the clock signal while using actual clocks, buffers will need to be added to the clock path.
* The clock edge will eventually reach the clock pin due to the buffer introduction, taking into account the delays of the buffers introduced.	
	
<img src="https://user-images.githubusercontent.com/118953938/215371051-c6a359c2-0366-44af-b493-ce7d88ccffa4.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/215371214-1602abb4-3863-421d-93fc-6428591d6983.png" width=80% height=80%>
	
* The delays from the inserted buffers must also be taken into account by the clock network delay.
* The delays caused by the added buffers will cause the window to move.

<img src="https://user-images.githubusercontent.com/118953938/215371429-c028b2c2-053a-4cf3-bd24-7bc97ebfb0c9.png" width=80% height=80%>

* The skew for this design will now be the difference between the deltas, and based on the picture provided, the equation for setup timing analysis will also change.
* We will have negative slack on the path, which means we have violations, if the time for data arrival is longer than the time for data requirement.	
	
**Hold Timing**

* Checking for the minimum delay the data should take to arrive at the second flop for the circuit to function correctly.
	
<img src="https://user-images.githubusercontent.com/118953938/215371743-12314b02-a98a-4129-81aa-7287742883fa.png" width=80% height=80%>
	
* The combinational delay should be bigger than the hold time of the flop in hold timing analysis when the capture edge is on the o clock rising edge.

<img src="https://user-images.githubusercontent.com/118953938/215372068-dbbb7eae-afc5-404b-996c-ad68e78b0a5d.png" width=80% height=80%>
	
* Hold time is the second mux delay, or the amount of time needed for the data to be transferred from the flop following the clock edge.	
	
<img src="https://user-images.githubusercontent.com/118953938/215372218-bf9eb29e-460e-496f-8307-8db99b951823.png" width=80% height=80%>
	
		
</p>
</details>	

:black_nib: **Hold timing analysis using real clocks**
	
<details><summary> Explainations </summary>
<p>		

Equation of hold time considering the clock skew:
	
Tcq1 + Tg >= Th + Tskew

Th <= (Tcq1 + Tg) — Tskew	
	
* Since the design is on the 0 clock edge and the arrival difference for the capture and launch flops will be the same, jitter for the launch clock and capture flop will not need to be taken into account.
* So, for the hold analysis, the uncertainty should be maintained to a minimum.	
	
<img src="https://user-images.githubusercontent.com/118953938/215372773-6e537fa1-77d3-4b90-af49-d85a65941b33.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/215372876-a2349676-d016-4ab7-815a-2a96fd9bec67.png" width=80% height=80%>
	
* We must take the previously mentioned deltas into account while setting up the timing path for actual clocks.
* Launch clock network delay will affect delta1 whereas capture clock network delay will affect delta2.	

<img src="https://user-images.githubusercontent.com/118953938/215373118-44c32836-0869-437d-902d-c75cb256bb8b.png" width=80% height=80%>

	
</p>
</details>
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>

### :microscope: Timing modelling using delay tables
	
#### :test_tube: Lab 1 - Lab steps to convert grid info to track info	

<details><summary> Reports </summary>
<p>	
	
**Library Exchange Format (LEF)**

Library Exchange Format is a specification for representing the physical layout of an integrated circuit in an ASCII format. It includes design rules and abstract information about the standard cells. LEF only has the basic information required at that level to serve the purpose of the concerned CAD tool.	
	
Main guidelines:

		The input and output ports must lie on the intersection of the vertical and horizontal tracks
		The width of standard cell should be on the track pitch, and the height should be on the track vertical pitch	
	
* Layers and metal traces	
	
<img src="https://user-images.githubusercontent.com/118953938/215332692-7104eeea-aed4-42a9-ac4f-42c6f472ca8f.png" width=80% height=80%>
	
* Adding grids
	
<img src="https://user-images.githubusercontent.com/118953938/215332788-e522e906-6899-4a8c-8a2c-468570a217b7.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215332906-96164312-cc45-41d4-b5dd-6a48c775b935.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215332933-72be71bf-cea6-4581-bbba-1473f149695f.png" width=80% height=80%>

The junction of the horizontal and vertical rails is where ports are located. It makes sure that the routes can go in both x and y directions to reach the ports.
Verified that the input and output ports adhere to the rule that states that they should be located at the junction of horizontal and vertical tracks.
	
</p>
</details>	

#### :test_tube: Lab 2 - Lab steps to convert magic layout to std cell LEF	

<details><summary> Reports </summary>
<p>	

* To guarantee that the layout is completed as required, the standard cell's width and height must be odd multiples of the x and y pitches.

* The layers are always described when a layout is created, but ports are not present since ports have no significance to the magic. 
* To extract the lef file, port definitions are necessary. The pins of the macros will be used to specify the ports.
	
<img src="https://user-images.githubusercontent.com/118953938/215332993-35d56adc-868e-4098-bb0a-3b66ff22c60c.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215335988-4aeb819a-4f55-4999-94b5-c1f2491953a8.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215336018-7905e62e-9818-4c31-ac9f-afeb75d09754.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215336066-17431c87-98b0-4e17-a1ba-9a1e18b721d7.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/215336091-3734860c-6c2f-409f-99e9-a6369dbc625c.png" width=80% height=80%>

	
</p>
</details>	
	
#### :test_tube: Lab 3 - Introduction to timing libs and steps to include new cell in synthesis	

<details><summary> Reports </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/215336358-29ed190e-7512-4afd-b398-1498eabf8f65.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215336381-f6613b79-4f18-435a-8575-bb9535e7e5ae.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215336395-2542fcb1-a2a0-4b87-83e2-ecbcdc172bb4.png" width=80% height=80%>
	
	
</p>
</details>


#### :test_tube: Lab 4 - Introduction to timing libs and steps to include new cell in synthesis	

<details><summary> Reports </summary>
<p>
	
<img src="https://user-images.githubusercontent.com/118953938/215336525-58a833d9-fc06-462b-afb3-6b6e5c222fb5.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215336578-b2a65489-135b-4470-8c37-5cc3b9f060c9.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215337619-d6ea2d1c-1d88-4caa-89ba-2e7de0b4ffef.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215337668-74768f93-f7f8-48bd-91a1-2a4bdb3d5a69.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215337702-53458b96-1c1d-43b2-a209-ce4bb415c453.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215337738-01c5aee8-58c5-48d5-99e7-8d5f125e097d.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215337769-60a46605-0d24-48dd-bb00-27e3bee94f5b.png" width=80% height=80%>

	
</p>
</details>	
	
### :microscope: Timing analysis with ideal clocks using openSTA
	
#### :test_tube: Lab 1 - Lab steps to configure OpenSTA for post-synth timing analysis	

<details><summary> Reports </summary>
<p>		
	
<img src="https://user-images.githubusercontent.com/118953938/215337914-d9d07fdc-3e79-47b7-b073-3595e2e0b7ae.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215338050-0f659c39-a23c-4ea0-86ba-3cec826d87e5.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215338081-cc86f595-faec-46d6-b0fb-4d8256430c22.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215338127-768e552f-8d17-41f3-afc4-378f4f37c03f.png" width=80% height=80%>
	
	
</p>
</details>	

#### :test_tube: Lab 2 - Lab steps to optimize synthesis to reduce setup violations	

<details><summary> Reports </summary>
<p>	
	
<img src="https://user-images.githubusercontent.com/118953938/215418998-aec6c442-70f3-4e17-bd3d-484ea494fe27.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215417870-a30cd07d-00a9-44aa-a282-9d96ffefb0a5.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215418225-9e0e552f-0692-4c92-baaf-b265da5c88c3.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215420300-0b216f5c-e0f1-44aa-8bf6-a77f0a09c679.png" width=80% height=80%>

**Improving the delay**
	
		in openlane	
		set ::env(SYNTH_MAX_FANOUT) 4	
		run_synthesis	
	
		replace_cell _38618_ sky130_fd_sc_hd__dfxtp_4 #increase drive strength
		report_checks -fields {net cap dlew input pins} -digits 4
		report_tns
		report_wns
	
<img src="https://user-images.githubusercontent.com/118953938/215421356-11bd26c0-a343-4f57-bd36-ea056f6fc2ed.png" width=80% height=80%>

	
</p>
</details>	
	
#### :test_tube: Lab 3 - Lab steps to do basic timing ECO	

<details><summary> Reports </summary>
<p>	
	
**Command**	
	
		report_checks -from _41952_ -through _41879_
	
By upsizing the cell, the delay will be reduced.	
</p>
</details>	
	
### :microscope: Clock tree synthesis TritonCTS and signal integrity
	
#### :test_tube: Lab 1 - Lab steps to run CTS using TritonCTS

<details><summary> Reports </summary>
<p>
	
**Commands**
	
		write_verilog ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-01_14-09/results/synthesis/picorv32a.synthesis.v
		cd ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-01_14-09/results/synthesis
		ls -lrt picorv32a.synthesis.v
	
		In openlane
		run_floorplan
		run_placement
		run_cts
	
		Back to terminal
		cd ~/Desktop/work/tools/openlane_working_dir/openlane/configuration
		vim README.md
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/215426720-ec13f7d6-c29a-4927-a2cc-449bb0f1ed15.png" width=80% height=80%>

	
</p>
</details>	

#### :test_tube: Lab 2 -  Lab steps to verify CTS runs

<details><summary> Reports </summary>
<p>
	
**Commands**	
	
		cd ~/Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands
		vim cts.tcl	
		cd ~/Desktop/work/tools/openlane_working_dir/openlane/scripts/openroad
		vim or_cts.tcl
		
		in openlane
		echo $::env(LIB_TYPICAL)
		echo $::env(CURRENT_DEF)
		echo $::env(CTS_MAX_CAP)
		echo $::env(CTS_CLK_BUFFER_LIST)
		echo $::env(CTS_ROOT_BUFFER)
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/215430505-1e8619ea-510b-4927-bfdc-415a240ecc2b.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/215430731-84fe6b87-6a2c-4d7f-a67a-72f14149d0b3.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/215431244-dc72764d-7ff3-4f0a-ad14-a1e6ed013b61.png" width=80% height=80%>

</p>
</details>	

### :microscope: Timing analysis with real clocks using openSTA
	
#### :test_tube: Lab 1 - Lab steps to analyze timing with real clocks using OpenSTA
	
<details><summary> Reports </summary>
<p>	
	
**Commands**	
		
		invoking openroad
		-openroad     
	
		read lef and def file
		-read_lef /openLANE_flow/designs/picorv32a/runs/13-01_14-09/tmp/merged.lef
		-read_def /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/cts/picorv32a.cts.def
		
		writing db file
		-write_db pico_cts.db
	
		read .db
		-read_db pico_cts.db
		-read_verilog /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/synthesis/picorv32a.synthesis_cts.v
		-read_liberty -max $::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib
		-read_liberty -min $::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib
	
		-set_propagated_clock [all_clocks]
		-read_sdc designs/picorv32a/src/my_base.sdc
	
		Report
		-report_checks -path_delay min_max -format full_clock_expanded -digits 4	
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/215476290-36efe8df-dc84-408e-894a-2c7dc5472c5b.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/215476470-0a7315a5-c86d-48c3-a4a0-22f7af18607c.png" width=50% height=50%>	
	
</p>
</details>
	
#### :test_tube: Lab 2 - Lab steps to execute OpenSTA with right timing libraries and CTS assignment
	
<details><summary> Reports </summary>
<p>	
	
**Commands**
		
		-exit
	
		invoke openroad
		-openroad
		-read_db pico_cts.db
		-read_verilog /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/synthesis/picorv32a.synthesis_cts.v
		-read_liberty $::env(LIB_SYNTH_COMPLETE)
	
		Linking the design with database
		-link_design picorv32a
	
		read_sdc designs/picorv32a/src/my_base.sdc
		-set_propagated_clock [all_clocks]
		-report_checks -path_delay min_max -fields {slew trans net cap input pin} -format full_clock_expanded
		-echo $::env(CTS_CLK_BUFFER_LIST)     
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/215477949-ce568247-5ad2-4d8e-a265-42a689724687.png" width=50% height=50%>
	
<img src="https://user-images.githubusercontent.com/118953938/215478281-89e5e721-78c4-4a0e-be4b-269caf9188d6.png" width=50% height=50%>
	
</p>
</details>	
	
#### :test_tube: Lab 3 - Lab steps to observe impact of bigger CTS buffers on setup and hold timing
	
<details><summary> Reports </summary>
<p>	
	
**Commands**	
	
		In openlane, run these command
		-exit 
		-echo $::env(CTS_CLK_BUFFER_LIST)
		-set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]
		-echo $::env(CURRENT_DEF)
		-set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/placement/picorv32a.placement.def
		-run_cts	
	
		Back to openroad
		Invoke
		-openroad
	
		read lef and def file
		-read_lef /openLANE_flow/designs/picorv32a/runs/13-01_14-09/tmp/merged.lef
		-read_def /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/cts/picorv32a.cts.def
	
		write and read db file
		-write_db pico_cts1.db
		-read_db pico_cts1.db
		-read_verilog /openLANE_flow/designs/picorv32a/runs/13-01_14-09/results/synthesis/picorv32a.synthesis_cts.v
		-read_liberty $::env(LIB_SYNTH_COMPLETE)
	
		linking file
		-link_design picorv32a
		-read_sdc designs/picorv32a/src/my_base.sdc
		-set_propagated_clock [all_clocks]
	
		report
		-report_checks -path_delay min_max -fields {slew trans net cap input pin} -format full_clock_expanded
	
		setup and hold time report
		-report_clock_skew -hold
		-report_clock_skew -setup
		-set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]     
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/215482336-17fd4862-eb29-4b9a-9886-785e7bff414e.png" width=50% height=50%>
	
<img src="https://user-images.githubusercontent.com/118953938/215483930-6d6f0831-71cb-4629-aadd-d3504409cf64.png" width=50% height=50%>
	
<img src="https://user-images.githubusercontent.com/118953938/215484464-c18e451c-497f-4f7d-9c5b-3ef724d6895f.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/215485597-05997654-2589-4d14-9ff5-d0e9ea6624ba.png" width=50% height=50%>

	
</p>
</details>	
	
	
</p>
</details>		
	
	
## :book: Day 19 - Final steps for RTL2GDS

<details><summary> :mag_right: Theories </summary>
<p>	
	
### :mag_right:  Final steps for RTL2GDS using tritonRoute and openSTA
	
:black_nib: **Introduction to Maze Routing using Lee's algorithm**
	
<details><summary> Explainations </summary>
<p>	
	
**What is maze routing algorithm?**
	
The Maze Routing algorithm is an algorithm to find connections between the terminals and the Lee algorithm is one possible solution for Maze routing problems. Lee algorithm searches for the shortest path between two terminals and guarantees to find a route between two points if the connection exists.	

**What is Lee algorithm used for?**
	
The Lee algorithm is one possible solution for maze routing problems. It always gives an optimal solution, if one exists, but is slow and requires large memory for dense layout.

<img src="https://user-images.githubusercontent.com/118953938/215517694-dfa5f387-7d40-4890-992c-5bbfe66252a8.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/215520017-b3229269-1560-45e7-8a17-f666aea0409d.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/215521235-30f33a2a-0dbb-43a4-8755-a3fd9eac40be.png" width=70% height=70%>

* There will be some standard dimentions to the grid.
* A routing grid is superimposed on routing region. Routing takes place along the grid lines. 
* The space between adjacent grid lines is called wire pitch and is equal to sum of minimum width of wires and spacing of wires.

It usually uses the following steps:
	
* A routing grid should be created behind the layout.
* Track down the two points. The source and target were established as the two points.
* The routing grid will be used by the algorithm to find the optimum path between the two spots.
* The tool will mark the grid ground where a horizontal and vertical grid will be close.
	
<img src="https://user-images.githubusercontent.com/118953938/215523626-c0ea4b51-3c2b-4b00-a0c2-1016bb36f3f0.png" width=70% height=70%>
	
	
</p>
</details>	

:black_nib: **Introduction to Maze Routing using Lee's algorithm**
	
<details><summary> Explainations </summary>
<p>	
	
* Continually add the numbers	
	
<img src="https://user-images.githubusercontent.com/118953938/215625976-58562084-ef81-49c2-8605-aaf1cce36293.png" width=70% height=70%>

* As seen in the image above, selecting the LHS is superior to selecting the RHS.
* The optimal path, which has less bending (L-shaped), was picked in the LHS figure rather than the RHS figure as below.
	
<img src="https://user-images.githubusercontent.com/118953938/215626436-6471acbe-9973-4fc1-95a0-5bdbf5515710.png" width=70% height=70%>
	
* LHS figure will therefore start the global routing. Routing for a single route will be quite straightforward, but if we need to route between millions of start and endpoints, this technique will take a lot of time and memory.	
* Large designs need more time and memory spent on maze routing.
* Some methods, such the line-search algorithm and stanner-tree algorithm, can help to decrease the amount of time and memory used.
	
<img src="https://user-images.githubusercontent.com/118953938/215626907-5529ce67-50ad-44de-aa12-4425e94c889c.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/215627250-15f9fef3-bcf3-4bd0-94eb-41e5e9598358.png" width=70% height=70%>
	

</p>
</details>		

:black_nib: **Design Rule Check**
	
<details><summary> Explainations </summary>
<p>	
	
**Design Rule Checking (DRC)**
* verifies as to whether a specific design meets the constraints imposed by the process technology to be used for its manufacturing. 
* DRC checking is an essential part of the physical design flow and ensures the design meets manufacturing requirements and will not result in a chip failure.	
* The minimum wire width rule, which states that the wire's width must not be smaller than a certain number depending on the constraints of the manufacturing process, may be one of the rules.
* The wire pitch rule, which states that the center-to-centre spacing between 2 wires should not be less than a specific distance, is another regulation based on the lithography fabrication method.	
	
<img src="https://user-images.githubusercontent.com/118953938/215628726-ce013dea-9f38-4a2e-af1a-d7cc708a56f4.png" width=70% height=70%>
	
* Wire spacing is another regulation, which states that there shall be a minimum space between any two wires.
* When completing the design's routing, the tool must take into consideration a number of rules.	
	
<img src="https://user-images.githubusercontent.com/118953938/215629342-56853fda-bdc8-45fa-bf97-a8b94d07002f.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/215629375-ae80fd9b-8155-4194-89fd-6b4cd946bd8f.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/215629659-2acb7c66-7b74-48f9-abf0-3a2ee9e69968.png" width=70% height=70%>

* A signal short, which occurs when two wires that are not supposed to be linked come into touch on the same layer, is one kind of DRC violation.
* It is necessary to address this as it might result in functional failure.
* Simply relocating one of the wires to a different metal layer will solve this problem.
* Please be aware that there are new DRC regulations that must be taken into consideration.	
	
<img src="https://user-images.githubusercontent.com/118953938/215630115-5a10a1fe-6f3f-481a-a5e4-3c1e9a6301d5.png" width=70% height=70%>

DRC rules to be followed when performing the routing of design<br>
1) wire width 
	* must not be less than yet not more than a certain quantity
2) wire pitch 
	* the two wires' centres should be separated by at least the specified amount of space.
3) wire spacing 
	* Minimum spacing should be used, which implies it can't be any smaller or larger.
	
<img src="https://user-images.githubusercontent.com/118953938/215630345-b73572e8-49e9-4458-aa38-77ffa686fee3.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/215631030-f27b8fca-e668-4b0e-a42b-336c460ee473.png" width=70% height=70%>

Executing parasitic extraction, where the wires' capacitances and resistances are removed and utilised in subsequent procedures.
	
<img src="https://user-images.githubusercontent.com/118953938/215631679-8bab978c-ca50-4d6b-83a1-453473776bfb.png" width=70% height=70%>

</p>
</details>

### :mag_right:  TritonRoute Features
	
:black_nib: **TritonRoute feature 1 - Honors pre-processed route guides**
	
<details><summary> Explainations </summary>
<p>	
	
**TritonRoute** 
* is an open source detailed router for modern industrial designs. The router consists of several main building blocks, including pin access analysis, track assignment, initial detailed routing, search and repair, and a DRC engine.	
	
* Performs the initial detail route
	
<img src="https://user-images.githubusercontent.com/118953938/215635124-a126bd27-6815-4d66-bd34-42815b1b4e33.png" width=70% height=70%>
	
* Honours the preprocessed route guides (obtained after fast routes), wherein the tool attempts as much as possible to route within route guides.
* Assumes route guides for each net satisfy inter-guide conectivity
* Works on proposed MILP-based panel routing scheme with intra-layer paralled and inter-layer sequential routing framework

<img src="https://user-images.githubusercontent.com/118953938/215635346-02014dac-ff3d-42af-b8d0-cdfd1b90d4d6.png" width=70% height=70%>
	
Requirements of preprocessed route guides:<br>
1) Should have unit width
2) Should be in preffered direction

Steps
* After FastRoute completed the global route. Initial routing guidance is the FastRoute's output. 
* It will split improperly when it should have encountered a horizontal axis instead of a vertical one, a process known as spilitting. 
* The process of merging the edges follows. net, which crosses a further top layer. 
* Preprocessed guidelines as M1 = vertical, M2 = horizontal are the last step.
	
</p>
</details>	

:black_nib: **TritonRoute Feature2 & 3 - Inter-guide connectivity and intra- & inter-layer routing**
	
<details><summary> Explainations </summary>
<p>	

There will be a preferred routing direction assigned to each layer or panel, in which the routes should be built.

Only once routing in the lower levels has been finished will routing in the higher layers start.
	
<img src="https://user-images.githubusercontent.com/118953938/215635346-02014dac-ff3d-42af-b8d0-cdfd1b90d4d6.png" width=70% height=70%>	
	
The two guides are connected if:	
* They are on the same metal layer with touching edges, or
* they are on the neighbouring metal layers with a non zero vertically overlapped area
	
Each connected terminal example a pin of a standard cell instance should have its pin shape overlapped by a route guide
	
<img src="https://user-images.githubusercontent.com/118953938/215648758-3a156459-be21-43ea-9134-debdd209309e.png" width=70% height=70%>
	
For more information can visit this link : https://slideplayer.com/slide/16030472/	
	
</p>
</details>	
	
:black_nib: **TritonRoute method to handle connectivity**
	
<details><summary> Explainations </summary>
<p>	

**TritonRoute method to handle connectivity**	
	
* Detailed routing is a dead-or-alive critical element in design automation tooling for advanced node enablement.	
* The LEF file, DEF file, and the Preprocessed route guidelines are the input files required by TritonRoute.
* A full routing solution with optimal wire-length and through count would be the TritonRoute's output.
* The route guide must be respected, as well as any connection restrictions and design guidelines, in TritonRoute.	
	
**TritonRoute method**

* 2 ways of handling the conectivity
	* Access Point (AP)
		* Access point: on-grid point on the metal layer of the route guide, and is used to connect to lower-layer segments, upper-layer segments, pins or IO ports.
	
	* Access Point Cluster (APC)	
		* Access Point Cluster: a union of all Access Points derived from the same lower-layer segment, upper-layer guide, a pin or an IO port.

<img src="https://user-images.githubusercontent.com/118953938/215649916-4c2ad4ec-7be0-4b8f-b336-f058d6cd94df.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/215650437-5c1a0baa-671a-4315-9008-cb61b62bb443.png" width=70% height=70%>

* Creating the best possible connection between two access points is the goal of Mixed Integer Linear Programming (MILP).
	* Pick which access point the via should be dropped at.
	* Deciding on the connection method between the first access point and the following access point.
	
<img src="https://user-images.githubusercontent.com/118953938/215651006-2b78975a-4dfe-463b-83d9-cb05059e236c.png" width=70% height=70%>
	
	
</p>
</details>	
	
	
</p>
</details>	
	
<details><summary> :test_tube: Labs </summary>
<p>

### :microscope:  Power Distribution Network and routing
	
#### :test_tube: Lab 1 - Lab steps to build power distribution network	
	
<details><summary> Reports </summary>
<p>
	
**Commands**
	
		invoking back the openlane
		-cd work/tools/openlane_working_dir/openlane
		-make mount
		-pwd
		-ls -ltr
		-./flow.tcl -interactive
		-package require openlane 0.9
		-prep -design picorv32a -tag 13-01_14-09

		To ensure current_def is on the CTS stage
		-echo $::env(CURRENT_DEF)  
	
		To generate power distribution network
		-gen_pdn                     
	
* If we want to retain the configurations from the last openlane job, we need to use **_prep -design -tag_**. 
* If we want to create a fresh run with new configurations but without changing the tag name, we need to use **_prep -design -tag -overwrite_**.
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/215661677-7861a577-3ba5-4beb-a270-1d8d1ffacefe.png" width=70% height=70%>

</p>
</details>	
	
#### :test_tube: Lab 2 - Lab steps from power straps to std cell power	
	
<details><summary> Reports </summary>
<p>

**What are the power distribution techniques in VLSI?**
There are several VLSI techniques to reduce leakage power, input rise time, source leakage current, gate current. Switching power,short circuit power, power in capacitance, and also dissipation in output loading effect the power consumption of device
	
* The power and ground rails has a pitch of 2.72um thus the reason why the customized inverter cell has a height of 2.72 or else the power and ground rails will not be able to power up the cell. 
* Looking at the LEF file runs/[date]/tmp/merged.nom.lef, you will notice that all cells are of height 2.72um and only width differs.
	
<img src="https://user-images.githubusercontent.com/118953938/215664521-0efa3f68-ac9e-43f0-bf1a-b1c686ccef72.png" width=70% height=70%>
	
	
</p>
</details>
	
	
#### :test_tube: Lab 3 - Basics of global and detail routing and configure TritonRoute	
	
<details><summary> Reports </summary>
<p>

**Commands**
	
		to see change from CTS 1 to floorplan/pdn.def
		-echo $::env(CURRENT_DEF) 
		-echo $::env(ROUTING_STRATEGY) 
		-run_routing
	
		read README.md
		-cd ~/Desktop/work/tools/openlane_working_dir/openlane/configuration
		-vim README.md
	
**Outputs**
	
<img src="https://user-images.githubusercontent.com/118953938/215666151-f0423387-da44-4f7d-b1c8-b2a11e4f1075.png" width=60% height=60%>
	
<img src="https://user-images.githubusercontent.com/118953938/215666412-22563704-ab9a-4d54-98db-1263ccfadca2.png" width=70% height=70%>

</p>
</details>
	
	
### :microscope:  TritonRoute Features
	
#### :test_tube: Lab 1 - Routing topology algorithm and final files list post-route	
	
<details><summary> Reports </summary>
<p>
	
**Triton Route**	
* Inputs
	* LEF, DEF, Preprocessed route guides
* Output
	* Detailed routing solution with optimized wire-length and via count
* Constraints
	* Route guide honoring, connectivity constraints and design rules
	
<img src="https://user-images.githubusercontent.com/118953938/215670096-71e92922-f64f-4a5a-84f6-6a5ea0087d0c.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/215670666-7b8e4dcf-68b9-40a0-a831-2f717a3ea426.png" width=40% height=40%>

* Currently, TritonRoute strategy = 0 has been selected.
* The violations may be 0 but the execution may take some time if TritonRoute strategy = 14 is selected.
* As a result, we must manually correct the violations.
	
<img src="https://user-images.githubusercontent.com/118953938/215671346-c46c91c5-208c-4e66-942f-7097e1dc0790.png" width=60% height=60%>
	
<img src="https://user-images.githubusercontent.com/118953938/215672020-9fb78994-34ea-415a-8b6b-32484d7f7fc2.png" width=70% height=70%>
	
Creating a new spef file that requires merged.lef and picorv32a.def	
* Routing guides 
* Extract parasitics where we need to declare the LEF and the DEF first
* Netlist modified due to the antenna diodes insertions happens	
	
<img src="https://user-images.githubusercontent.com/118953938/215672591-64f53b81-dfea-4088-b95e-ca879b56bbaf.png" width=70% height=70%>
	
</p>
</details>	
</p>
</details>	

## :book: Day 20 -  Floorplanning and power planning labs

<details><summary> :mag_right: Theories </summary>
<p>
	
### :mag_right: Floorplanning theory and recap	

**Divisions**
	
Typically, the IC physical design is categorized into full custom and semi-custom design.

* Full-Custom: Designer has full flexibility on the layout design, no predefined cells are used.
* Semi-Custom: Pre-designed library cells (preferably tested with DFM) are used, designer has flexibility in placement of the cells and routing.
	
One can use ASIC for Full Custom design and FPGA for Semi-Custom design flows. The reason being that one has the flexibility to design/modify design blocks from vendor provided libraries in ASIC.[5] This flexibility is missing for Semi-Custom flows using FPGAs (e.g. Altera).
		
<img src="https://user-images.githubusercontent.com/118953938/215805411-db49b39e-23b0-413a-8de8-f8268447fbe1.png" width=70% height=70%>

The **physical design flow** uses the technology libraries that are provided by the fabrication houses. These technology files provide information regarding the type of silicon wafer used, the standard-cells used, the layout rules (like DRC in VLSI), etc.

**Floorplanning** _is the process of identifying structures that should be placed close together, and allocating space for them in such a manner as to meet the sometimes conflicting goals of available space (cost of the chip), required performance, and the desire to have everything close to everything else._

* Floorplanning takes into account the macros used in the design, memory, other IP cores and their placement needs, the routing possibilities, and also the area of the entire design. 
* Floorplanning also determines the IO structure and aspect ratio of the design. A bad floorplan will lead to wastage of die area and routing congestion.
		
</p>
</details>	
	
<details><summary> :test_tube: Labs </summary>
<p>	
	
#### :test_tube: Task 1 : Physical Design Flow
	
<details><summary> Reports </summary>
<p>	

**Commands**
	
		In dc_shell
		 set target_library [list /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsddac.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsdpll.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db]
		set link_library  [list /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsddac.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/avsdpll.db /nfs/png/home/wahabm/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/lib/sky130_fd_sc_hd__tt_025C_1v80.db]
		set symbol_library ""
		read_file -format verilog {/nfs/png/disks/png_mip_gen6p9ddr_0032/wahabm/sky130RTLDesignAndSynthesisWorkshop/day20/VSDBabySoC_ICC2/vsdbabysoc.v}

	
	
	
**Outputs**	
	
<img src="https://user-images.githubusercontent.com/118953938/216206000-21f5ee3c-7bca-4a2c-9ab9-2df2daa80d94.png" width=70% height=70%>
	
<img src="https://user-images.githubusercontent.com/118953938/216227263-92e9eeb1-b971-432a-bab6-1a3e3d2a12f8.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/216229943-3ffcc3ef-1a29-4543-a34b-a648c0267b22.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217576627-a429c360-a433-4960-a579-d38818d8e84c.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/217576767-216f23c7-32ec-4628-ab35-722f51bd2f18.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217576836-a89fccd8-b97e-47c8-9f6e-3a0de475893e.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217576908-0e9aceaf-94c5-4ff1-9f72-6ffc7ea8302e.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/217574959-edf652ac-dd57-4be5-abad-95d37b9869dd.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217575570-a1685f27-a4f4-44a0-b56e-51c850d4381a.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217575951-7577dbe6-0891-4346-bc81-0a4a861c8f04.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217577348-01c7cb0b-b1ad-4d3c-813e-927c8b036d88.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217577623-9a72ad35-4817-4267-86f3-4d5775911d9f.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217578053-e8ae82bc-4838-4df4-ae44-4904418d2615.png" width=80% height=80%>

</p>
</details>		
	
#### :test_tube: Task 2 : Physical design
	
<details><summary> Reports </summary>
<p>	
	
**Files were modified accordingly**
	
<img src="https://user-images.githubusercontent.com/118953938/217581531-845264a1-25b8-4120-bbf8-b0a79d6c45fa.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/217581758-2ca6a642-460e-4aab-a0c1-7e9ec3dc83bc.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217582386-a7aa3a2c-b8a3-45de-9a34-16dfaa3f8780.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/217582727-652978e7-988c-4636-b03b-d77150ab1692.png" width=80% height=80%>
<img src="https://user-images.githubusercontent.com/118953938/217582973-531dd2e7-8ddf-4b30-a110-31c9b308def6.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217583543-693fdeb6-6d85-4bcd-b5b7-8154c912e330.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217583899-7bae85d1-e109-45a0-a46b-dce15deb21b4.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217584262-457e2d9d-ad57-48c7-b330-47ca4a38a750.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/217584573-1846f90c-2fe5-4547-86b5-7a0740db4012.png" width=80% height=80%>

**Opening the layout**

<img src="https://user-images.githubusercontent.com/118953938/218898209-71a1e104-51fe-44a2-bc27-1ed0844490fc.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/219287077-1ea4ace2-9332-4b27-80d6-2233f83b6f2d.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219287284-3a254ca3-5416-4e6f-82f5-d2e751b17b5c.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219287511-132e5509-680a-471f-9b01-b362957fd07f.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/219288170-52c84b03-e6f6-4811-a64d-bc3aaba2d8a0.png" width=50% height=50%>

</p>
</details>
	
</p>
</details>		
	
	
## :book: Day 21 - Placement and CTS labs

<details><summary> :mag_right: Theories </summary>
<p>

Pre-Placement Sanity Checks (need to check the preplacement timing once before going for placement of standard cells)
	* Floating Pins in Netlist
	* Unconstrained Pins
	* Timing
	* Pin direction mismatch, etc.
	
### :mag_right: Placement	
	
1) Standard Cell
	
2) Placement Stages
	* Global Placement-Global placement is very first stage of the placement where _**cells are placed inside the core area for the first time looking at the timing and congestion**_. 
	* Legalization-legalization is an essential step where the overlaps between gates/macros must be removed.
	* Detailed Placement-Refines object locations to legal cell sites and enforces nonoverlapping constraints. The detailed locations enable more accurate estimates of circuit delay for the purpose of timing optimization.

3) Objectives/Quality Checks
	* Congestion
		* How to analyze congestion in VLSI? Congestion Fixes
			* Add placement blockages in channels and around macro corners.
			* Review the macro placement.
			* Reduce local cell density using density screens.
			* Reordering scan chain to reduce congestion.
			* Congestion driven placement with high effort.
			* Continue the iterations until good congestion results.
	* Performance
	* Timing
		* Static timing analysis (STA) is a way of evaluating a design's timing performance by testing for timing violations along all conceivable paths. 
		* Dynamic simulation, which determines the whole behaviour of the circuit for a given set of input stimulus vectors, is another technique to do timing analysis
	* Routability
	* Runtime

4) Clock Tree Synthesis (CTS)
	* Inputs of CTS
		* Placement DB
		* CTS Spec File
	* CTS Steps
		* Clustering
		* DRV Fixing
		* Insertion Delay Reduction
		* Power Reduction
		* Balancing
		* Post-Conditioning

	* CTS Quality Checks
		* Skew
		* Pulse width
		* Duty cycle
		* Latency
		* Clock tree power
		* Signal Integrity and Crosstalk
	* Timing Analysis and Fixing	
	
	
	
</p>
</details>	
	
	
<details><summary> :test_tube: Labs </summary>
<p>	
	
#### :test_tube: Task 1 : Change core utilization from 7% to 40%
	
<details><summary> Reports </summary>
<p>	

**1) 40%**
	
<img src="https://user-images.githubusercontent.com/118953938/219292733-5e07cdbf-75f4-4d24-ab7e-3eacc8a778f7.png" width=60% height=60%>
	
<img src="https://user-images.githubusercontent.com/118953938/219293101-236ba485-03a8-45c5-bc95-8b929703a637.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219294064-e01b267c-464f-4ac2-93aa-a6a99bfc9063.png" width=80% height=80%>

**2) 20% (tryouts)**	
	
<img src="https://user-images.githubusercontent.com/118953938/219294703-fc6c878a-a906-4592-8e01-968938aad9c7.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/219295184-d2ffff4a-ab09-4cc1-b8d8-8ee8e5280025.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219295387-658fc692-9a0c-4b75-8daf-10eacbfec5d7.png" width=80% height=80%>

	
	
</p>
</details>	
	
#### :test_tube: Task 2 : All Reports 
	
<details><summary> Reports </summary>
<p>		
	
Path

<img src="https://user-images.githubusercontent.com/118953938/219325540-a8d9cafe-8f18-4893-8fa0-7280052ceef1.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/219323217-5acacabb-4cbc-4578-91a9-b7e41035f6dd.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/219323544-7f534576-2ba1-424d-837d-c92d61f9bc5b.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/219323789-468ec65e-c8b3-4a1a-8e3a-74cf9b5a7fc8.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219324068-1b91a28e-5e71-470f-b5ec-e04d5e8cc633.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219324309-bc0d31bd-e972-4e48-86f8-b2a5453011fd.png" width=60% height=60%>

	
</p>
</details>	

#### :test_tube: Task 3 : Schematic diagram of the clock connection 
	
<details><summary> Reports </summary>
<p>

<img src="https://user-images.githubusercontent.com/118953938/219325415-3d871848-bc1b-4f47-890b-de7ebab76856.png" width=80% height=80%>

**Steps**
	
<img src="https://user-images.githubusercontent.com/118953938/219326349-3db70cfa-31cc-45e6-a17c-be185fa10018.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219326763-d0067694-c388-4c30-b8ac-811455e35e31.png" width=80% height=80%>

**Output**
	
<img src="https://user-images.githubusercontent.com/118953938/219327080-0440e48a-b369-4125-92af-89ea74ccfbc0.png" width=80% height=80%>

**Steps**
	
<img src="https://user-images.githubusercontent.com/118953938/219327575-ce3ea351-efbd-40e6-b6e4-287970d5fbaa.png" width=80% height=80%>

**Output**
	
<img src="https://user-images.githubusercontent.com/118953938/219327701-1e850fb4-ecf6-4099-8477-9bd54e990739.png" width=80% height=80%>

</p>
</details>	
</p>
</details>	
	
	
## :book: Day 22 - CTS Lab analysis

<details><summary> :mag_right: Theories </summary>
<p>
	
### :mag_right: Clock Tree Synthesis

* The concept of Clock Tree Synthesis (CTS ) is the automatic insertion of buffers/inverters along the clock paths of the ASIC design in order to balance the clock delay to all clock inputs.
* In order to balance clock skew and minimize insertion delay, CTS is performed. 
* Naturally, before CTS, all clock pins are driven by a single clock source and considered as an ideal net.	
	
:black_nib: **Some prerequisites for CTS are:**

	Creating non-default rules (e.g., setting large metal width and spacing for clock routing)
	Setting clock’s max transition, max capacitance, and max fanout
	Selecting which cells (clock buffer, clock inverter) to use during CTS (although clock buffers have equal rise and fall time, to avoid pulse width violations, it is recommended to use clock inverters that balance both rise and fall time simultaneously)
	Setting CTS exceptions	

:black_nib: **Various algo’s used for CTS**
	
<img src="https://user-images.githubusercontent.com/118953938/219407346-c389aa3e-a867-4033-b5c2-6cfe16f25a87.png" width=80% height=80%>

:black_nib: **H-tree algorithm**

	1) Find out all the flops present
	2) Find out the center of all the flops
	3) Trace clock port ot the center point
	4) Now divide the core into two parts, trace both the parts and reach to each center
	5) Then form this center again divide the area into two and again trace till center at both the end
	6) Repeat this algo till the time we reach the flop clock pin.	
	
<img src="https://user-images.githubusercontent.com/118953938/219408919-0cc5e0b4-27ff-4c92-93fd-2fbbcf6da94d.png" width=40% height=40%>
	
:black_nib: **Various CTS checks**

	1) Skew check
	2) Pulse width check
	3) Duty cycle check
	4) Latency check
	5) Power check
	6) Crosstalk Quality check
	7) Delta Delay Quality check 8. Glitch Quality check	
	
:black_nib: **Command used**
	
1) Check if the placement done input is perfect
	* check_legality 

2) Edit those default constraints
	* set_clock_tree_options
	
3) Debug mode	
	* set cts_use_debug_mode true 
	
4) Compiling all the constraints	
	* compile_clock_tree

5) Reporting an actual, relevant skew, latency, interclock latency etc. for paths that are related	
	* report_clock_timing -type -summary/-skew 
	
6) Clock_opt = which performs clock tree synthesis and incremental physical optimization. 
	1. Performs clock tree power optimization 
	2. Synthesizes(Re-Synthesizes) the clock trees
	3. Optimizes the clock trees
	4. Adjusts the I/O timing
	5. Performs RC extraction of the clock nets and computes accurate clock arrival times
	6. Performs placement and timing optimization	
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>	
	
#### :test_tube: Task 1 : Check CTS Status
	
		

**Commands**
	
		check_clock_tree
		check_legality
		report_clock_timing -type summary
		report_clock_timing -type skew
		report_clock_timing -type latency
		report_clock_timing -type transition
	
**Outputs**
	
	
<img src="https://user-images.githubusercontent.com/118953938/219413791-24bb017e-c118-493d-bb2b-d91da03d78dd.png" width=80% height=80%>
	
<img src="https://user-images.githubusercontent.com/118953938/219414717-1b87db61-9400-482d-a992-7b2e3798bd9d.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/219415294-08992bf6-4632-4d59-a4dc-6059f3e93332.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219416389-ba0ab842-b484-46b3-b22f-9cc2eec3aeb4.png" width=50% height=50%>
	
<img src="https://user-images.githubusercontent.com/118953938/219416965-b73693fa-5e12-4ce0-81fb-f4bf3fdeab3a.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/219417274-777a5102-242c-436e-aab9-aa9966c7fc6d.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/219417554-294950dc-6e1b-403e-b0ca-d8dcacee482e.png" width=50% height=50%>

</p>
</details>	
	
## :book: Day 23 - Clock gating technique

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Clock gating
 
:black_nib: **Advanced H-Tree for million flop clock end-points randomly placed**

1) When CTS is performed, power consumption also needs to be taken care of, especially when designing a large number of clocks where the design might induce a larger power, as well as a larger power usage

2) A digital circuit with a lot of clocks would be so huge with many buffers etc when designing its clock tree

3) In order to fix that, the whole chip is sectioned into smaller versions where each section will have its own clock tree, and managed to get a complete routed tree
	
<img src="https://user-images.githubusercontent.com/118953938/219424239-0ab9264b-db4a-47b5-a662-bf972003bc20.png" width=80% height=80%>

:black_nib: **CLock Gating Principle**
	
1) The function of clock gating is to reduce the clock power consumption by cutting off the idle clock cycles	

2) it is inserted synthesis stage and optimized in the implementation stage (Physical Design stage)

3) Three types of Clock Gate(CG):

	CG -> AND gate<br>
	CG -> OR gate<br>
	CG -> universal NAND gate<br>
	
<img src="https://user-images.githubusercontent.com/118953938/219427591-b6d62cd8-27e1-4be6-9323-2f7fb4e59c78.png" width=50% height=50%>

4) Clock gating saves power by pruning the clock tree, at the cost of adding more logic to a circuit. 
	
5) Pruning the clock disables portions of the circuitry so that the flip-flops in them do not have to switch states. Switching states consumes power.	

:black_nib: **Routing**
	
1) Routing is the process of making physical connections between signal pins using metal layers	

2) Following Clock Tree Synthesis (CTS) and optimization, the routing step determines the exact pathways for interconnecting standard cells, macros, and I/O pins.
	
3) There are 3 types of routing
	1) P/G routing
	2) Clock routing
	3) Signal routing: Global routing and Detailed routing	
	
<img src="https://user-images.githubusercontent.com/118953938/219429072-7a4e03f1-269c-49be-bea2-10759912b112.png" width=50% height=50%>
	
	
	
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>	
	
#### :test_tube: Task : Scripts in routing stage
	
**Commands**

	Place and optimize the current design
	-place_opt  

	Synthesize and route the clocks, and then further optimize the design based on the propagated clock latencies
	-clock_opt 

	Run global routing, trace assignment, and detailed routing at once/automatically
	-route_auto 

**Scripts**
	
![image](https://user-images.githubusercontent.com/118953938/219430439-5527e105-dda2-442e-ad82-222f2ff14e35.png)

<img src="https://user-images.githubusercontent.com/118953938/219431713-8b045554-e8bd-4b32-9690-8a2a48b1ff5d.png" width=80% height=80%>
	
</p>
</details>		
	
## :book: Day 24 - Timing violations and ECO

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Introduction to Engineering Change Order (ECO)	
	
1) ECO is how you incorporate last minute changes in your design	

2) ECO will be done on the gate level netlist, but designer needs to edit the gate-level netlist and perform the same changes in RTL
	
3) Ensure that the ECO passes a formal and functional verification before we begin changing the layout. All verifications must be successful before it is moved onto the layout.
	
4) All violations are fixed, and all sign-off checks that were skipped during the PD flow are sealed.	
	
:black_nib: **Steps Performing ECO**

	1) Investigate the problem using the recent database
	2) ECO generation to address the problem
	3) ECO implementation with the recent database
	4) After implementing and fixing the problem, save it in the database for future

:black_nib: **ECO strategies**
	
1) Margin based fixing 
	* Design rule violations(DRV) - max_cap and max_tran 
	* Setup and hold violations
	
2) Selective endpoint biased fixing 
	* With and without margin 
	* With and without slack range
3) Slack based fixing 
	* Setup and hold target slack 
	* Max slack
4) Fix n number paths 
	* Number of paths per group (max_paths) 
	* Number of paths per endpoint (nworst)
5) GBA(group based) and PBA(path-based)fixing
6) Full chip vs reg2reg fixing
7) Leakage fixing using HVT
8) Hierarchical ECO 
	* Top level only 
	* Individual 
	* Replicated hierarchies only 
	* All of the above
9) Physical aware ECO 
	* Routing congestion aware 
	* Cell legalization aware 
	* Buffer on route
	
</p>
</details>

<details><summary> :test_tube: Labs </summary>
<p>	
	
#### :test_tube: Task : Report Timing Reveiw
	
![image](https://user-images.githubusercontent.com/118953938/219445653-4ed3428a-9be4-431d-a60b-370026ea88d5.png)

**Command**
	
		report_timing -from core/CPU_is_add_a3_reg -to core/CPU_Xreg_value_a4_reg[24][31] -path_type full_clock_expanded -capacitance -nets -physical

**Output**
	
![image](https://user-images.githubusercontent.com/118953938/219445904-476646c9-1612-436b-a1a9-519284d845a5.png)

<img src="https://user-images.githubusercontent.com/118953938/219446207-e371c81f-efa8-4401-a485-f9fbefc28f61.png" width=50% height=50%>

**Performing ECO**
* Since the slack was violated, ECO need to be performed to lower the slack
* One of the method is by increasing the cell size
	
**Command**
	
![image](https://user-images.githubusercontent.com/118953938/219446580-1c6129b1-1aa2-485c-a71a-07a2c6ac9d39.png)
	
**Output**	
	
![image](https://user-images.githubusercontent.com/118953938/219446856-c0101c33-15a5-43ab-89d3-d047d58a7484.png)

<img src="https://user-images.githubusercontent.com/118953938/219447567-2ca68cf7-2494-4d59-abf7-4ead97a624af.png" width=70% height=70%>

<img src="https://user-images.githubusercontent.com/118953938/219448794-e17ad871-d29e-468c-8145-a118285e8654.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/219450000-ab430b85-28cf-4792-8d05-d55c6eaad975.png" width=80% height=80%>

**Addition of Decap**
	
<img src="https://user-images.githubusercontent.com/118953938/219452308-4329847e-7ea2-41c4-9c4f-5e0355ab74a1.png" width=60% height=60%>

	report_power
	
<img src="https://user-images.githubusercontent.com/118953938/219452436-6c952c35-d144-4617-aaa7-8adafad0a182.png" width=80% height=80%>

	
	
	
</p>
</details>	
	
## :book: Day 25 - RISC-v core RTL2GDS flow

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Review RTL -> GDS

**From Repo DAY 15** : https://github.com/azrulhakimwahab/sd-training/edit/main/Readme.md#mag_right-sky130_d1_sk2---soc-design-and-openlane

:black_nib: **RTL to GDS flow**
	
* This flow starts with RTL coding and ends with GDS (Graphic Data Stream) file which is the final output of back end design, so this complete flow is also known as RTL to GDS (RTL2GDS) flow.

* GDS ( Graphical Design System or Graphical Data System) is a binary file used in VLSI Design to represent the IC layout.

<img src="https://user-images.githubusercontent.com/118953938/219562708-610a7ec9-777c-4e09-97eb-05d3f8e3b7f4.png" width=60% height=60%>

<img src="https://user-images.githubusercontent.com/118953938/219561041-01cdc1a9-244d-4cf9-8fb3-d5a846b52510.png" width=80% height=80%>
	
	
</p>
</details>

## :book: Day 26 - Introduction to mixed-signal flow

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Understanding mixed signal design	

:black_nib: **What is mixed signal design?**
	
<details><summary> Explainations </summary>
<p>	
	
Mixed signal designs ***combine both analog and digital signals*** within a single design or integrated circuit providing the most powerful features of both analog and digital circuitry in a single chip solution.	
	
Benefits of mixed signal circuit design:
	
	* Reduction in PCB interconnect which results in better power consumption
	* Smaller form factor
	* Reduction in system noise because a mixed signal design leads to a highly simplified overall design with functionality and component integration that reduces the number of high current switching output drivers

**What is signal in electronics?**<br>
A signal is an electromagnetic or electrical current that carries data from one system or network to another. In electronics, a signal is often a time-varying voltage that is also an electromagnetic wave carrying information, though it can take on other forms, such as current.
	
**There are two main types of signals used in electronics**: <br>
analog signals and digital signals	
	
<img src="https://user-images.githubusercontent.com/118953938/219690310-9b9b1b57-a456-4fed-9ed6-86ecbaaf3764.png" width=60% height=60%>
	
<img src="https://user-images.githubusercontent.com/118953938/219691443-1ff98688-ad5d-4410-a008-dca4b01e392c.png" width=60% height=60%>
	
**Mixed-signal chips** <br>
_are those that at least partially deal with input signals whose precise values matter_

	1) This broad class includes RF, Analog, Analog-to-Digital and Digital-to-Analog conversion
	2) More recently, a large number of Mixed-Signal chips where at least part of the chip design needs to measure signals with high precision
	3) These chips have very different Design and Process Technology demands than normal Digital circuits	
	
</p>
</details>	
	
:black_nib: **AMS: Analog and Mixed Signal (digital and analog)**
	
<details><summary> Explainations </summary>
<p>	

**What is Analog and Mixed Signal?**
	
* Analog electronics are devices with a continuous variable signal, while digital electronics provide discrete signals and differentiate only two levels (such as “on” and “off”). 
* As the name implies, mixed-signal devices contain both analog and digital circuits. 
* Mixed-signal designs are cost-effective solutions commonly used to build consumer electronics applications, and this group of specialty devices has seen dramatic growth with the increased use of smartphones and other portable technologies. 
* Processing equipment that provides high reliability and productivity cost-effectively is needed for the economical manufacture of analog and mixed-signal devices.
	
**Challenges in AMS Design and Modeling** [reference](https://www.design-reuse.com/articles/22773/analog-mixed-signal-modeling.html) <
	
	- Design stability in AMS systems is achieved after the design is simulated across all the corners and at all Process, Voltage and Temperature (PVT) conditions. 
	
	- Simulators which support AMS simulation are expensive and slow. In addition, co-simulation setup is a time consuming process. 
	
	- Modeling AMS system involves tradeoff between simulation time and accuracy. 
	
	- Simulink and Ptolemy can capture continuous time behavior, but do not target the design of AMS systems at an architecture level. 
	
	- HDL’s like VHDL-AMS and Verilog-AMS target the design of mixed signal subsystems close to implementation level, but these languages have limited capabilities to provide efficient HW/SW co-design at high level of abstraction. 
	
	- There is a lack in offering seamless design refinement flow for mixed-signal discrete event/continuous time systems and HW/SW systems at architecture level.	
	
	
**AMS: Analog and Mixed Signal Flow**	
	
<img src="https://user-images.githubusercontent.com/118953938/219694920-0d60a9dd-6284-4fbb-a80e-726caf1233bc.png" width=50% height=50%>

**Block diagram representation for mixed signal design**
	
<img src="https://user-images.githubusercontent.com/118953938/219695460-3e98b2fc-5e07-44ba-8c16-81ef2f47a166.png" width=80% height=80%>
	
	
</p>
</details>	
	
	
:black_nib: **Exploring the example of VSDBabySoC**
	
<details><summary> Explainations </summary>
<p>		
	
RVMYTH processor -> digital block<br>
PLL -> analog block<br>
DAC -> analog block (for digital to analog conversion)<br>	
	
For more information, visit here : https://github.com/azrulhakimwahab/sd-training/edit/main/Readme.md#mag_right-ip-cores
	
</p>
</details>	
		
:black_nib: **Introduction to various files**
	
<details><summary> Explainations </summary>
<p>		
	
* **LEF file**- Library Exchange Format file : Physical properties such as width, height etc regarding the standard cells 
	
	a. Tf (technology file) or Tlef (technology lef) -both containing the same information <br>
	b. Cell tf<br>
* **LIBerty file** - contains the timing information of the cells
* **gdsII and OASIS file** - GDSII is a file format similar to JPEG, DOCX, XLSX etc to enable a layout design to be transferred from one place to another(IP owner handoff to PD team, PD team to foundry for fabrication), to be viewed/used for verifications like Physical verification checks by EDA tools	
	
<img src="https://user-images.githubusercontent.com/118953938/219697762-7cde429d-74c3-44ad-b6b5-36c122136ce1.png" width=70% height=70%>

* **Place and Route (PnR) tools**
	* The tool aims to position the standard cell in a manner that will result in the least amount of congestion and the best timing. 
	* Every PnR tool offers a variety of instructions and switches so that users can better optimise the design in terms of timing, congestion, space, and power in accordance with their needs.

This is why we need the following files:

	* LEF file
	* LIB file
	* Tf files (tlu+ file)	
	
<img src="https://user-images.githubusercontent.com/118953938/219698552-39f2e01d-ce87-401d-9601-7ac180022874.png" width=70% height=70%>

_**Sources of various files**_
	
<img src="https://user-images.githubusercontent.com/118953938/219699059-29973ab3-bb85-44b1-8477-d86b1ed0f45e.png" width=70% height=70%>
	
Sources were taken from https://teamvlsi.com/2020/08/inputs-for-physical-design-physical-design-input-files.html
	
</p>
</details>

:black_nib: **IP cores**
	
<details><summary> Explainations </summary>
<p>		
	
**IP cores**
_It consists of a block of logic or data that is used in a semiconductor chip_
	
* The IP cores are usually the intellectual property of a particular person or company
* Also used when making a fieldprogrammable gate array (FPGA) or application-specific integrated circuit (ASIC)
* It created throughout the design process and can be turned into components for reuse
* There are different categories for IP cores including hard IP cores and soft IP cores
	* soft IP core -> can be customized during the physical design phase and mapped to any process technology
	* hard IP core -> has the logic implementation and the physical implementation
* In other words, the physical layout of a hard macro-IP is finished and fixed in a particular process technology.	
	
<img src="https://user-images.githubusercontent.com/118953938/219700729-6233b60d-47c1-4955-84eb-4930651b0fd9.png" width=70% height=70%>

Taken from https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.intel.sg%2Fcontent%2Fwww%2Fxa%2Fen%2Fproducts%2Fdetails%2Ffpga%2Fintellectual-property.html&psig=AOvVaw2USV-2fIVWMyeDtXHDOX81&ust=1676735207691000&source=images&cd=vfe&ved=0CA4QjhxqFwoTCIjV_eHznP0CFQAAAAAdAAAAABAD

**This is how it works in semiconductor industry**
	
<img src="https://user-images.githubusercontent.com/118953938/219701000-8cc492f6-2bff-4101-ab96-a3cdc8631d41.png" width=70% height=70%>
	
</p>
</details>	
		
## :book: Day 27 - Crosstalk

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: 	

:black_nib: **test**
	
<details><summary> Explainations </summary>
<p>	
	
</p>
</details>	
	
</p>
</details>	
	
	
## :book: Day 28 -  Introduction to SkyWater SKY130

<details><summary> :mag_right: Theories </summary>
<p>

### :mag_right: Introduction to SkyWater PDKs and opensource EDA tools	

:black_nib: ** Introduction to Skywater PDK**
	
<details><summary> Explainations </summary>
<p>	
	
</p>
</details>	
	
</p>
</details>		
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
	
