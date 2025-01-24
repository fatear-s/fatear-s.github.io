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

```HTML
<script src = "js/demo.js"></script>
```

不能自闭合

```html
<script src />
```

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



### Maven

#### 依赖管理

之前的项目中，需要下载jar包，使用maven只需要配置xml文件

#### 项目构建

#### 统一的项目结构

不同IDE会产生不同的结构，但是使用maven是统一的架构，都可以使用

- 项目对象模型 (Project Object Model)
- 依赖管理模型(Dependency)
- 构建生命周期/阶段(Build lifecycle & phases)

#### 项目对象模型

将我们自己的项目抽象成一个对象模型，有自己专属的坐标

坐标，就是资源(jar包)的唯一标识，通过坐标可以定位到所需资源(jar包)位置。

坐标的组成部分：

- groupId: 组织名
- arfitactId: 模块名
- Version: 版本号

#### 依赖管理模型

现在我们只需要在pom.xml中配置依赖的配置文件即可。 而这个依赖对应的jar包其实就在我们本地电脑上的maven仓库中。 



1. 在pom.xml中编写`<dependencies>`标签
2. 在`<dependencies>`标签中使用`<dependency>`引入坐标
3. 定义坐标的 `groupId`、`artifactId`、`version`
4. 点击刷新按钮，引入最新加入的坐标

```HTML
<dependencies>
    <!-- 依赖 : spring-context -->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>6.1.4</version>
    </dependency>
</dependencies>
```

如果不知道依赖的坐标信息，可以到mvn的中央仓库（https://mvnrepository.com/）中搜索

IDEA （Alt + Insert）搜索

#### 依赖传递

我们可以通过Maven中的排除依赖功能，来将这个依赖排除掉。

#### 依赖排除

```HTML
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context</artifactId>
    <version>6.1.4</version>

    <!--排除依赖, 主动断开依赖的资源-->
    <exclusions>
        <exclusion>
            <groupId>io.micrometer</groupId>
            <artifactId>micrometer-observation</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```

#### 依赖范围控制

在maven中，如果希望限制依赖的使用范围，可以通过 `<scope>…</scope>` 设置其作用范围。

### maven仓库

Maven仓库分为：

- 本地仓库：自己计算机上的一个目录(用来存储jar包)
- 中央仓库：由Maven团队维护的全球唯一的。仓库地址：https://repo1.maven.org/maven2/
- 远程仓库(私服)：一般由公司团队搭建的私有仓库

jar包的查找顺序，本地仓库 --> 远程仓库--> 中央仓库



#### 安装MaVen

下载Maven安装包，链接https://maven.apache.org/download.cgi

解压安装包

配置环境变量，将以下的命令添加到~/.zshrc文件中

```bash
export MAVEN_HOME="/Users/liutao/tools/apache-maven-3.9.9"
export PATH="$MAVEN_HOME/bin:$PATH"
```



maven坐标3组成

- groupId：定义当前Maven项目隶属组织名称（通常是域名反写，例如：com.itheima）
- artifactId：定义当前Maven项目名称（通常是模块名称，例如 order-service、goods-service）
- version：定义当前项目版本号
  - SNAPSHOT: 功能不稳定、尚处于开发中的版本，即快照版本
  - RELEASE: 功能趋于稳定、当前更新停止，可以用于发行的版本



### 测试

（重点在于尝试）



### SpringBootWeb

静态资源，HTML，CSS，JavaScript

动态资源，会根据用户请求和其他数据动态生成的，内容可能会在每次请求时都发生变化。Spring Framework

java程序开发的动态资源来说，我们通常会将这些动态资源部署在**Tomcat**，这样的Web服务器中运行





### Http协议

**基于TCP协议**

**基于请求-响应模型**

请求和响应是一一对应关系

**HTTP协议是无状态协议**

- 缺点:  多次请求间不能共享数据
- 优点:  速度快

