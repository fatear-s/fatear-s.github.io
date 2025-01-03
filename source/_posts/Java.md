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

`this` 引用的是当前对象的实例，而静态方法与类本身关联，不依赖于任何特定的对象实例。因此，静态方法并不需要 `this` 来访问，调用它时不需要实例对象。



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

​        boyList.stream().filter(s -> s.split(",")[0].length() == 3).limit(2).forEach(S -> System.out.println(S));
​        girlList.stream().filter(s -> s.split(",")[0].substring(0, 4).equals("yang")).skip(1).forEach(S -> System.out.println(S));

​        Stream<String> boyStream = boyList.stream().filter(s -> s.split(",")[0].length() == 3).limit(2);
​        Stream<String> girlStream = girlList.stream().filter(s -> s.split(",")[0].substring(0, 4).equals("yang")).skip(1);
​        Stream<String> aggrStream = Stream.concat(boyStream, girlStream);

​        //aggrStream.forEach(System.out::println);

​        List<Actor> collect = aggrStream.map(
​                s -> new Actor(s.split(",")[0], Integer.parseInt(s.split(",")[1]))
​        ).collect(Collectors.toList());

​        System.out.println(collect);
​    }
}
```



### 方法引用

要求

1、引用处必须是函数式接口

2、被引用方法必须已经存在

3、被引用方法的形参和返回值需要和抽象方法保持一致（类::method注意被引用的方法形参是跟第二个参数后面的保持一致）

静态方法引用 格式: class::method

成员方法引用 格式: new class()::method，如果引用流中数据类成员方法(class::methed)，如果是其他类(对象::method)

本类引用 this::method

父类引用super::method

构造方法引用class::new

### 异常

#### error

严重错误，系统级别错误。

#### exception

异常，可能出现的问题

##### runtimeexception

编译不会出现问题，但在运行时会产生错误。（本身及其子类               ）

##### 编译异常

编译时就出现的错误。

### File

成员方法

获取并遍历

File[] listFiles();

### IO流

字节流：操作所有类型的文件(拷贝使用场景)

字符流：操作纯文本文件(读取纯文本文件中的数据，往纯文本文件中写入)

#### FileOutputStream

父级路径必须存在，存在文件会清空文件内容

##### 写入

Write(byte b)

wrtie(byte[] b)

//byte[]  = String.getbytes();//得到字节流

![image-20241217203923457](/Users/liutao/Library/Application Support/typora-user-images/image-20241217203923457.png)

续写,fileoutputstream(str,append=true)

释放资源close()

#### FileinputStream

Read()//读不到返回-1

循环读取

```java
FileInputStream fis = FileInputStream("path");
int b;
while((b=fis.read())!=-1){
	System.out.print(b);
}
fis.close();

```

文件拷贝

释放资源，先开后释放

多字节读取

```java
int len;
byte[] bytes = new byte[len];
int lenRead = fis.read(bytes);
```

### 字符集

GBK

2字节存储，高位字节二进制1为开头（英文开头是0）区分

兼容ASCII

unicode

（utf-16,utf-32）

utf-8编码规则（1-4个字节）

ASCII 1一个字节

简体中文 3个字节

![image-20241219155426656](/Users/liutao/Library/Application Support/typora-user-images/image-20241219155426656.png)

(首位一定是1)



不要用字节流读取文本文件

getBytes()使用默认方式编码

getBytes(String charsetName) 使用指定的方式进行编码

String(byte[] bytes,String charsetName) 使用指定方式进行解码



### 字符流

字符流 = 字节流+字符集

#### 输入流Reader

FileReader fr

Fr.read()底层

按字符集读取

解码转成十进制数

需要强转(char) chr

```java
FileReader fr = new FileReader("");
int ch;
while((ch = fr.read())!=-1){
	System.out.print((char)ch);
}
```

注意有参数的read()

读取数据，解码，十进制强转，放到数组中

read()中有缓冲区,(8192字节).

```java
FileReader fr = new FileReader();
fr.read();
//创建缓冲区
FileReader fr1 = new FileReader();
//文件数据被清空
int ch;

while((ch = fr.read())!=-1){
	System.out.println((char)ch);
}

//能够读取到缓冲区的数据，但是无法读取文件数据,只会清空文件数据，但是不会清空缓冲区数据
```

#### 输出流Writer

FileWriter

FileWriter(String pasth,boolean append)续写

字节流没有缓冲区，但是字符流有缓冲区

缓冲区写入文件3种情况

缓冲区满了//刷新flush()//close()

### 缓冲流

![image-20241223153411523](/Users/liutao/Library/Application Support/typora-user-images/image-20241223153411523.png)

#### 字节缓冲流

```java
BufferInputStream bis = new BufferInputStream(new FileInputStream());
BufferOutputStream bos = new BufferOutputStream(new FileOutputStream());

