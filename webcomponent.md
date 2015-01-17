# web component

记录 web component

## 组成：

* Templates
* Shadow DOM - 解决了 DOM 树的封装问题。
* Custom Elements
* Packaging

> Chrome 25+ 支持 Shadow DOM，但 API 需要加 webkit 前缀。 在 Chrome 的最新版本中增加了无前缀的 API，可以通过开启 about:flags 下的 "实验性网络平台功能"来使用。

#### 第一个例子：[在线地址](http://jsfiddle.net/zhangyaochun/1w4ykb5t/)

``` html
<button id="test">我是按钮</button>
<button id="get">获取按钮文案</button>
```

``` js
var host = document.querySelector('#test');
//createShadowRoot
var root = host.createShadowRoot();
root.textContent = '我是shadow dom';

document.getElementById('get').onclick = function () {
    alert(document.querySelector('#test').textContent);
};
```

你不应该把内容放到 Shadow DOM 中。
这里id为test的按钮和一个新类型的节点关联起来了 - shadow root。
与一个 shadow root关联的元素（这个是id为test的按钮）- shadown host

注释：

> shadow host 的内容不会渲染；shadow root 的内容会渲染。

#### 第二个例子：[在线地址](http://jsfiddle.net/zhangyaochun/maf57rot/)


``` html
<div id="nameTag">豌豆荚</div>
<template id="nameTagTemplate">
    <style>
        .outer {
            border: 2px solid brown;
            border-radius: 1em;
            background: red;
            font-size: 20pt;
            width: 12em;
            height: 7em;
            text-align: center;
        }
        .boilerplate {
            color: white;
            font-family: sans-serif;
            padding: 0.5em;
        }
        .name {
            color: black;
            background: white;
            font-family:"Marker Felt", cursive;
            font-size: 45pt;
            padding-top: 0.2em;
        }
    </style>
    <div class="outer">
        <div class="boilerplate">欢迎加入豌豆荚</div>
        <div class="name">fe-team</div>
    </div>
</template>
```


``` js
//createShadowRoot
var shadow = document.querySelector('#nameTag').createShadowRoot();
//nameTagTemplate - template id
var template = document.querySelector('#nameTagTemplate');
var clone = document.importNode(template.content, true);
shadow.appendChild(clone);
```

#### 改进后的例子：[在线地址](http://jsfiddle.net/zhangyaochun/vhzhrns7/)


内容在文档内；展现在 Shadow DOM 里。

``` html
<div id="nameTag">fe-team</div>
<template id="nameTagTemplate">
    <style>
        .outer {
            border: 2px solid brown;
            border-radius: 1em;
            background: red;
            font-size: 20pt;
            width: 12em;
            height: 7em;
            text-align: center;
        }
        .boilerplate {
            color: white;
            font-family: sans-serif;
            padding: 0.5em;
        }
        .name {
            color: black;
            background: white;
            font-family:"Marker Felt", cursive;
            font-size: 45pt;
            padding-top: 0.2em;
        }
    </style>
    <div class="outer">
        <div class="boilerplate">欢迎加入豌豆荚</div>
        <content></content>
    </div>
</template>
```

区别在于template里面换成了 content。
content的内容来自 shadow host 里的内容。


## 样式相关

Shadow DOM 中定义的 CSS 样式只在 ShadowRoot 下生效。这意味着样式被封装了起来。

#### 例子：[在线地址](http://jsfiddle.net/zhangyaochun/h3evr8df/)


``` html
<div>
    <h3>原来的节点h3-1</h3>
    <h3>原来的节点h3-2</h3>
</div>
```

``` js
//createShadowRoot
var root = document.querySelector('div').createShadowRoot();
root.innerHTML = '<style>h3{ color: red; }</style>' +
    '<h3>欢迎加入豌豆荚</h3>';
```

* 页面中存在多个 h3 标签。但被 h3 选择器所匹配并且样式为红色的只有在 ShadowRoot 的那个元素。
* 页面中定义的其他关于 h3 的样式并没有影响我们的内容。原因在于选择器无法越过 shadow 边界。