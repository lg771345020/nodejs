# mongodb

## linux 安装

**下载**

1. 下载: monogodb(端口是28017)

    https://www.mongodb.com/dr/fastdl.mongodb.org/linux/mongodb-linux-x86_64-3.4.4.tgz/download

2. 解压:

    tar -xvzf mongodb-linux-x86_64-3.2.10.tgz

3. 将 mongodb 复制到安装目录:

    mv mongodb-linux-x86_64-3.2.10 /usr/local/mongodb

4. 创建 mongodb 数据库存储目录和日志存储目录:

    cd /usr/local/mongodb/

    //默认数据目录
    mkdir -p /data/db

    //默认数据目录
    mkdir -p /data/log
    touch mongodb.log

5. 启动 mongodb 服务端

    ./bin/mongod --dbpath=/usr/local/data/db --logpath=/usr/local/data/log/mongodb.log --fork

6. 启动 mongo 客户端

    ./bin/mongod