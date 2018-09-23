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

### 二、Git工具的配置与简单操作  
本节的内容是安装git工具，并结合GitHub学习一些基本的git操作命令。在开始之前，我们默认阅读本文档的读者了解基本的Linux命令。本文当中，安装的Linux版本是GNU/Linux 4.4.0-92-generic i686。**根据Linux版本的不同，输入的命令可能有所不同。 遇到命令失效时，[点击这里](www.baidu.com)。**

[What is Git?](www.baidu.com)  
[What is GitHub?](www.baidu.com)  
  
### 2.1 git的本地配置
* 用putty登录云服务器，输入如下命令：
```
sudo apt get install git
```
一系列的输出后，再次输入上述命令，出现下图即为安装成功。  
![install git]()

* 安装成功后，添加git账号，此账号是本地的，可以随时修改。在这里我输入的名字是nuaa:teaching2018  
```
git config --global user.name 'your name'
git config --global user.email 'your email'   
```
输入一下命令，检查是否添加正确。
```
git config --get-all user.name
git config --get-all user.email
```
![git config user]()

* 新建密匙  
我们先不着急了解何谓“密匙”。做到后面自然会知道。  
输入一下命令：   
```
ssh-keygen -C 'xxxxx@xxx.com' -t rsa
```  
会要求输入一个文件名，我的输入：gitKey.pub，注意扩展名即可,名字任意。
若要求密码可不填，直接回车。显示当前的文件，会发现多了两个文件。
**gitKey.pub是私人的密匙，gitKey.pub.pub是公共密匙。**
![ls gitkey file]()  

### 2.2 git与GitHub   
* 注册并登陆登录Github网站，右上角“Settings -> SSH and GPG keys -> New SSH keys”.  
Title任意，key填写**公共密匙xxx.pub.pub**里面的内容。  
![add ssh keys]()

* 点击网页右上角加号‘+’，“New Repository”填写相关信息。此处我新建了一个*nuaa-teaching2018*的仓库，后面我们就是将本地的文件备份到此仓库，或者把仓库中的项目开发代码clone到CVM。下面正式展示git的基本操作。  

* 在CVM中新建文件夹softwareTesting。输入如下命令初始化：
```
git init
```  
![git init]()

* 在此，将CVM的softwareTesting称为本地仓库，GitHub上的nuaa-teaching2018称为远程仓库。  
输入命令，关联本地仓库与远程仓库：
```
git remote add origin git@'你的仓库url地址'
```  

查看是否关联成功：
```
git remote -v
```  
成功如图：
![git remote -v]()

* 下载GitHub上nuaa-teaching2018仓库的文件到本地。  
```
git clone '你的仓库地址'
```  
![git clone]()

后在softwareTesting查看，会出现nuaa-teahing2018的文件夹。
![check git clone]()

* 接下来，我们在本地完成了一些代码，现在要把它推送到远程仓库中备份。  
在softwareTesting/nuaa-teaching2018写一个hello.cpp
```C++
#include<iostream>
#include<stdio.h>
int main()
{
        std::cout<<"Hello world from C++.\n"<<endl;
        printf("Hello world from C!\n");
        return 0;
}
```  
输入命令：  
```
git add hello.cpp
git commit -m "你的提交备注信息"
git push origin master
```  
会要求输入GitHub账号密码。  
这里我们都是在master分支上完成的，请根据自己的需要是否新建分支。（翻一翻PA教程）   
git add的作用是把文件添加到git的列表，决定push的时候是否上传这个文件。如果是添加所有文件，则是
```
git add .
```

![git push]()  

* 查看GitHub上的远程仓库，会发现nuaa-teaching2018下多了一个hello.cpp。   
![check push]()
注意到第一行的信息，图中红框。first commit 是提交时的备注信息，前面是2.1节中添加的本地用户名。


* 在CVM中输入git log，同样可查看你的提交记录。
![git log]()


