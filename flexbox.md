# css2014 flexbox
Flexbox 是 Web 布局的必然趋势。

## 布局:

 用 line-height 来做垂直置中，这本来是用来当作段落中的行距，但却因为这个属性能扩展文字的上下空间，结果也被拿来做垂直置中。那有没有一个方法能用来更好地实现 Web 布局呢？


> Angular Material's responsive CSS layout is built on flexbox

## what is flexbox?

这是设计来实现更复杂的版面布局。
Flexbox 从本质上就是一个 Box-model 的延伸， Box-model 定义了一个元素的盒模型，然而 Flexbox 更进一步的去规范了这些盒模型之间彼此的相对关系。




## 这能做什么？也就是他能解决什么问题？
## 能用在哪裡？在哪些地方能用这个方法？
## 为什么能用？他实现所用到的逻辑是什么？


#### 垂直居中：

	我只要先指定容器为一个 Flex 容器，然后 justify-content 让他水平方向置中，再 align-items 让他垂直方向置中。


#### 所有子元素等高：

只需要在 flex 容器加上 align-items 就好。


#### 兼容性：

Flex 最初被 W3C 于 09 年制定出来。拿指定元素为一个 flex 容器来讲，第一个版本里是 display:box，第二个版本是 display: flexbox，第三个版本是 display: flex。

caniuse 上面查看：

#### flex item 宽度计算。

display: flex  等价于：

``` css
flex-grow: 0;
flex-shrink: 1;
flex-basis: auto;
```

#### flex-basis

初始值 auto。来设置伸缩基准值。负长度不合法。

这个属性在 flex 容器为横向的时候，其实就是宽度。

若在 flex 缩写省略了此属性设置，则 flex-basis 的指定值是“0%”，
若 flex-basis 的指定值是“auto”，则伸缩基准值的指定值是元素主轴长度属性的值。

#### flex-grow

Number 类型，初始值0。来设置 扩展比率。负值不合法。

flex-grow 表示在 item 总宽度比容器小的时候，为了让 item 填满容器，每个 item 增加的宽度。

每一个item都是 100的化[各自 3 2 1]，总的是480

480-(3* 100) = 180

100 + 3/6 * 180 = 190
100 + 2/6 * 180 = 160
100 + 1/6 * 180 = 130


#### flex-shrink

flex-shrink 表示在 item 总宽度比容器大的时候，为了让 item 填满容器，每个 item 减少的宽度。

若省略则会被设置为“1”。

每一个item都是 200的化[各自 3 2 1]，总的是480

200 * 3 - 480 = 120
(3+2+1) * 200 = 1200
120 * 600/ 1200 = 60

200 - 3/6 * 120 = 140
200 - 2/6 * 120 = 160
200 - 1/6 * 120 = 180



## 术语：[官方在线地址](http://www.w3.org/html/ig/zh/wiki/Css3-flexbox/zh-hans)

* 伸缩容器：一个设有“display:flex”或“display:inline-flex”的元素
* 伸缩项目：伸缩容器的子元素
* 主轴、主轴方向：用户代理沿着一个伸缩容器的主轴配置伸缩项目，主轴是主轴方向的延伸
* 主轴起点、主轴终点：伸缩项目的配置从容器的主轴起点边开始，往主轴终点边结束
* 主轴长度、主轴长度属性：伸缩项目的在主轴方向的宽度或高度就是项目的主轴长度，伸缩项目的主轴长度属性是width或height属性，由哪一个对着主轴方向决定
* 侧轴、侧轴方向：与主轴垂直的轴称作侧轴，是侧轴方向的延伸
* 侧轴起点、侧轴终点：填满项目的伸缩行的配置从容器的侧轴起点边开始，往侧轴终点边结束
* 侧轴长度、侧轴长度属性：伸缩项目的在侧轴方向的宽度或高度就是项目的侧轴长度，伸缩项目的侧轴长度属性是「width」或「height」属性，由哪一个对着侧轴方向决定

图片：<img src="http://i.imgur.com/goJdO.png" border = "0"/>


#### 主轴与侧轴

	让 flexbox 正常工作的主轴和侧轴，他们看上去有点像X轴和Y轴，但还是有所差别的：

* 主轴的方向主要是用来确定 flex 的主方向，所以你子元素要么放置在一行，要么放置在一列。
* 侧轴主要垂直于主轴运行

如图：



#### 伸缩项目的对齐：

##### 主轴对齐伸缩项目

justify-content：用来设置伸缩项目沿主轴的对齐方式，有如下值：

* flex-start		伸缩项目向一行的起始位置靠齐
* center 			伸缩项目向一行的中间位置靠齐
* flex-end			伸缩项目向一行的结束位置靠齐
* space-between		伸缩项目会平均地分布在一行里
* space-around


如图：

##### 侧轴对齐伸缩项目

align-items：用来设置伸缩项目沿侧轴的对齐方式，有如下值：

* flex-start
* center
* flex-end
* space-between




#### 改变伸缩项目的顺序

order：用来设置伸缩项目的显示顺序，默认状态下，用户代理会用伸缩项目出现在源文档的次序配置这些伸缩项目。

order取值越大，越排在后面。并且 order 可以取负值。





扩展阅读：

* [w3的中文说明](http://www.w3.org/html/ig/zh/wiki/Css3-flexbox/zh-hans)
* [Solved by Flexbox](http://philipwalton.github.io/solved-by-flexbox/)


