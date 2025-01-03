---
title: javaWeb
date: 2024-12-09 16:53:27
tags:
---

# JavaWeb

## 介绍



![image-20241209170002293](/Users/liutao/Library/Application Support/typora-user-images/image-20241209170002293.png)

技术栈

![image-20241209170130894](/Users/liutao/Library/Application Support/typora-user-images/image-20241209170130894.png)

### MDN文档

### HTML

网页结构

```HTML

<html>

#给浏览器识别的
<head>
<title>标题</title>
</head>
#给用户看的内容
<body>
</body>

</html>
```

标签语言

标签

浏览器解析

### CSS

网页表现

层叠样式表



### JavaScript

网页动作

### 前端

### js引用

方式1

javaScript 放在<script></script>之间

一般放在<body>元素底部

方式2

<script src = "js/demo.js"></script>

不能自闭合<script src />

### js语法

#### 输出

```JavaScript
//警告框
windows.alert()
//在HTML中写入内容
document.write()
//写入浏览器控制台
console.log()
//变量
let a= 90;
//常量
const PI = 3.1415926;

```

#### 数据类型

number（整数，小数，Nan）

String  "",'',``

boolean

null

undefined

使用typeof返回类型

typeof 12;

#### 函数

```javascript
function func(参数1,参数2,...){
	//code
}
```

- 形参不需要声明类型，并且JS中不管什么类型都是let去声明，加上也没有意义。
- 返回值也不需要声明类型，直接return即可



```javaScript
let result = function(a,b){return a+b;}
let result2 = (a,b)=>{return a+b;}
```

#### 自定义对象

```javaScript
let Object1 = {
	属性1：值，
	属性2：值，
	方法名称:function(参数列表){}
};

//调用
Object1.属性名
Object2.方法名()
```

#### Json

```json
//json格式
{
"key":value,
"key":value,
"key":value
}


//3. JSON - JS对象标记法
let person = {
  name: 'itcast',
  age: 18,
  gender: '男'
}
alert(JSON.stringify(person)); //js对象 --> json字符串

let personJson = '{"name": "heima", "age": 18}';
alert(JSON.parse(personJson).name);
```

JSON.stringify(...)：作用就是将js对象，转换为json格式的字符串。

JSON.parse(...)：作用就是将json格式的字符串，转为js对象。

#### JS DOM

- Document：整个文档对象
- Element：元素对象
- Attribute：属性对象
- Text：文本对象
- Comment：注释对象

![image-20250103203709155](/Users/liutao/Library/Application Support/typora-user-images/image-20250103203709155.png)

DOM操作

#### 获取DOM元素对象

操作DOM对象的属性或者方法

```javascript
//根据CSS选择器来获取DOM元素，获取到匹配到的第一个元素：document.querySelector('CSS选择器');
//据CSS选择器来获取DOM元素，获取匹配到的所有元素：document.querySelectorAll('CSS选择器');

```

#### JS监听事件

HTML事件是发生在HTML元素上的 “事情”

给这些事件绑定函数，当事件触发时，可以自动的完成对应的功能，这就是事件监听。

```javascript
//语法
事件源.addEventListener("事件类型",要执行的函数);
//事件源: 哪个dom元素触发了事件, 要获取dom元素
//事件类型: 用什么方式触发, 比如: 鼠标单击 click, 鼠标经过 mouseover
//要执行的函数: 要做什么事
```

#### 常见事件

##### 鼠标

click

mouseenter

mouseleave

##### 键盘

keydown

Keyup

##### 焦点：指用户与网页上可交互元素（如输入框、按钮、链接等）进行交互时，系统对该元素的“关注”状态。可以粗浅的认为是光标

focus

Blur

##### 表单

input

submit

### Vue框架

##### Vue快速入门



##### Vue常用指令

##### Vue声明周期

