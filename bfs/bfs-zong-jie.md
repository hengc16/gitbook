# BFS总结

BFS \#1 操作过程：

* Data Structure: Maintain a FIFO queue. put all traversed nodes that haven't been expanded into queue.
* **initial state**: where to start
* **Expand:** a node from the queue, do something
* **Generate:**  reach all its neighbors, and put it into the queue.
* **Termination**: when to terminate, usually when the queue is empty, or if we reaches kth node.
* **Deduplicate**: typically for graph, each node should only be expand and generated once. 

BFS \#2 操作过程：

* 一般用在找最短路径，点到面（所有点）的距离算法。
* 用到priority\_queue.
* 例题： find kth smallest element in a NxN matrix. col and row are sorted. 

