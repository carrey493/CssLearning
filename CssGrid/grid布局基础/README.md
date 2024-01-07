# grid 布局基础到实战

https://www.bilibili.com/video/BV1Qg411b7od/?p=3&spm_id_from=333.880.my_history.page.click&vd_source=be3b45fc17b50a3c41a73ab4183d9c90

1. grid 布局的含义
2. grid 布局中的基础概念
3. grid 布局中的容器属性
4. grid 布局中的项目属性
5. grid 案例

## grid 布局基础

1. grid 布局的含义
   grid 布局，也被称之为网格布局，是将页面中的父元素划分成一个个小的格子，然后通过这些小的格子进行合并来制作出不同的网站效果。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106153933232-1320323051.png)

2. 如何触发网格
   给父元素添加 display 属性，并且将取值设置成：grid/inline-grid，**grid**：代码含义块状网格，默认独占一行，类似于块级元素，**inline-grid**：代码含义行内块网格，与行内块元素类似。

3. 触发网格有哪些特点
   划分行列后，才能将里面的区域进行划分，才能显示网格，才能进行合并。

4. grid 布局与 flex 布局异同，网格与表格的区别

   - grid 与 flex 布局
     - 相同点：都有容器和项目之分
     - 不同点：flex 布局被称之为一维布局，也叫做轴线布局；grid 被称之为二维布局，有行列之分。
   - grid 与表格
     - 相同点：都有行列之分，都能划分格子；
     - 不同点：代码嵌套

## grid 布局概念

- grid 容器：采用 grid 布局的父元素
- grid 内容：显示项目的区域
- grid 项目：grid 布局中每一个格子放置的元素
- 行：横向
- 列：纵向
- 网格线：网格布局中的横向的和纵向的线条
- 单元格：横纵线交汇的区域称之为单元格
- 间距：网格与网格之间的距离被称为间距

**一个 m 行 n 列的网格，需要使用 m+1 条横向，n+1 条纵向的网格线组成**

## grid 布局容器属性

1. 容器触发网格

```css
.box {
    width: 500px;
    height: 500px;
    border: 10px solid gray;
    display: grid;
    display: inline-grid;
}
```

2. 划分行列属性

- 行属性：grid-template-rows;
- 列属性：grid-template-columns;

**重点我们研究的是他们的取值，注意事项：后面跟几组值，就代表了几行几列。**+

**取值 1：纯数值**

```css
{
  grid-template-rows: 100px 100px 100px;
  grid-template-columns: 100px 100px 100px;
}
```

代码含义：

- 划分一个 3 行 3 列的网格
- 每一行行高：100px
- 每一列列宽：100px

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106111508649-1346248730.png)

**取值 2：百分比**

```css
{
  grid-template-rows: 20% 30% 50%;
  grid-template-columns: 100px 100px 100px;
}
```

代码含义：

- 划分一个 3 行 3 列的网格
- 每一行行高：分别是总高的 20% 30% 50%
- 每一列列宽：100px

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106111623325-95572330.png)

**取值 3：重复函数**

重复函数：使用的是 repeat(num1,num2)函数
两个参数： - 参数 1：重复次数 - 参数 2：需要重复的值

```css
/* 简化前写法 */
{
  grid-template-rows: 100px 100px 100px;
  grid-template-columns: 20% 20% 20% 20% 20%;
}
/* 简化后写法 */
{
  grid-template-rows: repeat(3, 100px);
  grid-template-columns: repeat(5, 20%);
}
```

代码含义：

- 划分一个 3 行 5 列的网格
- 每一行行高：100px
- 每一列列宽：均占总宽度的 20%
- 注意：repeat 函数，第一个参数是重复的次数，第二个参数为需要重复的数值

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106112700435-1428698264.png)

**取值 4：自动填充**

自动填充：`auto-fill`，应用在重复函数中，代码含义根据需要重复的数值，进行自动填充数量；(列如：以列宽为例子)

