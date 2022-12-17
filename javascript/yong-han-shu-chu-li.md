---
description: 处理数据的过程
---

# 用函数处理

## 函数的定义与调用

JavaScript 中的函数是一个处理数据的过程， 会在被调用时执行。

```javascript
//        函数名     参数
function myFunction(p1, p2) {
  //代码块
  return p1 * p2; // 该函数返回 p1 和 p2 的乘积
}
```

JavaScript 函数的定义一般遵循以下格式

```javascript
function 函数名(参数1, 参数2, 参数3) {
  //要执行的代码
}
```

### 定义方式

#### 普通函数方式(命名函数)

利用 `function` 定义函数

```javascript
// 定义方式
//        函数名     参数
function myFunction(p1, p2) {
  //代码块
  return p1 * p2; // 该函数返回 p1 和 p2 的乘积
}

var a = 114;
var b = 514;
// 调用
myFunction(a, b);
```

因为定义出来的函数有名字，所以也被称为**命名函数**

{% hint style="info" %}
JavaScript有 函数声明提前 的特性

使用 `function` 声明的函数 会在所有的代码执行之前就被定义

所以我们可以在函数声明前就调用函数，而使用下面的**函数表达式**创建函数不会被声明提前
{% endhint %}

#### 函数表达式方式(匿名函数）

JavaScript 函数也可以使用表达式来定义

就像这样

```javascript
//是的，没有函数名
function (p1, p2) {
  return p1 * p2
}
```

因为匿名函数没有名字，你只能通过以下方法调用它

```javascript
(function (p1, p2) {
  return p1 * p2
})(2,3)
//返回6
```

因此，我们通常将函数表达式储存在变量中，可以更方便的调用：

```javascript
// 这是函数表达式写法，匿名函数后面跟分号结束
var myFunction = function (p1, p2) {
  return p1 * p2
};

//在变量中保存函数表达式之后，此变量可用作函数：
var a = 114
var b = 514
// 调用
myFunction(a, b)
```

**箭头函数**

在 **Pouvoir** ，**JDK9+ 的环境下** 则支持 **箭头函数**

箭头函数就是简化版的函数表达式

不需要 function 关键字、return 关键字和花括号

{% hint style="info" %}
Lambda 爱好者狂喜
{% endhint %}

```javascript
// ES5 (jdk8)
var x = function (x, y) {
  return x * y;
};
// ES6 (jdk9+)
const x = (x, y) => x * y;
```

#### Function() 构造器

函数也可以通过**函数构造器**来定义

```javascript
// 最后一个参数前，均为函数参数名
//                           参数1 参数2  函数代码块
var myFunction = new Function("a", "b", "return a * b");
var x = myFunction(4, 3);
// x = 12
```

### 函数名

函数名可包含字母、数字、下划线和美元符号（规则与变量名相同）。

### 参数

圆括号可包括由逗号分隔的参数：

(参数 1, 参数 2, ...)

在函数中，参数是局部变量，也就是说代码块外，函数参数就不存在了。

### 代码块

由函数执行的代码被放置在花括号中：{}

{% hint style="info" %}
**函数参数**（Function parameters）是在函数定义中所列的名称。

**函数参数**（Function arguments）是当调用函数时由函数接收的真实的值。

&#x20;在 **Pouvoir教程** 中的 脚本注解的运用 会涉及到。
{% endhint %}

## 调用对象中的函数

你可以通过以下方式来调用对象中的函数:

```javascript
//           获取ColorUtils的静态类对象(Pouvoir教程里会讲)
const ColorUtils = static('ColorUtils')
//通过 对象.函数名(参数...) 来调用
print(ColorUtils.colored('&6哈哈~我有颜色哦!'))
```



***

本节部分摘录自 [https://www.w3school.com.cn/js/js\_functions.asp](https://www.w3school.com.cn/js/js\_functions.asp)
