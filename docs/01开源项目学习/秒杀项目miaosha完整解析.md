# 项目简介

### 摘要

本项目是使用Redis作为缓存的一个秒杀项目实例。项目中大量使用了redis的多张数据接口，并使用了redis作为mq实现秒杀流量的削峰填谷等操作。

## 项目信息

git链接：[gitee.com/1028125449/…](https://gitee.com/1028125449/miaosha)

作者：kater

### 首页截图

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200925/e97bdb7257854cc1a804e4ec1e2c9ce0.png)

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200925/bb2c219fd2df49278b886e3112d85660.png)

### 后台截图

### 重点功能截图

# 代码结构

```
└─wang
    └─moshu
        ├─cache
        │  │  GoodsBuyCurrentLimiter.java #限流器
        │  │  GoodsInfoCacheWorker.java #商品信息缓存
        │  │  GoodsRedisStoreCache.java #商品库存缓存
        │  │  MiaoshaFinishCache.java #秒杀结束标识缓存
        │  │  MiaoshaHandlingListCache.java #秒杀请求队列缓存
        │  │  MiaoshaSuccessTokenCache.java #秒杀下单token缓存器
        │  │  UserBlackListCache.java #用户黑名单列表缓存
        │  │
        │  ├─base
        │  │      CacheWorker.java  #缓存工具类
        │  │      CurrentLimiter.java #限流操作类
        │  │
        │  └─model
        │          MiaoshaSuccessToken.java  #秒杀成功生成的token
        │
        ├─config
        │      SystemConfig.java #系统初始化一下配置
        │
        ├─constant
        │      CommonConstant.java 
        │      MessageType.java
        │
        ├─controller
        │      MiaoshaInterface.java #秒杀相关接口
        │      MiaoshaPage.java #秒杀相关页面控制器
        │
        ├─dao
        │      GoodsMapper.java
        │      OrderMapper.java
        │
        ├─intercept
        │      IPInterceptor.java #恶意ip监测拦截器
        │      UserInterceptor.java #恶意用户监测拦截器
        │
        ├─model
        │      Goods.java
        │      Order.java
        │
        ├─mq
        │  ├─handler
        │  │      MiaoshaRequestHandler.java #秒杀请求消息队列处理器
        │  │
        │  └─message
        │          MiaoshaRequestMessage.java #秒杀队列消息模型
        │
        ├─service
        │      GoodsService.java
        │
        ├─task
        │      GoodsRedisStoreInitTask.java #商品库存初始化定时器
        │      GoodsTokenExpireClearTask.java #秒杀token过期定时处理器
        │
        └─util
                ConvertUtil.java
                IPUtil.java
                JedisBenchmark.java
                PoolBenchmark.java
                RedisUtil.java
                RedisUtilBenchmark.java
                SpringBeanUtils.java
复制代码
```

# 基本介绍

## 技术栈

### 前端

- jsp
- ajax
- countdown定时器

### 后端

- redis
- mybatis
- 存储过程
- 消息队列

## 项目启动步骤

- 导入sql文件
- 修改数据库连接配置的账号密码
- redis使用密码

## 学习重点（学习目的）

- redis的多种数据结构运用
- 秒杀场景的处理
- 消息队列的使用

## 功能大纲

秒杀、下单

# 模块分析

分析3-4个主要模块

## 秒杀分析

秒杀场景一般会在电商网站举行一些活动或者节假日在12306网站上抢票时遇到。对于电商网站中一些稀缺或者特价商品，电商网站一般会在约定时间点对其进行限量销售，因为这些商品的特殊性，会吸引大量用户前来抢购，并且会在约定的时间点同时在秒杀页面进行抢购。

### 1、秒杀系统场景特点

**瞬时并发量大**

- 秒杀时大量用户会在同一时间同时进行抢购，网站瞬时访问流量激增。

**库存量少**

- 秒杀一般是访问请求数量远远大于库存数量，只有少部分用户能够秒杀成功。

**业务简单**

- 秒杀业务流程比较简单，一般就是下订单减库存。

### 2、秒杀项目设计要点

**限流：**鉴于只有少部分用户能够秒杀成功，所以要限制大部分流量，只允许少部分流量进入服务后端。

**削峰：**对于秒杀系统瞬时会有大量用户涌入，所以在抢购一开始会有很高的瞬间峰值。高峰值流量是压垮系统很重要的原因，所以如何把瞬间的高流量变成一段时间平稳的流量也是设计秒杀系统很重要的思路。实现削峰的常用的方法有利用缓存和消息中间件等技术。

**异步处理：**秒杀系统是一个高并发系统，采用异步处理模式可以极大地提高系统并发量，其实异步处理就是削峰的一种实现方式。

