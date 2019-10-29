在线词典

1.确定技术点

  并发模型和网络模型
    多进程tcp 并发模型


  确定细节功能,注册要注册什么.注册后是否
    注册: 用户名密码,加密存储,注册后直接登录
    历史记录 : 最近的前10个

  直接登录一级界面,二级界面如何切换
   循环切换

2.mysql数据库设计 dict
  words
  users 建立用户信息表(用户id,用户名,用户密码,用户查询记录,用户查询时间)
  user:(id  name passwd)
  create table user (id int primary key auto_increment,name varchar(32) not null,passwd char(128) not null);

  hist:(id name word time)
  create table hist (id int primary key auto_increment,name varchar(32) not null,word varchar(32) not null,time datetime default now());


3.结构设计,功能模块划分
  如何封装,客户端和服务端工作流程,有几个功能模块
  * 函数封装
  * 图解工作流程
  * 功能模块: 通信,登录,注册,查询,历史记录

4.通信搭建

5.登录
     客户端:输入用户名密码
           发送请求
           接收反馈

     服务端:接收请求,判断请求类型
           判断用户可否登录
           给客户端反馈

  注册
     客户端: 输入用户名密码
               发送请求
               接收反馈

     服务端: 接收请求,判断请求类型
            判定用户可否注册
            给客户端反馈

  查询
     客户端:输入单词
           发送请求 (套接字)
           接收反馈

     服务端:接收请求,判断请求类型
           查找单词
           插入历史记录
           给客户端反馈

  历史记录

协议: 登录 L
     注册 R
     查单词 Q
     历史记录 H
     退出 E

cookie:
    import getpass

    pwd  = getpass.getpass()
    功能:隐藏输入内容

    import hashlib

    hash = hashlib.md5()
    功能:生成md5对象
    参数:  盐 (自定义的字节串)

    hash.update(passwd.encode())
    功能: 进行加密处理
    参数: 密码转换为字节串

    new_passwd = hash.hexdigest()
    功能: 得到转换后的密码
