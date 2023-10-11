---
title: Liquid Crystal Display (LCDs)
description: 
published: true
date: 2023-10-11T19:45:10.396Z
tags: 
editor: markdown
dateCreated: 2023-03-20T23:20:00.781Z
---

On this page, we will be providing information about the LCD Display (1602 A).

An LCD (Liquid Crystal Display) is a type of flat panel display which uses liquid crystals in its primary form of operation.

Here are some pictures taken of the sensor in our B16 lab:
<img src="/lcd_photos/lcd_front.png" alt="drawing" width="500"/> `(fig 1)`
<!-- #![lcd_front.png](/lcd_photos/lcd_front.png)# `(fig 1)` -->

There are usually 2 models of LCD Display. However, both of them have the same design on the front (Fig-1):
![lcd_back_(1).png](/lcd_photos/lcd_back_(1).png)
         `(Fig 2)`

But the design on the back is a bit different; there are models with 16 pins ( Fig-2 ) and others with 4 pins `(Fig-3)`.

![lcd_back_(2).png](/lcd_photos/lcd_back_(2).png)`(Fig 3)`

In the following images, we got an LCD Display connected with an Arduino printing “Hello World”:

![breadboard.png](/lcd_photos/breadboard.png)

Here is a the Arduino code implementation of the LCD  (1):

```
// include the library code:
#include <LiquidCrystal.h>

// initialize the library by associating any needed LCD interface pin
// with the arduino pin number it is connected to
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // Print a message to the LCD.
  lcd.print("  Hello World  ");
}

void loop() {
  // set the cursor to column 0, line 1
  // (note: line 1 is the second row, since counting begins with 0):
  lcd.setCursor(0, 1);
  
}
```

And here is a schematic of the necessary connections: (1)

![schematic.png](/lcd_photos/schematic.png)


### More tutorials and learning resources
[Arduino - LCD](https://arduinogetstarted.com/tutorials/arduino-lcd)

[Using LCD Displays with Arduino](https://www.youtube.com/watch?v=wEbGhYjn4QI)

[Arduino 16×2 LCD Tutorial – Everything You Need to Know](https://howtomechatronics.com/tutorials/arduino/lcd-tutorial/)
