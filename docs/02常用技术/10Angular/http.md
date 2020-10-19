## 启用 Http 服务

- open the root `AppModule`,
- import the `HttpClientModule` symbol from `@angular/common/http`,
- add it to the `@NgModule.imports` array.

```typescript
// app.module.ts:
 
import {NgModule} from '@angular/core';
import {BrowserModule} from '@angular/platform-browser';
 
// Import HttpClientModule from @angular/common/http
import {HttpClientModule} from '@angular/common/http';
 
@NgModule({
  imports: [
    BrowserModule,
    // Include it under 'imports' in your application module
    // after BrowserModule.
    HttpClientModule,
  ],
})
export class MyAppModule {}
```

## 发起一个 get 请求

```typescript
@Component(...)
export class MyComponent implements OnInit {
 
  results: string[];
 
  // Inject HttpClient into your component or service.
  constructor(private http: HttpClient) {}
 
  ngOnInit(): void {
    // Make the HTTP request:
    this.http.get('/api/items').subscribe(data => {
      // Read the result field from the JSON response.
      this.results = data['results'];
    });
  }
}
```

### Reading the full response

```typescript
this.http
  .get('https://jsonplaceholder.typicode.com/posts/1', {observe: 'response'})
  .subscribe(res => {
  console.log(res)
})
```

结果示例：

```

```

## 错误处理

```typescript
http
  .get('/api/items')
  .subscribe(
    // Successful responses call the first callback.
    data => {...},
    // Errors will call this callback instead:
    err => {
      console.log('Something went wrong!');	
    }
  );
```



