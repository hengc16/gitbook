# check if Binary tree is Symmetric

Given a binary tree, check whether it is a mirror of itself \(ie, symmetric around its center\).

For example, this binary tree `[1,2,2,3,4,4,3]` is symmetric:

```text
    1
   / \
  2   2
 / \ / \
3  4 4  3
```

But the following `[1,2,2,null,3,null,3]` is not:

```text
    1
   / \
  2   2
   \   \
   3    3
```

**Follow up:** Solve it both recursively and iteratively.

### 思路:

* 将tree从root 分开， compare 左子树和右子树是不是symmetric
* compare可以分3步
  * 如果root1 和root2 都为null， return true
  * else if  root1 或 root2 其中一个为空， return false
  * else if  root1的值root2的值不同， return false
* recursively 对 root1.left 和root2.right 做对比
* recursively 对root1.right和root2.left 做对比

```java
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root == null) return true;
        return helper(root.left, root.right);
    }
    private boolean helper(TreeNode root1, TreeNode root2) {
        if(root1 == null && root2 == null) {
            return true;
        }else if(root1 == null || root2 == null) {
            return false;
        }else if(root1.val != root2.val) {
            return false;
        }
        return helper(root1.left, root2.right) && helper(root1.right, root2.left);
    }
}
```

