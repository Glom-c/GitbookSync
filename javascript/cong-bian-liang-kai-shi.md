---
description: 数据的栖身之所
---

# 从变量开始

## 变量的定义

{% hint style="info" %}
变量是用来存放数据的容器
{% endhint %}

在 `JavaScript`中创建变量被称为“定义”变量。 您可以通过 `var` 关键词来定义 `JavaScript` 变量：

```javascript
//变量定义方式
var a;
```

如此定义后，变量是没有值的。（实际上，它的值是 undefined。）

{% hint style="info" %}
你可以通过  `a == "undefined"` 来判断一个js变量是否为 **undefined**
{% endhint %}

如需赋值给变量，需要使用等号：

```javascript
a = "Hello Wolrd!";
```

当然，你可以在定义变量时向它赋值：

```javascript
var a = "Hello Wolrd!";
```

这便是你的第一个变量了

### 变量定义方式

在JavaScript中，共有四种变量定义方式

* var
* let
* const
* function&#x20;

这四种定义变量的方式彼此之间的区别体现在：

**重复定义**

* `var` 能重复定义，后者覆盖前者
* `let`  `const`  `function` 则不能重复定义

**作用域的范围**

* var 的作用域是以函数/整个文件为作用域
* let, function 和 const 是块作用域

**const 的特殊之处**

* 由const定义的变量，只能赋值一次，也就是 **常量**

{% hint style="info" %}
常量即不可改变的量
{% endhint %}

**function 的特殊之处**

* 与其他三种方式存放数据不同，function 是专门用来定义"函数"的
* 同一个函数名不能重复定义

{% hint style="info" %}
是的，在 **JavaScript** 中函数也是一种变量
{% endhint %}

关于函数，我们会在下一节更深入的讲解它的定义与调用



### 变量名

JavaScript中变量名不可重复

**变量名的规范：**

* 名称可包含字母、数字、下划线和美元符号
* 名称必须以字母开头
* 名称也可以 $ 和 \_ 开头（但是在本教程中我们不会这么做）
* 名称对大小写敏感（y 和 Y 是不同的变量）
* 保留字（比如 JavaScript 的关键词）无法用作变量名称

> JavaScript 语句和 JavaScript 变量都对大小写敏感。

### 综上所述

可以通过以下方法判断一个变量是否被赋值：

```javascript
//注意 只定义不赋值
var a;

function a() {
  if (typeof a == "undefined") {
    //如没有则赋值
    a = "Hello Wolrd!";
  }
}
```

你也可以省略定义.

```javascript
function a() {
  if (typeof a == "undefined") {
    //如没有则赋值
    a = "Hello Wolrd!";
    //在Pouvoir中，以上方式可以用来定义全局变量
  }
}
```

### 数据类型

有关数据类型，请看 [https://www.runoob.com/js/js-datatypes.html](https://www.runoob.com/js/js-datatypes.html)

## 调用对象中的变量

你可以通过以下方式来调用对象中的变量:

```
//           获取Pouvoir的静态类对象(Pouvoir教程里会讲)
const Pouvoir= static('Pouvoir')
//通过 对象.变量名 来调用
print(Pouvoir.scriptManager)
```
