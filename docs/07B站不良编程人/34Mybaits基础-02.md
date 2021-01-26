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

#### 2.1 mybatis执行过程中数据库乱码问题

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

#### 2.2 mybatis中插入如何返回数据库自动生成id

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

### 3.Mybatis中CRUD

#### 3.1 记录更新操作

```java
public interface UserDAO {
	//更新方法
	int update(User user);
}
```

```xml
 <!--更新方法-->
<update id="update" parameterType="com.baizhi.entity.User">
  update t_user
  <set><!--set标签动态去掉 赋值语句前后多余, -->
    <!--test里面属性name为对象的属性名-->
    <if test="name!=null and name!=''">
      name=#{name},
    </if>
    <if test="age!=null">
      age=#{age},
    </if>
    <if test="bir!=null">
      bir=#{bir}
    </if>
  </set>
  where id = #{id}
</update>
```

```java
//更新操作
@Test
public void update() throws IOException {
  //读取配置文件
  InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
  //创建sqlSessionFactory
  SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
  //获取sqlSession 执行sql语句
  SqlSession sqlSession = sqlSessionFactory.openSession();
  try {
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    //更新数据
    // 更新: 有值更新 不存在值保留原始的值  1.先查再改  2.动态sql
    User user = new User();
    user.setId(1);
    user.setName("小张");
    user.setAge(26);
    int update = userDAO.update(user);
    System.out.println("修改的条数:" +update);
    sqlSession.commit();//提交
  } catch (Exception e) {
    e.printStackTrace();
    sqlSession.rollback();
  } finally {
    sqlSession.close();
  }

}
```

---

#### 3.2 删除操作

```java
//删除方法
int delete(Integer id);
```

```xml
<!--删除方法-->
<delete id="delete" parameterType="Integer">
  delete from t_user where id=#{id}
</delete>
```

```java
//删除操作
@Test
public void delete() throws IOException {
  //读取配置文件
  InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
  //创建sqlSessionFactory
  SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
  //获取sqlSession 执行sql语句
  SqlSession sqlSession = sqlSessionFactory.openSession();
  try {
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    int delete = userDAO.delete(1);
    System.out.println("删除条数: "+delete);
    sqlSession.commit();
  } catch (Exception e) {
    e.printStackTrace();
    sqlSession.rollback();
  } finally {
    sqlSession.close();
  }
}
```

#### 3.3 封装工具类

```java
public class MybatisUtil {
    private static SqlSessionFactory sqlSessionFactory;
    //静态代码块 static 特点: 类加载时候执行  只执行一次
    static{
        //读取配置文件
        InputStream is = null;
        try {
            is = Resources.getResourceAsStream("mybatis-config.xml");
            //创建sqlSessionFactory
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(is);
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            try {
                is.close();
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
    //提供sqlSession
    public static SqlSession getSqlSession(){
        //获取sqlSession 执行sql语句
        return  sqlSessionFactory.openSession();
    }
    //关闭sqlSession
    public static void close(SqlSession sqlSession){
        sqlSession.close();
    }
}
```

#### 3.4 mybatis查询操作

- 查询所有

  ```java
  //查询所有方法
  List<User> queryAll();
  ```

  ```xml
  <!--查询所有
          resultType: list集合的泛型类型 com.baizhi.entity.User
      -->
  <select id="queryAll" resultType="com.baizhi.entity.User">
    select id, name, age, bir from t_user
  </select>
  ```

  ```java
  //查询所有
  @Test
  public void testQueryAll(){
    SqlSession sqlSession = MybatisUtil.getSqlSession();
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    List<User> users = userDAO.queryAll();
    //遍历
    users.forEach(user-> System.out.println(user));
  }
  ```

- 查询一个基于id查询

  ```java
  //根据id查询一个用户
  User queryById(Integer id);
  ```

  ```xml
  <!--sql标签:用来实现sql语句复用 id:相当于给sql标签中内容定义一个唯一标识-->
  <sql id="userQuery">
    select id, name, age, bir
    from t_user
  </sql>
  <!--查询一个id-->
  <select id="queryById" parameterType="Integer" resultType="com.baizhi.entity.User">
    <include refid="userQuery"/>
    where id=#{id}
  </select>
  ```

  ```java
  //查询一个
  @Test
  public void testQueryById(){
    SqlSession sqlSession = MybatisUtil.getSqlSession();
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    User user = userDAO.queryById(7);
    System.out.println(user);
    MybatisUtil.close(sqlSession);
  }
  ```

