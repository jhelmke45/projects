# Projects

## Table of Contents
* [Table of Contents](#TableOfContents)
* [Hello_CircuitPython](#Hello_CircuitPython)
---

## Robot Arm Project

### Project Description

### Code

```python
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;

int pin1 = 9;
int pin2 = 10;
int pin3 = 11;

int pot1 = A0;
int pot2 = A1;
int pot3 = A2;

double state1 = 90;
double state2 = 90;
double state3 = 90;

double buffer = 50;
int delayLength = 5;

void setup() {
  Serial.begin(9600);
  servo1.attach(pin1);
  servo2.attach(pin2);
  servo3.attach(pin3);
}

void loop() {
  //servo 1
  state1 = analogRead(pot1);
  state1 = map(state1, 0, 1023, 1000, 13500); //map() only returns int, so map to a multiple of 100 and divide to get decimals
  state1 /= 100;
  servo1.write(state1);
  Serial.print(state1);
  Serial.print("     ");
  //servo2
  state2 = analogRead(pot2);
  state2 = map(state2, 0, 1023, 1000, 13500);
  state2 /= 100;
  servo2.write(state2);
  Serial.print(state2);
  Serial.print("     ");
  //servo3
  state3 = analogRead(pot3);
  state3 = map(state3, 0, 1023, 2000, 13500);
  state3 /= 100;
  servo3.write(state3);
  Serial.println(state3);
}
```

### Evidence

### Reflection
