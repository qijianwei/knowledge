## gulp合成雪碧图

具体文档：
 https://www.npmjs.com/package/gulp-css-spriter
 
需要安装的东西
## Install
```
1.npm install --save-dev gulp (作为项目的开发依赖（devDependencies）安装)
2.npm install gulp-css-spriter （安装插件）
```


新建gulpfile.js文件，在里面配置以下任务：
```
var gulp = require('gulp');
var spriter = require('gulp-css-spriter');
 
gulp.task('task3', function() {
    gulp.src('src/css/*.css')
    .pipe( spriter({
        //合成的雪碧图位置
        spriteSheet: './dist/images/spritesheet.png',
        pathToSpriteSheetFromCSS: '../images/spritesheet.png' //新的css文件引用雪碧图路径
    }) )
    .pipe(gulp.dest('./dist/css')); //新的.css文件所在位置
});

```


```
如果有些图片不想合并进雪碧图，配置以下注释
background: url('../images/dummy-blue.png'); /* @meta {"spritesheet": {"include": false}} */

```
注意：

1.全局下安装gulp的话，进入到项目目录，gulp执行

2.gulp安装在开发依赖里面的话，先进入到项目的bin目录，gulp+'任务名'执行；



## webpack 和gulp优劣
gulp:专一，任务调度
webpack1：模块化打包
webpack2:做的事情较多，配置相对较难