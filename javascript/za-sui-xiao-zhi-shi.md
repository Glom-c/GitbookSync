---
description: 从一点一滴开始...
---

# 杂碎小知识

## 注释

<pre class="language-javascript"><code class="lang-javascript">// 这里是单行注释
var x = 1
/*
<strong>  多行注释哦
</strong>  第二行注释
*/
print(1)
</code></pre>

## 优化您的脚本

### &#x20;减少循环中的活动

循环每重复一次，其中的每条语句，包括 `for` 语句，都会被执行

放在循环之外的语句或赋值会使循环运行得更快

差的代码：

```
var i;
for (i = 0; i < arr.length; i++) {
```

更好的代码：

```
var i;
var l = arr.length;
for (i = 0; i < l; i++) {
```

循环每次迭代时，坏代码就会访问数组的 `length` 属性。

好代码在循环之外访问 `length` 属性，使循环更快。

{% embed url="https://www.w3school.com.cn/js/js_best_practices.asp" %}

如果您已经掌握了基本的JavaScript知识，请移步

