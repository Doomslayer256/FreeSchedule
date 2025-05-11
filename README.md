# FreeSchedule

A **basic scheduler** for Raspberry Pi Pico, designed for use in the **Arduino IDE environment**.  
This library provides a simple, non-blocking task scheduler that allows multiple tasks to run at predefined intervals without using `delay()`. Ideal for projects that require multitasking without the complexity of an RTOS like FreeRTOS.

---

## Features

- Lightweight and efficient.
- Runs multiple tasks without blocking the main loop.
- Easy to use with minimal setup.
- Supports task addition, removal, and status monitoring.

---

## Installation

1. Download or clone this repository.
2. Place the `FreeSchedule` folder in your Arduino libraries directory (`Documents/Arduino/libraries/`).
3. Restart the Arduino IDE.

---

## Usage

```cpp
#include <FreeSchedule.h>

FreeSchedule scheduler;

void ledTask1() {
  static bool on = false;
  digitalWrite(2, on);
  on = !on;
  Serial.println("Task: Blink1, Interval: 500ms");
}

void ledTask2() {
  static bool on = false;
  digitalWrite(3, on);
  on = !on;
  Serial.println("Task: Blink2, Interval: 1000ms");
}

void setup() {
  Serial.begin(9600);
  pinMode(2, OUTPUT);
  pinMode(3, OUTPUT);

  scheduler.addTask("Blink1", ledTask1, 500);  // Blink every 500ms
  scheduler.addTask("Blink2", ledTask2, 1000); // Blink every 1000ms
}

void loop() {
  scheduler.run();  // Run the scheduler
}

```
This document written by AI sorry for mistakes.
