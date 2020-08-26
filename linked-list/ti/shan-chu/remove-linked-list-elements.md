# remove linked list elements

{% embed url="https://leetcode.com/problems/remove-linked-list-elements" %}

### 题意：

* 删除所有的值为target的node

### 思路：

* 如果cur = target， 让pre.next指向cur的next

```java
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        if(head == null) return null;
        ListNode dummy = new ListNode(0);
        dummy.next = head;
        ListNode cur = dummy.next;
        ListNode pre = dummy;
        while(cur != null) {
            if(cur.val == val){
                pre.next = cur.next;   
            }else{
                pre = pre.next;
            }
            cur = cur.next;
        }
        return dummy.next;
    }
}
```

* 也可以只用一个pointer

```java
public ListNode removeElements(ListNode head, int val) {
    if (head == null) return head;
    ListNode dummy = new ListNode(0);
    dummy.next = head;
    head = dummy;
    while (head.next != null) {
        if (head.next.val == val) {
            head.next = head.next.next;
        } else {
            head = head.next;
        }
    }
    return dummy.next;
}
```

