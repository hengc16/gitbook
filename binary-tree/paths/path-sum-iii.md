# Path Sum III

You are given a binary tree in which each node contains an integer value.

Find the number of paths that sum to a given value.

The path does not need to start or end at the root or a leaf, but it must go downwards \(traveling only from parent nodes to child nodes\).

The tree has no more than 1,000 nodes and the values are in the range -1,000,000 to 1,000,000.

**Example:**

```text
root = [10,5,-3,3,2,null,11,3,-2,null,1], sum = 8

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

Return 3. The paths that sum to 8 are:

1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
```

### 题意：

* 找出一共有多少条直上直下的一段path 的sum = target。这里path的起点可以不是root， 终点也可以不是leaf。

### 思路：

暴力解： 用dfs遍历整个tree，以每个点在做同样逻辑。 时间复杂度：O\(n^2\)

优化解： linear scan 这个tree， 带上prefixsum。 

* 用pre-fix sum 
  * prefix sum is a sum of the current value with all previous elements starting from the beginning of the structure.
  * 什么时候用prefix-sum： 
    * find a number of continuous subarrays / submatrices/ tree path that sum to target.

### 解法\#1

```java
class Solution {
    public int pathSum(TreeNode root, int sum) {
        if(root == null) return 0;
        return helper(root, sum) +
         pathSum(root.left, sum) + pathSum(root.right, sum);
    }
    private int helper(TreeNode root, int sum) {
        if(root == null) return 0;
        return (root.val == sum ? 1 : 0) +
         helper(root.left, sum - root.val) + helper(root.right, sum - root.val);
    }
}
```

### 解法\#2



```text

      10
     /  \
    5   -3
   / \    \
  3   2   11
 / \   \
3  -2   1

Return 3. The paths that sum to 8 are:

prefix sum = [0, 10, 15, 18, 21, 16, 17, 18, 
pfxSUm - T = [-8, 2,  7, 11, 13,  8,  9, 10,

1.  5 -> 3
2.  5 -> 2 -> 1
3. -3 -> 11
```



