# Bottom View Of Binary Tree





### 思路：

把这个树看成n个纵轴，每个纵轴由hd来代表，我们只要把每个hd的最下面的node的值保留下来就好了。

data structure： 

treeMap（key：hd； value: node值） 用treeMap来保证hd的从左到右的顺序。

queue&lt;TreeNode&gt; 拿来做level order traverse

queue&lt;Integer&gt; 用来存node 相对的hd。

利用level order traverse从上到下的特性， 只要map contains当前纵轴（hd），我们就更新它，因为我们只需要最bottom的node值。

### code:

```java
public class Solution {
  public List<Integer> borderView(TreeNode root) {
    // Write your solution here
    List<Integer> res = new ArrayList<>();
    if(root == null){
      return res;
    }
    Map<Integer, Integer> map = new TreeMap<>();
    Queue<TreeNode> q = new LinkedList<>();
    Queue<Integer> hdQ = new LinkedList<>();
    q.offer(root);
    hdQ.offer(0);
    while(!q.isEmpty()){
      TreeNode cur = q.poll();
      int hd = hdQ.poll();
      map.put(hd, cur.key);
      if(cur.left != null){
        q.offer(cur.left);
        hdQ.offer(hd - 1);
      }
      if(cur.right != null){
        q.offer(cur.right);
        hdQ.offer(hd + 1);
      }
    }
    for(Map.Entry<Integer,Integer> entry : map.entrySet()){
      res.add(entry.getValue());
    }
    return res;
  }
}
```

