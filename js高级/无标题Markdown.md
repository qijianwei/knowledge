## 路由
 当用户请求方式和请求路径与下面的绑定函数匹配，那么该函数就会被执行
*   路由：把一个http的请求方式和请求路径 与 一个函数进行绑定，当请求方式和请求路径都匹配的时候，执行该绑定函数
*   每一个路由都可以有一个或者多个处理器函数，当匹配到路由时，这个/些函数将被执行。
   
    格式：
    
      app.METHOD(PATH, HANDLER)
        
         app 是一个 express 实例
         METHOD：http中的某个请求方式：get、post
         HANDLER：某个路由绑定的执行函数

```
app.get('/', function (req, res) {

    res.send('<h1>首页</h1>');

});
```
## 托管publish目录
1. 当用户发送一个请求以后，express就会把当前请求的url指向到被托管的目录下进行查找，并读取文件，最后返回文件内容
**ForExample:**/html/index.html => public/html/index.html

```
app.use( express.static('public') );
```
2.我们也可以指定给一个前缀url，那么只有当用户访问的url前缀满足这个要求以后，才把该url和express.static('public')进行绑定

```
(static/miaov/leo/html/index.html=>/public/html/index.html)
app.use( '/static', express.static('public') );
```

## 模板引擎设置
1. 查找 app.set('views', './views'); 设置目录
2. 按照app.set('view engine', 'miaov');app.engine('miaov', jade.renderFile);设置名称作为后缀