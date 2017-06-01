---
layout: post
title: JavaScript常见算法总结
date: 2017-05-31 
tags: JavaSctipt   
---

### JavaScript常见算法总结

说起算法大家都会考察时间复杂度和空间复杂度。

### 先来看张图（图片来源于网络）
![](/images/posts/算法/1.png)
上述图片我们可以看出各种排序算法的时间和空间复杂度，并且是否稳定。

*名词解释：*
 - n:数据规模
 - k:‘桶’的规模
 - in-place:占用常用内存，不占用额外内存
 - out-place:占用额外内存
### 冒泡排序(Bubble sort)
众所周知冒泡排序算法是排序算法里最简单的一种方式了，所以大家都喜欢把它放到第一位。
冒泡算法的由来是因为越大的元素经过交换慢慢‘浮’到数列的顶端。

**原理**

 - 1：比较相邻的元素。如果第一个比第二个大，那么就交换他们两个。
 - 2：对每一对相邻元素做同样的工作，从开始第一对到结尾最后一对。所以最后一个元素应该是最大的元素。
 - 3：针对所有的元素重复以上步骤。
 - 4：持续每次对越来越少的元素重复上面的步骤，直到没有任何一个数字需要比较。

 **时间复杂度和空间复杂度**

 时间复杂度为：O(n^2);
 空间复杂度：O(n^2);

**冒泡排序动态图展示**

![](/images/posts/算法/冒泡排序.gif)

 **代码实现**
 ```
function BubbleSort(arr){
    var i = arr.length,j;
    var temp;
    while(i>0){
        for(j=0；j < i -1; j++){
            if(arr[j]>arr[j+1]){
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j +1 ] = temp;
            }
        }
        i--;
    }
    return arr;
}
 ``` 
但是冒泡排序的时间复杂度太大了，如果元素多的话，会占用很长时间，所以前人就对冒泡排序进行了两种优化，主要思想是：
 - 第一种是设置一个一个标志位聊标记是否发生变化，如果没有交换就提前结束；
 - 第二种是记录最后发生交换的位置，作为下一趟比较结束的位置。

 代码实现如下：

 ```
 //第一种
 function BubbleSort1(arr,n){
    var flag;
    var temp;
    for(var i = 0;i<n;++i){
        var flag = 0;
        for(var j =0;j< n-1-i; ++j){
            if(arr[j]<arr[j+1]){
                flag = 1;
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j + 1] = temp;
            }
        }
        if(flag === 0){
            break;
        }
    }
 }
 //第二种
 function BubbleSort2(arr,n){
     var temp;
     var flag = n;
     for(var i = 0; i<flag;++i){
         var k =flag;
         var flag =0;
         for(var j = 0;j = k;++j){
            if(arr[j] < arr[j + 1]){
                flag = j;
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j+1] = temp
            }
         }
     }
 }
 ```
 使用优化后的冒泡排序后，就是时间复杂度大大减少了

 ### 快速排序



