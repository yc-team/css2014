# css2014
css

记录[css大会](http://css.w3ctech.com/)的一些东东

## PPT 汇总：

* [Bert Bos](http://www.w3.org/Talks/2015/0110-CSS-Beijing/all)

> CSS 联合创始人

* [johnhax](http://johnhax.net/2015/myth-of-css-frameworks/#1)

> 长达178页 

* [W3C 吴小倩 - CSS性能](http://www.w3.org/2015/Talks/0109-CSSConf-xq/)

* [Jaych Su - Flexbox，更优雅的布局](http://mp.weixin.qq.com/s?__biz=MjM5ODc4MjcyMA==&mid=204599828&idx=1&sn=c6781fb2e52c2c9b07236c84354d1e97#rd)

* [勾三股四 - Web Components 中的 CSS](http://www.tudou.com/programs/view/8bvwGHaL6T4/)

> 视频啊，专业，有两个版本，一个是现场火箭版的，一个是慢的

注释：[慢的在这里](http://www.tudou.com/programs/view/dz4aXjDFnLw/)


## 样式表结构

因为出现了 shadow，所以和以往的有一些变化

* 元素可能包含 shadow
* 元素可能在另一个 shadow 内
* 元素可能包含子元素
* 子元素可能受 shadow 影响

## 建立联系：

* 外部结构
* 内部结构
* 子元素

## webcomponents

* 组件化开发
* 自定义标签 

``` html
<custom-element></custom-element>
```

* 隐藏内部结构

Shadow DOM

``` html
<custom-element>
  <!-- shadow-root -->
    <style>...</style>
    <!-- 内部结构 -->
  <!-- shadow-root -->
</custom-element>
```

1、生命周期
2、交互行为
3、自定义事件

#### 判断外部环境

``` css
:host
:host(<selector>)
:host-context(<selector>)
```

#### 

``` css
::shadow
/deep/
```

#### 内部判断子元素

``` css
::content
```

#### 实践：

* 管理后台


* Zorro.html