```css
{
  grid-template-rows: repeat(3, 100px);
  grid-template-columns: repeat(auto-fill, 30%);
}
```

**备注：** 在这里`auto-fill`会将列数宽度按照 30%的宽度进行划分；盛放不下的话则不再划分列数

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106114556148-735409923.png)

**取值 5：auto 自动**

`auto`自动代码含义，占剩余宽度和剩余高度的所有。

```css
{
  grid-template-rows: 100px auto 100px;
  grid-template-columns: auto 100px 100px;
}
```

代码含义：

- 划分一个 3 行 3 列的网格
- 第 1,3 行固定高度 100px；第 2 行高度自适应
- 第 2,3 列固定宽度 100px；第 1 列宽度自适应

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106115357247-2146614848.png)

**取值 6：片段划分**

片段划分：为了方便表示比例关系，网格布局提供了 fr 关键字(fraction 的缩写，意为“片段”)。

如果两列的宽度分别为 1fr 与 2fr，就表示后者是前者的两倍

```css
{
  grid-template-rows: 1fr 2fr 3fr;
  grid-template-columns: 100px 100px 100px;
}
```

代码含义：

- 划分一个 3 行 3 列的网格
- 其中行高总高划分成 6 份，第 1 行占 1/6，第 2 行占 2/6，第 3 行占 3/6.
- 每一列的宽度为：100px

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106151133842-160539524.png)

**取值 7：minmax()**

minmax(num1,num2)函数，刻意理解成最小最大值函数，函数中有两个参数；参数 1 代表最小值、参数 2 代表最大值。

如果条件允许，则一直使用最大值，如果条件不满足则使用中间值，如果剩下的大小不足以显示距离大小，则使用最小值。

```css
{
  grid-template-rows: 100px 100px minmax(100px, 200px);
  grid-template-columns: 100px 100px 100px;
}
```

代码含义：

- 划分一个 3 行 3 列的网格
- 其中 1,2 行行高为 100px，第 3 行高度会 >=100 <=200
- 每一列的宽度为：100px

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106152319291-165178103.png)

```css
{
  grid-template-rows: 200px 200px minmax(100px, 200px);
  grid-template-columns: 100px 100px 100px;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106152528644-1036859923.png)

```css
{
  grid-template-rows: 300px 200px minmax(100px, 200px);
  grid-template-columns: 100px 100px 100px;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106152729853-629283673.png)

3. 调整间距属性

- 行间距属性：grid-row-gap
- 列间距属性：grid-column-gap

```css
{
  grid-row-gap: 20px;
  grid-column-gap: 20px;
}
```

以上的代码比较复杂，所以我们需要进行简写。

使用属性：`grid-gap:num1 num2;`来实现，第一个参数代表的是行间距，第二个参数代表的是列间距。

```css
{
  grid-gap: 20px 30px;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106154353265-947255784.png)

## grid 布局容器项目

如果想要给网格做添加项目，我们需要在容器添加对应的 div，这些 div 被称之为项目，项目会默认自动撑开显示在单元格内部。

添加完对应的项目之后，默认项目是横向依次由左向右进行显示，第一行显示完毕之后，才会在第二行显示。

1. 调整项目顺序

我们可以使用：`grid-auto-flow`属性来完成调整项目顺序

`grid-auto-flow`属性有两个值

- row：横向显示
- columnn：纵向显示

```css
{
  grid-auto-flow: row;
}
```

```html
<div class="box2">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
  <div>5</div>
  <div>6</div>
  <div>7</div>
  <div>8</div>
  <div>9</div>
