## LeetCode - Intersection Of Two Linked Lists
Given the heads of two singly linked-lists headA and headB, return the node at which the two lists intersect. If the two linked lists have no intersection at all, return null.

For example, the following two linked lists begin to intersect at node c1:


It is guaranteed that there are no cycles anywhere in the entire linked structure.

Note that the linked lists must retain their original structure after the function returns.

 

### Example 1:
```
ListA:      4 -> 1 
                   \
                     8 -> 4 -> 5
                   /
ListB: 5 -> 6 -> 1
```
**Input:** intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3

**Output:** Intersected at '8'

**Explanation:** The intersected node's value is 8 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,6,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.

#### Example 2:
```
List A: 2 -> 6 -> 4
List B: 1 -> 5
```
**Input:** intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2

**Output:** No intersection

**Explanation:** From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. Since the two lists do not intersect, intersectVal must be 0, while skipA and skipB can be arbitrary values.
The two lists do not intersect, so return null.
 

### Constraints:

<li> The number of nodes of `listA` is in the m.
<li> The number of nodes of `listB` is in the n.
<li> 0 <= m, n <= 3 * 104
<li> 1 <= `Node.val` <= 105
<li> 0 <= skipA <= m
<li> 0 <= skipB <= n
<li> intersectVal is 0 if `listA` and `listB` do not intersect.
<li> intersectVal == listA[skipA + 1] == listB[skipB + 1] if listA and listB intersect.
 

Follow up: Could you write a solution that runs in O(n) time and use only O(1) memory?
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null)
          return null;
        
        HashMap<ListNode, String> mapOfListNode = new HashMap<>();
        while(headA!=null && headB!=null){
          if(mapOfListNode.containsKey(headA)){
            return headA;
          } else {
            mapOfListNode.put(headA, "A");
          }
          if(mapOfListNode.containsKey(headB)) {
            return headB;
          } else {
            mapOfListNode.put(headB, "B");
          }
          headA = headA.next;
          headB = headB.next;
       }
       while(headA!=null){
          if(mapOfListNode.containsKey(headA)){
            return headA;
          } else {
            mapOfListNode.put(headA, "A");
          }
          headA = headA.next;
       }
       while(headB!=null){
          if(mapOfListNode.containsKey(headB)){
            return headB;
          } else {
            mapOfListNode.put(headB, "B");
          }
          headB = headB.next;
       }
       
       return null;
    }
}
```
