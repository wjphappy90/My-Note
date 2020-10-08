## 1、基本概念

### 1.1、web开发

**web**，

- 网页的意思，如www.baidu.com

**静态web**

- html,css
- 提供给所有人看的数据始终不会发生变化

**动态web**

- 淘宝，几乎是所有的网站;
- 提供给所有人看的数据始终会发生变化。每个人在不同的时间，不同的地点看到的信息各不相同!
- 技术栈: Servlet/JSP, ASP, PHP
- 在Java中，静态动态web资源开发的技术统称为JavaWeb;

### 1.2、web应用程序

- web应用程序:可以提供浏览器访问的程序;
- a.html. .多个web资源，这些web资源可以被外界访问,对外界提供服务;
- 你们能访问到的任何-个页面或者资源，都存在于这个世界的某-个角落的计算机上。
- URL
- 这个统一的web资源会被放在同一个文件夹下，web应用程序-->Tomcat:服务器
  - html, CSS, js
  - jsp, servlet
  - 一个web应用由多部分组成(静态web,动态web)
  - Java程序
  - jar包 配置文件(Properties)
- web应用程序编写完毕后，若想提供给外界访问:需要一个服务器来统一 管理;

### 1.3、静态web

1. *.htm, *.html,这些都是网页的后缀，如果服务器.上一直存在这些东西，我们就可以直接进行读取。联络

![img](img/1905053-20200401132353197-991152038.png)

1. 静态web存在的缺点
   - Web页面无法动态更新，所有用户看到都是同一个页面
     - 轮播图，点击特效:伪动态
     - JavaScript [实际开发中，它用的最多]
     - VBScript
   - 它无法和数据库交互(数据无法持久化，用户无法交互)

### 1.4、动态web

1. 页面会动态展示: "Web的页面展示的效果因人而异";

   ![img](img/1905053-20200401132409975-283882118.png)

2. 缺点

   加入服务器的动态web资源出现了错误，我们需要重新编写我们的后台程序,重新发布;-----停机维护

3. 优点

   - Web页面可以动态更新，所有用户看到的都不是同一个页面

   - 它可以与数据库交互（数据持久化：注册，商品信息，用户信息...）

     ![img](img/1905053-20200401132424678-1195800405.png)

## 2、web服务器

### 2.1、三种

ASP:

- 微软:国内最早流行的就是ASP;
- 在HTML中嵌入了VB的脚本, ASP + COM;
- 在ASP开发中,基本-个页面都有几千行的业务代码， 页面极其换乱●维护成本高!●C#|

php:

- PHP开发速度很快，功能很强大,跨平台,代码很简单(70% , WP)无法承载大访问量的情况(局限性)

JSP/Servlet :

- B/S:浏览和服务器;
- C/S:客户端和服务器
  - sun公司主推的B/S架构
  - 基于Java语言的(所有的大公司,或者些开源的组件,都是用Java写的)
  - 可以承载三高(高并发，高可用，高性能)问题带来的影响;
  - 语法像ASP，ASP-->JSP ,加强市场强度;

### 2.2、web服务器简介

- 服务器是一种被动的操作，用来处理用户的- -些请求和给用户-一些响应信息;

- 两种服务器

  - **IIS**:微软的; ASP...Windows中自带的

  - Tomcat

     

    面向百度编程;

    - Tomcat是Apache软件基金会(Apache Software Foundation)的Jakarta项目中的一个核心项目, 最新的
    - Servlet和ISP规范总是能在Tomcat中得到体现，因为Tomcat 技术先进、性能稳定,而且免费，因而深受ava爱好者的喜爱并得到了部分软件开发商的认可,成为目前比较流行的Web应用服务器。
    - Tomcat服务器是一个免费的开放源代码的Web应用服务器， 属于轻量级应用服务器,
      在中小型系统和并发访问用户不是很多的场合下被昔遍使用,是开发和调试JSP程序的
      首选。对于-个Java初学web的人来说，它是最佳的选择
    - Tomcat实际上运行ISP页面和Servlet. Tomcat最新版本为9.0.*

## 3、Tomcat

### 3.1、下载安装解压

### 3.2、Tomcat启动和配置

**文件夹作用**

![img](img/1905053-20200401132448949-1949678673.png)

**启动关闭Tomcat**

![img](img/1905053-20200401132504205-570197873.png)

**访问测试http://localhost:8080/**

- 一个完整的URL地址由_协议.*主机* ,端口和文件四部分组成。
  ***超文本传输协议//本地主机(当前这台计算机) :端口号/省略的index.jsp文件***

**可能遇到的问题**

1.java环境变量没有配置--------------------Tomcat依赖于java
2.闪退问题------------------需要配置兼容性
3.乱码问题---------------------配置文件中设置

### 3.3、配置

**服务器核心配置**

![img](img/1905053-20200401132519223-199118020.png)

**可以配置启动的端口号**

Tomcat默认端口号: 8080

- ![img](img/1905053-20200401132538560-849046416.png)

MySQL:3306
http:80
https:443

**可以配置的主机的名称**

默认的主机名称：localhost--> 127.0.0.1
默认网站应用存放的位置为：webapps

![img](img/1905053-20200401132554529-1940094330.png)

**高难度面试题**：：请你谈谈网站是如何进行访问的

1. 输入一个域名:回车

2. 检查本机的C:\Windows\System32\drivers\etc\hosts配置文件下有没有这个域名映
   射

   - 有:直接返回对应ip地址，这个地址中，有我们需要访问的web程序，可以直接访问

     ![img](img/1905053-20200401132616440-474613810.png)

   - 没有：去DNS服务器找，找到的话就返回，找不到就返回找不到

3. 过程分析图

   注

   https//www.kuanstudy.com/不能访问
   有的域名需要解析到其它位置才可以访问------------例如日解析到blog 上https//blog.kuanstudy.com/可以访问

   服务器上跑的是程序

4. 可以配置下环境变量

### 3.4、发布一个web网站到Tomcat上

将自己写的网站，放到服务器(Tomcat) 指定web应用文件夹(webapps)下，就可以进
行本地访问了(远程访问)

![img](img/1905053-20200401132632250-1461097691.png)

![img](img/1905053-20200401132658926-590233255.png)

网站应该有的结构

![img](img/1905053-20200401132712831-1885405825.png)

## 4、Http

了解里面如何传输数据，如何交互

### 4.1、什么是Http

HTTP (超文本传输协议)是一个简单的请求 -响应协议，它通常运行在TCP之上

- 文本: html,字符串, ...
- 超文本:图片,音乐，视频定位,地图....
- 端口号：80

Https:安全的日

- 443

### 4.2、两个时代

**http1.0**
HTTP/1.0:客户端可以与web服务器连接后，只能获得一个web资源， 断开连接
**http2.0**
HTTP/1.1:客户端可以与web服务器连接后，可以获得多个web资源。

### 4.3、Http请求

客户端-发送请求(Request) -到-服务器

百度

> Request URL :https://www.baidu.com/ 请求地址
> Request Method:GET get方法/post方法
> status Code:200 OK 状态码: 200
> Remote (远程) Address:14.215.177.39:443

> Accept: text/htm1
> Accept - Encoding:gzip，deflate, br
> Accept-Language :zh-CN, zh;q=0.9 语言
> Cache-Contro1 :max-age=0
> Connection : keep-alive

1.请求行

请求行中的请求方式: GET

请求方式: Get, Post, HEAD,DELETE,PUT.,RAC... .

**get、post的区别**

get:请求能够携带的参数比较少。大小有限制，会在浏览器的URL地址栏显示数据内容,不安全,但高效
post:请求能够携带的参数没有限制，大小没有限制，不会在浏览器的URL地址栏显示数据内容，安全,但不高效。

2.消息头

> Accept: 告诉浏览器，它所支持的数据类型
> Accept-Encoding: 支持哪种编码格式GBK UTF-8 GB2312 IS08859-1
> Accept-Language: 告诉浏览器，它的语言环境
> Cache-Control: 缓存控制
> Connection: 告诉浏览器，请求完成是断开还是保持连接
> HOST: 主机..../.

### 4.4、Http响应

服务器--响应(Response) --客户端

百度

> Cache-Contro1 :private 缓存控制
> Connection :Keep-Alive 连接
> Content- Encoding:gzip 编码
> Content -Type :text/html 类型

1.响应体

> Accept: 告诉浏览器。它所支持的数据类型
> Accept-Encoding: 支持哪种编码格式GBKUTF-8 GB2312 IS08859-1
> Accept -Language: 告诉浏览器，它的语言环境
> Cache-Control: 缓存控制
> Connection: 告诉浏览器，请求完成是断开还是保持连接
> HOST:主..../.
> Refresh: 告诉客户端，多久刷新一次:
> Location: 让网页重新定位:

2.响应状态码

200:请求响应成功

- 200

3xx:请求重定向

- 重定向:你重新到我给你新位置去;

4xx:找不到资源404

- 404 资源不存在;

5xx:服务器代码错误

- 502 网关错误

### 常见面试题:

当你的浏览器中地址栏输入地址并回车的一-瞬间到页面能够展示回来，经历了什么?

## 5、Maven

### 5.1、Maven项目架构管理工具

我为什么要学习这个技术?

1. 在Javaweb开发中，需要使用大量的jar包，我们手动去导入
2. 如何能够让一个东西自动帮我导入和配置这个jar包。由此，Maven诞生了!

我们目前用来就是方便导入jar包的!

- 有约束，不要去违反。

Maven的核心思想:约定大于配置

Maven会规定好你该如何去编写我们的lava代码，必须要按照这个规范来;

### 5.2、下载安装Maven

下载完解压即可

### 5.3、配置环境变量

系统变量 ------> 配置

- M2_ HOME maven 目录下的bin目录
- MAVEN HOME maven的目录
- 在系统的path中配置%MAVEN_ HOME%\bin

mvn -version --------> 检查是否安装成功

### 5.4、阿里云镜像

镜像----->mirrors----->作用----->加速我们的下载
国内建议使用阿里云镜像

```xml
<mirror>
      <id>nexus-aliyun</id>
      <mirrorOf>central</mirrorOf>
      <name>Nexus aliyun</name>
      <url>http://maven.aliyun.com/nexus/content/groups/public</url> 
    </mirror>
```

在此处操作

![img](img/1905053-20200401133024319-321431787.png)

### 5.5、本地仓库

在本地的仓库，远程仓库

建立一个本地仓库存放下载的jar包

- localRepository

  ![img](img/1905053-20200401133042160-909475312.png)

### 5.6、在IDEA中使用Maven

#### 5.6.1、启动idea

#### 5.6.2、创建一个MavenWeb项目

a.使用模板创建的MavenWeb项目

![img](img/1905053-20200401133059729-994149277.png)

![img](img/1905053-20200401133118867-373956866.png)

![img](img/1905053-20200401133135634-2145933525.png)

![img](img/1905053-20200401133156706-298323858.png)

#### 5.6.3、等待项目初始化完毕

![img](img/1905053-20200401133212552-209684219.png)

![img](img/1905053-20200401133227517-2093300162.png)

#### 5.6.4、观察Maven仓库多了些什么东西

#### 5.6.5、IDEA中的Maven设置

注意IDEA项目创建成功后，看一眼Maven的配置

![img](img/1905053-20200401133245912-1378026950.png)

![img](img/1905053-20200401133304366-1748296413.png)

#### 5.6.6、到这里，Maven在IDE中的配置使用就OK了

### 5.7、(b)创建一个普通的Maven项目

![img](img/1905053-20200401133319662-907171967.png)

![img](img/1905053-20200401133333500-196968513.png)

![img](img/1905053-20200401133346177-127639612.png)

这个只有在web应用下才会有

### 5.8、IDEA标记文件夹功能

##### 第一种

![img](img/1905053-20200401133359628-1752760920.png)

##### 第二种

![img](img/1905053-20200401133413268-1142623749.png)

![img](img/1905053-20200401133427383-564813108.png)

![img](img/1905053-20200401133445371-257998139.png)

### 5.9、在IDEA中配置Tomcat

![img](img/1905053-20200401133501269-1845082443.png)

![img](img/1905053-20200401133515805-25920495.png)

![img](img/1905053-20200401133529114-1155746744.png)

