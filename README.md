# EXP NO :4
# DATE:02/04/2024
# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

**AIM**
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

**APPARATUS REQUIRED:**

Xilinx 14.7
Spartan6 FPGA

**LOGIC DIAGRAM**

SR FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)


JK FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

T FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)


D FLIPFLOP

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)


COUNTER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


  
**PROCEDURE:**
STEP:1 Start the vivado software, Select and Name the New project.

STEP:2 Select the device family, device, package and speed.

STEP:3 Select new source in the New Project and select Verilog Module as the Source type.

STEP:4 Type the File Name and module name and Click Next and then finish button. Type the code and save it.

STEP:5 Select the run simulation and then run Behavioral Simulation in the Source Window and click the check syntax.

STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.

STEP:7 compare the output with truth table.

**VERILOG CODE**

 **SR FLIPFLOP** 
 
 module SR(clk,s,r,rst,q );

input s,r,clk,rst;

output reg q;

always@(posedge clk)

begin

if(rst==1)

q=1'b0;

else

begin

case({s,r})

2'b00: q=q;

2'b01:q=1'b0;

2'b10:q=1'b1;

2'b11:q=1'bx;

endcase

end

end

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/19ef2df8-a1c8-42c9-b01a-d3f69e51b055)

 **JK FLIPFLOP**
 module jk(j,k,clk,rst,Q);

input j,k,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)Q=0;

else

begin

case({j,k})

2'b00:Q=Q;

2'b01:Q=0;

2'b10:Q=1;

2'b11:Q=~Q;

endcase

end

end

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/9a192bb7-5ac1-4073-863e-d4ceacfa262f)

**T FLIPFLOP**
module tff(t,clk,rst,Q);

input t,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else if(t==0)

Q=Q;

else

Q=~Q;

end

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/5fc4a516-f50e-4020-b9e1-64623b9136a0)

**D FLIPFLOP**
module dff(d,clk,rst,Q);

input d,clk,rst;

output reg Q;

always @(posedge clk)

begin

if(rst==1)

Q=1'b0;

else

Q=d;

end

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/fad65d46-97fd-4f86-832e-916aa9a1a303)

**COUNTER**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/442b5e83-98a9-46c0-9a4c-dedda2736565)

**4 bit UPDOWNCOUNTER**
module updown(clk,rst,updown,out);

input clk,rst,updown;

output reg[3:0]out;

always@(posedge clk)

begin

if(rst==1)

out=4'b0000;

else if(updown==1);

out=out-1;

end

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/f079da80-b23f-4e8e-b147-a5b89934d342)

**MOD 10 COUNTER:**

module mod(clk,rst,out);

input clk,rst;

output reg[3:0]out;

always @(posedge clk)

begin

if(rst==1 | out==4'b1001)

out=4'b0000;

else

out=out+1;

end

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/12cf0249-5bff-4ae7-a942-174592aacabe)

**RIPPLE CARRY COUNTER**
module ripple_carry_counter(q, clk, reset);

output [3:0] q;

input clk, reset;

T_FF tff0(q[0], clk, reset);

T_FF tff1(q[1], q[0], reset);

T_FF tff2(q[2], q[1], reset);

T_FF tff3(q[3], q[2], reset);

endmodule

module T_FF(q, clk, reset);

output q;

input clk, reset;

wire d;

D_FF dff0(q, d, clk, reset);

not n1(d, q);

endmodule

module D_FF(q, d, clk, reset);

output q;

input d, clk, reset;

reg q;

always @(posedge reset or negedge clk)

if (reset)

q = 1'b0;

else

q = d;

endmodule

**OUTPUT**
![image](https://github.com/harsha804/VLSI-LAB-EXP-4/assets/122807039/3b5d999a-62a9-49fb-99d2-e75aeabdd616)

**RESULT**
Thus simulate and synthesis JK-Flipflop, SR-Flipflop, T-Flipflop, D-Flipflop And counters was succesfully executed and verified.