?京东购物。加入购物车和去购物车结算是两次请求

提出了使用会话技术(Cookie、Session)来解决这个问题



HTTP协议又分为：请求协议和响应协议

### HTTP请求协议

**请求行、请求头 、请求体**

![image-20250104201559849](/Users/liutao/Library/Application Support/typora-user-images/image-20250104201559849.png)

- **请求行**(以上图中红色部分) ：HTTP请求中的第一行数据。由：`请求方式`、`资源路径`、`协议/版本`组成（之间使用空格分隔）

- 资源路径：/brand/findAll?name=OPPO&status=1

  - 请求路径：/brand/findAll
  - 请求参数：name=OPPO&status=1
    - 请求参数是以key=value形式出现
    - 多个请求参数之间使用`&`连接
  - 请求路径和请求参数之间使用`?`连接 

- **请求头**(以上图中黄色部分) ：第二行开始，上图黄色部分内容就是请求头。格式为key: value形式 

  - http是个无状态的协议，所以在请求头设置浏览器的一些自身信息和想要响应的形式。这样服务器在收到信息后，就可以知道是谁，想干什么了

- 常见的HTTP请求头有:

  - | 请求头          | 含义                                                         |
    | --------------- | ------------------------------------------------------------ |
    | Host            | 表示请求的主机名                                             |
    | User-Agent      | 浏览器版本。 例如：Chrome浏览器的标识类似Mozilla/5.0 ...Chrome/79 ，IE浏览器的标识类似Mozilla/5.0 (Windows NT ...)like Gecko |
    | Accept          | 表示浏览器能接收的资源类型，如text/*，image/*或者*/*表示所有； |
    | Accept-Language | 表示浏览器偏好的语言，服务器可以据此返回不同语言的网页；     |
    | Accept-Encoding | 表示浏览器可以支持的压缩类型，例如gzip, deflate等。          |
    | Content-Type    | 请求主体的数据类型                                           |
    | Content-Length  | 数据主体的大小（单位：字节）                                 |

- 请求体 ：存储请求参数

  - GET请求的请求参数在请求行中，故不需要设置请求体

- **POST方式的请求协议**

- **请求体**(以上图中绿色部分) ：存储请求参数 

  - 请求体和请求头之间是有一个空行隔开（作用：用于标记请求头结束）

  ### HTTP响应协议

  **响应行 、响应头 、响应体**

  - 响应行(以上图中红色部分)：响应数据的第一行。响应行由`协议及版本`、`响应状态码`、`状态码描述`组成

  | 状态码分类 | 说明                                                         |
  | ---------- | ------------------------------------------------------------ |
  | 1xx        | 响应中 --- 临时状态码。表示请求已经接受，告诉客户端应该继续请求或者如果已经完成则忽略 |
  | 2xx        | 成功 --- 表示请求已经被成功接收，处理已完成                  |
  | 3xx        | 重定向 --- 重定向到其它地方，让客户端再发起一个请求以完成整个处理 |
  | 4xx        | 客户端错误 --- 处理发生错误，责任在客户端，如：客户端的请求一个不存在的资源，客户端未被授权，禁止访问等 |
  | 5xx        | 服务器端错误 --- 处理发生错误，责任在服务端，如：服务端抛出异常，路由出错，HTTP版本不支持等 |

  - 响应头(以上图中黄色部分)：响应数据的第二行开始。格式为key：value形式

    ```
    Content-Type：表示该响应内容的类型，例如text/html，image/jpeg ；
    
    Content-Length：表示该响应内容的长度（字节数）；
    
    Content-Encoding：表示该响应压缩算法，例如gzip ；
    
    Cache-Control：指示客户端应如何缓存，例如max-age=300表示可以最多缓存300秒 ;
    
    Set-Cookie: 告诉浏览器为当前页面所在的域设置cookie
    ```

    

  - 响应体(以上图中绿色部分)： 响应数据的最后一部分。存储响应的数据

    - 响应体和响应头之间有一个空行隔开（作用：用于标记响应头结束）

    

    
  
    controller方法中的return的结果，怎么就可以响应给浏览器呢？
  
  答案：使用@ResponseBody注解
  
  - 类型：方法注解、类注解
  - 位置：书写在Controller方法上或类上
  - 作用：将方法返回值直接响应给浏览器，如果返回值类型是实体对象/集合，将会转换为JSON格式后在响应给浏览器
  
  在类上加了@RestController注解，而这个注解是由两个注解组合起来的，分别是：@Controller 、@ResponseBody。 那也就意味着，我们在类上已经添加了@ResponseBody注解了，而一旦在类上加了@ResponseBody注解，就相当于该类所有的方法中都已经添加了@ResponseBody注解。 


