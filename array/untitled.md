# 116. Array Deduplication II



Given a **sorted** integer array, remove duplicate elements. For each group of elements with the same value keep at most two of them. Do this in-place, using the left side of the original array and maintain the relative order of the elements of the array. Return the array after deduplication.

**Assumptions**

* The given array is not null

**Examples**

* {1, 2, 2, 3, 3, 3} → {1, 2, 2, 3, 3}

### 题意：

给你一个sorted array， 让你去重。标准时，如果有element出现次数超过2次，给他把超出的element删了。

### 思路：

2pointer同向而行，s, f指针。

s指针代表，从【0，s）不包括s，都为整理好的result

f代表当前index，【f，n-1】为未知区间

1 2 2 3 3 3 

                 l

                    f

因为是sorted， 所以如果a\[f\] == a\[s -2\]  那 a\[f\] == a\[s-1\]  

如果a\[f\] != a\[s-2\], 说明遇到了不重复的， a\[s++\] = a\[f\]

 

```java
/*

1 2 2 3 3 3
        s
        f 
11 22 33 每个数最多保留2个副本。
initialize:
在满足物理意义的情况下 initialize s = 2, f = 2;
拿f和s-2 做对比。 保证当前s 与s-2 不同时 才能s++

two cases 
case 1: A[f] == A[s - 2] its group of same number dont copy 
case 2: A[f] != A[s - 2]   its the correct case, s++ 
物理意义：
[0 to slow) result to return
[slow to fast] processed so far
[fast + 1 to n - 1] unexplored region
*/
public class Solution {
  public int[] dedup(int[] array) {
    // Write your solution here
    if(array.length <= 2) return array; 
    int slow = 2;
    for(int fast = 2; fast < array.length; fast++ ) {
      if(array[fast] != array[slow - 2]) {
        array[slow++] = array[fast];
      }
    }
    return Arrays.copyOfRange(array, 0, slow);
  }
}

```

### follow up

如果把保留2个副本改成保留k个副本呢

```java
public class Solution {
  public int[] dedup(int[] array, int k) {
    // Write your solution here
    if(array.length <= k) return array; 
    int slow = k;
    for(int fast = k; fast < array.length; fast++ ) {
      if(array[fast] != array[slow - k]) {
        array[slow++] = array[fast];
      }
    }
    return Arrays.copyOfRange(array, 0, slow);
  }
}
```

