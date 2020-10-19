#### 小Hub领读：

讲解视频也同步发布啦，记得去看哈，一键三连哇。

视频讲解：www.bilibili.com/video/bv1SD…

这系统，一定要学会用户-服务认证，服务-服务鉴权的那一套，这才算学会。

------

## 简介

Cloud-Platform是国内首个基于Spring Cloud微服务化开发平台，具有统一授权、认证后台管理系统，其中包含具备用户管理、资源权限管理、网关API 管理等多个模块，支持多业务系统并行开发，可以作为后端服务的开发脚手架。代码简洁，架构清晰，适合学习和直接项目中使用。 核心技术采用Spring Boot 2.1.2以及Spring Cloud (Greenwich.RELEASE) 相关核心组件，采用Nacos注册和配置中心，集成流量卫兵Sentinel，前端采用vue-element-admin组件，Elastic Search自行集成。

B站视频讲解：

**ps：注意本文讲解是基于Cloud-Platform v2.5版本，不是最新版本！**

## 技术选型

前端：vue-element-admin

后端：springcloud（eureka、gateway、admin、sidecar、Hystrix、feign、ribbon、zipkin）、tk+mybatis、lucene、jwt、rest

## 项目结构

```
ace-security
  ace-modules--------------公共服务模块（基础系统、搜索、OSS）
  ace-auth-----------------服务鉴权中心
  ace-gate-----------------网关负载中心
  ace-common---------------通用脚手架
  ace-control--------------运维中心（监控、链路）
  ace-sidebar--------------调用第三方语言服务  
复制代码
```

## 项目启动

***须知：\*** 因为Cloud-Platform是一个前后端分离的项目，所以后端的服务必须先启动，在后端服务启动完成后，再启动前端的工程。

### 环境

- mysql，redis，maven
- jdk1.8
- IDE插件一个，lombok插件，具体百度即可
- node

### 前端

git链接：[gitee.com/geek_qi/clo…](https://gitee.com/geek_qi/cloud-platform-ui)

- 先clone到本地，并进入cloud-platform-ui目录打开命令行窗口（cmd）
- 因为涉及node.js，所以需要安装npm，node等环境

node.js安装教程：[nodejs.cn/download/](http://nodejs.cn/download/)下载msi版本安装。

安装之后，命令行窗口，表示安装成功。

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200924/935f2f6008ce4c658f2d8d9670804737.png)

给项目打包依赖

```
# 1、安装淘宝镜像依赖
npm install -g cnpm --registry=https://registry.npm.taobao.org
# 2、安装项目依赖
cnpm install
# 启动服务
npm run dev
复制代码
```

启动成功后会自动打开链接：http://localhost:9527/

### 后端

首先clone项目下来（v2.5版本）：[gitee.com/geek_qi/clo…](https://gitee.com/geek_qi/cloud-platform/tree/v2.5/)

导入到idea中，然后导入数据库sql：

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200924/f8b8e394e83e43d8a0c9f1cc2d0f86b6.png)

修改数据库的账号密码（直接ctrl+shirt+r，搜索datasource:，可以很方便修改）：

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200924/95dcfeadc561430cb98ab07a7c5bedb9.png)

接下来启动redis，然后安装顺序启动我们的服务

```
# 启动顺序
CenterBootstrap -> AuthBootstrap -> AdminBootstrap -> GatewayServerBootstrap
复制代码
```

其他监控或服务可以先不启动。

## 服务说明

### ace-auth-server

关键类：

- AuthController
  - /jwt开头的控制器，登录、刷新、校验jwt
  - 网关不拦截这个链接的请求
- ClientController
  - 对外暴露的接口，可通过客户端的id和密钥获取到对应的授权相关资源
- ServiceController
  - 后台管理系统服务管理模块接口
- ClientTokenInterceptor
  - 拦截feign接口发起的请求，并自动添加请求头token
