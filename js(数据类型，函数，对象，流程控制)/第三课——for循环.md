# for
### 对象操作
当 key 命名不符合js变量命名规则的时候，需要使用 双引号 包含起来，值可以是js中7种数据类型中的任意一种，包括对象类型的

当key是数字的时候，创建的时候，可以不加引号


```
var a = {
    username: '妙味',
    'user-name': 'miaov',
    teachers: {
        leo: '刘胖子',
        motao: '莫胖子'
    },
    5: true,
    '5': false
};
```
* 我们需要通过 . 运算符去获取对象中的数据(成员)
* 结合性：left to right
* 如果 我们要获取的成员名称不符合命名规则，那么需要通过 [] 运算符 去获取，注意，这样的名字是字符串，所以[]中的名字也是应该和其对应



```
console.log( a['5'] );
console.log(a[5]);
```

* 如果key是数字，那么也是不可以使用 .，需要使用 []，但是可以不是字符串


### 元素的操作
* 文档 -> 对象  DOM

```
var lis = document.querySelectorAll('li');
lis[0].style.background = 'red';
```


## for
当我们需要完成重复操作的时候,可以通过循环的语法结构来完成

```
for( var i=0(初始化);i<10(循环条件);i++(改变判断条件) ){
    需要重复做的事情
}
```
> 注意:循环条件(终止和次数) 核心:终止条件    
> 当循环条件为真的时候,执行重复需要做的事情    
> i++  =  i=i+1  = i+=1

### this
当一个函数是被某个事件去调用,那么这个函数中有一个变量(系统自动创建)===>this,它表示触发当前事件的对象

## 自定义属性

```
    var lis = document.querySelectorAll('li');


    for (var i=0; i< lis.length; i++) {
        lis[i].miaov = i;//自定义一个miaov

        lis[i].onclick = function() {
            console.log( this.miaov );
        }

    }
```

## 选项卡的原理
*  获取所有选项 button
*  给所有 button 添加click函数
*  当某个button被click的时候，执行函数
    *    隐藏当前显示的内容
    *    显示和当前点击按钮对应的

```
        var btns = document.querySelectorAll('button');
        var divs = document.querySelectorAll('div');

        // 表示 当前显示的 第几个
        var n = 0;

        for (var i=0; i<btns.length; i++) {

            btns[i].index = i;

            //给每一个button添加click函数
            btns[i].onclick = function() {

                // 取消当前的button的样式
                btns[n].style.background = '';
                // 取消当前显示的内容div
                divs[n].style.display = 'none';

                // 给当前点击的button添加样式
                this.style.background = 'yellow';
                // 显示当前点击的按钮对应的div
                divs[this.index].style.display = 'block';

                //把n的值设置成当前点击的按钮的 序号
                n = this.index;

            }

        }
```
