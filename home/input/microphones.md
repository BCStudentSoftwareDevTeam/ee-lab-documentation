---
title: Microphones
description: 
published: true
date: 2023-09-03T05:28:35.432Z
tags: 
editor: markdown
dateCreated: 2023-03-20T23:15:10.732Z
---

# Microphone Sensor
In this tutorial, you will learn how to use a Microphone Sound Sensor Module, pictured below:

![sen-17-010-1.png](/microphone/sen-17-010-1.png)


The sound sensor has a microphone in it which detects the intensity of the sound. Inside the microphone, there is a diaphragm. When the clap sound or voice strikes the diaphragm, it vibrates and changes the capacitance. With the changing of capacitance, voltage changes and that’s how the module works.

REQUIRED MATERIALS
### 
-Arduino Uno

-Breadboard

-Microphone Sensor

-Wires

-FTDI Cable

Wiring and Schematics
### 
VCC ---->  5V(Red wire)
GND(Breadboard) ----> GND on Arduino(Black wire)
LED ----> D13 on Arduino Uno(Blue wire)
Output(Microphone Sensor) ----> GND on Arduino Uno(Black wire)
GND(Microphone Sensor) ----> D7 on Arduino(Yellow wire)
VCC(Microphone) ----> Power on Arduino Uno(Red wire)

  ![captujjre.png](/microphone/captujjre.png)

The code
### 
The implementation of the Microphone sensor on Arduino does not require the use of any library.
Here is how it is implemented:
```
int ledPin=13;
int sensorPin=7;
boolean val =0;


void setup(){
  pinMode(ledPin, OUTPUT);
  pinMode(sensorPin, INPUT);
  Serial.begin (9600);
}
 
void loop (){
  val =digitalRead(sensorPin);
  Serial.println (val);
  // when the sensor detects a signal above the threshold value, LED flashes
  if (val==HIGH) {
    digitalWrite(ledPin, HIGH);
  }
  else {
    digitalWrite(ledPin, LOW);
  }
}

```