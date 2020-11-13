# Boot Strap

## 1.Boot Strap 的引言

```txt
Bootstrap是美国Twitter公司的设计师Mark Otto和Jacob Thornton合作基于HTML、CSS、JavaScript 开发的简洁、直观、强悍的前端开发框架，使得 Web 开发更加快捷

Bootstrap一经推出后颇受欢迎，一直是GitHub上的热门开源项目，包括NASA的MSNBC（微软全国广播公司）的Breaking News都使用了该项目

Bootstrap 是最受欢迎的 HTML、CSS 和 JS 框架，用于开发响应式布局、移动设备优先的 WEB 项目。
```

----



## 2.Boot Strap 环境搭建

```html
1.下载bootStrap 相关资料  说明:bootstrap第3.3.7版本
  https://v3.bootcss.com/getting-started/#download
  
2.下载完成之后解压bootstrap压缩包
   css bootstrap核心css文件   bootstrap.css 核心css bootstarp.min.css(压缩css)
   fonts 用来存放bootstrap字体图标的文件夹
   js    bootstrap.js 是bootstrap核心js   bootstrap.min.js(压缩js)
    
3.将bootstrap文件夹全部放入项目中

4.页面使用bootstrap
   <meta name="viewport" content="width=device-width, initial-scale=1"> 移动设备优先
   <link rel="stylesheet" href="../boot/css/bootstrap.min.css">
```

---

## 3.Boot Strap 容器

```html
<div class="container" style="border: 1px red solid;"></div>

<div class="container-fluid" style="border: 1px blue solid;"></div>
```

---

## 4.Boot Strap 栅格系统

```html
栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。下面就介绍一下 Bootstrap 栅格系统的工作原理：

“行（row）”必须包含在 .container （固定宽度）或 .container-fluid （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
通过“行（row）”在水平方向创建一组“列（column）”。
你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。
类似 .row 和 .col-xs-4 这种预定义的类，可以用来快速创建栅格布局。Bootstrap 源码中定义的 mixin 也可以用来创建语义化的布局。
通过为“列（column）”设置 padding 属性，从而创建列与列之间的间隔（gutter）。通过为 .row 元素设置负值 margin 从而抵消掉为 .container 元素设置的 padding，也就间接为“行（row）”所包含的“列（column）”抵消掉了padding。
负值的 margin就是下面的示例为什么是向外突出的原因。在栅格列中的内容排成一行。
栅格系统中的列是通过指定1到12的值来表示其跨越的范围。例如，三个等宽的列可以使用三个 .col-xs-4 来创建。
如果一“行（row）”中包含了的“列（column）”大于 12，多余的“列（column）”所在的元素将被作为一个整体另起一行排列。
栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 .col-md-* 栅格类适用于与屏幕宽度大于或等于分界点大小的设备 ， 并且针对小屏幕设备覆盖栅格类。 因此，在元素上应用任何 .col-lg-* 不存在， 也影响大屏幕设备。

1.栅格系统分配
   注意: 无论屏幕尺寸多大在bootsrap中将其分为12份

2.栅格系统基本使用

  <div class="container-fulid">
       <div class="row">
           12column (.col-xs .col-sm .col-md .col-lg)
      </div>
  </div>

3.栅格系统的分配(一个行12等份)
  <div class="row">
            <!--行最多12个列-->
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
            <div class="col-sm-1 aa">1</div>
   </div>
4.栅格系统的拆分
	<div class="row">
            <!--行最多12个列-->
            <div class="col-sm-4 aa">1</div>
            <div class="col-sm-4 aa">1</div>
            <div class="col-sm-4 aa">1</div>
    </div>

5.栅格系统嵌套
	<div class="row">
        <!--行最多12个列-->
        <div class="col-sm-2 aa">1</div>
        <div class="col-sm-8 aa">
            <div class="col-sm-10 bb">
                aaa
            </div>
            <div class="col-sm-2 bb">
                bb
            </div>
        </div>
        <div class="col-sm-2 aa">1</div>
    </div>

6.栅格系统列偏移 (.col-sm-offset)
 	<div class="row">
        <div class="col-sm-4 aa col-sm-offset-8">aaa</div>	
	</div>

7.栅格系统多余列
 	<div class="row">
        <!--占4份-->
        <div class="col-sm-4 aa">aaa</div>
        <!--占4份-->
        <div class="col-sm-4 aa">bbb</div>
        <!--超过另起一行-->
        <div class="col-sm-8 aa">bbb</div>
        <!--没有超过12等份 在同一行-->
        <div class="col-sm-4 aa">ccc</div>
	</div>

```

## 5.Boot Strap 排版

### 5.1 标题

```html
	<h1>h1. Bootstrap heading</h1>
    <h2>h2. Bootstrap heading</h2>
    <h3>h3. Bootstrap heading</h3>
    <h4>h4. Bootstrap heading</h4>
    <h5>h5. Bootstrap heading</h5>
    <h6>h6. Bootstrap heading</h6>

    注意: 在bootstrap中默认h1标题的大小为36px   最小标题的字体12px
```

### 5.2  页面主体

```html
Bootstrap 将全局 font-size 设置为 14px，line-height 设置为 1.428。这些属性直接赋予 <body> 元素和所有段落元素
    
    1.使用可以直接在body标签中书写文字
    
    2.可以在<p>标签中书写文字和直接在body标签中书写文字样式一致
       <p>这是一个段落</p>
    
    3.突出显示
       <p class="lead">这是一个段落突出显示</p>
```

### 5.3 内联文本元素

```html
1.使用<mark>标签高亮元素
    这是一个段落<mark>突出</mark>显示
```

### 5.4 被删除的文本

```html
1.使用<del>标签让元素显示删除线
	小<del>黑小</del>明
    小<s>黑小</s>明
```

### 5.5 插入文本和带有下划线的文本

```html
1.使用<ins>标签
     <ins>这是bootstrap相关的内容</ins>
2.使用<u>标签
     <u>这是bootstrap相关的内容</u>
```

### 5.6 小号文本

```html
1.使用<small>标签完成字体小号展示 
     这是一个好<small>的课程</small>
     注意:使用 <small> 标签包裹，其内的文本将被设置为父容器字体大小的 85%
    
2.副标题
    <h1>h1. Bootstrap heading<small>V2.0</small></h1>
    <h2>h2. Bootstrap heading<small>副标题</small></h2>
    <h3>h3. Bootstrap heading<small>副标题</small></h3>
    <h4>h4. Bootstrap heading<small>副标题</small></h4>
    <h5>h5. Bootstrap heading<small>副标题</small></h5>
    <h6>h6. Bootstrap heading<small>副标题</small></h6>
```

