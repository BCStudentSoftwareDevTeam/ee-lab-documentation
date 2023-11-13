---
title: TurbiditySensor
description: 
published: true
date: 2023-11-13T19:44:57.614Z
tags: 
editor: markdown
dateCreated: 2023-11-13T19:44:36.383Z
---


Turbidity is the cloudiness or haziness of a fluid caused by large numbers of individual particles that are generally invisible to the naked eye, similar to smoke in the air. The measurement of turbidity is a key test of water quality.

The sensor operates on the principle that when the light is passed through a sample of water, the amount of light transmitted through the sample is dependent on the amount of soil in the water. As the soil level increases, the amount of transmitted light decreases. The turbidity sensor measures the amount of transmitted light to determine the turbidity of the wash water. 


REQUIRED MATERIALS

-Arduino Uno

-Breadboard

-Turbidity Sensor

-Wires

-FTDI Cable





PICTURE OF SENSOR





















TURBIDITY SENSOR SCHEMATICS



PIN ORIENTATION

Black wire - GND
Red wire - 5V
Blue wire - A0 on Arduino Uno

You can also check the below mentioned Youtube video for a clearer representation of the schematics

LIBRARIES

N/A


**CODE**
```
void setup() {
  Serial.begin(9600);
 
}
void loop() {
  int sensorValue = analogRead(A0);
  float voltage = sensorValue * (5.0 / 1024.0);
 
  Serial.println ("Sensor Output (V):");
  Serial.println (voltage);
  Serial.println();
  delay(1000);
}
```





YOUTUBE TUTORIAL

Also helps with the turbidity sensor schematics

https://www.youtube.com/watch?v=POsJc-tM2ZI  