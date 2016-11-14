- java
 - [基础](#计算机基础)
 - 微服务SpringCloud
 - Socket
- 数据库
- 数据结构
 - [二分查找](#二分查找)
 - 归并
 - BitMap
 - BloomFilter
 - RingBuffer
- DNS
- CND
- 监控
- 安全

##计算机基础
基础单位：bit, byte, KB, MB, GB, TB

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
