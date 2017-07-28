## 函数的执行

 - 函数() 就可以执行函数，其实就是通过 () 运算符 来（执行）运算 前面的函数。
 - 我们一般都会给函数起个名字，方便在不同的地方去调用和复用，所以，如果一个变量里面存的是函数的话，那么也可以直接通过 变量名() 来执行。
 - 如果直接在一个函数申明后面加括号，会有问题，如果前面是函数的申明方式，不能直接加()去执行，我们可以使用函数名，或者把前面的函数申明变成一个表达式
 > 一个函数 执行完成以后 会有结果的
   默认情况下函数的返回结果是：undefined
   我们可以在函数执行过程中使用 return 语句 指定函数执行后的返回结果
   返回的值是 函数的最终 执行的结果，值是7大类型之一
```
函数自执行：
(function fn() {
        console.log('fn....');
    })();

     function fn() {
        console.log('fn....');
    }();

    -function fn() {
        console.log('fn....');
    }();
    
    ~function fn() {
        console.log('fn....');
    }();    
    
    0*function fn() {
        console.log('fn....');
    }();
  
    console.log(3+function fn() {
            return 1;
        }());


    function todo() {
        console.log('todo');
        return function() {
            console.log('我就没错');
        }
    }

    document.onclick = todo();

    document.onclick();
    document.onclick = 1;
```
# this
> 上下文对象：
> 1. 上下文:语境、环境、作用域 (分全局和函数)；
> 2. 对象：Object      (一个根据环境（作用域）的变换而发生改变的对象)；

 1. 当我们在全局环境下面调用this的时候，this == window对象，
  **window对象是整个javascript对象最顶点**
2. 在函数中调用this：this的值由当前函数执行的时候来确定，默认情况下，一个函数中的this，指向调用该函数的前置对象
 


```
console.log(window);
console.log(this);

function fn() {
    console.log(this);
}

在js中有规定，约定：如果一个属性或方法是通过
window对象调用的，那么window可以省略不写

fn();
window.fn();

var p = {
    a: 100,
    b: fn
}
p.b(); 
所以当一个函数被事件调用的时候，那么该函数的
this就是触发该事件的对象 

document.onclick = function() {      
console.log(this); 
}
document.onclick()

var div = document.querySelector('div');
var a = 1;
function fn() {
    console.log(document);
    console.log(this);
}

 div.onclick = fn;   //div.onclick()
 document.onclick = fn;  //document.onclick();
 document.body.onclick = fn; //document.body.onclick()
```
## arguments 对象
- 该对象只能在函数中才能调用
-  当一个函数被调用的时候，自动会创建一个对象，名字：arguments
- 该对象下面保存了，函数在调用的时候传入的实参数据

>   用处：当参数个数不确定或可变的时候，通过形参就不好确定参数，可以通过arguments来获取


```
例如：
function plusplus() {
     var result = arguments[0];
     for (var i=1; i<arguments.length; i++ ) {
            result += arguments[i];
        }
        console.log(result);
    }

plusplus(1,2,5,7,9,3,20,30);
```
