---
title: PhotoResistor
description: 
published: true
date: 2023-04-18T23:53:17.431Z
tags: 
editor: markdown
dateCreated: 2023-03-31T00:16:57.528Z
---

The Pulse Sensor is a well-designed low-power plug-and-play heart-rate sensor for the Arduino. The pulse sensor shines light through the skin and measures the reflection with the photodetector. The working of the sensor can be divided into two parts, one is heart rate measurement and another is blood oxygen level measurement.

![image1.png](/pulsesensor/image1.png)

###### Materials
- PhotoResistor x 1
- 220 ohms resistor x 1
- Jumper wires x 3
-  Breadboard x 1
-  Arduino Uno x 1

In our lab, we used the Pulse sensor to generate graphs that indicate the cardiovascular performance of an individual However, please note that these pulse sensors are cheap and are not very precise.

The setup will look like the following 
![image1.png](/photoresistor/image1.png =450x)
![breadboard.png](/photoresistor/breadboard.png =600x)

The red wire is connected from one end of the photoresistor to the 5V port
The black wire connects from the end of the resistor to any of the GND port
The blue wire connects from the end of the photoresistor to the Analog port (A0)


The library code is the following 
````
int photoPin(){
	Serial.begin(9600);
}

void loop(){
	int light = analogRead(photoPin);
  Serial.printlin(light);
  delay(100);
}

````
In the code found above we set the photo pin equal to analog(0). We also print the lux measurement of the photoresistor. Also, it's important to add a delay of 100ms to properly read the lux values.
Next, we go to the tools and click on serial print. To test the code, you can either turn off the lights or put your hands covering the photoresistor. 

What were the observations of the values of resistance as decreased brightness on the photoresistor?

The graph plots Voltage as a function of flux
As you can see the resistance decreases as brightness decreases


##### External Resources
[Link](https://www.programmingelectronics.com/serial-begin-9600/#:~:text=Serial%20begin%20is%20used%20to,require%20the%20serial%20print%20function.)

