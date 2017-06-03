---
layout: post
title: JavaScript常见算法
date: 2017-05-31 
tags: Javascript   
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

 **代码实现**（代码来自网上）
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

 **代码实现**（代码来自阮一峰老师网站）
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

### 堆排序

堆排序（Headpsort）是指利用堆积树这种数据结构所设计的一种排序算法，发明人是罗伯特·弗洛伊德，它是选择排序的一种。可以利用数组的特点快速定位索引的元素。堆分为大根堆和小根堆，是完全二叉树。

**算法步骤**

 - 创建一个堆H[0...n-1];
 - 把堆首（最大值）和堆尾互换。
 - 把堆的尺寸缩小1，并调用shift_down（0），目的是把新的数组顶端数据调整到相应位置。
 - 重复步骤2，直到堆的尺寸为1

 **时间复杂度和空间复杂度**

 时间复杂度为：O(nlgon);
 空间复杂度：O(1);

**冒泡排序动态图展示**

![](/images/posts/算法/堆排序.gif)

**代码展示**

```
var h = [];//用来存放堆的数组
var n ;//用来存储堆中元素的个数，也是堆的大小。
//交换函数，交换堆中两个元素的值
function swap(x,y){
    var t;
    t = h[x];
    h[x] = h[y];
    h[y] = t;
}
//向下调整函数
function siftdown(i){
    //传入一个需要向下调整的节点编号i，这里传入1，即从堆的定点开始向下调整
    var flag = 0,
    var t;
    //当i节点有儿子（至少有个左儿子）并且继续调整的时候循环执行
    while(i*2 <=n && flag === 0){
        //首先判断它和左儿子的关系，并用t记录值较小的节点编号
        var leftChidrenIndex = i * 2 + 1 ,
        var rightChildrenIndex = i * 2 + 2;
        if(h[i] > h[leftChidrenIndex]){
            t = leftChidrenIndex;
        } else {
            t = i;
        }
        //如果他有右儿子，在右儿子进行讨论
        if(rightChildrenIndex <= n){
            //如果右儿子的值更小，更新较小的节点编号
            if(h[t] >h[rightChildrenIndex]){
                t = rightChildrenIndex;
            }
        }
        //如果发现最小的节点编号不是自己，说明子节点中有比父节点更小的
        if(t !== i){
            swap(t,i);//交换他们
            i = t;
        } else {
            flag = 1;
        }
    }
}
//建立堆函数
function heap() {
    var i;
    for(i = n/2 ;i>=0;i--){
        siftdown(i);
    }
    console.error(h);
}
//删除最大元素
function deleteMax(){
    var t ;
    t =h[0];//用一个临时变量记录堆顶点的值
    comnsole.info(t);
    h[0] =h[n];//将堆的最后一个点赋值到堆顶！
    n--;
    siftdown(0);//向下调整（相当于重新建造堆）
    return t;
}
function heapsort (arr) {
    h = arr;
    var num = arr.length;
    var i;
    n = num - 1;
    //建堆
    heap();
    var sortArr=[];
    for(i =0; i<=num;i++){
        sortArr.push(deleteMax());
    }
    return sortArr;
}
```