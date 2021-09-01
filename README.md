# Front-End-Interview(前端开发面试题)

## Javascript部分

- **JavaScript的数据类型都有什么？**
    - 基本数据类型：String,Boolean,Number,Undefined, Null
    - 引用数据类型：Object(Array,Date,RegExp,Function)

- **当一个DOM节点被点击时候，我们希望能够执行一个函数，应该怎么做？**
    - 直接在DOM里绑定事件：`<div onclick='test()'></div>`
    - 在JS里通过onclick绑定：`xxx.onclick = test`
    - 通过事件添加进行绑定：`addEventListener(xxx, 'click', test)`

- **那么问题来了，Javascript的事件流模型都有什么？**
    - “事件冒泡”：事件开始由最具体的元素接受，然后逐级向上传播
    - “事件捕捉”：事件由最不具体的节点先接收，然后逐级向下，一直到最具体的
    - “DOM事件流”：三个阶段：事件捕捉，目标阶段，事件冒泡

- **看下列代码,输出什么？解释原因**

    ```javascript
        var a = null;
        alert(typeof a); //object

        // null是一个只有一个值的数据类型，这个值就是null。表示一个空指针对象，所以用typeof检测会返回”object”。
    ```
 

- **看下列代码,输出什么？解释原因。**
```js
    var undefined;
    undefined == null; // true
    1 == true;   // true
    2 == true;   // false
    0 == false;  // true
    0 == '';     // true
    NaN == NaN;  // false
    [] == false; // true
    [] == ![];   // true


    // undefined与null相等，但不恒等（===）
    // 一个是number一个是string时，会尝试将string转换为number
    // 尝试将boolean转换为number，0或1
    // 尝试将Object转换成number或string，取决于另外一个对比量的类型
    // 所以，对于0、空字符串的判断，建议使用 “===” 。“===”会先判断两边的值类型，类型不匹配时为false。
```

- **那么问题来了，看下面的代码，输出什么，foo的类型为什么？**
```js
    var foo = "11"+2-"1";
    console.log(foo);
    console.log(typeof foo);

    // 执行完后foo的值为111，foo的类型为Number。
```

```js
    var foo = "11"+2+"1";    //体会加一个字符串'1' 和 减去一个字符串'1'的不同
    console.log(foo);
    console.log(typeof foo);

    // 执行完后foo的值为1121(此处是字符串拼接)，foo的类型为String。
```

- **已知数组var stringArray = [“This”, “is”, “Baidu”, “Campus”]，Alert出”This is Baidu Campus”。**
```js
    alert(stringArray.join(" "))
```

- **那么问题来了，已知有字符串foo="get-element-by-id",写一个function将其转化成驼峰表示法"getElementById"。**
```js
    function combo(msg){
        var arr = msg.split("-");
        var len = arr.length;    //将arr.length存储在一个局部变量可以提高for循环效率
        for(var i=1;i<len;i++){
            arr[i]=arr[i].charAt(0).toUpperCase()+arr[i].substr(1,arr[i].length-1);
        }
        msg=arr.join("");
        return msg;
    }

    // 考察基础API
```

- **var numberArray = [3,6,2,4,1,5];**
    - 实现对该数组的倒排，输出[5,1,4,2,6,3]
    - 实现对该数组的降序排列，输出[6,5,4,3,2,1]
```js
    var numberArray = [3,6,2,4,1,5];
        numberArray.reverse(); // 5,1,4,2,6,3
        numberArray.sort(function(a,b){  //6,5,4,3,2,1
        return b-a;
    })

    // 考察基础API
```

- **输出今天的日期，以YYYY-MM-DD的方式，比如今天是2014年9月26日，则输出2014-09-26**
```js
    var d = new Date();
    // 获取年，getFullYear()返回4位的数字
    var year = d.getFullYear();
    // 获取月，月份比较特殊，0是1月，11是12月
    var month = d.getMonth() + 1;
    // 变成两位
    month = month < 10 ? '0' + month : month;
    // 获取日
    var day = d.getDate();
    day = day < 10 ? '0' + day : day;
    alert(year + '-' + month + '-' + day);
```

- **将字符串”<tr><td>{$id}</td><td>{$name}</td></tr>”中的{$id}替换成10，{$name}替换成Tony**
```js
    "<tr><td>{$id}</td><td>{$id}_{$name}</td></tr>".replace(/{$id}/g, '10').replace(/{$name}/g, 'Tony');

    // 使用正则表达式
```

- **foo = foo || bar ，这行代码是什么意思？为什么要这样写？**
    - if(!foo) foo = bar; //如果foo存在，值不变，否则把bar的值赋给foo。
    - 短路表达式：作为"&&"和"||"操作符的操作数表达式，这些表达式在进行求值时，只要最终的结果已经可以确定是真或假，求值过程便告终止，这称之为短路求值。

- **看下列代码，将会输出什么?** (变量声明提升)
```js
    var foo = 1;
    function(){
        console.log(foo);
        var foo = 2;
        console.log(foo);
    }

    // 输出undefined 和 2。上面代码相当于：

    var foo = 1;
    function(){
        var foo;
        console.log(foo); //undefined
        foo = 2;
        console.log(foo); // 2;  
    }
```
