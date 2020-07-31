# factor combination

Given an integer number, return all possible combinations of the factors that can multiply to the target number.

Example

Give A = 24

since 24 = 2 x 2 x 2 x 3

              = 2 x 2 x 6

              = 2 x 3 x 4

              = 2 x 12

              = 3 x 8

              = 4 x 6

your solution should return

{ { 2, 2, 2, 3 }, { 2, 2, 6 }, { 2, 3, 4 }, { 2, 12 }, { 3, 8 }, { 4, 6 } }

note: duplicate combination is not allowed.

### 题意:

input是一个数字

output a list of这个数字所以乘积的**组合**，相乘可以得到这个数

### 思路：

all possible combination of factors

* 12 = \[a2 , b3, c4, d6\] 
* 2,3,4,6 为12 的factor
*  a,b,c,d 为 factor的的使用次数 
* 用coins combination的思想， 
* 先做个pre-process拿到所以factor
* 每层选一个factor 
* 循环factor对应的使用次数 对其进行递归调用
* 树高为factor的数量（log n）因为worst case 也是一直除以2 
* 每层分n/ factor 个叉

```java
public class Solution {
  public List<List<Integer>> combinations(int target) {
    // Write your solution here
    List<List<Integer>> res = new ArrayList<>();
    if( target == 1) return res;
    List<Integer> path = new ArrayList<>();
    List<Integer> factors = getFactors(target);
    helper(0, target, path, factors, res);
    return res;
  }
  private void helper(int index, int target, List<Integer> path, List<Integer> factors, List<List<Integer>> res){
    if(index == factors.size()) {
      if(target == 1) {
        res.add(new ArrayList<Integer> (path));
      }
      return;
    }
    //current level
    //get the current level factor
    int cur = factors.get(index);
    for(int i = cur;  target % i == 0; i *= cur) {
      path.add(cur);
      helper(index + 1, target/i, path, factors, res);
    }
    for(int i = cur; target % i == 0; i *= cur) {
      path.remove(path.size() - 1);
    }

    helper(index + 1, target, path, factors, res);
  }
  private List<Integer> getFactors(int n) {
    List<Integer> res = new ArrayList<>();
    for(int i = 2; i < n; i++) {
      if(n % i == 0) {
        res.add(i);
      }
    }
    return res;
  }

}
```

