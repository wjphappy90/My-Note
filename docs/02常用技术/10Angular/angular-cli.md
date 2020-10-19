![illustration-home-inverted.91b07808be](./media/illustration-home-inverted.91b07808be.png)

## 安装

## 依赖

- Node 6.9.0 or higher
- NPM 3 or higher
- Python
- C++ 编译工具

## 安装

```shell
npm install -g @angular/cli
```

## 使用帮助

```shell
ng help
```

## 初始化项目

```shell
ng new <项目名称>
```

## 启动开发服务

```shell
ng serve
```

`ng serve` 默认占用 `4200` 端口号，可以通过下面选项配置：

```shell
ng serve --port 4201
```

## 创建组件，指令，过滤器和服务

```shell
# 创建组件
ng generate component my-new-component

# 创建组件别名
ng g component my-new-component # using the alias

# components support relative path generation
# if in the directory src/app/feature/ and you run
ng g component new-cmp
# your component will be generated in src/app/feature/new-cmp
# but if you were to run
ng g component ../newer-cmp
# your component will be generated in src/app/newer-cmp
# if in the directory src/app you can also run
ng g component feature/new-cmp
# and your component will be generated in src/app/feature/new-cmp
```

可辅助创建资源的功能列表：

| Scaffold                                 | Usage                             |
| ---------------------------------------- | --------------------------------- |
| [Component](https://github.com/angular/angular-cli/wiki/generate-component) | `ng g component my-new-component` |
| [Directive](https://github.com/angular/angular-cli/wiki/generate-directive) | `ng g directive my-new-directive` |
| [Pipe](https://github.com/angular/angular-cli/wiki/generate-pipe) | `ng g pipe my-new-pipe`           |
| [Service](https://github.com/angular/angular-cli/wiki/generate-service) | `ng g service my-new-service`     |
| [Class](https://github.com/angular/angular-cli/wiki/generate-class) | `ng g class my-new-class`         |
| [Guard](https://github.com/angular/angular-cli/wiki/generate-guard) | `ng g guard my-new-guard`         |
| [Interface](https://github.com/angular/angular-cli/wiki/generate-interface) | `ng g interface my-new-interface` |
| [Enum](https://github.com/angular/angular-cli/wiki/generate-enum) | `ng g enum my-new-enum`           |
| [Module](https://github.com/angular/angular-cli/wiki/generate-module) | `ng g module my-module`           |

angular-cli will add reference to `components`, `directives` and `pipes` automatically in the `app.module.ts`. If you need to add this references to another custom module, follow this steps:

1. `ng g module new-module` to create a new module
2. call `ng g component new-module/new-component`

This should add the new `component`, `directive` or `pipe` reference to the `new-module` you've created.

## 在脚手架项目中使用 SASS 预处理器

SASS 是一款非常好用的 CSS 预编译器，Bootstrap 官方从4.0开始已经切换到了 SASS。

如果想要在脚手架项目中使用 SASS 预处理器，我们需要自己手动修改一些配置文件，请按照以下步骤依次修改：

- angular-cli.json 里面的 styles.css 后缀改成  `.scss`

![1515424529111](media/1515424529111.png)

当你后面再使用 `ng g c ***` 自动创建组件的时候，默认就会生成 `.scss` 后缀的样式文件了。



- angular-cli.json 里面的 styleExt 改成 .scss

![1515424609137](media/1515424609137.png)

- src 下面 styles.css 改成 styles.scss

![1515424718388](media/1515424718388.png)

- app.component.scss

![1515424763294](media/1515424763294.png)

- app.component.ts 里面对应修改

![1515424806351](media/1515424806351.png)

改完之后，重新 `ng serve`，打开浏览器查看效果。

SASS 的 API 请参考[官方网站](http://sass-lang.com/) 。

**SASS 只是一个预编译器，它支持所有 CSS 原生语法。利用 SASS 可以提升你的 CSS 编码效率，增强 CSS 代码的可维护性，但是千万不要幻想从此就可以不用学习 CSS 基础知识了。**

## 更新 Angular CLI

## 其它

### 切换包管理器

```shell
# 默认为 npm
ng set --global packageManager=npm

# 将包管理器设置为 yarn
ng set --global packageManager=yarn

# 将包管理器设置为 cnpm
ng set --global packageManager=cnpm
```

## 详细参考文档

> https://github.com/angular/angular-cli/wiki