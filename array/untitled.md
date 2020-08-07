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