**内存缓存：**秒杀系统最大的瓶颈一般都是数据库读写，由于数据库读写属于磁盘IO，性能很低，如果能够把部分数据或业务逻辑转移到内存缓存，效率会有极大地提升。

**可拓展：**当然如果我们想支持更多用户，更大的并发，最好就将系统设计成弹性可拓展的，如果流量来了，拓展机器就好了。像淘宝、京东等双十一活动时会增加大量机器应对交易高峰。

### 3、设计难点要点

- 对现有业务冲击
- 高并发应用负载高
- 突然增加网络与服务宽带
- 直接下单
- 控制商品页面购买按钮点亮
- 下单前置检查

### 4、优化方向

- **前端：**

**页面静态化\****：**将活动页面上的所有可以静态的元素全部静态化，并尽量减少动态元素。通过CDN来抗峰值。

**禁止重复提交\****：**用户提交之后按钮置灰，禁止重复提交。

- **服务端：**

**（1）将请求尽量拦截在系统上游** （不要让锁冲突落到数据库上去）。传统秒杀系统之所以挂，请求都压倒了后端数据层，数据读写锁冲突严重，并发高响应慢，几乎所有请求都超时，流量虽大，下单成功的有效流量甚小。以12306为例，一趟火车其实只有2000张票，200w个人来买，基本没有人能买成功，请求有效率为0。

**（2）充分利用缓存** ，秒杀买票，这是一个典型的读多写少的应用场景，大部分请求是车次查询，票查询，下单和支付才是写请求。一趟火车其实只有2000张票，200w个人来买，最多2000个人下单成功，其他人都是查询库存，写比例只有0.1%，读比例占99.9%，非常适合使用缓存来优化。

**（3）消息队列：** 消息队列可以削峰，将拦截大量并发请求，这也是一个异步处理过程，后台业务根据自己的处理能力，从消息队列中主动的拉取请求消息进行业务处理。

**（4）用户限流：** 在某一时间段内只允许用户提交一次请求，比如可以采取IP限流。

- **数据库层：**

数据库层是最脆弱的一层，一般在应用设计时在上游就需要把请求拦截掉，数据库层只承担“能力范围内”的访问请求。所以，上面通过在服务层引入队列和缓存，让最底层的数据库高枕无忧。

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200925/48205b9cc59c4415b7d7abb8bc4da03b.png)

（秒杀项目参考逻辑）

## 秒杀逻辑分析

### 处理逻辑

