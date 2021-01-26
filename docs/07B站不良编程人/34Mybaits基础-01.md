# 预热

- 安装maven环境以及环境配置
- 进入mybatis基础课程部分学习
- mybatis基本介绍 mybatis入门环境
- mybatis实现数据库CRUD
- mybatis中动态sql
- mybatis关联关系
- mybatis中resultType resultMap却别以及使用场景
- mybatis中缓存

-------

## idea中maven配置

```markdown
# 1.配置maven工具
-  在idea中打开如下位置: Preferences | Build, Execution, Deployment | Build Tools | Maven
-  按照如下配置
```

![image-20201221195626631](笔记.assets/image-20201221195626631.png)

```markdown
# 2.配置maven阿里云镜像加速
```

```xml
<mirror>
  <id>nexus-aliyun</id>
  <mirrorOf>*</mirrorOf>
  <name>Nexus aliyun</name>
  <url>http://maven.aliyun.com/nexus/content/groups/public</url>
</mirror> 
```

![image-20201221195956929](笔记.assets/image-20201221195956929.png)

----

## Mybatis 

### 1.mybatis引言

```markdown
# 1.什么是mybatis
-  定义: mybatis使用来完成数据库操作的半ORM框架 	官方定义:MyBatis 是一款优秀的持久层(mysql,oracle)框架
 		(Hibernate ORM框架) ==> 表t_user(id,name)  			java对象转化 User id name 
		ORM: Object Relationship  Mapping  对象关系映射  
		半ORM: mybatis 中自己在mapper配置文件中自己书写字段和对象属性映射关系

-  作用: 用来操作数据库 mysql oracle sqlServer等,解决原始jdbc编程技术中代码冗余,方便访问数据
```

### 2.第一个入门环境

```markdown
# 1.创建maven项目
```

![image-20201221201416262](笔记.assets/image-20201221201416262.png)

```markdown
# 2.项目中引入mybatis依赖
```

```xml
<!--mybatis依赖-->
<dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis</artifactId>
  <version>3.4.6</version>
</dependency>

<!--引入mysql驱动jar-->
<dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>5.1.38</version>
</dependency>
```

```markdown
# 3.mybatis的主配置文件
- 主配置文件:核心配置文件 作用:用来创建sqlSessionFactory对象
```

```xml
<configuration>
    <!--环境操作那个数据库 environments 环境复数 prod dev test ...-->
    <environments default="prod">
        <!--生产环境-->
        <environment id="prod">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybatis"/>
                <property name="username" value="root"/>
                <property name="password" value="root"/>
            </dataSource>
        </environment>
    </environments>
</configuration>
```

```markdown
# 4.获取sqlSession
```

```java
 //读取mybatis-config.xml
InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
//创建mybatis核心对象SqlSessionFactory
SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
//获取sqlSession
SqlSession sqlSession = sqlSessionFactory.openSession();
System.out.println(sqlSession);
```

```markdown
# 5.建表
```

```sql
CREATE TABLE `t_user` (
  `id` int(6) NOT NULL AUTO_INCREMENT,
  `name` varchar(40) DEFAULT NULL,
  `age` int(3) DEFAULT NULL,
  `bir` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

```markdown
# 6.实体对象 entity(实体) model(模型)  com.baizhi.entity  com.baizhi.model
```

```java
public class User {
    private Integer id;
    private String name;
    private Integer age;
    private Date bir;
  	//get set 有参数构造 无参数构造省略  toString省略
}
```

```markdown
# 7.开发DAO接口
- 注意: mybatis要求接口中不能定义方法的重载
```

```java
public interface UserDAO {
    //保存用户
    int save(User user);
}
```

```markdown
# 8.开发Mapper配置文件
- 注意: 在mybatis中一个DAO接口对应一个Mapper配置文件 idea中建立配置文件目录使用/
```

```xml
<!--
    namespace属性: 命名空间 用来书写当前mapper文件是对那个DAO接口的实现
    全限定名: 包.类
-->
<mapper namespace="com.baizhi.dao.UserDAO">
    <!--保存
        insert:插入操作
        id: 方法名
        parameterType:参数类型 包.类
        注意:1.insert标签内部写sql语句
            2.#{对象中属性名}
    -->
    <insert id="save" parameterType="com.baizhi.entity.User">
        insert into t_user values (#{id},#{name},#{age},#{bir})
    </insert>

</mapper>
```

```markdown
# 9.将mapper注册到mybatis-config.xml配置文件中
```

```xml
<!--注册项目中mapper.xml配置-->
<mappers>
  <mapper resource="com/baizhi/mapper/UserDAO.xml"/>
</mappers>
```

```markdown
# 10.测试UserDAO
```

```java
public static void main(String[] args) throws IOException {
        //读取mybatis-config.xml
        InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
        //创建mybatis核心对象SqlSessionFactory
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        //获取sqlSession
        SqlSession sqlSession = sqlSessionFactory.openSession();
        //获取DAO对象
        UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
        try {
            User user = new User();
            user.setId(1);
            user.setName("xiaochen");
            user.setAge(23);
            user.setBir(new Date());
            int count = userDAO.save(user);
            System.out.println("影响的条数: " + count);
            sqlSession.commit();//提交事务
        } catch (Exception e) {
            e.printStackTrace();
            sqlSession.rollback();//提交事务
        } finally {
            sqlSession.close();//释放资源
        }
    }
```

---

### mybatis执行过程中数据库乱码问题

```markdown
# 1.为什么会出现乱码?
- java中的编码在通过不同操作系统底层传递过程中由于和操作系统的编码不一致就会出现乱码
# 2.解决方案
```

```xml
<property name="url" value="jdbc:mysql://localhost:3306/mybatis?characterEncoding=utf-8"/>
```

![image-20201221205631455](笔记.assets/image-20201221205631455.png)

----

### mybatis中插入如何返回数据库自动生成id

```java
 UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
try {
  User user = new User();
  //user.setId(1);//不设置id使用数据库自动生成id
  user.setName("小王");
  user.setAge(23);
  user.setBir(new Date());
  int count = userDAO.save(user);
  System.out.println("影响的条数: " + count);
  //数据当前保存这条记录id
  System.out.println("本次数据库生成id: "+user.getId());
  sqlSession.commit();//提交事务
} catch (Exception e) {
  e.printStackTrace();
  sqlSession.rollback();//提交事务
} finally {
  sqlSession.close();//释放资源
}
```

![image-20201221210310912](笔记.assets/image-20201221210310912.png)

![image-20201221210245916](笔记.assets/image-20201221210245916.png)

-----

