# NPM
> Node Package Manager : Node包<模块>管理工具

# package.json
> 一个项目（包）的说明配置文件，这个文件有很多的配置项，通过这些配置项，我们可以对当前项目进行一个管理和维护

# 命令

### install
> 安装package
```
npm install <packagename>@<version>

//安装并写入package.json的dependencies中
npm install <packagename>@<version> -S

//安装并写入package.json的devDependencies中
npm install <packagename>@<version> -D

//安装到全局
npm install <packagename>@<version> -g

```

### init
> 初始化一个项目<包>，并自动创建package.json文件
```
npm init
```

### update
> 更新包
```
npm update <packagename>@<version>
```

### uninstall
> 卸载<删除>包
```
npm uninstall <packagename>@<version>
```


# package.json

> 他是一个json格式的文件，不是js中对象格式，他的key必须使用双引号包含，如果value需要引号的话，也是双引号

### name
> 包的名称

### version
> 包的版本

### 以上两项是必填项

### description
> 简介说明

### author
> 作者

### dependencies
> 依赖管理，申明当前这个项目所依赖的其他第三方的包以及对应的版本