### 5.7 着重  和 斜体

```html
1.使用<strong>标签着重展示
    小明是一个<strong>好人</strong>
    
2.使用<em>标签可以让包裹的文本变成斜体
    小明是一个<strong><em>好人</em></strong>
```

### 5.8 文本对齐方式

```html
1.设置文本对齐方式
	<!--左对齐-->
    <p class="text-left">小黑</p>
    <!--右对齐-->
    <p class="text-right">小黑</p>
    <!--居中对齐-->
    <p class="text-center">小黑</p>
    <!--不换行-->
    <p class="text-nowrap">小黑</p>
```

### 5.9 改变大小写

```html
1.设置转换大小写
	<p class="text-lowercase">LOwercased text.</p>
    <p class="text-uppercase">Uppercased text.</p>
    <p class="text-capitalize">Capitalized text boot.</p>   注意:这里是首字母大写
```

### 6.0 列表

```html
1.无序列表
	<ul>
        <li>小明</li>
        <li>小黑</li>
    </ul>

2.有序列表
	<ol>
        <li>小黑</li>
        <li>小张</li>
    </ol>

3.无样式列表
	<ul class="list-unstyled">
        <li>小明
            <ul>  
                <li>二级</li>
                <li>二级</li>
            </ul>
        </li>
        <li>小黑</li>
    </ul>
	注意: list-unstyled 只能解决ul中一级列表没有样式 但是内部嵌套列表依然存在样式

4.内联列表(列表项一行展示)
	<ul class="list-inline">
        <li>看电视</li>
        <li>看书</li>
        <li>看报</li>
    </ul>
5.水平列表
	<dl class="dl-horizontal">
        <dt>小明明</dt>
        <dd>是一个非常好的人</dd>
        <dd>是一个非常好的人1</dd>
        <dd>是一个非常好的人2</dd>
        <dt>小嘿嘿</dt>
        <dd>是一个非常好的人</dd>
        <dd>是一个非常好的人1</dd>
        <dd>是一个非常好的人2</dd>
    </dl>
```

----

## 6.Boot Strap 表格

### 6.1 基本表格

```html
基本样式表格.table 用来美化table控件
<table class="table">
  ...
</table>
```

### 6.2 条纹状表格(斑马线表格)

```html
<table class="table table-striped">
  ...
</table>
```

### 6.3 带边框的表格

```html
<table class="table table-bordered">
  ...
</table>
```

### 6.4 鼠标悬停表格(鼠标引入变色)

```html
<table class="table table-hover">
  ...
</table>
```

### 6.5 紧缩表格

```html
<table class="table table-condensed">
  ...
</table>
```

### 6.6 表格的状态类

```html
1.提供的状态类

.active	    鼠标悬停在行或单元格上时所设置的颜色  灰色着重
.success	标识成功或积极的动作               浅绿色
.info	    标识普通的提示信息或动作            浅蓝色     
.warning	标识警告或需要用户注意             
.danger	    标识危险或潜在的带来负面影响的动作

2.在tr中使用
	<tr class="active">...</tr>
	<tr class="success">...</tr>
	<tr class="warning">...</tr>
	<tr class="danger">...</tr>
	<tr class="info">...</tr>
3.在td中使用  注意: 只有当前td的背景颜色发生变化
    <tr>
      <td class="active">...</td>
      <td class="success">...</td>
      <td class="warning">...</td>
      <td class="danger">...</td>
      <td class="info">...</td>
    </tr>
```

----

## 7.Boot Strap 表单

### 7.1 基本实例

```html
使用方式:单独的表单控件会被自动赋予一些全局样式。所有设置了 .form-control 类的 <input>、<textarea> 和 <select> 元素都将被默认设置宽度属性为 width: 100%;。 将 label 元素和前面提到的控件包裹在 .form-group 中可以获得最好的排列。
    
1.基本实例
   <form action="">
         <div class="form-group">
             <label for="aa">用户名:</label>
             <input type="text" id="aa" name="name" class="form-control"/>
         </div>
         <div class="form-group">
             <label for="pwd">密码:</label>
             <input type="text" id="pwd" name="name" class="form-control"/>
         </div>

         <div class="form-group">
             <label for="exampleInputFile">请选择文件:</label>
             <input type="file" id="exampleInputFile">
             <p class="help-block">上传文件的大小不能超过2M!</p>
         </div>

         <div class="checkbox">
             <label>
                 <input type="checkbox"> 电视
             </label>
             <label>
                 <input type="checkbox"> 睡觉
             </label>
             <label>
                 <input type="checkbox"> 吃饭
             </label>
         </div>

         <select class="form-control">
             <option value="1">北京</option>
             <option value="2">南京</option>
             <option value="3">东京</option>
         </select>
    </form>
```

### 7.2 内联表单(一行展示表单控件)

```html
<form action="" class="form-inline">
    <div class="form-group">
       <label for="aa">用户名:</label>
       <input type="text" id="aa" name="name" placeholder="输名." class="form-control"/>
    </div>
    <div class="form-group">
        <label for="pwd">密码:</label>
        <input type="text" id="pwd" name="name" class="form-control"/>
    </div>

    <input type="submit" value="登录"></input>
</form>
```

### 7.3 输入框组(定制input框)

```html
<form action="" class="form-inline">
    <div class="form-group">
        <label for="name">请输入金额:</label>
        <div class="input-group">
            <div class="input-group-addon">$</div>
            <input type="text" class="form-control" id="name">
            <div class="input-group-addon">.00</div>
        </div>
    </div>
</form>
```

### 7.4 水平排列表单 (必须和栅格系统连用)

```html
<div class="container">
        <div class="row">
            <div class="col-sm-1"></div>
            <div class="col-sm-10">
                <form action="" class="form-horizontal">
                    <div class="form-group">
                        <label for="name" class="col-sm-2 control-label">用户名</label>
                        <div class="col-sm-10">
                            <input type="text" id="name" class="form-control"/>
                        </div>
                    </div>
                </form>
            </div>
            <div class="col-sm-1"></div>
        </div>
</div>
具体使用方式见下图:
```

![1552381474550](C:\Users\HIAPAD\AppData\Roaming\Typora\typora-user-images\1552381474550.png)

### 7.4 文本域

```html
<textarea class="form-control" rows="10"></textarea>
```

