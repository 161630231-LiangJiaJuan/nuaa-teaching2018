# 软件测试实验报告  
### 一、云服务器的注册与安装
* 首先，进入[腾讯云官网](https://cloud.tencent.com/)，注册登录。登陆后，会有各种套餐推送，选最便宜的。具体操作并不复杂，不展开说明。如果在注册CVM(Cloud Virtual Machine)遇到任何问题，请参考[腾讯云CVM入门](https://cloud.tencent.com/product/cvm/getting-started)。

* 完成配置后，查看网页右上角的消息中心，会收到一封邮件里面是云服务器的相关信息。  
![CVM-Info](www.baidu.com)

* 打开putty，填入如下图的信息HostName是CVM公网IP，PORT端口填写22，SSH方式连接。第一次登录连接收到警告，点击Yes即可。  
![putty-login](www.baidu.com)

* 填写用户名和密码，即官方消息中给出的账号密码。建议修改初始密码。登录成功之后就跟PA所使用的Linux系统差不多。见下图。
![cvm-login]()  

* 如果遇到任何问题，请查询[腾讯云CVM入门](https://cloud.tencent.com/product/cvm/getting-started)。

### 二、Git工具的安装
    本节的内容是安装git工具，并结合GitHub学习一些基本的git操作命令。在开始之前，我们默认阅读本文档的读者了解基本的Linux命令。   
[What is Git?](www.baidu.com)  
[What is GitHub?](www.baidu.com)  
  
* 用putty登录云服务器，输入如下命令：
