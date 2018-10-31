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

