# shell sort

是insertion sort的升级版。在做insertion sort前，先对数组进行整理。

![](../../.gitbook/assets/image%20%2821%29.png)

### 方法\#1 交换法。

* 3个for loop
  * 最外层循环log\_2 n 次， 每次gap /2
  * 中间层loop 对n - gap 组元素进行处理 
  * 最里层，compare相隔gap值得2个数，并进行swap 来保证相对顺序。
* 当gap为0的时候，说明我们已经sort好了这个数组。

### 方法\#2 移位法

* 3个loop
  * 最外层循环log\_2 n 次， 每次gap /2
  * 中间层loop 对n - gap 组元素进行处理 
  * 最里层，compare相隔gap值得2个数，做insertion sort

```java
public class ShellSort {
    public void sort(int[] array){
        for(int  gap = array.length / 2; gap > 0;  gap /= 2){
            for(int i = gap; i < array.length; i++){
                int j = i;
                int temp = array[j];
                if(array[j] < array[j-gap]){
                    while(j - gap >= 0 && temp < array[j - gap]) {
                        array[j] = array[j - gap];
                        j-= gap;
                    }
                    array[j] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        ShellSort test1 = new ShellSort();
        int[] sample = new int[]{4,2,11,3,8,-1};
        test1.sort(sample);
        System.out.println(Arrays.toString(sample));
    }
}
```

