# Swagger

学习目标:
●了解Swagger的作用和概念
●了解前后端分离
●在SpringBoot中集成Swagger

## 1、Swagger简介

前后端分离

Vue + SpringBoot

后端时代:前端只用管理静态页面; html==> 后端。模板引擎JSP =>后端是主力

前后端分离式时代:

- 后端:后端控制层,服务层,数据访问层[后端团队]
- 前端:前端控制层,视图层[前端团队]
  - 伪造后端数据，json。 已经存在了，不需要后端，前端工程依旧能够跑起来
- 前端后如何交互? ===> API
- 前后端相对独立,松耦合;
- 前后端甚至可以部署在不同的服务器上;

产生一个问题:

- 前后端集成联调，前端人员和后端人员无法做到“即使协商， 尽早解决”，最终导致问题集中爆发;

解决方案:首先指定schema[计划的提纲]，实时更新最新API,降低集成的风险;

- 早些年:指定word计划文档;
- 前后端分离:
  - 前端测试后端接口: postman
  - 后端提供接口，需要实时更新最新的消息及改动!

## 2、Swagger

- 号称世界上最流行的Api框架;
- RestFul Api文档在线自动生成工具=>**Api文档与API定义同步更新**
- 直接运行，可以在线测试API接口;
- 支持多种语言: Java, Php...

官网: https://swagger.io/

在项目使用Swagger需要springbox;

- swagger2
- ui

## 3、SpringBoot集成Swagger

1.新建一个SpringBoot-web项目

2.导入相关依赖

```xml
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger2 -->
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger2</artifactId>
   <version>2.9.2</version>
</dependency>

<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger-ui</artifactId>
   <version>2.9.2</version>
</dependency>
```

3.编写一个Hello工程

4.配置Swagger ==> Config

5.测试运行:http://localhost:8080/swagger-ui.html

![img](img/1905053-20200401211812033-1951894226.png)

## 4、配置Swagger信息

```java
package com.kuang.swagger.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.service.Contact;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

import java.util.ArrayList;

@Configuration
@EnableSwagger2 //开启Swagger2
public class SwaggerConfig {

    //配置了swagger的Docket的bean实例
    @Bean
    public Docket docket() {
        return new Docket(DocumentationType.SWAGGER_2).apiInfo(apiInfo());
    }

    //配置swagger信息=apiInfo
    private ApiInfo apiInfo() {
//作者信息
        Contact contact = new Contact("秦疆", "https://blog.kuangstudy.com/", "24736743@qq.com");
        return new ApiInfo(
                "狂神的SwaggerAPI文档",
                "即使再小的帆也能远航",
                "v1.0",
                "https://blog.kuangstudy.com/",
                contact,
                "Apache 2.0",
                "http://www.apache.org/licenses/LICENSE-2.0",
                new ArrayList()
        );
    }
}
```

## 5、Swangger配置扫描接口

Docket.select

接口过滤的一些东西

```java
//配置了swagger的Docket的bean实例
    @Bean
    public Docket docket() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .select()
                //RequestHandlerSelectors,配置要扫描接口的方式
                //basePackage:指定要扫描的包
                //any();扫描全部
                //none():不扫描
                //withClassAnnotation:扫描类上的注解，参数是一个注解的反射对象
                //wi thMethodAnnotation:扫描方法上的注解
       		   .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
                //paths():过滤什么路径
                .paths(PathSelectors.ant("/kuang/**"))
                .build();   
    }
```

## 6、配置是否启动Swagger

enable(false)//enable是否启动Swagger,如果为False,则Swagger不能再浏觉器中访问

```java
 @Bean
    public Docket docket() {
        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .enable(false)//enable是否启动Swagger,如果为False,则Swagger不能再浏觉器中访问
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
                //.paths(PathSelectors.ant("/kuang/**"))
                .build();

    }
```

**我只希望我的Swagger在生产环境中使用，在发布的时候不使用**?

- 判断是不是生产环境flag = false
- 注入enable (flag)

```java
@Bean
    public Docket docket(Environment environment) {

        //设置要显示的Swagger环境
        Profiles profiles = Profiles.of("dev", "test");
        //通过environment.acceptsProfiles判断是否处在自己设定的环境当中
        boolean flag = environment.acceptsProfiles(profiles);


        return new Docket(DocumentationType.SWAGGER_2)
                .apiInfo(apiInfo())
                .enable(flag)//enable是否启动Swagger,如果为False,则Swagger不能再浏觉器中访问
                .select()
                .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
                //.paths(PathSelectors.ant("/kuang/**"))
                .build();
    }
```

application.properties

```properties
spring.profiles.active=pro
```

application-dev.properties

```properties
server.port=8081
```

application-pro.properties

```properties
server.port=8083
```

结果：

![img](img/1905053-20200401211833417-1570386502.png)

将application.properties改为

```properties
spring.profiles.active=dev
```

![img](img/1905053-20200401211852513-2010735710.png)

## 7、配置API文档的分组

```java
 .groupName("西贝")
```

![img](img/1905053-20200401211910058-1511752028.png)

如何配置多个分组;多个Docket实例即可

```java
@Bean
    public Docket docket1() {
        return new Docket(DocumentationType.SWAGGER_2).groupName("1");
    }

    @Bean
    public Docket docket2() {
        return new Docket(DocumentationType.SWAGGER_2).groupName("2");
    }

    @Bean
    public Docket docket3() {
        return new Docket(DocumentationType.SWAGGER_2).groupName("3");
    }
```

查看分组

![img](img/1905053-20200401211926754-1561512497.png)

实体类：

```java
package com.kuang.swagger.pojo;

import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
//@ApiModel("注释")
@ApiModel("用户实体类")
public class User {
    @ApiModelProperty("用户名")
    public String username;
    @ApiModelProperty("密码")
    public String password;
}
```

接口的：

```java
//只要我们的接口中，返回值中存在实体类，他就会被扫描到swagger中
    @PostMapping(value = "/user")
    public User user() {
        return new User();
    }

    //operation接口,不是放在类上的，是方法
    @ApiOperation("Hello控制类")
    @GetMapping(value = "/hello2")
    public String hello2(@ApiParam("用户名") String username) {
        return "hello" + username;
    }
```

## 8、在线测试

```java
@ApiOperation("Post测试类")
    @PostMapping(value = "/postt")
    public User postt (@ApiParam("用户名") User user){
        int i = 5/0;
        return user ;
    }
```

![img](img/1905053-20200401211945433-847344851.png)

可观察错误

![img](img/1905053-20200401212002687-634594623.png)

## 9、总结

1.我们可以通过Swagger给一-些比较难理解的属性或者接口，增加注释信息

2.接口文档实时更新

3.可以在线测试

Swagger是一个优秀的工具， 几乎所有大公司都有使用它

[**注意点**]在正式发布的时候，关闭Swagger! ! !出于安全考虑。而且节省运行的内存;