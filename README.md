# 面试集锦总结文档  
## [在线C++编译器](https://wandbox.org/)  
## 杂项



### 1、fwrite和fflush作用

[fwrite,fflush,你不知道的事！](https://blog.csdn.net/zhangxiong2532/article/details/50608898)

[那些年，坑死自己的事之fread/fwrite](https://www.cnblogs.com/ashboy/archive/2014/11/30/fread.html)
### 2、const和define的区别
#define 的时候记得加括号，因为有优先级  
#define min(a,b) ((a>b)?b:a)  
[const常量与define宏定义的区别](https://blog.csdn.net/sinat_20265495/article/details/52945960)  
### 3、进程与线程区别
线程占有的资源:栈、寄存器、状态、程序计数器  
进程占有的资源:地址空间、全局变量、打开的文件、子进程、信号量、账户信息  
[线程、进程那些是共享、哪些是独占](https://www.nowcoder.com/questionTerminal/dbf3fb0fce0a4a199cd985796bdcad78?from=14pdf)
### 4、字节对齐
[C/C++内存对齐详解](https://mp.weixin.qq.com/s?__biz=MzIwNTc4NTEwOQ==&mid=2247483922&idx=1&sn=6fdbd8178dfaccf7732fb7c9b82a4c94&scene=21#wechat_redirect)
### 5、static用法
* 作为类的静态成员，被所有的类对象所共有  
* static加在局部变量的前面改变其存储类型使之成为静态局部变量，会延长它的生存周期，但是注意不会改变其作用域！！！   
* static加在全局变量的前面会限制该变量作用域为文件作用域，也就是说static全局变量只能在定义该变量的文件中使用，不能被其它文件使用。
加在函数定义或声明的前面，也是限制函数作用域到文件作用域。  
* sizeof不将静态成员变量的大小计算在内   
* 可以通过类名来访问静态成员（常见instance）   
static aaa* instance(void)
{
	static aaa x;
	return &x;
}
访问方式aaa::instance()
* 静态成员函数不能直接访问类的非静态成员，但可以通过以下方式访问  
[C++静态成员函数访问非静态成员的几种方法](https://www.cnblogs.com/rickyk/p/4238380.html)
[类的静态成员](https://mp.weixin.qq.com/s?__biz=MzIwNTc4NTEwOQ==&mid=2247483732&idx=1&sn=942f4ee8f3e0617b1d189eecd492d73f&scene=21#wechat_redirect)

### 6、智能指针
将释放内存操作写进析构函数
auto_ptr可以转移所有权，当有两个同时指向同一个内存，当退出作用域的时候会析构两次，造成错误；unique_ptr如果出现这种情况链接不通过；shared_ptr则采用内部计数器的方式，当0的时候就不进行析构
[智能指针share_ptr和unique_ptr](https://mp.weixin.qq.com/s?__biz=MzIwNTc4NTEwOQ==&mid=2247483809&idx=1&sn=373d64600b944be7258304119dae247e&scene=21#wechat_redirect)

### 7、多态
* 多态，即多种状态，在面向对象语言中，接口的多种不同的实现方式即为多态。
* C++ 多态有两种：静态多态（早绑定）、动态多态（晚绑定）。静态多态是通过函数重载实现的；动态多态是通过虚函数实现的。
* 多态是以封装和继承为基础的。

* 静态多态：早绑定，通过函数重载
class A
{
public:
    void do(int a);
    void do(int a, int b);
};
* 动态多态：晚绑定，用 virtual 修饰成员函数，使其成为虚函数
	* 普通函数不能是虚函数，应是类成员函数
	* static静态函数不能是虚函数
	* 构造函数不能是虚函数（因为在调用构造函数时，虚表指针并没有在对象的内存空间中，必须要构造函数调用完成后才会形成虚表指针）
	* 析构是虚函数的情况，为了解决基类的指针指向派生类对象，并用基类的指针删除派生类对象 Base *p=new son。[析构函数为什么要写成虚函数](https://blog.csdn.net/u011740322/article/details/10081505) 
	* 内联函数不能是表现多态性时的虚函数
* 虚函数的实现原理，虚函数表
	[虚函数表](https://blog.csdn.net/wuchuanpingstone/article/details/6742465/)

### 8、指针与引用
前者别名引用，后者句柄引用
[指针和引用区别](https://blog.csdn.net/study__linux/article/details/51352206)

### 9、STL容器
### 索引
[STL 方法含义](https://github.com/huihut/interview/tree/master/STL)
### 容器
[关于容器的面试题](https://www.cnblogs.com/wulala1119/p/4758345.html)  

容器 | 底层数据结构 | 有无序 | 可不可重复 | 其他
---|---|---|---|---
[array](https://github.com/huihut/interview/tree/master/STL#array)|数组|无序|可重复|支持快速随机访问
[vector](https://github.com/huihut/interview/tree/master/STL#vector)|数组|无序|可重复|支持快速随机访问
[list](https://github.com/huihut/interview/tree/master/STL#list)|双向链表|无序|可重复|支持快速增删
[deque](https://github.com/huihut/interview/tree/master/STL#deque)|双端队列（一个中央控制器+多个缓冲区）|无序|可重复|支持首尾快速增删，支持随机访问
[stack](https://github.com/huihut/interview/tree/master/STL#stack)|deque 或 list 封闭头端开口|无序|可重复|不用 vector 的原因应该是容量大小有限制，扩容耗时
[queue](https://github.com/huihut/interview/tree/master/STL#queue)|deque 或 list 封闭底端出口和前端入口|无序|可重复|不用 vector 的原因应该是容量大小有限制，扩容耗时
[priority_queue](https://github.com/huihut/interview/tree/master/STL#priority_queue)|vector|无序|可重复|vector容器+heap处理规则
[set](https://github.com/huihut/interview/tree/master/STL#set)|红黑树|有序|不可重复|
[multiset](https://github.com/huihut/interview/tree/master/STL#multiset)|红黑树|有序|可重复|
[map](https://github.com/huihut/interview/tree/master/STL#map)|红黑树|有序|不可重复|
[multimap](https://github.com/huihut/interview/tree/master/STL#multimap)|红黑树|有序|可重复|
hash_set|hash表|无序|不可重复|
hash_multiset|hash表|无序|可重复|
hash_map|hash表|无序|不可重复|
hash_multimap|hash表|无序|可重复|


## TCP UDP
### 1、对udp socket做connect，含义是？
对udp做connect是可以的，其效果是给这个sock绑定对端地址，普通的用法是：sendto(udpsock, xxx, 对端地址)，如果你先connect对端地址，然后就可以直接用send来发送udp，不用每次指定对端地址了，因为每次sendto将对端地址传入并拷贝到内核，还是有点费时间的
### 2、不用listen和accept，如何建立tcp链接
![image](https://raw.githubusercontent.com/CARLPC/sharedoc/master/%E7%8A%B6%E6%80%81%E8%BF%81%E7%A7%BB%E5%9B%BE.jpg)  
其实考的是tcp状态图中很特殊的一条线、tcp协议本身是允许不监听直接建立链接的、双方互相对撞syn包即可，具体测试方法很简单，你弄两个进程，分别创建tcp sock，绑定各自端口，然后死循环connect对方，只要两个connect刚好对上，链接就建立了。
实际这条应该是为了简化协议栈而引入的，不过貌似tcp打洞可以这样搞，p2p的时候，但是也跟nat策略有关，因为一般是udp打洞，所以很少碰到类似场景，但理论上是可行的





## 树
### 1、二叉树
每个节点最多有两个叶子节点。  
[二叉树](https://blog.csdn.net/cai2016/article/details/52589952)

### 2、完全二叉树
叶节点只能出现在最下层和次下层，并且最下面一层的结点都集中在该层最左边的若干位置的二叉树。  
[完全二叉树](https://baike.baidu.com/item/%E5%AE%8C%E5%85%A8%E4%BA%8C%E5%8F%89%E6%A0%91/7773232?fr=aladdin)

### 3、平衡二叉树
左右两个子树的高度差的绝对值不超过1，并且左右两个子树都是一棵平衡二叉树。  
[浅谈数据结构-平衡二叉树](http://www.cnblogs.com/polly333/p/4798944.html)
### 4、红黑树
[wiki红黑树](https://zh.wikipedia.org/wiki/%E7%BA%A2%E9%BB%91%E6%A0%91)  
[最容易懂得红黑树](https://blog.csdn.net/sun_tttt/article/details/65445754)这篇里有几个地方讲错了，能翻墙的最好去wiki上看比较准确  
[《浅谈算法和数据结构: 九 平衡查找树之红黑树》](http://www.cnblogs.com/yangecnu/p/Introduce-Red-Black-Tree.html)
## 进程通信
### 1、管道
### 2、命名管道
[管道文件(pipe,popen,mkfifo,pclose,dup2)](http://lobert.iteye.com/blog/1707450)  

### 3、消息队列

[linux c学习笔记----消息队列（ftok,msgget，msgsnd，msgrcv，msgctl）](http://lobert.iteye.com/blog/1743256)  
[Linux进程间通信（七）：消息队列 msgget()、msgsend()、msgrcv()、msgctl()](https://www.cnblogs.com/52php/p/5862114.html)

### 4、信号
[Linux系统的信号详解](https://blog.csdn.net/u010889616/article/details/48157937)  
[Linux的信号 SIGALRM和SIGINT的使用示例](https://blog.csdn.net/u010889616/article/details/48158165)  
[CTRL-C发生了什么--见书本186页](https://github.com/CARLPC/sharedoc/blob/master/unix%20cookbook.pdf)

### 5、信号量(PV操作)
[进程间通信方式——信号量（Semaphore）](https://blog.csdn.net/skyroben/article/details/72513985)  
[临界数据、临界区和原子操作](https://www.cnblogs.com/midhillzhou/p/7600837.html)
### 6、共享内存
[共享内存 shmget()、shmat()、shmdt()、shmctl()](https://www.cnblogs.com/52php/p/5861372.html)

