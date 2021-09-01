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
