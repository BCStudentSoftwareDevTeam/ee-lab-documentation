---
title: Temperature & Humidity Sensors (Model DHT11, DHT22, AM2302)
description: 
published: true
date: 2023-09-03T04:01:03.202Z
tags: 
editor: markdown
dateCreated: 2023-03-20T23:11:44.129Z
---

In this tutorial, you will learn how to use a DHT11 (Blue one) temperature and humidity sensor and a DHT22/AM2302 (White Ones). Both are pictured below.
![first_picture.png](/temperature_humidity/first_picture.png =400x300)

Here is the [datasheet](https://www.makerguides.com/wp-content/uploads/2019/02/DHT11-Datasheet.pdf) for the DHT11 model.

Here is the [datasheet](https://www.makerguides.com/wp-content/uploads/2019/02/DHT22-AM2302-Datasheet.pdf) for the DHT22/AM2302 model.

In the datasheets you can look for the pin numbers and specifications of the sensors. 

Both sensors work the same way. There are many options for using these including remote weather stations, plant/garden monitoring systems, and home automation projects. 
These sensors have 4 pins but you only have to worry about 3. The pins are numbered in the image below. The other image is a schematic to show what pins are used to connect. The resistor is 10 kΩ, and it is used between the signal and 5V connections. Pin 1 goes to the 5V. Pin 2 goes to the digital pin and in this case we will use D2 on the Arduino board. Pin 3 is not connected to anything. Pin 4 is connected to the ground. 

![combo_2.png](/temperature_humidity/combo_2.png =500x350)

Here is a physical connection on a breadboard below. 

![image5.png](/temperature_humidity/image5.png =700x)

After making the connections, it is time to download two libraries, so you can code the sensors. There are two methods to download the libraries. Method one is used inside Arduino. Method two is downloading zip files and adding them to your Arduino library folder. 

#### METHOD 1
The first thing you do when you are in Arduino is to click on tools and then manage libraries (figure below). Then, search “dht sensor library” for the first one and install the circled one below. Do the same thing for the second, but search “adafruit unified sensor.”

![image10.png](/temperature_humidity/image10.png =500x)

*For the “dht sensor library”*

![image1.png](/temperature_humidity/image1.png =500x)

*For the “adafruit unified sensor"*
![image3.png](/temperature_humidity/image3.png =550x)


#### METHOD 2
In this method, you download 2 zip files below here ([file 1](https://www.makerguides.com/wp-content/uploads/2019/02/DHT-sensor-library-master.zip) & [file 2](https://www.makerguides.com/wp-content/uploads/2019/02/Adafruit_Sensor-master.zip)). Then, you go to the Arduino folder on your PC. Next, you go to the libraries folder and add the zip files there, and it will be installed on your computer now. 

Now that you have the libraries installed and the connections set up you can test the sensor with code. You can use the following code to test it, but before you try you have to select which sensor you are using. You do this by uncommenting the line with the sensor you are using and commenting the others. Pictures will be after code for each sensor. 

Here is the code example for how to use the sensors

```
/* Arduino example code for DHT11, DHT22/AM2302 and DHT21/AM2301 temperature and humidity sensors. More info: www.www.makerguides.com */

// Include the libraries:
#include <Adafruit_Sensor.h>
#include <DHT.h>

// Set DHT pin:
#define DHTPIN 2

// Set DHT type, uncomment whatever type you're using!
//#define DHTTYPE DHT11   // DHT 11 
//#define DHTTYPE DHT22   // DHT 22  (AM2302)
//#define DHTTYPE DHT21   // DHT 21 (AM2301)

// Initialize DHT sensor for normal 16mhz Arduino:
DHT dht = DHT(DHTPIN, DHTTYPE);

void setup() {
  // Begin serial communication at a baud rate of 9600:
  Serial.begin(9600);

  // Setup sensor:
  dht.begin();
}

void loop() {
  // Wait a few seconds between measurements:
  delay(2000);

  // Reading temperature or humidity takes about 250 milliseconds!
  // Sensor readings may also be up to 2 seconds 'old' (its a very slow sensor)

  // Read the humidity in %:
  float h = dht.readHumidity();
  // Read the temperature as Celsius:
  float t = dht.readTemperature();
  // Read the temperature as Fahrenheit:
  float f = dht.readTemperature(true);

  // Check if any reads failed and exit early (to try again):
  if (isnan(h) || isnan(t) || isnan(f)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  // Compute heat index in Fahrenheit (default):
  float hif = dht.computeHeatIndex(f, h);
  // Compute heat index in Celsius:
  float hic = dht.computeHeatIndex(t, h, false);


  Serial.print("Humidity: ");
  Serial.print(h);
  Serial.print(" % ");
  Serial.print("Temperature: ");
  Serial.print(t);
  Serial.print(" \xC2\xB0");
  Serial.print("C | ");
  Serial.print(f);
  Serial.print(" \xC2\xB0");
  Serial.print("F ");
  Serial.print("Heat index: ");
  Serial.print(hic);
  Serial.print(" \xC2\xB0");
  Serial.print("C | ");
  Serial.print(hif);
  Serial.print(" \xC2\xB0");
  Serial.println("F");
}
```

For the DHT11 model uncomment line 11 in the code above. 
For For the DHT22 or AM2302 model uncomment line 12 in the code above. 

After you upload the code, check the serial monitor and you should start getting values for the temperature and humidity. Similar to the image below. 

![image7.png](/temperature_humidity/image7.png)


Now, you can try adding it to other sensors to create a project.
