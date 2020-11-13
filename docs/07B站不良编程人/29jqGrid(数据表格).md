# jqGrid  (数据表格)

## 1.使用jqgrid数据表格

### 1). 环境搭建

> 官方下载:      http://www.trirand.com/blog/
>
> 中文网下载:  <http://blog.mn886.net/jqGrid/>

### 2). 如何使用

```html
1.解压压缩包
	核心文件夹:  jqgrid

2.页面中使用
	引入jqgrid中核心css
 	引入jqgrid中国际化语言文件
    引入jqgrid中核心js文件 
	<link rel="stylesheet" href="${app}/boot/css/bootstrap.min.css">
    <%--引入jqgrid中主题css--%>
    <link rel="stylesheet" href="${app}/boot/jqgrid/css/ui.jqgrid.css">
    <%--引入js文件--%>
    <script src="${app}/boot/js/jquery-3.3.1.min.js"></script>
    <script src="${app}/boot/js/bootstrap.min.js"></script>
    <script src="${app}/boot/jqgrid/js/i18n/grid.locale-cn.js"></script>
    <script src="${app}/boot/jqgrid/js/jquery.jqGrid.src.js"></script>
        
        
3.创建jqgrid
    a.页面中含有<table id="list"></table>
    b.生成数据表格
		 //初始化表格
         $("#list").jqGrid({});
```

----

## 2.表格初始化参数使用

```js
1.表格的初始化参数的使用
 	$("#list").jqGrid({   //注意:用来书写初始化参数
                url:"${app}/users.json",//用来加载远程数据
                datatype:"json",  //用来指定返回数据类型
                cellEdit:true,//开启单元格编辑
                autowidth:true,//自适应父容器
                colNames:["ID","姓名","年龄","生日"],   //表格标题
	});

2.常用初始化参数
/*
	url			: 用来指定服务端的url地址 或  用来获取远程数据的url
	datatype	: 用来指定从服务器端返回的数据类型 (默认是:"xml") 使用时:"json" 	 
	colNames	: 用来指定表格列的名称 如 ["id","姓名".....]
	colModel	: 用来指定表格列的名称所对应的数据 注意:colNames和colModel长度必须一致
		 		  使用方式 colModel:[{name:"id".....},{},]
	pager		: 用来指定分页工具栏标签的id  注意:分页工具栏可以放在任意位置
			      使用方式: <div id="aa"></div>    grid中设置:pager:"#aa"
	rowNum		: 用来指定每页显示记录数 默认是:20 后台可以使用:rows变量进行参数接收
				  使用注意: 
				  	a.建议最好是rowList中一个子元素
				  	b.后台可以使用page变量接收当前页
				  	
	rowList		: 用来指定下拉列表中每页显示条数  注意:是一个数组
	viewrecords : 用来显示总记录数
				  使用注意: 
				  	a.一旦加入分页工具栏之后后台响应json数据格式变化为:
				  	{"rows":[当前页结果],"page":"当前页","total":"总页数","records":"总条数"}
				  	
	sortname	: 用来指定使用哪个列作为排序列  注意:后台使用sidx接收排序列结果	  
    caption     : 用来指定表格的标题
    autowidth	: 用来自适应父容器
    cellEdit	: 用来开启单元格的点击修改操作 注意:必须配合colModel中editable属性为true才生效
    editurl		: 用来指定编辑(增删改)时的url
    			  使用注意: 当执行grid中增删改时全部使用当前指定的url
    			  		   如果是保存 会传递一个参数名为oper值:add
    			  		   如果是修改 会传递一个参数名为oper值:edit
    			  		   如果是删除 会传递一个参数名为oper值:del
    hiddengrid	: 用来控制表格是否默认打开
    hidegrid	: 用来控制在使用标题情况下是否显示折叠按钮
    multiselect : 用来控制是否显示checkbox
    page		: 用来指定初始化的页码
    rownumbers  : 用来显示指定行的行号
    toolbar		: 用来指定表格的工具栏 使用方式:	['true','both']
    			  使用注意:
    			  	a.如果只有一个工具栏则为 “t_”+表格id 
    			  	b.如果为both 上面工具栏id为“t_”+表格id；下面则为 “tb_”+表格id；
*/
```

## 3.表格的colModel参数使用

```js
1.表格的colModel属性的使用
$("#list").jqGrid({ 
			colModel:[
                    {name:"id",align:"center",....//用来书写colModel属性},
			]
});

2.常用属性如下:
	
	//name	    	: 用来获取json中指定字段作为该列的数据展示
    //classes	 	: 用来给当前列设置样式 多个样式空格分开
	//align			: 用来设置该列值的对齐方式
	//editable		: 用来控制当前单元格是否可以点击编辑 必须配合初始化属性cellEdit:true使用
                
	//edittype      : 用来指定编辑时的类型 
		/*支持类型(text, textarea, select, checkbox, password, button, image and file.)*/

	//editoptions   : 用来指定编辑类型为select时,select标签的数据获取方式 
        /*editoptions:{value:"1:One;2:Two"}//本地数据
          editoptions:{dataUrl:"数据地址"}//加载远程数据 要求返回的结果必须是准备好select的html
        */
                
	//width			: 用来指定列的宽度
   
	//fixed   		: 用来指定当表格自动适应时,宽度固定
                
	//formatter		: 用来指定对表格列二次渲染值为function(value,options,row){return"渲染结果"}
                
    //hidden        : 用来指定表格在初始化时不显示哪个列
    
    //index    		: 向后台传递的参数(暂时没有实现)
                
    //resizable		: 用来修改当前列是否可以修改大小
    
    //search		: 用来指定该列是否可以参与搜索
               
   	//sortable      : 用来指定该列是否可以参与排序
    
    //surl          : 当该列为搜索列时使用指定的url请求数据(如果不指定默认使用grid的url属性的值)
```

## 4.事件使用方式

```js
1.事件的使用方式
    $("#emplist").jqGrid({
		全局初始化属性:
        ondblClickRow:function(){}//事件......
    })
```

## 5.方法调用

```js
1.方法调用方式
	$("#emplist").jqGrid('方法名',参数列表....);
```

![1.bootstrap的引言](img/1.bootstrap%E7%9A%84%E5%BC%95%E8%A8%80.png)

![2.bootstrap的CDN加速服务](img/2.bootstrap%E7%9A%84CDN%E5%8A%A0%E9%80%9F%E6%9C%8D%E5%8A%A1.png)

![3.页头使用](img/3.%E9%A1%B5%E5%A4%B4%E4%BD%BF%E7%94%A8.png)

![4.jqgrid中分页数据交互](img/4.jqgrid%E4%B8%AD%E5%88%86%E9%A1%B5%E6%95%B0%E6%8D%AE%E4%BA%A4%E4%BA%92.jpg)