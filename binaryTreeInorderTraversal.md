## LeetCode - Binary Tree Inorder traversal

Given the root of a binary tree, return the ignorer traversal of the nodes’ value

### Example

Tree:

   1
     \
      2
     /
   3

**Input:** [1, null, 2, 3]

**Output:** [1, 3, 2]

### Constraints

* The number of nodes in the tree is in the range [0, 100].
* -100 <= Node.val <= 100

```java
/**
* Inorder traversal is left -> root -> right
**/

/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */

class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
	List<Integer> inorderTraversal = new ArrayList<Integer>();
	if(root == null) {
		return inorderTraversal;
	}

        if (root.left !=null) {
		inorderTraversal.addAll(inorderTraversal(root.left));
	} 
	inorderTraversal.add(root.val);
	if (root.right !=null){
		inorderTraversal.addAll(inorderTraversal (root.right));
	}

	return inorderTraversal;
    }
}
```
