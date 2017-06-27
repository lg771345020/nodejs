# lodash

js 函数库，详情查阅 [`lodashjs`](http://lodashjs.com/docs/)

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