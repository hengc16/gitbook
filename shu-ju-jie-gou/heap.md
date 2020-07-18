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
* percolate：
  * 如图，我们需要move 14 down
  * 跟左右孩子比较，把smallest和自己swap。

![](../.gitbook/assets/image%20%2830%29.png)

```java
package com.heng.datastructure;


public class minHeapDemo {
    private int[] array;
    private int size;
    //constructor
    public minHeapDemo(int size) {
        if (size <= 0) {
            throw new IllegalArgumentException("input array cannot be empty");
        }
        array = new int[size];
        this.size = 0;
    }
    //constructor
    public minHeapDemo(int[] input) {
        if (input == null || input.length == 0) {
            throw new IllegalArgumentException("input array cannot be null or empty.");
        }
        array = input;
        size = array.length;
        heapify();
    }

    // 从最后一个non-leaf node 开始，做percolate down
    private void heapify() {
        for (int i = (size - 1 - 1) / 2; i >= 0; i--) {
            percolateDown(i);
        }
    }

    private void percolateUp(int i) {
        //跟自己的parent比较，如果比自己parent小就上去。
        while (i > 0) {
            int parentIndex = (i - 1) / 2;
            if (array[i] < array[parentIndex]) {
                swap(i, parentIndex);
            }else {
                break;
            }
            i = parentIndex;
        }
    }

    private void percolateDown(int i) {
        while (i <= (size - 1 - 1) / 2) {
            int l = i * 2 + 1;
            int r = i * 2 + 2;
            //默认换左孩子，因为non-leaf node肯定有左孩子。
            int swapCandidate = l;
            //如果右孩子存在，并且比左孩子小，切candidate为右孩子
            if (r <= size - 1 && array[r] <= array[l]) {
                swapCandidate = r;
            }
            //swap 和candidate only if candidate比自己小
            if (array[swapCandidate] < array[i]) {
                swap(i, swapCandidate);
            } else { //不用往下找了，就这了
                break;
            }
            i = swapCandidate;
        }
    }

    private void swap(int i, int swapCandidate) {
        int temp = array[i];
        array[i] = array[swapCandidate];
        array[swapCandidate] = temp;
    }

    //-----------------------------
    // 对外API

    // offer 会自动扩容，尾部加ele，percolate up。
    public void offer(int ele) {
        //如果array已经满了，自动扩容2 倍。
        if (size == array.length) {
            int[] newArray = new int[size * 2];
            newArray = array.clone();
            array = newArray;
        }
        array[size] = ele;
        size++;
        percolateUp(size - 1);
    }

    //peek
    public int peek() {
        if (size == 0) {
            throw new IllegalArgumentException("heap is empty");
        }
        return array[0];
    }

    //update
    public void update(int index, int ele) {
        if (index < 0 || index >= array.length) {
            throw new IllegalArgumentException("invalid index range");
        }
        int oldKey = array[index];
        array[index] = ele;
        //如果新的比旧的小，需要往上move
        if (oldKey > ele) {
            percolateUp(index);
        } else { //如果新的比旧的大，需要往下走
            percolateDown(index);
        }
    }

    // poll
    // 拿最上面的值，把尾部的值补到头部，再做percolatedown。 size--
    public int poll() {
        if(size == 0) {
            throw new IllegalArgumentException("heap is empty");
        }
        int output = array[0];
        array[0] = array[size - 1];
        size--;
        percolateDown(0);
        return output;
    }
    //isEmpty
    public boolean isEmpty(){
        return size == 0;
    }

    public void print() {
        if(size == 0){
            throw new IllegalArgumentException("heap is empty");
        }
        for(int i = 0; i < size; i++){
            System.out.println(array[i]);
        }
    }


    public static void main(String[] args) {
        minHeapDemo minheap = new minHeapDemo(5);
        int [] array1 = new int[] {2,3,4,6,5,3,2,1};
        minHeapDemo minheap2 = new minHeapDemo(array1);
        minheap2.print();
        System.out.println();
        for(int i = 0; i < array1.length; i++){
            System.out.println(minheap2.poll());
        }

    }
}

```