![img](img/1905053-20200401133544627-121710382.png)

解决警告问题------>为什么会有这个问题，我们访问一个网站，需要指定一个文件夹的名字

![img](img/1905053-20200401133556623-799440097.png)

![img](img/1905053-20200401133612487-959468773.png)

![img](img/1905053-20200401133630310-1429667851.png)

![img](img/1905053-20200401133643430-575430232.png)

### 5.10、pom文件

pom.xml是Maven的核心配置文件

![img](img/1905053-20200401133706369-1570624038.png)

![img](img/1905053-20200401133723697-2132702962.png)

![img](img/1905053-20200401133738843-993741870.png)

一个简单的web项目

![img](img/1905053-20200401133812124-1587238257.png)

Maven由于它的约定大于配置，我们之后可能遇到我们写的配置文件，无法被导出或者生效的问题（就是例如Java代码写.xml文件，.properties文件或者其它文件时），解决方案

![img](img/1905053-20200401133834199-1859182271.png)

### 5.11、IDEA操作

jar生成目录树

![img](img/1905053-20200401133900702-588415303.png)

![img](img/1905053-20200401133915514-925307613.png)

### 5.12、解决maven项目搭建中可能遇到的一些问题

#### 5.12.1、Maven 3.6.2

![img](img/1905053-20200401133929395-2068445799.png)

降级为Maven 3.6.1

#### 5.12.2、Tomcat闪退

#### 5.12.3、IDEA中每次都要重复配置Maven

在IDEA的默认全局配置中去配置

![img](img/1905053-20200401133943291-1822148439.png)

![img](img/1905053-20200401133956220-565431497.png)

#### 5.12.4、Maven项目中Tomcat无法配置

#### 5.12.5、maven默认web项目中的web.xml版本问题

![img](img/1905053-20200401134007570-138916067.png)

#### *替换为webapp4.0版本和tomcat一致*

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">

</web-app>
```

## 6、Servlet

### *用IDEA写一 个简单的Servlet*

1.使用Maven创建一个web项目 (带模板)

2.在main文件下建java和resource文件------>然后标记文件类型

![img](img/1905053-20200401191018647-1182966520.png)

3.配置pom.xml主配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.lenovo.servlet</groupId>
  <artifactId>javaweb-maven-02</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>war</packaging>

  <name>javaweb-maven-02 Maven Webapp</name>
  <!-- FIXME change it to the project's website -->
  <url>http://www.example.com</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>1.7</maven.compiler.source>
    <maven.compiler.target>1.7</maven.compiler.target>
  </properties>

  <dependencies>
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>4.0.1</version>
    </dependency>
  
  </dependencies>

  <build>
    <finalName>javaweb-maven-02</finalName>
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <plugin>
          <artifactId>maven-clean-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <!-- see http://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_war_packaging -->
        <plugin>
          <artifactId>maven-resources-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>2.22.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-war-plugin</artifactId>
          <version>3.2.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-install-plugin</artifactId>
          <version>2.5.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-deploy-plugin</artifactId>
          <version>2.8.2</version>
        </plugin>
      </plugins>
    </pluginManagement>

    <resources>
      <resource>
        <directory>src/main/resources</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>true</filtering>
      </resource>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>true</filtering>
      </resource>
    </resources>

  </build>
</project>
```

4.书写Servlet的java类

```java
package com.lenovo.servlet;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

public class Servlet02 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //响应的类型
        response.setContentType(" text/html");
        //配置字符集
        response.setCharacterEncoding("utf-8");
        //获取响应的输入流
        PrintWriter out = response.getWriter();
        out.println("<html)");
        out.println(" <head>");
        out.println("<title>Hello World!</title>");
        out.println("</head>");
        out.println(" <body>");
        out.println("<h1>我爱Java</hl>");
        out.println("</body>");
        out.println("</html>");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

5.web.xml中注册Servlet,以及配置Servlet的mapping映射请求路径

```xml
<!DOCTYPE web-app PUBLIC
 "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN"
 "http://java.sun.com/dtd/web-app_2_3.dtd" >

<web-app>
  <display-name>Archetype Created Web Application</display-name>

  <!--web. xmL中是配置我们web的核心应用-->
  <!--注册ServLet-->
  <servlet>
    <servlet-name>helloselvlet</servlet-name>
    <servlet-class>com.lenovo.servlet.Servlet02</servlet-class>
  </servlet>
  <!--一一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>helloselvlet</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/zhuchengbo</url-pattern>
  </servlet-mapping>

</web-app>
```

6.配置Tomcat服务器并启动

Run---->Edit Configurations...---->Tomcat---->本地----->Deployment---->添加该项目

7.启动Tomcat服务器并访问映射路径

### 6.1、Servlet简介

Servlet就是sun公司开发动态web的一 门技术

Sun在这些API中提供--个接口叫做: Servlet, 如果你想开发一个Servlet程序， 只需要完成两个小步骤:

- 编写一个类,实现Servlet接口
- 把开发好的Java类部署到web服务器中。

把实现了Servlet接口的Java程序叫做，Servlet

### 6.2、HelloServlet

#### ★Serlvet接口Sun公司有两个默认的实现类: HttpServlet，GenericServlet

#### 6.2.1.构建-一个普通的Maven项目，删掉里面的src目录以后我们的学习就在这个项目里建立Moudel,这个空的工程就是Maven主工程

#### 6.2.2.关于Maven父子工程的理解:

父项目中会有子模块

```xm
<modules>
     <module>servlet01</module>
</modules>
```

子项目会有父模块

```xml
<parent>
     <artifactId> javaweb-02-servlet</artifactId>
     <groupId>com.kuang</groupId>
	<version>1.0-SNAPSHOT</version>
</parent>
```

父项目中pom文件依赖子项目可以直接使用

#### 6.2.3.Maven环境优化

1.修改web.xml为最新的

2.将maven的结构搭建完整

#### 6.2.4.编写一个Servlet程序

1.编写一个普通类
2.实现Servlet接口，
这里我们直境承 HttpServlet

- 我们写的是AVA程序,但是要通过浏览器访问，而浏览器需要连接web服务器，所以我们需要再web服务中注册我们写的Servlet,还需给他-一个浏览器能够访问的路径;

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  
  <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                        http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
           version="4.0"
           metadata-complete="true">
      <!--web. xmL中是配置我们web的核心应用-->
      <!--注册ServLet-->
      <servlet>
          <servlet-name>helloselvlet</servlet-name>
          <servlet-class>com.lenovo.servlet.Servlet03</servlet-class>
      </servlet>
      <!--一一个Servlet对应一Mapping: 映射-->
      <servlet-mapping>
          <servlet-name>helloselvlet</servlet-name>
          <!--映射的请求路径-->
          <url-pattern>/zhuchengbo</url-pattern>
      </servlet-mapping>
  
  </web-app>
  ```

#### 6.2.5.编写Servlet的映射

为什么需要映射:

我们写的是AVA程序,但是要通过浏览器访问，而浏览器需要连接web服务器,所以我们需要再web服务中注册我们写的Servlet,还需给他一个浏览器能够访问的路径;

#### 6.2.6.配置Tomcat

注意配置项目发布的路径就可以了

#### 6.2.7.启动测试

### 6.3、Servlet原理

Servlet是由web服务器调用，web服务器在收到浏览器请求后会

![img](img/1905053-20200401191049302-423578461.png)

### 6.4、Mapping问题

#### 6.4.1、一个Servlet可以指定一个映射路径

```xml
<!----个Servlet对应一Mapping: 映射-->
<servlet-mapping>
    <servlet-name>helloselvlet</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/zhuchengbo</url-pattern>
</serv1et-mapping>
```

#### 6.4.2、一个Servlet可以指定多个映射路径

```xml
<!--Servlet的请求路径-->
<!--Localhost: 8088/s1/hello/hello-->
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/he11o1</url-pattern>
</servlet-mapping>
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/he11o2</url-pattern>
</servlet-mapping>
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/he11o3</url-pattern>
</servlet-mapping>
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/he11o4</url-pattern>
</servlet-mapping>
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/he11o5</url-pattern>
</servlet-mapping>
```

#### 6.4.3、一个Servlet可以指定通用映射路径

```xml
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/he11o/*</url-pattern>
</servlet-mapping>
```

#### 6.4.4、默认的请求路径

```xml
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>/*</url-pattern>
</servlet-mapping>
```

#### 6.4.5、指定一些后缀或者前缀等等...

```xml
<!--可以自定义后级实现请求映射
注意点，* 前面不能加项目映射的路径
hello/sajdlkaida.xibei-->
<servlet-mapping>
    <servlet-name>he11o</servlet-name>
    <url-pattern>*.xibei</url-pattern>
</servlet-mapping>
```

#### 6.4.6、优先级问题

指定了固有的映射路径优先级最高,如果找不到就会走默认的处理请求;

```xml
  <!--404-->
<servlet>
        <servlet-name>error</servlet-name>
        <servlet-class>com.lenovo.servlet.ErrorServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>error</servlet-name>
        <url-pattern>/*</url-pattern>
    </servlet-mapping>
```

### 6.5、ServletContext

#### web容器在启动的时候，它会为每个web程序都创建一-个对应的ServletContext对象，它代表了当前的web应用

#### 6.5.1、实现共享数据

1.我在这个Serlet中保存的数据，可以在另外一个servlet中拿到:

```java
public class HelloServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //this. getInitParameter() 初始化参数
        //this. getServletConfig() Servlet配置
        //this. getServletContext() Servlet 上下文
        ServletContext context = this.getServletContext();
        String name = "西贝";
        context.setAttribute("name",name); //将一个 数据保存在了ServletContext中，名字为: username 。值username

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        super.doPost(req, resp);
    }
}
```

2.读取它的类

```java
public class GetServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context = this.getServletContext();
        String name = (String) context.getAttribute("name");

        resp.setContentType("text/html");
        resp.setCharacterEncoding("utf-8");
        resp.getWriter().println("名字是"+name);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

3.配置web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">
  <!--web. xmL中是配置我们web的核心应用-->
  <!--注册ServLet-->
  <servlet>
    <servlet-name>helloselvlet</servlet-name>
    <servlet-class>com.lenovo.servlet.HelloServlet</servlet-class>
  </servlet>
  <!--一一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>helloselvlet</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/zhuchengbo</url-pattern>
  </servlet-mapping>

  <servlet>
    <servlet-name>getc</servlet-name>
    <servlet-class>com.lenovo.servlet.GetServlet</servlet-class>
  </servlet>
  <!--一一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>getc</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/getc</url-pattern>
  </servlet-mapping>

</web-app>
```

4.测试访问结果

先访问/zhuchengbo再访问/getc

#### 6.5.2、获取初始化参数

1、

```java
public class ServletDemo03 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context = this.getServletContext();
        String url = context.getInitParameter("url");
        resp.getWriter().println(url);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

2、

```xml
 <!--配置一些web应用初始化参数-->
   <context-param>
       <param-name>url</param-name>
       <param-value>jdbc:mysql://localhost:3306/mybatis</param-value>
   </context-param>
  <servlet>
    <servlet-name>url</servlet-name>
    <servlet-class>com.lenovo.servlet.ServletDemo03</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>url</servlet-name>
    <url-pattern>/url</url-pattern>
  </servlet-mapping>
```

3、

![img](img/1905053-20200401191111856-1744949764.png)

#### 6.5.3、请求转发

1、

```java
public class ServletDemo04 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        ServletContext context = this.getServletContext();
        //RequestDispatcher requestDispatcher =context. getRequestDispatcher("/gp"); //转发的请求路径
        //requestDispatcher.forward(req, resp); //调用forward实现请求转发;
        context.getRequestDispatcher("/url").forward(req, resp);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

2、

```xml
<servlet>
        <servlet-name>sd1</servlet-name>
        <servlet-class>com.lenovo.servlet.ServletDemo04</servlet-class>
</servlet>
<servlet-mapping>
        <servlet-name>sd1</servlet-name>
        <url-pattern>/sd1</url-pattern>
 </servlet-mapping>
```

3、

![img](img/1905053-20200401191125687-241736205.png)

![img](img/1905053-20200401191138337-89533333.png)

#### 6.5.4、读取资源文件

