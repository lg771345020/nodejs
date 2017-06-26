# MongoDB

MongoDB (非关系型数据库) 文档 集合 数据库。

MongoDB 适合存储：数据结构简单、数据量非常大、高并发读写的操作。

## linux 安装

1. 下载: monogodb(端口是28017)

        https://www.mongodb.com/dr/fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.4.4.tgz/download

2. 解压:

        tar -xvzf mongodb-linux-x86_64-3.2.10.tgz

3. 将 mongodb 复制到安装目录:

        mv mongodb-linux-x86_64-3.2.10 /usr/local/mongodb

4. 创建 mongodb 数据库存储目录和日志存储目录:

        cd /usr/local/mongodb/

        //数据库存储目录
        mkdir -p /data/db

        //日志文件存储目录
        mkdir -p /data/log
        touch mongodb.log

5. 启动 mongodb 服务端

        ./bin/mongod --dbpath=/usr/local/data/db --logpath=/usr/local/data/log/mongodb.log --fork

6. 启动 mongo 客户端

        ./bin/mongo

## mongodb 使用

#### 帮助系统

    help    //系统级帮助

    db.help()     //数据库组级别的帮助

    db.user.help()   //集合组别的帮助

#### 删除当前数据库中的集合

    db.user.drop()  //user 集合的名称

#### 使用 insert() 方法插入文档

    db.user.insert(document)

#### 使用 save() 方法插入文档

    //如果不指定 _id 字段 save() 方法类似于 insert() 方法。
    //如果指定 _id 字段 save() 方法更新文档。
    db.user.save(document)

#### 使用 update() 方法更新已存在的文档

    //query 查询条件
    //update 更新的对象
    //upsert 不存在则插入，默认为 false
    //multi 更新多条，默认为 false
    db.user.update(query, update, {upsert: true, multi: true})

    //所匹配记录 设置成 {name: 'join'}
    db.user.update({_id: 1}, {$set: {name: 'join'}})

    //所有记录 age 自增2
    db.user.update({}, {$inc: {age: 2}})

#### 使用 remove() 方法删除已存在的文档

    db.user.remove(query, {})
    
#### 使用 find() 方法查找文档 

   //查找记录，只显示 name 列
   db.user.find(query, {name: 1})

** query 查询操作符 **

操作|符号
--|----
= | {key: value}
\> | {key: {$gt: value}}
\>=| {key: {$gt: value}}
< | {key: {$gt: value}}
<=| {key: {$gt: value}}

** 使用 _id 查找 **

    {_id: Object(id)}

#### 使用 limit() 方法查找文档

   db.user.find().limit(num)   //查找前 num 记录

#### 使用 skip() 方法查找文档

   db.user.find().skip(num)   //忽略前 num 记录