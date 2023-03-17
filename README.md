# Projects

## Table of Contents
* [Table of Contents](#TableOfContents)
* [Robot Arm Project](#Robot_Arm_Project)
---

## Robot_Arm_Project

### Project Description

In this project, we made an articulated robot arm which can be controlled through a few potentiometers. It is designed so that different toolheads can be easily swapped in and out, making use of magnets, meaning it can be used to pick up things, draw with a pencil, grab things with a magnet, or just about anything else. Other toolheads can be easily designed in the future, and be used for all kinds of applications. 

### Code and Wiring

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

<img width="409" alt="wiring" src="https://user-images.githubusercontent.com/113116262/225998745-cab0ba79-55f3-4e7e-80db-314c34f4646b.png">

_Wiring diagram_

### Evidence

[Onshape Link](https://cvilleschools.onshape.com/documents/d6a7e94291a496a5fc988fe2/w/c47db00d9ece1087e6936482/e/6bb8c6e7503eb20d835169f3)

<img width="359" alt="robotArmAssembly" src="https://user-images.githubusercontent.com/113116262/225793507-db353efb-4f28-4f6d-a59c-728306d643d8.png"><img width="362" alt="head" src="https://user-images.githubusercontent.com/113116262/225982749-e140e9e5-97b5-47bf-a474-08dd8dcdea74.png">

_The arm and linkages. The head part contains holes for magnets, so that different toolheads can be easily attached and removed._

<img width="389" alt="baseAssembly" src="https://user-images.githubusercontent.com/113116262/225793579-b0e7cbbe-f3dc-49ca-aeaa-d5d4a7e48327.png"><img width="455" alt="base2" src="https://user-images.githubusercontent.com/113116262/225793529-14874869-1f79-4186-b0c6-c1f6b2e33bd4.png">

_The base parts to hold the arm. One platform is elevated so that a servo can be attached underneath._

<img width="422" alt="commandModule" src="https://user-images.githubusercontent.com/113116262/225985234-31749064-a48e-41a0-a92f-6820d50aad6b.png">

_The seperate plate containing wiring and labelled potentiometer mounts._

![arm1](https://user-images.githubusercontent.com/113116262/225988512-003b75d8-d280-46ab-ab38-a7887f701523.JPG)![arm2](https://user-images.githubusercontent.com/113116262/225988475-c693f362-bce6-4139-813e-7b26e649581f.JPG)


_The fully assembled and functional arm._

### Reflection

In the end, the project is fully functional, and actually moves very smoothly. It took a while to get the movement to be smooth, though, because the servos kept jittering back and forth. After a few different solutions, a lot of troubleshooting, and a complete transition from using CircuitPython and the Metro boards to using Arduino, we found a good solution. We simplified the code a bunch, and that combined with good use of the ```map()``` function resulted in just about zero jittering in all of the servos. 

We didn't run into too many issues with CAD, though we did have to find a solution to our goal of being able to easily swap the toolheads. We ended up settling on using magnets, and implementing them was realitively straightforward. The main linkage of our arm is based off of [this design](https://grabcad.com/library/modular-electromagnetic-robot-arm-1), though we have either edited or replaced most of the parts to customize them for our needs, or to be more efficiently fabricated. This linkage provides a smooth control system for the arm with only two potentiometers, while allowing for a large range of motion and keeping the head level with the ground. 

Overall, I think that this project was pretty successful. It moves well in 3 dimensions, can complete an assortment of tasks, and the head can be easily swapped. It would have been cool if the heads were automatically interchangeable and didn't require human interference, but the system we have is pretty seamless. 