![图片](https:////image-1300566513.cos.ap-guangzhou.myqcloud.com/upload/images/20200925/3dfe1e48203c421a854d5a858af94692.png)

（总流程时序图）

[秒杀设计时序图.puml](https://attachments-cdn.shimo.im/o6YihumJrr8jGhCT/秒杀设计时序图.puml)

1. 秒杀详情页，等待秒杀开始
2. 秒杀开始，获取秒杀链接
3. 进入秒杀，限流，判断是否重复秒杀，把请求消息推入redis消息处理队列
4. 消息处理器监听到消息后开始处理：
   1. 监测黑名单
   2. 判断秒杀是否已结束
   3. 先减redis库存（占位）
   4. 生成下单token，存入redis供前端查询
5. 前端查询秒杀结果
   1. 成功：显示下单按钮，用户使用token去下单
6. 用户下单
7. 检查token有效性，检查库存
8. 减库存，下单。（真正减库存）

拦截器：

- 恶意IP检测拦截器
  - 获取真实ip
  - 匹配ip是否是正常ip，是否在黑名单库
  - 使用redis增加ip的访问次数
  - 超过限定次数就加入到黑名单库
- 恶意用户检测拦截器
  - 同ip监测拦截

### 数据预处理

商品库存信息预先生成，服务器启动时加载。

### 请求过滤

入口只有活动开启前才能获得

入口恶意用户检测：多秒内多少次请求---可以记录最近10次请求时间，和前第九次请求时间对比

### 实时限流器

- 实时限流：限制正在处理的请求量（通过消息队列获取正在处理的请求数目）为库存的100倍请求（这个可自定义）；
- 如果出现了限流器满了，但仍然有库存的情况怎么办？直接拒绝请求，允许用户重新提交请求 ##请求减库存
- 请求通过了过滤之后，交给消息队列减库存+下单 ##消息队列处理
- 消息队列再次过滤请求是否是恶意的用户
- 否则，执行减库存+下单

## 限流处理

限制用户维度访问频率

## 需要考虑的恶意行为

- ip黑名单
- 用户黑名单

## redis的运用

Redis是一个分布式缓存系统，支持多种数据结构，我们可以利用Redis轻松实现一个强大的秒杀系统。作为缓存和消息队列使用

### 分析

Redis incr 可以实现原子性的递增，可应用于高并发的秒杀活动、分布式序列号生成等场景。

Redis丰富的数据结构适用于多种场景，如消息队列。

### redis消息队列

message-trunk是以redis为基础搭建的轻量级高性能消息总线（队列），和主流MQ相比使用起来更灵巧简便。

git地址：[gitee.com/1028125449/…](https://gitee.com/1028125449/message-trunk)

使用方法：

- 获取消息队列全局对象MessageTrunk（可以用spring注入），put入消息即可。

```
// 获取MessageTrunk实例
MessageTrunk mt = (MessageTrunk) SpringBeanUtils.getBean("messageTrunk");
Message<DemoMessage> message = new Message<DemoMessage>(MessageType.DEMO_MESSAGE, new DemoMessage(value));
// 消息入MT
mt.put(message);
复制代码
```

- 消息处理器：继承AbstarctMessageHandler抽象类。

```
public class DemoHandler extends AbstarctMessageHandler<DemoMessage>{
 
 private static Log logger = LogFactory.getLog(DemoHandler.class);
 public DemoHandler(){
  // 说明该handler监控的消息类型
  super(MessageType.DEMO_MESSAGE);
 }
 /**
  * 监听到消息后处理方法
  */
 @Override
 public void handle(DemoMessage message){
        // do handle
 }
 @Override
 public void handleFailed(DemoMessage obj){
  // handle failed
 }
}
复制代码
```

### 数据结构

- 哈希
  - 存储黑名单（ip，用户）
  - 秒杀处理请求列表
- 字符串
  - 增减库存
  - 商品描述是否结束标志
  - 下单token
  - ...
- 列表
  - 用户访问记录

## MySQL的存储过程

我们常用的操作数据库语言	SQL	语句在执行的时候需要要先编译，然后执行，而存储过程（	Stored Procedure	）是一组为了完成特定功能的	SQL	语句集，经编译后存储在数据库中，用户通过指定存储过程的名字并给定参数（如果该存储过程带有参数）来调用执行它。

```
FOUND_ROWS : 获取上一个select语句查询到的行数；
ROW_COUNT : 获取上一条update， insert ，delete 影响的行数；
复制代码
```

MySQL存储过程创建的格式：CREATE PROCEDURE 过程名 ([过程参数	[,...]]) [特性 ...] 过程体

mysql> DELIMITER //

mysql> CREATE PROCEDURE proc1(OUT s int)

-> BEGIN

-> SELECT COUNT(*) INTO s FROM user;

-> END

-> //

mysql> DELIMITER ;

用call和你过程名以及一个括号，括号里面根据需要，加入参数，参数包括输入参数、输出参数、输入输出参数。

**参数：**

IN 输入参数:表示该参数的值必须在调用存储过程时指定，在存储过程中修改该参数的值不能被返回，为默认值

OUT 输出参数:该值可在存储过程内部被改变，并可返回

INOUT 输入输出参数:调用时指定，并且可被改变和返回

存储过程通常有以下优点：

**(1).存储过程增强了SQL语言的功能和灵活性**。存储过程可以用流控制语句编写，有很强的灵活性，可以完成复杂的判断和较复杂的运算。

**(2).存储过程允许标准组件是编程**。存储过程被创建后，可以在程序中被多次调用，而不必重新编写该存储过程的SQL语句。而且数据库专业人员可以随时对存储过程进行修改，对应用程序源代码毫无影响。

**(3).存储过程能实现较快的执行速度**。如果某一操作包含大量的Transaction-SQL代码或分别被多次执行，那么存储过程要比批处理的执行速度快很多。因为存储过程是预编译的。在首次运行一个存储过程时查询，优化器对其进行分析优化，并且给出最终被存储在系统表中的执行计划。而批处理的Transaction-SQL语句在每次运行时都要进行编译和优化，速度相对要慢一些。

**(4).存储过程能过减少网络流量**。针对同一个数据库对象的操作（如查询、修改），如果这一操作所涉及的Transaction-SQL语句被组织程存储过程，那么当在客户计算机上调用该存储过程时，网络中传送的只是该调用语句，从而大大增加了网络流量并降低了网络负载。

**(5).存储过程可被作为一种安全机制来充分利用**。系统管理员通过执行某一存储过程的权限进行限制，能够实现对相应的数据的访问权限的限制，避免了非授权用户对数据的访问，保证了数据的安全。

# 总结

学好秒杀，多学会使用消息队列，限流等思想.


作者：MarkerHub
链接：https://juejin.im/post/6876312532965916679
来源：掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。