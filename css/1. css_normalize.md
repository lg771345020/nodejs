# Normalize.css

样式重置，用来覆盖不同浏览器渲染 Html 元素时的各种默认样式。原文请移步这里 [关于css样式的重置：Reset.css和Normalize.css](http://www.qdfuns.com/notes/16799/70306b117ceaf74825b5099ac6687a50.html)，更多 reset， 请移步这里 [知乎：到底该不该用 CSS reset？](https://www.zhihu.com/question/23554164)

## reset.css VS Normalize.css：

reset.css 的目的是将所有的浏览器的自带样式重置掉，这样更易于保持各浏览器渲染的一致性。

Normalize.css则尽量保留浏览器的默认样式，该项目依赖于研究浏览器默认元素风格之间的差异，精确定位需要重置的样式。

* Preserves useful defaults, unlike many CSS resets. - 保留了有用的浏览器默认样式而不是完全去掉它们。

* Normalizes styles for a wide range of elements. - 为大部分HTML元素提供一般化的样式

* Corrects bugs and common browser inconsistencies. - 修复浏览器自身的bug并保证各浏览器的一致性

* Improves usability with subtle improvements. - 用一些小技巧优化CSS可用性

* Explains what code does using detailed comments. - 用注释和详细的文档来解释代码

## Normalize.css 的优势：

1.　Normalize.css 保护了有价值的默认值 Reset通过为几乎所有的元素施加默认样式，强行使得元素有相同的视觉效果， 相比之下，Normalize.css保持了许多默认的浏览器样式；这就意味着你不用再为所有公共的排版元素重新设置样式。 当一个元素在不同的浏览器中有不同的默认值时，Normalize.css会力求让这些样式保持一致并尽可能与现代标准相符合。

2. Normalize.css 修复了浏览器的bug 它修复了常见的桌面端和移动端浏览器的bug。这往往超出了Reset所能做到的范畴。 关于这一点，Normalize.css修复的问题包含了HTML5元素的显示设置、预格式化文字的font-size问题、在IE9中SVG的溢出、许多出现在各浏览器和操作系统中的与表单相关的bug。

## Normalize.css 中文注释

```css
/**
 * 1. Set default font family to sans-serif.
 * 1. 设置默认字体样式为无衬线字体
 * 2. Prevent iOS and IE text size adjust after device orientation change,
 * 2. 防止IOS设备和IE下字体大小因为屏幕的转向而改变。
 *  附：iOS设备旋转后可能会自动调整字体大小（e.g. 竖着的时候是14px，横着就自动调整成20px）。
 * without disabling user zoom.
 * 并没有禁用用户放大。
 */

html {
  font-family: sans-serif; /* 1 */
  -ms-text-size-adjust: 100%; /* 2 */
  -webkit-text-size-adjust: 100%; /* 2 */
}

/**
 * Remove default margin.
 * 移除默认的 margin.
 */

body {
  margin: 0;
}

/* HTML5 display definitions
   ========================================================================== */

/**
 * Correct `block` display not defined for any HTML5 element in IE 8/9.
 * 纠正了 HTML5 元素的块状属性在 IE8/9 中无法识别。
 * Correct `block` display not defined for `details` or `summary` in IE 10/11
 * and Firefox.
 *IE10/11 及 Firefox 中 details` or `summary 无法块状显示
 * Correct `block` display not defined for `main` in IE 11.
 *在 IE11 中 main 不是块状级别。
 */

article,
aside,
details,
figcaption,
figure,
footer,
header,
main,
menu,
nav,
section,
summary {
  display: block;
}

/**
 * 1. Correct `inline-block` display not defined in IE 8/9.
 * 1.补充了 HTML5 新元素 inline-block 在 IE8/9 下的正确显示。
 * 2. Normalize vertical alignment of `progress` in Chrome, Firefox, and Opera.
 * 2.补充了部分 HTML5 新元素在浏览器下的垂直对齐方式为基线对齐（vertical-align: baseline）
 */

audio,
canvas,
progress,
video {
  display: inline-block; /* 1 */
  vertical-align: baseline; /* 2 */
}

/**
 * Prevent displaying `audio` without controls in Mobile Safari 4/5/6/7.
 * 如果 audio 标签没有控制栏，则应该隐藏
 */

audio:not([controls]) {
  display: none;
  height: 0;
}

/**
 * Address `[hidden]` styling not present in IE 8/9/10.
 * Hide the `template` element in IE 8/9/10/11, Safari, and Firefox < 22.
 * 新的 template 标签用于 HTML 模板，兼容旧浏览器，隐藏模板。
 */

[hidden],
template {
  display: none;
}

/* Links
   ========================================================================== */

/**
 * Remove the gray background color from active links in IE 10.
 * 移除在 IE10 下点击超链接出现的背景。
 */

a {
  background-color: transparent;
}

/**
 * Improve readability of focused elements when they are also in an
 * active/hover state.
 */

a:active,
a:hover {
  outline: 0;
}

/**
* Text-level semantics
* 语义化文本标签
*/
/*
   ========================================================================== */

/**
 * Address inconsistent styling of `abbr[title]`.
 * 1. Correct styling in Firefox 39 and Opera 12.
 * 2. Correct missing styling in Chrome, Edge, IE, Opera, and Safari.
 */

abbr[title] {
  border-bottom: none; /* 1 */
  text-decoration: underline; /* 2 */
  text-decoration: underline dotted; /* 2 */
}

/**
 * Address inconsistent styling of b and strong.
 * 统一了b,strong样式格式：
 * 1. Correct duplicate application of `bolder` in Safari 6.0.2.
 * 1.abbr 元素在 firefox 外其他的浏览器下没有下划线的问题
 * 2. Correct style set to `bold` in Edge 12+, Safari 6.2+, and Chrome 18+.
 * 2.统一了 Safari and Chrome 给 b 和 strong 设置的属性是bolder
 */
 
b,
strong {
  font-weight: inherit; /* 1 */
}

b,
strong {
  font-weight: bolder; /* 2 */
}

/**
 * Address styling not present in Safari and Chrome.
 * dfn 用于对特殊术语和专业短语的定义，在 safari 和 chrome 中不是斜体
 */

dfn {
  font-style: italic;
}

/**
 * Address variable `h1` font-size and margin within `section` and `article`
 * contexts in Firefox 4+, Safari, and Chrome.
 * 在 section 和 article 中 h1 标签的字体大小、margin 样式不统一
 */

h1 {
  font-size: 2em;
  margin: 0.67em 0;
}

/**
 * Address styling not present in IE 8/9.
 * mark 标签用来突出显示标记的文本，背后有一个高亮的背景色，低版本中并不识别。
 */

mark {
  background-color: #ff0;
  color: #000;
}

/**
 * Address inconsistent and variable font size in all browsers.
 * 统一了 small 标签在所有浏览器中的样式
 */
 
small {
  font-size: 80%;
}

/**
 * Prevent `sub` and `sup` affecting `line-height` in all browsers.
 * sub 和 sup 表示上标和下表，统一两者的样式。
 */
 
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}

sup {
  top: -0.5em;
}

sub {
  bottom: -0.25em;
}

/* Embedded content
   ========================================================================== */

/**
 * Remove border when inside `a` element in IE 8/9/10.
 * 移除了在IE 8/9/10下a标签img的边框(旧版本的IE浏览器下有蓝色边框)
 */
 
img {
  border: 0;
}

/**
 * Correct overflow not hidden in IE 9/10/11.
 * 图片多余部分在IE 9/10/11下不隐藏的问题
 */

svg:not(:root) {
  overflow: hidden;
}

/* Grouping content群组元素
   ========================================================================== */

/**
 * 修复margin不起作用问题
 */

figure {
  margin: 1em 40px;
}

/**
 * Address inconsistent styling of `hr`.
 * 统一了 hr 样式.
 * 1. Correct `box-sizing` set to `border-box` in Firefox.
 * 1. 在Firefox下设置了 `box-sizing` 为 `border-box`
 * 2. Correct `overflow` set to `hidden` in IE 8/9/10/11 and Edge 12.
 * 2. 修正在 IE 8/9/10/11 and Edge 12 下 overflow 值为 visible
 */

hr {
  box-sizing: content-box; /* 1 */
  height: 0; /* 1 */
  overflow: visible; /* 2 */
}

/**
 * Contain overflow in all browsers.
 * 原先标签多出的直接溢出，这里标签溢出增加滚动条.
 */

pre {
  overflow: auto;
}

/**
 * 1. Correct inheritance and scaling of font-size for preformatted text.
 * 2. Address odd `em`-unit font size rendering in all browsers.
 * 统一了在各个浏览器中字体样式
 */

code,
kbd,
pre,
samp {
  font-family: monospace, monospace; /* 1 */
  font-size: 1em; /* 2 */
}

/* Forms表单
   ========================================================================== */

/**
 * Known limitation: by default, Chrome and Safari on OS X allow very limited
 * styling of `select`, unless a `border` property is set.
 */

/**
 * 1. Correct font properties not being inherited.
 * 1. 纠正了表单标签字体不继承的问题。
 * 2. Address margins set differently in Firefox 4+, Safari, and Chrome.
 * 2. 在各个浏览器中外边距不统一
 */

button,
input,
optgroup,
select,
textarea {
  font: inherit; /* 1 */
  margin: 0; /* 2 */
}

/**
 * Address `overflow` set to `hidden` in IE 8/9/10/11.
 * 将button便签在IE 8/9/10/11溢出属性改为visible
 */

button {
  overflow: visible;
}

/**
 * Address inconsistent `text-transform` inheritance for `button` and `select`.
 * All other form control elements do not inherit `text-transform` values.
 * Correct `button` style inheritance in Firefox, IE 8/9/10/11, and Opera.
 * Correct `select` style inheritance in Firefox.
 * 纠正了button、select标签text-transform属性继承的问题。
 */
 
button,
select {
  text-transform: none;
}

/**
 * 1. Avoid the WebKit bug in Android 4.0.* where (2) destroys native `audio`
 *    and `video` controls.
 * 1. 避免 Android 4.0.* 中的 WebKit bug 破坏原生的 audio 和 video 控制器.
 * 2. Correct inability to style clickable `input` types in iOS.
 * 2. 无法设置可点击的 input 标签问题
 * 3. Improve usability and consistency of cursor style between image-type
 *    `input` and others.
 * 3. 统一其他类型的 input 光标样式
 */

button,
html input[type="button"], /* 1 */
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button; /* 2 */
  cursor: pointer; /* 3 */
}

/**
 * 统一按钮禁用时的鼠标光标样式
 */

button[disabled],
html input[disabled] {
  cursor: default;
}

/**
 * 移除 Firefox 4+ 下的边框和内边距.
 */

button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}

/**
 * Restore focus style in Firefox 4+ (unset by a rule above)
 */

button:-moz-focusring,
input:-moz-focusring {
  outline: 1px dotted ButtonText;
}

/**
 * 修复了Firefox 4+中设置`line-height`为normal!important样式。
 */

input {
  line-height: normal;
}

/**
 * It's recommended that you don't attempt to style these elements.
 * Firefox's implementation doesn't respect box-sizing, padding, or width.
 *
 * 1. Address box sizing set to `content-box` in IE 8/9/10.
 * 1. 修正checkbox、radio在IE 8/9/10下box sizing设置为content-box的问题
 * 2. Remove excess padding in IE 8/9/10.
 * 2. 移除checkbox、radio在IE 8/9/10中多余的内边距
 */

input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box; /* 1 */
  padding: 0; /* 2 */
}

/**
 * Fix the cursor style for Chrome's increment/decrement buttons. For certain
 * `font-size` values of the `input`, it causes the cursor style of the
 * decrement button to change from `default` to `text`.
 * 修正 input[type="number"] 光标改变效果
 */

input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}

/**
 * Address `appearance` set to `searchfield` in Safari and Chrome.
 * 修正在 chrome下 input[type="search"]appearance 值设置为 searchfield
 */

input[type="search"] {
  -webkit-appearance: textfield;
}

/**
 * Remove inner padding and search cancel button in Safari and Chrome on OS X.
 * Safari (but not Chrome) clips the cancel button when the search input has
 * padding (and `textfield` appearance).
 * 统一输入框的样式，移除了默认的一些样式。
 */

input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}

/**
 * 统一了fieldset的border、外边距和内边距
 */

fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}

/**
 * 1. Correct `color` not being inherited in IE 8/9/10/11.
 * 1. 在 IE 8/9/10/11下颜色不继承问题
 * 2. Remove padding so people aren't caught out if they zero out fieldsets.
 * 2. 重置了内边距
 */

legend {
  border: 0; /* 1 */
  padding: 0; /* 2 */
}

/**
 * Remove default vertical scrollbar in IE 8/9/10/11.
 * 移除了textarea在IE 8/9/10/11下的滚动条
 */

textarea {
  overflow: auto;
}

/**
 * Restore font weight (unset by a rule above).
 * NOTE: the default cannot safely be changed in Chrome and Safari on OS X.
 * 统一了optgroup标签的font-weight属性为bold
 */

optgroup {
  font-weight: bold;
}

/* Tables
   ========================================================================== */

/**
 * Remove most spacing between table cells.
 * 删除表格间的空白
 */

table {
  border-collapse: collapse;
  border-spacing: 0;
}

td,
th {
  padding: 0;
}
```

## resize.css

```css
/*Bsic reset*/
html{color:#000;background:#fff;}
body{font: 12px/1.5 Arial,宋体,sans-serif;}
body,h1,h2,h3,h4,h5,h6,p,dl,dt,dd,ul,ol,li,pre,
fieldset,legend,input,textarea,th,td{margin:0;padding:0;}
table{border-collapse:collapse;border-spacing:0;}
ul,li{list-style:none;}
fieldset,img{border:none;}
a{text-decretiom:none;color: #333333;}
a:hover{text-decoration:inline;color: #cc0000;}
input:focus{outline: none;}
/*旧浏览器html新增的标签无法识别块状显示*/
article,aside,details,figcaption,figure,footer,header,hgroup,menu,nav,section{display:block;}
```

## 参考：

1. [伪元素表单控件默认样式重置与自定义大全](http://www.zhangxinxu.com/wordpress/2013/06/%E4%BC%AA%E5%85%83%E7%B4%A0-%E8%A1%A8%E5%8D%95%E6%A0%B7%E5%BC%8F-pseudo-elements-style-form-controls/#input_number)