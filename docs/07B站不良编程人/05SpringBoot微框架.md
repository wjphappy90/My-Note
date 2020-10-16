# Spring Boot 微框架



## 1. springboot的引言

> Spring Boot是由`Pivotal团队提供的全新框架`，其设计目的是用来`简化Spring应用的 初始搭建以及开发过程`。该框架使用了`特定的方式来进行配置`，从而使开发人员不 再需要定义样板化的配置。通过这种方式，Spring Boot致力于在蓬勃发展的快速应 用开发领域(rapid application development)成为领导者。
>
> `springboot(微框架) = springmvc(控制器) + spring(项目管理)`

---

## 2. springboot的特点

1. `创建独立的Spring应用程序  `

2. `嵌入的Tomcat，无需部署WAR文件`

3. `简化Maven配置`

4. `自动配置Spring`

5. `没有XML配置`

   ---


## 3. springboot的环境搭建

> 环境要求:
>
> > 1. MAVEN 3.x+
> > 2. Spring FrameWork 4.x+
> > 3. JDK7.x +
> > 	. Spring Boot 1.5.x+	

##### 	3.1 项目中引入依赖

```xml
    <!--继承springboot的父项目-->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.7.RELEASE</version>
    </parent>

    <dependencies>
        <!--引入springboot的web支持-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
```

##### 	3.2 引入配置文件

​		`项目中src/main/resources/application.yml`

##### 	3.3 建包并创建控制器

```java
//在项目中创建指定的包结构
/*
	 com
	    +| baizhi
	    		+| controller */ 
                	@Controller
                    @RequestMapping("/hello")
                    public class HelloController {
                        @RequestMapping("/hello")
                        @ResponseBody
                        public String hello(){
                            System.out.println("======hello world=======");
                            return "hello";
                        }
                    }
               	    		  		
```

##### 	3.4 编写入口类

```java
//在项目中如下的包结构中创建入口类 Application
/*
	com
		+| baizhi                  */
            @SpringBootApplication
            public class Application {
                public static void main(String[] args) {
                    SpringApplication.run(Application.class,args);
                }
            }
```

##### 	3.5 运行main启动项目

```java
o.s.j.e.a.AnnotationMBeanExporter        : Registering beans for JMX exposure on startup
s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat started on port(s): 8989 (http)
com.baizhi.Application : Started Application in 2.152 seconds (JVM running for 2.611)

//说明:  出现以上日志说明启动成功
```

##### 	3.6 访问项目 

```java
//注意: springboot的项目默认没有项目名
//访问路径:  http://localhost:8080/hello/hello
```

---

## 4. 启动tomcat端口占用问题

```yaml
server:
  port: 8989                 #用来指定内嵌服务器端口号
  context-path: /springboot  #用来指定项目的访问路径
```

---

## 5. springboot相关注解说明

```markdown

# Spring boot通常有一个名为 xxxApplication的类,入口类中有一个main方法, 在main方法中使用SpringApplication.run(xxxApplication.class,args)启动springboot应用的项目。

# @RestController: 就是@Controller+@ResponseBody组合，支持RESTful访问方 式，返回结果都是json字符串。

# @SpringBootApplication 注解等价于: 
	@SpringBootConfiguration           标识注解,标识这是一个springboot的配置类
	@EnableAutoConfiguration           自动与项目中集成的第三方技术进行集成
	@ComponentScan			 			扫描入口类所在子包以及子包后代包中注解	
   
```

---

## 6. springboot中配置文件的拆分

```yaml
#说明: 在实际开发过程中生产环境和测试环境有可能是不一样的 因此将生产中的配置和测试中的配置拆分开,是非常必要的在springboot中也提供了配置文件拆分的方式. 这里以生产中项名名称不一致为例:
	
	生产中项目名为: cmfz
	测试中项目名为: springboot
	端口同时为:   8080

拆分如下:
	#主配置文件:
			application.yml	#用来书写相同的的配置
				server:
					port: 8080 #生产和测试为同一个端口
                   
    #生产配置文件:
    	  application-pord.yml
    			server:
    				context-path: /cmfz
    #测试配置文件:
    		application-dev.yml
    			server:
    				context-path: /springboot

```

---

## 7.springboot中创建自定义简单对象

### 7.1 管理单个对象

> 在springboot中可以管理自定义的`简单组件`对象的创建可以直接使用注解形式创建。

```markdown
# 1.使用 @Repository  @Service @Controller 以及@Component管理不同简单对象
	如: 比如要通过工厂创建自定义User对象:
```

```java
@Component
@Data
public class User {
  private String id;
  private String name;
  ......
}	
```