### 7.5 复选框 和 单选扭

```html
1.复选框|单选按钮水平排列
 	<div class="checkbox">
        <label>
            <input type="checkbox"> 看书
        </label>
        <label>
            <input type="checkbox"> 看书
        </label>
	</div>

2.复选框单选按钮垂直排列
	<div class="checkbox">
        <label>
            <input type="checkbox"> 看书
        </label>
    </div>
    <div class="checkbox">
        <label>
            <input type="checkbox" disabled> 看书
        </label>
    </div>

3.使用bootstrap提供样式水平展示(.checkbox-inline .radio-inline)
<label class="checkbox-inline">
    <input type="checkbox" id="aa0" value="option1"> 1
</label>
<label class="checkbox-inline">
    <input type="checkbox" id="aa2" value="option2"> 2
</label>
<label class="checkbox-inline">
    <input type="checkbox" id="aa3" value="option3"> 3
</label>

<hr>
<label class="radio-inline">
    <input type="radio" name="rad" id="aa4" value="option1"> 1
</label>
<label class="radio-inline">
    <input type="radio" name="rad" id="aa5" value="option2"> 2
</label>
<label class="radio-inline">
    <input type="radio" name="rad" id="aa6" value="option3"> 3
</label>
```

### 7.6 下拉列表

```html
1.下拉列表(单选) 加入form-control可以更好的适应bootstrap	
	<select name="" id="" class="form-control">
        <option value="1">北京</option>
        <option value="1">东京</option>
        <option value="1">天津</option>
    </select>

2.下拉列表(多选)  实现多选必须在select标签上加入multiple属性
    <select name="citys" multiple class="form-control">
        <option value="1">北京</option>
        <option value="1">东京</option>
        <option value="1">天津</option>
    </select>
```

### 7.7 静态控件

```html
<div class="contaier">
    <div class="row">
        <div class="col-sm-12">
            <form action="" class="form-horizontal">
                <div class="form-group">
                    <label class="col-sm-2 control-label">Emial</label>
                    <div class="col-sm-10">
                       <p class="form-control-static"><strong><u>60992323@qq.com</u></strong></p>
                    </div>
                </div>
            </form>
        </div>
    </div>
</div>
```

### 7.8 校验状态

```html
Bootstrap 对表单控件的校验状态，如 error、warning 和 success 状态，都定义了样式。使用时，添加 .has-warning、.has-error 或 .has-success 类到这些控件的父元素即可。任何包含在此元素之内的 .control-label、.form-control 和 .help-block 元素都将接受这些校验状态的样式。

1.使用校验状态
<div class="form-group has-warning">
    <label class="col-sm-2 control-label">Emial</label>
    <div class="col-sm-10">
        <input type="text" name="email" class="form-control">
        <p class="help-block">必须是邮箱格式</p>
    </div>
</div>

2.为校验状态设置图标 
   注意:反馈图标（feedback icon）只能使用在文本输入框 <input class="form-control"> 元素上
   <div class="form-group has-warning  has-feedback">
       <label class="col-sm-2 control-label">Emial</label>
       <div class="col-sm-10">
           <input type="text" name="email" class="form-control ">
           <span class="glyphicon glyphicon-ok  form-control-feedback"></span>
           <p class="help-block">必须是邮箱格式</p>
       </div>
	</div>
	使用方式见图:
```

![1552384632005](C:\Users\HIAPAD\AppData\Roaming\Typora\typora-user-images\1552384632005.png)

```html
3.为校验设置前后图标
<div class="form-group has-warning  has-feedback">
    <label class="col-sm-2 control-label">Emial</label>
    <div class="col-sm-10">
        <div class="input-group">
            <span class="input-group-addon">@</span>
            <input type="text" name="email" class="form-control ">
        </div>
        <span class="glyphicon glyphicon-ok  form-control-feedback"></span>
        <p class="help-block">必须是邮箱格式</p>
    </div>
</div>
使用方式见图:
```

![1552384948963](C:\Users\HIAPAD\AppData\Roaming\Typora\typora-user-images\1552384948963.png)

### 7.9 控件尺寸

```html
1.控制form基本实例控件的尺寸(.input-lg大 中form-control默认 .input-sm小 )
	<input class="form-control input-lg" type="text" placeholder=".input-lg">
    <input class="form-control" type="text" placeholder="Default input">
    <input class="form-control input-sm" type="text" placeholder=".input-sm">

    <select class="form-control input-lg">...</select>
    <select class="form-control">...</select>
    <select class="form-control input-sm">...</select>

2.控制form表单水平排列的尺寸(.form-group-lg)

<div class="form-group form-group-lg">
    <label class="col-sm-2 control-label" for="formGroupInputLarge">Large label</label>
    <div class="col-sm-10">
        <input class="form-control" type="text" id="formGroupInputLarge" placeholder="Large input">
    </div>
</div>
```

----

## 8.Boot Strap 按钮

### 8.1 可以作为按钮标签

```html
为 <a>、<button> 或 <input> 元素添加按钮类（button class）即可使用 Bootstrap 提供的样式。
```

## 8.2 创建按钮(.btn)

```html
<a href="" class="btn btn-default">link</a>
<button class="btn btn-default">button</button>
<input type="button" value="input" class="btn btn-default">
```

### 8.3 内置按钮样式

```html
 	<button class="btn btn-default">link</button>
    <button class="btn btn-primary">link</button>
    <button class="btn btn-warning">link</button>
    <button class="btn btn-info">link</button>
    <button class="btn btn-success">link</button>
    <button class="btn btn-danger">link</button>
    <button class="btn btn-link">link</button>
```

### 8.4 调整按钮尺寸

```html
使用 .btn-lg、.btn-sm 或 .btn-xs 就可以获得不同尺寸的按钮
<button class="btn btn-success btn-lg">link(默认样式)</button>
<button class="btn btn-default">link(默认样式)</button>
<button class="btn btn-default btn-sm">link(默认样式)</button>
<button class="btn btn-default btn-xs">link(默认样式)</button>
```

### 8.5 按钮适应父元素

```html
通过给按钮添加 .btn-block 类可以将其拉伸至父元素100%的宽度，而且按钮也变为了块级（block）元素。
 <button class="btn btn-success btn-lg btn-block">link(默认样式)</button>
```

### 8.6 按钮激活状态

```html
1.但是在需要让其表现出同样外观的时候可以添加 .active 类。
<button class="btn btn-success btn-lg btn-block active">link(默认样式)</button>
2.为<button> 元素添加 disabled 属性，使其表现出禁用状态。
<a href="" disabled="disabled" class="btn btn-success btn-lg btn-block active">xxxxx </a>
```

