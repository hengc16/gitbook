# 34. Reverse Linked List



Reverse a singly-linked list iteratively.

**Examples**

* L = null, return null
* L = 1 -&gt; null, return 1 -&gt; null
* L = 1 -&gt; 2 -&gt; 3 -&gt; null, return 3 -&gt; 2 -&gt; 1 -&gt; null



### 解法\#iterative

```java
public class Solution {
  public ListNode reverse(ListNode head) {
    // Write your solution here
    //prev
    ListNode prev = null;
    //use head as iterative pointer
    while(head != null) {
      //save head.next for future use
      ListNode next = head.next;
      //let head point backwards 
      head.next = prev; 
      //iterate the prev and cur forward once 
      prev = head;
      head = next;
    }
    //the while loop stop when head == null, so prev is the last element is the list is not empty;
    return prev;
  }
}
```

### 解法\#recursive

```java
public class Solution {
  public ListNode reverse(ListNode head) {
    // Write your solution here
    if(head == null){
      return null;
    }
    //返回最后一个node
    if(head.next == null) {
      return head;
    }
    //拿到最后一个node
    ListNode last = reverse(head.next);
    //拿到后，开始反转
    //head -> last -> head.   
    head.next.next = head;
   // last->head->null;
    head.next = null;
    return last;

  }
}
```

