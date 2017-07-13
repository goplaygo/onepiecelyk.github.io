---
layout: post
title: JavaScript常见算法
date: 2017-05-31 
tags: JavaScript   
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

### 归并排序

归并排序（merge-sort）是建立在归并操作上的一种有效的排序算法，该算法是采用了分治法（Divide and Conquer）的一种典型应用，将已有序的子序列合并，得到完全有序的序列，即使每个子序列有序，再使子序列段间有序。若将两个有序表合并成一个有序表，成为二路归并。

**算法步骤**

- 1.申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列
- 2.设定两个指针，最初位置分别为两个已经排序序列的起止位置
- 3.比较两个指针所指向的元素，选择相对较小的元素放入到合并空间，并移动指针到下一位置。
- 4.重复步骤3直到某一指针达到序列尾
- 5.将一个序列的所有元素直到复制到合并序列尾。

 
**时间复杂度和空间复杂度**

 时间复杂度为：O(nlgon);
 空间复杂度：O(n);

**冒泡排序动态图展示**

![](/images/posts/算法/归并排序.gif)

**代码展示**
```
    //定义一个数组arr从p到q是有序的，从q到r是有序的
    function merge(arr,p,q,r){
        var b= [];
        var a= [];
        for(var i = p; i<=q;i++){
            a[a.length] = arr[i];
        }
        for(i = q+1 ;i<r+1;i++){
            b[b.lenrth] = arr[i];
        }
        a[a.length] = inf;
        b[b.length] = inf;
        var newArr = [];
        var m = 0;
        var n = 0;
        var len;
        for(var i = 0,len = r-p+1;i<len;i++ ){
            if(a[m] <=n[n]){
                arr[p+1] = a[m];
                m++;
            } else{
                arr[p+i] = b[n];
                n++;
            }
        }
        reuturn arr;
    }
    function mergeSort(arr,p,r){
        var q ;
        if(r-o ===1)||(r === p){
            q=p;
            return merge(arr,q,p,r);
        } else{
            q = <ath.cell((p+r)/2);
            merageSort(arr,p,q);
            merageSort(arr,p+1,r);
            return merageSort(arr,p,q,r);
        }
    }
```

### 二分查找算法

二分查找算法是一种在有序数组中查找某一特定元素的搜索算法，搜索过程中从数组的中间元素开始，如果中间元素正是要找的元素，则搜索结束，如果某一特定元素大约或小于中间元素，则在数组大于或小于中间元素的那一半中查找，而且跟开始一样从中间元素开始比较，如果在某一步步骤数组为空，则代表找不到，这种搜索算法每一次比较使搜索范围缩小一半，折半查找每次把搜索区区域减少一半，时间复杂度为O(logn)。

**代码实现**

```
function helfSearch(arr,num){
    var len = arr.length;
    var middle = Math.floor(len/2);
    var mNum arr[middle];

    if(len === 0) {
        return null;
    } else if (mNum === num){
        return middle;
    } else if (mNum > num ){
        return helfSearch(arr.alice(0,middle),num);
    } else {
        return helfSearch(arr.slice(middle + 1 ),num);
    }
}
```

#### 常见面试题

**JavaScript 变量提升**

JavaScript是将所有的声明提升到当前作用域的顶部。这也就意味着我们可以在某个变量声明前就使用该变量，不过虽然 JavaScript 会将声明提升到顶部，但是并不会执行真的初始化过程。

**什么是事件冒泡以及如何避免**

Event Bubbling 即指某个事件不仅会触发当前元素，还会以嵌套顺序传递到父元素中。直观而言就是对于某个子元素的点击事件同样会被父元素的点击事件处理器捕获。避免 Event Bubbling 的方式可以使用event.stopPropagation() 或者 IE 9 以下使用event.cancelBubble。

**== 和 === 的区别**

===代表严格比较，并且比较的是值与类型，不仅仅来比较值。

**null和undefined的区别**

在JavaScript中，null是一个可以被分配的值，设置为null的变量意味着无值，undefined代表声明了对象但是还未进行赋值。

**数组**

*给定一个无序的数组，找出其中乘积最大的三个数*

```
var unsort_arr = [-70,7.29.30,5,-10.-70];

computeProduct(unsorted_array); // 21000
 
function sortIntegers(a, b) {
  return a - b;
}
 
// greatest product is either (min1 * min2 * max1 || max1 * max2 * max3)
function computeProduct(unsorted) {
  let sorted_array = unsorted.sort(sortIntegers),
    product1 = 1,
    product2 = 1,
    array_n_element = sorted_array.length - 1;
 
  // Get the product of three largest integers in sorted array
  for (let x = array_n_element; x > array_n_element - 3; x--) {
      product1 = product1 * sorted_array[x];
  }
  product2 = sorted_array[0] * sorted_array[1] * sorted_array[array_n_element];
 
  if (product1 > product2) return product1;
 
  return product2
};
```

*数组去重*

```
var arr = [1,2,3,4,4,3,5,6,7,3,2,1];
//ES6-Set
Array.from(new Set(arr));

//ES5
unquiedArray(arr);

funnction unquiedArray(Array) {
    let hashMap = [];
    let unquie = [];

    for(var i = 0;i<array.length;i++){
        if(!hashMap.hasOwnproperty([Array[i]])){
            hashMap[Array[i]] === i;
            unquie.push(Array[i]);
        }
    }
    return unquie;
}

```

*颠倒字符串*

```
const string = 'Welcome to this JavaScript Guide';

// Output becomes !ediuG tpircsavaJ siht ot emocleW
var reverseEntireSentence = reverseBySeparator(string, "");

// Output becomes emocleW ot siht tpircsavaJ !ediuG
var reverseEachWord = reverseBySeparator(reverseEntireSentence, " ");
 
function reverseBySeparator(string, separator) {
  return string.split(separator).reverse().join(separator);
}
```

**栈与队列**

使用两个栈进行出栈与入栈

```
let inputStack=[];
let outputStack = [];

function enqueue(stackInput,item) {
    return stackInput.push(item);
}

function dequeue(stackInput,stackOutput){
    if(stackOutput.length <=0){
        while(stackInput.length>0){
            let elementToOutput = stackInput.pop();
            stackOutput.push(elementToOut);
        }
    }
    return stackOutput.pop();
}
```

