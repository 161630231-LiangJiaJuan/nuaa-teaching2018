# 软件测试实验报告  
## 一、云服务器的注册与安装
* 首先，进入[腾讯云官网](https://cloud.tencent.com/)，注册登录。登陆后，会有各种套餐推送，选最便宜的。具体操作并不复杂，不展开说明。如果在注册CVM(Cloud Virtual Machine)遇到任何问题，请参考[腾讯云CVM入门](https://cloud.tencent.com/product/cvm/getting-started)。

* 完成配置后，查看网页右上角的消息中心，会收到一封邮件里面是云服务器的相关信息。  
![CVM-Info](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image036.jpg?raw=true)  

* 打开putty，填入如下图的信息HostName是CVM公网IP，PORT端口填写22，SSH方式连接。第一次登录连接收到警告，点击Yes即可。    
![putty-login](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image038.jpg?raw=true)

* 填写用户名和密码，即官方消息中给出的账号密码。建议修改初始密码。登录成功之后就跟PA所使用的Linux系统差不多。

* 如果遇到任何问题，请查询[腾讯云CVM入门](https://cloud.tencent.com/product/cvm/getting-started)。

## 二、Git工具使用  
本节的内容是安装git工具，并结合GitHub学习一些基本的git操作命令。在开始之前，我们默认阅读本文档的读者了解基本的Linux命令。本文当中，安装的Linux版本是GNU/Linux 4.4.0-92-generic i686。**根据Linux版本的不同，输入的命令可能有所不同。**

[What is Git?](https://www.baidu.com)  
[What is GitHub?](https://www.baidu.com)  
  
### 2.1 git的本地配置
* 用putty登录云服务器，输入如下命令：
```
sudo apt get install git
```
一系列的输出后，再次输入上述命令，出现下图即为安装成功。  
![install git](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image001.png?raw=true)

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

![git config user](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image005.png?raw=true)

* 新建密匙  
我们先不着急了解何谓“密匙”。做到后面自然会知道。  
输入一下命令：   
```
ssh-keygen -C 'xxxxx@xxx.com' -t rsa
```  
会要求输入一个文件名，我的输入：gitKey.pub，注意扩展名即可,名字任意。
若要求密码可不填，直接回车。显示当前的文件，会发现多了两个文件。
**gitKey.pub是私人的密匙，gitKey.pub.pub是公共密匙。**  

![ls gitkey file](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image013.png?raw=true)  

### 2.2 git与GitHub   
* 注册并登陆登录Github网站，右上角“Settings -> SSH and GPG keys -> New SSH keys”.  
Title任意，key填写**公共密匙xxx.pub.pub**里面的内容。  
![add ssh keys](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image009.png?raw=true)

* 点击网页右上角加号‘+’，“New Repository”填写相关信息。此处我新建了一个*nuaa-teaching2018*的仓库，后面我们就是将本地的文件备份到此仓库，或者把仓库中的项目开发代码clone到CVM。下面正式展示git的基本操作。  

* 在CVM中新建文件夹softwareTesting。输入如下命令初始化：
```
git init
```  
![git init](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image015.png?raw=true)

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

![git remote -v](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image019.png?raw=true)

* 下载GitHub上nuaa-teaching2018仓库的文件到本地。  
```
git clone '你的仓库地址'
```  
![git clone](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image021.png?raw=true)

后在softwareTesting查看，会出现nuaa-teahing2018的文件夹。  


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

![git push](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image025.png?raw=true)  

* 查看GitHub上的远程仓库，会发现nuaa-teaching2018下多了一个hello.cpp。   

![check push](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image029.png?raw=true)  

注意到第一行的信息。first commit 是提交时的备注信息，前面是2.1节中添加的本地用户名。


* 在CVM中输入git log，同样可查看你的提交记录。  
![git log](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/image033.png?raw=true)  

* 到这里，基本学会了**备份操作**了- -。

## 三、Redmine的配置和使用
本节的内容是在云服务器上配置Redmine。  

### 3.1 Redmine的安装
* 安装Redmine  
先从[Bitnami](https://bitnami.com/)下载Redmine的安装包。  

* 把Redmine安装包通过sftp上传到云服务器。  
* 通过一下命令初始化安装包，目的是给redmine.run赋予执行安装的权限。执行完之后文件名会`变绿`。然后执行第二条命令启动安装包。
```
chmod +x xxxx.run
sudo ./xxxx.run
```

* 按照指引即可完成安装。最后通过浏览器访问redmine项目。url地址是`http://120.78.188.73:80`。  
`120.78.188.73`是公网云服务器IP，80是端口。  
可能存在80端口被占/关闭的情况（身边有同学遇到，但是我并没有）。


### 3.2 Redmine的使用介绍
访问[我的Redmine主页](http://120.78.188.73/redmine/)， 点击右上角登录，账号密码在安装过程中已有提示进行设置。    
根据老师要求：   
账号为：`unaa`     
密码为：`teaching2018`     
随意新建了一个`nuaa-teaching`的项目。     
登录后界面如下：     
![redmine logic in](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/redmine%20logic%20in.png?raw=true)      


* **活动**   
`活动`标签按照时间顺序展示所有人员对项目的操作。
![acivity](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/1.png?raw=true)  


* **添加问题追踪**   
如下图。作用是添加项目问题，其中问题可以是：功能模块设计/开发/BUG，并指派负责的人员。     
![add bug](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/5.png?raw=true)    
   
点击进入问题的详细页面，可追踪该问题，并添加项目组成员的工时。    
![detail bug](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/6.png?raw=true)  


* **查看各项耗时**   
如下图，点击`耗时`标签，可查看之前添加的耗时。   
![time](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/3.png?raw=true)     

* **甘特图**   
`甘特图`显示问题的起止日期以及版本的截至日期。      
![甘特图](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/4.png?raw=true)  


* **日历**  
`日历`可显示项目从创建到当前这一时间跨度的所有活动。  

* **文档**   
`文档`区域用于展示项目组各个工作人员在开发/测试过程中所保留的说明文档。     

* **配置**   
`配置`标签是对Redmine的页面进行布局，可以选择/删除你需要/不需要的功能标签。     

* **工作台**  
`工作台`在页面的左上角，可以查看**指派给自己的所有工作**。   
![工作台](https://github.com/sinkinben/nuaa-teaching2018/blob/master/images/2.png?raw=true)   




    