</div>
```

```css
.box2 {
  width: 500px;
  height: 500px;
  border: 10px solid rgb(44, 133, 242);
  display: grid;
  margin: 100px auto;
  grid-template-rows: 100px 100px 100px;
  grid-template-columns: 100px 100px 100px;
}
.box2 > div {
  border: 2px dashed darkgoldenrod;
}
```

> 默认展示

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106191528544-1881434025.png)

> 调整排列顺序后展示

```css
.box2 {
  width: 500px;
  height: 500px;
  border: 10px solid rgb(44, 133, 242);
  display: grid;
  margin: 100px auto;
  grid-template-rows: 100px 100px 100px;
  grid-template-columns: 100px 100px 100px;
  grid-auto-flow: column;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106191326389-104165312.png)

2. 项目对齐方式

给项目添加宽度之后，默认项目是在单元格左上角显示的，如何调整项目位于单元格内部的对齐呢？

- 水平对齐方式：justify-items
- 垂直对齐方式：align-items

```css
{
  justify-items: start;
}
```

这行代码代表的是，项目位于水平方向的开始位置(默认设置)。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106193822822-1508243597.png)

```css
{
  justify-items: center;
}
```

这行代码代表的是，项目位于水平方向的中间位置。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106193903461-76269237.png)

```css
{
  justify-items: end;
}
```

这行代码代表的是，项目位于水平方向的结束位置。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106193931369-250886792.png)

```css
{
  align-items: start;
}
```

这行代码代表的是，项目位于垂直方向的开始位置(默认设置)。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106194015218-1750655502.png)

```css
{
  align-items: center;
}
```

这行代码代表的是，项目位于垂直方向的中间位置。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106194040553-1038791776.png)

```css
{
  align-items: end;
}
```

这行代码代表的是，项目位于垂直方向的结束位置。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106194107764-2135064659.png)

项目可以通过`justify-items`,和`align-items`属性实现在单元格水平和垂直方向对齐,除了`start`,`center`,`end`这三个取值之外,另有一个默认值就是`stretch` 拉伸效果

但是以上两个属性均为单一属性,是否有对应的复合属性来实现？

**语法：**`place-items: align-items justify-items`

- 第一个取值代表的是垂直方向
- 第二个取值代表的是水平方向

**例如：place-items: end center;**

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106194345507-1873983354.png)

3. 网格对齐方式

默认情况下网格位于容器的左上角位置显示,我们可以使用

- 水平方向对其属性: justify-content
- 垂直方向对其属性: align-content

```css
{
  justify-content: start;
}
```

此行代码代表的是：网格位于容器水平方向开始位置显示(默认设置)。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240106235902582-416341926.png)

```css
{
  justify-content: end;
}
```

此行代码代表的是：网格位于容器水平方向结束位置显示(默认设置)。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107000332009-1185455358.png)

```css
{
  justify-content: center;
}
```

此行代码代表的是：网格位于容器水平方向中间位置显示(默认设置)。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107000450835-1464485653.png)

```css
{
  align-content: start;
}
```

此行代码代表的是：网格位于容器垂直方向开始位置显示(默认设置)。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107000741115-1621805941.png)

```css
{
  align-content: end;
}
```

此行代码代表的是：网格位于容器垂直方向结束位置显示。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107000828526-2014045134.png)

```css
{
  align-content: center;
}
```

此行代码代表的是：网格位于容器垂直方向中间位置显示。

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107000914161-1271823561.png)

如果想要水平和垂直方向都进行位置调整,则两个属性需要配合一起使用:

