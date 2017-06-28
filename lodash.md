# lodash

[`lodashjs`](http://lodashjs.com/docs/) 是一套 js 工具库，它内部封装了诸多对字符串、数组、对象等常见数据类型的处理函数

## 模块组成

Lodash 提供的辅助函数主要分为以下几类，函数列表和用法实例请查看 Lodash 的官方文档：

* `Array`，适用于数组类型，比如填充数据、查找元素、数组分片等操作

* `Collection`，适用于数组和对象类型，部分适用于字符串，比如分组、查找、过滤等操作

* `Function`，适用于函数类型，比如节流、延迟、缓存、设置钩子等操作

* `Lang`，普遍适用于各种类型，常用于执行类型判断和类型转换

* `Math`，适用于数值类型，常用于执行数学运算

* `Number`，适用于生成随机数，比较数值与数值区间的关系

* `Object`，适用于对象类型，常用于对象的创建、扩展、类型转换、检索、集合等操作

* `Seq`，常用于创建链式调用，提高执行性能（惰性计算）

* `String`，适用于字符串类型

## _.find(collection, [predicate=_.identity], [thisArg])

查找匹配到的记录，只查找一条记录

```js
var users = [
  { 'user': 'barney',  'age': 36, 'active': true },
  { 'user': 'fred',    'age': 40, 'active': false },
  { 'user': 'pebbles', 'age': 1,  'active': true }
];

_.result(_.find(users, function(chr) {
  return chr.age < 40;
}), 'user');
// => 'barney'
```

## _.escape([string=''])

将 "&", "<", ">", '"', "'", "`" 转换成 html 实体

```js
var escapeSignature = function (signature) {
    return signature.split('\n').map(function (p) {
        return _.escape(p);
    }).join('<br>');
};

console.log(escapeSignature('&\n<div>hello, "leigang"</div>\n你好'))
// => &amp;<br>&lt;div&gt;hello, &quot;leigang&quot;&lt;/div&gt;<br>你好
```