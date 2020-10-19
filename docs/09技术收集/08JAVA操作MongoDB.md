---
title: "Java操作MongoDB"
date: 2020-01-02 23:20:30
tags: Java
comments: true
description: "Java操作MongoDB" 作者:聂长安"
---

> 作者:Nie Changan 转载请标明出处

## 使用Java操作MongoDB

我这边使用的docker安装MongoDB作为服务器的,如果你们服务器或者本机安装了也可以

1.安装Docker

```shell
#更新yum
yum update
#安装docker
yum install docker
#查看版本
docker -v
#设置国内仓库地址
vi /etc/docker/daemon.json
{
        "registry-mirrors": ["http://f1361db2.m.daocloud.io"]
}
#重启服务
systemctl restart docker.service
#下载Mongo
docker pull mongo
#查看镜像
docker images
#制作容器
docker run --name mongo -p 27017:27017 -d mongo
#进入容器内部
docker exec -it 容器ID /bin/bash
#找到客户端
whereis mongo
find / -name mongo
#启动客户端加入数据
./mongo
```

```tex
db.student.insert({_id:"1",content:"我还是没有想明白到底为啥出错",userid:"1012",name:"ange",visits:NumberInt(2020)}); 
db.student.insert({_id:"2",content:"加班到半夜",userid:"1013",name:"rock",visits:NumberInt(1023)}); 
db.student.insert({_id:"3",content:"手机流量超了咋办？",userid:"1013",name:"pika",visits:NumberInt(111)}); 
db.student.insert({_id:"4",content:"坚持就是胜利",userid:"1014",name:"tiger",visits:NumberInt(1223)}); 
```

* 实现java操作Mongo的查询

pom.xml

```xml
<dependencies>
    <dependency>
        <groupId>org.mongodb</groupId>
        <artifactId>mongodb-driver</artifactId>
        <version>3.8.2</version>
    </dependency>
</dependencies>
```

* 查询

```java
//创建连接
MongoClient client = new MongoClient("192.168.126.154");

//获取操作的数据库
MongoDatabase studentdb = client.getDatabase("studentdb");

//获取集合(collections)
MongoCollection<Document> student = studentdb.getCollection("student");

//按照条件进行查询
//第一种
/*Map<String,Object> map = new HashMap<>();
        map.put("userid","1013");
        map.put("name","rock");
        BasicDBObject bson = new BasicDBObject(map);*/
//BasicDBObject bson = new BasicDBObject("userid","1013");

//不能支持多个条件传入的
Bson bson = Filters.eq("userid", "1013");

//获取文档中的内容
FindIterable<Document> documents = student.find(bson);

/*Document doc = student.find(bson).first();
        System.out.println(doc.getString("_id"));*/

//循环获取内容
//创建一个Student的类
//创建一个List<Student>的集合
for (Document document :documents
             ) {
            System.out.println(document.getString("_id"));
            System.out.println(document.getString("content"));
            System.out.println(document.getString("name"));
            System.out.println(document.getString("userid"));
            System.out.println(document.getInteger("visits"));
        }

//关闭连接
client.close();
```

* 新增

```java
MongoClient client = null;
try {
    //创建连接
    client = new MongoClient("192.168.126.154");

    //获取操作的数据库
    MongoDatabase studentdb = client.getDatabase("studentdb");

    //获取集合(collections)
    MongoCollection<Document> student = studentdb.getCollection("student");

    Map<String,Object> map = new HashMap<>();
    map.put("_id",5);
    map.put("content","今天天气还算是不错的");
    map.put("userid","1018");
    map.put("name","qingmu");
    map.put("visits",200);
    Document document = new Document(map);

    //插入数据
    student.insertOne(document);

    System.out.println("增加成功");
} catch (Exception e) {
    e.printStackTrace();
}finally {
    //关闭连接
    client.close();
}
```

* 删除

```java
MongoClient client = null;
try {
    //创建连接
    client = new MongoClient("192.168.126.154");

    //获取操作的数据库
    MongoDatabase studentdb = client.getDatabase("studentdb");

    //获取集合(collections)
    MongoCollection<Document> student = studentdb.getCollection("student");

    //一次只会删除一条
    //student.deleteMany()
    Bson bson = Filters.eq("_id",5);
    student.deleteOne(bson);

    System.out.println("删除成功");
} catch (Exception e) {
    e.printStackTrace();
}finally {
    //关闭连接
    client.close();
}
```

* 更新