### 分层解耦

1. ### 三层架构

单一职责原则：一个类或一个方法，就只做一件事情，只管一块功能。

这样就可以让类、接口、方法的复杂度更低，可读性更强，扩展性更好，也更利于后期的维护。

- Controller：控制层。接收前端发送的请求，对请求进行处理，并响应数据。
- Service：业务逻辑层。处理具体的业务逻辑。
- Dao：数据访问层(Data Access Object)，也称为持久层。负责数据访问操作，包括数据的增、删、改、查。

![image-20250104220004637](/Users/liutao/Library/Application Support/typora-user-images/image-20250104220004637.png)



1. 解耦

Service中调用Dao层中的内容，称为层与层之间的耦合

#### 解耦思路

**1). 首先不能在EmpController中使用new对象。代码如下**

- **控制反转：** Inversion Of Control，简称**IOC**。对象的创建控制权由程序自身转移到外部（容器），这种思想称为控制反转。
  - 对象的创建权由程序员主动创建转移到容器(由容器创建、管理对象)。这个容器称为：IOC容器或Spring容器。

- **依赖注入：** Dependency Injection，简称**DI**。容器为应用程序提供运行时，所依赖的资源，称之为依赖注入。
  - 程序运行时需要某个资源，此时容器就为其提供这个资源。
  - 例：EmpController程序运行时需要EmpService对象，Spring容器就为其提供并注入EmpService对象。
- **bean对象：**IOC容器中创建、管理的对象，称之为：bean对象。



在实现类加上 `@Component` 注解，就代表把当前类产生的对象交给IOC容器管理。（IOC可以造）

在需要类的声明上加上**@Autowired**注解，代表注入依赖。(可以从IOC容器中取)

声明bean的四大注解，要想生效，还需要被组件扫描注解 `@ComponentScan` 扫描



包 `pojo`，专门用来存放实体类

SpringBoot debug

```XML
<!--在pom.xml中添加配置-->
<plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <excludes>
                        <exclude>
                            <groupId>org.projectlombok</groupId>
                            <artifactId>lombok</artifactId>
                        </exclude>
                        <jvmArguments>
                            -Xdebug -Xrunjdwp:transport=dt_socket,server=y,suspend=y,address=5005
                        </jvmArguments>
                    </excludes>
                </configuration>
            </plugin>
```

# lombok java 无法将类 XX类中的构造器 X应用到给定类型