byte[] bytes = new byte[1024];
int len;
while((len = bis.read())!=-1){
	bos.write(bytes,0,len);
}
bis.close();
bos.close();
//缓冲区是磁盘读到内存的缓存（磁盘->内存），byte[1024]则是内存中转手的数据(内存->内存)
```

![image-20241223155023942](/Users/liutao/Library/Application Support/typora-user-images/image-20241223155023942.png)

### 字符缓冲流

BufferReader(new FileReader());

BufferWriter(new FileWriter());

带有默认的8k的字符的缓冲区

readLine()//无数据返回null，不会保存换行

newLine()跨平台的写入换行



### 转换流

字符流与字节流的桥梁

![image-20241223163005262](/Users/liutao/Library/Application Support/typora-user-images/image-20241223163005262.png)

```java
//转换流
InputStreamReader isr = new InputStreamReader(new FileInputStream(),"GBK");

OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream(),"UTF-8");

int b;
while((b= isr.read())!=-1){
	osw.write(b);
}
isr.close();
osw.close();

//JDK11后,替换方案

FileReader fr = new FileReader(path,Charset.forName("GBK"));
FileWriter fw = new FileWriter(path,Charset.forName("UTF-8"));

int b;
while((b=fr.read())!=-1){
	fw.write(b);
}
fr.close();
fw.close();
```

字节流想要使用字符流中的方法

```java
//使用字符流readline()读取一整行字节流
BfferReader bf = new BufferReader(new InputStreamReader(new FileInputStream(path)));

String line;
while((line = bf.readline())!=null){
	System.out.println(line);
}
bf.close();
```

### 序列化流

字节流的一种

java对象写入到本地文件

Serializable//没有抽象方法的接口，标志性接口，标志该类可以被序列化

```java
ObiectOutputStreram oos = new ObjectOutputStream(FileOutputStream(path));
oos.writeObject(new Student("",""));
oos.close();
```



### 反序列化流

```java
ObjectInputStream ois = new ObjectInputStream(new FileInputStream(path));

Student stu = (Student) ois.readObject();

ois.close();


```



如果javaBean发生修改，增加版本号

```java
//在javaBean中增加版本号
private static final long serialVersionUID = 1L;
//设定部分参数不能够序列化,添加瞬态关键字
public transient String address;
```



多次写入和读取对象，注意封装到ArrayList中

```java
ObjectOutputStream oos =new ObjcetOutputStrem(new FileOutputStream(path));

//封装
ArrayList<Student> list = new ArrayList<>();
list.add(new Student);
list.add(new Student);

oos.writeObject(list);
oos.close();
//读取

ObjectInputStream ois = new ObjectInputStream(new FileInputStream(path));

ArrayList<Student> listRead = (ArrayList<Student>)ois.readObject();

ois.close();
```

### 打印流

#### printStream

 write

//数据远洋输出//写出+自动刷新+自动换行

print

println

printf

（System.out就是一个打印流）

#### printWriter

有缓冲区，自动刷新需要手动开启

### 解压缩流

```java
File src = new File(path);
File dest =new File(path);
zipinputStream zip = new zipInputStream(new FileInputStream(src));

zipEntry entry;
while((entry = zip.getEntry())!=null){
	System.out.print(entry);
	if(entry.isDirectory()){
		File file = new File(dest,entry.toString());
		file.mkdir();
	}else{
		//读取文件数据
		FileOutputStream fos = new FileOutputStream(new File(dest,entry,toString()));
		byte[] bytes = new byte[1024];
		int len;
		while((len=zip.read())!=-1){
			fos.write(bytes,0,len);
		}
		fos.close();
		//表示一个文件读取完毕
		fos.closeEntry();
	}
}
zip.clsoe();
```

### 压缩流

```java
File src = new File(path);
File destParent = new File(pathParent);
File dest = new File(destParent,src.getName()+".zip");

zipOutputStream zos = new zipOutputStream(new FileOutputStram(dest));
//获取src中文件，变成zipEntry对象，放入压缩包中(需递归)
zip.clsoe();

public static void toZip(File src ,ZipOutputStream zos,String name){
	File[] filelist = src.listFiles();
	for(File file:filelist){
		if(file.isFile()){
			ZipEntry entry = new ZipEntry(name + "\\" + file.getName());
			//创建压缩包中的文件结构
			zos.putNextEntry(entry);
			//写入
			FileInputStream fis = enw FileInputStream(file);
			byte[] bytes = new byte[1024];
			int len;
			while((len = fis.read(bytes))!=-1){
				zos.write(bytes,0,len);
			}
			fis.close();
			zos.closeEntry();
	}else{
		//是文件
		toZip(file,zos,name+"\\"+file.getName());
	}
	}
	zos.close()
}



