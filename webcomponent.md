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




