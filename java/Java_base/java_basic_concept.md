## java基础概念和常识
**1. java的特性**

**简单性：**
没有头文件、指针运算、结构、联合、操作符重载、虚基类

**面向对象：**
将重点放在数据（即对象）和对象的接口上。
与c++不同主要在于多继承上，java取而代之的是简单的接口概念以及元类模型。

**网络技能：**
java的网络能力强大且易用

**健壮性：**
早期问题检测、后期动态检测（运行时）、采用的指针模型可以消除重写内存和损坏数据的可能性。

**安全性：**
一开始，java就设计成能够防范各种袭击。

**体系结构中立：**
java精心设计的字节码不仅可以很容易再任何机器上解释运行，而且还可以迅速第翻译成本地机器的代码。解释字节码肯定会比全速地运行机器指令慢很多，但虚拟机有个选项可以将使用最频繁的字节码序列翻译成机器码，这个过程叫即时编译。

**可移植性：**
java的数据类型具有固定的大小，消除代码移植时令人头疼的主要问题。二进制数据以固定的格式进行的存储和传输，消除了字节顺序的困扰。字符串是用标准的Unicode格式存储的。

**解释型：**
Java解释器可以再任何移植了解释器的机器上执行java字节码。

**高性能：**
解释器优化比以前好了，如即时编译。

**多线程：**
java多线程使用起来更便捷。

**动态性：**
java当前版本允许程序员知道对象的结构和行为，这对于必须在运行是分析对象的系统来说非常有用。

**2. java的一些术语**

**JDK：**
java development kit Java开发工具箱。编写java程序的程序员使用的软件。是功能齐全的java SDK。拥有JRE所拥有的一切，还有编译器（javac）和工具（如javadoc和jdb）。它可以创建和编译程序。

**JRE：**
java runtime environment Java运行时环境，运行Java程序的用户使用的软件。它是运行已编译Java程序所需的所有内容的集合，包括java虚拟机、Java类库、java命令以及其他的一些基础构件。但是不能用于创建新程序。

**JVM：**
Java虚拟机是运行Java字节码的虚拟机。JVM有针对不同系统的特定实现，目的是使用相同的字节码，它们都会给出相同的结果。

**字节码：**
在java中，JVM可以理解的代码叫字节码（即拓展名为.class的文件），它不面向任何特定的处理器，只面向虚拟机。java语言通过字节码的方式，在一定的程度上解决了传统解释型语言执行效率低的问题，同时又保留了解释型语言的可移植性。所以java程序运行时比较高效，而且java程序无需重新编译便可以在多种不同的操作系统的计算机上运行。