```css
{
  justify-content: center;
  align-content: center;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107000953413-1138486019.png)

也完全可以使用复合属性`place-content`完成

- 属性: place-content:
- 取值: align-content justify-content

代码例如

```css
{
  place-content: center center;
}
```

需要注意: `justify-content`, `align-content`取值除了有`star`, `end`, `center`,这些取值之外,还有对应的`stretch`, `space-around`, `space-between`, `space-evenly`等值

- stretch：代表的是拉伸默认值
- space-around：行列间距环绕
- space-between：行列两端对齐
- space-evenly：行列间距平分

## grid 布局项目属性

1. 合并单元格属性

合并单元格是将划分好的网格﹐通过让元素使用网格线占位的形式，来达到合并的效果.

如下图所示

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107111723937-2000104425.png)

我们可以使用：

- grid-row-start 横向网格线开始占位
- grid-row-end 横向网格线结束占位
- grid-column-start 纵向网格线开始占位
- grid-column-end 纵向网格线结束占位

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107112147090-1478698640.png)

可以使用`grid-row`与`grid-column`属性来快捷设置占位

`grid-row`与`grid-column`的取值为`number1/number2`的形式

- number1代表的是水平或垂直方向上面的开始占位线
- number2代表的是水平或垂直方向上面的结束占位线

```html
<div class="box">
    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
    <div>4</div>
    <div>5</div>
    <div>6</div>
    <div>7</div>
</div>
```

```css
.box {
    width: 500px;
    height: 500px;
    border: 10px solid rgb(56, 157, 240);
    display: grid;
    margin: 100px auto;
    grid-template-rows: repeat(4, 100px);
    grid-template-columns: repeat(3, 100px);
}

.box>div {
    background-color: aquamarine;
    border: 1px dashed #d64f4f;
}

.box1 {
    /* grid-row-start: 1;
    grid-row-end: 3;
    grid-column-start: 2;
    grid-column-end: 4; */
    grid-row: 1/3;
    grid-column: 2/4;
}

.box2 {
    /* grid-row-start: 3;
    grid-row-end: 4;
    grid-column-start: 1;
    grid-column-end: 3; */
    grid-row: 3/4;
    grid-column: 1/3;
}

.box3 {
    /* grid-row-start: 4;
    grid-row-end: 5;
    grid-column-start: 2;
    grid-column-end: 4; */
    grid-row: 4/5;
    grid-column: 2/4;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107121206829-536340587.png)

## grid 布局案例

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107132217671-104495185.png)

```html
<div class="box">
    <div class="box1">1</div>
    <div class="box2">2</div>
    <div class="box3">3</div>
    <div class="box4">4</div>
    <div class="box5">5</div>
    <div class="box6">6</div>
    <div>7</div>
    <div>8</div>
    <div>9</div>
    <div>10</div>
    <div>11</div>
    <div>12</div>
    <div>13</div>
    <div>14</div>
    <div>15</div>
    <div>16</div>
    <div>17</div>
    <div>18</div>
    <div>19</div>
    <div>20</div>
    <div>21</div>
    <div>22</div>
    <div>23</div>
    <div>24</div>
    <div>25</div>
    <div>26</div>
    <div>27</div>
    <div>28</div>
    <div>29</div>
    <div>30</div>
    <div>31</div>
    <div>32</div>
    <div>33</div>
    <div>34</div>
    <div>35</div>
    <div>36</div>
    <div>37</div>
    <div>38</div>
</div>
```

```css
* {
    margin: 0;
    padding: 0;
}

.box {
    width: 1700px;
    height: 500px;
    border: 10px solid rgb(56, 157, 240);
    display: grid;
    margin: 100px auto;
    grid-template-rows: repeat(4, 100px);
    grid-template-columns: repeat(13, 100px);
    grid-gap: 20px 20px;
    place-content: center center;
}

.box>div {
    background-color: rgb(255, 145, 0);
    border: 1px dashed #d64f4f;
    grid-gap: 20px 20px;
}

.box1 {
    grid-row: 1/3;
    grid-column: 12/14;
}

.box2 {
    grid-row: 1/2;
    grid-column: 10/12;
}

.box3 {
    grid-row: 2/4;
    grid-column: 6/9;
}

.box4 {
    grid-row: 2/3;
    grid-column: 1/3;
}

.box5 {
    grid-row: 3/5;
    grid-column: 1/3;
}

.box6 {
    grid-row: 4/5;
    grid-column: 12/14;
}
```

![](https://img2024.cnblogs.com/blog/2332774/202401/2332774-20240107133823576-808116852.png)
