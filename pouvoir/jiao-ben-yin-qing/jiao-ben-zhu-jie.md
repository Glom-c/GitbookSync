---
description: 一套方便快捷的注解系统
---

# 脚本注解

## 用法

```javascript
//@注解名(注解参数)
fun test2(函数参数1,函数参数2){
//code
}
```

## Pouvoir

<details>

<summary>@Annotation - 注册脚本</summary>

可选注解参数: key - 注解名

若无参数key则以函数名作为注解名

使用此注解函数的参数:

1. data : [ScriptAnnotationData](https://doc.skillw.com/pouvoir/com/skillw/pouvoir/api/script/annotation/ScriptAnnotationData.html)

例子:

```javascript
//@Annotation(MyAnnotation)
fun test(data){
  const func = data.function
  const args = data.args
  print("函数" + func + "使用了注解@MyAnnotation！")
  print("参数为: " + args)
}

//@MyAnnotation(hahaha,lalala)
fun test2(){
}
```

当此脚本文件被加载时，后台输出:

```
函数test2使用了注解@MyAnnotation!
参数为: hahaha,lalala
```

</details>

<details>

<summary>@Awake - 唤醒函数</summary>

详见：[**开始运行脚本**](kai-shi-yun-hang-jiao-ben.md#he-shi-xing-lai-awake-zhu-jie)****

</details>

<details>

<summary>@Function - 注册内联函数</summary>

可选注解参数: key - 内联函数名

若无参数key则以函数名作为内联函数名

使用此注解函数的参数:

1. parser : [Parser](https://doc.skillw.com/pouvoir/com/skillw/pouvoir/api/function/parser/Parser.html)

例子:

```javascript
//@Function(myFunction)
fun test(parser){
  const value = parser.parseDouble()
  print("test value: " + value)
}

//测试内联函数
fun test2(){
//使用顶级函数eval
eval("myFunction 100")
}
```

当执行函数test2时，后台输出:

```
test value: 100
```

</details>

<details>

<summary>@Listener - 注册监听器</summary>

必填注解参数:

* \-event 事件类名   ——  事件

可选注解参数:

* \-priority 优先级   ——  优先级 默认 NORMAL
* \--ignoreCancel   ——  是否无视已取消的事件 默认 否

使用此注解函数的参数:

1. event: 事件对象

例子:

```javascript
//@Listener(-event org.bukkit.event.player.PlayerInteractEvent -priority LOWEST --ignoreCancel)
function onPlayerInteract(event) {
  // 玩家交互时会调用这个函数
  if (event.action.name() == "LEFT_CLICK_AIR") {
    // 判断是不是右键空气
    event.player.sendMessage('哈！ 你与空气交互♂了！')
  }
}
```

当生存模式的玩家右击空气时，会收到消息:

```
哈！ 你与空气交互♂了！
```

</details>

<details>

<summary>@Placeholder - 注册PAPI占位符</summary>

必填注解参数

1. 变量名
2. 插件/脚本名
3. 作者名
4. 版本

使用此注解函数的参数:

1. params —— 参数
2. player —— 玩家

例子:

```javascript
//@Placeholder(health,TestScript,Glom_,0.0.1)
fun test(params,player){
  return player.health
}

fun test2(){
  print(placeholder("%health%",this.sender))
}
```

当生命值为20的玩家执行`/pou run test.js test2`时，后台输出:

```
20
```

</details>

<details>

<summary>@PouPlaceholder - 注册PouPAPI占位符</summary>

必填注解参数

1. 变量名
2. 插件/脚本名
3. 作者名
4. 版本

使用此注解函数的参数:

1. params —— 参数
2. entity —— 实体
3. def —— 默认值

例子:

```javascript
//@PouPlaceholder(health,TestScript,Glom_,0.0.1)
fun test(params,entity,def){
  return entity.health
}

fun test2(){
  print(placeholder("%health%",this.sender))
}
```

当生命值为20的玩家执行`/pou run test.js test2`时，后台输出:

```
20
```

</details>

