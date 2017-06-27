# xss

防止跨站脚本攻击(Cross Site Scripting)，详情查阅 [`xss`](https://www.npmjs.com/package/xss)

跨站脚本攻击：往 Web 页面里注入恶意 Script 代码，当用户浏览该页之时，嵌入其中 Web 里面的 Script 代码会被执行，从而达到恶意攻击用户的目的。

## 安装

    npm install xss

## 例子

```js
var xss = require('xss');
var html = xss('<script>alert("xss");</script>');

console.log(html);
// => &lt;script&gt;alert("xss");&lt;/script&gt;
```

```js
var xss = require('xss');

var myxss = new xss.FilterXSS({
  onIgnoreTagAttr: function (tag, name, value, isWhiteAttr) {
    // 让 prettyprint 可以工作
    if (tag === 'pre' && name === 'class') {
      return name + '="' + jsxss.escapeAttrValue(value) + '"';
    }
  }
});
```