##### Properties

***1.在resources目录下新建properties***

1、

![img](img/1905053-20200401191153313-1060486175.png)

2、

```java
public class ServletDemo05 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        InputStream is = this.getServletContext().getResourceAsStream("/WEB-INF/classes/db.properties");
        Properties prop = new Properties();
        prop.load(is);
        String user = prop.getProperty("username");
        String pwd = prop.getProperty("password");
        resp.getWriter().print(user + " :" + pwd);
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
```

3、

```xml
<servlet>
        <servlet-name>db</servlet-name>
        <servlet-class>com.lenovo.servlet.ServletDemo05</servlet-class>
</servlet>
<servlet-mapping>
        <servlet-name>db</servlet-name>
        <url-pattern>/db</url-pattern>
 </servlet-mapping>
```

4、

![img](img/1905053-20200401191212032-1062865025.png)

***2.在java目录下新建properties***

![img](img/1905053-20200401191224062-1471711867.png)

```java
        InputStream is = this.getServletContext().getResourceAsStream("/WEB-INF/classes/com/lenovo/servlet/aa.properties");
```

##### 发现:都被打包到了同一个路径下: classes,我们俗称这个路径为classpath: .

##### 思路:需要一个文件流;

### 6.6、HttpServletResponse

#### web服务器接收到客户端的http请求针对这个请求，分别创建一个代表请求的HttpServletRequest对象,代表响应的一个HttpServletResponse;

- 如果要获取客户端请求过来的参数找HttpServletRequest
- 如果要给客户端响应一些信息:找HttpServletResponse

#### 1、方法的一些简单分类

负责向浏览器发送数据的方法

```java
1 Servletoutputstream getoutputstream0 throws IOException;
2 Printwriter getwriter0 throws IOException;
```

负责向浏览器发送响应头的方法

```java
void setCharacterEncoding(string var1);
void setContentLength(int var1);
void setContentlengthLpng(long var1);
void setcontentType(string var1);
void setDateHeader(string var1, 1ong var2) ;
void addDateHeader(string var1, long var2) ;
void setHeader(string var1 string var2);
void addHeader(string var1，string var2);
void setIntHeader(string var1, int var2);
void addIntHeader(string var1, int var2);
```

负责设置文本的方法

```java
void setCharacterEncoding(string var1);
void setContentLength(int varl);
void setContentLengthLong(long var1);
void setContentType(string var1);
```

[响应的状态码](https://www.cnblogs.com/ZN-225/p/11008125.html)

#### 2.常见应用

##### 1.向浏览器输出消息(一直在讲，就不说了)

##### 2.下载文件

步骤

1. 要获取下载文件的路径
2. 下载的文件名是啥?
3. 设置想办法让浏览器能够支持(Content-Disposition) 下载我们需要的东西，中文文件
   名URLEncoder . encode编码,否则有可能乱码
4. .获取下载文件的输入流
5. 创建缓冲区
6. 获取0utputStream对象
7. 将FileOutputStream流写入到buffer缓中区，使用Outputstream将缓冲区中的数据
   输出到客户端!

例题

```java
public class FileServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 1.要获取下载文件的路径
        String realPath = "D:\\Project\\IdeaProject\\javaweb-01-servlet\\response\\src\\main\\resource\\西贝.jpg";
        System.out.println("下载文件的路径: " + realPath);
        // 2.下载的文件名是啥?
        String fileName = realPath.substring(realPath.lastIndexOf("\\") + 1);
        // 3.设置想办法让浏览器能够支持(Content -Disposition)下载我们需要的东西，中文文件名URLEncoder . encode编码，否则有可能乱码
        resp.setHeader("Content-Disposition", "attachment;filename=" + URLEncoder.encode(fileName, "UTF-8"));
        // 4.获取下载文件的输入流
        FileInputStream in = new FileInputStream(realPath);
        // 5.创建缓冲区
        int len = 0;
        byte[] buffer = new byte[1024];
        // 6.获取0utputStream对象
        ServletOutputStream out = resp.getOutputStream();
        // 7.将FileOutputStream流 写入到buffer缓冲区,使用Outputstream将缓冲区中的数据输出到客户端!
        while ((len = in.read(buffer)) > 0) {
            out.write(buffer, 0, len);
        }
        in.close();
        out.close();

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

##### 3.验证码功能

验证怎么来的?
●前端实现

●后端实现，需要用到Java的图片类，生产一个图片

步骤

1、

```java
public class ImageServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //如何让湖览器3秒自动刷新-次
        resp.setHeader("refresh", "3");
        //在内存中创建一个图片
        BufferedImage image = new BufferedImage(80, 20, BufferedImage.TYPE_INT_BGR);
        //得到图片
        Graphics2D g = (Graphics2D) image.getGraphics(); //笔
        //设置图片的背景颜色
        g.setColor(Color.white);
        g.fillRect(0, 0, 80, 20);
        //给图片写数据
        g.setColor(Color.BLUE);
        g.setFont(new Font(null, Font.BOLD, 20));
        g.drawString(makeNum(), 0, 20);
        //告诉沟览器，这个请求用图片的方式打开
        resp.setContentType("image/jpeg");
        //网站存在缓存，不让测览器缓存
        resp.setDateHeader("expires", -1);
        resp.setHeader("Cache-Control", "no-cache");
        resp.setHeader("Pragma", "no-cache");
        //把图片写给浏览器
        ImageIO.write(image, "jpg", resp.getOutputStream());

    }
    //.生成随机数
    private String makeNum() {
        Random random = new Random();
        String num = random.nextInt(999999) + "";
        StringBuffer sb = new StringBuffer();
        for (int i = 0; i < 7 - num.length(); i++) {
            sb.append("0");
        }
        num = sb.toString() + num;
        return num;
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

2、

```xml
<servlet>
    <servlet-name>y</servlet-name>
    <servlet-class>com.lenovo.servlet.ImageServlet</servlet-class>
  </servlet>
  <!--一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>y</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/img</url-pattern>
  </servlet-mapping>
```

3、

![img](img/1905053-20200401191246019-1042934710.png)

##### 4.实现重定向

过程

![img](img/1905053-20200401191300330-1794258695.png)

B-个web资源收到客户端A请求后，B他会通知A客户端去访问另外一个web资源C,这个
过程叫重定向

常见场景:

- 用户登录.
- void sendRedi rect(S tring var1) throws IOException;

测试

```java
public class RedirectServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        /**
         * 原理
         *  resp.setHeader("Location","/response/img");
         *  resp.setStatus(302);
         */
      resp.sendRedirect("/response/img");
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
<servlet>
    <servlet-name>redirect</servlet-name>
    <servlet-class>com.lenovo.servlet.RedirectServlet</servlet-class>
  </servlet>
  <!--一一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>redirect</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/red</url-pattern>
  </servlet-mapping>
```

面试题:请你聊聊重定向和转发的区别?
相同点

- 页面都会实现跳转

不同点

- 请求转发的时候，url不会产生变化;----307
- 重定向时候，url地址栏会发生变化;----302

### 6.7、HttpServletRequest

#### Request测试

1、

```jsp
<html>
<body>
<h2>Hello World!</h2>
<%--这里提交的路径，需要寻找到项目的路径--%>
<%--${pageContext. request. contextPath}代表当前的项目--%>
<form action=" ${pageContext.request.contextPath}/login" method="get">
    用户名: <input type="text" name="username"> <br>
    密码: <input type="password" name="password"> <br>
    <input type="submit">
</form>
</body>
</html>
```

2、

```java
public class RequestTest extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //处理请求
        String username = req . getParameter("username");
        String password = req. getParameter( "password");
        System. out. println(username+" : "+password);
       //重定向时候一定要注意。路径问题。否则404:
        resp. sendRedirect( "/response/success.jsp");

    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

3、

```xml
<servlet>
    <servlet-name>request</servlet-name>
    <servlet-class>com.lenovo.servlet.RequestTest</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>request</servlet-name>
    <url-pattern>/login</url-pattern>
  </servlet-mapping>
```

4、success.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>success</h1>
</body>
</html>
```

#### 获取参数，请求转发

##### 登录实例

###### 1、index.jsp

```jsp
<html>
<body>
<h2>登录</h2>
<div style="text-align: center">
<%--  这里表单表示的意思：以post方式提交表单，提交到我们的Login请求  --%>
    <form action="${pageContext.request.contextPath}/login" method="post">
        用户名：<input type="text" name="username"><br>
        密码：<input type="password" name="password"><br>
        爱好：
        <input type="checkbox" name="hobbys" value="代码">
        <input type="checkbox" name="hobbys" value="java">
        <input type="checkbox" name="hobbys" value="唱歌">
        <input type="checkbox" name="hobbys" value="跳舞">
        <input type="checkbox" name="hobbys" value="电影">
        <br>
        <input type="submit">
    </form>
</div>

</body>
</html>
```

###### 2、LoginServlet

```java
public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doPost(req, resp);
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        resp.setCharacterEncoding("utf-8");
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String[] hobbys = req.getParameterValues("hobbys");
        System.out.println("=========================");
        //后台接收中文乱码问题
        System.out.println(username);
        System.out.println(password);
        System.out.println(Arrays.toString(hobbys));
        System.out.println("========================");
        System.out.println(req.getContextPath());
        //通过请求转发
        //这里的 / 代表当前的web应用
        req.getRequestDispatcher("/success.jsp").forward(req, resp);

    }
}
```

###### 3、web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>

<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">

  <servlet>
    <servlet-name>request</servlet-name>
    <servlet-class>com.lenovo.servlet.LoginServlet</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>request</servlet-name>
    <url-pattern>/login</url-pattern>
  </servlet-mapping>
</web-app>
```

###### 4.success.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>登录成功</h1>
</body>
</html>
```

## 7、Cookie、 Session

### 7.1、会话

会话:用户打开一个浏览器，点击了很多超链接,访问多个web资源，关闭浏览器,这个过程可以称之为会话

有状态会话:个同学来过教室，下次再来教室， 我们会知道这个同学,曾经来过

#### 你能怎么证明你是学校的学生?

- 你 学校
- 1.发票 学校 给你发票
- 2.学校的登记 学校 标记你来过了

#### 一个网站，怎么证明你来过?

客户端 服务器

> 1.服务端给客户端一个信件 客户端下次访问服务端芾上信件就可以了; cookie
> 2.服务器登记你来过了，下次你来的时候我来匹配你; seesion

### 7.2、 保存会话的两种技术 。

#### cookie

●客户端技术 (响应,请求)

#### session

●服务器技术利用这个技术，可以保存用户的会话信息?我们可以把信息或者数据放在Session中.
常见:网站登录之后，你下次不用再登录了，第二次访问直接就上去了!

### 7.3、Cookie

#### 7.3.1、从请求中拿到cookie信息

#### 7.3.2、服务器响应给客户端cookie

```java
Cookie[] cookies = req. getcookiesO); //获得Cookie
cookie. getName(; //获得cookie中的key
cookie. getvalue(); //获得cookie中的vlaue
new Cookie("lastLoginTime", System. currentTimeMillisO+""); //新建一个cookie
cookie. setMaxAge(24*60*60); //设置cookie的有 效期
resp. addcookie(cookie); //响应给客户端 - -个cookie
```

#### 7.3.3、cookie: 一般会保存在本地的用户目录下appdata;

#### 7.3.4、一个网站cookie是否存在上限!聊聊细节问题

- 一个Cookie只能保存一个信息:
- 一个web站点可以给浏览器发送多 个cookie.最多存放20个cookie
- Cookie大小有限制4kb;
- 浏览器 上限300个cookie

#### 7.3.5、删除Cookie;

- 不没置有效期，关闭浏览器，自动失效
- 设置有效期时间为0;

#### 7.3.6、编码解码:

```java
URLEncoder.encode("西贝","utf-8")
URL Decoder.decode(cookie.getvalue(),"UTF-8")
```

#### 例题:

##### 1、cookie的缓存

```java
//保存用户上一次访问的时间
public class CookieDome01 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //服务器，告诉你，你来的时间，把这个时间封装成为一个信件，你下带来，我就知道你来了
        //解决中文乱码
        req.setCharacterEncoding("utf-8");
        resp.setContentType("text/html;charset=utf-8");
        resp.setCharacterEncoding("utf-8");
        PrintWriter out = resp.getWriter();
        //Cookie,服务器端从客户端获取呀:
        Cookie[] cookies = req.getCookies(); //这里返回数组，说明Cookie 可能存在多个

        //为Cookie是否存在
        if (cookies != null) {
            //如果存在怎么办
            out.write("你上一次访 问的时间是:");
            for (int i = 0; i < cookies.length; i++) {
                Cookie cookie = cookies[i];
                //获取cookie的名字
                if (cookie.getName().equals("lastLoginTime")) {
                    //获取cookie中的值
                    long lastLoginTime = Long.parseLong(cookie.getValue());
                    Date date = new Date(lastLoginTime);
                    out.write(date.toLocaleString());
                }
            }
        } else {
            out.write("这是您第一次访问本站");
        }
        //服务给客户端响应一rcookie;
        Cookie cookie = new Cookie("lastLoginTime", System.currentTimeMillis() + "");
        //cookie有效期为1天
        cookie.setMaxAge(24 * 60 * 60);
        resp.addCookie(cookie);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws
            ServletException, IOException {
        doGet(req, resp);
    }
}
```

##### 2、删除Cookie;

```java
public class CookieDome02 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //创建一个cookie.名字必须要 和要删除的名字-致
        Cookie cookie = new Cookie("lastLoginTime", System.currentTimeMillis() + "");
        //将cookie有效期设置为，立马过期
        cookie.setMaxAge(0);
        resp.addCookie(cookie);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws
            ServletException, IOException {
        doGet(req, resp);
    }
}
```

##### 3、编码解码:

```java
public class CookieDome03 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //解决中文码
        req.setCharacterEncoding("utf-8");
        resp.setContentType("text/html;charset=utf-8");
        resp.setCharacterEncoding("utf-8");
        //Cookie,服务器端从客户端获取呀:
        Cookie[] cookies = req.getCookies(); //这里返回数组。说明cookie可能存在多 个
        PrintWriter out = resp.getWriter();
        //判断iCookie是否存在
        if (cookies != null) {
            //如果存在怎么办
            out.write("你上一次访问的时间是:");
            for (int i = 0; i < cookies.length; i++) {
                Cookie cookie = cookies[i];
                System.out.println("111111111111");
                //获取cookie的名字
                if (cookie.getName().equals("name")) {
                    System.out.println("2222222222222222");
                    System.out.println(cookie.getValue());
                    //解码
                    //out.write(URLDecoder.decode(cookie.getValue(), "UTF-8"));
                    out.write(cookie.getValue());
                }
            }
        } else {
            out.write("这是您第一次访问本站");
            //编码
            Cookie cookie = new Cookie("name", URLEncoder.encode("西贝", "utf-8"));
            resp.addCookie(cookie);
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

### 7.4、 Session（重点）

#### 7.4.1、什么是Session:

- 服务器会给每-个用户浏览器)创建一个Session对象;
- 一个Session独占y一个浏览器，只要浏览器没有关闭，这个Session就存在:
- 用户登录之后，整个网站它都可以访问! -->保存用户的信息;保存购物车的信息..

#### 7.4.2、Session和cookie的区别:

- Cookie是把用户的数据写给用户的浏览器,浏览器保存(可以保存多个)
- Session把用户的数据写到用户独占Session中服务器端保存(保存重要的信息，减少服务器资源的浪费)
- Session对象由服务创建;

#### 7.4.3、使用场景:

- 保存一个登录用户的信息;
- 购物车信息;.
- 在整个网站中经常会使用的数据，我们将它保存在Session中;

#### 7.4.4、session使用

##### 1、获取session以及session的一些方法

```java
public class SessionDome01 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //解决乱码问题
        req.setCharacterEncoding("UTF-8");
        resp.setCharacterEncoding("UTF-8");
        resp.setContentType("text/html; charset=utf-8");
        //得到Session
        HttpSession session = req.getSession();
        //给Session中存东西
        session.setAttribute("name", "西贝");
        //获取Session的ID
        String sessionId = session.getId();
        //判断Session是不是新创建
        if (session.isNew()) {
            resp.getWriter().write("session创建成功, ID: " + sessionId);
        } else {
            resp.getWriter().write("session以及在服务器中存在了,ID:" + sessionId);
        }
        //Session 创建的时候做了什么事情:
        //Cookie cookie = new Cookie("JSESSIONID", sessionId);
        //resp. addCookie(cookie);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

##### 2、

```java
public class SessionDome02 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //解决乱码问题
        req.setCharacterEncoding("UTF-8");
        resp.setCharacterEncoding("UTF-8");
        resp.setContentType("text/html; charset=utf-8");
       //得到Session
        HttpSession session = req.getSession();
        String name = (String) session.getAttribute("name");
        System.out.println(name);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

##### 3、手动设置session失效

```java
public class SessionDome03 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        HttpSession session = req. getSession();
        session. removeAttribute( "name" ) ;
        //手动设置失效
        session.invalidate();

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req,resp);
    }
}
```

#### 7.4.5、会话自动过期，web.xml中设置

```xml
<!--设置Session默认的失效时间-->
    <session-config>
        <!--15 分钟后Session自动失效。以分钟为单位-->
        <session-timeout>1</session-timeout>
    </session-config>
