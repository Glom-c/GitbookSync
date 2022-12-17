---
description: 让执行任务变得井然有序吧！
---

# 使用任务调度器

**Pouvoir** 提供了一系列任务调度器函数，涵盖**Bukkit的任务调度器**的所有功能

以下均为顶级函数(全局函数),可以直接调用

<pre class="language-javascript"><code class="lang-javascript">//时间单位均为 tick
// 20 tick 等于 1s (TPS = 20 的情况下)
//Consumor 表示 一个参数 无返回值 的匿名函数
//Supplier 表示 无参数 有返回值 的<a data-footnote-ref href="#user-content-fn-1">匿名</a>函数
function task(Consumor&#x3C;PlatformTask>) //同步任务
function taskLater(delay,Consumor&#x3C;PlatformTask>) //延时同步任务
function taskTimer(delay,period,Consumor&#x3C;PlatformTask>) //延时定时同步任务

function taskAsync(Consumor&#x3C;PlatformTask>) //异步任务
function taskAsyncLater(delay,Consumor&#x3C;PlatformTask>) //延时异步任务
function taskAsyncTimer(delay,period,Consumor&#x3C;PlatformTask>) //延时定时异步任务

function sync(Consumor&#x3C;PlatformTask>) //异步时快速跳回同步并有返回值 (同步不要用，会堵塞线程)


    // public interface PlatformTask {
    //     public abstract fun cancel(): kotlin.Unit
    // }
</code></pre>

## 为什么要有同步任务与异步任务？

在实现我们的奇思妙想时，其中有些过程放在主线程(同步任务)会浪费服务器资源，我们需要使用异步任务来分担主线程的压力。在另一方面，有些非线程安全的数据在异步的情况下操作会使数据有误，我们需要将其在主线程上进行，来避免_数据污染_

> 在拥有共享数据的多条线程并行执行的程序中，线程安全的代码会通过同步机制保证各个线程都可以正常且正确的执行，不会出现数据污染等意外情况。 “引自百度百科”

以下一段话引自[https://bdn.tdiant.net/#/unit/3-5](https://bdn.tdiant.net/#/unit/3-5)

Minecraft 中几乎所有的游戏逻辑都运行于主线程中, 而插件的大多数逻辑也是运行于主线程中的, 这包括插件命令的执行、(同步)事件的处理等等. 如果我们调度了一个异步任务, 或者处于异步事件中, 那么就不应当访问与Minecraft游戏内容有关的API(比如操作方块、加载区块、踢出玩家等). 尝试这么做极有可能得到异常, 使得插件崩溃

线程安全的有:

1.  Player#sendMessage()

    > 你可以发现大量插件在AsyncPlayerChatEvent事件中调用player.sendMessage(). 因此我们有理由确信这是线程安全的.
2.  PluginManager#callEvent(event)

    > 用于触发事件的方法. 在`SimplePluginManager`中, 该方法使用了synchronized关键字对其实例加锁, 因此是线程安全的. 更多细节请阅读源代码.
3.  发包 - sendPacket

    > 为何Player#sendMessage()是线程安全的就是因为它. 我们可以深入craftbukkit乃至nms(net.minecraft.server), sendPacket不过是将数据包传入netty管道, 让netty处理. 如果某个方法仅仅执行了发包流程而没有实际从游戏里加载数据, 那么一般可视其为线程安全的. 因此利用`World#spawnParticle`发送粒子效果以及`World#playEffect`向玩家发送特效、`Player#sendTitle`向玩家发title等也是线程安全的. 我们可以把相关数学运算放到异步线程中, 算完再切换线程发粒子特效.

非线程安全的有:

1. 设置/获取方块、加载/生成区块
2. 操作实体
3. 权限检查(是的. 某些情况下这是非线程安全的, 因为插件一同共享权限列表)

## 例子

```javascript
task(function(task){
  print(1)
}) // 同步打印 1

//        tick
taskLater([
20,function(task){
  print(1)
}
]) // 同步,在1秒后打印1

taskAsyncTimer([
20,10,function(task){

 let x = sync(function(task){
    print(1)
    return 2
 }) //跳到同步打印1 然后返回1
 print(x)
}
]) // 异步，在1秒后每半秒从异步线程跳到同步线程执行任务，再将同步任务返回值赋值给x变量，并打印


```

匿名函数的`task`参数为&#x20;

```kotlin
    interface PlatformTask {
         fun cancel(): kotlin.Unit
    }
```

也就是说，你可以通过以下代码实现任务中的自行取消

```javascript
taskAsyncTimer([
20,10,function(task){
  task.cancel() //取消任务
}
])
```

如果你在使用JDK9+，那么你可以用箭头函数来简化匿名函数的声明:

```javascript
taskLater([
20,(task) => { print(1);}
]) // 同步,在1秒后打印1 (帅吗?)
```

[^1]: 
