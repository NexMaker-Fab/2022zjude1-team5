# 课堂练习 1：Button 按钮

Pushbuttons or switches connect two points in a circuit when you press them. This example turns on the built-in LED on pin 13 when you press the button.

## 硬件设备

- Arduino Board
- Momentary button or Switch
- 10K ohm resistor
- hook-up wires
- breadboard

## 代码说明

打开和关闭连接到数字 pin13 的发光二极管（LED）。当按下连接在第 2 针脚上的按钮时，该电路：

- LED 通过 220 ohm 的电阻从 pin13 连接到地
- 按键从 +5V 连接到 pin2
- 10K ohm 电阻从地面连接到 pin2
- 注意：在大多数 Arduinos 上，板子上已经有一个 LED 连接到 pin13。
- 代码来源：[https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button](https://www.arduino.cc/en/Tutorial/BuiltInExamples/Button)

```c
const int buttonPin = 2;     // the number of the pushbutton pin
const int ledPin =  13;      // the number of the LED pin

// variables will change:
int buttonState = 0;         // variable for reading the pushbutton status

void setup() {
  // initialize the LED pin as an output:
  pinMode(ledPin, OUTPUT);
  // initialize the pushbutton pin as an input:
  pinMode(buttonPin, INPUT);
}

void loop() {
  // read the state of the pushbutton value:
  buttonState = digitalRead(buttonPin);

  // check if the pushbutton is pressed. If it is, the buttonState is HIGH:
  if (buttonState == HIGH) {
    // turn LED on:
    digitalWrite(ledPin, HIGH);
  } else {
    // turn LED off:
    digitalWrite(ledPin, LOW);
  }
}
```

## 模拟操作

[Tinkercad](https://www.tinkercad.com/dashboard)

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/emulate.png)

## 实操

### 问题

接口设置错误

### 解决方式

工具-端口-COMX

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/COM.png)

# 课堂练习 2：Analog Input 模拟输入

In this example we use a variable resistor (a potentiometer or a photoresistor), we read its value using one analog input of an Arduino board and we change the blink rate of the built-in LED accordingly. The resistor's analog value is read as a voltage because this is how the analog inputs work.

## 硬件设备

- Arduino Board
- Potentiometer **_or_**
- 10K ohm photoresistor and 10K ohm resistor
- built-in LED on pin 13 **_or_**
- 220 ohm resistor and red LED

## 程序代码

```c
int sensorPin = A0;    // select the input pin for the potentiometer
int ledPin = 13;      // select the pin for the LED
int sensorValue = 0;  // variable to store the value coming from the sensor

void setup() {
  // declare the ledPin as an OUTPUT:
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  // read the value from the sensor:
  sensorValue = analogRead(sensorPin);
  // turn the ledPin on
  digitalWrite(ledPin, HIGH);
  // stop the program for <sensorValue> milliseconds:
  delay(sensorValue);
  // turn the ledPin off:
  digitalWrite(ledPin, LOW);
  // stop the program for for <sensorValue> milliseconds:
  delay(sensorValue);
  Serial.println(analogRead(A0));
  delay(200);
}
```

## 模拟操作

## 硬件图片

<div align=center>
   <img src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/hardware-photo.png" width=500px></img>
</div>

# 课后作业：Hello World

演示了 16x2 的 LCD 显示屏的使用。将 "Hello World!"打印到 LCD 上并显示时间。

LiquidCrystal Library - Hello World

Demonstrates the use a 16x2 LCD display. The LiquidCrystal library works with all LCD displays that are compatible with the Hitachi HD44780 driver. There are many of them out there, and you can usually tell them by the 16-pin interface.

## 程序代码

This sketch prints "Hello World!" to the LCD and shows the time.

```c
// include the library code:
#include <LiquidCrystal.h>

// initialize the library with the numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup() {
  // set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
  // Print a message to the LCD.
  lcd.print("hello, world!");
}

void loop() {
  // set the cursor to column 0, line 1
  // (note: line 1 is the second row, since counting begins with 0):
  lcd.setCursor(0, 1);
  // print the number of seconds since reset:
  lcd.print(millis() / 1000);
}
```

## 实际操作

# 课堂练习 1：超声波传感器+1602 显示屏

## 程序代码

```c
// include the library code:
#include <LiquidCrystal.h>
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
#define TrigPin A4
// __|^|_____________
// 10us or more HITH SIGNAL will drive it work for one time

#define EchoPin A5
// initialize the library with the numbers of the interface pins
int count = 0;

long duration;
// PULSE WIDTH

void setup() {
    // set Serial communication
    Serial.begin(115200);
    // set pin mode
    pinMode(TrigPin, OUTPUT);
    pinMode(EchoPin, INPUT);
    // init pin
    digitalWrite(TrigPin, LOW);
    delay(1);

// set up the LCD's number of columns and rows:
  lcd.begin(16, 2);
}



long getDistance() {
    // trig
    digitalWrite(TrigPin, LOW);
    delayMicroseconds(2);
    digitalWrite(TrigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(TrigPin, LOW);
    // echo
    duration = pulseIn(EchoPin, HIGH);     // unit: us
    return duration * 0.34029 / 2;         // unit: mm
}


void loop() {
      // Print a message to the LCD.
//  lcd.print(count++);
//  lcd.setCursor(0, 1);
  lcd.print(getDistance());
  delay(2000);
  lcd.clear();

}
```

## 实际操作

# Processing communication with Arduino