``` markdown
# 2.通过工厂创建之后可以在使用处任意注入该对象
	如:在控制器中使用自定义简单对象创建
```

```java
@Controller
@RequestMapping("hello")
public class HelloController {
    @Autowired
    private User user;
  	......
}
```

### 7.2 管理多个对象

> 在springboot中如果要管理`复杂对象`必须使用`@Configuration + @Bean`注解进行管理

```markdown
# 1.管理复杂对象的创建
```

```java
@Configuration(推荐)|@Component(不推荐)
public class Beans {
    @Bean
    public Calendar getCalendar(){
        return Calendar.getInstance();
    }
}
```

```markdown
# 2.使用复杂对象
```

```java
@Controller
@RequestMapping("hello")
public class HelloController {
    @Autowired
    private Calendar calendar;
    ......
}
```

```markdown
# 注意: 
			  1.@Configuration 配置注解主要用来生产多个组件交给工厂管理  (注册形式)
			  2.@Component     用来管理单个组件                      (包扫描形式)
```

------

## 8.springboot中注入

> ​	springboot中提供了三种注入方式: `注入基本属性`,`对象注入`

##### 8.1 基本属性注入

```markdown
# 1.@Value 属性注入   [重点]
```

```java
@Controller
@RequestMapping("hello")
public class HelloController {
  
    @Value("${name}")
    private String name;
    
    @Value("#{'${lists}'.spilt(",")}")
    private List<String> lists;
    
    @Value("#{${maps}}")
    private Map<String,String> maps;
}
```

```markdown
# 2.在配置文件中注入
```

```yaml
name: xiaohei
lists: xiaohei,xiaoming,xiaowang
maps: "{key:'value',key1:'value1'}"
```

##### 8.2 对象方式注入

```markdown
# 1. @ConfigurationProperties(prefix="前缀")
```

```java
@Component
@Data
@ConfigurationProperties(prefix = "user")
public class User {
    private String id;
    private String name;
    private Integer age;
    private String  bir;
    .....
}
```

```markdown
# 2. 编写配置文件
```

```yaml
user:
  id: 24
  name: xiaohei
  age: 23
  bir: 2012/12/12
```

```markdown
# 3. 引入依赖构建自定义注入元数据
```

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-configuration-processor</artifactId>
  <optional>true</optional>
</dependency>
```

------

## 9. springboot中集成jsp展示

##### 	9.1 引入jsp的集成jar包

```xml
<dependency>
    <groupId>jstl</groupId>
    <artifactId>jstl</artifactId>
    <version>1.2</version>
</dependency>

<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-tomcat</artifactId>
</dependency>

<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
```

##### 	9.2 引入jsp运行插件

```xml
<build>
    <finalName>springboot_day1</finalName>
    <!--引入jsp运行插件-->
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

##### 	9.3 配置视图解析器

```yaml
#在配置文件中引入视图解析器
spring:
  mvc:
    view:
      prefix: /   	# /代表访问项目中webapp中页面
      suffix: .jsp 
```

##### 	9.4 启动访问jsp页面

```http
http://localhost:8989/cmfz/index.jsp
```

---

## 10. springboot集成mybatis

##### 	10.1 引入依赖

```markdown
<!--整合mybatis-->
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>1.3.3</version>
</dependency>

<dependency>
	<groupId>com.alibaba</groupId>
	<artifactId>druid</artifactId>
	<version>1.1.12</version>
</dependency>

<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.38</version>
</dependency>

>说明:由于springboot整合mybatis版本中默认依赖mybatis 因此不需要额外引入mybati版本,否则会出现冲突
```

##### 	10.2 配置配置文件

```yaml
spring:
  mvc:
    view:
      prefix: /
      suffix: .jsp
  datasource:
    type: org.apache.commons.dbcp.BasicDataSource   #指定连接池类型
    driver-class-name: com.mysql.jdbc.Driver        #指定驱动
    url: jdbc:mysql://localhost:3306/cmfz           #指定url
    username: root									#指定用户名
    password: root								 	#指定密码
```

##### 	10.3 加入mybatis配置

```yaml
#配置文件中加入如下配置:

mybatis:
  mapper-locations: classpath:com/baizhi/mapper/*.xml  #指定mapper配置文件位置
  type-aliases-package: com.baizhi.entity              #指定起别名来的类
```

```java
//入口类中加入如下配置:
@SpringBootApplication
@MapperScan("com.baizhi.dao")   //必须在入口类中加入这个配置
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class,args);
    }
}
```



##### 	10.4 建表

