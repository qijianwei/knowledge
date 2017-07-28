# GuestBook

### 项目需求
- 首页
> 显示所有的留言（如果留言比较多的话，可以使用分页）
- 注册
> 注册一个唯一的用户，留言需要注册用户才能使用
- 登录
> 登录留言本，进行留言
- 退出
> 退出留言本
- 留言
> 提交数据

### 所需页面
> 首页：/
> 注册：/register
> 登录：/login
> 留言 /post
> 提示页面：/message

### 使用技术
- nodejs
- express
- bootstrap
- jQuery
- swig
- body-parser
- cookie

# step 1
> 初始化项目
```
npm init
```

# step 2
> 安装依赖
- express
```
npm install -S express
```

# step 3
> 创建服务端入口文件 -> Server.js

# step 4
> 安装swig
```
npm install -S swig
```

# step 5
> 在express中设置模板引擎swig

# step 6
> 安装body-parser中间件，用于解析post提交过来的数据

db.students.update({'name':'平'},{$set:{'name':'刘平平'}})

 db.collection.update({}, {$set: {otherkey: ‘gender’}}, {multi: 1})