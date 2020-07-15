# QuickSort

### 介绍

* quicksort 是对冒泡排序的一种改进。
* 每次循环找个pivot
  * 把比pivot小的数放pivot左边
  * 把比pivot大的数放pivot右边
* 除了你能确定pivot的位置，你没法保证左右两端为sorted， 所以对左右2段做相同逻辑recursion调用

![](../../.gitbook/assets/image%20%2822%29.png)

* worst case can still occur if the input array is such that the maximum \(or minimum\) element is always chosen as pivot.

```java
package com.heng.code.sorting;

import java.util.Arrays;

public class QuickSortDemo {
    public void quickSort(int[] array){
        if(array == null) return;
        sort(array, 0, array.length - 1);
    }
    private void sort(int[] array, int left, int right){
        if(left >= right) return;
        int pivotIndex = partition(array, left, right);
        sort(array, left, pivotIndex);
        sort(array, pivotIndex + 1, right);
    }
    private int partition(int [] array, int left, int right){
        int pivotIndex = getPivot(left, right);
        swap(array, pivotIndex, right);
        int pivot = array[right];
        int l = left;
        int r = right - 1;
        while(l <= r){
            if(array[l] < pivot){
                l++;
            }else if (array[r] >= pivot){
                r--;
            }else{
                swap(array, l , r);
                l++;
                r--;
            }
        }
        swap(array,l, right);
        return l;
    }
    private int getPivot(int left, int right){
        return left + (int)(Math.random() * (right - left + 1));
    }
    private void swap (int[] array, int left, int right){
        int tmp = array[left];
        array[left] = array[right];
        array[right] = tmp;
    }
    public static void main(String[] args) {
        QuickSortDemo test1 = new QuickSortDemo();
        int[] sample = new int[]{4,2,2,2,2,11,3,2,8,-1};
        test1.quickSort(sample);
        System.out.println(Arrays.toString(sample));
    }
}

```