```sql
CREATE TABLE `t_clazz` (
  `id` varchar(40) NOT NULL,
  `name` varchar(80) DEFAULT NULL,
  `no` varchar(90) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

##### 	10.5 开发实体类

```java
public class Clazz {
    private String id;
    private String name;
    private String no;
    //get set 方法省略....
}
```

##### 	10.6 开发DAO接口以及Mapper

```java
public interface ClazzDAO {
    List<Clazz> findAll();
}
```

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.baizhi.dao.ClazzDAO">
    <select id="findAll" resultType="Clazz">
        select * from t_clazz 
    </select>
</mapper>
```

##### 	10.7 开发Service以及实现

```java
//接口
public interface ClazzService {
    List<Clazz> findAll();
}
//实现
@Service
@Transactional
public class ClazzServiceImpl implements  ClazzService {
    @Autowired
    private ClazzDAO clazzDAO;
    
    @Transactional(propagation = Propagation.SUPPORTS)
    @Override
    public List<Clazz> findAll() {
        return clazzDAO.findAll();
    }
}
```

##### 	10.8 引入测试依赖

```xml
 <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
     <scope>test</scope>
</dependency>
```

##### 	10.9 编写测试类

```java
@RunWith(SpringRunner.class)
@SpringBootTest(classes = Application.class)
public class TestClazzService {

    @Autowired
    private ClazzService clazzService;

    @Test
    public void test(){
        List<Clazz> all = clazzService.findAll();
        for (Clazz clazz : all) {
            System.out.println(clazz);
        }

    }
}
```

## 11.开启jsp页面热部署

##### 11.1 引言

> `在springboot中默认对jsp运行为生产模式,不允许修改内容保存后立即生效,因此在开发过程需要调试jsp页面每次需要重新启动服务器这样极大影响了我们的效率,为此springboot中提供了可以将默认的生产模式修改为调试模式,改为调试模式后就可以保存立即生效,如何配置为测试模式需要在配置文件中加入如下配置即可修改为开发模式。`

##### 11.2 配置开启测试模式

```yml
server:
  port: 8989
  jsp-servlet:
    init-parameters:
      development: true  #开启jsp页面的调试模式
```

----

## 12.springboot中devtools热部署

##### 12.1  引言

> ​	`为了进一步提高开发效率,springboot为我们提供了全局项目热部署,日后在开发过程中修改了部分代码以及相关配置文件后,不需要每次重启使修改生效,在项目中开启了springboot全局热部署之后只需要在修改之后等待几秒即可使修改生效。`

##### 12.2 开启热部署

###### 	12.2.1 项目中引入依赖

```xml
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-devtools</artifactId>
   <optional>true</optional>
</dependency>
```

###### 	12.2.2 设置idea中支持自动编译

```markdown
# 1.开启自动编译

	Preferences | Build, Execution, Deployment | Compiler -> 勾选上 Build project automatically 这个选项

# 2.开启允许在运行过程中修改文件
	ctrl + alt + shift + / ---->选择1.Registry ---> 勾选 compiler.automake.allow.when.app.running 这个选项
```

###### 12.2.3 启动项目检测热部署是否生效

```markdown
# 1.启动出现如下日志代表生效
```

```verilog
2019-07-17 21:23:17.566  INFO 4496 --- [  restartedMain] com.baizhi.InitApplication               : Starting InitApplication on chenyannandeMacBook-Pro.local with PID 4496 (/Users/chenyannan/IdeaProjects/ideacode/springboot_day1/target/classes started by chenyannan in /Users/chenyannan/IdeaProjects/ideacode/springboot_day1)
2019-07-17 21:23:17.567  INFO 4496 --- [  restartedMain] com.baizhi.InitApplication               : The following profiles are active: dev
2019-07-17 21:23:17.612  INFO 4496 --- [  restartedMain] ationConfigEmbeddedWebApplicationContext : Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@66d799c5: startup date [Wed Jul 17 21:23:17 CST 2019]; root of context hierarchy
2019-07-17 21:23:18.782  INFO 4496 --- [  restartedMain] s.b.c.e.t.TomcatEmbeddedServletContainer : Tomcat initialized with port(s): 8989 (http)
2019-07-17 21:23:18.796  INFO 4496 --- [  restartedMain] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2019-07-17 21:23:18.797  INFO 4496 --- [  restartedMain] org.apache.catalina.core.StandardEngine  : Starting Servlet Engine: Apache Tomcat/8.5.20

```

> `注意:日志出现restartedMain代表已经生效,在使用热部署时如果遇到修改之后不能生效,请重试重启项目在试`

