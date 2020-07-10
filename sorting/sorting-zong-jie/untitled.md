# bubble sort

冒泡排序：

* 2个指针，如果不是升序，swap。
* 一共进行n-1 次循环，每层确定最后一个element的位置
* 如果发现在某一层iteration，我们没有进行swap，可以提前结束，说明这个array已经是升序的了。

```java

for(int i = 0; i < array.length - 1; i++){
    boolean flag = flase;
    for(int j = 0; j < array.length - 1 - i; j++){
        if(array[j] > array[j+1]){
            int temp = array[j];
            array[j] = array[j+1];
            array[j + 1] = temp;
            flag = true;
        }
    }
    if(!flag) break;
}
```

