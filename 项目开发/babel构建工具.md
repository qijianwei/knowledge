## babel
1.npm install -g babel-cli 安装全局babel

2.进入项目目录，输入命令：npm init，生成package.json文件（package.json);

<!--3.输入命令：npm install webpack
--save-dev为项目添加webpack依赖（其实就是node-modules-->）

4到指定的目录src底下创建一个1.js,写入es6格式的js文件，然后在同级里添加一个dist文件

5.es6格式js创建好了，还需要安装es2015（因为es6需要编译成es5的）
npm install --save-dev babel-preset-es2015

6.最终编译命令：babel src/1.js -o dist/2.js --presets es2015（把你写好的es6格式的1.js指向到dist/1.js里并编译成es5的）



