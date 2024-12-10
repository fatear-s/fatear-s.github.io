---
title: Java
---



# Java

## Point

### String 

```java
"-".repeat(count)
```



### 容器

不能存基本数据类型，只能存引用数据类型和包装类

ArrayList

泛型<Type>

Comparator<Type>接口,重写compare方法进行使用,ArrayList.sort(list,Comparator<type>)

compareTo(Object o){}

![image-20241210172404281](/Users/liutao/Library/Application Support/typora-user-images/image-20241210172404281.png)

### static(修饰词)

变量：相同类型不同对象之间的数据共享

public static int a;

可以类名调用

内存：堆中，静态区

类内存分配（字节码到方法区）

![image-20241111121638273](/Users/liutao/Library/Application Support/typora-user-images/image-20241111121638273.png)

方法：

javabean类

描述一类事物

测试类

带有main方法，用于测试

工具类

帮助实现的工具，Math等（私有化构造方法）

工具类就使用static修饰词

static 注意事项

静态方法只能访问静态变量



### 继承

class Student extends Person{}

默认父类:Object()



子类能继承父类

构造方法不能继承

this.name 本类

super.name 父类

this,super 都符合就近原则，本类找不到就父类找，直到找到

成员变量

private 继承但不可直接使用

成员方法

虚方法表（非private，非static，非final）继承



内存分析工具

jps  查看类的ID

jhsdb 内存查看



重新，就是覆盖虚方发表中的方法。



父类构造方法

Super()父类无参构造，可以有参构造

this()本类构造方法

类的基本方法，ClassLayout.praseInstance(calss s )

### 多态

子类对象赋值给父类引用

继承关系

父类引用

方法重写

Person  p = new Student()

成员变量，与成员方法区别：

成员变量没有重写这一个说法，就近原则，而成员方法会调用子类重写的方法。

编译的时候看父类的声明，父类没有就报错

成员变量，编译看左边，运行看左边

成员方法，编译看左边，运行看右边

使用：

定义方法，传入参数是父类，就可以接受所有子类的传入



类型强制转换

(Student) p;

判断引用是不是某类型

引用 instanceof type

引用 instanceof type 引用1

### 包

包就是文件夹

package 包名;

不需要导入包：1同一个包中的类。2Java.lang包中的类

### final

修饰方法

不能够重写

修饰类

不能够被继承

修饰变量

变量只能够被赋值一次

![image-20241113101959831](/Users/liutao/Library/Application Support/typora-user-images/image-20241113101959831.png)

修饰引用数据类型

地址不能够变

![image-20241113102927823](/Users/liutao/Library/Application Support/typora-user-images/image-20241113102927823.png)

### 代码块

{}

#### 局部代码块（淘汰）

提前结束变量的生命周期

#### 构造代码块(淘汰)

构造方法中重复的代码,写在成员位置代码块

#### 静态代码块

Static{}

只执行一次

类加载时，执行一些代码块

### 抽象类和抽象方法

public abstract class 

### 接口

行为的抽象

public interface 接口名{}

public class 类名 implements 接口名1,接口名2{}

接口成员变量，只能够是常量

构造方法，无

成员方法，jdk7 只能够抽象方法

（类中得我接口，抽象方法）

如何抽象出类（自下而上，分类，行为抽取，抽取接口）

接口升级的问题

接口升级，实现类必须全部实现才能执行，但是接口升级的同时，实现的类也需要能够运行。

默认方法

非抽象方法，可以不重写

public default 返回值类型 方法名(){}

接口中可以有静态方法和私有方法

### 内部类

内部类可以使用外部类的成员，包括私有。

#### 匿名内部类

new 类名(){方法重写};



### 集合

#### Map

put//添加，覆盖,返回覆盖的值

remove

containskey

containvalue

clear

#### 遍历

Set<String> keys = map.keySet();

map.get(key);



map.entrySet();

//键值对

#### HashMap

![image-20241210154828375](/Users/liutao/Library/Application Support/typora-user-images/image-20241210154828375.png)

HashMap源码



#### LinkedHashMap

(双向链表记录顺序)

#### TreeMap

按指定的顺序规则进行排序。

#### 可变参数

最多只有一个可变参数，只能写在最后

int...args（本质上是数组）

#### Collections

Java.util.collections集合工具类

##### 批量添加元素

addAll()

Collections.addAll(list ,elements 1,elements 2,...)

##### 打乱List集合元素顺序

Collections.Shuffle(list)
