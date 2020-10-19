## Angular 是什么

![angular.png](./media/angular.png)

Angular（读音['æŋgjʊlə]）是一套用于构建用户界面的 JavaScript 框架。由 Google 开发和维护，主要被用来开发单页面应用程序。

- 类似于 [Vue.js](https://cn.vuejs.org/)
  + MVVM（数据驱动视图思想）
  + 组件化
  + 模块化
  + 指令
  + ......
- 由 Google 开发和维护
- 开发单页面应用程序（SPA） 

## 特性

- MVVM
- 组件化
- 模块化
- 指令
- 服务
- 依赖注入
- TypeScript
- ...

## 发展历史

### 起源

2009年，Misko hevery 和 Adam abrons 在业余时间打造了 `GetAngular`

![./media/MiskoInterview.png](./media/MiskoInterview.png)

![./media/4529.jpg](./media/4529.jpg)



Misko Hevery 接手了 Google 内部的一个项目 `Feedback` ，该项目经过6个月的迭代代码量已经达到了17000行。项目的开发和维护已经变得非常的困难。所有 Misko 就决定用 `GetAngular` 重写这个项目。

结果就是小伙子成功了，使用 ``GetAngular` 之后该项目从17000行缩减到了1500行，前后仅仅使用了三周时间。

![17000-1500.png](./media/17000-1500.png)

Misko 领导一看，小伙子厉害啊，同时也看到了 `GetAngular` 所带来的商业价值，所以决定把  `GetAngular` 正式立项，组织专职团队开发和维护。

Abrons 后来离开了这个计划，但在 Google 工作的 Hevery 和一些谷歌员工如 Igor Minár 和 Vojta Jína 等则继续开发维护此库。

由于已不再是个人项目，所以开发团队将 `GetAngular` 重新命名为了 `AngularJS` 。

![angularjs](./media/AngularJS-large.png)

至此，AngularJS 就进入了漫长的发展迭代阶段。

- 经过了3年的发展，AngularJS 在2012年6月份，`1.0.0` 版本正式推出。
- AngularJS 在1.2之后的版本不再支持 IE 6和7
- AngularJS 在 1.3 之后不再支持 IE8
- AngularJS 在 1.5 增加了类似组件化的开发方式
  - 为过渡到 Angular2 做铺垫
- AngularJS `1.x.x` 当前已发布到了 `1.6.x`

### 困境

- 饱受诟病的性能问题
  - 脏检查
- 落后于当前 Web 发展理念
  - 例如组件化
  - 模块化支持不好
- 对移动端支持不够友好

### Angular 2 横空出世

Angular 1.x 由于问题太多，历史包袱太重，重构几乎不可能。

不过早在2014年3月，官方博客就有提及开发新版本 Angular 的计划。

2014年9月下旬一个大会上，`Angular2` 正式亮相。

2016年9月15号，`Angular2` 正式发布。

由于 ng2 几乎完全重写了 ng1 ，所以官方把2之后的版本都称之为 Angular。

![Angular-large.png](./media/Angular-large.png)

Angular 2 之后的正式 Logo：

![angular.png](./media/angular.png)

新版本发布了，那用户如何从 1 升级到 2 呢？

![ng2-ng1](./media/ng2-ng1.png)

那到底要不要更新呢？

![1515398136619](media/mountain.png)

### ng2 相比 ng1

- 移除了 controller+$scope 的设计方式，改用了当前主流的组件化构建
- 相比 ng1 性能更好
- 优先为移动端设计
- 更贴合未来标准
  - EcmaScript 6
  - Web Component
- TypeScript
- 反正就是更现代化，更好了......

### 现状

- 自 Angular 2 之后，官方承诺之后的版本都会兼容到 Angular 2
- 当前 Angular 最新发布版为 `5.x.x`
- 新版的 Angular 在 Github 上也已收获了 3万+ ☆
- 使用量低于 React 和 Vue

## 那我为什么要学习使用 Angular ？

任何一种技术或者框架，一定要有自己的特色，如果跟别人的完全一样，解决的问题也和别人一样，那存在的意义和价值就会遭到质疑。

- 企业需求
- 增加职业竞争力
- 技术的本质思想都是一样的，也许你在其它技术中无法理解的事物，在这门课程中你能找到答案。

这里我们要明白技术只是工具，主要目的还是用来帮助我们解决业务问题。
作为开发人员，我们对待技术的态度应该博学开放，多学习和了解不同技术。
只有当你见得东西多了才能有自己的想法，才不会人云亦云，不至于迷失在技术更新迭代的浪潮之中！

## 学习 Angular 的一些建议

![on-my-god.png](./media/on-my-god.png)

- 读官方文档
- 写 demo 测试
- 写小项目练手
- 参与实际项目开发经验
- 日积月累......

这是一个知识开放的时代，我们每个人都拥有一本《九阴真经》，至于你如何利用它产生价值则需要一些方式。我们学习技术就像武侠练功一样，希望大家像郭靖一样拥有坚韧不拔的精神，锲而不舍的探索下去，终成一代大侠。

![img](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1515419600105&di=0adaf3d00289c04fbf2525fa15006255&imgtype=0&src=http%3A%2F%2Fphotocdn.sohu.com%2F20150409%2Fmp10041383_1428590888019_1_th.jpeg)

```
在金庸武侠中，男主角练就上层武功的方法有很多，有意外服用了灵丹妙药的，有机缘巧合得到前辈几十年功力的，有被别人打通任督二脉的，还有武功为什么厉害没有原因的（小说开始就设定东邪、西毒、南帝、北丐、中神通武功厉害，没有为什么），但是郭靖，却是靠自己的努力一步步争取到的。在郭靖成功的每一步上，都有他付出的无数汗水。

郭靖资质愚钝，学习武功，靠的是坚韧不拔；结交朋友，靠的是坦诚相待；树立威望，靠的是侠肝义胆。所以我想，《武穆遗书》和《九阴真经》也只有到了诚朴质实的人手里，才能有号令天下的作用。金毛狮王有屠龙刀，灭绝师太有倚天剑，周芷若两者皆有，但是他们的江湖地位却没有因此提高，也没有人听从他们的号召；只有侠之大者，为国为民的郭靖，能够一统江湖纷争，力挫异族入侵中华的企图。

作者：水边芦苇
链接：https://www.jianshu.com/p/58fee3439ede
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

## 相关链接

- [维基百科 - Angular](https://zh.wikipedia.org/wiki/Angular)
- [AngularJS 1.x.x 官网](https://angularjs.org/)
- [Angular 官网](https://angular.io/)
- [Angular Github](https://github.com/angular/angular)
- [Angular 官方文档](https://angular.io/docs)
- [Angular 官方教程](https://angular.io/tutorial)
- [Angular APi文档](https://angular.io/api)
