Understanding Quartz Oscillator:

![image](https://github.com/user-attachments/assets/85cd5148-ce2a-4fbd-a08d-ce26c1ef1dc3)

^ from STM Guidelines for Oscillator Design


"Typical" Quartz Oscillator Circuit

![image](https://github.com/user-attachments/assets/01f797e7-4a3a-4e95-945f-4c46850442a9)

^ from STM32L496xx Datasheet

An important number to know when determining the capacitors to use in an oscillator circuit is the load capacitance ($$C_L$$).
This value can be calculated from $$C_{L1}$$ and $$C_{L2}$$, the two external capacitors in the oscillator circuit, and $$C_S$$, the total excess capacitance from the microcontroller, PCB board, etc.

In the STM32L496xx Datasheet, it is specified that $$C_S$$ can be taken as 10 pF (pg 162).

The formula for calculating $$C_L$$ from the previous values is as follows:

$$C_L = \frac{C_{L1} * C_{L2}}{C_{L1} + C_{L2}} + C_S$$

The load capacitance is important because it is used to determine if a given oscillator setup is capable of oscillating.


This is found by calculating the gain ratio margin $$(\frac{g_m}{g_{mcrit}})$$, which is the ratio of the transconductance of the microcontroller to the transconductance of the given oscillator circuit.
- $$g_m$$ is the transconductance of the microcontroller, for the STM32L496xx it is provided in the datasheet as 1.5 $$\frac{mA}{V}$$.
- $$g_{mcrit}$$ is the minimal transconductance necessary to maintain a stable oscillation in a given oscillator circuit.

To calculate $$g_{mcrit}$$, we utilize the following formula provided in the STM Guidelines for Oscillator Design:

$$g_{mcrit} = 4 * ESR * (2 * \pi * F)^2 * (C_0 + C_L)^2$$

where,
- ESR is the Equivalent Series Resistance of the oscillator, provided in the datasheet
- F is the Frequency of the oscillator
- $$C_0$$ is the Shunt Capacitance of the oscillator
- $$C_L$$ is the Load Capacitance of the oscillator

Oscillator Specifications:

![image](https://github.com/user-attachments/assets/8598e5f9-5cee-450d-86bb-195a21757449)

^ from ABM8AIG - 16.000MHz Datasheet

