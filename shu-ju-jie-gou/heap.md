# heap

### 介绍：

* 堆（heap）也被称为优先队列（priority queue\), 与queue不同的是，它分min heap和max heap。
  * 在min\_heap里，堆的最上面永远是这个堆里面最小的那个值。
  * 在max\_heap里，堆的最上面永远是这个堆里面最大的那个值
  * 并且每个分支也可以看做一个最小堆或最大堆
* 常见堆是由complete tree的方法来表示堆，因为可以方便用-array-来access堆里的节点。
  * 在array里，root的index为0。
  * 每个node的index和parent， and 它的 children都是有关系的， 如果node的index为i
    * 它的左孩子的index为 2i + 1
    * 它的右孩子的index为2i + 2 
    * 它的parent的index为 \(n-1\)/2
* 堆的时间复杂度
  * heapify一个数组是o\(n\)
  * 把n个element push 到heap里来sort是： O\(N log N\)
  * offer\(E e\) - O\(log n\)
  * peek\(\) : O\(1\)
  * poll\(\) : O\(log n\)
  * remove: O\(n\)  or O\(logn\) if with balanced BST  
  * size\(\) O\(1\)
  * isEmpty O\(1\)
* 主要method：
  * heapify\(\):  convert an array to a heap in O\(n\) time.
    * perform percolate Down from the last \(non-leaf\) node to the root. 
  * percolateUp\(\): 
    * when: when u offer new element to the heap, the element need to move up to maintain the heap property. 
    * how: compare with its parent\(n-1\)/2 , swap it if the cur &lt; parent.  \(min\_heap\) 
  * percolateDown\(\):
    * when: the element need to be moved down to maintain the heap property. When we poll an element from the heap.
    * how: compare the element with two children, if the if the smallest one among two children is smaller than parent, swap it. 

