---
title: RGB Sensor
description: 
published: true
date: 2023-10-30T18:34:11.692Z
tags: 
editor: markdown
dateCreated: 2023-10-30T18:24:46.333Z
---

TCS34725 RGB Sensor Tutorial by Cortez Watkins
 
This sensor measures the red, blue and green lights in the area as well as light sensing values. Below is all the coding for the Arduino code. 
For the wiring, you would connect SDA to pin A4, SCL to A5, GND to GND, and finally Vin to VCC. From there, go to the Sketch tap and hover over Include Library then select Manage Libraries. Once there, type in Adafruit TCS34725 in the search box. Once you find it, install it and then include it on the code itself. Then, copy and paste the code down below. 

~~~#include <Wire.h>
#include "Adafruit_TCS34725.h"
 
// Pick analog outputs, for the UNO these three work well
// use ~560  ohm resistor between Red & Blue, ~1K for green (its brighter)
#define redpin 3
#define greenpin 5
#define bluepin 6
// for a common anode LED, connect the common pin to +5V
// for common cathode, connect the common to ground
 
// set to false if using a common cathode LED
#define commonAnode true
 
// our RGB -> eye-recognized gamma color
byte gammatable[256];
 
 
Adafruit_TCS34725 tcs = Adafruit_TCS34725(TCS34725_INTEGRATIONTIME_50MS, TCS34725_GAIN_4X);
 
void setup() {
  Serial.begin(9600);
  //Serial.println("Color View Test!");
 
  if (tcs.begin()) {
    //Serial.println("Found sensor");
  } else {
    Serial.println("No TCS34725 found ... check your connections");
    while (1); // halt!
  }
 
  // use these three pins to drive an LED
 
  pinMode(redpin, OUTPUT);
  pinMode(greenpin, OUTPUT);
  pinMode(bluepin, OUTPUT);
 
  // thanks PhilB for this gamma table!
  // it helps convert RGB colors to what humans see
  for (int i = 0; i < 256; i++) {
    float x = i;
    x /= 255;
    x = pow(x, 2.5);
    x *= 255;
 
    if (commonAnode) {
      gammatable[i] = 255 - x;
    } else {
      gammatable[i] = x;
    }
    //Serial.println(gammatable[i]);
  }
}
 
 
void loop() {
  float red, green, blue;
  tcs.setInterrupt(false);  // turn on LED
  delay(60);  // takes 50ms to read
  tcs.getRGB(&red, &green, &blue);
  tcs.setInterrupt(true);  // turn off LED
 
  Serial.print("R:\t"); Serial.print(int(red));
  Serial.print("\tG:\t"); Serial.print(int(green));
  Serial.print("\tB:\t"); Serial.print(int(blue));
 
  Serial.print("\n");
 
  analogWrite(redpin, gammatable[(int)red]);
  analogWrite(greenpin, gammatable[(int)green]);
  analogWrite(bluepin, gammatable[(int)blue]);
 
}~~~

Testing: To test the code, go to the Serial Monitor located in the Tools tap. From there, go to the bottom when you see ‘baud’. Select it and pick 9600 baud. Once done, press the Reset button on your Arduino and you should see the RGB Sensor start running. 

For more information, check out this link. 
https://www.makerguides.com/tcs34725-rgb-color-sensor-with-arduino/
