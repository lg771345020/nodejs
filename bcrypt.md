# bcryptjs

[`bcryptjs`](https://www.npmjs.com/package/bcryptjs) 模块是比 nodejs 自带的 crypt 更好用的加密模块

## 例子

新建 toos.js 文件

```js
var bcrypt = require('bcryptjs');

/**
 * hash + salt 加密算法
 * callback
 * - err 错误
 * - hash 加密后的数据
 */
exports.bhash = function (str, callback) {
  bcrypt.hash(str, 10, callback);
};
```
