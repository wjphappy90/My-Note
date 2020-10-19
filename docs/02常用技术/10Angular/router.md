## 基本用法

1. 添加 `AppRoutingModule`

```shell
ng generate module app-routing --flat --module=app
```

`app-routing.module.ts`

```typescript
import { NgModule }             from '@angular/core';
import { RouterModule, Routes } from '@angular/router';

import { FooComponent } from './foo/foo.component'
import { BarComponent } from './bar/bar.component'

const routes: Routes = [
  {
    path: 'foo',
    component: FooComponent
  },
  {
    path: 'bar',
    component: BarComponent
  }
]

@NgModule({
  imports: [
    RouterModule.forRoot(routes)
  ],
  exports: [ RouterModule ]
})
export class AppRoutingModule {}

```

设置路由出口：

```html
<h1>{{title}}</h1>
<router-outlet></router-outlet>
```

设置导航链接：

```html
<ul>
  <li>
    <a routerLink="/foo">Go Foo</a>
  </li>
  <li>
    <a routerLink="/bar">Go Foo</a>
  </li>
</ul>
```

## 导航链接 routerLink

## 路由对象

- path
  - 不能以 `/` 开头
- component

默认路由：

```
{ path: '', redirectTo: '/dashboard', pathMatch: 'full' },
```



## 动态路由匹配

动态路径配置：

```
{ path: 'detail/:id', component: HeroDetailComponent },
```

导航链接：

```
<a *ngFor="let hero of heroes" class="col-1-4"
    routerLink="/detail/{{hero.id}}">
```

在组件中解析获取动态路径参数：

```typescript
import { Component, OnInit } from '@angular/core';
import { ActivatedRoute } from '@angular/router';
import { Location } from '@angular/common';

@Component({
  selector: 'app-user',
  templateUrl: './user.component.html',
  styleUrls: ['./user.component.css']
})
export class UserComponent implements OnInit {

  constructor(
    private route: ActivatedRoute,
    private location: Location
  ) { }

  ngOnInit() {
    const id = this.route.snapshot.paramMap.get('id')
    console.log(id)
  }

}

```

## 路由导航

后退：

```typescript
this.location.back();
```



