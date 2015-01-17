# web component

记录 web component

## 组成：

* Templates
* Shadow DOM - 解决了 DOM 树的封装问题。
* Custom Elements
* Packaging

> Chrome 25+ 支持 Shadow DOM，但 API 需要加 webkit 前缀。 在 Chrome 的最新版本中增加了无前缀的 API，可以通过开启 about:flags 下的 "实验性网络平台功能"来使用。

第一个例子：[在线地址](http://jsfiddle.net/zhangyaochun/1w4ykb5t/)

``` html
<button id="test">我是按钮</button>
<button id="get">获取按钮文案</button>
```

``` js
var host = document.querySelector('#test');
var root = host.createShadowRoot();
root.textContent = '我是shadow dom';

document.getElementById('get').onclick = function () {
    alert(document.querySelector('#test').textContent);
};
```


