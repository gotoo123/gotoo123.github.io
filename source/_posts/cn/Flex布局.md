---
title: Flex 布局
catalog: false
date: 2022-01-19 21:38:00
subtitle:
lang: cn
header-img: /img/header_img/lml_bg.jpg
tags:
- style
categories:
- css知识
---

## Flex布局

> 设为flex布局以后，子元素的float、clear、vertival-align属性将失效

- 父—>容器； 子—>项目
- 主轴，交叉轴；



#### 容器的属性

- flex-direction（设定主轴的方向。default: row）

  ```css
  .box {
    flex-direction: row | row-reverse | column | column-reverse
  }
  ```

- flex-wrap（定义一条轴线排不下，如何换行。default: nowrap）

  默认项目都排在轴线上。

  ```css
  .box {
    flex-wrap: nowrap | wrap | wrap-reverse
  }
  ```

- flex-flow（flex-direction和flex-wrap的简写形式。default）

  ```css
  .box {
    flex-flow: <flex-direction> || <flex-wrap>
  }
  ```

- justify-content（定义了项目在主轴上的对齐方式。default: flex-start）

  ```css
  .box {
    justify-content: flex-start | flex-end | center | space-between | space-around
  }
  
  /*
  space-between: 两端对齐，项目之间的间隔都相等
  space-around: 每个项目两侧的间隔相等。（项目之间的间隔比项目与边框的间隔大一倍哦）
  */
  ```

- align-items（定义项目在交叉轴上的对齐方式。default: flex-start）

  ```css
  .box {
    align-items: flex-start | flex-end | center | baseline |stretch
  }
  
  /*
  baseline: 项目的第一行文字的基线对齐
  stretch：如果项目未设置高度或者高度设为auto，则占满整个容器
  */
  ```

- align-content（定义了多根轴线的对齐方式。default: stretch）

  如果项目只有一根轴线，则该属性不起作用。一般为 flex-wrap: wrap。

  ```css
  .box {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch
  }
  
  /*
  space-between: 与交叉轴两端对齐，轴线之间的间隔平均分布
  space-around: 每根轴线之间的距离都相等。大一倍
  stretch: 轴线占满整个交叉轴
  */
  ```



#### 2.项目的属性

- order（定义项目的排列顺序。default: 0）

  数值越小，位置越靠前可以为负数。

  ```css
  .item {
    order: <integer>
  }
  ```

- flex-grow（定义项目的放大比例。default: 0）

  （放大时会忽略item其原本的宽高值）

  ```css
  .item {
    flex-grow: <integer>
  }
  ```

  - 默认为0 ，说明即使存在剩余空间，也不放大。
  - 如果所有项目flex-grow都为1，则他们将等分剩余空间（如果有的话 <严谨>）。
  - 如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项目多一倍。

- flex-shrink（定义了项目的缩小比例。default: 1）

  默认为1，即如果空间不足，该项目将缩小。不能为负值。

  ```css
  .item {
    flex-shrink: <number>
  }
  ```

  - 如果所有项目的flex-shrink都为1，则当空间不足时，都将等比例缩小。

  - 如果一个项目的flex-shrink属性为0，其他项目不为0时，则当空间不足时，该项目不缩小。

  - 对于放大缩小这里，还有很多的坑，这里先马一下：

    >https://www.cnblogs.com/liyan-web/p/11217330.html

- flex-basis（定义了在分配多余空间之前，项目占据的主轴空间。default: auto）

  默认值为auto，即项目的本来大小。

  浏览器根据这个属性，计算主轴是否有多余的空间。

  ```css
  .item {
    flex-basis: <length> | auto
  }
  ```

- flex（flex-grow flex-shrink flex-basis 的简写。 default:  0 1 auto）

  优先使用这个属性，而不是写三个单独分离的属性，浏览器会推算相关值。

  ```css
  .item {
    flex: none | [<flex-grow> <flex-shrink>? || <flex-basis>]
  }
  
  /*
  后两个属性可选。
  */
  ```

  该属性有两个快捷值：

  - auto: 1 1 auto
  - none:  0 0 auto

- align-self（允许单个项目有与其他项目不一样的对齐方式。 default: auto）

  该属性可覆盖容器的align-items属性。

  默认值为auto代表继承容器的align-items属性。如果没有父元素，则等同于stretch。

  ```css
  .item {
    align: auto | flex-start | flex-end | center | baseline | stretch
  }
  ```

  

    

    