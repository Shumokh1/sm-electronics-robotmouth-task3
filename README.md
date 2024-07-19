# sm-electronics-robotmouth-task3

This project simulates a robot mouth using an LED matrix connected to an Arduino Uno. The matrix displays a talking mouth. The simulation is done using the Wokwi platform.


## Overview

The project aims to create a simple representation of a robot's mouth using an 8x8 LED matrix. The expressions are controlled by an Arduino Uno, and the simulation is run on Wokwi, an online Arduino simulator.
https://wokwi.com/projects/403424894110618625


## Code

The LED matrix patterns were generated using the [Online LED Matrix Font Generator](https://www.riyas.org/2013/12/online-led-matrix-font-generator-with.html). This tool makes specifying the pin configuration easier.

```cpp
#include <LedControl.h>

int DIN = 12;
int CS =  11;
int CLK = 10;
LedControl lc = LedControl(DIN, CLK, CS, 0);

byte circle[8] = {
    B00000000,
    B00000000,
    B00000000,
    B00111100,
    B01000010,
    B00111100,
    B00000000,
    B00000000
};

byte line[8] = {
    B00000000,
    B00000000,
    B00000000,
    B00000000,
    B00000000,
    B01111110,
    B00000000,
    B00000000
};

void setup() {
    lc.shutdown(0, false);       
    lc.setIntensity(0, 15);      
}

void loop() { 
    for (int i = 0; i <= 7; i++) {
        lc.setRow(0, i, circle[i]);
    }
    delay(100);
    for (int i = 0; i <= 7; i++) {
        lc.setRow(0, i, line[i]);
    }
    delay(100);
}

## Resources
https://youtu.be/TJ76sQpGMlQ?si=zGFA4LhUUzdoos8A