---

## 9. BootStrap 图片

### 9.1 图片的生成

```html
通过为 <img> 元素添加以下相应的类.img-rounded (圆角) .img-circle(圆形) .img-thumbnail(边框)
 注意:跨浏览器兼容性
	请时刻牢记：Internet Explorer 8 不支持 CSS3 中的圆角属性。
   <img src="../boot/img/aa.jpg" class="img-rounded" alt="这是提示信息" title="嘻嘻嘻嘻嘻">
   <img src="../boot/img/aa.jpg" class="img-circle" alt="这是提示信息" title="嘻嘻嘻嘻嘻">
   <img src="../boot/img/aa.jpg" class="img-thumbnail" alt="这是提示信息" title="嘻嘻嘻嘻嘻">
```

----

## 10. Bootstrap 辅助类

### 10.1 情境文本颜色

```html
<p class="text-muted">...</p>
<p class="text-primary">...</p>
<p class="text-success">...</p>
<p class="text-info">...</p>
<p class="text-warning">...</p>
<p class="text-danger">...</p>
```

### 10.2 情境背景色

```html
<p class="bg-primary">...</p>
<p class="bg-success">...</p>
<p class="bg-info">...</p>
<p class="bg-warning">...</p>
<p class="bg-danger">...</p>
```

### 10.3 关闭按钮

```html
 <button type="button" class="close" aria-label="Close"><span aria-hidden="true">&times;</span></button>
```

### 10.4 三角按钮

```html
<span class="caret"></span>
```

### 10.5 快速浮动

```html
<div class="pull-left">...</div>
<div class="pull-right">...</div>
```

---

## 11. Boot Strap 字体图标

### 11.1 使用字体图标

```html
1.生成图标注意事项
	a.为了设置正确的内补（padding），务必在图标和文本之间添加一个空格。
	b.图标类不能和其它组件直接联合使用。它们不能在同一个元素上与其他类共同存在
    c.应该创建一个嵌套的<span> 标签，并将图标类应用到这个 <span> 标签上
    d.图标类只能应用在不包含任何文本内容或子元素的元素上
       
2.创建图标
  	<span class="glyphicon glyphicon-king"></span> 皇冠
    <span class="glyphicon glyphicon-flash"></span> 闪电
        
3.应用与按钮图标
    a.文字和图标存在
    <button class="btn btn-primary btn-lg">
        <span class="glyphicon glyphicon-apple"></span> link
    </button>
    b.只有图标存在
    <button class="btn btn-success">
        <span class="glyphicon glyphicon-align-left"></span>
    </button>
```

---

## 12.Boot Strap 下拉菜单

### 12.1 下拉菜单

```html
1.创建下拉菜单注意事项
	a. 要求出发下拉菜单控件 和 下拉菜单必须通过.dropdown类包裹
    b. 触发按钮要加入 .dropdown-toggle 和 data-toggle属性的值必须为 dropdown
	c. 下拉菜单中 ul 必须加入 .dropdown-menu 

2.创建下拉菜单
    <div class="dropdown">
        <button class="btn btn-default dropdown-toggle" data-toggle="dropdown">
            点我实现拉列表 <span class="caret"></span>
        </button>
        <ul class="dropdown-menu">
            <li><a href="">Springmvc</a></li>
            <li><a href="">Springboot</a></li>
            <li><a href="">Springcloud</a></li>
        </ul>
    </div>
```

### 12.2 下拉菜单添加标题

```html
<div class="dropdown">
       <button class="btn btn-default dropdown-toggle" data-toggle="dropdown">
           点我下拉 <span class="caret"></span>
       </button>
       <ul class="dropdown-menu">
           <li class="dropdown-header"><a href="">框架</a></li>
           <li><a href="">Spring MVC</a></li>
           <li><a href="">Spring BOOT</a></li>
           <li><a href="">Spring Cloud</a></li>
           <li class="dropdown-header"><a href="">WEB</a></li>
           <li><a href="">JDBC</a></li>
           <li  class="divider"></li>    //这是分割线
           <li class="disabled"><a href="">Mybatis</a></li>   //disabled 不可用
       </ul>
</div>
```

---

## 13. Boot Strap 按钮组

### 13.1 创建按钮组

```html
使用方式:  将多个按钮通过.btn-group包裹
<div class="btn-group">
    <button class="btn btn-default">按钮</button>
    <button class="btn btn-default">按钮</button>
    <button class="btn btn-default">按钮</button>
</div>
```

### 13.2 创建按钮组工具栏(toolbar)

```html
<div class="btn-toolbar" >
  <div class="btn-group" >...</div>
  <div class="btn-group" >...</div>
  <div class="btn-group" >...</div>
</div>
```

### 13.3 按钮组的下拉菜单

```html
<div class="btn-group">
    <button class="btn btn-default">按钮1</button>
    <button class="btn btn-default">按钮2</button>
    <!--下拉菜单-->
    <div class="btn-group">
        <button class="btn btn-default dropdown-toggle" data-toggle="dropdown">
            点我下拉 <span class="caret"></span>
        </button>
        <ul class="dropdown-menu">
            <li><a href="">springmvc</a></li>
            <li><a href="">springmvc</a></li>
        </ul>
    </div>
</div>
```

### 13.4 垂直排列的下拉按钮

```html
1.使用说明如果想要使用按钮组垂直排列只需要将.btn-group替换为.btn-group-vertical即可
<div class="btn-group-vertical" role="group" aria-label="...">
  ...
</div>
```

### 13.5 按钮组适应父容器

```html
1.如果想要使用按钮实现两端对齐(适应父元素),必须使用<a> 元素创建按钮,然后将一系列 .btn 元素包裹到 .btn-group.btn-group-justified 中即可。
 
 <div class="btn-group btn-group-justified" style="width: 100%;">
     <a class="btn btn-primary">按钮</a>
     <a class="btn btn-primary">按钮</a>
     <a class="btn btn-primary">按钮</a>
 </div>
    
2.关于button标签构建按钮组实现两端对齐(自适应父容器)
 <div class="btn-group btn-group-justified">
      <div class="btn-group">
          <button class="btn btn-default">按钮1</button>
      </div>
      <div class="btn-group">
          <button class="btn btn-default">按钮1</button>
      </div>
 </div>
```

----

## 14. Boot Strap 导航