打开idea 注释处理器（Annotation Processors） 路径为File ->setting -> build,execution,deploment->Compiler -> [Enable](https://so.csdn.net/so/search?q=Enable&spm=1001.2101.3001.7020) annotation processing

链接：https://blog.csdn.net/qq_30683537/article/details/140888655

![image-20250110193754007](/Users/liutao/Library/Application Support/typora-user-images/image-20250110193754007.png)





### SQL

#### DDL

DDL英文全称是Data Definition Language(数据定义语言)，用来定义数据库对象(数据库、表)。



查询

```sql
show database;#查询所有数据库
select database();#查询当前数据库

```

创建

```sql
create database [if not exists] 数据库名 [default charset utf8mb4]
```

使用

```sql
use 数据库名;
```

删除

```sql
drop database [if exists] 数据库名;
```

#### 表操作

对表结构的操作

创建

```sql
create table 表名(
	字段1 字段2类型[约束] [comment 字段1注释],
	字段2 字段2类型2约束] [comment 字段2注释],
	字段3 字段2类型3约束] [comment 字段3注释],
	......
	字段n 字段n类型[约束] [comment 字段n注释]
)[ comment 表注释];
```

查询

```sql
-- 查询当前数据库的所有表
show tables;

-- 查看指定的表结构
desc 表名 ;   -- 可以查看指定表的字段、字段的类型、是否可以为NULL、是否存在默认值等信息

-- 查询指定表的建表语句
show create table 表名 ;
```

添加字段

```sql
-- 添加字段
alter table 表名 add  字段名  类型(长度)  [comment 注释]  [约束];

-- 比如： 为tb_emp表添加字段qq，字段类型为 varchar(11)
alter table tb_emp add  qq  varchar(11) comment 'QQ号码';
```

修改字段

```sql
-- 修改字段类型
alter table 表名 modify  字段名  新数据类型(长度);

-- 比如： 修改qq字段的字段类型，将其长度由11修改为13
alter table tb_emp modify qq varchar(13) comment 'QQ号码';

-- 修改字段名，字段类型
alter table 表名 change  旧字段名  新字段名  类型(长度)  [comment 注释]  [约束];

-- 比如： 修改qq字段名为 qq_num，字段类型varchar(13)
alter table tb_emp change qq qq_num varchar(13) comment 'QQ号码';
```

删除

```sql
-- 删除字段
alter table 表名 drop 字段名;

-- 比如： 删除tb_emp表中的qq_num字段
alter table tb_emp drop qq_num;
```

修改表名

```sql
-- 修改表名
rename table 表名 to  新表名;

-- 比如: 将当前的emp表的表名修改为tb_emp
rename table emp to tb_emp;
```

删除表结构

```sql
-- 删除表
drop  table [ if exists ]  表名;

-- 比如：如果tb_emp表存在，则删除tb_emp表
drop table if exists tb_emp;  -- 在删除表时，表中的全部数据也会被删除。
```

#### DML

数据处理

增加

```sql
#向指定字段添加数据
insert into 表名 (字段名1, 字段名2) values (值1, 值2);
#全部字段添加数据
insert into 表名 values (值1, 值2, ...);
#批量添加数据（指定字段）
insert into 表名 (字段名1, 字段名2) values (值1, 值2), (值1, 值2);
#批量添加数据（全部字段）
insert into 表名 values (值1, 值2, ...), (值1, 值2, ...);
```

修改

```sql
update 表名 set 字段名1 = 值1 , 字段名2 = 值2 , .... [where 条件] ;
```

删除

```sql
delete from 表名  [where  条件] ;
```

#### DQL

查询数据库表中的记录

查询关键字：**SELECT**

```sql
SELECT
        字段列表
FROM
        表名列表
WHERE
        条件列表
GROUP  BY
        分组字段列表
HAVING
        分组后条件列表
ORDER BY
        排序字段列表
LIMIT
        分页参数
```

- 基本查询（不带任何条件）

```sql
#查询多个字段
select 字段1, 字段2, 字段3 from  表名;
#查询所有字段（通配符）
select *  from  表名;
#设置别名
select 字段1 [ as 别名1 ] , 字段2 [ as 别名2 ]  from  表名;
#去除重复记录
select distinct 字段列表 from  表名;
```



- 条件查询（where）

```
select  字段列表  from   表名   where   条件列表 ; -- 条件列表：意味着可以有多个条件
```



学习条件查询就是学习条件的构建方式，而在SQL语句当中构造条件的运算符分为两类：

- 比较运算符
- 逻辑运算符

常用的比较运算符如下: 

| 比较运算符          | 功能                                     |
| ------------------- | ---------------------------------------- |
| >                   | 大于                                     |
| >=                  | 大于等于                                 |
| <                   | 小于                                     |
| <=                  | 小于等于                                 |
| =                   | 等于                                     |
| <> 或 !=            | 不等于                                   |
| between ... and ... | 在某个范围之内(含最小、最大值)           |
| in(...)             | 在in之后的列表中的值，多选一             |
| like 占位符         | 模糊匹配(_匹配单个字符, %匹配任意个字符) |
| is null             | 是null                                   |

常用的逻辑运算符如下:

| 逻辑运算符 | 功能                        |
| ---------- | --------------------------- |
| and 或 &&  | 并且 (多个条件同时成立)     |
| or 或 \|\| | 或者 (多个条件任意一个成立) |
| not 或 !   | 非 , 不是                   |

注意：查询为NULL的数据时，不能使用 `= null` 或 `！=null` 。得使用 `is null` 或 `is not null`。





- 聚合函数

之前我们做的查询都是横向查询，就是根据条件一行一行的进行判断，而使用聚合函数查询就是纵向查询，它是对一列的值进行计算，然后返回一个结果值。（将一列数据作为一个整体，进行纵向计算）

常用聚合函数：

| 函数  | 功能     |
| ----- | -------- |
| count | 统计数量 |
| max   | 最大值   |
| min   | 最小值   |
| avg   | 平均值   |
| sum   | 求和     |

注意 : 聚合函数会忽略空值，对NULL值不作为统计。



- 分组查询（group by）

```sql
select  字段列表  from  表名  [where 条件]  group by 分组字段名  [having 分组后过滤条件];
```

分组之后，查询的字段一般为聚合函数和分组字段，查询其他字段无任何意义

执行顺序：where > 聚合函数 > having 



执行时机不同：where是分组之前进行过滤，不满足where条件，不参与分组；而having是分组之后对结果进行过滤。



判断条件不同：where不能对聚合函数进行判断，而having可以。







- 排查查询



```sql
select  字段列表  
from   表名   
[where  条件列表] 
[group by  分组字段 ] 
order  by  字段1  排序方式1 , 字段2  排序方式2 … ;
```

排序方式：

ASC ：升序（默认值）

DESC：降序



- 分页查询（limit）

```sql
select  字段列表  from  表名  limit  起始索引, 查询记录数 ;
```

1. 起始索引从0开始。           计算公式 ：起始索引 = （查询页码 - 1）* 每页显示记录数
2. 分页查询是数据库的方言，不同的数据库有不同的实现，MySQL中是LIMIT
3. 如果查询的是第一页数据，起始索引可以省略，直接简写为 limit  条数



### JDBC

**就是使用Java语言操作关系型数据库的一套API**

```java
//获取连接
//创建预编译的PreparedStatement对象
//设置预编译参数
//执行语句
//处理结果
//释放资源
```



ResultSet（结果集对象）：封装了DQL查询语句查询的结果。

- next()：将光标从当前位置向前移动一行，并判断当前行是否为有效行，返回值为boolean。
  - true：有效行，当前行有数据
  - false：无效行，当前行没有数据
- getXxx(…)：获取数据，可以根据列的编号获取，也可以根据列名获取（推荐）。



- 预编译SQL（参数动态传递）

```Java
conn.prepareStatement("SELECT * FROM user WHERE username = ? AND password = ?");
pstmt.setString(1, "daqiao");
pstmt.setString(2, "123456");
ResultSet resultSet = pstmt.executeQuery();
```

执行语句

```java
ResultSet rs = pstmt.executeQuery();
int rowsUpdated = pstmt.executeUpdate();
```

- JDBC程序执行DML语句：int rowsUpdated = pstmt.executeUpdate();  //返回值是影响的记录数
- JDBC程序执行DQL语句：ResultSet resultSet = pstmt.executeQuery(); //返回值是查询结果集

#### Mybatis



### 项目实战

#### 部门管理

安装Apifox



#### 限制请求方式

```java
@RequestMapping(value = "/dept",method = RequestMethod.GET)
@Getmapping()
```

#### 数据封装

- 实体类属性名和数据库表查询返回的字段名一致，mybatis会自动封装。

- 如果实体类属性名和数据库表查询返回的字段名不一致，不能自动封装。

  ```java
  @Results({@Result(column = "create_time", property = "createTime"),
            @Result(column = "update_time", property = "updateTime")})
  @Select("select id, name, create_time, update_time from dept")
  public List<Dept> findAll();
  ```

  #### Nginx

  ##### 反向代理

  ```
  
  ```

  nginx项目安装并配置

  nginx项目迁移

  mac中的nginx项目需要修改root路径(M1芯片),因为全局路径不同.

  windows项目放入到mac中，需要放置在NGINX安装目录下，才能够运行正确(暂时不知道原因)

  

  

  NGINX项目测试

  注意浏览器缓存(关闭nginx代理仍然能够访问)

  

  

  ```Java
  
  
  
  @GetMapping
  
  @PostMapping
  
  @PutMapping
  
  @DeleteMapping = @RequestMapping(method = RequestMethod.DELETE)
  
  @PatchMapping
  
  ```

  #### 删除部门
  
  ```java
  //mapper
  @Delete("delete from dept where id =#{id}")
  public void deleteById(Integer id);
  
  //service，新增接口方法，实现
  //controller
  @DeleteMapping("/depts")
  
  ```
  
  #### 新增部门
  
  ```java
  //mapper
  @Insert("insert into dept(name,create_time,update_time) values(#{name},#{createTime},#{updateTime})")
  void insert(Dept)
  //service,补全参数
  
  
  //controller
  @Postmapping("/depts")
  
  ```
  
  

#### 问题

中文不适配，添加挥着修改是中文字符会产生错误

#### 修改部门

```java
//回显
//mapper
@Select()

//service实现，

//controller
@GetMapping("/depts/{id}")
public Result getById(@PathVariable("id") Integer id) {}

//修改
//mapper

@Update("update dept set name = #{name},update_time = #{updateTime} where id = #{id}")
void update(Dept dept);

//service,补全

//contoller
@PutMapping("/depts")


```



#### SQL的XML的配置

**在Mybatis中使用XML映射文件方式开发，需要符合一定的规范：**

1. XML映射文件的名称与Mapper接口名称一致，并且将XML映射文件和Mapper接口放置在相同包下（同包同名）
2. XML映射文件的namespace属性为Mapper接口全限定名一致
3. XML映射文件中sql语句的id与Mapper接口中的方法名一致，并保持返回类型一致。
4. **注意：一个接口方法对应的SQL语句，要么使用注解配置，要么使用XML配置，切不可同时配置。**



#### 动态SQL

```xml
 				<where>
            <if test="name != null and name != ''">
                e.name like concat('%',#{name},'%')
            </if>
            <if test="gender != null">
                and e.gender = #{gender}
            </if>
            <if test="begin != null and end != null">
                and e.entry_date between #{begin} and #{end}
            </if>
        </where>
```



#### Error

连接，mapper 中写的变量名才是传入到mapper.xml中的变量

#### 事务

@Transactional

#### **默认情况下，只有出现RuntimeException(运行时异常)才会回滚事务**

rollbackFor 指定何种error回滚

propagation

- **REQUIRED：**大部分情况下都是用该传播行为即可。
- **REQUIRES_NEW：**当我们不希望事务之间相互影响时，可以使用该传播行为。比如：下订单前需要记录日志，不论订单保存成功与否，都需要保证日志记录能够记录成功。
