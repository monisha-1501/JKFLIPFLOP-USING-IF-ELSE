# JKFLIPFLOP-USING-IF-ELSE

**AIM:** 

To implement  JK flipflop using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**JK Flip-Flop**

JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.

![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/a649c30b-232b-4558-b188-fd6c09845180)


This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs. The following table shows the state table of JK flip-flop.

![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/c4360742-e8a8-4937-b089-c46c0433f9a3)

 
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop. Present Inputs Present State Next State
 
![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/6c275261-a6d5-4c37-a3a7-1e88ca11c4cd)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
 
![image](https://github.com/naavaneetha/JKFLIPFLOP-USING-IF-ELSE/assets/154305477/5174f41b-0ce0-4329-a372-6d1943ea6673)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

**Procedure**

```
1. Apply the clock signal
The JK flip-flop changes its output only at the active clock edge (usually positive edge).


2. Check reset (if present)
If reset = 1, the output Q becomes 0, regardless of J and K.


3. Observe inputs J and K
Based on their values, the output updates as follows:

J = 0, K = 0 → Output remains the same (No change)

J = 0, K = 1 → Output resets to 0

J = 1, K = 0 → Output sets to 1

J = 1, K = 1 → Output toggles (Q becomes Q̅)



4. Store the output
The new output Q is stored until the next clock edge.
```

**PROGRAM**

/*
Developed by:Monisha D 
RegisterNumber:25007487
*/
```
'''
module jk_flipflop (
    input  J,
    input  K,
    input  clk,
    input  reset,
    output reg Q
);

always @(posedge clk or posedge reset)
begin
    if (reset)
        Q <= 1'b0;          // Reset
    else
        case ({J, K})
            2'b00: Q <= Q;  // No change
            2'b01: Q <= 1'b0; // Reset
            2'b10: Q <= 1'b1; // Set
            2'b11: Q <= ~Q; // Toggle
        endcase
end

endmodule
'''
```

**RTL LOGIC FOR FLIPFLOPS**

![RTL realization for JK flipflop](https://github.com/user-attachments/assets/51d7c07f-d66f-4b48-b484-4f20115bf882)


**TIMING DIGRAMS FOR FLIP FLOPS**

![Waveform for jk flipflop](https://github.com/user-attachments/assets/a8cd3950-9537-4f19-8146-7f4a6885c88c)


**RESULTS**

Thus the JK flipflop is implemented and verified.