### 14.1 标签页导航

```html
1.生成基本导航栏的注意事项:
	a. Bootstrap 中的导航组件都依赖同一个 .nav 类

2.生成标签页导航
<ul class="nav nav-tabs">
    <li class="active"><a href="">Home</a></li>
    <li><a href="">Home</a></li>
    <li><a href="">Home</a></li>
</ul>
```

### 14.2 胶囊式标签页

```html
<ul class="nav nav-pills">
    <li><a href="">Home</a></li>
    <li class="active"><a href="">Spring</a></li>
    <li><a href="">SpringMvc</a></li>
</ul>
```

### 14.3 两端对齐标签页

```html
<ul class="nav nav-tabs nav-justified">
  ...
</ul>
<ul class="nav nav-pills nav-justified">
  ...
</ul>
```

### 14.4 带有下拉菜单的标签页

```html
<ul class="nav nav-tabs">
        <li><a href="">HOME</a></li>
        <li><a href="">SpringMVC</a></li>
        <li class="dropdown">
            <a class="dropdown-toggle" data-toggle="dropdown">
                点我下拉 <span class="caret"></span>
            </a>
            <ul class="dropdown-menu">
                <li><a href="">北京</a></li>
                <li><a href="">上海</a></li>
                <li><a href="">南京</a></li>
            </ul>
        </li>
    </ul>
```

----

### 15. BootStrap 导航条

### 15.1 生成导航条的标题

```html
1.生成导航条的注意事项:
	a.建议使用<nav>标签生成导航条
    b.生成导航条时让<nav>包裹.container .container-fuild

2.创建方式
 <nav class="navbar navbar-default">
    <div class="container-fluid">
        <!--导航条标题-->
        <div class="navbar-header">
            <a href="" class="navbar-brand">后台管理系统V1.0</a>
        </div>
    </div>
</nav>
```

### 15.2 生成导航条中(连接 按钮 下拉菜单)

```html
<div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
            <ul class="nav navbar-nav">
                <!--生成链接-->
                <li><a href="">Link</a></li>
                <!--生成按钮-->
                <li><button class="btn btn-default navbar-btn">按钮</button></li>
                <!--生成下拉菜单-->
                <li class="dropdown">
                    <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">Dropdown <span class="caret"></span></a>
                    <ul class="dropdown-menu">
                        <li><a href="#">Action</a></li>
                        <li><a href="#">Another action</a></li>
                        <li><a href="#">Something else here</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">Separated link</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">One more separated link</a></li>
                    </ul>
                </li>
            </ul>
        </div>
```

### 15.3 生成导航条中表单

```html
<!--导航条-->
<nav class="navbar navbar-default">
    <div class="container-fluid">
        <!--导航条标题-->
        <div class="navbar-header">
            <a href="" class="navbar-brand">
                <!--放入图标-->
               <!-- <img src="../boot/img/aa.jpg" width="20" height="20" alt="">-->
                <!--放入文本-->
                后台管理系统
            </a>
        </div>
        <!--导航内容-->
        <div class="collapse navbar-collapse" >
            <!--放入表单元素-->
            <form class="navbar-form navbar-left" role="search">
                <div class="form-group">
                    <input type="text" class="form-control" placeholder="Search">
                </div>
                <button type="submit" class="btn btn-default">Submit</button>
            </form>
            <ul class="nav navbar-nav">
                <!--生成链接-->
                <li><a href="">Link</a></li>
                <!--生成按钮-->
                <li><button class="btn btn-default navbar-btn">按钮</button></li>
                <!--生成下拉菜单-->
                <li class="dropdown">
                    <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">Dropdown <span class="caret"></span></a>
                    <ul class="dropdown-menu">
                        <li><a href="#">Action</a></li>
                        <li><a href="#">Another action</a></li>
                        <li><a href="#">Something else here</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">Separated link</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">One more separated link</a></li>
                    </ul>
                </li>
            </ul>
        </div>
    </div>
</nav>

```

### 15.4 生成导航条放入文本 右侧组件

```html
<!--导航条-->
<nav class="navbar navbar-default">
    <div class="container-fluid">
        <!--导航条标题-->
        <div class="navbar-header">
            <a href="" class="navbar-brand">
                <!--放入图标-->
               <!-- <img src="../boot/img/aa.jpg" width="20" height="20" alt="">-->
                <!--放入文本-->
                后台管理系统
            </a>
        </div>
        <!--导航内容-->
        <div class="collapse navbar-collapse" >
            <!--放入表单元素-->
            <form class="navbar-form navbar-left" role="search">
                <div class="form-group">
                    <input type="text" class="form-control" placeholder="Search">
                </div>
                <button type="submit" class="btn btn-default">Submit</button>
            </form>
            <ul class="nav navbar-nav">
                <!--生成链接-->
                <li><a href="">Link</a></li>
                <!--生成按钮-->
                <li><button class="btn btn-default navbar-btn">按钮</button></li>
                <!--生成下拉菜单-->
                <li class="dropdown">
                    <a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">Dropdown <span class="caret"></span></a>
                    <ul class="dropdown-menu">
                        <li><a href="#">Action</a></li>
                        <li><a href="#">Another action</a></li>
                        <li><a href="#">Something else here</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">Separated link</a></li>
                        <li role="separator" class="divider"></li>
                        <li><a href="#">One more separated link</a></li>
                    </ul>
                </li>
            </ul>
            <!--放入文本元素-->
            <p class="navbar-text">Signed in as Mark Otto</p>
            <!--放入非导航链接-->
            <p class="navbar-text">Signed in as <a href="#" class="navbar-link">Mark Otto</a></p>

            <!--将元素放在右侧-->
            <ul class="nav navbar-nav navbar-right">
                <li><a href="">Link</a></li>
            </ul>
        </div>
    </div>
</nav>

```

### 15.5 导航条位置

```html
1.固定在顶部
<nav class="navbar navbar-default navbar-fixed-top">
  <div class="container">
    ...
  </div>
</nav>

2.固定在底部
<nav class="navbar navbar-default navbar-fixed-bottom">
  <div class="container">
    ...
  </div>
</nav>
```

### 15.6 反色导航条

```html
<nav class="navbar navbar-inverse">
  ...
</nav>
```

### 15.7 简单方式导航条

