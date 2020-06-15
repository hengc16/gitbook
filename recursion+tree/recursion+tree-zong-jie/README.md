# Recursion+Tree总结

### 1. 第一类问题： bottom-up 从下往上返（三部曲）

* 三部曲方法去解决：

  1. 问左右孩子要什么
  2. 当前层做什么
  3. 返回给你parent什么

### 2.第2类问题： top-down  直上直下路径（比三部曲更为简单）

一般都是从上往下的一条直上直下路径， 有可能是complete path ，也有可能是sub-path。

key-point： carry a 直上直下path prefix while traversing the tree

原始方法：

preorder traverse 带个path -prefix（list of integer）， 加上dfs 吃吐。

优化方法：

prefix可以根据具体要求做更改。 如当前路径的合，只需要存一个prefix-sum instead of list of integer。



