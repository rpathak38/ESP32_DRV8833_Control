# ESP32_DRV833_Control
Optimized motor control for DRV8833 using ESP32 MCPWM

### A library to ESP32 control motors using MCPWM

#### Works only with ESP32.

## Contents
 - [About](#about)
 - [Using](#usage)
 - [Releases](#releases)

## About

This library is for control motors with MCPWM of ESP32 board for motors connected with the DRV8833. Code is highly optimized to
both conserve power and maintain robustness.

[![image](https://docs.espressif.com/projects/esp-idf/en/latest/_images/mcpwm-brushed-dc-control.png)
(from Espressif documentation)

It is tested with [DRV8833](http://www.ti.com/lit/ds/symlink/drv8833.pdf) Dual H-Bridge Motor Driver,
and can works with any controller with 4 input pinouts (AIN1, AIN2, BIN1 and BIN2) as DRV8825, A4988.

Not yet working with 6 input pinouts controllers, as L298.


## Usage

###include

```cpp
#include "ESP32MotorControl.h" 	// https://github.com/JoaoLopesF/ESP32MotorControl
```
###instance
- After #include, before setup
```cpp
// MotorControl instance

ESP32MotorControl MotorControl = ESP32MotorControl();
```
###setup

- In the setup function
```cpp

// Attach 2 motors

MotorControl.attachMotors(MOTOR_GPIO_IN1, MOTOR_GPIO_IN2, MOTOR_GPIO_IN3, MOTOR_GPIO_IN4);

```
- To control the motors

```cpp

// To stop all motors

MotorControl.motorsStop();

// To control the motors

MotorControl.motorForward(0, speed);
MotorControl.motorReverse(0, speed);
MotorControl.motorForward(1, speed);
MotorControl.motorReverse(1, speed);
MotorControl.motorsSet(75, -75);

// To get info about motors

speed = getMotorSpeed(0);
forward = isMotorForward(0);
stopped = isMotorStopped(0);

```

## Releases

#### 0.1
- First Beta
#### 0.2
- Revision by Karol Pieniący

