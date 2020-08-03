# Fibonacci

![](../../.gitbook/assets/image%20%2838%29.png)

* 一共有n层，每层分2叉，时间复杂度是2^n
* 但是在分的叉里有很多的重复计算
* 如果我们有个记事本，可以把所以我们计算过的值都记录下来
  * 如果遇到重复的值，我们不需要计算直接看记事本
  * 如果没遇到过，就计算，然后存到记事本

```java
public int fib (int n, HashMap<Integer,Integer> m) {
    if( n == 0 || n == 1) {
        return n;
    }
    if(m.containsKey(n)) {
        return m.get(n);
    }
    int res = fib(n - 1) + fib( n - 2);
    m.put(n,res);
    return res;
}
```

* 时间复杂度就被降到了O\(n\)
* 缺点： 这个space是O\(n\) 并且是开辟在call stack上的。如果n恨大， callstack 又很小，就会crash

### 用iteration：

* 开辟个长度为 n +1 的数组当memo
* 初始化好memo最小号问题的值
* linear scan 回头看小一号问题的解

```java
public int fib (int n) {
    int[] m = new int[n+1];
    m[0] = 0;
    m[1] = 1;
    for(int i = 2; i <= n; i++) {
        m[i] = m[i-1] + m[i-2];
    }
    return m[n];
}
```



