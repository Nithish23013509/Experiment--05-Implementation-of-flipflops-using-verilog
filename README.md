# NAME: NITHISH S
# REFERENCE NUMBER:23013509
# Experiment--05-Implementation-of-flipflops-using-verilog
### AIM: To implement all the flipflops using verilog and validating their functionality using their functional tables
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 
# PROCEDURE
1. TYPE THE PROGRAM IN QUARTUS SOFTWARE.
2. COMPILE AND RUN THE PROGRAM.
3. GENERATE THE RTL SCHEMATIC AND SAVE THE LOGIC DIAGRAM.
4. CREATE NODES FOR  INPUTS AND OUTPUTS TO GENERATE THE TIMING DIAGRAM.
5. FOR DIFFERENT INPUT COMBINATIONS,GENERATE THE TIMING DIAGRAM
   
SR Flip-Flop
SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

![image](https://user-images.githubusercontent.com/36288975/167910294-bb550548-b1dc-4cba-9044-31d9037d476b.png)

 
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable.
The following table shows the state table of SR flip-flop.


![image](https://user-images.githubusercontent.com/36288975/167910648-ced88e69-869c-42e2-9718-a285a3902446.png)


Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop.
Present Inputs	Present State	Next State


![image](https://user-images.githubusercontent.com/36288975/167908180-5fc9d589-1cb5-41f5-b2c8-927e04f5f387.png)

By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

![image](https://user-images.githubusercontent.com/36288975/167908214-25b30a54-db20-4bcb-9385-5f93a1982a09.png)

 
The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is
Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)
# PROGRAM
```
module sr(S,R,clk,Q,Qbar);
input S,R,clk;
output reg Q;
output reg Qbar;
initial Q=0;
initial Qbar=1;
always @(posedge clk)
begin
Q=S|((~R)&Q);
Qbar=R|((~S)&(Qbar));
end
endmodule
```
# RTL LOGIC FOR SR-FLIPFLOP

![292769065-ce5a7829-502e-4b27-b0e9-abdda7a25b0a](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/df77c8a0-8c26-40b6-b277-d7c6ec4a2335)

# TRUTH TABLE FOR SR-FLIPFLOP
![292769105-e38c80df-9eaf-45cc-a7bc-1dc4b9161468](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/63f2bdec-eb93-4823-aa10-8f167e77140a)
# TIMING DIAGRAM FOR SR-FLIPFLOP
![292769117-6ae04ff9-eb5d-4025-9294-2c2b8b34460d](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/480af6c7-4baa-4fb8-a138-29031d1fbcfa)

### D Flip-Flop
D flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, D latch operates with enable signal. That means, the output of D flip-flop is insensitive to the changes in the input, D except for active transition of the clock signal. The circuit diagram of D flip-flop is shown in the following figure.
 
This circuit has single input D and two outputs Qtt & Qtt’. The operation of D flip-flop is similar to D Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable.
The following table shows the state table of D flip-flop.
![image](https://user-images.githubusercontent.com/36288975/167908342-e03f0cbb-5958-43bb-b74a-5e3ec2341675.png)

![image](https://user-images.githubusercontent.com/36288975/167910325-aeef0739-0a54-40e2-bebd-6f5fa0cad10e.png)



Therefore, D flip-flop always Hold the information, which is available on data input, D of earlier positive transition of clock signal. From the above state table, we can directly write the next state equation as
Qt+1t+1 = D



![image](https://user-images.githubusercontent.com/36288975/167908850-d39d07ba-7f9d-490a-b9f2-274e189fd047.png)

Next state of D flip-flop is always equal to data input, D for every positive transition of the clock signal. Hence, D flip-flops can be used in registers, shift registers and some of the counters.
# PROGRAM
```
module d(d,clk,q,qbar);
input d,clk;
output q,qbar;
reg q,qbar;
always @(posedge clk)
begin
q=d;
qbar=~q;
end
endmodul
```
# RTL LOGIC FOR D-FLIPFLOP
![292769160-7d8c2735-9f97-4117-8555-dc664f6a0066](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/ee870042-c4fb-42b6-995e-f903b375f0fd)

# TRUTH TABLE FOR D-FLIPFLOP

![292769171-11eb80fe-1f9c-4357-b1c6-294a7dd20480](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/63a45aca-d4ed-4760-a5df-0bca5dbb8b8e)
# TIMING DIAGRAM FOR D-FLIPFLOP
![292769185-e9863b55-f811-4850-8045-d31129cbf40c](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/7332000e-8d56-4937-bc74-7bfe41529c6a)


### JK Flip-Flop
JK flip-flop is the modified version of SR flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of JK flip-flop is shown in the following figure.
![image](https://user-images.githubusercontent.com/36288975/167910378-d2d984a7-2815-4d17-8c41-ee4bdf59ec24.png) 

 
This circuit has two inputs J & K and two outputs Qtt & Qtt’. The operation of JK flip-flop is similar to SR flip-flop. Here, we considered the inputs of SR flip-flop as S = J Qtt’ and R = KQtt in order to utilize the modified SR flip-flop for 4 combinations of inputs.
The following table shows the state table of JK flip-flop.


![image](https://user-images.githubusercontent.com/36288975/167908575-59c35afb-50d3-46a2-888c-47478a3179d5.png)

Here, Qtt & Qt+1t+1 are present state & next state respectively. So, JK flip-flop can be used for one of these four functions such as Hold, Reset, Set & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of JK flip-flop.
Present Inputs	Present State	Next State

![image](https://user-images.githubusercontent.com/36288975/167908664-c854ffe9-0bd3-44c2-bfa6-e53928181c69.png)


By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. Three variable K-Map for next state, Qt+1t+1 is shown in the following figure.
 
 
 ![image](https://user-images.githubusercontent.com/36288975/167908688-fa93c3e9-8323-4864-947d-c11d163d5a90.png)

The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is
Q(t+1)=JQ(t)′+K′Q(t)Q(t+1)=JQ(t)′+K′Q(t)

#PROGRAM
```module jk(J,K,clk,Q,Qbar);
input J,K,clk;
output reg Q;
output reg Qbar;
initial Q=0;
initial Qbar=1;
always @(posedge clk)
begin
Q=(J&(~Q))|((~K)&Q);
Qbar=((~J)&(Qbar))|K&(~Qbar);
end
endmodule
```
# RTL LOGIC FOR JK-FLIPFLOP
![292769220-ac2b29a9-44ad-4328-b2b1-3fd26e0e16d6](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/4262a70c-111d-47ec-9c0f-adfe1f65557e)

#TRUTH TABLE FOR JK-FLIPFLOP

![292769239-b3dd7c30-a15d-4a98-b1d3-50dfe7e3a377](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/56033d5b-cb75-4adf-aa5a-217d7058d469)

#TIMING DIAGRAM FOR JK-FLIPFLOP
![292769258-4325b01a-7704-4ccc-9030-7899d9518380](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/8b3c3ac2-f422-4016-96c2-ef82dc15c4f3)


### T Flip-Flop
T flip-flop is the simplified version of JK flip-flop. It is obtained by connecting the same input ‘T’ to both inputs of JK flip-flop. It operates with only positive clock transitions or negative clock transitions. The circuit diagram of T flip-flop is shown in the following figure.

![image](https://user-images.githubusercontent.com/36288975/167911534-5f3c445d-bc68-46e2-9a9c-7efce5febc60.png)



This circuit has single input T and two outputs Qtt & Qtt’. The operation of T flip-flop is same as that of JK flip-flop. Here, we considered the inputs of JK flip-flop as J = T and K = T in order to utilize the modified JK flip-flop for 2 combinations of inputs. So, we eliminated the other two combinations of J & K, for which those two values are complement to each other in T flip-flop.
The following table shows the state table of T flip-flop.



Here, Qtt & Qt+1t+1 are present state & next state respectively. So, T flip-flop can be used for one of these two functions such as Hold, & Complement of present state based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of T flip-flop.
Inputs	Present State	Next State


![image](https://user-images.githubusercontent.com/36288975/167909015-53aa9450-3f28-4202-887a-79d88228f8a0.png)

From the above characteristic table, we can directly write the next state equation as
Q(t+1)=T′Q(t)+TQ(t)′
⇒Q(t+1)=T⊕Q(t)


# PROGRAM 
```
module t(clk,T,q,qbar);
input clk,T;
output q,qbar;
reg q,qbar;
always @(posedge clk)
begin
q=(T&~q)|(~T&q);
qbar=~q;
end
endmodule
```

### RTL LOGIC FOR T-FLIPFLOPS 

![292769306-84e87d04-32da-408f-a5eb-1a5b3cd068d2](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/f7e093b3-7708-4df8-8cc1-ab1e804bed48)
# TRUTH TABLE FOR T-FLIPFLOP
![292769335-0fc64a53-3242-44cc-b95a-6f512c2ca057](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/0c79af5b-7c9a-4148-acd6-9cafb65168bc)


### TIMING DIGRAMS FOR T-FLIP FLOPS 

![292769344-b1c6145d-144d-48fb-849a-2ac485393e24](https://github.com/Nithish23013509/Experiment--05-Implementation-of-flipflops-using-verilog/assets/149038138/0388fd7c-2f5c-4df0-bbf6-4dd7ab424279)

### RESULTS 

Thus implementation of SR,JK,D and T flipflops using nand gates are done sucessfully

