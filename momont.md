# moment

格式化时间，详情查阅 [`momentjs`](http://momentjs.com/docs/#/parsing/)

## 安装

    npm install moment --save

## 例子:

```js
var moment = require('moment');

moment.locale('zh-cn'); // 使用中文

// friendly 为 true 时，将 date 格式化，flase 时，计算已过去多长时间
exports.formatDate = function (date, friendly) {
  date = moment(date);

  if (friendly) {
    return date.fromNow();
  } else {
    return date.format('YYYY-MM-DD HH:mm');
  }
};
```