# css

## 浏览器内核以及其前缀

- CSS标准中各个属性都要经历从草案到推荐的过程，css3中的属性进展都不一样，浏览器厂商在标准尚未明确情况下提前支持会有风险,浏览器厂商对新属性的支持情况也不同，所以会加厂商前缀加以区分。
- 如果某个属性已经从草案变为了或接近推荐方案,并且厂商已经完全实现了推荐属性，那就不用加厂商前缀。
- 如border-radius已经很成熟不用加前缀。
- 根据不同的浏览器内核，css前缀会有不同。最基本的浏览器内核有如下四种，其它的内核都是基于此四种进行再研发的。
  - 1.Gecko内核 前缀为-moz-火狐浏览器
  - 2.Webkit内核 前缀为-webkit-也叫谷歌内核，chrome浏览器最先开发使用，safari浏览器也使用该内核。国内很多浏览器也使用了webkit内核，如360极速、世界之窗、猎豹等。
  - 3.Trident内核 前缀为-ms-也称IE内核
  - 4.Presto内核 前缀-o-目前只有opera采用

## 文字阴影

- 水平偏移 垂直偏移 模糊度 
- 格式 text-shadow:阴影1,阴影2
  - 1.横向偏移位置
  - 2.纵向偏移位置
  - 3.模糊度
  - 4.阴影的颜色         

## 盒子阴影

- 格式：box-shadow:阴影1,阴影2
- 阴影的格式：
  - 水平偏移位置 垂直偏移位置 模糊度 外沿值 内置阴影

## 渐变

- CSS3渐变(gradients）可以让你在两个或多个指定的颜色之间显示平稳的
  过渡。
- 以前，你必须使用图像来实现这些效果
- 现在，使用CSS3渐变( gradients），通过代码来实现渐变可以减少请求和节约带宽。
- CSS3定义了两种类型的渐变(gradients)
  - 线性渐变（Linear Gradients)
  - 径向渐变(Radial Gradients)

### 1.线性渐变

- 向下/向上/向左/向右/对角方向
- background: linear-gradient(direction,color-stopl，color-stop2，.. . );

### 2.径向渐变

- 由它们的中心定义
- background: radial-gradient(center，shape，size，start-color,...,last-color);
  - 默认情况下，渐变的中心是center(表示在中心点)，渐变的形状是ellipse （表示椭圆形)
  - 它可以是值circle或ellipse。其中，circle表示圆形，ellipse表示椭圆形

## 圆角border-radius

- 语法
  - border-radius: value;四个角
  - border-radius: value value;左上右下、右上左
  - 下border-radius: value value value value;
  - 代表设置对象左上角、右上角、右下角、左下角

## Transform

- CSS3中的转换允许我们对元素进行旋转、缩放、移动或倾斜。它为分2D转换或3D转换。
- 在css2时代，如果要做一些图片转换角度，都依赖于图片、Flash或JavaScript才能完成。
- 但是现在借助CSS3就可以轻松倾斜、缩放、移动以及翻转元素。
- 通过CSS变形，可以让元素生成静态视觉效果，但也可以很容易结合CSS3的transition和动画的keyframe产生一些动画效果。

### 1.转换Transform 2D的属性

- 通常的属性包含了属性名和属性值，而CSS3的transform属性是用函数来定义的。
- Transform 2D函数包括了translate()、scale()、rotate()和skew()。
- 书写格式:transform:函数名(x轴值，y轴值);

#### 1.translate()函数

- translate()方法，根据左(X轴)和顶部(Y轴)位置给定的参数，从当前元素位置移动。
- 接受CSS的标准度量单位（ px)
- translate(x,y):转换，沿着X和Y轴移动元素。

#### 2.rotate()

- 通过rotate()方法，元素顺时针旋转给定的角度。
- 允许负值，元素将逆时针旋转。
- 它以deg为单位，代表了旋转的角度。

#### 3.scale()

- 通过值把宽和高转换为原始尺寸的n倍，接受两个参数，前面的为宽，后面的为高。
- 可取值:默认值为1
- 缩小:0-1之间的数
- 放大:大于1的数

#### 4.skew()

