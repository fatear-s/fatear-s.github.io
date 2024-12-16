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

### 泛型

<type>

限定集合类型

伪泛型。内部存储依旧是Object,取出来的时候强转相应的类型

泛型不能基本类型，只能写包装类

写在

#### 泛型类

类名<类型>

#### 泛型方法

修饰符 <类型>返回值类型 方法名(类型 变量名){}

#### 泛型接口

修饰符 interface 接口名<E>{}

实现时给定类型,或者实现类继承泛型.

泛型不具备继承性。想要限定类型的范围(继承),使用?

方法名(ArrayList<? extend E> list){}//E的子类及其以下

方法名(ArrayList<? super E> list){}//E的父类及以上

### lambda表达式

函数式接口,有且仅有一个抽象方法的接口(抽象类不行)

(参数1,参数2)->{实现方法}

### 集合

#### Map(双列集合)

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

HashMap的键位置如果存储的是自定义对象，需要重写hashCode和equals方法。

HashMap源码



#### LinkedHashMap

(双向链表记录顺序)

#### TreeMap

按指定的顺序规则进行排序。

#### 可变参数

最多只有一个可变参数，只能写在最后

int...args（本质上是数组）

#### Collections(单列集合)

(List)(ArrayList,LinkedList)

(Set)(HashSet,TreeSet)

(HashSet)(LinkedHashSet)

Java.util.collections集合工具类,集合顶层接口

#### 遍历

##### 迭代器遍历

不依赖索引.

Iterator<E>  iterator().是Collections中的方法,获取迭代对象

Iter.hasNext();是否还有下一个,返回boolean值

Iter.next();返回下一个.

迭代过程中，不能用集合中增加或者删除，但是可以使用迭代器中的删除。

##### 增强for遍历

底层就是一个迭代器

##### Lambda表达式遍历

coll.forEach()

##### 批量添加元素

addAll()

Collections.addAll(list ,elements 1,elements 2,...)

##### 打乱List集合元素顺序

Collections.Shuffle(list)

#### 不可变集合

不可修改集合内容

List<String> list = list.of(" "," ");

Set.of()

Map.of()

### Stream流

#### 得到stream流

流会自动关闭，不能使用两次流，使用链式编程

单列集合

List.stream()

双列集合

转换成单列集合,keySet(),entrySet()

数组

零散

调用API

#### 中间方法

filter()过滤

limit(int i )个数

Skip(int i) 跳过几个元素

Distinct()去除重复

Concat()合并流

Map(new Function<String ,Object>)类型转换

#### 终结方法

forEach()遍历

count()统计

toArray()收集数组

collect(Collector.toList())收集集合

```java
package day05.stream.test02;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Map;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args){
        /*
        创建ArrayList添加字符串（zhangsan ,23//lisi,24//wangwua,25）
        ,保存大于24的人，收集到map
         */
        ArrayList<String> list =new ArrayList<>();
        Collections.addAll(list,"zhangsan,23","lisi,24","wangwu,25");

//        Map<String, Integer> collect = list.stream().filter(s -> Integer.parseInt(s.split(",")[1]) > 24).collect(Collectors.toMap(
//                new Function<String, String>() {
//                    @Override
//                    public String apply(String s) {
//                        return s.split(",")[0];
//                    }
//                },
//                new Function<String, Integer>() {
//                    @Override
//                    public Integer apply(String s) {
//                        return Integer.parseInt(s.split(",")[1]);
//                    }
//                }
//        ));
        Map<String, Integer> collect = list.stream().filter(s -> Integer.parseInt(s.split(",")[1]) >= 24).collect(Collectors.toMap(s -> s.split(",")[0], s -> Integer.parseInt(s.split(",")[1])));
        System.out.println(collect);
    }
}
```

收集成Map是将流上的数据组合成字符串，再对字符串做处理，放入到建和值中

Map()类型转换

```java
package day05.stream.test03;

import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.function.Function;
import java.util.stream.Collector;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class Main {
    public static void main(String[] args) {
        /*
        两个list集合，第一个集合中，存储6名男人信息（“张三,23”）;第二个存贮6名女人
        男只要名字长度为3前2名
        女只要姓"yang"的，不要第一个
        过滤后合并到一起
        以上封装成Actor对象
        将所有人保存到List中
         */
        ArrayList<String> boyList = new ArrayList<>();
        ArrayList<String> girlList = new ArrayList<>();
        Collections.addAll(boyList, "张三,23", "张三风,14", "李三思,25", "王三一,26", "赵三囍,37", "钱三强,28");
        Collections.addAll(girlList, "yangyi,34", "wangkeer,12", "dianzhatian,23", "weifangyu,45", "yangyangle,23", "yabngzibo,34");

        boyList.stream().filter(s -> s.split(",")[0].length() == 3).limit(2).forEach(S -> System.out.println(S));
        girlList.stream().filter(s -> s.split(",")[0].substring(0, 4).equals("yang")).skip(1).forEach(S -> System.out.println(S));

        Stream<String> boyStream = boyList.stream().filter(s -> s.split(",")[0].length() == 3).limit(2);
        Stream<String> girlStream = girlList.stream().filter(s -> s.split(",")[0].substring(0, 4).equals("yang")).skip(1);
        Stream<String> aggrStream = Stream.concat(boyStream, girlStream);

        //aggrStream.forEach(System.out::println);

        List<Actor> collect = aggrStream.map(
                s -> new Actor(s.split(",")[0], Integer.parseInt(s.split(",")[1]))
        ).collect(Collectors.toList());

        System.out.println(collect);
    }
}
```

