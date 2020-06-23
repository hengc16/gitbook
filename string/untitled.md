# 3. Longest Substring Without Repeating Characters

### Description

 Given a string, find the length of the **longest sub string** without repeating characters.

[https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

\*\*\*\*[**https://app.laicode.io/app/problem/253**](https://app.laicode.io/app/problem/253)\*\*\*\*

**Example 1:**

```text
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
```

**Example 2:**

```text
Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```

**Example 3:**

```text
Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
Note that the answer must be a substring, "pwke" is a subsequence
and not a substring.
```

### Clarification:

Just want to confirm if my understanding is correct, if with input String "ab\_c\_d\_c", the output should be 4, since the longest sub string of this input is "ab\_c“; And also, what if the input is null, I will return -1 in this case. 

### Approach:

* algorithm: sliding window 
* data structure: HashMap, where key is the element, value is the element's index.
* High level: use hashmap as our sliding window container, \[i, j\). iterate the array, fill the window with the longest unrepeated substring.
* mid level: The semantic of \[i,j\)
  * we use i as the left boundary of the window. It records the beginning element of this substring.
  * we use j as the point to iterate the array, for all the elements from i to j - 1 should be unique
  * The reason to use hashmap is because when we face a repeated character\(j'\), we can use the Entry to find the index of first seen element in the hashmap\(j\),  if the index is within the current window, then shift the left bounder of the window to j + 1. 
* Time complexity: O\(n\) 
* Space complexity: O\(min\(m,n\)\)  n represents the array length, m represents the 26 alphabets. 

### Code:

```java
  public int longest(String input) {
    if(input == null || input.length() == 0) {
      return 0;
    }
    //key is the element, value is the index
    Map<Character, Integer> map = new HashMap<>();
    int i= 0;
    int j= 0;
    int max = 0;
    while(j < input.length()) {
      char c = input.charAt(j);
      //if we have seen this char before. 
      if(map.containsKey(c)){
        //the index of old element(j)'s index is with in this window.
        if(map.get(c) >= i) {
          i = map.get(c) + 1;
        }
      }
      //upadte the j' to the current map
      map.put(c, j);
      //update the max length if needed 
      max = Math.max(max, j - i + 1);
      //traverse to the next element
      j++;
    }
    return max;
  }
```





