# JAVA解析Excel工具EasyExcel

Java解析、生成Excel比较有名的框架有Apache poi、jxl。但他们都存在一个严重的问题就是非常的耗内存，poi有一套SAX模式的API可以一定程度的解决一些内存溢出的问题，但POI还是有一些缺陷，比如07版Excel解压缩以及解压后存储都是在内存中完成的，内存消耗依然很大。easyexcel重写了poi对07版Excel的解析，能够原本一个3M的excel用POIsax依然需要100M左右内存降低到几M，并且再大的excel不会出现内存溢出，03版依赖POI的sax模式。在上层做了模型转换的封装，让使用者更加简单方便

[GitHub地址](https://github.com/alibaba/easyexcel)

[相关文档](https://www.yuque.com/easyexcel/doc/easyexcel)

## excel导出后台代码

**pom.xml**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>xinguan-parent</artifactId>
        <groupId>com.xioaoge</groupId>
        <version>0.0.1-SNAPSHOT</version>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>xinguan-base-common</artifactId>

    <dependencies>
        <!--controller层-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!--数据访问层-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-boot-starter</artifactId>
        </dependency>

        <!--mybatis自动代码生成-->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus-generator</artifactId>
        </dependency>

        <!--代码生成的模板引擎-->
        <dependency>
            <groupId>org.apache.velocity</groupId>
            <artifactId>velocity-engine-core</artifactId>
        </dependency>

        <!--java连接mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>

        <!--swagger-->
        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger2</artifactId>
        </dependency>

        <dependency>
            <groupId>io.springfox</groupId>
            <artifactId>springfox-swagger-ui</artifactId>
        </dependency>

        <!--lombok简化getter和setter-->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
        </dependency>

        <dependency>
            <groupId>com.github.xiaoymin</groupId>
            <artifactId>knife4j-spring-boot-starter</artifactId>
        </dependency>

        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>easyexcel</artifactId>
        </dependency>
    </dependencies>
</project>
```

主要是添加了`easyexcel`的相关依赖

**User**

```java
package com.xiaoge.system.entity;

import com.alibaba.excel.annotation.ExcelProperty;
import com.baomidou.mybatisplus.annotation.TableField;
import com.baomidou.mybatisplus.annotation.TableName;
import com.baomidou.mybatisplus.annotation.IdType;
import java.util.Date;
import com.baomidou.mybatisplus.annotation.TableId;
import java.io.Serializable;

import com.fasterxml.jackson.annotation.JsonFormat;
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import lombok.Data;
import lombok.EqualsAndHashCode;

/**
 * <p>
 * 用户表
 * </p>
 *
 * @author xiaoge
 * @since 2020-09-04
 */
@Data
@EqualsAndHashCode(callSuper = false)
@TableName("tb_user")
@ApiModel(value="User对象", description="用户表")
public class User implements Serializable {

    private static final long serialVersionUID = 1L;

    @ApiModelProperty(value = "用户ID")
    @ExcelProperty(value = "用户ID")
    @TableId(value = "id", type = IdType.AUTO)
    private Long id;

    @ApiModelProperty(value = "用户名")
    @ExcelProperty(value = "用户名")
    private String username;

    @ApiModelProperty(value = "昵称")
    @ExcelProperty(value = "昵称")
    private String nickname;

    @ApiModelProperty(value = "邮箱")
    @ExcelProperty(value = "邮箱")
    private String email;

    @ApiModelProperty(value = "头像")
    @ExcelProperty(value = "头像")
    private String avatar;

    @ApiModelProperty(value = "联系电话")
    @ExcelProperty(value = "联系电话")
    private String phoneNumber;

    @ApiModelProperty(value = "状态 0锁定 1有效")
    @ExcelProperty(value = "状态 0锁定 1有效")
    private Integer status;

    @ApiModelProperty(value = "创建时间")
    @ExcelProperty(value = "创建时间")
    private Date createTime;

    @ApiModelProperty(value = "修改时间")
    @ExcelProperty(value = "修改时间")
    private Date modifiedTime;

    @ApiModelProperty(value = "性别 0男 1女 2保密")
    @ExcelProperty(value = "性别 0男 1女 2保密")
    private Integer sex;

    @ApiModelProperty(value = "盐")
    @ExcelProperty(value = "盐")
    private String salt;

    @ApiModelProperty(value = "0:超级管理员，1：系统用户")
    @ExcelProperty(value = "0:超级管理员，1：系统用户")
    private Integer type;

    @ApiModelProperty(value = "密码")
    @ExcelProperty(value = "密码")
    private String password;

    @ApiModelProperty(value = "生日")
    @ExcelProperty(value = "生日")
    @JsonFormat(pattern = "yyyy-MM-dd",timezone = "GMT+8")
    private Date birth;

    @ApiModelProperty(value = "部门id")
    @ExcelProperty(value = "部门id")
    private Long departmentId;

    @ApiModelProperty(value = "逻辑删除")
    @ExcelProperty(value = "是否删除 0:否 1:是")
    private Boolean deleted;

    @ApiModelProperty(value = "部门名称")
    @ExcelProperty(value = "部门名称")
    @TableField(exist = false)
    private String name;
}
```

添加了注解:`@ExcelProperty(value = "")`

**UserService**

```java
package com.xiaoge.system.service;

import com.baomidou.mybatisplus.core.conditions.query.QueryWrapper;
import com.baomidou.mybatisplus.core.metadata.IPage;
import com.baomidou.mybatisplus.extension.plugins.pagination.Page;
import com.xiaoge.system.entity.User;
import com.baomidou.mybatisplus.extension.service.IService;

import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.List;

/**
 * <p>
 * 用户表 服务类
 * </p>
 *
 * @author xiaoge
 * @since 2020-09-04
 */
public interface UserService extends IService<User> {

    IPage<User> findUserPage(Page<User> page,QueryWrapper<User> wrapper);

    /**
     * 导出用户Excel
     * @param response
     * @param tbUsers
     * @throws IOException
     */
    void exportUserExcel(HttpServletResponse response, List<User> tbUsers) throws IOException;
}
```

**UserServiceImpl**

```java
package com.xiaoge.system.service.impl;

import com.alibaba.excel.EasyExcel;
import com.alibaba.excel.write.style.column.LongestMatchColumnWidthStyleStrategy;
import com.baomidou.mybatisplus.core.conditions.query.QueryWrapper;
import com.baomidou.mybatisplus.core.metadata.IPage;
import com.baomidou.mybatisplus.extension.plugins.pagination.Page;
import com.xiaoge.handler.BusinessException;
import com.xiaoge.response.ResultCode;
import com.xiaoge.system.entity.Department;
import com.xiaoge.system.entity.User;
import com.xiaoge.system.mapper.UserMapper;
import com.xiaoge.system.service.UserService;
import com.baomidou.mybatisplus.extension.service.impl.ServiceImpl;
import org.springframework.stereotype.Service;

import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.List;

/**
 * <p>
 * 用户表 服务实现类
 * </p>
 *
 * @author xiaoge
 * @since 2020-09-04
 */
@Service
public class UserServiceImpl extends ServiceImpl<UserMapper, User> implements UserService {

    @Override
    public IPage<User> findUserPage(Page<User> page, QueryWrapper<User> wrapper) {
        return this.baseMapper.findUserPage(page,wrapper);
    }

    @Override
    public void exportUserExcel(HttpServletResponse response, List<User> users) throws IOException {

        //----- 写入excel文件
        String exportFileName = "TbUserInfo.xlsx";
        response.setCharacterEncoding("UTF-8");
        response.setContentType("application/vnd.ms-excel");
        response.addHeader("Content-Disposition", "attachment;filename=" + exportFileName);
        EasyExcel.write(response.getOutputStream(), User.class)
                .sheet("用户信息")
                //自动列宽
                .registerWriteHandler(new LongestMatchColumnWidthStyleStrategy())
                .doWrite(users);
    }
}
```

**UserController**

```java
package com.xiaoge.system.controller;


import com.baomidou.mybatisplus.core.conditions.query.LambdaQueryWrapper;
import com.baomidou.mybatisplus.core.conditions.query.QueryWrapper;
import com.baomidou.mybatisplus.core.metadata.IPage;
import com.baomidou.mybatisplus.extension.plugins.pagination.Page;
import com.xiaoge.response.Result;
import com.xiaoge.system.entity.User;
import com.xiaoge.system.service.UserService;
import com.xiaoge.vo.UserVO;
import io.swagger.annotations.Api;
import io.swagger.annotations.ApiOperation;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Qualifier;
import org.springframework.stereotype.Repository;
import org.springframework.util.StringUtils;
import org.springframework.web.bind.annotation.*;
import org.springframework.web.multipart.MultipartFile;

import javax.annotation.Resource;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.List;

/**
 * <p>
 * 用户表 前端控制器
 * </p>
 *
 * @author xiaoge
 * @since 2020-09-03
 */
@Api(value = "用户管理")
@RestController
@RequestMapping("/user")
@CrossOrigin
public class UserController {

    @Resource
    private UserService userService;

    /**
     * 分页查询用户列表
     *
     * @return
     */
    @ApiOperation("分页查询用户列表")
    @GetMapping("/findUserList")
    public Result findUserList(@RequestParam(required = true, defaultValue = "1") Integer current,
                               @RequestParam(required = true, defaultValue = "6") Integer size) {
        //对用户进行分页,泛型中注入的就是用户实体类
        Page<User> page = new Page<>(current, size);
        //单表的时候其实这个方法是非常好用的
        LambdaQueryWrapper<User> queryWrapper = new LambdaQueryWrapper<>();
        Page<User> userPage = userService.page(page);
        long total = userPage.getTotal();
        List<User> records = userPage.getRecords();
        return Result.ok().data("total", total).data("records", records);
    }

    /**
     * 根据条件进行分页查询
     *
     * @param current
     * @param size
     * @param userVO
     * @return
     */
    @PostMapping("/findUserPage")
    public Result findUserPage(@RequestParam(required = true, defaultValue = "1") Integer current,
                               @RequestParam(required = true, defaultValue = "6") Integer size,
                               @RequestBody UserVO userVO) {
        //对用户进行分页,泛型中注入的就是用户实体类
        Page<User> page = new Page<>(current, size);
        //单表的时候其实这个方法是非常好用的
        QueryWrapper<User> wrapper = getWrapper(userVO);
        IPage<User> userPage = userService.findUserPage(page, wrapper);
        long total = userPage.getTotal();
        List<User> records = userPage.getRecords();
        return Result.ok().data("total", total).data("records", records);
    }

    /**
     * 封装查询条件
     *
     * @param userVO
     * @return
     */
    private QueryWrapper<User> getWrapper(UserVO userVO) {
        QueryWrapper<User> queryWrapper = new QueryWrapper<>();
        if (userVO != null) {
            if (!StringUtils.isEmpty(userVO.getDepartmentId())) {
                queryWrapper.eq("department_id", userVO.getDepartmentId());
            }
            if (!StringUtils.isEmpty(userVO.getUsername())) {
                queryWrapper.eq("username", userVO.getUsername());
            }
            if (!StringUtils.isEmpty(userVO.getEmail())) {
                queryWrapper.eq("email", userVO.getEmail());
            }
            if (!StringUtils.isEmpty(userVO.getSex())) {
                queryWrapper.eq("sex", userVO.getSex());
            }
            if (!StringUtils.isEmpty(userVO.getNickname())) {
                queryWrapper.eq("nickname", userVO.getNickname());
            }
        }
        return queryWrapper;
    }

    @ApiOperation(value = "导出用户信息")
    @PostMapping(value = "/export")
    public void exportUserExcel(HttpServletResponse response, @RequestBody(required = false) UserVO userVO) throws IOException {
        QueryWrapper<User> wrapper = getWrapper(userVO);
        List<User> users = userService.list(wrapper);
        userService.exportUserExcel(response,users);
    }
}
```

## excel导出前端代码

**users.js**

```javascript
<el-button type="warning" icon="el-icon-download" @click="exportExcel">导出</el-button>

import request from '../utils/request'

/**
 * 后面的每次请求都是需要携带token的
 */
export const findUserList= (current,size,userVO) => {
  return request({
    url: "/user/findUserPage",
    method: 'post',
    params: {
      current,
      size
    },
    data: userVO
  })
}

/**
 * 导出用户Excel
 * @param userVo
 */
export function exportUserInfo(userVo) {
  return request({
    url: '/user/export',
    method: 'post',
    data: userVo,
    responseType: "blob"
  })
}
```

```javascript
async exportExcel(){
    exportUserInfo(this.userVo).then(res => {
        //这里没有返回数据,但是要在响应头中进行下载操作
        // 将二进制文件转化为可访问的url
        let url = window.URL.createObjectURL(new Blob([res]));
        var a = document.createElement("a");
        document.body.appendChild(a);
        a.href = url;
        a.download = "用户列表.xls";
        a.click();
        window.URL.revokeObjectURL(url);
    }).catch(err => {

    })
},
```







