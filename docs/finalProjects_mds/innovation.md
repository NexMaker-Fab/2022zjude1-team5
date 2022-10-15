# 玩法 1

## 外观

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/appearance1.png)

<center>图 1</center>

## 规则

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/Untitled.png)

<center>图 2</center>

- 养殖厂、种植厂、堆肥厂、加工厂四大模块保持不变
- 农副产品可进行选择
- 连接后，互动正确给予正向反馈，如养殖业的牛连接到加工厂的牛奶

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/table.png)

**闯关制概念**

- 每局游戏设置要达成的目标或者分数
- 模块可以独立运作，一个模块搭建完后，提示（如灯光闪烁提示）可以连接下个模块。
- 连接后，模块之间的互动。如养殖业的牛 连接到 加工厂的牛奶；互动正确给予正向反馈，如积分。
- 补充：考虑上发电的话，还可以给整个游戏预设环境，例如预设在中国西部，风力发电会更合适；长江流域水力发电可能更合适（甚至各个区域也有适合的种植业和养殖业）

## 交互形式

### 传达游戏目标

- 例，风力发电-测小风车的转速，转速到达 xx 发电模块才能正常运转

### 游戏过程

- 连接正确给予声光反馈（不同内容发出相应声音）

### 游戏进程

- 点阵 LED 简单显示得分/倒计时

<div class="three-in-a-row pic-with-caption">
    <img class=three-in-a-row src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/screen1.png" style="align-self: center"></img>
    <img class=three-in-a-row src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/screen2.png" style="align-self: center"></img>
    <img class=three-in-a-row src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/screen3.png" style="align-self: center"></img>
    <p style="justify-self: center">图3 (a)</p>
    <p style="justify-self: center">图3 (b)</p>
    <p style="justify-self: center">图3 (c)</p>
</div>

# 玩法 2

## 外观

<div align=center>
    <img src="https://raw.githubusercontent.com/Juniper1106/docsify/main/img/giiker1.png"></img>
</div>

<center>图 4</center>

![](https://raw.githubusercontent.com/Juniper1106/docsify/main/img/gravitrax.png)

<center>图 5</center>

## 规则

基于积分关卡制

### 基础逻辑环节

1. 基础逻辑：需要正确将对应环节的物质流动联系起来，一旦连接完成，本模块将会开始生产，生产完成后对应环节将会产出正确产物和一定的副产物

   **例如：**

   （）-种植业-（主产品：玉米）（副产品：饲料）

   主产品可以得分，副产品将会堆积，堆积过几轮后，副产物溢出，生产环节将会停滞，停滞的每一轮都会扣分。

2. 某些环节需要原料输入，若未能输入，将会扣除积分作为购买成本

   **例如：**

   （输入：饲料）-畜牧业-（主产品：牛奶、牛肉）（副产品：粪便）

   若无饲料输入，则扣除积分，作为成本。

### 游戏目标

简单模式下，得分积累至目标即可完成

中等模式下，会给定某一初始条件，如以畜牧业和一定积分开始，目标为建立对应给定的生产环节产业（如结束时必须含有种植业、食品加工业、肥料厂），并得到超过目标的分数

困难模式下，在中等模式的基础上将会降低每一生产环节的得分，并要求各个环节完成对应的生产轮数，得到对应的分数，才能达到目标。

### 案例

自由的模块化底盘，能够识别放置在其上的玩具具体玩法，如以下案例

1. 放置和设置好棋盘
2. 放置第一个生产环节（如种植业）
3. 棋盘识别出第一个生产环节并开始计时
4. 一段时间后，该环节生产完成，由模块和棋盘上的声光反馈提示完成
5. 根据放置的生产环节，系统输出结果（若为种植业，则输出农产品和饲料）
6. 根据反馈的输出结果，在对应的位置摆放下一环节（例如原种植业左边输出农产品，下方输出饲料，则需要在左边放置仓库，右边放置畜牧业设施）
7. 下一环节在被正确放置之后，投入生产。

## 交互形式

为**图 4** 所示的点阵底盘，光流表示物质流动，用实体物件表示物质流动，搭建类似上图的轨道，实现更有趣的物质流动形式。

如**图 5**，不同的小球代表不同的产出物，小球滚动至某一生产环节可释放此模块内的小球，使其进入下一环节，实现物质流的更替。（例如代表饲料的小球进入畜牧业模块后，可以释放堆肥原料和畜牧业产品的小球进入下一环节）
