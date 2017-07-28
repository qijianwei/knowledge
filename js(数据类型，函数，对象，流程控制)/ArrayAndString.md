
```
<!DOCTYPE html>
<html lang="zh-cn">

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <meta content="black" name="apple-mobile-web-app-status-bar-style">
    <meta content="telephone=no" name="format-detection">
    <title>字符串与数组</title>
    <style>
    .box {
        padding: 20px;
        background-color: #f0f0f0;
    }
    </style>
    <script>
    // slice(start,end) 
    // 提取字符串的片断，并在新的字符串中返回被提取的部分。不包括end所在的字符，参数可以为负数
    // 返回值：一个新的字符串
    var str = 'hello world!';
    console.log('======slice======');
    console.log(str.slice(6, 8)); // wo
    console.log(str.slice(-2)); // d!
    console.log(str.slice(6, -2)); // worl
    console.log(str.slice(6)); // world!
    console.log('');
    // substr(start,length)
    // 字符串中抽取从 start 下标开始的指定数目的字符。index可以为负数，length可选返回长度
    // 返回值：一个新的字符串
    var str2 = 'how old are you?';
    console.log('======substr======');
    console.log(str2.substr(5)); // ld are you?
    console.log(str2.substr(-4)); // you?
    console.log(str2.substr(-4, 2)); // yo
    console.log('');
    // substring(start,stop)
    // 提取字符串中介于两个指定下标之间的字符。参数不能为负数
    // 其内容是从 start 处到 stop-1 处的所有字符，其长度为 stop 减 start。
    // 如果参数 start 与 stop 相等，那么该方法返回的就是一个空串（即长度为 0 的字符串）。如果 start 比 stop 大，那么该方法在提取子串之前会先交换这两个参数。
    // 返回值：一个新的字符串
    var str3 = 'how old are you?';
    console.log('======substring======');
    console.log(str3.substring(5)); // ld are you?
    console.log(str3.substring(2, 6)); // w ol
    console.log(str3.substring(6, 2)); // w ol
    console.log('');
    // split(separator,howmany)
    // 方法用于把一个字符串分割成字符串数组，分隔符可以是正则表达式或字符串，howmany可选返回长度
    // 返回值：一个字符串数组
    var str4 = 'jay,jam,jane,jj';
    console.log('======split======');
    console.log(str4.split(',')); // ["jay", "jam", "jane", "jj"]
    console.log('');
    // match(searchvalue|regexp)
    // 在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。
    // 返回值：存放匹配结果的数组
    var str5 = 'jay,33jam,2jane,19jj';
    console.log('======match======');
    console.log(str5.match(',')); // [",", index: 3, input: "jay,33jam,2jane,19jj"]
    console.log(str5.match(/\d/gi)); // ["3", "3", "2", "1", "9"]
    console.log('');
    // replace(regexp|substr,replacement)
    // 字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
    // 返回值：一个新的字符串
    var str6 = 'jay,33jam,2jane,19jj';
    console.log('======replace======');
    console.log(str6.replace('33', 66)); // jay,66jam,2jane,19jj
    console.log(str6.replace(/,/g, '#')); // jay#33jam#2jane#19jj
    console.log('');
    // search(regexp)
    // 检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。
    // 返回值：stringObject 中第一个与 regexp 相匹配的子串的起始位置。
    var str7 = 'jay,33jam,2jane,19jj';
    console.log('======search======');
    console.log(str7.search('33')); // 4
    console.log(str7.search('xxx')); // -1
    console.log(str7.search(/jj/)); // 18
    console.log('');
    // charAt(index)
    // 返回指定位置的字符。
    var str8 = 'jay,33jam,2jane,19jj';
    console.log('======charAt======');
    console.log(str8.charAt(7)); // a
    console.log('');
    // concat(stringX,stringX,...,stringX)
    // 连接两个或多个字符串。
    var str9 = 'jay,33jam,2jane,19jj';
    console.log('======concat======');
    console.log(str9.concat(',haha')); // jay,33jam,2jane,19jj,haha
    console.log('');
    // indexOf(searchvalue,fromindex)
    // 返回某个指定的字符串值在字符串中首次出现的位置。如果未找到返回-1
    var str10 = 'jay,33jam,2jane,19jj';
    console.log('======indexOf======');
    console.log(str10.indexOf('2')); // 10
    console.log(str10.indexOf('*')); // -1
    console.log(str10.indexOf('2', 9)); // 10
    console.log('');
    // lastIndexOf(searchvalue,fromindex)
    // 返回一个指定的字符串值最后出现的位置，在一个字符串中的指定位置从后向前搜索。如果未找到返回-1
    var str11 = 'jay,33jam,2jane,19jj';
    console.log('======lastIndexOf======');
    console.log(str11.lastIndexOf('2')); // 10
    console.log(str11.lastIndexOf('9')); // 17
    console.log(str11.lastIndexOf('2', 15)); // 10
    console.log('');
    // 数组方法
    // slice(start,end)
    // 从已有的数组中返回选定的元素。
    // 返回值：返回一个新的数组
    var arr1 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======slice======');
    console.log(arr1.slice(1)); // ["John", "Thomas", "James", "Adrew", "Martin"]
    console.log(arr1.slice(2, 5)); // ["Thomas", "James", "Adrew"]
    console.log('');
    // join(separator)
    // 把数组中的所有元素放入一个字符串。
    // 返回值：返回一个字符串
    var arr2 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======join======');
    console.log(arr1.join('@')); // George@John@Thomas@James@Adrew@Martin
    console.log('');
    // splice(index,howmany,item1,.....,itemX)
    // 向/从数组中添加/删除项目，然后返回被删除的项目。
    // 返回值：包含被删除项目的新数组，如果有的话。
    var arr3 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======splice======');
    arr3.splice(0, 0, 'haha'); // 添加
    console.log(arr3); // ["haha", "George", "John", "Thomas", "James", "Adrew", "Martin"]
    arr3.splice(2, 1, 'Tom'); // 替换
    console.log(arr3); // ["haha", "George", "Tom", "Thomas", "James", "Adrew", "Martin"]
    arr3.splice(3, 1); // 删除
    console.log(arr3); // ["haha", "George", "Tom", "James", "Adrew", "Martin"]
    console.log('');
    // shift()
    // 把数组的第一个元素从其中删除，并返回第一个元素的值。
    var arr4 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======shift======');
    console.log(arr4.shift()); // George
    console.log('');
    // unshift()
    // 方法可向数组的开头添加一个或更多元素，并返回新的长度。
    var arr5 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======unshift======');
    console.log(arr5.unshift('888')); // 7
    console.log('');
    // pop()
    // 方法用于删除并返回数组的最后一个元素。
    var arr6 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======pop======');
    console.log(arr4.pop('')); // Martin
    console.log('');
    // push()
    // 方法可向数组的末尾添加一个或多个元素，并返回新的长度。
    var arr7 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======push======');
    console.log(arr7.push('222')); // 7
    console.log('');
    // reverse()
    // 方法用于颠倒数组中元素的顺序。
    var arr8 = ['George', 'John', 'Thomas', 'James', 'Adrew', 'Martin'];
    console.log('======reverse======');
    console.log(arr8.reverse()); // ["Martin", "Adrew", "James", "Thomas", "John", "George"]
    console.log('');
    // sort(sortby)
    // 方法用于对数组的元素进行排序。参数为函数
    // 返回值：对数组的引用
    // 比较函数参数说明：
    //若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
    //若 a 等于 b，则返回 0。
    //若 a 大于 b，则返回一个大于 0 的值。
    var arr9 = [1, 22, 68, 33, 79, 57, 61, 37, 64, 99, 6];
    console.log('======sort======');
    // 从小到大排序
    arr9.sort(function(n1, n2) {
        return n1 - n2;
    });
    console.log(arr9);
    console.log('');
    
    // concat(arrayX,arrayX,......,arrayX)
    // 方法用于连接两个或多个数组。
    var arr10 = [1,2,3];
    console.log('======concat======');
    console.log(arr10.concat(4,5));
    console.log(arr10.concat(['a','b','c']));
    </script>
</head>

<body>
</body>

</html>
```
