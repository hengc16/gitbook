# DFS 总结

### DFS 基本方法：

1. Recursion tree 有多少层， 每层干什么。
2. Recursion tree 分多少叉， 对于每个状态要动态变化吗（如coins问题）
3. 注意做dfs时，吃吐守恒。

### BFS vs DFS:

因为都是树的traverse，正确性上是都可行的。

问题就出现在了空间上，DFS的空间是一条直上直下的路径。而BFS的queue size最高可以是recursion tree上最后一层的值。因为recursion tree每层的node 可以是grow exponentially的。

### backtracking:

* 是一种算法，来找出所有的解（或一部分解）， 属于brute force的一种
* 用来解决constraint satisfaction problems（如 8皇后，图着色，数独，填字）
* 方法强调
  * 1.incrementally builds candidates -&gt; 逐步构造
  * 2. abandons a candidate\('backtracks'\) as soon as it determines that the candidate cannot possibly be completed -&gt; 剪枝
* 跟brute force不同在于，backtracking强调剪枝。
* 
### sub-set 问题：

subset 是

![](../../.gitbook/assets/image%20%285%29.png)

1. **找出所有subset**
   1. 每层加与不加，找出所有可能性
2. **在一串数组中 找出符合条件的某一组subset或所有符合条件的subset**
   1. 每层check是否符合条件。
3. **All possible combinations of K element**
   1. 在termination上做改动。

### Parenthesis problems:

![](../../.gitbook/assets/image%20%282%29.png)

1. 打印所有possible permutation of given parenthesis。 

   1. 有多少个 parenthesis 就有多少层
   2. 每层分 所有种类的parenthesis \* 2 个叉。 乘以2是因为每种括号分左右括号。

### Coins:

![](../../.gitbook/assets/image%20%2816%29.png)

1. 给你一个number，问用着4种coins有多少种方法可以拼出这个number

   1. 这里每层分的叉是dynamically change的

### Permutation：

* 首先是permutation 和combination 有什么不同：

  * permutation的长度固定，顺序决定结果。如abc 的permutation为 abc，acb, bac, bca, cab, cba.
    * 如果给4个人颁发4个奖牌，每个奖牌代表意义不同，那总共的可能性为4\*3\*2\*1
    * 如果给4个人颁发2个奖牌，那就是4！/ 2! = 4 \* 3= 7 种颁发方式。
    * 那如果我们有n个人k个奖牌， 那可能性就是n! / \(n-k\)! 
  * combination结果长度不固定，并且顺序无所谓。如abc里bc 和cb 没有本质上区别，都是由b和c组成的长度为2的组合。

    * 如果给4个人颁发4个可乐，每个可乐都一样，那他只有一种颁发方式。
    * 如果给4个人颁发2个可乐，那就是4！/ \(2! \* \(4-2\)!\) = 6种颁发方式
    * 如果有n个人，和k个可乐， 那就是 n! / \(k! \* \(n-k\)!\) .

 

![](../../.gitbook/assets/image%20%2810%29.png)

这里每一层里 从 【0 当前层\)的element都已经确定了。  不确定的是【当前层 到n-1】的剩余位置。

这里的output 是于每个元素的顺序有关， 所以用swap。 

