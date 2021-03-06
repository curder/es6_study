# 变量的赋值

## ES5中常用的赋值用法

在es5中我们定义变量`a`, `b`, `c`的方式可能是：

```
var a = 1;
var b = 2;
var c = 3;
```

或者是：

```
var a = 1, b = 2, c = 3;
```

## ES6中常见的数组赋值用法

在es6中我们定义变量`a`, `b`, `c`的方式进行数组结构赋值是：

```
var [a, b, c] = [1, 2, 3];

var [a, [b, c]] = [1, [2, 3]];
```

或者是忽略`b`变量的值，只定义`a`, `c`两个变量:

```
var [a, , c] = [1, 2, 3]; // 此时 a = 1; c = 3;
```

又或者是将后面的值直接赋值给`c`变量:

```
var [a, ...c] = [1, 2, 3]; // 此时 a = 1; c = [2, 3];
```

### 变量赋值时的默认值

```
var [a, b, c = 'default', d = 'default'] = [1, 2, 3]; // a = 1; b = 2; c = 3; d = 'default';
```

## ES6中常见的对象赋值用法

```
var obj = {
    a: 1,
    b: 2
};
let {a, b} = obj; // 此时 a = 1; b = 2; c = undefined;
```

### 在赋值时自定义变量名

在对象变量赋值时，我们可以使用`:变量名`的形式，将变量名自定义为我们需要的。

```
var obj = {
    a: 1,
    b: 2
};
let {a: A, b, c} = obj; // 此时 A = 1; b = 2; c = undefined; 打印a变量会报错 
```

### 变量赋值时的默认值

```
var {a = 1, b = 2} = {a: 10} // a = 10; b = 2;
// 重命名并指定默认值
var {a:A = 1, b = 2} = {a: 10} // A = 10; b = 2; 打印a变量会报错
```

## 其他

### 在ES6中可以通过解包的方式进行赋值

```
let [a, b, c] = 'Yo.';
console.log(a, b, c); // 此时 a = 'Y'; b = 'o'; c = '.'
```


### 在ES6中我们可以直接对函数的传参进行解包

- 在ES5中，我们的代码可能是这样：

```
var arr = [1, 2];
function test(a, b){
    console.log(a); // 1
    console.log(b); // 2
}
test(arr[0], arr[1]);
```

- 在ES6中，数组传参代码示例：

```
var arr = [1, 2];
function test([a, b = 'default']) { // 如果不传递第二个值，则使用`default`
    console.log(a); // 1
    console.log(b); // 2
}

test(arr);
```

> 上述`test`函数解决了我们变量的传参问题，但是这样写的话规定了我们传参的顺序，我们不能更改，如果在实际开发中，我们需要更改传参的顺序的话，可以使用对象传参的方式。

- ES6中，对象传参示例：

```
var object = {a: 1, b: 2};

function test({a, b = 'default'}) { // 如果不传递第二个值，则使用`default`
    console.log(a); // 1
    console.log(b); // 2
}

test(object);
```
> 上面的写法的话，就不用考虑函数传参的顺序问题。


## 变量赋值在实际开发中的应用

比如当我们在处理一个响应时，我们可以使用ES6的语法简写我们的变量赋值。

```
let res = {
    status : 200,
    message: 'OK',
    data: [
        {name: 'ES6'},
        {name: 'jQuery'},
        {name: 'JavaScript'}
    ]
}

let {status, message, data} = res; // status = 200; message = "OK"; data = [ {name: "ES6"}, {name: "jQuery"}, {name: "JavaScript"} ]
if(status == 200) {
    ...
}
...
```

### 提取对象中的成员方法

我们可以使用ES6下的变量赋值，获取Js内置对象的成员方法，例如：

```
let {floor, pow} = Math;

console.log(floor(2.2)); // 计算的结果是 2
console.log(pow(2, 3)); // 计算的结果是 8
```