##  12. logback日志的集成

##### 	12.1 logback简介

> Logback是由[log4j](https://baike.baidu.com/item/log4j/480673)创始人设计的又一个开源日志组件。目前，logback分为三个模块：logback-core，logback-classic和logback-access。是对log4j日志展示进一步改进

##### 	12.2 日志的级别

	> DEBUG < INFO < WARN < ERROR   
	>
	> 日志级别由低到高:  日志级别越高输出的日志信息越少

##### 	12.3 项目中日志分类

	> 日志分为两类
	>
	>  一种是rootLogger :  用来监听项目中所有的运行日志 包括引入依赖jar中的日志 
	>
	>  一种是logger :         用来监听项目中指定包中的日志信息

##### 	12.4 java项目中使用

###### 12.4.1 logback配置文件

		> logback的配置文件必须放在项目根目录中 且名字必须为logback.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<configuration>
    <!--定义项目中日志输出位置-->
    <appender name="stdout" class="ch.qos.logback.core.ConsoleAppender">
        <!--定义项目的日志输出格式-->
        <!--定义项目的日志输出格式-->
        <layout class="ch.qos.logback.classic.PatternLayout">
            <pattern> [%p] %d{yyyy-MM-dd HH:mm:ss} %m %n</pattern>
        </layout>
    </appender>

    <!--项目中跟日志控制-->
    <root level="INFO">
        <appender-ref ref="stdout"/>
    </root>
    <!--项目中指定包日志控制-->
    <logger name="com.baizhi.dao" level="DEBUG"/>

</configuration>
```

###### 		12.4.2 具体类中使用日志

```java
@Controller
@RequestMapping("/hello")
public class HelloController {
    //声明日志成员
    private static org.apache.log4j.Logger logger = org.apache.log4j.Logger.getLogger(HelloController.class);
    @RequestMapping("/hello")
    @ResponseBody
    public String hello(){
        System.out.println("======hello world=======");
        logger.debug("DEBUG");
        logger.info("INFO");
        logger.warn("WARN");
        logger.error("ERROR");
        return "hello";
    }
}
```

###### 12.4.3 使用默认日志配置

```yml
logging:
  level:
    root: debug
    com.baizhi.dao: debug
  path: /Users/chenyannan/aa.log
  file: bbb.log
```



---

## 12. 切面编程

##### 	12.1 引言

> springboot是对原有项目中spring框架和springmvc的进一步封装,因此在springboot中同样支持spring框架中AOP切面编程,不过在springboot中为了快速开发仅仅提供了注解方式的切面编程.

##### 	12.2 使用

###### 		12.2.1 引入依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

###### 		12.2.2 相关注解

```java
/**
    @Aspect 用来类上,代表这个类是一个切面
    @Before 用在方法上代表这个方法是一个前置通知方法 
    @After 用在方法上代表这个方法是一个后置通知方法 @Around 用在方法上代表这个方法是一个环绕的方法
    @Around 用在方法上代表这个方法是一个环绕的方法
**/
```

###### 		12.2.3 前置切面

```java
@Aspect
@Component
public class MyAspect {
    @Before("execution(* com.baizhi.service.*.*(..))")
    public void before(JoinPoint joinPoint){
        System.out.println("前置通知");
        joinPoint.getTarget();//目标对象
        joinPoint.getSignature();//方法签名
        joinPoint.getArgs();//方法参数
    }
}
```

###### 		12.2.4 后置切面

```java
@Aspect
@Component
public class MyAspect {
    @After("execution(* com.baizhi.service.*.*(..))")
    public void before(JoinPoint joinPoint){
        System.out.println("后置通知");
        joinPoint.getTarget();//目标对象
        joinPoint.getSignature();//方法签名
        joinPoint.getArgs();//方法参数
    }
}
```

	> **注意: 前置通知和后置通知都没有返回值,方法参数都为joinpoint**

###### 	12.2.5 环绕切面

```java
@Aspect
@Component
public class MyAspect {
    @Around("execution(* com.baizhi.service.*.*(..))")
    public Object before(ProceedingJoinPoint proceedingJoinPoint) throws Throwable {
        System.out.println("进入环绕通知");
        proceedingJoinPoint.getTarget();//目标对象
        proceedingJoinPoint.getSignature();//方法签名
        proceedingJoinPoint.getArgs();//方法参数
        Object proceed = proceedingJoinPoint.proceed();//放行执行目标方法
        System.out.println("目标方法执行之后回到环绕通知");
        return proceed;//返回目标方法返回值
    }
}
```

> **`注意: 环绕通知存在返回值,参数为ProceedingJoinPoint,如果执行放行,不会执行目标方法,一旦放行必须将目标方法的返回值返回,否则调用者无法接受返回数据`**

---

## 13. 文件上传下载

##### 13.1 文件上传

###### 	13.1.1 准备上传页面

```html
<form action="路径...." method="post" enctype="multipart/form-data">
        <input type="file" name="aa">
        <input type="submit" value="上传">
</form>
<!--
	1. 表单提交方式必须是post
	2. 表单的enctype属性必须为multipart/form-data
	3. 后台接受变量名字要与文件选择name属性一致
-->
```

###### 	13.1.2 编写控制器

```java
@Controller
@RequestMapping("/file")
public class FileController {
  @RequestMapping("/upload")
  public String upload(MultipartFile aa, HttpServletRequest request) throws IOException {
        String realPath = request.getRealPath("/upload");
        aa.transferTo(new File(realPath,aa.getOriginalFilename()));//文件上传
        return "index";
  }
}
```

###### 	13.1.3 修改文件上传大小

```yaml

#上传时出现如下异常:  上传文件的大小超出默认配置  默认10M
nested exception is java.lang.IllegalStateException: org.apache.tomcat.util.http.fileupload.FileUploadBase$SizeLimitExceededException: the request was rejected because its size (38443713) exceeds the configured maximum (10485760)
#修改上传文件大小:
spring:
  http:
    multipart:
       max-request-size: 209715200  #用来控制文件上传大小的限制
       max-file-size: 209715200 #用来指定服务端最大文件大小   
```



##### 	13.2 文件下载

###### 		13.2.1 提供下载文件链接

```html
<a href="../file/download?fileName=corejava.txt">corejava.txt</a>
```

###### 		13.2.2 开发控制器

```java
@RequestMapping("/download")
public void download(String fileName, HttpServletRequest request, HttpServletResponse response) throws Exception {
        String realPath = request.getRealPath("/upload");
        FileInputStream is = new FileInputStream(new File(realPath, fileName));
        ServletOutputStream os = response.getOutputStream();
        response.setHeader("content-disposition","attachment;fileName="+ URLEncoder.encode(fileName,"UTF-8"));
        IOUtils.copy(is,os);
        IOUtils.closeQuietly(is);
        IOUtils.closeQuietly(os);
    }
```

---

## 14. 拦截器

##### 	14.1 开发拦截器

```java
public class MyInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object o) throws Exception {
        System.out.println("======1=====");
        return true;//返回true 放行  返回false阻止
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object o, ModelAndView modelAndView) throws Exception {
        System.out.println("=====2=====");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object o, Exception e) throws Exception {
        System.out.println("=====3=====");
    }
}
```

##### 	14.2 配置拦截器

```java
@Component
public class InterceptorConfig extends WebMvcConfigurerAdapter {
    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        //添加拦截器
        registry.addInterceptor(new MyInterceptor())
            .addPathPatterns("/**")//定义拦截路径
            .excludePathPatterns("/hello/**"); //排除拦截路径
    }
}
```

------

## 15. war包部署

##### 	15.1 设置打包方式为war

> ​	**<packaging>war</packaging>**

##### 	15.2 在插件中指定入口类

```xml
<build>
	<plugins>
      <plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
        <!--使用热部署出现中文乱码解决方案-->
        <configuration>
          <fork>true</fork>
          <!--增加jvm参数-->
          <jvmArguments>-Dfile.encoding=UTF-8</jvmArguments>
          <!--指定入口类-->
          <mainClass>com.baizhi.Application</mainClass>
        </configuration>
      </plugin>
    </plugins>
</build>	
```

##### 	15.3 排除内嵌的tomcat

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-tomcat</artifactId>
  <scope>provided</scope>   <!--去掉内嵌tomcat-->
</dependency>

<dependency>
  <groupId>org.apache.tomcat.embed</groupId>
  <artifactId>tomcat-embed-jasper</artifactId>
  <scope>provided</scope>  <!--去掉使用内嵌tomcat解析jsp-->
</dependency>
```

##### 	15.4 配置入口类

```java
//1.继承SpringBootServletInitializer
//2.覆盖configure方法
public class Application extends SpringBootServletInitializer{
    public static void main(String[] args) {
        SpringApplication.run(Application.class,args);
    }
    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
        return builder.sources(Application.class);
    }
}
```

##### 	15.5 打包测试

```java
/* 一旦使用war包部署注意:
	1. application.yml 中配置port context-path 失效
	2. 访问时使用打成war包的名字和外部tomcat端口号进行访问项目
*/
```



