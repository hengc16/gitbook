# Heap Sort

### 介绍

* 背后是一个由complete tree转换来的array
  * i 的左子树index为 2i + 1
  * 右子树为 2i + 2 
  * parent为（i-1） / 2
* 将input 转为heap， 如果是升序就用maxHeap， 如果是降序就用minHeap。
* 以升序为例：
  * 将input转为maxHeap的array
  * 此时maxHeap的top是最大值， 将它与array的最后一个元素swap
  * array\[n-1\]位置的元素确定了
  * 重新repeat上述，解决【0， n-i】的问题





