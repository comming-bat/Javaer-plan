- java
 - [基础](#计算机基础)
 - 微服务SpringCloud
 - Socket
- 数据库
 - 主从
- 数据结构
 - [二分查找](#二分查找)
 - 归并
 - BitMap
 - BloomFilter
 - RingBuffer
- DNS
- CND
- 监控
 - [硬件性能评估](#硬件性能评估)
 - 日志规范
 - 进程监控
- 安全

##计算机基础
基础单位：bit, byte, kb, M, G, T

##硬件性能评估
- vmstat 查看进程数，cpu情况 us+sy>80% cpu不足
- free -g +buffers 应用程序可用内存
- iostat -xdk 1 %util=100% 磁盘满， await>wvctm IO等待，= 良好
- top loadavg > cpu数，线程过多，-H -p 显示线程
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
