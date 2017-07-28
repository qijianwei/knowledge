## for of
>得到的是value,且循环的是可迭代对象
* 迭代器函数：Symbol(Symbol.iterator)    
* 当一个对象拥有迭代器函数的时候，该对象才能被迭代（forof）
 
 ```
 这个对象为不可迭代对象，但是让它有迭代器就可以迭代
  var obj = {
        x: 100,
        y: 200
    };
  
   // 报错，目前该对象不可迭代
   for (var property of obj) {
       console.log(property);
   }   

    obj[Symbol.iterator] = function () {
        
        //Object.keys(obj) ： 返回一个对象的所有key的集合-数组
        var keys = Object.keys(obj);
        // keys = ['x', 'y']

        /*
        * 迭代对象：
        *   包含一个next方法的对象
        * */
        return {
            next: function() {
                if (keys.length) {
                    var key = keys.shift();
//                    console.log(v);
                   /* return {value: key, done: false} *///for in
                  return {value: obj[key], done: false}
                   /* return {value: [key, obj[key]], done: false}*/
                } else {
                    return {done: true}
                }

            }
        };
    };
    //通过给对象加了Symbol.iterator属性，可循环迭代了
     for(var data of obj){
        console.log(data);  //100，200
    }
 ```
###  以下有惊喜：
 ```
 var arr = ['a', 'b', 'c'];
 //以下两个都是数组的迭代属性
 console.log(arr.entries());
 console.log(arr.keys());
 
 
 var arrInterator = arr.keys();
 //循环一次得到一个值
 console.log( arrInterator.next())
 ```
 
 ## for...of与for...in的区别
1.for...in循环会遍历一个object所有的==可枚举属性==。

2.for...of语法是为各种collection对象专门定制的，并不适用于所有的object.它会以这种方式迭代出任何拥有[Symbol.iterator] 属性的collection对象的每个元素。

3.下面的例子演示了for...of 循环和 for...in 循环的区别。for...in ==遍历（当前对象及其原型上的）每一个属性名称==,而 for...of遍历（当前对象上的）每一个属性值:
```
Object.prototype.objCustom = function () {}; 
Array.prototype.arrCustom = function () {};

let iterable = [3, 5, 7];
iterable.foo = "hello";

for (let i in iterable) {
  console.log(i); // logs 0, 1, 2, "foo", "arrCustom", "objCustom"
}

for (let i of iterable) {
  console.log(i); // logs 3, 5, 7
}
```