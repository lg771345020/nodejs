# mongoose

## 安装

    npm i mongoose --save

## 一、快速通道

### 1.1 名词解释

   `Schema`  ：  一种以文件形式存储的数据库模型骨架，不具备数据库的操作能力

   `Model`   ：  由Schema发布生成的模型，具有抽象属性和行为的数据库操作对

   `Entity`  ：  由Model创建的实体，他的操作也会影响数据库

注意：

1. 本学习文档采用严格命名方式来区别不同对象，例如：

```js
var PersonSchema;   //Person的文本属性
var PersonModel;    //Person的数据库模型
var PersonEntity;   //Person实体
```

2. Schema、Model、Entity 的关系请牢记，Schema 生成 Model，Model 创造 Entity，Model 和 Entity 都可对数据库操作造成影响，但 Model 比 Entity 更具操作性。


### 1.2 准备工作

1. 首先你必须安装 [MongoDB]() 和 [NodeJS]()

2. 执行如下的代码，测试 mongodb 是否连接成功:

    var mongoose = require('mongoose');

    //创建一个数据库连接
    var db = mongoose.createConnection('localhost','test');

    db.on('error', function (err) {
        console.log('数据库连接失败');
    });
    db.once('open', function () {
        console.log('数据库连接成功');

        //对数据库进行操作
    });

### Model.find

`Mongoose` 模型提供了 find, findOne, 和 findById 方法用于文档查询。

#### Model.find

```js
Model.find(query, fields, options, callback)
// fields 和 options 都是可选参数
```

**简单查询**

```js
Model.find({ 'csser.com': 5 }, function (err, docs) {
  // docs 是查询的结果数组
});
```

**只查询指定键的结果**

```js
Model.find({}, ['first', 'last'], function (err, docs) {
  // docs 此时只包含文档的部分键值
})
```

#### Model.findOne

与 Model.find 相同，但只返回单个文档

```js
Model.findOne({ age: 5}, function (err, doc){
  // doc 是单个文档
});
```

#### Model.findById

与 findOne 相同，但它接收文档的 _id 作为参数，返回单个文档。_id 可以是字符串或 ObjectId 对象。

```js
Model.findById(obj._id, function (err, doc){
  // doc 是单个文档
});
```

#### Model.count

返回符合条件的文档数。

```js
Model.count(conditions, callback);
```js

#### Model.remove

删除符合条件的文档。

```js
Model.remove(conditions, callback);
```

#### Model.distinct

查询符合条件的文档并返回根据键分组的结果。

```js
Model.distinct(field, conditions, callback);
```

#### Model.where

当查询比较复杂时，用 where：

```js
Model
.where('age').gte(25)
.where('tags').in(['movie', 'music', 'art'])
.select('name', 'age', 'tags')
.skip(20)
.limit(10)
.asc('age')
.slaveOk()
.hint({ age: 1, name: 1 })
.run(callback);
```

#### Model.$where

有时我们需要在 MongoDB 中使用 JavaScript 表达式进行查询，这时可以用 find({$where : javascript}) 方式，$where 是一种快捷方式，并支持链式调用查询。

```js
Model.$where('this.firstname === this.lastname').exec(callback)
```

#### Model.update

使用 update 子句更新符合指定条件的文档，更新数据在发送到数据库服务器之前会改变模型的类型。

```js
var conditions = { name: 'borne' },
    update = { $inc: { visits: 1 }},
    options = { multi: true };

Model.update(conditions, update, options, callback)
```

注意：为了向后兼容，所有顶级更新键如果不是原子操作命名的，会统一被按 $set 操作处理，例如：

```js
var query = { name: 'borne' };
Model.update(query, { name: 'jason borne' }, options, callback)

// 会被这样发送到数据库服务器
Model.update(query, { $set: { name: 'jason borne' }}, options, callback)
```

#### 查询 API

如果不提供回调函数，所有这些方法都返回 Query 对象，它们都可以被再次修改（比如增加选项、键等），直到调用 exec 方法。

```js
var query = Model.find({});

query.where('field', 5);
query.limit(5);
query.skip(100);

query.exec(function (err, docs) {
  // called when the `query.complete` or `query.error` are called
  // internally
});
```