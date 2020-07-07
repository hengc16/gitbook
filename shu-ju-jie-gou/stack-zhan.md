# stack（栈）

先进后出，后进西出。

### 应用场景：

1. 递归：
2. 表达式的转换和求值。
3. 树的遍历
4. dfs。

### Java deque的api \(use deque instead of stack\(legacy\)\)

* offerFirst
* pollFirst
* peekFirst
* size

### 用array来实现stack：

1. 定义一个top来表示栈顶，初始化为-1 
2. 入栈：当数据入栈时，判断是否栈满， stack\[++top\] = data。
3. 出栈： 判断是否为空，return stack\[top--\];

### 用stack去实现一个计算器：

1.   遍历input array
2. 如果是数字就放入栈中
3. 如果是符合， 
   1. 如果符号栈为空，直接加入
   2. 如果符号栈不为空，判断当前运算符是否比top运算符优先。
      1. **如果优先**，就直接入栈，因为还没有读到操作符后面的那个数字没办法现在运算。
      2. 如果不优先，就pop出top运算符，和2个数字进行运算，并将算好的放回去，然后将当前运算符再push进stack。
4. 遍历完，开始pop数字stack和符号栈，开始运算
5. 最后数字栈里只会有一个数字。 

