> 内容纲要
>
> - 项目结构介绍
> - 了解一个 Angular 应用是如何启动的



![ng启动过程.png](./media/ng启动过程.png)

## 目录结构

```
.
├── e2e 端到端测试（暂且不关心）
├── node_modules npm安装的第三方包
├── src 存放业务源码
├── .angular-cli.json AngularCLI脚手架工具配置文件
├── .editorconfig 针对编辑器的代码风格约束
├── .gitignore Git仓库忽略配置项
├── karma.conf.js 测试配置文件（给karma用的，暂且不用关心）
├── package.json 项目包说明文件
├── protractor.conf.js 端到端测试配置文件（暂且不用关心）
├── README.md 项目说明文件
├── tsconfig.json TypeScript配置文件
└── tslint.json TypeScript代码风格校验工具配置文件（类似于 eslint）
```



## `npm scripts` 介绍

```
...
"scripts": {
    "ng": "ng", 运行查看 Angular CLI 脚手架工具使用帮助
    "start": "ng serve", 运行开发模式
    "build": "ng build --prod", 运行项目打包构建（用于发布到生成环境）
    "test": "ng test", 运行karma单元测试
    "lint": "ng lint", 运行TypeScript代码校验
    "e2e": "ng e2e" 运行protractor端到端测试
  },
...
```



## `.angular-cli.json` 文件

```json
{
  "$schema": "./node_modules/@angular/cli/lib/config/schema.json",
  "project": {
    "name": "my-app"
  },
  "apps": [
    {
      "root": "src", 源码根目录
      "outDir": "dist", 打包编译结果目录
      "assets": [ 存放静态资源目录
        "assets",
        "favicon.ico"
      ],
      "index": "index.html", 单页面
      "main": "main.ts", 模块启动入口
      "polyfills": "polyfills.ts", 用以兼容低版本浏览器不支持的 JavaScript 语法特性
      "test": "test.ts", 测试脚本
      "tsconfig": "tsconfig.app.json",
      "testTsconfig": "tsconfig.spec.json",
      "prefix": "app", 使用脚手架工具创建组件的自动命名前缀
      "styles": [ 全局样式文件
        "styles.css"
      ],
      "scripts": [], 全局脚本文件
      "environmentSource": "environments/environment.ts",
      "environments": {
        "dev": "environments/environment.ts",
        "prod": "environments/environment.prod.ts"
      }
    }
  ],
  "e2e": { 端到端测试相关配置
    "protractor": {
      "config": "./protractor.conf.js"
    }
  },
  "lint": [ TypeScript代码风格校验相关配置
    {
      "project": "src/tsconfig.app.json",
      "exclude": "**/node_modules/**"
    },
    {
      "project": "src/tsconfig.spec.json",
      "exclude": "**/node_modules/**"
    },
    {
      "project": "e2e/tsconfig.e2e.json",
      "exclude": "**/node_modules/**"
    }
  ],
  "test": { karma单元测试相关配置
    "karma": {
      "config": "./karma.conf.js"
    }
  },
  "defaults": { 默认后缀名
    "styleExt": "css",
    "component": {}
  }
}

```

## main.js

- 描述：模块化启动入口
- 职责：加载启动根模块

## AppModule

- 描述：项目根模块
- 职责：把组件、服务、路由、指令等组织到一起，设置启动组件为根组件

## AppComponent

- 描述：项目根组件
- 职责：替换掉 `index.html` 文件中的 `<app-root></app-root>` 节点

## 其它资源

- 资源
- 指令
- 路由
- 服务
- ......