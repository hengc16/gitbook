# insertion sort

基本思想：

* 把n个待排序的元素看成是一个有序表和一个无序表
* 开始时有序表只有一个元素，无序表中有n-1个元素
* 排序过程中，每次从无序表里拿一个出来，将它插入到有序表中。

|  | 3 | 25 | 14 | 20 | 9 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 第一轮 | 3 | 25 | 14 | 20 | 9 |
| 第二轮 | 3 | 14 | 25 | 20 | 9 |
| 第三轮 | 3 | 14 | 20 | 25 | 9 |
| 第四轮 | 3 | 9 | 14 | 20 | 25 |

* \[0,i\) 为有序数列
* \[i, n-1\] 为无序数列
* 先存array\[i\]
* 将array\[i\]与array\[prev\]做比较， prev为i-1
  * 如果array\[i\] &lt; array\[prev\]， 将array\[prev\]的值后移，同时prev指向再前一个元素。
  * 如果array\[i\] &gt; array\[prev\]，说明找到位置了，
* 将array\[i\]插入到 prev+1 的位置

```java
public class InsertionSort {
    public void sort(int[] input){
        for(int i = 1; i < input.length;i++){
            int insertValue = input[i];
            int insertIndex = i - 1;
            while(insertIndex >= 0 && insertValue < input[insertIndex]){
                input[insertIndex + 1] = input[insertIndex];
                insertIndex--;
            }
            input[insertIndex + 1] = insertValue;
        }
    }
    public static void main(String[] args) {
        InsertionSort test1 = new InsertionSort();
        int[] sample = new int[]{4,2,11,3,8,-1};
        test1.sort(sample);
        System.out.println(Arrays.toString(sample));
    }
}
```

