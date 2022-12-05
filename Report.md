# My Respository

## Contents

[DAY 0](https://github.com/azrulhakimwahab/sd-training/blob/main/Report.md#day-0)

[DAY 1](https://github.com/azrulhakimwahab/sd-training/blob/main/Report.md#day-1)

## Day 0-System/Tool Setup Check. GitHub ID creation
### Theory Review
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

#### Basic understanding of System Software interactions

1) Application softwares-*An application, also referred to as an application program or application software, is a computer software package that performs a specific function directly for an end user or, in some cases, for another application.*
2) System Software-*System software is a type of computer program that is designed to run a computer's hardware and application programs.*
    2.1) Compiler-compiler, computer software that translates (compiles) source code written in a high-level language (e.g., C++) into a set of machine-language instructions that can be understood by a digital computer's CPU. Compilers are very large programs, with error-checking and other abilities.<br />
    2.2) Assembler-A software that converts an assembly language code to machine code. It takes basic Computer commands and converts them into Binary Code that Computer's Processor can use to perform its Basic Operations.
3) Hardware-*Hardware refers to the external and internal devices and equipment that enable you to perform major functions such as input, output, storage, communication, processing, and more.* 
as shown below

<img src="https://user-images.githubusercontent.com/118953938/205213514-731d48e5-526e-4525-a472-5247fabe5ad9.png" width=50% height=50%>

Synthesis-<br />
Synthesis is a process of converting RTL (synthesizable Verilog code) into a technology specific Gate level netlist which includes nets, sequential cells, combinational cells and their connectivity. In other words, It is a process of combining pre-existing elements to form something new. It is the conversion of an idea into an implementation.<br />

#### Next Review
1) Logic Synthesis
2) Static Timing Analysis

################################################################################################

### Lab Work

#### Intel Unix System

<img src="https://user-images.githubusercontent.com/118953938/205214388-1e25012b-6851-47a6-9b7c-437779e538ab.png" width=50% height=50%>

Successfully executed!


## Day 1-

### Lab Work
#### Lab 1

<img src="https://user-images.githubusercontent.com/118953938/205256498-ca0e627e-924d-419e-8099-f5d832882c20.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205256649-2699c0ec-b49d-4fab-83af-a2d678915d05.png" width=50% height=50%>

#### Lab 1.1

<img src="https://user-images.githubusercontent.com/118953938/205260137-79f93e7a-ad6b-4879-87ce-18bccbb15ef0.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205260341-e0bfea4e-3a18-4816-aadb-fa914fd0d384.png" width=50% height=50%>
<img src="https://user-images.githubusercontent.com/118953938/205260820-9d56d72a-1eee-4f65-9969-7e56d776150f.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205261274-3b66e0cf-46b1-44d3-9f4c-251b71595e86.png" width=50% height=50%>

#### Lab 2

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


module good_mux (input i0 , input i1 , input sel , output reg y);
always @ (*)
begin
        if(sel)
                y <= i1;
        else

#### Lab 3

##### 1) Invoking YOSYS <br />

<img src="https://user-images.githubusercontent.com/118953938/205570129-9ab774c1-bfc1-4f56-8608-f22952e646a7.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205580276-cca4faf2-9989-4b41-96ca-b1cb20596dda.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205580716-c39e49e1-07ab-414b-8772-8416c03dce3b.png" width=50% height=50%>

<img src="https://user-images.githubusercontent.com/118953938/205584426-033b3a65-620f-4750-9798-6a9e5d12dbb0.png" width=80% height=80%>

<img src="https://user-images.githubusercontent.com/118953938/205584955-2c0c5989-8753-462a-96fc-b7ff1de5228e.png" width=50% height=50%>