- ServiceAuthRestInterceptor
  - 拦截的url为/service/**（WebConfiguration）
  - 服务之间的调用鉴权
  - 一般feign、或者restTemplate方式调用
- UserAuthRestInterceptor
  - 拦截的url为/service/**（WebConfiguration）
  - 获取用户的token并解析，为会话上下文添加用户信息（ThreadLocal）
- OkHttpTokenInterceptor
  - 拦截所有的feign请求，OkHttp重写请求
  - OkHttp3一个强有力的机制，能够监控，重写以及重试（请求的）调用

## 模块分析

![图片](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="800" height="600"></svg>)

### 用户授权

首先我们来弄清楚一下登录的流程，登录中和之后发生了什么事，那么我们打开前段登录页面，按下F12，然后点击登录，可以查看到以下几个动作：

- 点击登录，提交表单：http://localhost:9527/api/auth/jwt/token

```
#返回值
{"status":200,"data":"eyJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJhZG1pbiIsInVzZXJJZCI6IjEiLCJuYW1lIjoiTXIuQUciLCJleHAiOjE1NjE0NDEyNTZ9.tXNw8nhAFmI4QIQDpKy4DzWtJSTpfwD4685JqbA2pGScdyfXt_5DDs_r1gVZA4CwQC4oZxBsmLKZGclTLGc4HKeXlP2PiVoHZfSWymFRLNfvFqOzKUETJ6WpyDqK55yjf1wddTBD3VzSFvY49uunvozEcb2oFjOs3M_I2sgxAAU","rel":false}
复制代码
```

可以看到登录成功之后返回的是一个jwt的token值，应该就是标识用户身份用的token。

- ajax发起请求获取用户信息以及菜单列表等：http://localhost:9527/api/admin/user/front/info?token=eyJhbGciOiJSUzI1NiJ9.eyJzdWIiOiJhZG1pbiIsInVzZXJJZCI6IjEiLCJuYW1lIjoiTXIuQUciLCJleHAiOjE1NjE0NDEyNTZ9.tXNw8nhAFmI4QIQDpKy4DzWtJSTpfwD4685JqbA2pGScdyfXt_5DDs_r1gVZA4CwQC4oZxBsmLKZGclTLGc4HKeXlP2PiVoHZfSWymFRLNfvFqOzKUETJ6WpyDqK55yjf1wddTBD3VzSFvY49uunvozEcb2oFjOs3M_I2sgxAAU

```
# 返回值
{"id":"1","username":"admin","name":"Mr.AG","description":"","menus":[{"code":"userManager","type":"menu","uri":"/admin/user","method":"GET","name":"访问","menu":"用户管理"},{"code":"baseManager","type":"menu","uri":"/admin","method":"GET","name":"访问","menu":"基础配置管理"},
.....(此次删除了部分),{"code":"serviceManager:btn_clientManager","type":"button","uri":"/auth/service/{*}/client","method":"POST","name":"服务授权","menu":"服务管理"}]}
复制代码
```

同时注意请求头的信息：带有刚才登录后的jwt token，名称叫Authorization，以后的所有请求都会带上这个Authorization用于标识用户身份。 ![图片](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="800" height="600"></svg>)

接下来我们来走下这个过程：

- 客户端点击按钮发起登录请求http://localhost:9527/api/auth/jwt/token
  - 到达网关gate首先经过我们的过滤器AccessGatewayFilter
    - 获取请求uri，method
    - 判断是否是不拦截地址
    - 刚好我们发现不拦截地址中有这个配置：gate: ignore: startWith: /auth/jwt
    - 所以网关过滤器直接将请求代理到ace-auth服务
- 网关ace-gateway-v2的代理以及过滤配置

```
 # 网关代理规则
 spring:
   cloud:
      gateway:
        locator:
          enabled: true
        routes:
        # =====================================
        - id: ace-auth
          uri: lb://ace-auth
          order: 8000
          predicates:
          - Path=/api/auth/**
          filters:
          - StripPrefix=2
        - id: ace-admin
          uri: lb://ace-admin
          order: 8001
          predicates:
          - Path=/api/admin/**
          filters:
          - StripPrefix=2
gate:
  ignore:
    startWith: /auth/jwt
复制代码
```

那么我们进入ace-auth中找到对应controller 可以找到这里：

```
@RestController
@RequestMapping("jwt")
@Slf4j
public class AuthController {    @RequestMapping(value = "token", method = RequestMethod.POST)
    public ObjectRestResponse<String> createAuthenticationToken(
            @RequestBody JwtAuthenticationRequest authenticationRequest) throws Exception {
        log.info(authenticationRequest.getUsername()+" require logging...");
        final String token = authService.login(authenticationRequest);
        return new ObjectRestResponse<>().data(token);
    }
}
复制代码
```

这个方法里面只有一个方法就是authService.login，点这个方法进去发现里面又有个方法是**userService**.validate，这是一个feign接口

```
@FeignClient(value = "ace-admin",configuration = FeignConfiguration.class)
public interface IUserService {  @RequestMapping(value = "/api/user/validate", method = RequestMethod.POST)
  public UserInfo validate(@RequestBody JwtAuthenticationRequest authenticationRequest);
复制代码
```

}可以看到这是远程调用，那么接下来，我们看看远程调用的过程，这设计到服务间的相互鉴权

### 服务间鉴权

上面的**userService**.validate，类上有这样的注解

```
@FeignClient(value = "ace-admin",configuration = FeignConfiguration.class)
表示声明式调用ace-admin服务，接下来我们解析一下这个过程发生了什么事情，我们可以看到有个configuration = FeignConfiguration.class，我们打开FeignConfiguration
@Configuration
public class FeignConfiguration {
    @Bean
    ClientTokenInterceptor getClientTokenInterceptor(){
        return new ClientTokenInterceptor();
    }
}
复制代码
```

再打开ClientTokenInterceptor ：

```
public class ClientTokenInterceptor implements RequestInterceptor {
    private Logger logger = LoggerFactory.getLogger(ClientTokenInterceptor.class);
    @Autowired
    private ClientConfiguration clientConfiguration;
    @Autowired
    private AuthClientService authClientService;    @Override
    public void apply(RequestTemplate requestTemplate) {
        logger.info("----> 为feign调用添加token头");
        try {
            requestTemplate.header(clientConfiguration.getClientTokenHeader(), authClientService.apply(clientConfiguration.getClientId(), clientConfiguration.getClientSecret()));
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
从上面的配置我们知道，RequestInterceptor 是feign接口下的包装拦截器，从代码里面看到，其实意思就是在feign发起远程调用时候往请求里添加请求头信息（clientToken），所以发起的请求头中就有了当前服务的身份token，接受端的服务器就能根据token辨别来源服务器的身份。

复制代码
```

接下来我们看看接收端怎么辨别的。ServiceAuthRestInterceptor

```
public class ServiceAuthRestInterceptor extends HandlerInterceptorAdapter {
    private Logger logger = LoggerFactory.getLogger(ServiceAuthRestInterceptor.class);    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {        logger.info("------>判断服务A是否有权限访问当前服务B ~");
        HandlerMethod handlerMethod = (HandlerMethod) handler;
        // 配置该注解，说明不进行服务拦截
        IgnoreClientToken annotation = handlerMethod.getBeanType().getAnnotation(IgnoreClientToken.class);
        if (annotation == null) {
            annotation = handlerMethod.getMethodAnnotation(IgnoreClientToken.class);
        }
        if(annotation!=null) {
            return super.preHandle(request, response, handler);
        }        String token = request.getHeader(serviceAuthConfig.getTokenHeader());
        IJWTInfo infoFromToken = serviceAuthUtil.getInfoFromToken(token);
        String uniqueName = infoFromToken.getUniqueName();
        for(String client:serviceAuthUtil.getAllowedClient()){ //ace-auth、ace-gate
            if(client.equals(uniqueName)){
                return super.preHandle(request, response, handler);
            }
        }
        throw new ClientForbiddenException("Client is Forbidden!");
    }
}
复制代码
```

从代码看到首先看下有没IgnoreClientToken的注解，有的话就跳过。没有的话继续获取调用端服务器的token，然后再去获取当前服务器允许访问的lient（**serviceAuthUtil**.getAllowedClient()），然后匹配调用端的名称是否在允许的客户端内，如果允许就继续，不允许就forbidden。所以挺清晰的。 那这套客户端和允许的访问的客户端这套关系是哪里维护的呢，其实有两张表

![图片](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="800" height="600"></svg>)

- auth_client ：客户端的id和名称等
- auth_client_service： 服务端允许调用的客户端关联表

从这张表中，我们就可以得出哪些允许被访问，哪些不能被访问了

### ![图片](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="800" height="600"></svg>)

cloud-platform鉴权逻辑.png

![图片](data:image/svg+xml;utf8,<?xml version="1.0"?><svg xmlns="http://www.w3.org/2000/svg" version="1.1" width="800" height="600"></svg>)

服务间调用优化.png

## 总结

第一件事

- 新建所有需要用到的模块，基本搭建好框架
- 做好增删改查的封装、接口规范
- 全局异常捕捉封装
- 单元测试
- 通用工具类

第二件事

- 决定服务的授权模式（jwt、oauth2等）

第三件事

- 服务内部鉴权
- 权限控制

------

（完）

视频讲解：www.bilibili.com/video/bv1SD…


作者：MarkerHub
链接：https://juejin.im/post/6875998121802301453
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。