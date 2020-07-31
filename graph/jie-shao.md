# 介绍

* 线性表 -》局限于一个pre 和一个next
* tree =》 局限于只能有一个parent，也就是一对多的关系
* tree是一种特殊的graph， v是点，边就是v-1条，并且无环。
  * O\(V+E\) ~~ O\(n\)
* 当我们需要**多对多的关系**时，就需要用到**graph**

### 无向图（undirected simple graph）

* 图中的node也可以被称为vertex，node和node之间的连接被称之为edge边。
* 不存在超过一条edge join 同一对vertices
  * 这样的edges被叫做 " multiple edges’ or “parallel edges”
* 不存在loop: 一条边的两端是相同的点
* undirected simple graph引申出
  * undirected multigraph 允许存在multi edges
  * undriected multigraph permitting loops 允许存在loops 和multi edges
  * undriected simple graph permitting loops 允许存在loops

![](../.gitbook/assets/image%20%2836%29.png)

### 有向图



![](../.gitbook/assets/image%20%2833%29.png)

### 带权图\(weighted graph or network\)

![](../.gitbook/assets/image%20%2831%29.png)

### 连通图：（connected graph）

* 虽然连通图并不像前面三个是一类图的的种类，但是也是非常重要的知识点
* 联通就是指两个点之间有一条path
* 在undirected connected graph里，every pair of nodes in graph is connected。每2个点之间都有一条path
* 在driected connected graph里
  * weakly -&gt; 换成undirected edge之后是connected
  * strongly -&gt; for every pair of vertices u, v, 即存在a directed path from u to v 也存在a directed path from  v to u. 

### 图的表示方式：

* 用二维数组来表示：
  * n个node就开个n\*n的矩阵，1代表2点之间直接相连。

![](../.gitbook/assets/image%20%2834%29.png)

* 用邻接表来表示，用linkedlist

  * 因为矩阵是n x n的空间，有很多边是不存在的，会造成空间浪费。
  * 邻接表只关心存在的边，一共有n条linkedlist， 每个header对应图的每个vertex，链接后面的node即为与这个vertex相连的vertex。

![](../.gitbook/assets/image%20%2835%29.png)

### 补充

在面试的时候，面试官很少会要求你的input具体是以什么方式实现的。 为了方便操作，我们可以assume这个图已经被转换好了。不要傻傻的用list of eadges 再手动转换成邻接链表或邻接矩阵



