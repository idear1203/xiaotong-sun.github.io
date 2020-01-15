## 使用Hexo+Github搭建个人网站（Ubuntu19.10）
##### 工具：node.js, npm, Hexo, Github
##### 前提： git工具， github账号， 基本的git操作
---
#### 一：什么是Hexo
**Hexo**是一个快速、简洁且高效的博客框架。 **Hexo**使用Markdown解析文章，在几秒内，即可利用靓丽的主题生成静态网页。
+ **nodejs官方网站：https://hexo.io/**
+ ***Hexo的安装和使用，必须有node.js环境***

#### 二：准备工作
1. **什么是node.js？**
node.js是能够在服务器端运行JavaScript的开放源代码、跨平台JavaScript运行环境
2. **安装nodejs和npm**
对于ubuntu这样的Linux系统来说，安装nodejs和npm比较简单，可以通过终端命令完成
        $sudo apt install nodejs
        $sudo apt install npm
通过以下命令检查安装的nodejs和npm版本
        $node -v
        $npm -v
nodejs官网已推送至12.14.1版本，npm为6.13.4版本，若所安装的版本过低并且像笔者一样不会通过源码包安装的童鞋可以参考下面网站所示方法：http://github.com/nodesource/distributions/blob/master/README.md

#### 三：安装Hexo框架
+ 打开终端，依次输入：
        $npm install hexo-cil -g                  #安装hexo-cli命令
        
        $hexo init <file>                                 #初始化博客文件
        
        $cd <file>                                              #跳转到博客文件夹
        
        $npm install                                       #还原各种包的关联
        
        $hexo server                                      #进行预览
 参考网址：https://hexo.io/
 
 以上步骤完成后，博客网址完成基本搭建。
 

 #### 四：关联github
 1. **在github上新建一个仓库。**
 
 仓库命名要严格按照以下格式：
         <github用户名>.github.io

![](2020-01-15 16-37-10 的屏幕截图.png)
+ **用README初始化也是必须的。**

+  ***由于我已经创建好库，所以会显示重复命名***

**2.获得ssh密匙**
  在本地通过终端输入：
  
  
  
    $ssh -keygen
一路enter下去，就会在当前用户名下生成一个**.ssh文件夹**
打开.ssh文件夹中的**id_rsa.pub文件并复制所有内容**


**3.在github上填入公匙，即所复制的内容**

 ![](2020-01-15 16-58-06 的屏幕截图.png)
  ![](2020-01-15 16-58-27 的屏幕截图.png)

![](2020-01-15 16-58-50 的屏幕截图.png)

4.**判断ssh是否添加成功**
终端输入


         
        $ssh -T git@github.com
        
如果出现你的用户名，那么表示ssh添加成功

5.**配置文件，将博客与github关联**
打开博客根目录下的_config.yml文件，这是博客的配置文件，可在此修改与博客相关的各种信息
+ 打开后修改最后一行的配置
        deploy:
      type: git
      repo: git@github.com:xiaotong-sun/xiaotong-sun.github.io.git        # 根据自己的仓库地址填写
      branch: master
 
 
 #### 五：最后一步
 终端执行：
 
         $hexo clean
         $hexo g -d   
         
## 到此博客网站正式搭建成功##