```

### Commons-io

jar包

![image-20241224160534486](/Users/liutao/Library/Application Support/typora-user-images/image-20241224160534486.png)

#### FileUtils

copyFile

readFileToString

#### IOUtils

### Hutool

### 多线程

#### 多线程实现

##### 继承Thread

重写run()方法

Run()中书写运行代码

```java
//线程类MyThread extend Thread
MyThread t1 = new MyThread();
t1.start();
```



##### 实现Runnable接口实现多线程

重写其中的run方法

```java
//MyRun implements Runnable
//获取当前线程对象currentThread()
```



##### 

可以获取线程执行后的返回值

```java
public class MyCallable implements Callable<Integer>{
	public Integer call() {
		//run code;
	}
}

//创建多线程参数,Callable表示多线程执行的任务的数据参数
MyCallable myCall =new MyCallable();
//创建FutureTask对象(管理多线程运行结果)
FutureTask<Integer> ft = new FutureTask<>(myCall);
//创建线程的对象
Thread t = new Thread();
t.start();
//获取实验结果
Integer result = t.get();
```



##### 总结

![image-20241231170316032](/Users/liutao/Library/Application Support/typora-user-images/image-20241231170316032.png)

###### 常见的成员方法

```java
getName()
setName()//也可以使用MyThread重写Thread的构造方法
currentThread()//获取当前线程对象，当JVM启动，便会有main线程
sleep(long time)//线程休眠
setPriority(int newPriority)//设置优先级
final int newPriority()//获取优先级
setDaemon()//设置守护进程
yield()//出让进程
join()//插入进程


```

（无法抛出父类没有的异常，只能够使用try）

##### 优先级

优先级是一个概率问题

##### 守护线程

当非守护进程结束后，守护进程也结束了

#### 线程声明周期

![image-20241231205234338](/Users/liutao/Library/Application Support/typora-user-images/image-20241231205234338.png)

#### 安全问题-同步问题

锁

```java
static Object obj = new Object();//锁对象必须是唯一static
//一般锁对象使用class字节码文件对象
public void run(){
	synchronized(MyThread.class){
		//run code
	}
}
```

#### 同步方法

![image-20241231211501900](/Users/liutao/Library/Application Support/typora-user-images/image-20241231211501900.png)

```

```



#### 锁

Lock接口,实现类ReentrantLock

```java
static public Lock lock =new ReentrantLock();
public void run(){
	lock.lock();
  try{
    //code
  }catch{
    //error
  }finally{
    lock.unlock();
  }
}
```

##### 死锁

不要写嵌套锁

### 等待唤醒机制

### 线程的状态

![image-20250102135028873](/Users/liutao/Library/Application Support/typora-user-images/image-20250102135028873.png)

JVM中定义的状态

![image-20250102135300146](/Users/liutao/Library/Application Support/typora-user-images/image-20250102135300146.png)

### 线程池

线程复用，一个线程执行完毕，使用存在的线程运行当前线程

如果线程池中没有空闲的线程，则创建新的线程，没有足够的线程额，线程就排队等待

#### ExecutorService

#### 自定义线程池

![image-20250102143328266](/Users/liutao/Library/Application Support/typora-user-images/image-20250102143328266.png)

##### 最大并行数

4核心8线程，8个逻辑处理器，并行数8

![image-20250102144349598](/Users/liutao/Library/Application Support/typora-user-images/image-20250102144349598.png)

thread dump 计算总时间/cpu计算时间



### 网络编程

cs/bs

cs本地数据，提供更好的画面

bs维护简单，本地没有数据



IP：设备在网络中的地址

端口：程序在设备中的唯一标识

协议：数据传输的规则



#### IP

IPV4

IPV6

![image-20250102150239409](/Users/liutao/Library/Application Support/typora-user-images/image-20250102150239409.png)

公网IP,局域网IP

168.192.0.0局域网ip

##### InetAddress

#### 端口

0~65535

0~1023是知名程序使用的端口ftp

#### 协议

TCP

UDP

#### UDP

单播

组播224.0.0.0~239.255.255.255

广播：255.255.255.255

### 反射

反射允许对成员变量，成员方法，构造方法的信息进行编程访问

获取class对象的三种方式

1、Class.forName() 源代码阶段 Class.forName("包名+类名")

2、类名.class 加载阶段

3、对象.getClass() 运行阶段

![image-20250102165312312](/Users/liutao/Library/Application Support/typora-user-images/image-20250102165312312.png)



![image-20250102200453645](/Users/liutao/Library/Application Support/typora-user-images/image-20250102200453645.png)



![image-20250102200517326](/Users/liutao/Library/Application Support/typora-user-images/image-20250102200517326.png)

![image-20250102200812716](/Users/liutao/Library/Application Support/typora-user-images/image-20250102200812716.png)

### 动态代理

类加载器：将class文件加载到内存中classLoader()

?

