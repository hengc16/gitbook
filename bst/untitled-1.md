# 213. Reconstruct Binary Tree With Preorder And Inorder

### Description:

Given the preorder and inorder traversal sequence of a binary tree, reconstruct the original tree.

**Assumptions**

* The given sequences are not null and they have the same length
* There are no duplicate keys in the binary tree

**Examples**

preorder traversal = {5, 3, 1, 4, 8, 11}

inorder traversal = {1, 3, 4, 5, 8, 11}

the corresponding binary tree is

        5

      /    \

    3        8

  /   \        \

1      4        11

### 解法：

pre-process 把inorder的值和index 放到map里。

 每层通过preorder的开头找root， 在map里找root在inorder array里的index，把inorder在root index 分成 左右子树。在根据root index 前面element的个数，从pre-order往后数相同个，划分为pre-order的左子树。

### 时间复杂度：

时间: O\(n\)

空间: O\(n\)

### Code：

```java
public class Solution {
  public TreeNode reconstruct(int[] inOrder, int[] preOrder) {
    // Write your solution here
    Map<Integer, Integer> inMap = new HashMap<>();
    for(int i = 0; i < inOrder.length; i++) {
     inMap.put(inOrder[i], i); 
    }
    return helper(preOrder, inMap, 0, inOrder.length - 1, 0, preOrder.length - 1);
  }
  private TreeNode helper(int[]pre, Map<Integer,Integer> inMap, int inLeft, int inRight, int preLeft, int preRight) {
    if(inLeft > inRight) {
      return null;
    }
    TreeNode root = new TreeNode(pre[preLeft]);
    int leftSize = inMap.get(root.key) - inLeft;
    // preLeft + 1 是 pre order 第一个数为root， 左子树的范围从root后一个开始
    // preLeft + leftSize 是指pre order的左子树终止在 起点 + leftSize 是指inorder左子树的node的个数。
    root.left = helper(pre, inMap, inLeft, inLeft + leftSize - 1, preLeft + 1, preLeft + leftSize);
    // preLeft + leftSize 是左子树的终点， 那他的右子树的起点 就在左子树终点后一位。
    root.right = helper(pre, inMap, inLeft + leftSize + 1, inRight, preLeft + leftSize + 1, preRight);
    return root;
  }
}
/*
  pre-process 把inorder的值和index 放到map里
  每层通过preorder的开头找root，  在map里找root在inorder array里的index，把inorder在root index 分成
  左右子树。在根据root index 前面element的个数，从pre-order往后数相同个，划分为pre-order的左子树。
*/

```

