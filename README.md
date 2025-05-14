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

1. Type the program in Quartus software.

2. Compile and run the program.

3. Generate the RTL schematic and save the logic diagram.

Create nodes for inputs and outputs to generate the timing diagram.

For different input combinations generate the timing diagram.

**PROGRAM**

/* Program for 4 Bit Ripple Counter and verify its truth table in quartus using Verilog programming.

```
module RIPPLE(
    input wire clk,        // Clock input
    input wire reset,      // Asynchronous reset
    output wire [3:0] q    // 4-bit output
);

    wire clk1, clk2, clk3;

    // First flip-flop (LSB)
    T_FF tff0 (
        .clk(clk),
        .reset(reset),
        .q(q[0]),
        .clk_out(clk1)
    );

    // Second flip-flop
    T_FF tff1 (
        .clk(clk1),
        .reset(reset),
        .q(q[1]),
        .clk_out(clk2)
    );

    // Third flip-flop
    T_FF tff2 (
        .clk(clk2),
        .reset(reset),
        .q(q[2]),
        .clk_out(clk3)
    );

    // Fourth flip-flop (MSB)
    T_FF tff3 (
        .clk(clk3),
        .reset(reset),
        .q(q[3]),
        .clk_out()
    );

endmodule

// Toggle Flip-Flop Module
module T_FF (
    input wire clk,
    input wire reset,
    output reg q,
    output wire clk_out
);
    assign clk_out = q;  // Output to next stage

    always @(negedge clk or posedge reset) begin
        if (reset)
            q <= 0;
        else
            q <= ~q;
    end
endmodule
```

 Developed by: Naveen Jaisanker RegisterNumber: 212224110039 
*/

**RTL LOGIC FOR 4 Bit Ripple Counter**

![Screenshot 2025-05-14 090029](https://github.com/user-attachments/assets/a08e8c16-2f6c-4ca3-bd96-7dd4f1e44cd2)

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![Screenshot 2025-05-14 091011](https://github.com/user-attachments/assets/cf8c9833-fcef-4fe7-bbe0-69a1d5ee6bc9)


**RESULTS**

Thus, the implementation of 4 bit Ripple Counter using Verilog HDL was successful. 
