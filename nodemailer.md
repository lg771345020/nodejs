# nodemailer

[`nodemailer`](https://nodemailer.com/about/) 发送邮件 email.

```js
var nodemailer = require('nodemailer');
var smtpTransport = require('nodemailer-smtp-transport');

// 开启一个 SMTP 连接池
var transport = nodemailer.createTransport(smtpTransport({
    host: "smtp.qq.com", // 主机
    secure: true, // 使用 SSL
    port: 465, // SMTP 端口
    auth: {
        user: "771345020@qq.com", // 账号
        //这里密码不是qq密码，是你设置的smtp密码
        pass: "pdykavtpyatkbfgi"
    }
}));

// 设置邮件内容
var mailOptions = {
    from: "771345020<771345020@qq.com>", // 发件地址
    to: "leigang023081@163.com", // 收件列表
    subject: "Hello world", // 标题
    text:"hello",
    html: "<b>thanks a for visiting!</b> 世界，你好！" // html 内容
}

// 发送邮件
transport.sendMail(mailOptions, function(error, response) {
    if (error) {
        console.error(error);
    } else {
        console.log(response);
    }
    transport.close(); // 如果没用，关闭连接池
});
```

## 应用

新建 nodeclub/common/mail.js

```js
var mailer = require('nodemailer');
var smtpTransport = require('nodemailer-smtp-transport');
var logger = require('./logger');
var util = require('util');
var config = require('../config');
var transport = mailer.createTransport(smtpTransport(config.mail_opts));
var async = require('async');
var SITE_ROOT_URL = 'http://' + config.host;

/*
 * 发送邮件
 * data (Object) 邮件对象的封装
 */
exports.sendMail = function(data){
    // if(config.debug) return;

    // 重试5次
    async.retry({times: 5}, function (done) {
        transport.sendMail(data, function (err, info) {
            //邮件发送失败
            if(err) {
                logger.error('send email error', err, data);
                return done(err, info);
            }
            //邮件发送成功
            return done(null, info);
        });
    }, function (err, info) {
        if(err) {
            return logger.error('send mail finally error', err, data);
        }
        logger.info('send mail success', data);
    });
}


/**
 * 发送激活通知邮件
 * @param {String} who 接收人的邮件地址
 * @param {String} token 重置用的token字符串
 * @param {String} name 接收人的用户名
 */
exports.sendActiveMail = function (who, token, name) {
    var from    = util.format('%s <%s>', config.name, config.mail_opts.auth.user);
    var to      = who;
    var subject = config.name + '社区帐号激活';
    var html    = '<p>您好：' + name + '</p>' +
        '<p>我们收到您在' + config.name + '社区的注册信息，请点击下面的链接来激活帐户：</p>' +
        '<a href  = "' + SITE_ROOT_URL + '/active_account?key=' + token + '&name=' + name + '">激活链接</a>' +
        '<p>若您没有在' + config.name + '社区填写过注册信息，说明有人滥用了您的电子邮箱，请删除此邮件，我们对给您造成的打扰感到抱歉。</p>' +
        '<p>' + config.name + '社区 谨上。</p>';

    exports.sendMail({
        from: from,
        to: to,
        subject: subject,
        html: html
    });
};

/**
 * 发送密码重置通知邮件
 * @param {String} who 接收人的邮件地址
 * @param {String} token 重置用的token字符串
 * @param {String} name 接收人的用户名
 */
exports.sendResetPassMail = function (who, token, name) {
    var from = util.format('%s <%s>', config.name, config.mail_opts.auth.user);
    var to = who;
    var subject = config.name + '社区密码重置';
    var html = '<p>您好：' + name + '</p>' +
        '<p>我们收到您在' + config.name + '社区重置密码的请求，请在24小时内单击下面的链接来重置密码：</p>' +
        '<a href="' + SITE_ROOT_URL + '/reset_pass?key=' + token + '&name=' + name + '">重置密码链接</a>' +
        '<p>若您没有在' + config.name + '社区填写过注册信息，说明有人滥用了您的电子邮箱，请删除此邮件，我们对给您造成的打扰感到抱歉。</p>' +
        '<p>' + config.name + '社区 谨上。</p>';

    exports.sendMail({
        from: from,
        to: to,
        subject: subject,
        html: html
    });
};
```
## 资料参考：

* [node.js 发送邮件 email](http://www.cnblogs.com/pingfan1990/p/4864822.html)

* [qq 邮箱 smpt 设置独立密码](http://www.yzmg.com/app/103426.html)