- 根据水平轴和垂直轴翻转，接受两个或一个值，两个值时前面为水平，后面为垂直的角度，一个值只是水平轴的角度。
- 此函数是指元素的倾斜角度。

### 2.转换Transform 3D的属性

- Transform 3D常用函数有:
- translate3d(x,y,z)---定义3D转化。
- translateX(x)---定义3D转化，仅使用用于×轴的值。
- translateY(y)---定义3D 转化，仅使用用于y轴的值。
- translateZ(z)---定义3D转化，仅使用用于z轴的值。
- scale3d(x,y ,z)---定义3D缩放转换。
- scaleX(x)---定义3D缩放转换，通过给定一个×轴的值。
- scaleY(y)---定义3D缩放转换，通过给定一个y轴的值。
- scaleZ(z)---定义3D缩放转换，通过给定一个z轴的值。
- rotate3d(x,y,z,angle)---定义3D旋转。
- rotateX(angle)---定义沿×轴的3D旋转。
- rotateY(angle)---定义沿y轴的3D旋转。
- rotateZ(angle)---定义沿z轴的3D旋转。

## 过渡Transition

### 1.什么是过渡

- 使用css的属性值在一段时间内平滑的过渡
- 比如，鼠标悬停后，背景色在1s内，由白色平滑的过渡到红色
  - 1）指定四个要素:
    - 过渡属性，如lbackground、color等
    - 过渡所需时间
    - 过渡函数，即过渡的速度、方式等
    - 过渡延迟时间，表示开始执行的时间
  - 2）触发过渡
    - 通过用户的行为触发，如点击、悬浮等

### 2.过渡属性

- transition-property: none all property;
- 多个属性用逗号隔开
- 可设置过渡的属性
  - 颜色属性
  - 取值为数值的属性
  - 转换属性
  - 渐变属性
  - 阴影属性

### 3.过渡时间

- transition-duration: s|ms ;
- 默认值为0，意味着不会有效果，所以必须设置transition-duration属性

### 4.过渡函数

- transition-timing-function:

- 取值:
  - ease:默认值，规定慢速开始，然后变快，然后慢速结束的过渡效果
  - linear:匀速
  - ease-in:规定以慢速开始，加速效果ease-out:规定以慢速结束，减速效果
  - ease-in-out:规定以慢速开始和结束，先加速后减速效果

### 5.简写属性transition

- transition属性是一个简写属性，用于设置四个过渡属性
- 语法: transition:property duration timing function delay;

```css
#box {
width: 200px;height: 200px;
background-color: #1fb57b;
transition: background 4s linear 1s;
}
#box : hover {
background-color: red;
}
```

## animation动画

- 过渡属性只能模拟动画效果
- animation属性可以制作类似Flash动画
  - 通过关键帧控制动画的每一步
  - 使元素从一种样式逐渐变化为另一种样式
  - 实现复杂的动画效果

### 1.@keyframes

- 作用:用于声明动画，指定关键帧
- 帧，用于分解动画动作
  - 每个帧代表某个时间点
  - 定义每个帧上的动作

```css
@keyframes的语法
@keyframes name {
from | 0% {
css样式
}
percent {
css样式
)
to  100% {
css样式
}
}
```

### 2.animation属性

- animation属性用于控制动画
  - 调用由@keyframes定义的动画
  - 设置动画属性，如时间、次数等
- animation属性是一个简写属性
  - 语法为: animation:name duration timing-function delay iteration-count direction;

### 3.动画子属性

- animation-name: ;调用动画，规定需要和keyframes的名字一致
- animation-duration: s ms;动画完成一个周期所需要的时间
- animation-timing-function: ;规定动画的速度变化类型
- animation-delay:s ms ;播放之前的延迟时间
- 动画子属性
- agimation-iteration-count:数值|infinite;播放次数
  - infinite表示无限次播放
- animation-direction: normal alternate;动画播放方向
  - normal为默认值，表示正常播放
  - alternate表示轮流播放，即动画会在奇数次正常播放，而在偶数次向后播放
- animation-fill-mode: forwards;动画停在最后一帧
  - 默认值为none
- animation-play-state:paused running;属性规定动画正在运行还是暂停
  - 默认值为running