## 起步

下载模板：

```shell
git clone https://github.com/tastejs/todomvc-app-template.git --depth 1
```

初始化项目：

```shell
ng new todomvc-angular
cd todomvc-angular
ng serve
```

将 `todomvc-angular\src\app\app.component.html` 文件内容替换如下：

```html
<section class="todoapp">
  <header class="header">
    <h1>todos</h1>
    <input class="new-todo" placeholder="What needs to be done?" autofocus>
  </header>
  <!-- This section should be hidden by default and shown when there are todos -->
  <section class="main">
    <input id="toggle-all" class="toggle-all" type="checkbox">
    <label for="toggle-all">Mark all as complete</label>
    <ul class="todo-list">
      <!-- These are here just to show the structure of the list items -->
      <!-- List items should get the class `editing` when editing and `completed` when marked as completed -->
      <li class="completed">
        <div class="view">
          <input class="toggle" type="checkbox" checked>
          <label>Taste JavaScript</label>
          <button class="destroy"></button>
        </div>
        <input class="edit" value="Create a TodoMVC template">
      </li>
      <li>
        <div class="view">
          <input class="toggle" type="checkbox">
          <label>Buy a unicorn</label>
          <button class="destroy"></button>
        </div>
        <input class="edit" value="Rule the web">
      </li>
    </ul>
  </section>
  <!-- This footer should hidden by default and shown when there are todos -->
  <footer class="footer">
    <!-- This should be `0 items left` by default -->
    <span class="todo-count"><strong>0</strong> item left</span>
    <!-- Remove this if you don't implement routing -->
    <ul class="filters">
      <li>
        <a class="selected" href="#/">All</a>
      </li>
      <li>
        <a href="#/active">Active</a>
      </li>
      <li>
        <a href="#/completed">Completed</a>
      </li>
    </ul>
    <!-- Hidden if no completed items are left ↓ -->
    <button class="clear-completed">Clear completed</button>
  </footer>
</section>
<footer class="info">
  <p>Double-click to edit a todo</p>
  <!-- Remove the below line ↓ -->
  <p>Template by <a href="http://sindresorhus.com">Sindre Sorhus</a></p>
  <!-- Change this out with your name and url ↓ -->
  <p>Created by <a href="http://todomvc.com">you</a></p>
  <p>Part of <a href="http://todomvc.com">TodoMVC</a></p>
</footer>

```

安装模板依赖的样式文件：

```shell
npm install todomvc-app-css
```

在 `todomvc-angular\src\styles.css` 文件中导入样式文件：

```css
/* You can add global styles to this file, and also import other style files */
@import url('../node_modules/todomvc-app-css/index.css');
```

看到如下页面说明成功。

![todomvc-angular](./media/todomvc-angular.png)

