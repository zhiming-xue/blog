---
title: 常用排序算法总结1一一冒泡排序 
date: 2016-08-28 19:38:42
tags: [sort, algorithm]
toc: true
categories: 算法
---

## 前言

排序算法是一种能将一串数据依照特定排序方式进行排列的一种算法。最常用到的排序方式是***数值顺序***以及***字典顺序***。

有效的排序算法在一些算法（例如搜索算法与合并算法）中是重要的，如此这些算法才能得到正确解答。排序算法也用在处理文字数据以及产生人类可读的输出结果。基本上，排序算法的输出必须遵守下列两个原则：

- 输出结果为递增序列（递增是针对所需的排序顺序而言）
- 输出结果是原输入的一种排列、或是重组


### 排序算法分类

在计算机科学所使用的排序算法通常被分类为：

- 计算的时间复杂度（最差、平均、和最好性能），依据列表（list）的大小(n)。一般而言，好的性能是O(n log n)，且坏的性能是O(n2)。对于一个排序理想的性能是O(n)。仅使用一个抽象关键比较运算的排序算法总平均上总是至少需要O(n log n)。
- 内存使用量（以及其他电脑资源的使用）
- **稳定性**：稳定排序算法会让原本有相等键值的纪录维持相对次序。也就是如果一个排序算法是稳定的，当有两个相等键值的纪录R和S，且在原本的列表中R出现在S之前，在排序过的列表中R也将会是在S之前。
- 依据排序的方法：`插入、交换、选择、合并`等等。


<!--more-->

![排序算法比较](http://img.blog.csdn.net/20160828112755020)
## 定义

> 冒泡排序（英语：Bubble Sort）是一种简单的排序算法。它重复地走访过要排序的数列，一次比较两个元素，如果他们的顺序错误就把他们交换过来。走访数列的工作是重复地进行直到没有再需要交换，也就是说该数列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端。

![冒泡排序过程](http://img.blog.csdn.net/20160828111556305)

## 算法步骤

冒泡排序算法的运作如下：

- 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
- 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
- 针对所有的元素重复以上的步骤，除了最后一个。
- 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

伪代码如下：
```
function bubble_sort (array, length) {
    var i, j;
    for(i from 0 to length-1){
        for(j from 0 to length-1-i){
            if (array[j] > array[j+1])
                swap(array[j], array[j+1])
        }
    }
}
```

## 代码实现（java）

``` java
/**
 *
 * @Title: bubbleSort
 * @Description: 冒泡排序的简单实现
 *
 *               支持泛型
 * @param: @param <E>
 * @param: @param comparable
 * @return: void
 * @throws
 */
public static <E extends Comparable<? super E>> void bubbleSort(
            E[] comparable)
{
    boolean changed = false;
    do {
        changed = false;
        for (int a = 0; a < comparable.length - 1; a++) {
            if (comparable[a].compareTo(comparable[a + 1]) > 0) {
                E tmp = comparable[a];
                comparable[a] = comparable[a + 1];
                comparable[a + 1] = tmp;
                changed = true;
            }
        }
    } while (changed);
}
```

## 参考文章

- [排序算法](https://wikipedia.org/wiki/%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95#.E7.A9.A9.E5.AE.9A.E7.9A.84.E6.8E.92.E5.BA.8F)
- [冒泡排序](https://wikipedia.org/wiki/%E5%86%92%E6%B3%A1%E6%8E%92%E5%BA%8F#JAVA)
