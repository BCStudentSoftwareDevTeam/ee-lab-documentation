---
title: Ultrasonic sensors
description: 
published: true
date: 2023-03-31T00:27:57.742Z
tags: 
editor: markdown
dateCreated: 2023-03-28T00:37:39.813Z
---

On this page, we will be providing information about the Ultrasonic sensor.

An Ultrasonic sensor is a sensor that emits ultrasonic sensor that would reflect back when they hit objects which allows it to return the distance of that object in proximity.

Here are some pictures taken of the sensor in our B16 lab:

![image4.png](/image4.png =400x)

![sensor.png](/sensor.png =400x)

In the following images, we got the Ultrasonic sensor connected to Arduino and reporting back on the distance of the object in front of it:

![breadboard.png](/breadboard.png =400x)

![breadboard_1.png](/breadboard_1.png =400x)

And here is how the console reports the distances ( in centimeters) :
![serialmonitor.png](/serialmonitor.png =400x)

Here is the Arduino code that made that happen:

```
const int trigPin = 9;
const int echoPin = 10;
// defines variables
long duration;
int distance;
void setup() {
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
  pinMode(echoPin, INPUT); // Sets the echoPin as an Input
  Serial.begin(9600); // Starts the serial communication
}
void loop() {
  // Clears the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  // Sets the trigPin on HIGH state for 10 micro seconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  // Reads the echoPin, returns the sound wave travel time in microseconds
  duration = pulseIn(echoPin, HIGH);
  // Calculating the distance
  distance = duration * 0.034 / 2;
  // Prints the distance on the Serial Monitor
  Serial.print("Distance: ");
  Serial.println(distance);
}
```


And here is a schematic of the necessary connections: 

![schematic.png](/schematic.png =600x)

GND  =====> GND
Echo  =====> Digital Pin 10
Trig    =====> Digital Pin 9
VCC  =====> 5V

### More tutorials and learning resources hyperlinks

[Arduino - Ultrasonic Sensor](https://www.tutorialspoint.com/arduino/arduino_ultrasonic_sensor.htm#:~:text=The%20Ultrasonic%20sensor%20has%20four,GND%20with%20GND%20on%20Arduino.)
[Complete Guide for Ultrasonic Sensor HC-SR04 with Arduino](https://randomnerdtutorials.com/complete-guide-for-ultrasonic-sensor-hc-sr04/)
[How HC-SR04 Ultrasonic Sensor Works & Interface It With Arduino](https://lastminuteengineers.com/arduino-sr04-ultrasonic-sensor-tutorial/)

