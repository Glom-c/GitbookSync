---
description: 一些便捷的全局函数/变量
---

# 顶级成员

## 什么是顶级成员

在**Pouvoir**中，顶级成员包括

* 静态类
* 静态属性
* 静态方法

在脚本中，他们可以直接被调用

## 能干什么？

顶级成员可以提高你的脚本编写速率

就像下面这个例子

```javascript
//static就是一个顶级函数 可以快速获取类对象
var Coere = static("Coere");
function isNum(numStr) {
  return Coere.asDouble(numStr).isPresent;
}
```

## 都有哪些？

通过**顶级函数** `checkUsableVars` 在后台打印**Pouvior**及其它插件提供的顶级成员列表：

```javascript
function printTopLevel() {
  checkUsableVars();
}
```

## 如何使用?

对于**顶级静态类** **顶级静态属性**，可以当作普通变量一样调用

对于**顶级函数** 则需有以下几点注意事项

* 对于单参数函数，可当作普通函数调用
* 对于多参数函数，需用`[]`将所有参数括起来
* 对于 `Consumor` 与 `Supplier` 类型的参数，填入的函数需要确实有返回值或有参数
* 对于 `Java`**数组类型**的参数 需要使用`arrayOf` 来将`JsArray`转为`JavaArray`

例子:

```javascript
//单参数的顶级函数，直接当做普通函数调用
const ExampleClass = static('ExampleClass')
//多参数的顶级函数，需要用[]将多个参数括起来
taskLater([
  20,
  //对于Consumer与Supplier的函数要按规定填入参数
  //例如这里的task
  function(task){
    print(1)
  }
])

```

**Pouvoir**默认了一些常用的顶级函数（不是所有）

```javascript
// ? 代表可空 也就是可以填null
// 函数 : 的后面是返回值类型
// JsArray就是将值用 [] 括起来 如 [1,2,3]
function arrayOf(JsArray) : Array<Any?> //js数组 转 java数组
function listOf(JsArray) : MutableList<Any?> //js数组 转 List

function analysis(String): String //解析字符串内嵌函数
function placeholder(String,entity): String  //解析字符串内占位符(papi&pou)
function color(String): String //解析字符串内颜色
function calculate(formula,Player?,Map?): BigDecimal //计算公式，支持带入papi&pou占位符，支持Map<String,String>替换

function find(path) : StaticClass?  //查找静态类
function static(path) : StaticClass? //获取静态类

function info(Object?) //控制台打印文字
function warning(Object?) //控制台打印警告
function debug(String) //当Pouvoir在debug模式时才打印

//时间单位均为 tick
//Consumor 表示 接受一个参数 无返回值
//Supplier 表示 无参数 有返回值
function task(Consumor<PlatformTask>) //同步任务
function taskLater(delay,Consumor<PlatformTask>) //延时同步任务
function taskTimer(delay,period,Consumor<PlatformTask>) //延时定时同步任务

function taskAsync(Consumor<PlatformTask>) //异步任务
function taskAsyncLater(delay,Consumor<PlatformTask>) //延时异步任务
function taskAsyncTimer(delay,period,Consumor<PlatformTask>) //延时定时异步任务

function sync(Consumor<PlatformTask>) //异步时快速跳回同步并有返回值 (同步不要用，会堵塞线程)


```

{% hint style="info" %}
通常

`Function0` = 无参数的函数

`Function1` = 1个参数的函数

以此类推
{% endhint %}
