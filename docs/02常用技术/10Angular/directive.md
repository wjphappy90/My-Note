在 Angular 中最常用的指令分为两种，它们分别是 **属性型指令** 和 **结构型指令**。

## NgClass

- 作用：添加或移除一组 CSS 类

## NgStyle

- 作用：添加或移除一组 CSS 样式

## NgModel

- 作用：双向绑定到 HTML 表单元素

## NgIf

- 作用：根据条件添加或移除 DOM
- 语法：

```html
<div class="box" *ngIf="false">看不见我</div>
```



我们也可以通过[类绑定](https://angular.cn/guide/template-syntax#class-binding)或[样式绑定](https://angular.cn/guide/template-syntax#style-binding)来显示或隐藏一个元素。

```html
<!-- isSpecial is true -->
<div [class.hidden]="!isSpecial">Show with class</div>
<div [class.hidden]="isSpecial">Hide with class</div>

<div [style.display]="isSpecial ? 'block' : 'none'">Show with style</div>
<div [style.display]="isSpecial ? 'none'  : 'block'">Hide with style</div>
```





## NgSwitch

- 作用：类似于 JavaScript 中的 switch 语句，根据条件渲染多个选项中的一个。
- 语法：该指令包括三个相互协作的指令：`NgSwitch`、`NgSwitchCase`、`NgSwitchDefault`

```html
<div [ngSwitch]="currentHero.emotion">
  <app-happy-hero    *ngSwitchCase="'happy'"    [hero]="currentHero"></app-happy-hero>
  <app-sad-hero      *ngSwitchCase="'sad'"      [hero]="currentHero"></app-sad-hero>
  <app-confused-hero *ngSwitchCase="'confused'" [hero]="currentHero"></app-confused-hero>
  <app-unknown-hero  *ngSwitchDefault           [hero]="currentHero"></app-unknown-hero>
</div>
```



## NgFor

- 作用：列表渲染
- 语法：

```html
<div *ngFor="let hero of heroes">{{hero.name}}</div>
```

### 带索引的 `*ngFor`

```html
<ul>
  <li *ngFor="let item of todos; let i = index">{{ item.title + i }}</li>
</ul>
```

## 自定义指令

> 参考文档：
>
> - 属性型指令：https://angular.io/guide/attribute-directives
> - 结构型指令：https://angular.io/guide/structural-directives