- 模糊查询 where like '%张%' 

  ```java
  //模糊查询
  List<User> queryLikeByName(String name);
  ```

  ```xml
  <!--sql标签:用来实现sql语句复用 id:相当于给sql标签中内容定义一个唯一标识-->
  <sql id="userQuery">
    select id, name, age, bir
    from t_user
  </sql>
  <!--根据名字模糊查询-->
  <select id="queryLikeByName" parameterType="String" resultType="com.baizhi.entity.User">
    <include refid="userQuery"/>
    <!--oarlce: '%'||#{name}'%' mysql: concat('%',#{name},'%')-->
    where name like concat('%',#{name},'%')
  </select>
  ```

  ```java
  //模糊查询
  @Test
  public void testQueryLike(){
    SqlSession sqlSession = MybatisUtil.getSqlSession();
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    List<User> users = userDAO.queryLikeByName("三");
    users.forEach(user-> System.out.println(user));
    MybatisUtil.close(sqlSession);
  }
  ```

- 分页查询  select .. from ... limit 起始条数,每页显示的记录数

  ```java
  //分页查询 //参数1:起始位置  参数2:每页显示记录数
  List<User> queryByPage(@Param("start") Integer start, @Param("rows") Integer rows);
  ```

  ```xml
  <!--分页查询 多个参数不写parameterType-->
  <select id="queryByPage" resultType="com.baizhi.entity.User">
    <include refid="userQuery"/>
    limit #{start},#{rows}
  </select>
  ```

  ```java
  //分页查询
  @Test
  public void testQueryPage(){
    SqlSession sqlSession = MybatisUtil.getSqlSession();
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    //mysql默认从0开始  start 当前页:1   起始位置:0 当前页2:  起始位置:2  当前页:3 起始位置: 4
    // 起始位置规律:(当前页-1)*每页显示的记录数
    List<User> users = userDAO.queryByPage(4, 2);
    users.forEach(user-> System.out.println(user));
    MybatisUtil.close(sqlSession);
  }
  ```

- 查询总条数

  ```java
  //查询总条数
  Long queryTotalCounts();
  ```

  ```xml
  <!--查询总条数-->
  <select id="queryTotalCounts" resultType="Long">
    select count(id) from t_user
  </select>
  ```

  ```java
  //查询总条数
  @Test
  public void testQueryTotalCounts(){
    SqlSession sqlSession = MybatisUtil.getSqlSession();
    UserDAO userDAO = sqlSession.getMapper(UserDAO.class);
    Long counts = userDAO.queryTotalCounts();
    System.out.println("总记录数为: "+counts);
    MybatisUtil.close(sqlSession);
  }
  ```

  ----

  ## 4.resultType 和 resultMap区别

  总结: resultType 、resultMap都是用来对数据库中返回的结果进行封装的

  - resultType 只能封装简单类型的对象 简单类型对象： 对象中没有对象类型的属性===》简单对象
  - resultMap 封装复杂类型对象的      处理库表关联关系===>一对一 一对多 多对多关系时封装对象

- resultMap使用

  ```xml
  <!--查询所有
          resultType: list集合的泛型类型 com.baizhi.entity.User
      -->
      <!--sql标签:用来实现sql语句复用 id:相当于给sql标签中内容定义一个唯一标识-->
      <sql id="userQuery">
          select id, name as uname, age, bir
          from t_user
      </sql>
      <!--结果映射 id:resultMap标签起一个唯一标识 type:指定封装对象的类型  -->
      <resultMap id="userResultMap" type="com.baizhi.entity.User">
          <!--主键封装: id标签-->
          <id column="id" property="id"/>
          <!--普通列 result-->
          <result column="uname" property="name"/>
          <result column="age" property="age"/>
          <result column="bir" property="bir"/>
      </resultMap>
      <select id="queryAll" resultMap="userResultMap">
          <include refid="userQuery"/><!--include:包含那个sql片段 refid:包含片段的id-->
      </select>
  ```

  ![image-20201223211358555](笔记.assets/image-20201223211358555.png)

  ----

  