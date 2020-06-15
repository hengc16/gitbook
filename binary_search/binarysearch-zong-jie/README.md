# BinarySearch 总结

1. we must guarantee that the search space decreases over time\(after each iteration \)
2. we must guarantee that the target\(if exists\) cannot be ruled out accidentally, when we change the value of the left or right. 

### 题型track：

**中心开花：**

* 如kth closest, 我们先找到最近的2个element 在从那向外延伸 找k closest。

**sorted 2D matrix**

* 通过 row = index / col  和 col= index % col  来 access matrix【row, col】的element。

**shift sorted array**

* 3 4 5 1 2
* 每次取mid， 如果left &lt;= mid , 如mid 为5， left 为3。 说明【left, mid】为sorted区间。可以做binary search
* 5 1 2 3 4 
* 如果left&gt; mid， 如果left &gt; mid, 如mid 为2， left 为5， 则说明\[mid, right\] 为sorted区间。可以做binary search。



