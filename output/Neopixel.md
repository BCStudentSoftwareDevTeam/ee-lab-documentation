---
title: Neopixel Strips
description: 
published: true
date: 2023-04-19T01:31:48.715Z
tags: 
editor: markdown
dateCreated: 2023-04-19T01:10:02.805Z
---

# Neopixel LED Strip
The Neopixel RGB LED strip is a strip of LEDs that the color and brightness of each LED on the strip can be controlled individually. In this tutorial we are going to learn how to useArduino to control Neopixel RGB LED strips. To control all LEDs on the Neopixel strip, we just need to use a single Arduino pin.

![strip.png](/neopixel/strip.png)

REQUIRED MATERIALS
### 

-Arduino Uno

-Breadboard

-Neopixel RGB LED Sensor strip

-Wires

-FTDI Cable


Wiring and Schematics
### 

![stttttttttttttttttttttttt.png](/neopixel/stttttttttttttttttttttttt.png)


Black wire ---> GND
Red wire  ---> 5V
Yellow wire ---> D6

The Libraries
### 

Adafruit Neopixel Library by Adafruit
1) Either download it from here :
`https://github.com/adafruit/Adafruit_NeoPixel
`

2) Or, open Arduino software and click “Sketch” at the top left hand corner of the screen, go down the list and click on “Include Library”. Then click on “Manage Libraries” or “Ctrl+Shift+I”. From there just search for the Libraries mentioned above and download the Adafruit Neopixel library.

The code
### 
Here is how the Neopixel LED Strip is implemented on Arduino :
```
#include <Adafruit_NeoPixel.h>

int LEDPIN = 6;
int NUMPIXELS = 8;
Adafruit_NeoPixel pixels = Adafruit_NeoPixel(NUMPIXELS, LEDPIN, NEO_GRB + NEO_KHZ800);

int delayval = 500; 
void setup() {
  pixels.begin(); 
}

void loop() {
  pixels.setPixelColor(0, pixels.Color(150,0,0)); 
  pixels.setPixelColor(1, pixels.Color(0,150,0)); 
  pixels.setPixelColor(2, pixels.Color(0,0,150)); 
  pixels.setPixelColor(3, pixels.Color(50,50,50)); 
  pixels.setPixelColor(4, pixels.Color(0,0,0)); 
  pixels.setPixelColor(5, pixels.Color(25,25,25)); 
  pixels.setPixelColor(6, pixels.Color(90,50,170)); 
  pixels.setPixelColor(7, pixels.Color(150,50,0)); 
  
  pixels.show(); 
  delay(delayval); 
 
  pixels.setPixelColor(0, pixels.Color(75,0,75)); 
  pixels.setPixelColor(1, pixels.Color(75,75,0)); 
  pixels.setPixelColor(2, 0,  75, 75); 
  pixels.setPixelColor(3, 100,100,100); 
  pixels.setPixelColor(4, 0x661133); 
  pixels.setPixelColor(5, 0x054411); 
  pixels.setPixelColor(6, pixels.ColorHSV(20,100,100)); 
  pixels.setPixelColor(7, pixels.ColorHSV(75,25,25));
  
  pixels.show(); 
  delay(delayval); 
}

```