# express

## express 配置

### 模板文件路径
```js
//模板文件路径
app.set('views', path.join(__dirname, 'views'));
```

## 模板引擎 html

    npm install ejs-mate --save

### 使用

```js
//模板引擎为 html 后缀
app.set('view engine', 'html');
app.engine('html', require('ejs-mate'));
```

## 日志

    npm install morgan --save

```js
var logger = require('morgan');
app.use(logger('dev'));
```