```

#### 7.4.6、流程图

##### session

![img](img/1905053-20200401191332688-1670337895.png)

##### cookie

![img](img/1905053-20200401191344583-1160928363.png)

##### ServletContext

![img](img/1905053-20200401191356013-2118423809.png)

## 8、JSP

### 8.1、什么是JSP

Java Server Pages : Java服务器端页面， 也和Servlet- 样,用于动态Web技术! .
最大的特点:
●写JSP就像在写HTML
●区别:
。HTML只给用户提供静态的数据
。JSP页面中可以嵌入AVA代码，为用户提供动态数据;

### 8.2、JSP原理

思路: JSP到底怎么执行的!|

- 代码层面没有任何问题

- 服务器内部工作
  tomcat中有一个work目录;
  IDEA中使用Tomcat的会在IDEA的tomcat中生产一个work目录

  ![img](img/1905053-20200401191506303-1269865000.png)

发现页面转变成了Java程序!

![img](img/1905053-20200401191642687-1329835989.png)

**浏览器向服务器发送请求，不管访问什么资源，其实都是在访问Servlet!**
JSP最终也会被转换成为一个Java类!
**JSP本质上就是一个Servlet**

```java
//初始化
public void._jspInit(){    
}
//销毁
public void._jspDestroy(){
}
//JSPService
public void.jspService(. HttpServletRequest request ，HttpServletResponse response){}
```

1.判断请求
2.内置一些对象

```java
final javax.servlet.jsp.PageContext pageContext; //页面上下文
javax.serv1et.http.HttpSession session = nu11;
//session
final javax.serv1et.ServletContext application; / /applicati onContext
fina1 javax.servlet.ServletConfig config;
//config
javax.servlet.jsp.Jspwriter out = nu11;
//out
final java.lang.object page = this;
//page:当前
HttpServletRequest request
//请求
HttpServ1etResponse response
//响应
```

3.输出页面前增加的代码

```java
response.setContentType ("text/htm1");
//设置响应的页面类型
pageContext = _jspxFactory.getPageContext(this,request，response,nu11，true, 8192，true) ;
_jspx_page_ context = pageContext;
application = pageContext.getserv1etContextO;
config = pageContext.getServ1etConfigO;
session = pageContext.getSessionO;
out = pageContext.getoutO;
_jspx_ _out = out;
```

4.以上的这些个对象我们可以在JSP页面中直接使用!

![img](img/1905053-20200401191701288-1431264777.png)

在JSP页面中; .
只要是JAVA代码就会原封不动的输出;
如果是HTML代码，就会被转换为:

```java
out.write ("<htm1>\r\n");
```

这样的格式，输出到前端

![img](img/1905053-20200401191834853-1710046387.png)

### 8.3、JSP基础语法

任何语言都有自己的语法，JAVA中有。JSP 作为java技术的一种应用，它拥有一些自己扩充的语法(了解,知道
即可! )，Java所有语法都支持!

**JSP表达式**

```JSP
<%--JSP表达式
作用:用来将程序的输出，输出到客户端
<%=变量或者表达式%>
--%>
<%=new java.util.Date()%>
```

**jsp脚本片段**

```jsp
<%--jsp脚本片段--%>
<%
int sum = 0;
for(inti=1;i<=100;i++){
sum+=i;
}
out.print1n("<h1>Sum="+sum+"</h1>");
%>
```

**JSP声明**

```jsp
<%!
static{
System.out.println("Loading Servlet!");
}
private int g1obalvar = 0;
public void kuang(){
System.out.print1n("进入了方法Kuang! ");
}
%>
```

JSP声明:会被编译JSP生成ava的类中!其他的，就会被生成到jspService方法中!
在JSP，嵌入ava代码即可!

```jsp
<%%>
<%=%>
<%!%>
<%--注释--%>
```

JSP的注释,在客户端打开时不会在客户端显示，HTML就会!

### 8.4、JSP指令

```jsp
<%@page args.... %>
<%@include file=""%>
<%--@include会将两个页面合二为---%>
<%@include file="common/header.jsp"%>
<h1>网页主体</hl>
<%@include file="common/footer.jsp"%>
<hr>

<%--jSP标签
jsp:include:拼接页面，本质还是三个
<jsp:include page="/common/header.jsp"/>
<h1>网页主体</hl>
<jsp:include page="/common/footer.jsp"/>
```

***可定制错误页面（404,500）以及公共页面***

### 8.5、九大内置对象和四大作用域

### 8.5.1、四大作用域

> page域:只能在当前jsp页面使用(当前页面)
> request域:只能在同一个请求中使用(转发)
> session域:只能在同一个会话(session对象)中使用(私有 的)
> context域:只能在同一个web应用中使用(全局的)

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<%--内置对象--%>
<%
    pageContext.setAttribute("name1", "秦疆1号"); //保存的数据只在一个页面中有效
    request.setAttribute("name2", "秦疆2号"); //保存的数据只在一次请求中有效，请求转发会携带这个数据
    session.setAttribute("name3", "秦疆3号"); //保存的数据只在一次会话中有效，从打开浏览器到关闭浏览器
    application.setAttribute("name4", "秦疆4号"); // 保存的数据只在服务器中有效。从打开服务器到关闭服务器
%>
<%--脚本片段中的代码。会被原封不动生成到。JSP.java
要求:这里面的代码:必须保证Java语法的正确性--%>
//从pageContext取出，我们通过寻找的方式来
//从起层到高层(作用城) : page->request-->session-->application
<%
    String name1 = (String) pageContext.findAttribute("name1");
    String name2 = (String) pageContext.findAttribute("name2");
    String name3 = (String) pageContext.findAttribute("name3");
    String name4 = (String) pageContext.findAttribute("name4");
    String name5 = (String) pageContext.findAttribute("name5"); // 不存在
%>
<%--使EL表达式输出${} --%>
<h1>取出的值为: </h1>
<h3>${name1}</h3>
<h3>${name2}</h3>
<h3>${name3}</h3>
<h3>${name4}</h3>
<h3><%=name5%>
</h3>
</body>
</html>
```

page:

request:客户端向服务器发送请求，产生的数据，用户看完就没用了，比如:新闻，用户看完没用的.

session:客户端向服务器发送请求，产生的数据，用户用完一会还有用， 比如:购物车;

application:客户端向服务器发送请求，产生的数据, -个用户用完了，其他用户还可能使用,比如:聊天数
据;

### 8.5.1、九大内置对象

> 内置对象名 类型
> request HttpServletRequest
> response HttpServletResponse
> config ServletConfig
> application ServletContext
> session HttpSession
> exception Throwable
> page object(this)
> out JspWriter
> pageContext PageContext

### 8.6、JSP标签、JSTL标签、EL表达式

#### 8.6.1、JSP标签

往上翻

#### 8.6.2、JSTL标签

