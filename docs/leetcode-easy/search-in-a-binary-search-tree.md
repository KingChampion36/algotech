# Search in a Binary Search Tree

### Link - [https://leetcode.com/problems/search-in-a-binary-search-tree/description/](https://leetcode.com/problems/search-in-a-binary-search-tree/description/){target="_blank"}

```java
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
  public TreeNode searchBST(TreeNode root, int val) {
    if (root == null) {
      return null;
    }
    if (root.val == val) {
      return root;
    }
    if (root.val > val) {
      return searchBST(root.left, val);
    }
    return searchBST(root.right, val);
  }
}
```

### Explanation:

* **Node Definition**: The code begins with the definition of the binary tree node class `TreeNode`, which includes a value (`val`), and references to the left and right child
  nodes (`left` and `right`).

* **Method Explanation**: The `searchBST` method searches for a node with a specific value (`val`) in the binary search tree rooted at `root`.

* **Base Case**: It starts with a base case where it checks if the current root node is null. If the root is null, it means the value was not found in the tree, and it returns
  null.

* **Value Comparison**: Next, it checks if the value of the current root node (`root.val`) matches the target value (`val`). If it matches, it returns the current root node,
  indicating that the value was found.

* **Recursive Search**: If the value is not found at the current root node, it decides whether to search in the left subtree or the right subtree based on a comparison between the
  target value and the current root node's value:

  * If the target value is less than the current node's value (`root.val`), it recursively calls `searchBST` on the left subtree (`root.left`).
  * If the target value is greater than the current node's value, it recursively calls `searchBST` on the right subtree (`root.right`).

* **Return Value**: The method returns the result of the recursive call, which will eventually return either the node with the target value or null if the value is not found in the
  tree.

!!! tip "Time and Space Complexities"

    - **Time Complexity:** O(log(n))
    - **Space Complexity:** O(log(n))