```java
MongoClient client = null;
try {
    //创建连接
    client = new MongoClient("192.168.126.154");

    //获取操作的数据库
    MongoDatabase studentdb = client.getDatabase("studentdb");

    //获取集合(collections)
    MongoCollection<Document> student = studentdb.getCollection("student");

    //一次只会删除一条
    //student.deleteMany()
    Bson bson = Filters.eq("_id","4");
    Document document = new Document("$set",new Document("content","每天坚持上车"));
    student.updateOne(bson,document);

    System.out.println("修改成功");
} catch (Exception e) {
    e.printStackTrace();
}finally {
    //关闭连接
    client.close();
}
```



## 使用SpringBoot操作MongoDB

* pom.xml

  ```xml
  <dependencies>
      <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-data-mongodb</artifactId>
      </dependency>
      <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-web</artifactId>
      </dependency>
  
      <dependency>
          <groupId>org.projectlombok</groupId>
          <artifactId>lombok</artifactId>
          <optional>true</optional>
      </dependency>
      <dependency>
          <groupId>org.springframework.boot</groupId>
          <artifactId>spring-boot-starter-test</artifactId>
          <scope>test</scope>
          <exclusions>
              <exclusion>
                  <groupId>org.junit.vintage</groupId>
                  <artifactId>junit-vintage-engine</artifactId>
              </exclusion>
          </exclusions>
      </dependency>
  </dependencies>
  ```

* application.yml

  ```yaml
  spring:
    data:
      mongodb:
        host: 192.168.126.154
        database: studentdb
  ```

* Student.java

  ```java
  package com.yrkedu.springboot_mongodb.pojo;
  
  import lombok.Data;
  
  @Data
  public class Student {
  
      private String id;
  
      private String content;
  
      private String name;
  
      private String userId;
  
      private Integer visits;
  }
  ```

* StudentDao.java

  ```java
  package com.yrkedu.springboot_mongodb.dao;
  
  import com.yrkedu.springboot_mongodb.pojo.Student;
  
  import java.util.List;
  
  public interface StudentDao {
  
      void save(Student student);
  
      void update(Student student);
  
      List<Student> findAlll();
  
      void delete(String id);
  }
  ```

* StudentDaoImpl.java

  ```java
  package com.yrkedu.springboot_mongodb.dao.impl;
  
  import com.yrkedu.springboot_mongodb.dao.StudentDao;
  import com.yrkedu.springboot_mongodb.pojo.Student;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.data.mongodb.core.MongoTemplate;
  import org.springframework.data.mongodb.core.query.Criteria;
  import org.springframework.data.mongodb.core.query.Query;
  import org.springframework.data.mongodb.core.query.Update;
  import org.springframework.stereotype.Component;
  
  import java.util.List;
  
  @Component
  public class StudentDaoImpl implements StudentDao {
  
      @Autowired
      private MongoTemplate mongoTemplate;
  
  
      @Override
      public void save(Student student) {
          mongoTemplate.save(student);
      }
  
      @Override
      public void update(Student student) {
  
          //条件
          Query query = new Query(Criteria.where("_id").is(student.getId()));
  
          //修改的内容
          Update update = new Update();
          update.set("content",student.getContent());
          update.set("userid",student.getUserId());
          update.set("name",student.getName());
          update.set("visits",student.getVisits());
  
          mongoTemplate.updateFirst(query,update,Student.class);
      }
  
      @Override
      public List<Student> findAlll() {
          return mongoTemplate.findAll(Student.class);
      }
  
      @Override
      public void delete(String id) {
          Student student = mongoTemplate.findById(id, Student.class);
          mongoTemplate.remove(student);
      }
  }
  ```

* StudentController.java

  ```java
  package com.yrkedu.springboot_mongodb.controller;
  
  import com.yrkedu.springboot_mongodb.dao.StudentDao;
  import com.yrkedu.springboot_mongodb.pojo.Student;
  import org.springframework.beans.factory.annotation.Autowired;
  import org.springframework.data.mongodb.core.query.Criteria;
  import org.springframework.data.mongodb.core.query.Query;
  import org.springframework.data.mongodb.core.query.Update;
  import org.springframework.web.bind.annotation.*;
  
  import java.util.List;
  
  @RestController
  public class StudentController {
  
      @Autowired
      private StudentDao studentDao;
  
      @PostMapping("/save")
      public String save(Student student) {
          try {
              studentDao.save(student);
              return "1";
          } catch (Exception e) {
              e.printStackTrace();
              return "0";
          }
      }
  
      @PutMapping("/update")
      public String update(Student student) {
          studentDao.update(student);
          return "1";
      }
  
      @GetMapping("/findAll")
      public List<Student> findAlll() {
          return studentDao.findAlll();
      }
  
      @DeleteMapping("/delete")
      public String delete(String id) {
          studentDao.delete(id);
          return "1";
      }
  }
  ```

