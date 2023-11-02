---
title: RGBSensor
description: 
published: true
date: 2023-11-02T23:48:53.290Z
tags: 
editor: markdown
dateCreated: 2023-10-30T18:24:46.333Z
---

## RGB Sensor Tutorial by Cortez Watkins
 
This sensor measures the red, blue and green lights in the area as well as light sensing values. Below is all the coding for the Arduino code. 
For the wiring, you would connect SDA to pin A4, SCL to A5, GND to GND, and finally Vin to VCC. From there, go to the Sketch tap and hover over Include Library then select Manage Libraries. Once there, type in Adafruit TCS34725 in the search box. Once you find it, install it and then include it on the code itself. Then, copy and paste the code down below. 
```
#include <Wire.h>
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
 
}
```
Testing: To test the code, go to the Serial Monitor located in the Tools tap. From there, go to the bottom when you see ‘baud’. Select it and pick 9600 baud. Once done, press the Reset button on your Arduino and you should see the RGB Sensor start running. 

For more information, check out this link. 
https://www.makerguides.com/tcs34725-rgb-color-sensor-with-arduino/

TCS34725 RGB Sensor Tutorial by Cortez Watkins
 
This sensor measures the red, blue and green lights in the area as well as light sensing values. Below is all the coding for the Arduino code. 
For the wiring, you would connect SDA to pin A4, SCL to A5, GND to GND, and finally Vin to VCC. From there, go to the Sketch tap and hover over Include Library then select Manage Libraries. Once there, type in Adafruit TCS34725 in the search box. Once you find it, install it and then include it on the code itself. Then, copy and paste the code down below. 










#include <Wire.h>
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
 
}

Testing: To test the code, go to the Serial Monitor located in the Tools tap. From there, go to the bottom when you see ‘baud’. Select it and pick 9600 baud. Once done, press the Reset button on your Arduino and you should see the RGB Sensor start running. 

For more information, check out this link. 
https://www.makerguides.com/tcs34725-rgb-color-sensor-with-arduino/



Date
Description


02/03
Draft for review
M.R
03/22
Reviewed:
1. Missing Arduino code
2. Missing actual breadboarding wiring picture
W.W

Done M.R








On this page, we will provide information about TCS34725 or color (RGB) sensors. 


A TCS34725 sensor is a digital Light-to-Digital converter that transforms visible light into a digital signal, which can be interpreted by a microcontroller. 

					Figure 1

Applications

RGB LED Backlight Control 
 Light Color Temperature Measurement
 Ambient Light Sensing for Display Backlight Control 
 Fluid and Gas Analysis
 Product Color Verification and Sorting













Here is a picture of the front of TCS3472 Light-to-Digital Converter. 



There are six pins on the front. The numbers are ordered from right to left. 


Pin Number
Pin Name
Description 
1
VIN
Supply voltage
2
GND
IC ground reference
3
3V3
Supply 3.3 volts
4
SCL
Serial clock line
5
SDA
Serial data line
6
INT
Interrupt output, open-drain
7
LED
Light-emitting diode




As you can see, there are two power volts: 5 volts and 3.3 volts. Either of them works perfectly. 

More Description: 

Pin 1: The VIN pin in the TCS34725 color sensor is the input voltage pin, it provides power to the device. The voltage applied to this pin should be within the range specified by the manufacturer to ensure the proper operation of the sensor.

Pin 2: The GND (Ground) pin in the TCS34725 color sensor is used to provide a common reference voltage for the device and the microcontroller. It is connected to the ground potential of the power supply and serves as a return path for electrical current. The GND pin helps to ensure that the voltage levels of the different components in the system remain stable and at a common level, which is necessary for proper communication and operation of the sensor.

Pin 3: The 3V3 in the TCS34725 color sensor refers to the 3.3-volt power supply. This voltage is used to power the device and provide the necessary electrical power for its operation. The 3.3 volts are typically provided by a voltage regulator, which steps down a higher voltage from the power source to the required 3.3 volts. It is important to use a power supply within the specified voltage range to ensure the proper operation of the sensor.

Pin 4: SCL in the TCS34725 color sensor refers to the serial clock line. It is a communication line that is used in the I2C protocol to synchronize the data transfer between the sensor and the microcontroller. The microcontroller sends clock signals on the SCL line to coordinate the data transfer and ensure that the data is transmitted accurately.

Pin 5: SDA in the TCS34725 color sensor refers to the serial data line. It is a communication line that is used in the I2C protocol to transmit data between the sensor and the microcontroller. The SDA line carries data in both directions, from the microcontroller to the sensor and from the sensor to the microcontroller. The data transfer is coordinated by the clock signals sent on the SCL line.

Pin 6: The INT (Interrupt) pin in the TCS34725 color sensor is used to generate an interrupt signal. It is an output pin that is used to indicate to the microcontroller that the sensor has finished measurement and data are available for reading. The INT pin can be configured to generate an interrupt on various events, such as the completion of a measurement or the detection of a certain color threshold. The interrupt signal is used to notify the microcontroller and trigger the appropriate action, such as reading the data from the sensor or processing the data for the application.

Pin 7: The LED in the TCS34725 color sensor refers to the light-emitting diode. It is an integral part of the color sensor and is used to illuminate the object being measured. The LED emits light in the visible spectrum and the reflected light from the object is then captured by the sensor and converted into a digital signal that represents the color information of the object. The LED is typically controlled by the microcontroller, which can turn it on or off as needed for a specific application.


Now let’s connect our RGB color sensor to our Arduino board.

Here’s what the connection should look like:

                                                        Figure 1







Connect: 
The LED pin to any digital pin
SDA data pin to an A4 pin on Arduino Uno.
SCL clock pin with an A5 pin on Arduino Uno.
3.3 V with a 3V3 pin on Arduino Uno
GND with a ground pin on Arduino Uno.

Next, install Adafruit_TCS34725 by going to tools – > manage libraries in your Arduino IDE. After installing the package, put the following code in your Arduino.

#include <Wire.h>
#include "Adafruit_TCS34725.h"
int led = 5;

void setup(void) {
  Serial.begin(9600);

  pinMode (led, OUTPUT); 
  if (tcs.begin()) {
    Serial.println("Found sensor");
  } else {
    Serial.println("No TCS34725 found ... check your connections");
    while (1);
  }
}

void loop(void) {
  uint16_t r, g, b, c;
  tcs.getRawData(&r, &g, &b, &c);
  Serial.print("Red: "); Serial.print(r, DEC); Serial.print(" ");
  Serial.print("Green: "); Serial.print(g, DEC); Serial.print(" ");
  Serial.print("Blue: "); Serial.print(b, DEC); Serial.print(" ");
  Serial.print("Color: "); Serial.print(c, DEC); Serial.print(" ");
  Serial.println(" ");
analogWrite (led, c); 
  delay(100);
}







You should get the following result. 