```html
<!--生成导航条-->
<nav class="navbar navbar-inverse">
    <div class="container-fluid">

        <!--生成导航标题-->
        <div class="navbar-header">
            <a href="" class="navbar-brand">后台管理系统</a>
        </div>
        <!--生成导航内容-->
        <ul class="nav navbar-nav">
            <li class="active"><a href="">Link</a></li>
            <li><button class="btn btn-default navbar-btn">按钮</button></li>
            <li>
                <form class="navbar-form">
                    <div class="form-group">
                        <input type="text" class="form-control">
                    </div>
                    <button class="btn btn-primary">提交</button>
                </form>
            </li>
            <li class="dropdown">
                <a class="dropdown-toggle" data-toggle="dropdown">
                    下拉菜单 <span class="caret"></span>
                </a>
                <ul class="dropdown-menu">
                    <li><a href="">Springmvc</a></li>
                    <li><a href="">Springmvc</a></li>
                </ul>
            </li>
            <li>
                <p class="navbar-text">this is xiaohei </p>
            </li>
        </ul>
    </div>
</nav>
```

---

## 16. BootStrap 分页

### 16.1 基本分页

```html
<nav aria-label="Page navigation" class="pull-right" >
    <ul class="pagination">
        <li>
            <a href="#" aria-label="Previous">
                <span aria-hidden="true">&laquo;</span>
            </a>
        </li>
        <li><a href="#">1</a></li>
        <li><a href="#">2</a></li>
        <li><a href="#">3</a></li>
        <li><a href="#">4</a></li>
        <li><a href="#">5</a></li>
        <li>
            <a href="#" aria-label="Next">
                <span aria-hidden="true">&raquo;</span>
            </a>
        </li>
    </ul>
</nav>
```

### 16.2 分页激活状态

```html
<nav aria-label="...">
  <ul class="pagination">
    <li class="disabled"><a href="#" aria-label="Previous"><span aria-hidden="true">&laquo;</span></a></li>
    <li class="active"><a href="#">1 <span class="sr-only">(current)</span></a></li>
    ...
  </ul>
</nav>
```

### 16.3 简单分页

```html
<!--基本简单分页-->
<nav aria-label="...">
    <ul class="pager">
        <li><a href="#">Previous</a></li>
        <li><a href="#">Next</a></li>
    </ul>
</nav>

<hr>
<!--两端分页-->
<nav aria-label="...">
    <ul class="pager">
        <li class="previous"><a href="#">Previous</a></li>
        <li class="next"><a href="#">Next</a></li>
    </ul>
</nav>

<hr>
<!--禁用分页-->
<nav aria-label="...">
    <ul class="pager">
        <li class="previous disabled"><a href="#">Previous</a></li>
        <li class="next"><a href="#">Next</a></li>
    </ul>
</nav>

```



---

### 17. 标签

### 17.1 简单标签

```html
<h3>Example heading <span class="label label-default">New</span></h3>
```

### 17.2 标签变体

```html
<span class="label label-default">Default</span>
<span class="label label-primary">Primary</span>
<span class="label label-success">Success</span>
<span class="label label-info">Info</span>
<span class="label label-warning">Warning</span>
<span class="label label-danger">Danger</span>

```

---

## 18.徽章

```html
1.生成徽章使用  <span class="badge">数字</span>

2.创建简单徽章
<a href="">小黑 <span class="badge">1</span></a>

3.创建按钮徽章
<button class="btn btn-primary">
    按钮 <span class="badge">18</span>
</button>
```

---

## 19. 巨幕

```html
<div class="jumbotron">
        <h1>Hello, world!</h1>
        <p>This is a simple hero unit, a simple jum....</p>
        <p><a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a></p>
    </div>
```

---

## 20. 页头

```html
<div class="page-header">
  <h1>Example page header <small>Subtext for header</small></h1>
</div>
```

----

## 21. 警告框

### 21.1 基本实例

```html
1.生成警告框注意事项:
	a.警告框的基类是.alert 使用时必须先引入这个类

2.创建警告框
<div class="alert alert-success" role="alert">...</div>
<div class="alert alert-info" role="alert">...</div>
<div class="alert alert-warning" role="alert">...</div>
<div class="alert alert-danger" role="alert">...</div>

```

### 21.2 关闭警告框

```html
1.在关闭的按钮上加入data-dismiss="alert" 可以实现关闭警告框功能 注意:依赖jqueryjs 和 boot的js

<div class="alert alert-warning">
    <button type="button" class="close" data-dismiss="alert" aria-label="Close">
        <span aria-hidden="true">&times;</span>
    </button>
    可以关闭的
</div>
```

### 21.3 警告框中连接

```html
<div class="alert alert-warning">
    <button type="button" class="close" data-dismiss="alert" aria-label="Close">
        <span aria-hidden="true">&times;</span>
    </button>
    <a href="" class="alert-link">可以关闭的</a>
</div>
注意: alert-link 这个类可以保证连接的颜色和警告框的颜色一致
```

----

## 22. 列表组

### 22.1 基本实例

```html
<ul class="list-group">
  <li class="list-group-item">Cras justo odio</li>
  <li class="list-group-item">Dapibus ac facilisis in</li>
  <li class="list-group-item">Morbi leo risus</li>
  <li class="list-group-item">Porta ac consectetur ac</li>
  <li class="list-group-item">Vestibulum at eros</li>
</ul>
```

### 22.2 加入徽章的列表组

```html
<ul class="list-group">
    <li class="list-group-item">小黑 <span class="badge">34</span></li>
    <li class="list-group-item">小白 <span class="badge">14</span></li>
</ul>
```

### 22.3 链接列表组

```html
1.连接列表组使用div替换原来ul 使用a标签替换原来的li标签,并将a标签href设置指定路径

<div class="list-group">
    <a href="http://www.baidu.com" class="list-group-item active">
        Cras justo odio
    </a>
    <a href="#" class="list-group-item">Dapibus ac facilisis in</a>
    <a href="#" class="list-group-item">Morbi leo risus</a>
    <a href="#" class="list-group-item">Porta ac consectetur ac</a>
    <a href="#" class="list-group-item">Vestibulum at eros</a>
</div>
```

### 22.4 按钮列表组

```html
1.还是使用div作为容器标签  使用button标签作为列表组的项标签
<div class="list-group">
    <button type="button" class="list-group-item">Cras justo odio</button>
    <button type="button" class="list-group-item">Dapibus ac facilisis in</button>
    <button type="button" class="list-group-item">Morbi leo risus</button>
    <button type="button" class="list-group-item">Porta ac consectetur ac</button>
    <button type="button" class="list-group-item">Vestibulum at eros</button>
</div>
```

### 22.5 情景类

