# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

/* write all the steps invloved */
```
 1.Type the Verilog program in Quartus Prime to implement the 4-bit Serial-In Serial Out
 (SISO) Shift Register. 2.Compile and run the program to ensure the design is error-free.
 3.Generate the RTL schematic to visualize the cascading D flip-flop connections and
 save it for documentation. 4.Create nodes for the serial input (SI), clock (CLK), and serial
 output (SO) to observe the shifting process during simulation. 5.Simulate the design for
 different input serial data patterns and observe the timing diagrams
```

**PROGRAM**

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

 Developed by:V.KAMALESH VIJAYAKUMAR RegisterNumber:(24011704)
*/
```
module ripple (     
    input clk,     
    input reset,   
    output [3:0] q 
);     
    reg [3:0] q_int;      
    assign q = q_int;      

    always @(posedge clk or posedge reset) begin
        if (reset)              
            q_int[0] <= 1'b0; 
        else              
            q_int[0] <= ~q_int[0]; 
    end      

    genvar i;     
    generate         
        for (i = 1; i < 4; i = i + 1) begin : ripple             
            always @(posedge q_int[i-1] or posedge reset) begin
                if (reset)                      
                    q_int[i] <= 1'b0; 
                else                      
                    q_int[i] <= ~q_int[i]; 
            end         
        end     
    endgenerate 
endmodule
```

**RTL LOGIC FOR 4 Bit Ripple Counter**
![image](https://github.com/user-attachments/assets/d662fe81-e9fd-4165-b2fc-c7d2aaf1db51)


**TIMING DIGRAMS FOR 4 Bit Ripple Counter**
![image](https://github.com/user-attachments/assets/27ad35f3-5ce7-4d9c-99dd-830f87c7fec6)


**RESULTS**
The implementation of 4 Bit Ripple Counter has been done using verilog and validation of their functionality using their functional tables has been verified.