1. 相关依赖

   ```xml
    <!--JSTL的依赖-->
           <dependency>
               <groupId>javax.servlet</groupId>
               <artifactId>jstl</artifactId>
               <version>1.2</version>
           </dependency>
           <!-- standard标签库-->
           <dependency>
               <groupId>taglibs</groupId>
               <artifactId>standard</artifactId>
               <version>1.1.2</version>
           </dependency>
   ```

   1. JSTL表达式

      JSTL标签库的使用就是为了弥补HTML标签的不足;它自定义许多标签,可以供我们使用，标签的功能和java代码一样!

      - 格式化标签

      - SQL标签

      - XML标签

      - **核心标签**(掌握部分)

        ![img](img/1905053-20200401191858341-669934799.png)

   1 实例演示<c:if>

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h4>if测试</h4>
<hr>
<form action="coreif.jsp" method="get">
    <%--
    EL表达式获取表单中的数据
    ${param.参数名
    --%>
    <input type="text" name="username" value="${param. username}" >
    <input type=" submit" value="登录" >
</form>
<%--判断如果提交的用户名是管理员。则登录成功--%>
<c:if test="${param. username=='admin'}" var="isAdmin">
    8 <c:out value="管理员欢迎您! "/>
</c:if>
<c:out value="${isAdmin}"/>
</body>
</html>
```

2实例演示<c:choose>

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
         pageEncoding="UTF-8"%>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
    <title>c:choose 标签实例</title>
</head>
<body>
<c:set var="salary" scope="session" value="${2000*2}"/>
<p>你的工资为 : <c:out value="${salary}"/></p>
<c:choose>
    <c:when test="${salary <= 0}">
        太惨了。
    </c:when>
    <c:when test="${salary > 1000}">
        不错的薪水，还能生活。
    </c:when>
    <c:otherwise>
        什么都没有。
    </c:otherwise>
</c:choose>
</body>
</html>
```

运行结果如下：

```
你的工资为 : 4000

不错的薪水，还能生活。
```

3.实例演示<c:forEach>

```jsp
<%@ page import="java.util.ArrayList" %>
<%@ page language="java" contentType="text/html; charset=UTF-8"
         pageEncoding="UTF-8" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<html>
<head>
    <title>c:forEach 标签实例</title>
</head>
<body>
<%
    ArrayList<String> people = new ArrayList<>();
    people.add(0, "张三");
    people.add(1, "李四");
    people.add(2, "王五");
    people.add(3, "赵六");
    people.add(4, "田七");
    request.setAttribute("list", people);
%>
<%--
var，每一一次遍历出米的变量
items，要遍历的对象
begin,哪里开始
end,到哪里
step,步长
--%>
<c:forEach var="people" items="${list}">
<c:out value="${people}"/> <br>
</c:forEach>
<hr>
<c:forEach var="people" items="${list}" begin="1" end="3" step="1">
<c:out value="${people}"/> <br>
</c:forEach>
</body>
</html>
```

运行结果如下：

![img](img/1905053-20200401191916831-58716949.png)

1. JSTL标签库使用步骤

- 引用核心标签库taglib

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

- 使用其中的方法
- 在Tomcat也需要引入jstl的包，否则会报错: JSTL解析错误 (需手动导包至lib目录下)500错误

#### 8.6.3、EL表达式

EL表达式: ${}作用：

- 获取数据
- 执行运算
- 获取web开发的常用对象

## 9、JavaBean

### 实体类

JavaBean有特定的写法:

- 必须要有一个无参构造
- 属性必须私有化
- 必须有对应的get/set方法;

一般用来和数据库的字段做映射ORM;
ORM:对象关系映射

- 表-->类
- 字段-->属性
- 行记--->对象

| 序号 | name | age  | address |
| ---- | ---- | ---- | ------- |
| 1    | 鸣人 | 12   | 木叶    |
| 2    | 佐助 | 13   | 木叶    |
| 3    | 雏田 | 14   | 木叶    |

```java
class Peop1e {
    private int id;
    private string name;
    private int id;
    private string address;
}

class A {
	new Peop1e(1,"鸣人",12,"木叶");
	new Peop1e(2,"佐助",13,"木叶");
	new Peop1e(3,"雏田",14,"木叶");
}
```

## 10、 MVC三层架构

什么是MVC: Model view Controller模型、视图、控制器

Controller层：接受用户参数，调用业务层，转发视图

业务层;主要处理对应业务

持久层：增删改查的事

前端：展示页面

### 10.1、早些年

![img](img/1905053-20200401191958674-2043966334.png)

用户直接访问控制层，控制层就可以直接操作数据库;

> servlet--CRUD-->数据库
> 弊端:程序十分臃肿，不利于维护
> servlet的代码中:处理请求、响应、视图跳转、处理JDBC、处理业务代码、处理逻辑代码
> 架构:没有什么是加一层解决不了的!
>
> 程序猿调用
> JDBC
> Mysql oracle sqlServer...

### 10.2、MVC三层架构

![img](img/1905053-20200401192014714-1738932149.png)

Model

- 业务处理:业务逻辑(Service)
- 数据持久层: CRUD (Dao)

View

- 展示数据
- 提供链接发起Servlet请求(a, form, img..)

Controller (Servlet)

- 接收用户的请求: (req: 请求参数、Session信息...
- 交给业务层处理对应的代码
- 控制视图的跳转

> 登录--->接收用户的登录请求--->处理用户的请求(获取用户登录的参数，username, password) ----> 交
> 给业务层处理登录业务(判断用户名密码是否正确:事务) --->Dap层查询用户名和密码是否正确-->数据库

## 11、过滤器(Filter)(重点)

### 11.1、Filter:过滤器，用来过滤网站的数据;

●处理中文乱码
●登录验证

![img](img/1905053-20200401192033217-586274667.png)

***Filter开发步骤:***

**1.导包**

```xml
  <!--servlet的依赖-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>4.0.1</version>
        </dependency>
        <!--jsp的依赖-->
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>javax.servlet.jsp-api</artifactId>
            <version>2.3.3</version>
            <scope>provided</scope>
        </dependency>
        <!--JSTL的依赖-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
        <!-- standard标签库-->
        <dependency>
            <groupId>taglibs</groupId>
            <artifactId>standard</artifactId>
            <version>1.1.2</version>
        </dependency>
        <!--连接数据库-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.17</version>
        </dependency>
    </dependencies>
```

**2.编写过滤器**

1. 导包不要错

![img](img/1905053-20200401192049589-1234101975.png)

1. 实现Filter接口，重写对应的方法即可

```java
public class CharacterEncodingFilter implements Filter {
    //初始化：web服务器启动。就以及初始化了随时等待过滤对象出现!
    public void init(FilterConfig filterConfig) throws ServletException {
        System.out.println("CharacterEncodingFilter创建");
    }

    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        servletRequest.setCharacterEncoding("utf-8");
        servletResponse.setCharacterEncoding("utf-8");
        servletResponse.setContentType("text/html;charset=UTF-8");

        System.out.println("CharacterEncodingFilter执行前...");
        filterChain.doFilter(servletRequest, servletResponse); // 让:我们的请求继续走，如果不写，程序到这里就被拦藏停止: !(固定格式)
        System.out.println("CharacterEncodingFilter执行后....");

    }

    //销毁：web服务器关闭的时候，过滤会销毁
    public void destroy() {
        System.out.println("CharacterEncodingFilter销毁");
    }
}
```

1. 在web.xml中配置Fiter

```xml
 <!--web. xmL中是配置我们web的核心应用-->
    <!--注册ServLet-->
    <servlet>
        <servlet-name>Servlet</servlet-name>
        <servlet-class>com.lenovo.filter.Servlet</servlet-class>
    </servlet>
    <!--一一个Servlet对应一Mapping: 映射-->
    <servlet-mapping>
        <servlet-name>Servlet</servlet-name>
        <!--映射的请求路径-->
        <url-pattern>/servlet/show</url-pattern>
    </servlet-mapping>
    <servlet-mapping>
        <servlet-name>Servlet</servlet-name>
        <!--映射的请求路径-->
        <url-pattern>/show</url-pattern>
    </servlet-mapping>

    <filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>com.lenovo.filter.CharacterEncodingFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>CharacterEncodingFilter</filter-name>
        <!--只要是/servlet的任何请求。会经过这个过滤器-->
        <url-pattern>/servlet/*</url-pattern>
        <!--<url -pattern>/*</url-pattern>-->
    </filter-mapping>
```

1. 编写一个Servlet类可以发现

   ```java
   public class Servlet extends HttpServlet {
       @Override
       protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
   //       req.setCharacterEncoding("utf-8");
   //       resp.setCharacterEncoding("utf-8");
   //       resp.setContentType("text/html;charset=UTF-8");
           resp.getWriter().println("你好，世界");
       }
   
       @Override
       protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
           doGet(req, resp);
       }
   }
   ```

   1. 可以观察到过滤器筛选了哪些路径可通过过滤器

      ![img](img/1905053-20200401192110633-1078153409.png)

![img](img/1905053-20200401192122090-656553154.png)

## 12、监听器（listener）

实现一个监听器的接口; (有N种)

### 12.1、session监听器

1. 编写一个监听器
   实现监听器的接口.

```java
//统计网站在线人数:统计session
public class listener implements HttpSessionListener {
    //创建session监听:看你的一举一动
    //一旦创建Session就会触发一次这 个事件!
    public void sessionCreated(HttpSessionEvent se) {
        ServletContext ctx = se.getSession().getServletContext();
        System.out.println(se.getSession().getId());

        Integer onlineCount = (Integer) ctx.getAttribute("OnlineCount");
        if (onlineCount == null) {
            onlineCount = new Integer(1);
        } else {
            int count = onlineCount.intValue();
            onlineCount = new Integer(count + 1);
        }
        ctx.setAttribute("OnlineCount", onlineCount);
    }

    //销毁session监听
    //一旦销毁Session就会触发一次这个事件!
    public void sessionDestroyed(HttpSessionEvent se) {
        ServletContext ctx = se.getSession().getServletContext();
        Integer onlineCount = (Integer) ctx.getAttribute("OnlineCount");
        if (onlineCount == null) {
            onlineCount = new Integer(0);
        } else {
            int count = onlineCount.intValue();
            onlineCount = new Integer(count - 1);
        }
        ctx.setAttribute("OnlineCount", onlineCount);
    }
    /*Session销毁:
        1.手动销毁
        getSession(). invalidate();
        2.自动销毁*/
}
```

1. web.xml中注册监听器

```xml
<!--注册监听器-->
    <listener>
        <listener-class>com.lenovo.filter.listener</listener-class>
    </listener>
    <!--设置session过期时间-->
    <session-config>
        <session-timeout>1</session-timeout>
    </session-config>
```

1. 看情况是否使用!

   ```jsp
   <%@ page contentType="text/html;charset=UTF-8" language="java" %>
   <html>
     <head>
       <title>$Title$</title>
     </head>
     <body>
     <h1>当前有<span><%=this.getServletConfig().getServletContext().getAttribute("OnlineCount")%></span>人在线</h1>
     </body>
   </html>
   ```

   1. ![img](img/1905053-20200401192144851-141558961.png)

### 12.2、键盘监听器

### 12.3、窗口监听器

## 13、过滤器、监听器常见应用

### 13.1、监听器

#### 13.1.1、CUI编程（图形界面编程）游戏等

1. 监听器: GUI编程中经常使用;

```java
public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame("中秋节快乐"); //新建一 一个窗体
        Panel panel = new Panel(null); //面板
        frame.setLayout(null); //设置窗体的布局
        frame.setBounds(300, 300, 500, 500);
        frame.setBackground(new Color(8, 8, 255)); //设置背景颜色
        panel.setBounds(50, 50, 300, 300);
        panel.setBackground(new Color(0, 255, 0)); //设置背景颜色
        frame.add(panel);
        frame.setVisible(true);
        //监听事件，监听关闭事件
        frame.addWindowListener(new WindowListener() {
            public void windowOpened(WindowEvent e) {
                System.out.println("打开");
            }
            public void windowClosing(WindowEvent e) {
                System.out.println("关闭ing");
                System.exit(0);
            }
            public void windowClosed(WindowEvent e) {
                System.out.println("关闭ed");
            }
            public void windowIconified(WindowEvent e) {
            }
            public void windowDeiconified(WindowEvent e) {
            }
            public void windowActivated(WindowEvent e) {
                System.out.println("激活");
            }
            public void windowDeactivated(WindowEvent e) {
                System.out.println("未激活");
            }
        });

    }
}
```

1. 当必须重写方法过多，而且用不到时，可以new其子类，这样就可以选择自己需要用的方法重写

```java
public class TestPanel {
    public static void main(String[] args) {
        Frame frame = new Frame("中秋节快乐"); //新建一 一个窗体
        Panel panel = new Panel(null); //面板
        frame.setLayout(null); //设置窗体的布局
        frame.setBounds(300, 300, 500, 500);
        frame.setBackground(new Color(8, 8, 255)); //设置背景颜色
        panel.setBounds(50, 50, 300, 300);
        panel.setBackground(new Color(0, 255, 0)); //设置背景颜色
        frame.add(panel);
        frame.setVisible(true);
        //监听事件，监听关闭事件
        frame.addWindowListener(new WindowAdapter() {
            @Override
            public void windowClosing(WindowEvent e) {
                System.exit(0);
            }
        });

    }
```

1. 结果相同

![img](img/1905053-20200401192212836-514089742.png)

#### 13.1.2、统计在线人数（往上看）

### 13.2、过滤器

#### 13.2.1、用户登录拦截

用户登录之后才能进入主页!用户注销后就不能进入主页了!(即不能直接访问http://localhost:8080/sys/success.jsp，需要先登录才可以，否则直接跳到http://localhost:8080/error.jsp)
1.用户登录之后，向Sesison中放入用户的数据
2.进入主页的时候要判断用户是否已经登录;没有登录过则返回登录页面。

要求:在过滤器中实现!

1. Login.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>登录</h1>
<form action="/servlet/login" method="post">
    用户名：<input type="text" name="username">
    <input type="submit">
</form>

</body>
</html>
```

1. web.xml

```xml
 <servlet>
        <servlet-name>LoginServlet</servlet-name>
        <servlet-class>com.lenovo.servlet.LoginServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>LoginServlet</servlet-name>
        <url-pattern>/servlet/login</url-pattern>
    </servlet-mapping>
    
    <servlet>
        <servlet-name>LogoutServlet</servlet-name>
        <servlet-class>com.lenovo.servlet.LogoutServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>LogoutServlet</servlet-name>
        <url-pattern>/servlet/logout</url-pattern>
    </servlet-mapping>
    <filter>
        <filter-name>SysFilter</filter-name>
        <filter-class>com.lenovo.filter.SysFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>SysFilter</filter-name>
        <url-pattern>/sys/*</url-pattern>
    </filter-mapping>
```

1. Constan

```java
public class Constant {
    public final static String USER_SESSION	="USER_SESSION";
}
```

1. LoginServle

```java
public class LoginServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取前端清求的参数
        String username = req.getParameter( "username");
        if (username. equals("admin")){ // 登录成功
            req.getSession().setAttribute(Constant.USER_SESSION, req.getSession().getId());
            resp.sendRedirect("/sys/success.jsp");
        }else { //登录失败
            resp.sendRedirect("/error.jsp");
        }
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

1. success.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java"%>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>主页</h1>
<p><a href="/servlet/logout">注销</a></p>

</body>
</html>
```

1. error.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>错误</h1>
<h3>没有权限，用户名错误</h3>
<a href="/Login.jsp">返回登录页面</a>

</body>
</html>
```

1. LogoutServlet

```xml
public class LogoutServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        Object user_session = req.getSession().getAttribute("USER_SESSION");
        if (user_session != null) {
            req.getSession().removeAttribute("USER_SESSION");
            resp.sendRedirect("/Login.jsp");
        }
    }
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

1. SysFilter

```java
public class SysFilter implements Filter {
    public void init(FilterConfig filterConfig) throws ServletException {

    }
    public void doFilter(ServletRequest req, ServletResponse resp, FilterChain chain) throws IOException, ServletException {
        //IServLetRequest HttpServLetRequest
        HttpServletRequest request = (HttpServletRequest) req;
        HttpServletResponse response = (HttpServletResponse) resp;
        if (request.getSession().getAttribute(Constant.USER_SESSION)==null){
            response.sendRedirect("/error.jsp");
        }
        chain.doFilter(request, response);

    }

    public void destroy() {

    }
}
```

项目结构

![img](img/1905053-20200401192235669-1279303505.png)

#### 13.2.2、字符乱码问题（往上看）

## 14、JDBC

### 14.1、什么是JDBC，Java连接数据库

![img](img/1905053-20200401192325423-198485620.png)

需要jar包的支持:
●java.sql
●javax.sql
●mysql-connector-java... 连接驱动(必须要导入)

### 14.2、实验环境搭建(步骤)

#### 14.2.1、通过Navicat/SQLyog或者直接用MySQL建立数据库（jdbc）、数据表

![img](img/1905053-20200401192342756-554266664.png)

#### 14.2.2、导入连接数据库依赖

```xml
 <!--连接数据库-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.17</version>
        </dependency>
```

#### 14.2.3、使用IDEA连接MySQL数据库

![img](img/1905053-20200401192358475-830300081.png)

![img](img/1905053-20200401192411838-1141207083.png)

![img](img/1905053-20200401192430258-892479804.png)

#### 14.2.4、JDBC固定步骤:

1.加载驱动
2.连接数据库,代表数据库
3.向数据库发送SQL的对象Statement : CRUD
I4.编写SQL (根据业务，不同的SQL)
5.执行SQL
6.关闭连接

```java
//配置信息
    //url地址："jdbc:mysql://localhost:3306
    //数据库名称:jdbc
    //useUnicode=true&characterEncoding=utf-8解决中文乱码
    public static void main(String[] args) throws ClassNotFoundException, SQLException {
        String url = "jdbc:mysql://localhost:3306/jdbc?useUnicode=true&characterEncoding=utf-8";
        String username = "root";
        String password = "981204";
        //1.加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.连接数据库。代表数据库
        Connection connection = DriverManager.getConnection(url, username, password);
        //3.向数据库发送SQL的对象Statement : CRUD
        Statement statement = connection.createStatement();
        //4.编写SQL
        String sql = "select * from users";
        //5.执行查询SQL.返回一个 ResultSet :结果集
        ResultSet rs = statement.executeQuery(sql);
        while (rs.next()) {
            System.out.println("id=" + rs.getObject("id"));
            System.out.println("id=" + rs.getObject("name"));
            System.out.println("id=" + rs.getObject("password"));
            System.out.println("id=" + rs.getObject("email"));
            System.out.println("id=" + rs.getObject("birthday"));
        }
        //6.关闭连接：释放资源(一定要做)先开后关
        rs.close();
        statement.close();
        connection.close();

    }
String sql = "delete from users where id=4";
//受影响的行数i，增删改都是用executeUpdate即可
//int i = statement . executeUpdate(sql);
```

**预编译SQL**

使用preparedStatement

```java
public class TestJDBC02 {
    //配置信息
    //url地址："jdbc:mysql://localhost:3306
    //数据库名称:jdbc
    //useUnicode=true&characterEncoding=utf-8解决中文乱码
    public static void main(String[] args) throws Exception {
        String url = "jdbc:mysql://localhost:3306/jdbc?useUnicode=true&characterEncoding=utf-8";
        String username = "root";
        String password = "981204";
        //1.加载驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.连接数据库。代表数据库
        Connection connection = DriverManager.getConnection(url, username, password);
        //3.编写SQL
        String sql = "insert into users(id,name,password,email,birthday) values (?,?,?,?,?);";
        //4.预编译
        PreparedStatement preparedStatement = connection.prepareStatement(sql);
        preparedStatement.setInt(1, 2);//给第一个占位符? 的值赋值为2:
        preparedStatement.setString(2, "西贝");//给第二个占位符?的值赋值为西贝;
        preparedStatement.setString(3, "123456");//给第三个占位符?的值赋值为123456;
        preparedStatement.setString(4, "24736743@qq.com");//给第四个占位符?的值赋值为24736743@qq. com;
        preparedStatement.setDate(5, new Date(new java.util.Date().getTime()));//给第五个占位符?的值赋值为new Date(new java.util.Date().getTime())
        //5.执行SQL
        int i = preparedStatement.executeUpdate();
        if (i > 0) {
            System.out.println("插入成功@");
        }
        //6.关闭连接，释放资源(一定要做)先开后关
        preparedStatement.close();
        connection.close();
    }
```

### 事务1

要么都成功，要么都失败!
ACID原则:保证数据的安全。

> 1开启事务
> 2事务提交 commit()
> 3事务回滚 rollback()
> 4关闭事务
>
> 例：转账:
>
> A:1000 B:1000
>
> A(900)--100-->B(1100)

### Junit单元测试

依赖

```xml
   <!--单元测试-->
        <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.11</version>
        </dependency>
```

简单使用
@Test注解只有在方法上有效，只要加了这个注解的方法，就可以直接运行!

```java
public class TestJDBC03 {
    @Test
    public void test(){
        System.out.println("插入成功");
    }
}
```

![img](img/1905053-20200401192448980-1408545506.png)

失败的时候是红色:

![img](img/1905053-20200401192506366-887656665.png)

### 事务2

转账原表

![img](img/1905053-20200401192519389-538290689.png)

##### 1.使用MySQL执行一条事务

```my
start transaction; #开启事务
update account set money = money-100 where name ='张三';
commit;
```

结果

![img](img/1905053-20200401192540491-516759462.png)

##### 2.使用Java执行一条事务

```java
public class TestJDBC03 {
    @Test
    public void test() {
        String url = "jdbc:mysql://localhost:3306/jdbc?useUnicode=true&characterEncoding=utf-8";
        String username = "root";
        String password = "981204";
        Connection connection = null;
        //1.加载驱动
        try {
            Class.forName("com.mysql.jdbc.Driver");
            //2.连接数据库。代表数据库
            connection = DriverManager.getConnection(url, username, password);
            //3.通知数据库开启事务,false开启
            connection.setAutoCommit(false);
            String sql = "update account set money = money-100 where name = '张三'";
            connection.prepareStatement(sql).executeUpdate();
            //制造错误
            //int i = 1 / 0;
            String sql2 = "update account set money = money+100 where name = '李四'";
            connection.prepareStatement(sql2).executeUpdate();
            connection.commit();//以上两条SQL都执行成功了，就提交事务!
            System.out.println("success");
        } catch (Exception e) {
            try {
                //如果出现异常，就通知数据库回滚事务
                connection.rollback();
            } catch (SQLException e1) {
                e1.printStackTrace();
            }
            e.printStackTrace();
        } finally {
            try {
                connection.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```

结果

![img](img/1905053-20200401192554981-379970162.png)

## 15、邮件发送

### 15.1、一个简单的邮件发送

#### 15.1.1、

简单邮件:没 有附件和图片,纯文本邮件
复杂邮件:有附件和图片
要发送邮件，需要获得协议和支持!开启服务POP3/SMTP服务
授权码:ikteyhtmiwmieajb

#### 15.1.2、流程

![img](img/1905053-20200401192612070-1574987142.png)

#### 15.1.3、相关依赖

```xml
 <!-- https://mvnrepository.com/artifact/javax.mail/mail -->
    <dependency>
      <groupId>javax.mail</groupId>
      <artifactId>mail</artifactId>
      <version>1.4.7</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/javax.activation/activation -->
    <dependency>
      <groupId>javax.activation</groupId>
      <artifactId>activation</artifactId>
      <version>1.1.1</version>
    </dependency>
```

#### 15.1.4、java代码

```java
package com.lenovo.mail;

import com.sun.mail.util.MailSSLSocketFactory;

import javax.mail.*;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import java.util.Properties;

//发送一封简单的邮件
public class MailDemo01 {
    public static void main(String[] args) throws Exception {
        Properties prop = new Properties();
        prop.setProperty("mail.host", "smtp.qq.com"); //// 设置QQ邮件服务器
        prop.setProperty("mail.transport.protocol", "smtp"); //邮件发送协议
        prop.setProperty("mail.smtp.auth", "true"); //需要验证用户名密码
        //关于Q邮箱，还要设置SSL加密，加上以下代码即可
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable", "true");
        prop.put("mail.smtp.ssl.socketFactory", sf);

        //使用JavaMail发送邮件的5个步骤
        //1、创建定义整个应用程序所需的环境信息的Session 对象
        //创建定义整个应用程序所需的环境信息的Session对象
        //QQ才有!其他邮箱就不用
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            public PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名授权码
                return new PasswordAuthentication("2458736697@qq.com", "ikteyhtmiwmieajb");
            }
        });
        //开启Session的debug模式，这样就可以查看到程序发送Email的运行状态
        session.setDebug(true);

        //2、通过session 得到transport对象
        Transport ts = session.getTransport();
        //3、使用邮箱的用户名和授权码连上邮件服务器
        ts.connect("smtp.qq.com", "2458736697@qq.com", "ikteyhtmiwmieajb");
        //4、创建邮件:写邮件
        //注意需要传递Session;
        MimeMessage message = new MimeMessage(session);
        //指明邮件的发件人
        message.setFrom(new InternetAddress("2458736697@qq.com"));
        //指明邮件的收件人，现在发件人和收件人是一样的，那就是自己给自己发
        message.setRecipient(Message.RecipientType.TO, new InternetAddress("2458736697@qq.com"));
        //邮件的标题
        message.setSubject("感谢秦老师教授的Java知识");
        //邮件的文本内容
        message.setContent("<h1 style='color: red'>你好啊!</h1>", "text/html; charset=UTF-8");
        //5.发送邮件
        ts.sendMessage(message, message.getAllRecipients());
        //6.关闭连接
        ts.close();

    }
}
```

#### 15.1.5、结果

![img](img/1905053-20200401192627647-1627449265.png)

### 15.2、带图片和附件的邮件发送

1、

MIME (多用途互联网邮件扩展类型)
MimeBodyPart类（javax.mailinternet.MimeBodyPart类）

MimeMultipart类

![img](img/1905053-20200401192706537-572824440.png)

#### 15.2.1、带图片的邮件

```java
package com.lenovo.mail;

import com.sun.mail.util.MailSSLSocketFactory;

import javax.activation.DataHandler;
import javax.activation.FileDataSource;
import javax.mail.*;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeBodyPart;
import javax.mail.internet.MimeMessage;
import javax.mail.internet.MimeMultipart;
import java.util.Properties;

//发送一封简单的邮件
public class MailDemo01 {
    public static void main(String[] args) throws Exception {
        Properties prop = new Properties();
        prop.setProperty("mail.host", "smtp.qq.com"); //// 设置QQ邮件服务器
        prop.setProperty("mail.transport.protocol", "smtp"); //邮件发送协议
        prop.setProperty("mail.smtp.auth", "true"); //需要验证用户名密码
        //关于Q邮箱，还要设置SSL加密，加上以下代码即可
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable", "true");
        prop.put("mail.smtp.ssl.socketFactory", sf);

        //使用JavaMail发送邮件的5个步骤
        //1、创建定义整个应用程序所需的环境信息的Session 对象
        //创建定义整个应用程序所需的环境信息的Session对象
        //QQ才有!其他邮箱就不用
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            public PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名授权码
                return new PasswordAuthentication("2458736697@qq.com", "ikteyhtmiwmieajb");
            }
        });
        //开启Session的debug模式，这样就可以查看到程序发送Email的运行状态
        session.setDebug(true);

        //2、通过session 得到transport对象
        Transport ts = session.getTransport();
        //3、使用邮箱的用户名和授权码连上邮件服务器
        ts.connect("smtp.qq.com", "2458736697@qq.com", "ikteyhtmiwmieajb");
        //4、创建邮件:写邮件
        //注意需要传递Session;
        MimeMessage message = new MimeMessage(session);
        //指明邮件的发件人
        message.setFrom(new InternetAddress("2458736697@qq.com"));
        //指明邮件的收件人，现在发件人和收件人是一样的，那就是自己给自己发
        message.setRecipient(Message.RecipientType.TO, new InternetAddress("2458736697@qq.com"));
        //邮件的标题
        message.setSubject("感谢秦老师教授的Java知识");

        //=========================================================
        //邮件的文本内容
        //准备图片数据
        MimeBodyPart image = new MimeBodyPart();
        //图片需要经过数据处理... DataHandLer: 数据处理
        DataHandler dh = new DataHandler(new FileDataSource("D:\\Project\\IdeaProject\\mail\\src\\1.bmp"));
        image.setDataHandler(dh);//在我们的Body中放入这个处理的图片数据
        image.setContentID("bz.jpg");//给图片设置一个ID， 我们在后面可以使用!
        //准备正文数据.
        MimeBodyPart text = new MimeBodyPart();
        text.setContent("这是一封邮件正文带图片<img src='cid:bz.jpg'>的邮件", "text/html ;charset=UTF-8");
        //描述数据关系
        MimeMultipart mm = new MimeMultipart();
        mm.addBodyPart(text);
        mm.addBodyPart(image);
        mm.setSubType("related");
        //设置到消息中，保存修改
        message.setContent(mm);//把最后编辑好的邮件放到消息当中
        message.saveChanges();//保存修改!

        //=========================================================

        //5.发送邮件
        ts.sendMessage(message, message.getAllRecipients());
        //6.关闭连接
        ts.close();

    }
}
```

#### 15.2.2、带图片和附件的邮件

```java
package com.lenovo.mail;

import com.sun.mail.util.MailSSLSocketFactory;

import javax.activation.DataHandler;
import javax.activation.FileDataSource;
import javax.mail.*;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeBodyPart;
import javax.mail.internet.MimeMessage;
import javax.mail.internet.MimeMultipart;
import java.util.Properties;

public class MailDemo02 {
    public static void main(String[] args) throws Exception {
        Properties prop = new Properties();
        prop.setProperty("mail.host", "smtp.qq.com"); //// 设置QQ邮件服务器
        prop.setProperty("mail.transport.protocol", "smtp"); //邮件发送协议
        prop.setProperty("mail.smtp.auth", "true"); //需要验证用户名密码
        //关于Q邮箱，还要设置SSL加密，加上以下代码即可
        MailSSLSocketFactory sf = new MailSSLSocketFactory();
        sf.setTrustAllHosts(true);
        prop.put("mail.smtp.ssl.enable", "true");
        prop.put("mail.smtp.ssl.socketFactory", sf);

        //使用JavaMail发送邮件的5个步骤
        //1、创建定义整个应用程序所需的环境信息的Session 对象
        //创建定义整个应用程序所需的环境信息的Session对象
        //QQ才有!其他邮箱就不用
        Session session = Session.getDefaultInstance(prop, new Authenticator() {
            public PasswordAuthentication getPasswordAuthentication() {
                //发件人邮件用户名授权码
                return new PasswordAuthentication("2458736697@qq.com", "ikteyhtmiwmieajb");
            }
        });
        //开启Session的debug模式，这样就可以查看到程序发送Email的运行状态
        session.setDebug(true);

        //2、通过session 得到transport对象
        Transport ts = session.getTransport();
        //3、使用邮箱的用户名和授权码连上邮件服务器
        ts.connect("smtp.qq.com", "2458736697@qq.com", "ikteyhtmiwmieajb");
        //4.连接上之后我们需要发送邮件;
        MimeMessage mimeMessage = imageMail(session);
        //5.发送邮件
        ts.sendMessage(mimeMessage, mimeMessage.getAllRecipients());
        //6.关闭连接
        ts.close();
    }

    public static MimeMessage imageMail(Session session) throws MessagingException {
        //消息的固定信息
        MimeMessage mimeMessage = new MimeMessage(session);
        //邮件发送人
        mimeMessage.setFrom(new InternetAddress("2458736697@qq.com"));
        //邮件接收人，可以同时发送给很多人，我们这里只发给自己;
        mimeMessage.setRecipient(Message.RecipientType.TO, new InternetAddress("2458736697@qq.com"));
        mimeMessage.setSubject("我也不知道是个什么东西就发给你了"); //邮件主题
        /*
        编写邮件内容
        1.图片
        2.附件
        3.文本
        */
        //图片
        MimeBodyPart body1 = new MimeBodyPart();
        body1.setDataHandler(new DataHandler(new FileDataSource("D:\\Project\\IdeaProject\\mail\\src\\qq.jpg")));
        body1.setContentID("yhbxb.png"); //图片设置ID
        //文本
        MimeBodyPart body2 = new MimeBodyPart();
        body2.setContent("请注意，我不是广告<img src='cid:yhbxb.png'>","text/html; charset=utf-8");
        //附件
        MimeBodyPart body3 = new MimeBodyPart();
        body3.setDataHandler(new DataHandler(new FileDataSource("D:\\Project\\IdeaProject\\mail\\src\\main\\resource\\log4j.properties")));
        body3.setFileName("log4j.properties"); //附件设置名字
        MimeBodyPart body4 = new MimeBodyPart();
        body4.setDataHandler(new DataHandler(new FileDataSource("D:\\Project\\IdeaProject\\mail\\src\\main\\resource\\1.txt")));
        body4.setFileName(""); //附件设置名字
        //拼装邮件正文内容
        MimeMultipart multipart1 = new MimeMultipart();
        multipart1.addBodyPart(body1);
        multipart1.addBodyPart(body2);
        multipart1.setSubType("related"); //1. 文本和图片内嵌成功!
        //new MimeBodyPart(). setContent (multipart1); //将拼装好的正文内容设置为主体
        MimeBodyPart contentText = new MimeBodyPart();
        contentText.setContent(multipart1);
        //拼接附件
        MimeMultipart allFile = new MimeMultipart();
        allFile.addBodyPart(body3); //附件
        allFile.addBodyPart(body4); //附件
        allFile.addBodyPart(contentText);//正文
        allFile.setSubType("mixed"); //正 文和附件都存在邮件中，所有类型设置为mixed;
        //放到Message消息中
        mimeMessage.setContent(allFile);
        mimeMessage.saveChanges();//保存修改
        return mimeMessage;
    }
}
```

项目结构

![img](img/1905053-20200401192731326-1658655105.png)

#### 15.2.3、JavaWeb网站注册成功发送邮件

项目结构

![img](img/1905053-20200401192748504-1974549550.png)

所需依赖

```xml
 <dependencies>
    <!--servlet的依赖-->
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>4.0.1</version>
    </dependency>
    <!--jsp的依赖-->
    <dependency>
      <groupId>javax.servlet.jsp</groupId>
      <artifactId>javax.servlet.jsp-api</artifactId>
      <version>2.3.3</version>
      <scope>provided</scope>
    </dependency>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
    <!-- https://mvnrepository.com/artifact/javax.mail/mail -->
    <dependency>
      <groupId>javax.mail</groupId>
      <artifactId>mail</artifactId>
      <version>1.4.7</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/javax.activation/activation -->
    <dependency>
      <groupId>javax.activation</groupId>
      <artifactId>activation</artifactId>
      <version>1.1.1</version>
    </dependency>
    <!-- 小辣椒 -->
    <dependency>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <version>1.16.20</version>
      <scope>provided</scope>
    </dependency>
  </dependencies>
```

1.实体类

```java
package com.lenovo.pojo;

import jdk.nashorn.internal.objects.annotations.Constructor;
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;
import java.io.Serializable;

@Data
@NoArgsConstructor
@AllArgsConstructor
public class User implements Serializable {
    private String username ;
    private String password;
    private String email;
}
```

2.发送邮件工具类

```java
package com.lenovo.util;

import com.lenovo.pojo.User;
import com.sun.mail.util.MailSSLSocketFactory;

import javax.mail.*;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;
import java.util.Properties;

//网站3秒原则:用户体验
//多线程实现用户体验! (异步处理)
public class Sendmail extends Thread {
    //用于给用户发送邮件的邮箱
    private String from = "2458736697@qq.com";
    //邮箱的用户名
    private String username ="2458736697@qq.com";
    //邮箱的密码
    private String password = "ikteyhtmiwmieajb";
    //发送邮件的服务器地址
    private String host = "smtp.qq.com";

    private User user;

    public Sendmail(User user) {
        this.user = user;
    }

    //重写run方法的实现，在run方法中发送邮件给指定的用户
    @Override
    public void run() {
        try {
            Properties prop = new Properties();
            prop.setProperty("mail.host", host);
            prop.setProperty("mail.transport.protocol", "smtp");
            prop.setProperty("mail.smtp.auth", "true");
            //关于QQ邮箱。还要设置SSL加密，加上以下代码即可
            MailSSLSocketFactory sf = new MailSSLSocketFactory();
            sf.setTrustAllHosts(true);
            prop.put("mail.smtp.ssl.enable", "true");
            prop.put("mail.smtp.ssl.socketFactory", sf);
            //1、创建定义整个应用程序所需的环境信息的Session对象
            Session session = Session.getDefaultInstance(prop, new Authenticator() {
                public PasswordAuthentication getPasswordAuthentication() {
                    //发件人邮件用户名、报权码
                    return new PasswordAuthentication("2458736697@qq.com", "ikteyhtmiwmieajb");
                }
            });
            //开启Sessiondebug模式，这样就可以查看到程序发送Email的运行状态
            session.setDebug(true);
            //2.通i过session 得transport对象
            Transport ts = session.getTransport();
            //3、使用邮前的用户名和技权码连上:邮件服务器
            ts.connect(host, username, password);
            //4、创建邮件
            MimeMessage message = new MimeMessage(session);
            message.setFrom(new InternetAddress(from)); //发件人
            message.setRecipient(Message.RecipientType.TO, new InternetAddress(user.getEmail())); //收件人
            message.setSubject("用户注册邮件"); //邮件的标题
            String info = "基喜您注册成功，您的用户名:" + user.getUsername() + ",您的密码:" + user.getPassword() + "，请妥普保管，如有问题请联系网站客服！！";
            message.setContent(info, "text/html; charset=UTF-8");
            message.saveChanges();
            //发送邮件
            ts.sendMessage(message, message.getAllRecipients());
            ts.close();
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

3.Servlet

```java
package com.lenovo.servlet;

import com.lenovo.pojo.User;
import com.lenovo.util.Sendmail;
import com.sun.org.apache.bcel.internal.generic.NEW;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

public class RegisterServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        //按收用户请求，封装成对象
        String username = request.getParameter("username");
        String password = request.getParameter("password");
        String email = request.getParameter("email");
        User user = new User(username, password, email);

        //用户注册成功之后，给用户发送一封邮件
        //我们使用线程米专们发送邮件，防止出现耗时，那网站注册人数过多的情况;
        Sendmail send = new Sendmail(user);
        //启动线程。线程启动之后就会执f行run方法来发送邮件
        send.start();
        //注册用户
        request.setAttribute("message", "注册成功，我们已经发了一封带了注册信息的电子邮件，请查收!如网络不稳定，可能过会儿才能收到! !");
        request.getRequestDispatcher("info.jsp").forward(request, response);

        System.out.println(username);
        System.out.println(password);
        System.out.println(email);

    }

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        doGet(request, response);
    }
}
```

4.web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">
  <servlet>
    <servlet-name>RegisterServlet</servlet-name>
    <servlet-class>com.lenovo.servlet.RegisterServlet</servlet-class>
  </servlet>
  <!--一一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>RegisterServlet</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/RegisterServlet.do</url-pattern>
  </servlet-mapping>

</web-app>
```

5.注册页面，提示页面

index.jsp

```jsp
<%@ page contentType="text/html ;charset=UTF-8" language="java" %>
<html>
    <head>
        <title>注册</title>
    </head>
    <body>
        <form action="${pageContext.request.contextPath}/RegisterServlet.do" method="post">
            用户名: <input type="text" name="username"/><br/>
            密码: <input type="password" name="password"/><br/>
            邮箱: <input type="text" name="email"/><br/>
            <input type="submit" value="注册"/>
        </form>
    </body>
</html>
```

info.jsp

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java"%>
<html>
<head>
    <title>Title</title>
</head>
<body>
<h1>xxx网站温馨提示</h1>
${message}
</body>
</html>
```

## 100、可能用到的依赖

### 1、Servlet

```xml
  <!--servlet的依赖-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
            <version>4.0.1</version>
        </dependency>
        <!--jsp的依赖-->
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>javax.servlet.jsp-api</artifactId>
            <version>2.3.3</version>
            <scope>provided</scope>
        </dependency>
        <!--JSTL的依赖-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>
        <!-- standard标签库-->
        <dependency>
            <groupId>taglibs</groupId>
            <artifactId>standard</artifactId>
            <version>1.1.2</version>
        </dependency>
        <!--连接数据库-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.17</version>
        </dependency>
        <!--单元测试-->
        <dependency>
          <groupId>junit</groupId>
          <artifactId>junit</artifactId>
          <version>4.11</version>
        </dependency>




 <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
    <dependency>
      <groupId>org.mybatis</groupId>
      <artifactId>mybatis</artifactId>
      <version>3.5.2</version>
    </dependency>
      <!-- https://mvnrepository.com/artifact/org.duracloud/common -->
      <dependency>
          <groupId>org.duracloud</groupId>
          <artifactId>common</artifactId>
          <version>6.0.0</version>
      </dependency>
    <!-- log4j -->
    <!-- https://mvnrepository.com/artifact/log4j/log4j -->
    <dependency>
      <groupId>log4j</groupId>
      <artifactId>log4j</artifactId>
      <version>1.2.17</version>
    </dependency>
    <!-- 将java对象转化为json格式的对象 -->
    <!-- https://mvnrepository.com/artifact/com.alibaba/fastjson -->
    <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>fastjson</artifactId>
      <version>1.2.58</version>
    </dependency>




<!--文件上传,导入文件上传的jar包，commons-fileupload ，Maven会自动帮我们导入他的依赖包 commons-io包；-->
    <dependency>
      <groupId>commons-fileupload</groupId>
      <artifactId>commons-fileupload</artifactId>
      <version>1.3.3</version>
    </dependency>




<!-- 邮件发送相关依赖 -->
 <!-- https://mvnrepository.com/artifact/javax.mail/mail -->
    <dependency>
      <groupId>javax.mail</groupId>
      <artifactId>mail</artifactId>
      <version>1.4.7</version>
    </dependency>
    <!-- https://mvnrepository.com/artifact/javax.activation/activation -->
    <dependency>
      <groupId>javax.activation</groupId>
      <artifactId>activation</artifactId>
      <version>1.1.1</version>
    </dependency>
    
```

### 2、

```xml
 <dependencies>
     <!-- 小辣椒 
          @Data
          @NoArgsConstructor
          @AllArgsConstructor-->
	<dependency>
		<groupId>org.projectlombok</groupId>
		<artifactId>lombok</artifactId>
		<version>1.16.20</version>
		<scope>provided</scope>
	</dependency>
	<!-- spring-context -->
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-context -->
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-context</artifactId>
		<version>4.3.3.RELEASE</version>
	</dependency>
     <!-- spring-webmvc -->
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-webmvc</artifactId>
		<version>4.3.3.RELEASE</version>
	</dependency>
     <!-- spring-mybatis -->
	<!-- https://mvnrepository.com/artifact/org.mybatis/mybatis-spring Spring整合Mybatis需要的整合包 -->
	<dependency>
		<groupId>org.mybatis</groupId>
		<artifactId>mybatis-spring</artifactId>
		<version>1.3.2</version>
	</dependency>
     <!-- AOP注解扫包 -->
	<!-- https://mvnrepository.com/artifact/aopalliance/aopalliance -->
	<dependency>
		<groupId>aopalliance</groupId>
		<artifactId>aopalliance</artifactId>
		<version>1.0</version>
	</dependency>
     <!-- https://mvnrepository.com/artifact/org.aspectj/aspectjweaver -->
	<dependency>
		<groupId>org.aspectj</groupId>
		<artifactId>aspectjweaver</artifactId>
		<version>1.8.10</version>
	</dependency>

	<!-- https://mvnrepository.com/artifact/com.fasterxml.jackson.core/jackson-databind -->
	<dependency>
		<groupId>com.fasterxml.jackson.core</groupId>
		<artifactId>jackson-databind</artifactId>
		<version>2.9.8</version>
	</dependency>
     <!-- tx配置事务管理器 -->
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-tx -->
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-tx</artifactId>
		<version>4.3.3.RELEASE</version>
	</dependency>

	<!-- 数据源 可以使用dbcp2,c3p0,druid... -->
	<!-- https://mvnrepository.com/artifact/org.apache.commons/commons-dbcp2 -->
	<dependency>
		<groupId>org.apache.commons</groupId>
		<artifactId>commons-dbcp2</artifactId>
		<version>2.1.1</version>
	</dependency>
	<!-- 文件上传 -->
	<!-- https://mvnrepository.com/artifact/commons-fileupload/commons-fileupload -->
	<dependency>
		<groupId>commons-fileupload</groupId>
		<artifactId>commons-fileupload</artifactId>
		<version>1.3.3</version>
	</dependency>
	<!-- Jackson -->

	<!-- 配置声明式事务 -->
	<!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-jdbc</artifactId>
		<version>4.3.3.RELEASE</version>
	</dependency>
	<!-- jedisjar -->
	<dependency>
		<groupId>redis.clients</groupId>
		<artifactId>jedis</artifactId>
		<version>2.9.0</version>
	</dependency>
	<!-- 连接池 -->
	<!-- https://mvnrepository.com/artifact/commons-pool/commons-pool -->
	<dependency>
		<groupId>commons-pool</groupId>
		<artifactId>commons-pool</artifactId>
		<version>1.5.6</version>
	</dependency>
	<!-- spring整合Redis包 -->
	<!-- https://mvnrepository.com/artifact/org.springframework.data/spring-data-redis -->
	<dependency>
		<groupId>org.springframework.data</groupId>
		<artifactId>spring-data-redis</artifactId>
		<version>1.6.0.RELEASE</version>
	</dependency>
 </dependencies>
```

### 3、pom.xml中设置资源通配

maven由于他的约定大于配置，我们之后可以能遇到我们写的配置文件，无法被导出或者生效的问题，解决方
案:

```xml
<build>
    <resources>
      <resource>
        <directory>src/main/resources</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>true</filtering>
      </resource>
      <resource>
        <directory>src/main/java</directory>
        <includes>
          <include>**/*.properties</include>
          <include>**/*.xml</include>
        </includes>
        <filtering>true</filtering>
      </resource>
    </resources>
  </build>
```

### 4、web.xml通用头文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">
  

</web-app>
```

### 5、web.xml中可以配置

```xml
	<display-name>Archetype Created Web Application</display-name>


  <!--web. xmL中是配置我们web的核心应用-->
  <!--注册ServLet-->
  <servlet>
    <servlet-name>helloselvlet</servlet-name>
    <servlet-class>com.lenovo.servlet.Servlet02</servlet-class>
  </servlet>
  <!--一一个Servlet对应一Mapping: 映射-->
  <servlet-mapping>
    <servlet-name>helloselvlet</servlet-name>
    <!--映射的请求路径-->
    <url-pattern>/zhuchengbo</url-pattern>
  </servlet-mapping>


 <!--配置一些web应用初始化参数-->
   <context-param>
       <param-name>url</param-name>
       <param-value>jdbc:mysql://localhost:3306/mybatis</param-value>
   </context-param>
  <servlet>
    <servlet-name>url</servlet-name>
    <servlet-class>com.lenovo.servlet.ServletDemo03</servlet-class>
  </servlet>
  <servlet-mapping>
    <servlet-name>url</servlet-name>
    <url-pattern>/url</url-pattern>
  </servlet-mapping>


	<!--注册监听器-->
    <listener>
        <listener-class>com.lenovo.filter.listener</listener-class>
    </listener>


    <!--设置Session默认的失效时间:真实业务需球-->
    <session-config>
        <!--15 分钟后Session自动失效。以分钟为单位-->
        <session-timeout>1</session-timeout>
    </session-config>


 	<!--设置欢迎页面-->
	<!--启动服务器后直接展示的页面-->
    <welcome-file-list>
    	<welcome-file>admin_login.jsp</welcome-file>
    </welcome-file-list>


  	<!--用户登录过滤器-->
	<!--设置admin_list.jsp不能直接访问，需要先进行登录-->
    <filter>
        <filter-name>SysFilter</filter-name>
        <filter-class>com.neuedu.filter.SysFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>SysFilter</filter-name>
        <url-pattern>/admin_list.jsp</url-pattern>
    </filter-mapping>
```