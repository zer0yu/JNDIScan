# JNDIScan

![](https://img.shields.io/badge/build-passing-brightgreen)
![](https://img.shields.io/badge/golang-1.17-blue)

## ⚠️免责声明

### 该工具不具备任何攻击性，主要适用于甲方内网自测

在原有的协议中追加以下内容：

本项目禁止进行未授权商业用途

本项目禁止二次开发后进行商业用途

本项目仅面向合法授权的企业安全建设行为，在使用本项目进行检测时，您应确保该行为符合当地的法律法规，并且已经取得了足够的授权

如您在使用本项目的过程中存在任何非法行为，您需自行承担相应后果，我们将不承担任何法律及连带责任

在使用本项目前，请您务必审慎阅读、充分理解各条款内容，限制、免责条款或者其他涉及您重大权益的条款可能会以加粗、加下划线等形式提示您重点注意

除非您已充分阅读、完全理解并接受本协议所有条款，否则，请您不要使用本项目

您的使用行为或者您以其他任何明示或者默示方式表示接受本协议的，即视为您已阅读并同意本协议的约束

## 介绍
这是什么？

该项目一款无须借助`dnslog`且完全无害的`JNDI`反连检测工具，解析`RMI`和`LDAP`协议实现，可用于甲方内网自查

特点：
- 由`Golang`编写，直接运行可执行文件进行检测
- 完全无害，不存在任何`Payload`仅基于`LDAP`和`RMI`协议检测
- 根据检测结果动态生成`HTML`页面
- 检测当前内网和外网的IP打印可用的`Payload`

![](https://github.com/EmYiQing/JNDIScan/blob/master/img/01.png)

## 使用

使用`${jndi:ldap://ip:端口/}`这样的`Payload`

如果目标存在漏洞，该项目就会收到`ldap/rmi`请求，从而快速定位哪些目标存在漏洞

![](https://github.com/EmYiQing/JNDIScan/blob/master/img/02.png)

命令：`./JNDIScan -p port(默认8001)`

```text
       ___   ______  _________
      / / | / / __ \/  _/ ___/_________ _____
 __  / /  |/ / / / // / \__ \/ ___/ __ `/ __ \
/ /_/ / /|  / /_/ // / ___/ / /__/ /_/ / / / /
\____/_/ |_/_____/___//____/\___/\__,_/_/ /_/
    coded by 4ra1n
[+] [11:55:41] use port: 8001
[+] [11:55:41] start fake reverse server
|-------------------------------------------|
|--Payload: ldap://192.168.1.4:8001---------|
|--Payload: ldap://127.0.0.1:8001-----------|
|--Payload: ldap://your-ip:8001-------------|
|--Payload: rmi://192.168.1.4:8001/xxx------|
|--Payload: rmi://127.0.0.1:8001/xxx--------|
|--Payload: rmi://your-ip:8001/xxx----------|
|-------------------------------------------|

```

只需要将`Payload`设置为输出的这些之一

即可在命令行看到连接结果，当前目录的`result.html`是动态渲染后的`HTML`页面

## 其他

其实该项目是我与某位大佬共同开发的，由于一些原因他让我删了他的ID

本来支持动态的web页面，由于一些原因被迫删除，并且不会再添加该功能