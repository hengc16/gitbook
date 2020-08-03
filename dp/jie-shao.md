# 介绍

-optimization : recursion + memoization 

* 思想就是拿空间换时间，拿个小本子把重复计算的记下来。

![](../.gitbook/assets/image%20%2837%29.png)

### 常见题：

一维**：**

* 一维的original data\(such as a rope, a word\)  求max/min （cut，merge，etc）
  * if the weight of each smallest element int the original data is identical/similar 
    * identical: 1 meter of rope 
    * similar: a letter, a number 
* 解决这种问题的思路一般都是linear scan 回头看
  * longest ascending subarray \(在i的位置，看 i -1 的值\)
  * longest ascending subsequence \( 在i的位置， 看 1 到 i -1）
  * cut rope
  * cut palindrome 
  * etc
* 如果weight are not the same
  * 切木头问题
  * 解决方法 是 中心开花
* pizza问题， 两头凑

二维：



