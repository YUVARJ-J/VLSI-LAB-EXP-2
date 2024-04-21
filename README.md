# SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

## APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## LOGIC DIAGRAM

## ENCODER
![301734849-3cd1f95e-7531-4cad-9154-fdd397ac439e](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/e0686f04-ab98-4b23-b0f7-7bfd04004b32)

**verilog code**
~~~
module encoder(y,a);
input [7:0]y;
output [2:0]a;
or g1(a[0],y[1],y[3],y[5],y[7]);
or g2(a[1],y[2],y[3],y[6],y[7]);
or g3(a[2],y[4],y[5],y[6],y[7]);
endmodule


~~~
**output**
![image](https://github.com/YUVARJ-J/VLSI-LAB-EXP-2/assets/161425982/bb5f006f-7d03-4b69-b53e-2c7137f37078)


## DECODER
![301735010-45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/4a43503a-8dd4-4968-a06c-359e67030439)

**verilog code**
~~~
module decoder(a,y);
input [2:0]a;
output [7:0]y;
and g4(y[0],~a[2],~a[1],~a[0]);
and g5(y[1],~a[2],~a[1],a[0]);
and g6(y[2],~a[2],a[1],~a[0]);
and g7(y[3],~a[2],a[1],a[0]);
and g8(y[4],a[2],~a[1],~a[0]);
and g9(y[5],a[2],~a[1],a[0]);
and g10(y[6],a[2],a[1],~a[0]);
and g11(y[7],a[2],a[1],a[0]);
endmodule

~~~
**output**
![image](https://github.com/YUVARJ-J/VLSI-LAB-EXP-2/assets/161425982/3876ae67-0348-4adb-9a02-7f7fe3a8685d)


## MULTIPLEXER
![301735287-427f75b2-8e67-44b9-ac45-a66651787436](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/f2b7c963-4b8a-4ae6-918e-81248613eec5)

**verilog code**
~~~
module multiplexer(d,s,y);
input [7:0]d;
input [2:0]s;
output y;
wire w0,w1,w2;
wire x0,x1,x2,x3,x4,x5,x6,x7;
not g1(w0,s[0]);
not g2(w1,s[1]);
not g3(w2,s[2]);
and g4(x0,d[0],w0,w1,w2);
and g5(x1,d[1],w0,w1,s[2]);
and g6(x2,d[2],w0,s[1],w2);
and g7(x3,d[3],w0,s[1],s[2]);
and g8(x4,d[4],s[0],w1,w2);
and g9(x5,d[5],s[0],w1,s[2]);
and g10(x6,d[6],s[0],s[1],w2);
and g11(x7,d[7],s[0],s[1],s[2]);
or g12(y,x0,x1,x2,x3,x4,x5,x6,x7);
endmodule

~~~
**output**
![image](https://github.com/YUVARJ-J/VLSI-LAB-EXP-2/assets/161425982/b3dcf51a-8c58-4974-9121-d3d767478039)

## DEMULTIPLEXER
![301735386-1c45a7fc-08ac-4f76-87f2-c084e7150557](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/6dcb6ced-2602-4d6d-951e-3a8c22a279f7)

**verilog code**
~~~
module demux(d,s,y);
input d;
input [2:0]s;
output [7:0]y;
wire w0,w1,w2;
not g1(w0,s[0]);
not g2(w1,s[1]);
not g3(w2,s[2]);
and g4(y[0],d,w0,w1,w2);
and g5(y[1],d,s[0],w1,w2);
and g6(y[2],d,w0,s[1],w2);
and g7(y[3],d,s[0],s[1],w2);
and g8(y[4],d,w0,w1,s[2]);
and g9(y[5],d,s[0],w1,s[2]);
and g10(y[6],d,w0,s[1],s[2]);
and g11(y[7],d,s[0],s[1],s[2]);
endmodule

~~~
**output**

![image](https://github.com/YUVARJ-J/VLSI-LAB-EXP-2/assets/161425982/c93adfdf-94b4-4431-abbb-e43a407a8366)

## MAGNITUDE COMPARATOR
![301735522-b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2](https://github.com/Jayanth-T/VLSI-LAB-EXP-2/assets/106177371/ca9b5ed3-9b51-480a-889e-9474be9e35a1)

**verilog code**
~~~

module comparator(a,b,gr,lt,eq);
input [1:0]a,b;
output reg gr,lt,eq;
always @(*)
begin
if (a>b)
begin
gr=1'b1;
lt=1'b0;
eq=1'b0;
end
else if(a<b)
begin
gr=1'b0;
lt=1'b1;
eq=1'b0;
end
else
begin
gr=1'b0;
lt=1'b0;
eq=1'b1;
end
end
endmodule

~~~
**output**
![image](https://github.com/YUVARJ-J/VLSI-LAB-EXP-2/assets/161425982/f736b3d3-95b9-486b-87ce-69bb1322d1ce)


## RESULT
Thus the Encoder, Decoder, Multiplexer, Demultiplexer and Magnitude Comparator are Synthesis and stimulated Successfully Using Xilinx ISE.

