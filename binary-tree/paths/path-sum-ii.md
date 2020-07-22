# Path Sum II

Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

**Note:** A leaf is a node with no children.

**Example:**

Given the below binary tree and `sum = 22`,

```text
      5
     / \
    4   8
   /   / \
  11  13  4
 /  \    / \
7    2  5   1
```

Return:

```text
[
   [5,4,11,2],
   [5,8,4,5]
]
```

### 思路：

* 用一个arraylist来当prefix path 来存当前path的node
  * 注意吃吐
* 触底为true， deep copy 当前prefix path 到res
* dfs 思想

```java
class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> res = new ArrayList<>();
        List<Integer> prefixPath = new ArrayList<>();
        if(root == null) return res;
        helper(res, prefixPath, root, sum);
        return res;
    }
    private void helper (List<List<Integer>> res, List<Integer> prefixPath, TreeNode root, int sum) {
        if(root == null) return; 
        if(root.left == null && root.right == null && root.val == sum) {
            prefixPath.add(root.val);
            res.add(new ArrayList<Integer>(prefixPath));
            prefixPath.remove(prefixPath.size() - 1);
        }
        //cur 
        prefixPath.add(root.val);
        helper(res, prefixPath, root.left, sum - root.val);
        helper(res, prefixPath, root.right, sum- root.val);
        prefixPath.remove(prefixPath.size() - 1);
    }
}
```

