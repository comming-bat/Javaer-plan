
##目录
- [刚开始](#刚开始)
- java
 - [计算机基础](#计算机基础)
 - [JAVA基础](#JAVA基础)
 - [高可用架构](#高可用架构)

- 数据结构
 - [基本数据类型](#基础数据类型)
 - [二分查找](#二分查找)
 - [B+ tree](#B-tree)
 - 归并
 - BitMap
 - BloomFilter
 - 进程和线程

- 监控
 - [硬件性能评估](#硬件性能评估)
 - 日志规范
 - 进程监控
- 安全
- 扩展知识
 - [爬虫](#爬虫)
 - [网络](#网络)
 - [操作系统](#Linux)

##刚开始
```
1.每家公司都会随机挑选几个工程师出来面试，每个人有自己的风格，其中有失败的也是比较正常的，接下来要做的就是准备好每一次面试
2.这是一份历时4个月的计划，前面的已经学习的要反复练习
3.每天花3个小时
4.学习的过程中尽量去造轮子
```
[参考1](http://www.cnblogs.com/wilsonwen/archive/2013/05/22/3093383.html) [参考2](http://www.cnblogs.com/wilsonwen/archive/2013/05/26/3100025.html)
##计算机基础
一、基础单位：bit, byte, kb, M, G, T

1. 代码是如何在cpu执行的
2. 程序是如何编译的
3. 基础数据是如何存储的，[float](http://www.cnblogs.com/xugang/archive/2010/05/04/1727431.html)，int
4. Unicode [字符编码笔记：ASCII，Unicode和UTF-8](http://www.ruanyifeng.com/blog/2007/10/ascii_unicode_and_utf-8.html)

二、[计算机科学cs50：程序算法](http://open.163.com/special/opencourse/cs50.html)  [算法导论](http://open.163.com/special/opencourse/algorithms.html)

1. 复杂度
2. 增长阶数
3. 渐进性

三、CPU缓存，L1，L2，L3和伪共享

1. RingBuffer

##JAVA基础
一、 JVM

1. Java内存模型
2. Java内存管理
3. Java堆和栈
4. 垃圾回收
5. JVM各种参数及调优
6. jps, jstack, jmap, jconsole, jinfo, jhat, javap

[参考](./Java性能优化.md)

##高可用架构
- web缓存
 - 缓存策略 [参考1](http://baotiao.github.io/2016/09/14/cache-policy/)
 - memcached 内存结构：slab机制-有初始化容量，采用LRU策略 [参考](http://blog.itpub.net/15480802/viewspace-1422370/)
 - redis 内存结构：HASH+链表+自定义数据结构  [参考1](http://www.searchtb.com/2011/05/redis-storage.html) [参考2](http://blog.csdn.net/yfkiss/article/details/23775917)
 - 数据库
	- B+Tree
	- LSM-Tree
	- 主从
	- 集群
- 负载均衡

		LVS ，Nginx， Apache， dns， cdn
- SOA
	- rpc 序列化,和队列化的系统
	
			thrift，dubbo，dubbox
	- SpringCloud [参考1](http://docs.springcloud.cn/)	[参考2](http://www.w2bc.com/Article/87106)
- 高可用算法
	- Paxos 一致性算法:
	- 一致性哈希
- 缓存

##基础数据类型

一、数组

二、链表

三、堆栈

四、队列

五、HashMap [面试参考1](http://www.admin10000.com/document/3322.html) [hashMap源码解读](https://my.oschina.net/boxizen/blog/177744) [HashMap死循环](http://ifeve.com/hashmap-infinite-loop/)

六、树

七、字典

##二分查找
```java
public static int binarySearch(int[] arry, int low, int height, int desc){
    	if(arry == null || desc<0){ 
    		throw new IllegalArgumentException("参数为空");
    	}
    	int middle = 0;
    	while(low < height){
    		middle = low + (height-low)>>1;
    		if(arry[middle] == desc){
    			return middle;
    		}else if (arry[middle]>desc) {
    			return binarySearch(arry,low,middle-1,desc );
			}else if (arry[middle]<desc) {
				return binarySearch(arry,middle+1,height,desc );
				
			}
    	}
    	return -1;
    }
```
##B+ tree 
```
聚集索引、非聚集索引
```
[参考1](http://www.ruzuojun.com/topic/420.html)	 [参考2](http://www.cnblogs.com/lyhabc/p/3196479.html)
##硬件性能评估
- vmstat 查看进程数，cpu情况 us+sy>80% cpu不足
- free -g +buffers 应用程序可用内存
- iostat -xdk 1 %util=100% 磁盘满， await>wvctm IO等待，= 良好
- top loadavg > cpu数，线程过多，-H -p 显示线程

##爬虫
一、[参考](https://www.zhihu.com/question/31427895)

##网络
一、TCP/IP 模型 [四层](http://blog.csdn.net/superjunjin/article/details/7841099)	[七层](http://blog.csdn.net/yaopeng_2005/article/details/7064869)	[三次握手](http://geek.csdn.net/news/detail/114503)

##Linux
一、Shell

二、VIM
