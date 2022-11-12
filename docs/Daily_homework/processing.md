# Catch the Spark

眼睛会跟随鼠标移动，鼠标点击可以出现火花，键盘按键可以眨眼。

主要分为两部分

1. 绘图  
   a. 眼睛  
   b. 火花
2. 动作交互  
   a. 瞳孔跟随鼠标运动  
   b. 通过键盘按键控制眨眼  
   c. 点击鼠标出现火花

## STEP 1：绘图

### 眼睛

```Java
  noStroke();
  fill(255);
  ellipse(238, 300, 120, height);
  fill(255);
  ellipse(382, 300, 120, height);
  fill(0);
  ellipse(mouseX/6+188, mouseY/6+250, 60, 60);
  fill(0);
  ellipse(mouseX/6+332, mouseY/6+250, 60, 60);
```

- 眼白和瞳孔通过 ellipse 绘制，所需参数参考 processing[官网教程](https://processing.org/reference/ellipse_.html)

### 火花

```Java
  stroke(b);
  line(mouseX-8, mouseY, mouseX-16, mouseY);
  line(mouseX+8, mouseY, mouseX+16, mouseY);
  line(mouseX+5, mouseY+8, mouseX+8,mouseY+13);
  line(mouseX-5, mouseY+8, mouseX-8,mouseY+13);
  line(mouseX+5, mouseY-8, mouseX+8,mouseY-13);
  line(mouseX-5, mouseY-8, mouseX-8,mouseY-13);
```

- 火花由六个线条组成，line 所需参数参考 processing[官网教程](https://processing.org/reference/line_.html)
- 火花位置由鼠标位置决定，在鼠标点击点周围出现

## STEP 2：动作交互

### 瞳孔跟随鼠标运动

屏幕大小 600\*600，眼白大小 120\*120，为将瞳孔大部分框在眼白内，在鼠标运动横跨屏幕的时候，瞳孔跨越大半个眼白，且原点在眼白中心，因此代码为：

```Java
  fill(0);
  ellipse(mouseX/6+188, mouseY/6+250, 60, 60);
  fill(0);
  ellipse(mouseX/6+332, mouseY/6+250, 60, 60);
```

### 通过键盘按键控制眨眼

通过改变 ellipse 高度来体现眨眼

- 在最开始设置 ellipse 高度为 120

```Java
//height是眼睛的高度
float height = 120;
```

- 在键盘按下的时候，将高度改为 0.3，因为改成 0 就直接消失了，没有眨眼的感觉

```Java
  if (keyPressed) {
    height = 0.3;
  }
```

- 在眨眼 1000 毫秒后，自动睁开，高度变回 120

```Java
if (millis()>1000) {
    height = 120;
  }
```

### 点击鼠标出现火花

通过改变描边颜色来让火花能被看见

- 首先定义火花为黑色，隐藏在背景中看不到

```Java
int b = 0;
```

- 在鼠标点击后，描边变色，可以被看到

```Java
  if (mousePressed) {
    b = 200;
  }
```

- 在 1000 毫秒后火花自动消失（变为黑色）

```Java
  if (millis()>1000) {
    height = 120;
    b = 0;
  }
```

## 最终呈现

### 完整代码

```Java
//height是眼睛的高度
float height = 120;

//b是火花描边的颜色
int b = 0;

void setup() {
  size(600, 600);
  noStroke();
  loop();
}

void draw() {
  background(0);

  //眨眼
  if (keyPressed) {
    height = 0.3;
  }

  //火花
  if (mousePressed) {
    b = 200;
  }

  //火花形状
  stroke(b);
  line(mouseX-8, mouseY, mouseX-16, mouseY);
  line(mouseX+8, mouseY, mouseX+16, mouseY);
  line(mouseX+5, mouseY+8, mouseX+8,mouseY+13);
  line(mouseX-5, mouseY+8, mouseX-8,mouseY+13);
  line(mouseX+5, mouseY-8, mouseX+8,mouseY-13);
  line(mouseX-5, mouseY-8, mouseX-8,mouseY-13);

  //眼睛
  noStroke();
  fill(255);
  ellipse(238, 300, 120, height);
  fill(255);
  ellipse(382, 300, 120, height);
  fill(0);
  ellipse(mouseX/6+188, mouseY/6+250, 60, 60);
  fill(0);
  ellipse(mouseX/6+332, mouseY/6+250, 60, 60);

  //眨眼后睁眼，火花熄灭
  if (millis()>1000) {
    height = 120;
    b = 0;
  }
}
```

### GIF 展示

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/Catch_the_Spark.gif)
