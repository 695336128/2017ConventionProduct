
# Java基础-Java Object类公有方法

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Object类是Java中其他所有类的祖先，该类位于java.lang中。java.lang包包含着Java最基础和核心的类，在编译时会自动导入。Object类没有定义属性，一共有13个方法，具体的类定义结构如图:

![N|Solid](https://images0.cnblogs.com/i/426802/201404/262136225915517.jpg)


### 1.类构造器 public Object();

Java 中规定：在类定义过程中，对于未定义构造函数的类，默认会有一个无参数的构造函数，作为所有类的基类。在源码中，未给出Object类构造函数的定义，但实际上这个构造函数是存在的。
**并不是所有类的构造函数都是Public**

### 2.public final  Class<?> getClass();

**getClass() 返回的是次Object对象的类对象、运行时类对象Class<？>。效果与Object.class相同**

类对象：在Java中，类是对具有一组相同特征或行为的实例的抽象并进行描述，对象则是此类所描述的特征或行为的具体实例。

### 3.public boolean equals(Object obj) 

==表示的是变量值完全相同（对于基础类型，地址中存储的是值，引用类型则存储只想实际对象的地址）；
equals表示的是对象的内容完全相同，此处的内容多指对象的特征/属性。
**equals()方法的正确理解应该是：判断两个对象是否相等。**
**重写equals()方法必须重写hashCode()方法。**


### 4.public int hashCode();

hashCode()方法返回一个整型数值，表示该对象的哈希码值。
hashCode()具有如下约定：
- 在Java应用程序执行期间，对于同一对象多次调用hashCode()方法时，其返回的哈希码是相同的，前提是将对象进行equals比较时所用的标尺信息未做修改。在Java应用程序的一次执行到另一次执行，同一对象的hashCode()返回的哈希码无需保持一致；
- 如果两个对象相等（调用equals()方法），那么这两个对象调用hashCodeO()返回的哈希码也必须相等；
- 反之，两个对象调用hashCode()返回的哈希码相等，这两个对象不一定相等。

**hashCode()方法的作用主要用于增强哈希表的性能**
以集合类中Set为例，当添加一个对象是，需要判断现有集合中是否已经存在与此对象相等的结果，如果没有hashCode()方法，需要将Set进行一次遍历，并逐一用equals()方法判断量对象是否相等，时间复杂度为`n(o)`。通过借助于hashCode方法，先计算出新对象的哈希码，然后根据哈希算法计算出此对象的位置，直接判断此位置上是否已有对象即可。


### 5.protected Object clone() throws CloneNotSupportedException

clone函数返回的是一个引用，指向的新的clone出来的对象，此对象与原对象分别占用不同的堆空间。

clone()的正确调用是需要实现Cloneable接口，如果没有实现Cloneable接口，并且子类直接调用Object类的clone()方法，则会抛出CloneNotSupportedException异常。
Cloneable接口仅是一个表示接口，接口本身不包含任何方法，用来只是Object.clone()可以合法的被子类引用所调用。

### 6.public String toString() 

toString()方法返回该对象的字符串表示。具体实现如下：
```
    public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
```

**toString() 是由对象的类型和其哈希码唯一确定的，同一类型但不相等的两个对象分别调用toString()方法返回的结果可能相同。**


### 7/8/9. wait(...)/nitify()/notifyAll()

这几个方法主要用于java多线程之间的写作。
- wait(...)： 调用此方法所在的当前线程等待，知道在其他线程上调用此方法的主调（某一对象）的`notify()`/`notifyAll()`方法。wait(...)方法调用后当前想成将立即阻塞，且释放其所持有的同步代码块中的锁，直到被唤醒或超时或打断后并且重新获取到锁后才能继续执行；
- notify()/notifyAll()：唤醒在此对象监视器上等待的单个线程/所有线程。方法调用后期所在线程不会立即释放所持有的锁，知道其所在同步代码块中的代码执行完毕，此时释放锁，因此，如果其同步代码块后带有代码，其执行则依赖于JVM的线程调度。

### 10.protected void finalize() throws Throwable{}

finalize方法主要与java垃圾回收机制有关。这是一个空方法。
Object中定义finalize方法表明java中每一个对象都将具有finalize这种行为，其具体调用时机在：JVM准备对此对象所占用的内存空间进行垃圾回收前，将被调用。
