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