```html
<ul class="list-group">
  <li class="list-group-item list-group-item-success">Dapibus ac facilisis in</li>
  <li class="list-group-item list-group-item-info">Cras sit amet nibh libero</li>
  <li class="list-group-item list-group-item-warning">Porta ac consectetur ac</li>
  <li class="list-group-item list-group-item-danger">Vestibulum at eros</li>
</ul>
<div class="list-group">
  <a href="#" class="list-group-item list-group-item-success">Dapibus ac facilisis in</a>
  <a href="#" class="list-group-item list-group-item-info">Cras sit amet nibh libero</a>
  <a href="#" class="list-group-item list-group-item-warning">Porta ac consectetur ac</a>
  <a href="#" class="list-group-item list-group-item-danger">Vestibulum at eros</a>
</div>
```

### 22.6 列表组定制

```html
<div class="list-group">
  <a href="#" class="list-group-item active">
    <h4 class="list-group-item-heading">List group item heading</h4>
    <p class="list-group-item-text">...</p>
  </a>
</div>
```

---

## 23. 面板

### 23.1 基本实例

```html
<div class="panel panel-default">
  <div class="panel-body">
    Basic panel example
  </div>
</div>
```

### 23.2 标题面板

```html
1.直接设置标题
<!--标题的面板-->
<div class="panel panel-default">
    <!--标题-->
    <div class="panel-heading">标题</div>
    <div class="panel-body">
        这是一个面板
    </div>
</div>

2.使用h标签设置标题
 <!--标题的面板-->
    <div class="panel panel-default">
        <!--标题-->
        <div class="panel-heading">
            <h3 class="panel-title">标题</h3>
        </div>
        <div class="panel-body">
            这是一个面板
        </div>
    </div>
```

### 23.3 带脚注的面板

```html
<div class="panel panel-default">
  <div class="panel-body">
    Panel content
  </div>
  <div class="panel-footer">Panel footer</div>
</div>
```

### 23.4 带表格的面板

```html
<div class="panel panel-default">
  <!-- Default panel contents -->
  <div class="panel-heading">Panel heading</div>
  <div class="panel-body">
    <p>...</p>
  </div>

  <!-- Table -->
  <table class="table">
    ...
  </table>
</div>
```

---

## 24.模态框

### 24.1静态实例

```html
1.使用模态框注意事项:
	a.千万不要在一个模态框上重叠另一个模态框,要想同时支持多个模态框，需要自己写额外的代码来实现
    b.务必将模态框的 HTML 代码放在文档的最高层级内（也就是说，尽量作为 body 标签的直接子元素），以避免其
      他组件影响模态框的展现和使用

2.创建模态框
  a.在页面中生成模态框 注意:默认书写模态框在页面中没有展示 需要手动展示
	<div class="modal fade" id="myModal" data-backdrop="false" data-keyboard="false" tabindex="-1" role="dialog">
    <div class="modal-dialog" role="document">
        <div class="modal-content">
            <div class="modal-header">
                <button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>
                <h4 class="modal-title">Modal title</h4>
            </div>
            <div class="modal-body">
                <p>One fine body&hellip;</p>
            </div>
            <div class="modal-footer">
                <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
                <button type="button" class="btn btn-primary">Save changes</button>
            </div>
        </div><!-- /.modal-content -->
    </div><!-- /.modal-dialog -->
</div><!-- /.modal -->

	b.使用javascript代码通过参数形式展示
		$("#myModal").modal({
                show:true,//初始化后立即展示
         });
	c.设置其他参数直接在模态框中标签中使用data-参数形式进行设置
	<div class="modal fade" id="myModal" data-backdrop="false" data-keyboard="false" tabindex="-1">
    </div>
```

## 24.2 动态实例

```html
1.模态框在创建时是隐藏不可见的
<div class="modal fade" id="myModal" tabindex="-1">
    <div class="modal-dialog">
        <div class="modal-content">
            <!--模态框标题-->
            <div class="modal-header">
                <!--
                    用来关闭模态框的属性:data-dismiss="modal"
                -->
                <button type="button" class="close" data-dismiss="modal" ><span >&times;</span></button>
                <h4 class="modal-title">编辑用户信息</h4>
            </div>

            <!--模态框内容体-->
            <div class="modal-body">

                <form action="" class="form-horizontal">

                    <div class="form-group">
                        <label class="col-sm-2 control-label">用户名</label>
                        <div class="col-sm-10">
                            <input type="text" name="name" id="name" placeholder="请输入姓名" class="form-control">
                        </div>
                    </div>

                </form>

            </div>

            <!--模态页脚-->
            <div class="modal-footer">
                <button type="button" class="btn btn-primary">保存</button>
                <button type="button" class="btn btn-danger" data-dismiss="modal">取消</button>
            </div>

        </div>
    </div>
</div>

2.展示模态框可以调用模态框的方法
	$("#myModal").modal('show');

3.使用模态框中事件
$("#myModal").on("show.bs.modal",function () {
	console.log("1");
});

$("#myModal").on("shown.bs.modal",function () {
	console.log("2");
})

//监听隐藏事件
$("#myModal").on("hide.bs.modal",function () {
	console.log("3");
})

$("#myModal").on("hidden.bs.modal",function () {
	console.log("4");
})
```

## 25. 标签页

### 25.1 标签页动态实例

```html
<!--标签-->
    <ul class="nav nav-tabs">
        <li class="active"><a href="#list" data-toggle="tab">用户列表</a></li>
        <li><a href="#saveInfo" data-toggle="tab">用户添加</a></li>
        <li class="dropdown">
            <!--触发器-->
            <a href="" class="dropdown-toggle" data-toggle="dropdown">
                下拉菜单 <span class="caret"></span>
            </a>
            <!--下拉菜单-->
            <ul class="dropdown-menu">
                <li><a href="#SpringMvc" data-toggle="tab">SpringMVC</a></li>
                <li><a href="#SpringBoot" data-toggle="tab">SpringBOOT</a></li>
            </ul>
        </li>
    </ul>

    <!--标签内容组-->
    <div class="tab-content">
        <!--标签内容面板-->
        <div class="tab-pane active" id="list">A</div>

        <div class="tab-pane" id="saveInfo">B</div>
        <div class="tab-pane" id="SpringMvc">SpringMvc</div>
        <div class="tab-pane" id="SpringBoot">SpringBoot</div>
    </div>
```

## 25.1 胶囊式标签页动态实例

