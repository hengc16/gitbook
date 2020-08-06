# Dictionary Problem



Given a word and a dictionary, determine if it can be composed by concatenating words from the given dictionary.

**Assumptions**

* The given word is not null and is not empty
* The given dictionary is not null and is not empty and all the words in the dictionary are not null or empty

**Examples**

Dictionary: {“bob”, “cat”, “rob”}

* Word: “robob” return false
* Word: “robcatbob” return true since it can be composed by "rob", "cat", "bob"



### 题意：

给你一个dictionary，里面有一些单词。 

又给了你一个string， 问你可以不可以以把string 切成若干个pieces, 每个piece都是dic里的单词

### 思路：

这里要用到左大段+ 右小段的思想

左大段为历史上见过的问题， 右小段为要去字典里查的部分。

2个for 循环， 第一个负责从1 到n的iterate一遍

第2个负责回头看，尝试对每个点做切割，0到j为左大段，去memo里找。 j到i 为右小段，固定去字典里查。

如果左边拿到底是true 并且右小段也是true 我们就更新当前memo的值to true。 并且提前结束当前层。继续去下一个i。

当i走完了， 判断一下我们的memo里最后一个数是否为true。

```java
public class Solution {
  public boolean canBreak(String input, String[] dict) {
    // Write your solution here
    Set<String> dic = new HashSet<>();
    for(String word: dict) {
      dic.add(word);
    }
    boolean[] memo = new boolean[input.length() + 1];
    memo[0] = true;
    // i 为当前word的长度
    for(int i = 1; i <= input.length(); i++){
      //从一刀不切到 i-1 每段都切一刀, j=0代表一刀不切的情况。
      for(int j = 0; j < i; j++) {
        //左大段[0, j] 去看memo， 右小段[j,i]去查字典
        if(memo[j] && dic.contains(input.substring(j, i))) {
          //update memo
          memo[i] = true;
          break;  // 只要有一种切法可以符合条件就可以
        }
      }
    }
    return memo[input.length()];
  }
}

```

### 时间复杂度: 

这个implementation 是O\(n^3\)的。因为用到了java 里的substring api O\(n\)的。

space = O\(n\)

