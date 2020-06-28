# Binary Tree Layer By Layer Zig-Zag Order

Get the list of keys in a given binary tree layer by layer in zig-zag order.

**Examples**

        5

      /    \

    3        8

  /   \        \

 1     4        11

the result is \[5, 3, 8, 11, 4, 1\]

**Corner Cases**

* What if the binary tree is null? Return an empty list in this case.

**How is the binary tree represented?**

We use the level order traversal sequence with a special symbol "\#" denoting the null node.

### 思路

 0   &lt;-------               5 

1   ---------&gt;          3     8

 2  &lt;---------       1   4      11

3  -------------&gt;      7              9

output:          5 3 8 11 4 1 

even number traverse from right to left

odd number goes from left to right . 

we can do level order traverse, for each level, we can check whether its odd or even:

 if even: 

         we read the node from right to left 

if odd: 

          we read from left to right.

data structure:

instead of using queue for level order traverse, we can use deque to be able to read the queue from both end.

我们确定了每行读取得顺序， even从右往左读， odd从左往右读。 那我们就要确保我们每次的deque要和tree的从左到右的顺序一样，这样读才有意义。

如图，somehow我们能保证我们每层的deque跟图上的每层顺序和数量一样，我们只需要通过判断当前层是不是even 来定义我们从头还是从尾读这一层。

读的操作，就相当于我们expand 步骤在bfs里，

那expand后我们的generation需要如何定义。

我们要保证我们generate出来的node 在deque的顺序和图上的一样。并且还要和expand不冲突。

为什么会冲突，如果我们当前层expand（读）是pollLast（）拿最尾部，那我们generate就不能从尾部插入，因为如果offerLast了，下一次expand就会是刚插入的这个node，就变成stack了。 

当在even层时，我们是从右往左读的\(pollLast\)，generate左右子node时，要offerFirst\(\), 如果是正常的先做后右，右节点在下一层就会在左节点前面， 拿5举例子， offerfirst 左孩子， offerfirst右孩子， 结束当前层， 那到下一层，你的deque就会是 8 3。 



### code：

```java
public class Solution {
  public List<Integer> zigZag(TreeNode root) {
    // Write your solution here
    List<Integer> res = new ArrayList<>();
    if(root == null){
      return res;
    }
    Deque<TreeNode> deque = new LinkedList<>();
    deque.offerFirst(root);
    boolean isEven = true;
    while(!deque.isEmpty()){
      int size = deque.size();
      for(int i = 0; i < size; i++){
        if(isEven){
          TreeNode cur = deque.pollLast();
          res.add(cur.key);
          if(cur.right != null){
            deque.offerFirst(cur.right);
          }
          if(cur.left != null){
            deque.offerFirst(cur.left);
          }
        }else{
          TreeNode cur = deque.pollFirst();
          res.add(cur.key);
          if(cur.left != null){
            deque.offerLast(cur.left);
          }
          if(cur.right != null){
            deque.offerLast(cur.right);
          }
        }
      }
      isEven = !isEven;
    }
    return res;
  }
}
```