```html
<ul class="nav nav-pills ">
    <li class="active"><a href="#mvc" data-toggle="pill">Springmvc</a></li>
    <li><a href="#boot" data-toggle="pill">SpringBoot</a></li>
</ul>



<!--标签页内容组-->
<div class="tab-content">
    <div class="tab-pane active" id="mvc">MVC</div>
    <div class="tab-pane" id="boot">Boot</div>
</div>
```

### 25.2 胶囊式标签页方法调用

```html
1.使用tab的展示(show)方法时:
	a.应该使用对应标签页链接id调用tab的show方法进行展示
```

![1552534288358](C:\Users\HIAPAD\AppData\Roaming\Typora\typora-user-images\1552534288358.png)

---

### 25.3 标签页事件的使用

```html
 $('a[data-toggle="pill"]').on('show.bs.tab', function (e) {
    console.log(e.target); //切换之后目标对象
    console.log(e.relatedTarget);  //切换之前的对象
    console.log($(e.target).text());
    console.log($(e.target).attr("name"));
    console.log("1")
})
$('a[data-toggle="pill"]').on('shown.bs.tab', function (e) {
    console.log(e.target); //切换之后目标对象
    console.log(e.relatedTarget);  //切换之前的对象
    console.log("2")
})

$('a[data-toggle="pill"]').on('hide.bs.tab', function (e) {
    console.log(e.target); //切换之后目标对象
    console.log(e.relatedTarget);  //切换之前的对象
    console.log("1")
});

$('a[data-toggle="pill"]').on('hidden.bs.tab', function (e) {
    console.log(e.target); //切换之后目标对象
    console.log(e.relatedTarget);  //切换之前的对象
    console.log("2")
})
```

----

## 26.Accordion组件(手风琴)

### 26.1 基本实例

```html
 <!--创建手风琴实例-->
    <div class="panel-group" id="panelgroup">


        <!--创建面板-->
        <div class="panel panel-default">
            <div class="panel-heading">
                <div class="panel-title">
                    <!--使用连接完成折叠效果-->
                    <a href="#aa" data-toggle="collapse" data-parent="#panelgroup" ><h5>用户管理</h5></a>
                </div>
            </div>

            <div class="panel-collapse collapse" id="aa">
                <div class="panel-body" >
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                </div>
            </div>
        </div>


        <!--创建另一个面板-->
        <div class="panel panel-default">
            <div class="panel-heading">
                <div class="panel-title">
                    <!--使用连接完成折叠效果-->
                    <a href="#bb" data-toggle="collapse" data-parent="#panelgroup" ><h5>用户管理</h5></a>
                </div>
            </div>

            <div class="panel-collapse collapse" id="bb">
                <div class="panel-body" >
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                    <p>标签页(胶囊式)02.html</p>
                </div>
            </div>
        </div>
    </div>
```

### 26.2 带有列表组的手风琴

```html
<!--创建手风琴实例-->
<div class="panel-group" id="panelgroup">


    <!--创建面板-->
    <div class="panel panel-default">
        <div class="panel-heading">
            <div class="panel-title">
                <!--使用连接完成折叠效果-->
                <a href="#aa" data-toggle="collapse" data-parent="#panelgroup" ><h5>用户管理</h5></a>
            </div>
        </div>

        <div class="panel-collapse collapse" id="aa">
            <ul class="list-group">
                <li class="list-group-item"><a href="">用户列表</a></li>
                <li class="list-group-item"><a href="">用户添加</a></li>
            </ul>
        </div>
    </div>


    <!--创建另一个面板-->
    <div class="panel panel-default">
        <div class="panel-heading">
            <div class="panel-title">
                <!--使用连接完成折叠效果-->
                <a href="#bb" data-toggle="collapse" data-parent="#panelgroup" ><h5>类别管理</h5></a>
            </div>
        </div>

        <div class="panel-collapse collapse" id="bb">
            <ul class="list-group">
                <li class="list-group-item">类别列表</li>
                <li class="list-group-item">添加类别</li>
            </ul>
        </div>
    </div>
  
</div>
```

### 26.3 手风琴方法使用

```html
1.调用手风琴方法:
	a.使用对应面板的内容的id调用collapse的相关方法  (使用隐藏内容的唯一标识调用方法)

2.代码如下
 <!--创建面板-->
        <div class="panel panel-default">
            <div class="panel-heading">
                <div class="panel-title">
                    <!--使用连接完成折叠效果-->
                    <a href="#aa" data-toggle="collapse" data-parent="#panelgroup" ><h5>用户管理</h5></a>
                </div>
            </div>

            <div class="panel-collapse collapse in" id="aa">
                <ul class="list-group">
                    <li class="list-group-item"><a href="">用户列表</a></li>
                    <li class="list-group-item"><a href="">用户添加</a></li>
                </ul>
            </div>

        </div>

//展开指定面板
$("#aa").collapse('show');
$("#aa").collapse('toggle');
$("#aa").collapse('hide');
```

### 26.4 事件的使用

```html
1.监听指定面板的事件
<!--创建手风琴实例-->
    <div class="panel-group" id="panelgroup">

        <!--创建面板-->
        <div class="panel panel-default">
            <div class="panel-heading">
                <div class="panel-title">
                    <!--使用连接完成折叠效果-->
                    <a href="#aa" data-toggle="collapse" data-parent="#panelgroup" ><h5>用户管理</h5></a>
                </div>
            </div>

            <div class="panel-collapse collapse in" id="aa">
                <ul class="list-group">
                    <li class="list-group-item"><a href="">用户列表</a></li>
                    <li class="list-group-item"><a href="">用户添加</a></li>
                </ul>
            </div>

        </div>


        <!--创建另一个面板-->
        <div class="panel panel-default">
            <div class="panel-heading">
                <div class="panel-title">
                    <!--使用连接完成折叠效果-->
                    <a href="#bb" data-toggle="collapse" data-parent="#panelgroup" ><h5>类别管理</h5></a>
                </div>
            </div>

            <div class="panel-collapse collapse" id="bb">
                <ul class="list-group">
                    <li class="list-group-item">类别列表</li>
                    <li class="list-group-item">添加类别</li>
                </ul>
            </div>
        </div>
    </div>


2.监听指定面板事件
	$('#aa').on('show.bs.collapse', function () {
    	console.log("1")
    });

    $('#aa').on('shown.bs.collapse', function () {
    	console.log("2")
    });

3.监听所有面板的事件
	 $('.collapse').on('show.bs.collapse',function () {
    	console.log("1");
     });
```

