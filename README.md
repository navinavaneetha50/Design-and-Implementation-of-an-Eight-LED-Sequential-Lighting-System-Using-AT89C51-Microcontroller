# Design-and-Implementation-of-an-Eight-LED-Sequential-Lighting-System-Using-AT89C51-Microcontroller
Design and Implementation of an Eight-LED Sequential Lighting System Using AT89C51 Microcontroller using Proteus

overview
This project presents the design and implementation of an eight-LED sequential lighting system using the AT89C51 microcontroller.

Eight LEDs are interfaced with Port 2 (P2.0–P2.7) of the AT89C51. The microcontroller controls the LEDs such that they glow one after another with a predefined time delay, producing a running LED effect.

The project demonstrates basic concepts of 8051 microcontroller programming, GPIO interfacing, bit manipulation, and software delay generation.

Objectives
To interface eight LEDs with the AT89C51 microcontroller.
To understand the operation of 8051 I/O ports.
To generate a sequential LED lighting pattern.
To implement software delay using Embedded C.
To understand bit shifting and port manipulation.
To simulate the circuit using Proteus.

Hardware Requirements

Component	Quantity
AT89C51 Microcontroller	1
LED	8
Resistor 330 Ω	8
Crystal Oscillator 11.0592 MHz	1
Capacitor 33 pF	2
5 V DC Power Supply	1
Breadboard	1
Connecting Wires	As required


Software Requirements
Keil µVision – For Embedded C programming and HEX file generation
Proteus – For circuit simulation

circuit connections
AT89C51                    LED

P2.0 ───── 330Ω ───── LED1
P2.1 ───── 330Ω ───── LED2
P2.2 ───── 330Ω ───── LED3
P2.3 ───── 330Ω ───── LED4
P2.4 ───── 330Ω ───── LED5
P2.5 ───── 330Ω ───── LED6
P2.6 ───── 330Ω ───── LED7
P2.7 ───── 330Ω ───── LED8

working principle
The AT89C51 sends an 8-bit pattern to Port 2. Only one bit is set at a time, causing one LED to glow.
The sequence is:
00000001 → 00000010 → 00000100 → 00001000
     ↓
00010000 → 00100000 → 01000000 → 10000000

Therefore:

LED1 → LED2 →LED3 → LED4 → LED5 → LED6 → LED7 → LED8

embedded c program
```
#include <reg51.h>

void delay(void)
{
     unsigned int i, j;

    for(i = 0; i < 500; i++)
    {
        for(j = 0; j < 120; j++);
    }
}

void main(void)
{
    unsigned char i;

    while(1)
    {
        for(i = 0; i < 8; i++)
        {
            P2 = (1 << i);
            delay();
        }
    }
}
```
Simulation

The circuit can be simulated in Proteus using the following procedure:

Create the AT89C51 circuit.
Connect eight LEDs to Port 2.
Add 330 Ω resistors in series with the LEDs.
Connect the crystal oscillator and capacitors.
Add the reset and power supply connections.
Write the Embedded C program in Keil µVision.
Compile the program and generate the .hex file.
Load the HEX file into the AT89C51 model in Proteus.
Start the simulation.
Observe the sequential LED operation.

project structure

Eight-LED-Sequential-Lighting/
│
├── README.md
│
├── src/
│   └── led_sequence.c
│
├── hex/
│   └── led_sequence.hex
│
├── simulation/
│   └── led_sequence.pdsprj
│
└── images/
    ├── circuit.png
    └── simulation.png
circuit diagram
<img width="1080" height="760" alt="image" src="https://github.com/user-attachments/assets/bacd976e-c7d2-4bb4-b29b-5abf7a37f432" />


output
LED1 → LED2 → LED3 → LED4
                      ↓
LED8 ← LED7 ← LED6 ← LED5

Result
The eight-LED sequential lighting system using the AT89C51 microcontroller** was successfully designed and implemented. The eight LEDs connected to Port 2 of the AT89C51 glowed **sequentially from LED1 to LED8 with a predefined time delay. The sequence was repeated continuously, producing a running-light effect.Thus, the required sequential LED lighting operation was successfully achieved and verified through simulation.




