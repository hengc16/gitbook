# Segment Tree

* 是binary tree，每个节点有2个子节点
* 是balance的，log n 的高度
* leaf里的值为array的值
* 下面0-0代表了range， 如图，这里做的是sum，3取自array index 0 到 1 这个range。
* 操作
  * build\( start, end, array\) o\(n\)
  * update \(index, value\) O\(logn\)
  * rangeQuery\(start, end\)  O\(logn + k\)   k -&gt; the number of reported segments

![](../.gitbook/assets/image%20%2847%29.png)

```java
build  像是创一个bst

struct SegmentTreeNode {
    int start;
    int end;
    int sum;   // can be max, min ,etc  depends on the question
    SegmentTreeNode left;
    SegmentTreeNode right;
}
public SegmentTreeNode build (int start, int end, int[] array) {
    if(start == end) {
        return new SegmentTreeNode(start, end, array[start];
    }
    int mid = start + (end - start) / 2;
    SegmentTreeNode left = build(start, mid, array);
    SegmentTreeNode right =  build(mid + 1, end, array);
    
    return new SegmentTreeNode(start, end, left.sum + right.sum, left, right);
         
}
//时间复杂度：O(n)

public void update(SegemenTreeNode root, int index, int val) {
    if(root.start == root.end == index){
        root.sum = val;
        return;
    }
    int mid = root.start + (root.end - root.start) / 2;
    if(index < mid) {
        update(root.left, index, val);
    }else{
        update(root.right, index, val);
    }
    root.sum = root.left.sum + root.right.sum;
}
//找到相应index，更新，并更新它的所以parent的sum
//时间复杂度是log(n)的。 

//method 求querySum 给你一个i到j的区间，求sum
public int querySum(SegementTreeNode root, int i, int j){
    if(root.left == i & root.right == j) {
    return root.sum;
    }
    int mid = root.left + (root.right - root.left) / 2;
    if( j <= mid ) {
       // 全部在我的左子树，
        return querySum(root.left, i, j);
    }else if ( i > mid) {
        //全部在我的右子树
        return querySum(root.right, i, j);
    }else{
        //当这个区间一部分在我的左子树，一部分在我的右子树。
        return querySum(root.left, i, mid) + querySum(root.right, mid + 1, j);
    }
}
//时间复杂度： Log(n) + k;  k是一共访问的node数量；
```

