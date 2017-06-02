---
layout: post
title: JavaScript常见算法总结
date: 2017-06-01 
tags: JavaSctipt   
---

### JavaScript常见算法总结

本文的所有知识点都是来源于网络，是自己总结出来的。

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

**算法步骤**

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

快速排序是由东尼·霍尔在1962年提出的一种排序算法。
其主要思想是使用分治法（Divide and conquer）策略将一个将要排序的数据分分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据要小，然后按照此方法对着两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序数列。

**算法步骤**

 - 从数列中挑选出一个元素，成为基数（pivot）
 - 重新排列数列，所有元素比基准数小的放在前面，所有元素比基准数大的放到后面（相同的可以放在任意一边），在这个分区退出以后，该基准数就处于数列的中间位置。这个称为分区操作。
 - 递归的把小于基准数的子数列和大于基准数的子序列排序。

 递归的最底部情形，是数列的大小是零或一。也就是说永远都被排序好了，

 **时间复杂度和空间复杂度**

 时间复杂度为：O(nlgon);
 空间复杂度：O(logn);

**冒泡排序动态图展示**

![](/images/posts/算法/快速排序.gif)

 **代码实现**
```
var quickSort = function (arr){
    if(arr.length <=1) {return arr;}
    var pivotIndex = Math.floor(arr.length / 2);
    var povit = arr.splice(pivotIndex,1)[0];
    var left = [];
    var right = [];
    for ( var i = 0; i<arr.length;i++){
        if(arr[i] < pivot){
            left.push(arr[i]);
        } else{
            right.push(arr[i]);
        }
    }
    return quickSort(left).concat([pivot],auickSort(right));
}
```

