# 介绍

* 线性表 -》局限于一个pre 和一个next
* tree =》 局限于只能有一个parent，也就是一对多的关系
* 当我们需要**多对多的关系**时，就需要用到**graph**

### 无向图

* 图中的node也可以被称为vertex，node和node之间的连接被称之为edge边。 

![](../.gitbook/assets/image%20%2835%29.png)

### 有向图

![](../.gitbook/assets/image%20%2832%29.png)

### 带权图\(weighted graph\)

![](../.gitbook/assets/image%20%2831%29.png)

### 图的表示方式：

* 用二维数组来表示：
  * n个node就开个n\*n的矩阵，1代表2点之间直接相连。

![](../.gitbook/assets/image%20%2833%29.png)

* 用邻接表来表示，用linkedlist

  * 因为矩阵是n x n的空间，有很多边是不存在的，会造成空间浪费。
  * 邻接表只关心存在的边，一共有n条linkedlist， 每个header对应图的每个vertex，链接后面的node即为与这个vertex相连的vertex。

![](../.gitbook/assets/image%20%2834%29.png)

