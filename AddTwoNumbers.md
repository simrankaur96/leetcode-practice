## LeetCode - Add Two Numbers
You are given 2 non-empty linked lists representing non-negative integers.
The digits are stored in reverse order, and each of their nodes contains a single digit. 
Add the two numbers and return the sum as a linked list.
You may assume the two numbers do not contain any leading zero, except the number 0 itself.

### Example
2 -> 4 -> 3

5 -> 6 -> 4
___________
7 -> 0 -> 8

**input**: l1 = [2,4,3], l2 = [5,6,4]

**output**: [7,0,8]

**Explanation**: 342 + 453 = 807

### Constraints
<li> The number of nodes in each linked list is in the range [1, 100]. </li>
<li> 0 <= Node.val <= 9 </li>
<li> It is guaranteed that the list represents a number that does not have leading zeros. </li>

### Code
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode sum = new ListNode(0);
        ListNode head = sum;
        int remainder = 0;
        while(l1!=null && l2!=null){
          sum.next = new ListNode(remainder);
          sum = sum.next;
          sum.val += (l1.val + l2.val); 
          remainder = sum.val/10; //final value in remainder = (l1.val + l2.val + remainder)/10;
          sum.val %=10; // final value in sum.val = (l1.val + l2.val + remainder)%10;
          l1 = l1.next;
          l2 = l2.next;          
        }
        while(l1!=null){
          sum.next = new ListNode(remainder);
          sum = sum.next;
          sum.val += l1.val;
          remainder = sum.val/10;
          sum.val %= 10;
          l1 = l1.next;
        }
        while(l2!=null){
          sum.next = new ListNode(remainder);
          sum = sum.next;
          sum.val += l2.val;
          remainder = sum.val/10;
          sum.val %= 10;
          l2 = l2.next;
        }
        if(remainder > 0){ // in case there is any carry over left.
          sum.next = new ListNode(remainder);
        }
        return head.next;
    }
}
```
