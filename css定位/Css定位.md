#### Css-position属性

#### position属性规定应用于元素的定位方法的类型

**有五个不同的值*

- static
- relative
- fixed
- absolute
- sticky

首先需要设置position属性，用于定位元素的top、bottom、left、right属性才会起作用

##### 1.position: static

- HTML 元素默认情况下的定位方式为 static（静态）。
- 静态定位的元素不受 top、bottom、left 和 right 属性的影响。
- position: static; 的元素不会以任何特殊方式定位；它始终根据页面的正常流进行定位

##### 2.position: relative

- position: relative 的元素相对于其正常位置进行定位。
- 设置相对定位的元素的 top、right、bottom 和 left 属性将导致其偏离其正常位置进行调整。
- 不会对其余内容进行调整来适应元素留下的任何空间。

##### 3.position: fixed

- position: fixed的元素是相对于视口定位的，这意味着即使滚动页面，它也始终位于同一位置。
- top、right、bottom 和 left 属性用于定位此元素。
- 固定定位的元素不会在页面中通常应放置的位置上留出空隙。
- 通常用于把一个元素固定在右下角或者右上角不需要改变位置的地方

##### 4.position: absolute

- position: absolute的元素相对于最近的定位祖先元素进行定位
- **如果绝对定位的元素没有祖先，它将使用文档主体（body），并随页面滚动一起移动。-->脱离文档流**
- **被定位的”元素是其位置除static以外的任何元素**

##### 5.position: sticky

- position:sticky的元素根据用户的滚动位置进行定位。
- 粘性元素根据滚动位置在相对（relative）和固定（fixed）之间切换。
- 起先它会被相对定位，直到在视口中遇到给定的偏移位置为止 - 然后将其“粘贴”在适当的位置

#### Css定位属性

- clip：剪裁绝对定位的元素(不太熟悉)
- bottom：设置定位框的底部外边距边缘。
- left：设置定位框的左侧外边距边缘。
- right：设置定位框的右侧外边距边缘。
- top：设置定位框的顶部外边距边缘。
- z-index：设置元素的堆叠顺序，可正可负
- position：规定元素的定位类型