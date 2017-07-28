## 全局安装vue-cli
```
npm i -g vue-cli
```

## 在项目开发目录，通过vuecli初始化项目
```
vue init webpack 项目名称
```

## 进入项目目录
```
cd 项目名称<文件夹名称>
```

## 安装依赖包
```
npm i
```

## 编译运行项目
```
npm run dev

```








---


# 前后端项目开启

1. 开启mongodb服务器
```
mongod --dbpath=解压后的db存放目录
```
2. 进入BackEnd目录，开启后端web服务器
```
node Server.js
```
或者安装热重载工具：supervisor
```
npm i -g supervisor
```
使用热重载启动web服务器
```
supervisor start Server.js
```
3. 进入FrontEnd目录，开启前端服务器
```
npm run dev
```

#### 其他一些开发工具
1. postMan : 抓包工具，web接口测试工具
2. Robomongo : mongodb客户端GUI管理工具
3. vue.js devtools : vue.js的chrome调试工具
