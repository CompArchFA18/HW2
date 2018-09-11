# HW 0b010: Verilog Building Blocks

Due: Friday, September 21st before class

This homework prepares some of the gate level primitives you will use in the design of your processor.  You will reuse these modules in several future designs.  Therefore, the structure and test will be in separate modules.

This homework is to be done individually.

## The Devices

This homework is based on the following three devices:

1. 2-bit decoder with enable (2+1 inputs, 4 outputs)
1. 4:1 (four input multiplexer)
1. 1-bit full adder

For each of these three devices, you will do the following:

1. Write a test bench to test the functionality of the device.
1. Test your test bench against my version of the device.
1. Write your own version of the device.
1. Test your device against your test bench.

## The Test Benches
For each device, first write a test bench that verifies the appropriate behavior of your device.  We have already completed this for you for the 2 bit decoder as an example, so you will only have to write the other two.

The test bench should:

1. Instantiate a copy of the device it is testing (Device Under Test = DUT)
1. Show what the truth table should be
1. Show what the truth table is

## The Behavioral Devices
We've provided versions of each of the three devices in a language subset called "Behavioral Verilog".  Use these versions to test your test benches.  Connect the test bench to the device definition provided and verify that your test bench passes with the given behavioral device.

## The Structural Devices
Create the three devices in Structural Verilog, using only the gate primitives we have already gone over:
```verilog
NOT AND NAND OR NOR XOR
```

Do not use behavioral constructs such as `assign` or `case`.

Give all of your gates a delay of 50 units of time.

## The Write Up
Create a PDF or Markdown file demonstrating your circuits working correctly. It should contain pictures of your test bench results and your waveforms that clearly show the gate propagation delays.  

## Submission
Please submit:

1. Your 3 Verilog device files and 3 test files
2. Your writeup as a PDF or Markdown file
3. The scripts you used to run the tests

Push the work to your repo, then submit a link to your work on Canvas for us to respond to with feedback.

## Hints / Tricks

### Gate delays
In order to model some sort of delay for our gates, simply put these statements at the top of your Verilog source:

```verilog
// define gates with delays
`define AND and #50
`define OR or #50
`define NOT not #50
```

Then, when you go to instantiate an AND, for instance, instead of using just `and`, use `` `AND``. That is, back-tick followed by the define you specified. Think of the back-tick as a macro definition.

That means that the gate, `` `AND``, has a delay of 50 units. Then, in your simulation, you should wait between transitions of the input long enough to allow the signals to propagate to the output of your circuit.

### Signal Declaration
You need to declare all your inputs and outputs and all the intermediate signals you use in your designs.   Thus, if you have the statement:
```verilog
and myandgate(out, in1, in2)
```

You need to have previously declared `out`, `in1`, and `in2`, to be some sort of physical entity (`wire`, `reg`).

### Tutorials
There are some Verilog resources listed on the [course website](https://canvas.instructure.com/courses/1414489/pages/verilog)

