# Processing communication with Arduino

四个按钮分别代表上下左右，控制 process 中的点的位置。

## 程序代码

### Arduino coding

```c
int upPin = 3;
int downPin = 4;
int leftPin = 5;
int rightPin = 6;
int up1,down1,left1,right1;

void setup() {
  pinMode(upPin,INPUT_PULLUP);
  pinMode(downPin,INPUT_PULLUP);
  pinMode(leftPin,INPUT_PULLUP);
  pinMode(rightPin,INPUT_PULLUP);
  Serial.begin(9600);
}

void loop() {

  up1 = digitalRead(upPin);
  down1 = digitalRead(downPin);
  left1 = digitalRead(leftPin);
  right1 = digitalRead(rightPin);
  if(up1 == 0)
  {
    delay(500);
    Serial.write("a");
  }
  else if(down1 == 0)
  {
    delay(500);
    Serial.write("b");
  }
  else if(left1 == 0)
  {
    delay(500);
    Serial.write("c");
  }
  else if(right1 == 0)
  {
    delay(500);
    Serial.write("d");
  }
}
```

### Processing coding

```java
import processing.serial.*;
Serial port;
int a = 300;
int b = 300;

void setup(){
  size(600,600);
  background(200,200,200);
  fill(255,0,0);
  ellipse(a,b,30,30);
  port = new Serial(this,"COM4",9600);
}

void draw()
{
  while(port.available()>0)
  {
    char input = port.readChar(); //read information from Arduino
    switch(input)
    {
      case'a':
      background(200,200,200);
      fill(255,0,0);
      b -= 20;
      ellipse(a,b,30,30);
      break;

      case'b':
      background(200,200,200);
      fill(255,0,0);
      b += 20;
      ellipse(a,b,30,30);
      break;

      case'c':
      background(200,200,200);
      fill(255,0,0);
      a -= 20;
      ellipse(a,b,30,30);
      break;

      case'd':
      background(200,200,200);
      fill(255,0,0);
      a += 20;
      ellipse(a,b,30,30);
      break;
      default:break;
    }
  }
}
```

## 接线模拟

## 实际操作

<div align=center>
   <img src="../img/Pr+Ard_gif.gif" width=400px></img>
</div>

## 魔改版

- 修改颜色和背景
- 圆点显示走动轨迹

### Processing coding

```java
import processing.serial.*;
Serial port;
int a = 300;
int b = 300;

void setup(){
  size(600,600);
  background(255,200,200);
  stroke(255,255,255);
  fill(255,200,200);
  ellipse(a,b,30,30);
  port = new Serial(this,"COM4",9600);
}

void draw()
{
  while(port.available()>0)
  {
    char input = port.readChar(); //read information from Arduino
    switch(input)
    {
      case'a':
      noStroke();
      fill(255,255,255);
      b -= 50;
      ellipse(a,b,30,30);
      break;

      case'b':
      noStroke();
      fill(255,255,255);
      b += 50;
      ellipse(a,b,30,30);
      break;

      case'c':
      noStroke();
      fill(255,255,255);
      a -= 50;
      ellipse(a,b,30,30);
      break;

      case'd':
      fill(255,255,255);
      a += 50;
      ellipse(a,b,30,30);
      break;
      default:break;
    }
  }
}
```

### 实际操作

<div align=center>
   <img src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/Pr%2BArd_gif_modified.gif" width=400px alt="GIF loading..."></img>
</div>
